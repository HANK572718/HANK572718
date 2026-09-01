<h1 align="center">林常瀚 Hank Lin</h1>
<p align="center">
  <b>工業 AI 視覺工程師</b>｜自動控制背景　·　台中
</p>

---

三個產業的產線瑕疵檢測落地，一套訓練後端支撐 4 個客戶約 50 個版本。三個手工特徵消掉約 70% 誤報。3D 定位現場誤差 1 cm。3.5 週從零到展會 demo。

自動控制本科，在自動化系統整合商擔任工程師三年（2023.08–2026.06）。做的是把 AI 檢測裝進既有產線的完整流程：相機與光源選型、影像擷取策略、特徵分析與模型選型、推論加速、服務化常駐與現場維運。設備端自己接 —— 相機觸發、光源、PLC 交握。

選型靠數據不靠直覺：六種異常偵測模型做完整 benchmark 再決定；3D 案評估後放棄 PointNet，幾何特徵 + DBSCAN 就夠。最後一年自己定調 GUI 架構、Ed25519 授權機制與部署工具鏈，並主導商用模型授權合規調查。

> 曾追一個只在現場那台機器上發生的 crash。抓 dump 比對，三份 failure hash 完全相同 —— 硬體不會每次死在同一個位址。翻 OpenVINO 原始碼找到文件沒寫的預設值開了 64 條閒置執行緒在跟 asyncio 搶 GIL。**症狀像硬體，根因在 library。**
> 所以系統要穩，硬體、驅動、軟體版本、library 參數、組合測試，每一層都得親手顧過 —— 模型只是其中一層。

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
