# AI-Market-Analyst

本專案透過 **API 爬取 Yahoo Finance 最新市場新聞**，使用 **AI 生成摘要與情緒分析**，並獲取 **市場指數數據**，最終透過 **Email 自動發送分析報告**。

## 1. 功能
- **Google News API** 爬取 Yahoo Finance 最新新聞
- **Hugging Face API** 生成新聞摘要 & 情緒分析
- **Yahoo Finance API（yfinance）** 獲取市場指數（S&P 500、Nasdaq、Dow Jones、Apple、Tesla）
- **Matplotlib & WordCloud** 生成視覺化分析（條形圖 & 文字雲）
- **SMTP API** 自動發送 Email，附加分析報告與圖片

## 2. 安裝
```bash
pip install -r requirements.txt
```
或手動安裝：
```bash
pip install requests beautifulsoup4 matplotlib pandas wordcloud yfinance yahoo_fin transformers torch
```

## 3. 運行
```bash
python main.py
```
系統將：
1. 爬取 Yahoo Finance 最新新聞
2. 生成 AI 摘要 & 情緒分析
3. 獲取市場數據
4. 生成圖表（條形圖 & 文字雲）
5. 自動發送 Email

## 4. API 整合
- **Google News API**：
  ```python
  response = requests.get("https://www.google.com/search?q=site:finance.yahoo.com+stock+market+news&tbm=nws", headers={"User-Agent": "Mozilla/5.0"})
  ```
- **Hugging Face API**：
  ```python
  summarizer = pipeline("summarization", model="facebook/bart-large-cnn")
  sentiment_analyzer = pipeline("sentiment-analysis")
  ```
- **Yahoo Finance API**：
  ```python
  import yfinance as yf
  price = yf.Ticker("^GSPC").history(period="1d")["Close"].iloc[-1]
  ```
- **SMTP API**：
  ```python
  server = smtplib.SMTP_SSL("smtp.gmail.com", 465)
  server.login(sender_email, password)
  server.sendmail(sender_email, receiver_email, msg.as_string())
  ```

## 5. Email 設定
1. 啟用 **Google 兩步驟驗證**
2. 生成 **應用程式密碼**
3. 在 Colab 或本地輸入 Gmail 密碼：
   ```python
   import getpass
   password = getpass.getpass("輸入 Gmail 應用程式密碼: ")
   ```

## 6. 視覺化分析
程式將自動生成：
- **條形圖**（新聞情緒分析）
- **文字雲**（新聞標題關鍵字）

```markdown
![情緒分析條形圖](images/sentiment_chart.png)
![新聞標題詞雲](images/wordcloud.png)
```

## 7. 未來發展
- 整合更多財經 API（Google Finance）
- AI 預測市場情緒
- Web Dashboard 可視化分析
