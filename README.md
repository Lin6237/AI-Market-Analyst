# AI-Market-Analyst

本專案透過 Hugging Face AI 模型分析 Yahoo Finance 的最新市場新聞，並進行 AI 自動摘要與情緒分析。系統也能透過 Email 推送分析結果，幫助投資者快速掌握市場動態。

## 1. 功能介紹
- 爬取 Yahoo Finance 最新市場新聞
- AI 生成新聞摘要（Hugging Face BART）
- AI 進行情緒分析（Positive / Negative / Neutral）
- 視覺化新聞數據（條形圖與詞雲）
- 發送 Email（市場新聞報告）

## 2. 技術架構
本專案使用以下技術：
- Python 3.8+
- Hugging Face Transformers（`facebook/bart-large-cnn` 摘要模型）
- BeautifulSoup4（爬取 Yahoo Finance 新聞）
- Matplotlib 與 WordCloud（新聞可視化）
- SMTP（Gmail 發送 Email）

## 3. 安裝環境
請確保環境有 Python 3.8 以上，然後執行：
pip install -r requirements.txt

如果希望安裝成完整的 Python 套件，可以執行：
python setup.py install

## 4. 如何運行專案
執行以下指令：
python main.py

系統將會爬取 Yahoo Finance 最新新聞，生成 AI 摘要與情緒分析結果，並顯示可視化圖表。

## 5. 設定 Email 推送功能
如需啟用 Email 通知，請至 Google 帳戶開啟「應用程式密碼」。

## 6. 視覺化結果
本專案包含：
條形圖：統計新聞的情緒分析結果
詞雲：從新聞標題中提取關鍵字

## 7. 其他
若爬取 Yahoo Finance 失敗，可能是 Google 變更了 HTML 結構，可嘗試更新 BeautifulSoup 解析邏輯。
若 Email 無法發送，請確認 Gmail 設定是否允許 SMTP 存取。
