<h1 align="center">林常瀚 Hank Lin</h1>
<p align="center">
  <b>工業 AI 視覺工程師</b>｜台中<br/>
  用 AI 視覺把工廠現場的檢測問題，做成能交付、能維運、授權乾淨的系統
</p>

---

自動化系統整合商 AI 工程師三年（2023.08–2026.06），主責工業瑕疵檢測系統
**從概念驗證到工廠 24/7 部署**的完整流程：相機與光源選型、影像擷取策略、
模型選型與訓練、推論加速，以及最容易被低估的那一段 —— **現場維運**。

三個不同產業產線落地，共用同一套訓練後端。最後一年重心從「寫能動的程式」
轉向「設計能交付的系統」：自己定調 GUI 架構、軟體授權機制與部署工具鏈，
並主導商用模型的授權合規調查。

> **現場的穩定性問題，不一定在程式碼裡。**
> 曾追一個間歇性 crash 追到最後，根因是 CPU 在推論、IO、GPU 同時高載時的
> 瞬間功耗把供電模組打到熱衝擊 —— 這類問題單看 log 永遠找不到。

## 做過什麼

| 專案 | 重點成果 |
|---|---|
| **工業表面瑕疵檢測系統** | 三產業落地、共用訓練後端支撐 4 客戶約 50 個 tag；粒子分析邏輯**消除約 70% 誤報**；現場推論 4×512² 約 **0.25 秒** |
| **3D 點雲定位與機械手臂取放** | 投射紋理立體視覺 + Open3D，現場誤差 **1 cm**；評估後**放棄 PointNet/DGCNN**，改用 DBSCAN + 幾何特徵 |
| **VisionFlow — SOP 工序電子化與即時監控** | PySide 6 + YOLOv11s-seg + TensorRT；**Ed25519 授權 + 機器指紋**；自製 Poetry plugin 做部署 |
| **CV 多任務標註暨訓練平台** | SAM2 多幀半自動標註；4 個訓練後端整合、3 種訓練類型 |

## 交付鏈上的三個 Poetry plugin

```mermaid
flowchart LR
    A["poetry-hw-plugin<br/>管進去<br/>跨平台依賴 variants"] --> B["rich-deploy<br/>管出來<br/>打包成可交付形態"]
    B --> C["simple_license_manager<br/>管到了之後<br/>離線 RSA-2048 授權"]

    style A fill:#1f3d4a,color:#fff
    style B fill:#1f4a3d,color:#fff
    style C fill:#4a3d1f,color:#fff
```

單獨看每一個都只是小工具，合起來是一條完整的交付鏈 ——
被實際交付產品逼出來的，不是設計出來的。

## 開源

| 專案 | 做什麼 |
|---|---|
| [simple_license_manager](https://github.com/HANK572718/simple_license_manager) | `licmg` — 離線 RSA-2048 授權管理，Poetry plugin + 獨立 CLI |
| [rich-deploy](https://github.com/HANK572718/rich-deploy) | 部署打包用的 Poetry plugin |
| [poetry-hw-plugin](https://github.com/HANK572718/poetry-hw-plugin) | 跨平台依賴管理，自動切換硬體 variants |
| [torch-xpu-patch](https://github.com/HANK572718/torch-xpu-patch) | Intel XPU（Arc GPU）通用 Torch monkey patch |
| [craft_file_mcp](https://github.com/HANK572718/craft_file_mcp) | Craft 檔案存取的 MCP server |
| [img2voice](https://github.com/HANK572718/img2voice) | 書頁照片轉文字與語音，本機 GPU（GOT-OCR2.0 + edge-tts） |
| [FCU_LabVIEW_Course_AI_part](https://github.com/HANK572718/FCU_LabVIEW_Course_AI_part) | 逢甲大學 LabVIEW + Python 課程 AI 段教材 |
| [nvchad_config](https://github.com/HANK572718/nvchad_config) | 個人 Neovim / NvChad 設定 |

## 技術棧

**CV**　OpenCV · anomalib（RD / EfficientAD / FastFlow / STFPM / PatchCore / PaDiM）· YOLOv10 / v11-seg · RF-DETR · Detectron2 · SAM / SAM2
**推論部署**　OpenVINO · TensorRT · ONNX · cx_Freeze · NSSM · Poetry
**3D 視覺**　Open3D · PCL · DBSCAN · RANSAC · 立體相機 SDK · 座標系校正
**後端 / MLOps**　Python · FastAPI · 非同步推論 · MLflow · TensorBoard
**LLM**　LangChain · LangGraph · SQL Agent · RAG · Streamlit
**硬體整合**　工業相機 · 雷射位移感測 · Intel Arc GPU / Core Ultra NPU · 工業電腦 · PLC · PoE

## 學歷

逢甲大學　自動控制工程學系　學士　｜　國立台中高工　機械科

畢業專題「新式自動化垂直農場」獲**國科會大專生研究計畫**與學術論壇**最佳論文獎**；
全國技能競賽機器人職種**中部分區賽第四**（48 隊）。

---

<p align="center">
  <a href="https://HANK572718.github.io/">個人網站</a>　·　<a href="mailto:ha28763024@gmail.com">ha28763024@gmail.com</a>
</p>
