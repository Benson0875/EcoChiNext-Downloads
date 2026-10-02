# 下載與燒錄

## 1. 下載完整草稿

到 [Releases](https://github.com/Benson0875/EcoChiNext-Downloads/releases/latest) 下載 `EcoChiNext-0.13.0-observe-Arduino.zip`，解壓到本機一般資料夾。開啟內部 `EcoChiNext/EcoChiNext.ino`，不要只複製一個 `.ino`，也不要使用舊的 EcoChi 草稿。

核對 IDE 標題 **EcoChiNext**、`Config.h` 中版本 **0.13.0-observe**。此下載包不依賴開發者的 WSL 路徑或 Windows 檔案關聯腳本。

## 2. Arduino IDE

安裝 ESP32 by Espressif Systems（本版編譯紀錄使用 3.3.8），以及 Library Manager 的 Adafruit GFX Library、Adafruit ST7735 and ST7789 Library、Adafruit AHTX0、Adafruit BusIO、RTClib。

| 設定 | 值 |
| --- | --- |
| Board | ESP32 Dev Module（ESP32-WROOM-32） |
| Partition Scheme | Huge APP（3MB No OTA/1MB SPIFFS） |
| PSRAM | Disabled |
| Flash Size / Mode / Frequency | 4MB / DIO / 40MHz |
| CPU Frequency / Upload Speed | 240MHz / 115200 |
| Port | 你的實際 ESP32 序列埠，不一定是 COM7 |
| Erase All Flash Before Sketch Upload | Disabled |

先備份 SD 的 `/next/` 與原有存檔，按 Verify 編譯通過，再按 Upload。不要清卡或整片 Flash 擦除。成功後核對開機／115200 baud 序列版本回報；只看到上傳完成不代表所有功能通過。

存檔 v5 使用 CRC32、A/B 雙槽；原版存檔與 Next 分開。舊 Next 不一定能讀 v5，降版前備份。

## 3. 必要硬體對照

本版不是任何 ESP32 裸板都能直接玩；需要符合以下接線的 TFT、按鍵與周邊。所有模組共地，ADC 不得接 5V。

| 元件 | ESP32 GPIO |
| --- | --- |
| ST7735 SCK / MOSI / CS / DC / RST | 18 / 23 / 15 / 25 / EN |
| SD SCK / MOSI / MISO / CS | 18 / 23 / 19 / 5 |
| AHT20、DS3231 SDA / SCL | 21 / 22 |
| GY-61 X / Y / Z（3.3V 供電） | 34 / 35 / 39 |
| MQ-135 AO | 20kΩ 上臂、33kΩ 下臂分壓後接 36；不可直入 ADC |
| 上 / 下 / 左 / 右 | 4 / 13 / 14 / 27；按鍵另一端 GND |
| A / B | 32 / 33；按鍵另一端 GND |
| VOL+ / VOL− / 蜂鳴器 IN | 16 / 17 / 26 |

MQ-135 模組為 5V，AO 分壓上臂接 AO、下臂接 GND。請自行確認模組、供電及 TFT 驅動相容，勿以本文件取代電氣檢查。

## 4. 開機驗收

確認取名／地圖、六鍵、TFT、SD 保存與重載、感測缺值及 Wi-Fi。SD 缺失仍可開機；無 SD 正式評測不可用。GY-61 需實測方向、範圍與穩定性，校正通過不保證排除浮接。

下載包不包含 Arduino IDE 或第三方函式庫；請由官方來源安裝。專案公開提供下載，不代表第三方元件失去其原有授權。
