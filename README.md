# 📈 Investment Dashboard

A full-stack investment portfolio tracker that lets you monitor stocks and cryptocurrencies in real time. Search for assets, track their historical price charts, view company financials, convert between currencies, and keep your portfolio persisted across sessions — all in one sleek dashboard.

---

## 🖥️ Tech Stack

| Layer      | Technology                          |
|------------|--------------------------------------|
| Frontend   | React 17, Chart.js, Bulma CSS        |
| Backend    | Node.js, Express                     |
| APIs       | Yahoo Finance, Alpha Vantage, Nomics, CoinCap |
| Storage    | Browser Local Storage                |

---

## ✨ Features

- **Portfolio Overview** — Doughnut chart showing your asset allocation at a glance
- **Stock & Crypto Search** — Auto-complete search powered by Yahoo Finance & CoinCap APIs
- **Price History Charts** — Weekly-adjusted historical price charts via Alpha Vantage
- **Live Price Refresh** — Fetch latest prices on demand
- **Company Financials** — View key financial data for any listed company
- **Currency Conversion** — Switch your portfolio display between multiple currencies
- **Persistent Portfolio** — Assets and preferred currency saved to local storage automatically
- **Welcome Onboarding** — First-time modal to guide new users

---

## 📁 Project Structure

```
investment-dashboard/
├── backend-server/          # Express API server
│   ├── routes/
│   │   ├── search.js        # Stock & crypto search endpoints
│   │   ├── price.js         # Current & historical price endpoints
│   │   ├── currency.js      # Currency conversion endpoint
│   │   └── financials.js    # Company financials endpoint
│   ├── server.js            # Entry point
│   ├── .env.sample          # Environment variable template
│   └── package.json
│
└── frontend-react/          # React application
    ├── src/
    │   ├── components/
    │   │   ├── navbar/          # Top navigation bar
    │   │   ├── doughnut/        # Portfolio doughnut chart
    │   │   ├── assets/          # Asset table component
    │   │   ├── addAsset/        # Add/edit asset modal
    │   │   ├── ui/              # Shared UI components
    │   │   ├── CurrencySelector.js
    │   │   ├── RefreshPricesBtn.js
    │   │   ├── Instructions.js
    │   │   └── WelcomeModal.js
    │   ├── lib/                 # Utility logic (localStorage, price updates)
    │   ├── data/                # Static data (currency lists, etc.)
    │   ├── utils/               # Helper functions
    │   └── App.js               # Root component
    └── package.json
```

---

## 🚀 Getting Started

### Prerequisites

- [Node.js](https://nodejs.org/) (v14 or higher recommended)
- npm (comes with Node.js)
- API keys (see [API Keys](#-api-keys) section below)

---

### 1. Clone the Repository

```bash
git clone https://github.com/your-username/investment-dashboard.git
cd investment-dashboard
```

---

### 2. Set Up API Keys

Navigate to `backend-server/` and copy the sample environment file:

```bash
cd backend-server
copy .env.sample .env
```

Then open `.env` and fill in your API keys:

```env
HYPERCHARTS_API_KEY=your-api-key-here
ALPHA_VANTAGE_API_KEY=your-api-key-here
NOMICS_API_KEY=your-api-key-here
COIN_CAP_API_KEY=your-api-key-here
```

---

### 3. Install Dependencies

**Backend:**
```bash
cd backend-server
npm install
```

**Frontend:**
```bash
cd ../frontend-react
npm install
```

---

### 4. Run the Application

Open **two terminal windows** and run each service separately.

**Terminal 1 — Backend:**
```bash
cd backend-server
npm run dev
```
> Backend runs at `http://localhost:3000`

**Terminal 2 — Frontend:**
```bash
cd frontend-react
npm start
```
> Frontend runs at `http://localhost:3001` (or next available port)

---

## 🔑 API Keys

| API | Purpose | Free Tier | Link |
|-----|---------|-----------|------|
| **Alpha Vantage** | Historical stock & crypto price charts | ✅ Yes (5 req/min) | [alphavantage.co](https://www.alphavantage.co/support/#api-key) |
| **Nomics** | Live crypto prices | ✅ Yes | [nomics.com](https://nomics.com/) |
| **CoinCap** | Crypto search & discovery | ✅ Yes | [coincap.io](https://docs.coincap.io/) |
| **HyperCharts** | Company financials | ✅ Yes | [hypercharts.co](https://hypercharts.co/) |

> **Note:** Yahoo Finance endpoints are used without an API key (unofficial public API).

---

## 🌐 Backend API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| `GET` | `/wake-up` | Health check — returns `{ status: "Awake" }` |
| `GET` | `/search/stocks/:input` | Search for stocks by keyword |
| `GET` | `/search/crypto/:input` | Search for cryptocurrencies |
| `GET` | `/price/stock/current/:symbol` | Get current stock price |
| `GET` | `/price/stock/historical/:symbol` | Get weekly historical stock price |
| `GET` | `/price/crypto/current/:symbol` | Get current crypto price |
| `GET` | `/price/crypto/historical/:symbol` | Get daily historical crypto price |
| `GET` | `/currency` | Get currency conversion rates |
| `GET` | `/financials` | Get company financial data |

---

## 🛠️ Scripts

### Backend (`backend-server/`)

| Command | Description |
|---------|-------------|
| `npm run dev` | Start server with hot-reload using nodemon |

### Frontend (`frontend-react/`)

| Command | Description |
|---------|-------------|
| `npm start` | Start React development server |
| `npm run build` | Build for production |
| `npm test` | Run test suite |

---

## ⚠️ Known Issues & Notes

- The **Alpha Vantage free tier** is limited to 5 requests per minute and 500/day. Loading many assets quickly may result in incomplete chart data.
- The **Nomics API** is rate-limited to 1 request/second — the backend uses `express-slow-down` to handle this gracefully.
- The **Daily Adjusted** Alpha Vantage endpoint is now a **premium feature**; the app uses the free **Weekly Adjusted** endpoint instead.
- Portfolio data is stored in **browser local storage** — clearing your browser data will erase your saved assets.

---

## 📄 License

This project is licensed under the [MIT License](LICENSE).

---

## 🙏 Acknowledgements

- [Yahoo Finance](https://finance.yahoo.com/) — Stock data & search
- [Alpha Vantage](https://www.alphavantage.co/) — Historical price data
- [CoinCap](https://coincap.io/) — Cryptocurrency data
- [Nomics](https://nomics.com/) — Live crypto pricing
- [Chart.js](https://www.chartjs.org/) — Interactive charts
- [Bulma](https://bulma.io/) — CSS framework
