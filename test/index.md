# N64 Style 3D Spinning Logo GIF Generator

這個項目是一個基於 WebGL (Three.js) 與 GIF 運算庫的網頁應用程式，重現了 90 年代經典 **Nintendo 64（如《Mario Kart 64》）** 開機畫面中的立體橢圓旋轉標誌，並支援即時輸入文字、七彩自訂顏色，以及一鍵匯出 360° 轉圈 GIF 動畫。

---

## 🛠️ 技術架構與原理 (How it Works)

網頁採用單一 HTML 檔案架構（Single-File Component），結合以下核心技術：

1. **Three.js (3D 繪圖引擎)**
   - **Torus Geometry (圓環體)**：構建標誌外圍的經典紅色立體橢圓框，並透過 Scale 縮放塑造 N64 獨特的扁平橢圓形狀。
   - **Cylinder Geometry (圓柱體)**：作為橢圓框內部的底座。
   - **Dynamic Canvas Texture (動態畫布貼圖)**：將使用者輸入的自訂文字動態繪製於 Canvas 2D，再作為 Texture 貼上 3D Banner 網格，確保文字支援各種語言且清晰銳利。
   - **Dynamic Lighting (動態光照)**：配置 AmbientLight（環境光）、DirectionalLight（平行光）與 PointLight（點光源），呈現 90 年代 Arcade 遊戲機台的金屬感與高光切面。

2. **GIF.js (用戶端 GIF 編碼器)**
   - 利用 Web Workers 在背景執行幀擷取與 LZW 壓縮演算法。
   - 精確計算 360° 旋轉的角度差（$\Delta \theta = \frac{2\pi}{\text{Total Frames}}$），均勻擷取 30 個角度幀。
   - 自動將 WebGL Canvas 渲染圖層縮放到 320x320 像素，並合成本地可直接下載的循環 GIF 檔案。

3. **Tailwind CSS & Google Fonts**
   - 使用 retro 電玩風格字型（*Press Start 2P* 與 *Outfit*）。
   - 打造響應式（Mobile-friendly）的懷舊霓虹暗色調介面。

---

## 🚀 主要功能 (Features)

- 🔤 **自訂文字**：即時預覽輸入的名稱（如 `MARIO KART`、`NINTENDO` 或你自己的名字）。
- 🎨 **七彩顏色面板**：
  - 獨立調整外框顏色、標誌底色、文字顏色及背景顏色。
  - **Rainbow 霓虹模式**：開啟 HSL 動態 Rainbow 炫光效果。
  - **預設配色方案**：包含 N64 經典紅、聖劍黃金、賽博朋克與翡翠碧綠。
- 🎛️ **動態參數調校**：支援調整旋轉速度與 3D 標誌厚度/深度。
- 💾 **一鍵輸出 360° GIF**：自動計算完整轉圈幀率並提供進度條，完成後可即時下載。

---

## 📁 檔案結構 (File Structure)

```text
.
├── index.html   # 包含所有 UI 介面、Three.js 3D 渲染與 GIF 生成邏輯的主檔案
└── README.md    # 項目說明與技術文件
```

---

## 💻 執行方式 (How to Run)

1. 不需要安裝任何 Node.js 或後端伺服器環境。
2. 直接使用瀏覽器（Chrome、Edge、Safari、Firefox 等）打開 `index.html` 即可使用。
