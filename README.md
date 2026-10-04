# 投資決策工作台（GitHub Pages 版）

單一檔案的靜態網頁 `index.html`。輸入股票代號、按「查詢並自動填入」，就會在你自己的瀏覽器裡直接呼叫：

- **FinMind API**（財報、月營收等，免金鑰）
- **台灣證交所官方 OpenAPI**（股價 OHLC，免金鑰）

把能查到的真實數字自動填進品質關、估值關、風控關；查不到共識數字的欄位（未來預估EPS、情境本益比）保持空白，由你自己判斷填入。

## 上架到 GitHub Pages（用 GitHub Desktop）

1. 打開 GitHub Desktop → File → New repository，Name 隨意（例如 `stock-desk`），Local Path 選一個你平常放專案的資料夾，建立好。
2. 用檔案總管/Finder，把這個資料夾裡的 `index.html`（和這份 `README.md`）複製進剛剛建立的 repo 資料夾裡。
3. 回到 GitHub Desktop，左下角會看到變更，填一下 commit 訊息（例如「first version」），按 **Commit to main**。
4. 按上方 **Publish repository**（如果要私人用，勾選 Keep this code private 也沒關係，Pages 私人repo免費帳號也能開）。
5. 瀏覽器打開 `https://github.com/<你的帳號>/<repo名稱>` → **Settings** → 左側 **Pages** → Build and deployment 的 Source 選 **Deploy from a branch** → Branch 選 **main** / **root** → Save。
6. 等 1-2 分鐘，重新整理該頁面，會出現網址，例如 `https://<你的帳號>.github.io/<repo名稱>/`，打開就是你的工作台。

之後要更新（例如請 Claude 幫你調整介面），把新的 `index.html` 覆蓋進同一個資料夾，GitHub Desktop 會自動偵測變更，commit → push 就會更新上線的網站。

## 已知限制

- 這是純前端網頁，沒有後端，所以你的輸入（情境假設、觀察名單等）只存在你自己瀏覽器的 localStorage，換瀏覽器/換裝置不會同步。
- 如果 FinMind 或證交所某天改版、關站或調整流量限制，查詢可能失敗——失敗時狀態列會顯示原因，欄位仍可手動填寫，不影響四關計算本身。
- 情境關（悲觀/中性/樂觀 EPS 與本益比）、未來預估EPS 目前沒有可靠的免費公開API能自動抓，仍需要你自己判斷或請 Claude 幫你查完後手動填入。
