# Investment Dashboard

A full-stack investment dashboard for tracking your portfolio, viewing stock & crypto price history, and analyzing company financials.

## Tech Stack

- **Frontend:** React, Chart.js
- **Backend:** Node.js, Express

## Getting Started

### 1. Install dependencies

```bash
cd backend-server
npm install

cd ../frontend-react
npm install
```

### 2. Set up environment variables

Rename `.env.sample` to `.env` in the `backend-server` folder and add your API keys.

### 3. Run the app

**Backend:**
```bash
cd backend-server
npm run dev
```

**Frontend:**
```bash
cd frontend-react
npm run dev
```

The frontend will be available at `http://localhost:3000`.

## Features

- Portfolio tracking with a doughnut chart breakdown
- Stock & crypto price history charts
- Company financials viewer
- Currency conversion
- Search for stocks and crypto assets
- Portfolio data persisted in local storage
