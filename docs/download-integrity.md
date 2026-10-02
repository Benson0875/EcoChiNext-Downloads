# 下載版本與完整性

發布版本：**0.13.0-observe**；整理日期：2026-10-03（Asia/Taipei）。

下載檔：`EcoChiNext-0.13.0-observe-Arduino.zip`，位於本專案 GitHub Releases。

SHA-256：

```text
e66671081fd5945adad33e73576352380ed71f921c6572c238c8b6e3d6f48be3
```

PowerShell 核對：

```powershell
Get-FileHash .\EcoChiNext-0.13.0-observe-Arduino.zip -Algorithm SHA256
```

此 ZIP 為完整 Arduino 原始碼、網頁原始碼及教學，不是單一預編譯安裝程式。沒有散布整片 Flash 映像，避免使用者誤將開發板設定與資料區一起覆蓋。請按安裝說明編譯上傳。

發布前核對：全部草稿 `.ino/.h/.cpp` 與兩份網頁原始碼包含在 ZIP；每個 ZIP 檔案與打包來源 SHA-256 一致；未包含 `.git`、`.build`、CSV、遊戲存檔、受試者資料、帳號或開發工具。

重新 Arduino 編譯成功：程式 1,172,889 bytes（37%）、全域 RAM 61,380 bytes（18%）。本次只建立下載包，沒有燒錄。此包與已知版本的工程功能一致，不代表所有下載者的硬體已通過實機驗證。

原始碼內的 `ecochi26` 是公開文件中的原型 AP 預設密碼，不是 GitHub token 或私人帳號憑證。不要把此固定密碼網路用於公開環境或敏感人體資料收集。
