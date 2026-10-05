# Aryan Salunkhe

**I build full-stack products with a machine-learning core.**

I like projects where three parts have to work together: a clear front end, a Node.js back end that does the real-time plumbing, and a Python service that does the modelling. Most of what's below is built that way, from fraud scoring that learns each user's habits to forecasting market stress and settling a poker night in the fewest payments.

📍 Maharashtra, India

---

## Featured projects

### 🛡️ [PayShield](https://github.com/AeroSalu/PayShield): real-time risk intelligence for digital payments

Fraud in instant payments has to be caught in the fraction of a second between "Pay" and "Paid". PayShield scores every payment event as it arrives, explains the score, recommends an action and streams the result to a live dashboard.

- **Learns each user's normal behaviour**: typical amount and spread, hours they transact in, known devices and beneficiaries. Profiles update with an exponential moving average, and only from payments judged safe, so a suspicious burst can't teach the system that it's normal.
- **Looks at the receiving side too**: tracks unique senders and incoming velocity per beneficiary to flag potential mule-account patterns.
- **Hybrid scoring**: rule-based behavioural signals combined with an Isolation Forest anomaly score from a separate Python service.
- **Live by design**: sliding-window velocity counters in Redis sorted sets, results pushed to the dashboard over WebSockets, whole stack runs with one Docker Compose command.
- Currently an MVP on synthetic payment events, with a provider interface ready for a real payment source.

`React` `Vite` `Tailwind CSS` `Node.js` `Express` `PostgreSQL` `Redis` `WebSockets` `Python` `FastAPI` `scikit-learn` `Docker`

### 📉 [Financial Crisis Early Warning System](https://github.com/AeroSalu/financial-crisis)

A probabilistic dashboard that estimates market-crash risk, banking instability and liquidity shortage, and lets you stress-test the forecast.

- **Forecasting core**: a VARIMA model (Darts) trained on market data from Yahoo Finance and FRED, with Student-t Monte Carlo paths for fat-tailed risk.
- **News as a signal**: VADER sentiment analysis on recent headlines feeds into the risk estimate.
- **Any asset, on demand**: trains a fresh model for a chosen asset such as NIFTY 50, Bitcoin or gold, and projects P10–P90 price corridors over horizons from one day to three weeks.
- **Scenario simulator**: sliders for shocks like a rate hike or a COVID-style crash, with the shock propagating across correlated assets and decaying over time.
- **Practical touches**: SQLite cache for market data so the app doesn't get rate-limited.

`Python` `FastAPI` `Darts` `NumPy` `Pandas` `SciPy` `Node.js` `Express` `SQLite` `Chart.js`

### 🔥 [RoastIt](https://github.com/AeroSalu/Roastit): AI profile analysis that people actually read

Paste a GitHub or Instagram profile and get honest, technically informed feedback: strengths, weaknesses, patterns and what to fix, delivered as a roast so it sticks.

- **Runs on a local LLM**: Qwen 3 8B through Ollama, so no paid AI API and no profile data sent to a third-party AI service.
- **Grounded in real data**: pulls a profile and its repositories from the GitHub API, and the model is told to answer only from what it is given.
- **Structured output**: every roast comes back as validated JSON with technical, project and activity analysis, strengths, weaknesses and concrete recommendations.
- **English or Hinglish**: a second mode written in natural Roman Hinglish rather than translated English.
- **Accounts and history**: Google sign-in with Firebase Authentication; roasts saved per user in Firestore, with security rules that keep each user's history private.

`JavaScript` `Node.js` `Express` `Ollama` `Firebase Auth` `Firestore` `GitHub REST API`

### ♠️ [PokerSplit](https://github.com/AeroSalu/PokerSplit) · [try it live](https://pokersplit-rose.vercel.app)

An installable app for home poker nights that replaces the notebook: who bought in, who owes whom, and how to square up.

- **Fewest-payments settlement**: finds the minimum number of transfers to settle the table using a bitmask search over zero-sum groups of players.
- **Built around how home games really run**: buy-ins from the bank or from another player's stack, players joining and leaving mid-game, half and custom buy-ins, and an editable log that refuses changes which would make the history inconsistent.
- **Offline-first PWA**: works with no signal, installs to the home screen, keeps debts, history and a leaderboard on the phone.
- **Live table view**: a read-only link for other players over Firebase Realtime Database, with signed writes so only the scorer's phone can update a game.
- **No framework, no build step**: plain JavaScript with a tested pure-logic core.

`JavaScript` `PWA` `Service Workers` `Firebase Realtime Database` `Vercel`

---

## Stack

```text
Languages    JavaScript    Python        Java          SQL
Frontend     React         Vite          Tailwind CSS  Chart.js      PWA
Backend      Node.js       Express       FastAPI       REST APIs     WebSockets
Data         PostgreSQL    Redis         SQLite        Firestore     Realtime Database
ML / AI      scikit-learn  Darts         Pandas        NumPy         Ollama (local LLMs)
Techniques   Anomaly detection   Time-series forecasting   Monte Carlo   Sentiment analysis
Tools        Git           Docker        Vercel        Firebase
```

## Problem solving

I practise data structures and algorithms in Java on LeetCode. My accepted solutions sync automatically to [AeroSalu/leetcode](https://github.com/AeroSalu/leetcode), 70 problems and counting, and I look for chances to use them in real projects, like the settlement algorithm in PokerSplit.
