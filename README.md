 Kamala-fx-
Chart Analysis 

<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>MARKET EDGE — Pure Signal Trading</title>
<link href="https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@300;400;600;700&family=Syne:wght@400;600;800&display=swap" rel="stylesheet">
<style>
  :root {
    --bg: #060a0f;
    --bg2: #0d1520;
    --bg3: #111d2e;
    --border: #1a2d45;
    --accent: #00d4ff;
    --accent2: #00ff9d;
    --accent3: #ff6b35;
    --danger: #ff3d5a;
    --warn: #ffcc00;
    --text: #e8f4ff;
    --muted: #4a6a8a;
    --card: #0a1929;
    --bull: #00ff9d;
    --bear: #ff3d5a;
    --neutral: #ffcc00;
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'JetBrains Mono', monospace;
    min-height: 100vh;
    overflow-x: hidden;
  }

  /* Animated grid background */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background-image:
      linear-gradient(rgba(0,212,255,0.03) 1px, transparent 1px),
      linear-gradient(90deg, rgba(0,212,255,0.03) 1px, transparent 1px);
    background-size: 40px 40px;
    pointer-events: none;
    z-index: 0;
  }

  body::after {
    content: '';
    position: fixed;
    top: -50%;
    left: -50%;
    width: 200%;
    height: 200%;
    background: radial-gradient(ellipse at 30% 20%, rgba(0,212,255,0.04) 0%, transparent 50%),
                radial-gradient(ellipse at 70% 80%, rgba(0,255,157,0.03) 0%, transparent 50%);
    pointer-events: none;
    z-index: 0;
    animation: aurora 20s ease-in-out infinite alternate;
  }

  @keyframes aurora {
    0% { transform: translate(0,0) rotate(0deg); }
    100% { transform: translate(2%, 2%) rotate(3deg); }
  }

  /* HEADER */
  header {
    position: relative;
    z-index: 10;
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 18px 32px;
    border-bottom: 1px solid var(--border);
    background: rgba(6,10,15,0.9);
    backdrop-filter: blur(20px);
  }

  .logo {
    font-family: 'Syne', sans-serif;
    font-size: 22px;
    font-weight: 800;
    letter-spacing: -0.5px;
    display: flex;
    align-items: center;
    gap: 10px;
  }

  .logo-icon {
    width: 32px; height: 32px;
    background: linear-gradient(135deg, var(--accent), var(--accent2));
    clip-path: polygon(50% 0%, 100% 38%, 82% 100%, 18% 100%, 0% 38%);
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 14px;
    animation: pulse-logo 3s ease-in-out infinite;
  }

  @keyframes pulse-logo {
    0%,100% { box-shadow: 0 0 10px rgba(0,212,255,0.4); }
    50% { box-shadow: 0 0 25px rgba(0,212,255,0.8); }
  }

  .logo span { color: var(--accent); }

  .header-status {
    display: flex;
    align-items: center;
    gap: 20px;
    font-size: 11px;
    color: var(--muted);
  }

  .live-dot {
    width: 6px; height: 6px;
    background: var(--accent2);
    border-radius: 50%;
    animation: blink 1.5s infinite;
  }

  @keyframes blink {
    0%,100% { opacity: 1; transform: scale(1); }
    50% { opacity: 0.3; transform: scale(0.8); }
  }

  /* CONTROLS */
  .controls {
    position: relative;
    z-index: 10;
    display: flex;
    gap: 12px;
    padding: 16px 32px;
    border-bottom: 1px solid var(--border);
    flex-wrap: wrap;
    align-items: center;
    background: rgba(6,10,15,0.7);
  }

  select, button {
    font-family: 'JetBrains Mono', monospace;
    font-size: 12px;
    background: var(--bg3);
    color: var(--text);
    border: 1px solid var(--border);
    padding: 8px 14px;
    cursor: pointer;
    transition: all 0.2s;
    border-radius: 3px;
    outline: none;
  }

  select:hover, select:focus { border-color: var(--accent); }

  .btn-primary {
    background: linear-gradient(135deg, rgba(0,212,255,0.15), rgba(0,255,157,0.1));
    border-color: var(--accent);
    color: var(--accent);
    font-weight: 600;
    letter-spacing: 1px;
    text-transform: uppercase;
    font-size: 11px;
  }

  .btn-primary:hover {
    background: linear-gradient(135deg, rgba(0,212,255,0.3), rgba(0,255,157,0.2));
    box-shadow: 0 0 20px rgba(0,212,255,0.3);
  }

  .btn-primary:disabled {
    opacity: 0.5;
    cursor: not-allowed;
  }

  /* STRATEGY PILLS */
  .strat-pills {
    display: flex;
    gap: 8px;
    flex-wrap: wrap;
  }

  .pill {
    padding: 6px 12px;
    border: 1px solid var(--border);
    border-radius: 20px;
    font-size: 10px;
    cursor: pointer;
    transition: all 0.2s;
    color: var(--muted);
    text-transform: uppercase;
    letter-spacing: 0.5px;
  }

  .pill.active { border-color: var(--accent); color: var(--accent); background: rgba(0,212,255,0.1); }
  .pill:hover { border-color: var(--accent); color: var(--accent); }

  /* MAIN LAYOUT */
  .main {
    position: relative;
    z-index: 5;
    display: grid;
    grid-template-columns: 1fr 340px;
    gap: 0;
    height: calc(100vh - 120px);
  }

  /* CHART AREA */
  .chart-area {
    border-right: 1px solid var(--border);
    display: flex;
    flex-direction: column;
    overflow: hidden;
  }

  .chart-header {
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 14px 24px;
    border-bottom: 1px solid var(--border);
    flex-shrink: 0;
  }

  .pair-display {
    font-family: 'Syne', sans-serif;
    font-size: 24px;
    font-weight: 800;
    letter-spacing: -1px;
  }

  .price-display {
    font-size: 28px;
    font-weight: 700;
    color: var(--accent2);
    transition: color 0.3s;
  }

  .price-change {
    font-size: 12px;
    padding: 3px 8px;
    border-radius: 3px;
  }

  .price-change.up { background: rgba(0,255,157,0.15); color: var(--bull); }
  .price-change.down { background: rgba(255,61,90,0.15); color: var(--bear); }

  canvas#chart {
    flex: 1;
    display: block;
    cursor: crosshair;
  }

  /* SIGNAL BAR */
  .signal-bar {
    display: flex;
    gap: 12px;
    padding: 10px 24px;
    border-top: 1px solid var(--border);
    background: var(--bg2);
    flex-wrap: wrap;
    flex-shrink: 0;
  }

  .sig-item {
    display: flex;
    align-items: center;
    gap: 6px;
    font-size: 10px;
    color: var(--muted);
    text-transform: uppercase;
    letter-spacing: 0.5px;
  }

  .sig-val { font-weight: 600; font-size: 11px; }
  .sig-val.bull { color: var(--bull); }
  .sig-val.bear { color: var(--bear); }
  .sig-val.neutral { color: var(--neutral); }

  /* SIDEBAR */
  .sidebar {
    display: flex;
    flex-direction: column;
    overflow-y: auto;
    scrollbar-width: thin;
    scrollbar-color: var(--border) transparent;
  }

  .sidebar::-webkit-scrollbar { width: 4px; }
  .sidebar::-webkit-scrollbar-track { background: transparent; }
  .sidebar::-webkit-scrollbar-thumb { background: var(--border); border-radius: 2px; }

  /* SIGNAL CARD */
  .signal-card {
    margin: 16px;
    padding: 20px;
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 4px;
    position: relative;
    overflow: hidden;
  }

  .signal-card::before {
    content: '';
    position: absolute;
    left: 0; top: 0; bottom: 0;
    width: 3px;
  }

  .signal-card.LONG::before { background: var(--bull); }
  .signal-card.SHORT::before { background: var(--bear); }
  .signal-card.NEUTRAL::before { background: var(--neutral); }

  .signal-card.LONG { border-color: rgba(0,255,157,0.2); }
  .signal-card.SHORT { border-color: rgba(255,61,90,0.2); }

  .signal-title {
    font-family: 'Syne', sans-serif;
    font-size: 11px;
    font-weight: 600;
    color: var(--muted);
    text-transform: uppercase;
    letter-spacing: 2px;
    margin-bottom: 12px;
  }

  .signal-direction {
    font-family: 'Syne', sans-serif;
    font-size: 36px;
    font-weight: 800;
    line-height: 1;
    margin-bottom: 8px;
    letter-spacing: -1px;
  }

  .signal-direction.LONG { color: var(--bull); }
  .signal-direction.SHORT { color: var(--bear); }
  .signal-direction.NEUTRAL { color: var(--neutral); }

  .signal-conf {
    font-size: 12px;
    color: var(--muted);
    margin-bottom: 16px;
  }

  .conf-bar {
    height: 4px;
    background: var(--border);
    border-radius: 2px;
    overflow: hidden;
    margin-bottom: 16px;
  }

  .conf-fill {
    height: 100%;
    border-radius: 2px;
    transition: width 0.5s ease;
  }

  .conf-fill.LONG { background: linear-gradient(90deg, var(--bull), #00ff9d88); }
  .conf-fill.SHORT { background: linear-gradient(90deg, var(--bear), #ff3d5a88); }
  .conf-fill.NEUTRAL { background: linear-gradient(90deg, var(--warn), #ffcc0088); }

  .signal-levels {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;
    gap: 8px;
    font-size: 10px;
  }

  .level-box {
    background: var(--bg3);
    border: 1px solid var(--border);
    padding: 8px;
    border-radius: 3px;
    text-align: center;
  }

  .level-label {
    color: var(--muted);
    text-transform: uppercase;
    letter-spacing: 0.5px;
    font-size: 9px;
    margin-bottom: 4px;
  }

  .level-price { font-weight: 700; font-size: 11px; }
  .level-price.entry { color: var(--accent); }
  .level-price.sl { color: var(--bear); }
  .level-price.tp { color: var(--bull); }

  /* STRATEGY CARDS */
  .strat-section {
    padding: 0 16px 16px;
  }

  .strat-header {
    font-size: 10px;
    color: var(--muted);
    text-transform: uppercase;
    letter-spacing: 2px;
    margin-bottom: 10px;
    padding-bottom: 8px;
    border-bottom: 1px solid var(--border);
  }

  .strat-card {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 4px;
    padding: 12px 14px;
    margin-bottom: 8px;
    display: flex;
    align-items: center;
    gap: 12px;
    transition: all 0.2s;
  }

  .strat-card:hover { border-color: var(--accent); }

  .strat-icon {
    width: 32px; height: 32px;
    border-radius: 3px;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 14px;
    flex-shrink: 0;
  }

  .strat-info { flex: 1; min-width: 0; }
  .strat-name { font-size: 11px; font-weight: 600; margin-bottom: 2px; }
  .strat-desc { font-size: 9px; color: var(--muted); line-height: 1.4; }

  .strat-signal {
    font-size: 10px;
    font-weight: 700;
    padding: 3px 8px;
    border-radius: 2px;
    text-transform: uppercase;
    letter-spacing: 0.5px;
    flex-shrink: 0;
  }

  .strat-signal.bull { background: rgba(0,255,157,0.15); color: var(--bull); }
  .strat-signal.bear { background: rgba(255,61,90,0.15); color: var(--bear); }
  .strat-signal.neutral { background: rgba(255,204,0,0.15); color: var(--warn); }

  /* MARKET METRICS */
  .metrics-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 8px;
    padding: 0 16px 16px;
  }

  .metric-box {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 4px;
    padding: 12px;
  }

  .metric-label {
    font-size: 9px;
    color: var(--muted);
    text-transform: uppercase;
    letter-spacing: 1px;
    margin-bottom: 6px;
  }

  .metric-value {
    font-family: 'Syne', sans-serif;
    font-size: 18px;
    font-weight: 800;
    line-height: 1;
  }

  .metric-sub {
    font-size: 9px;
    color: var(--muted);
    margin-top: 3px;
  }

  /* LOADER */
  .loader-overlay {
    position: fixed;
    inset: 0;
    background: var(--bg);
    z-index: 1000;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    gap: 20px;
    transition: opacity 0.5s;
  }

  .loader-overlay.hidden { opacity: 0; pointer-events: none; }

  .loader-logo {
    font-family: 'Syne', sans-serif;
    font-size: 48px;
    font-weight: 800;
    letter-spacing: -2px;
    animation: fadeInUp 0.6s ease;
  }

  .loader-logo span { color: var(--accent); }

  .loader-bar {
    width: 200px;
    height: 2px;
    background: var(--border);
    border-radius: 1px;
    overflow: hidden;
  }

  .loader-bar-fill {
    height: 100%;
    background: linear-gradient(90deg, var(--accent), var(--accent2));
    border-radius: 1px;
    animation: loading 1.5s ease forwards;
  }

  @keyframes loading {
    0% { width: 0; }
    100% { width: 100%; }
  }

  .loader-text {
    font-size: 11px;
    color: var(--muted);
    letter-spacing: 3px;
    text-transform: uppercase;
    animation: fadeInUp 0.6s 0.3s both;
  }

  @keyframes fadeInUp {
    from { opacity: 0; transform: translateY(20px); }
    to { opacity: 1; transform: translateY(0); }
  }

  /* STATUS */
  .status-msg {
    font-size: 11px;
    color: var(--muted);
    padding: 8px 0;
    text-align: center;
    animation: pulse-text 2s infinite;
  }

  @keyframes pulse-text {
    0%,100% { opacity: 0.6; }
    50% { opacity: 1; }
  }

  .error-msg {
    font-size: 11px;
    color: var(--bear);
    padding: 8px 0;
    text-align: center;
  }

  /* TOOLTIP */
  .tooltip {
    position: fixed;
    background: var(--bg2);
    border: 1px solid var(--border);
    border-radius: 3px;
    padding: 8px 12px;
    font-size: 10px;
    color: var(--text);
    pointer-events: none;
    z-index: 100;
    display: none;
  }

  .tooltip.visible { display: block; }
  .tooltip-price { font-weight: 700; font-size: 13px; color: var(--accent); }
  .tooltip-time { color: var(--muted); margin-top: 2px; }

  /* REGIME BADGE */
  .regime-badge {
    display: inline-flex;
    align-items: center;
    gap: 6px;
    padding: 4px 10px;
    border-radius: 3px;
    font-size: 10px;
    font-weight: 600;
    text-transform: uppercase;
    letter-spacing: 1px;
  }

  .regime-badge.trending { background: rgba(0,255,157,0.1); color: var(--bull); border: 1px solid rgba(0,255,157,0.3); }
  .regime-badge.ranging { background: rgba(255,204,0,0.1); color: var(--warn); border: 1px solid rgba(255,204,0,0.3); }
  .regime-badge.volatile { background: rgba(255,61,90,0.1); color: var(--bear); border: 1px solid rgba(255,61,90,0.3); }

  /* RR Display */
  .rr-display {
    text-align: center;
    padding: 10px;
    background: var(--bg3);
    border: 1px solid var(--border);
    border-radius: 3px;
    margin-top: 8px;
    font-size: 10px;
    color: var(--muted);
  }

  .rr-val {
    font-family: 'Syne', sans-serif;
    font-size: 24px;
    font-weight: 800;
    color: var(--accent);
    display: block;
  }

  /* Responsive */
  @media (max-width: 768px) {
    .main { grid-template-columns: 1fr; grid-template-rows: 1fr auto; }
    .sidebar { max-height: 50vh; }
    header { padding: 12px 16px; }
    .controls { padding: 10px 16px; gap: 8px; }
  }
</style>
</head>
<body>

<div class="loader-overlay" id="loader">
  <div class="loader-logo">MARKET<span>EDGE</span></div>
  <div class="loader-bar"><div class="loader-bar-fill"></div></div>
  <div class="loader-text">Pure Signal · No Noise · No Lag</div>
</div>

<div class="tooltip" id="tooltip">
  <div class="tooltip-price" id="tt-price">—</div>
  <div class="tooltip-time" id="tt-time">—</div>
</div>

<header>
  <div class="logo">
    <div class="logo-icon">◈</div>
    MARKET<span>EDGE</span>
  </div>
  <div class="header-status">
    <div class="live-dot"></div>
    <span>LIVE DATA</span>
    <span id="last-update">—</span>
    <span id="regime-badge" class="regime-badge ranging">⊙ RANGING</span>
  </div>
</header>

<div class="controls">
  <select id="pair-select">
    <optgroup label="CRYPTO">
      <option value="BTCUSDT">BTC/USDT</option>
      <option value="ETHUSDT">ETH/USDT</option>
      <option value="SOLUSDT">SOL/USDT</option>
      <option value="BNBUSDT">BNB/USDT</option>
      <option value="XRPUSDT">XRP/USDT</option>
    </optgroup>
    <optgroup label="FOREX via BINANCE">
      <option value="EURUSDT">EUR/USD (EURUSDT)</option>
      <option value="XAUUSDT">XAU/USD — GOLD</option>
    </optgroup>
  </select>

  <select id="tf-select">
    <option value="5m">5 min</option>
    <option value="15m" selected>15 min</option>
    <option value="1h">1 hour</option>
    <option value="4h">4 hours</option>
    <option value="1d">Daily</option>
  </select>

  <button class="btn-primary" id="analyze-btn" onclick="loadAndAnalyze()">▶ ANALYZE</button>

  <div class="strat-pills">
    <div class="pill active" data-strat="all">All Strategies</div>
    <div class="pill" data-strat="momentum">Momentum</div>
    <div class="pill" data-strat="mean">Mean Reversion</div>
    <div class="pill" data-strat="volatility">Volatility</div>
    <div class="pill" data-strat="structure">Market Structure</div>
  </div>
</div>

<div class="main">
  <div class="chart-area">
    <div class="chart-header">
      <div>
        <div class="pair-display" id="pair-label">BTC/USDT</div>
        <div style="font-size:10px;color:var(--muted);margin-top:2px" id="tf-label">15M · BINANCE</div>
      </div>
      <div style="text-align:right">
        <div class="price-display" id="current-price">—</div>
        <div class="price-change" id="price-change">—</div>
      </div>
    </div>
    <canvas id="chart"></canvas>
    <div class="signal-bar" id="signal-bar">
      <div class="sig-item"><span>RSI:</span><span class="sig-val neutral" id="sig-rsi">—</span></div>
      <div class="sig-item"><span>ATR:</span><span class="sig-val neutral" id="sig-atr">—</span></div>
      <div class="sig-item"><span>MACD:</span><span class="sig-val neutral" id="sig-macd">—</span></div>
      <div class="sig-item"><span>REGIME:</span><span class="sig-val neutral" id="sig-regime">—</span></div>
      <div class="sig-item"><span>TREND:</span><span class="sig-val neutral" id="sig-trend">—</span></div>
      <div class="sig-item"><span>VWAP DEV:</span><span class="sig-val neutral" id="sig-vwap">—</span></div>
    </div>
  </div>

  <div class="sidebar">
    <div id="signal-container" style="padding:16px 16px 0">
      <div style="font-size:11px;color:var(--muted);text-align:center;padding:40px 0">
        Select a pair and click ANALYZE<br>to receive pure signal intelligence.
      </div>
    </div>

    <div class="strat-section" id="strat-container"></div>

    <div class="metrics-grid" id="metrics-grid">
      <div class="metric-box">
        <div class="metric-label">Volatility (ATR%)</div>
        <div class="metric-value" id="m-atr">—</div>
        <div class="metric-sub" id="m-atr-sub">—</div>
      </div>
      <div class="metric-box">
        <div class="metric-label">Momentum</div>
        <div class="metric-value" id="m-mom">—</div>
        <div class="metric-sub" id="m-mom-sub">—</div>
      </div>
      <div class="metric-box">
        <div class="metric-label">Mean Rev. Score</div>
        <div class="metric-value" id="m-rev">—</div>
        <div class="metric-sub" id="m-rev-sub">—</div>
      </div>
      <div class="metric-box">
        <div class="metric-label">Structure Score</div>
        <div class="metric-value" id="m-str">—</div>
        <div class="metric-sub" id="m-str-sub">—</div>
      </div>
    </div>
  </div>
</div>

<script>
// ─────────────────────────────────────────────────────────────────────────────
//  MARKET EDGE — CORE ENGINE
//  Strategies based on mathematical edge, no retail nonsense.
//
//  1. ADAPTIVE MOMENTUM (EMA Crossover + RSI Filter + Volume Confirmation)
//     - Fast EMA crosses Slow EMA in direction of HTF trend
//     - RSI must not be in extreme territory (avoids fake breakouts)
//     - Volume spike confirms institutional participation
//
//  2. VOLATILITY MEAN REVERSION (Bollinger Band + Keltner Channel Squeeze)
//     - When price compresses (low ATR, BB inside KC = squeeze), explosive move likely
//     - At BB extremes with RSI divergence → fade the move
//     - Exit: opposite BB band or VWAP return
//
//  3. MARKET MICROSTRUCTURE (VWAP + Standard Deviation Bands)
//     - Price below/above VWAP + 2σ is statistically extreme
//     - Reversion to VWAP is the highest probability trade
//     - Used by quant desks, execution algorithms, prop firms
//
//  4. TREND STRENGTH FILTER (ADX + Slope Analysis)
//     - ADX > 25 = trending market → ride momentum
//     - ADX < 20 = ranging → mean revert
//     - Slope of price change confirms or denies
// ─────────────────────────────────────────────────────────────────────────────

let candles = [];
let analysisResult = null;

// ──── BINANCE API ────────────────────────────────────────────────────────────
async function fetchBinanceKlines(symbol, interval, limit = 200) {
  const url = `https://api.binance.com/api/v3/klines?symbol=${symbol}&interval=${interval}&limit=${limit}`;
  const res = await fetch(url);
  if (!res.ok) throw new Error(`Binance API error: ${res.status}`);
  const data = await res.json();
  return data.map(k => ({
    time: k[0],
    open: parseFloat(k[1]),
    high: parseFloat(k[2]),
    low: parseFloat(k[3]),
    close: parseFloat(k[4]),
    volume: parseFloat(k[5]),
  }));
}

// ──── MATH HELPERS ───────────────────────────────────────────────────────────
function ema(arr, period) {
  const k = 2 / (period + 1);
  let result = [];
  let val = arr[0];
  result.push(val);
  for (let i = 1; i < arr.length; i++) {
    val = arr[i] * k + val * (1 - k);
    result.push(val);
  }
  return result;
}

function sma(arr, period) {
  return arr.map((_, i) => {
    if (i < period - 1) return null;
    const slice = arr.slice(i - period + 1, i + 1);
    return slice.reduce((s, v) => s + v, 0) / period;
  });
}

function stddev(arr, period) {
  return arr.map((_, i) => {
    if (i < period - 1) return null;
    const slice = arr.slice(i - period + 1, i + 1);
    const mean = slice.reduce((s, v) => s + v, 0) / period;
    const variance = slice.reduce((s, v) => s + (v - mean) ** 2, 0) / period;
    return Math.sqrt(variance);
  });
}

function rsi(closes, period = 14) {
  let gains = [], losses = [];
  for (let i = 1; i < closes.length; i++) {
    const diff = closes[i] - closes[i - 1];
    gains.push(diff > 0 ? diff : 0);
    losses.push(diff < 0 ? -diff : 0);
  }
  let avgGain = gains.slice(0, period).reduce((a, b) => a + b, 0) / period;
  let avgLoss = losses.slice(0, period).reduce((a, b) => a + b, 0) / period;
  let result = new Array(period).fill(null);
  result.push(100 - 100 / (1 + avgGain / (avgLoss || 0.0001)));
  for (let i = period; i < gains.length; i++) {
    avgGain = (avgGain * (period - 1) + gains[i]) / period;
    avgLoss = (avgLoss * (period - 1) + losses[i]) / period;
    result.push(100 - 100 / (1 + avgGain / (avgLoss || 0.0001)));
  }
  return result;
}

function atr(candles, period = 14) {
  let trs = [0];
  for (let i = 1; i < candles.length; i++) {
    const tr = Math.max(
      candles[i].high - candles[i].low,
      Math.abs(candles[i].high - candles[i - 1].close),
      Math.abs(candles[i].low - candles[i - 1].close)
    );
    trs.push(tr);
  }
  let result = new Array(period).fill(null);
  let val = trs.slice(1, period + 1).reduce((a, b) => a + b, 0) / period;
  result.push(val);
  for (let i = period + 1; i < trs.length; i++) {
    val = (val * (period - 1) + trs[i]) / period;
    result.push(val);
  }
  return result;
}

function adx(candles, period = 14) {
  // Simplified ADX
  let plusDM = [], minusDM = [], tr = [];
  for (let i = 1; i < candles.length; i++) {
    const up = candles[i].high - candles[i - 1].high;
    const dn = candles[i - 1].low - candles[i].low;
    plusDM.push(up > dn && up > 0 ? up : 0);
    minusDM.push(dn > up && dn > 0 ? dn : 0);
    tr.push(Math.max(
      candles[i].high - candles[i].low,
      Math.abs(candles[i].high - candles[i - 1].close),
      Math.abs(candles[i].low - candles[i - 1].close)
    ));
  }
  // Smooth
  let sTR = tr.slice(0, period).reduce((a, b) => a + b, 0);
  let sPDM = plusDM.slice(0, period).reduce((a, b) => a + b, 0);
  let sMDM = minusDM.slice(0, period).reduce((a, b) => a + b, 0);
  let adxVals = [];
  let dx = Math.abs((sPDM / sTR - sMDM / sTR) / (sPDM / sTR + sMDM / sTR + 0.0001)) * 100;
  let adxSmooth = [dx];
  for (let i = period; i < tr.length; i++) {
    sTR = sTR - sTR / period + tr[i];
    sPDM = sPDM - sPDM / period + plusDM[i];
    sMDM = sMDM - sMDM / period + minusDM[i];
    const diP = sPDM / sTR * 100;
    const diM = sMDM / sTR * 100;
    dx = Math.abs(diP - diM) / (diP + diM + 0.0001) * 100;
    adxSmooth.push((adxSmooth[adxSmooth.length - 1] * (period - 1) + dx) / period);
  }
  return new Array(period + 1).fill(null).concat(adxSmooth);
}

function macd(closes, fast = 12, slow = 26, signal = 9) {
  const emaFast = ema(closes, fast);
  const emaSlow = ema(closes, slow);
  const macdLine = emaFast.map((v, i) => v - emaSlow[i]);
  const signalLine = ema(macdLine.slice(slow - 1), signal);
  const padded = new Array(slow - 1).fill(null).concat(signalLine);
  const hist = macdLine.map((v, i) => padded[i] !== null ? v - padded[i] : null);
  return { macdLine, signalLine: padded, hist };
}

function vwap(candles) {
  let cumTPV = 0, cumVol = 0;
  return candles.map(c => {
    const tp = (c.high + c.low + c.close) / 3;
    cumTPV += tp * c.volume;
    cumVol += c.volume;
    return cumTPV / cumVol;
  });
}

function bollingerBands(closes, period = 20, mult = 2) {
  const mid = sma(closes, period);
  const sd = stddev(closes, period);
  const upper = mid.map((m, i) => m !== null ? m + mult * sd[i] : null);
  const lower = mid.map((m, i) => m !== null ? m - mult * sd[i] : null);
  return { upper, mid, lower };
}

function keltnerChannels(candles, period = 20, mult = 1.5) {
  const closes = candles.map(c => c.close);
  const mid = ema(closes, period);
  const atrVals = atr(candles, period);
  const upper = mid.map((m, i) => atrVals[i] !== null ? m + mult * atrVals[i] : null);
  const lower = mid.map((m, i) => atrVals[i] !== null ? m - mult * atrVals[i] : null);
  return { upper, mid, lower };
}

// ──── MARKET REGIME DETECTOR ─────────────────────────────────────────────────
function detectRegime(candles) {
  const closes = candles.map(c => c.close);
  const adxVals = adx(candles, 14);
  const lastADX = adxVals.filter(v => v !== null).at(-1) || 20;

  // ATR% — normalized volatility
  const atrVals = atr(candles, 14);
  const lastATR = atrVals.filter(v => v !== null).at(-1) || 0;
  const lastClose = closes.at(-1);
  const atrPct = (lastATR / lastClose) * 100;

  let regime;
  if (lastADX > 28) regime = 'trending';
  else if (atrPct > 2.5) regime = 'volatile';
  else regime = 'ranging';

  return { regime, adx: lastADX, atrPct };
}

// ──── STRATEGY 1: ADAPTIVE MOMENTUM ─────────────────────────────────────────
// Uses EMA8/21/55 cascade + RSI 45-55 neutral zone filter + volume confirmation
function strategyMomentum(candles) {
  const closes = candles.map(c => c.close);
  const vols = candles.map(c => c.volume);

  const ema8 = ema(closes, 8);
  const ema21 = ema(closes, 21);
  const ema55 = ema(closes, 55);
  const rsiVals = rsi(closes, 14);
  const volSma = sma(vols, 20);

  const i = closes.length - 1;
  const lastRSI = rsiVals[i];
  const volRatio = vols[i] / (volSma[i] || 1);

  // EMA alignment
  const bullAlign = ema8[i] > ema21[i] && ema21[i] > ema55[i];
  const bearAlign = ema8[i] < ema21[i] && ema21[i] < ema55[i];

  // Recent cross check
  const prevBullAlign = ema8[i-1] > ema21[i-1] && ema21[i-1] > ema55[i-1];
  const recentCross = bullAlign !== prevBullAlign || bearAlign !== prevBullAlign;

  // RSI not overbought/oversold for entry
  const rsiOK_long = lastRSI > 45 && lastRSI < 70;
  const rsiOK_short = lastRSI < 55 && lastRSI > 30;
  const volOK = volRatio > 1.2;

  let signal = 'NEUTRAL', confidence = 0, reason = '';

  if (bullAlign && rsiOK_long) {
    signal = 'LONG';
    confidence = 60 + (volOK ? 20 : 0) + Math.min(20, (lastRSI - 45) / 25 * 20);
    reason = `EMA cascade bullish · RSI ${lastRSI.toFixed(0)} · Vol ×${volRatio.toFixed(1)}`;
  } else if (bearAlign && rsiOK_short) {
    signal = 'SHORT';
    confidence = 60 + (volOK ? 20 : 0) + Math.min(20, (55 - lastRSI) / 25 * 20);
    reason = `EMA cascade bearish · RSI ${lastRSI.toFixed(0)} · Vol ×${volRatio.toFixed(1)}`;
  } else {
    reason = `No clean EMA alignment · RSI ${lastRSI ? lastRSI.toFixed(0) : '—'}`;
  }

  return {
    name: 'Adaptive Momentum',
    icon: '⟁',
    iconBg: '#0d2040',
    desc: 'EMA8/21/55 cascade + RSI filter + volume confirmation',
    signal, confidence: Math.min(95, confidence),
    reason,
    entry: closes[i],
    ema8: ema8[i], ema21: ema21[i], ema55: ema55[i],
    rsi: lastRSI
  };
}

// ──── STRATEGY 2: VOLATILITY COMPRESSION / SQUEEZE ───────────────────────────
// Bollinger inside Keltner = volatility squeeze → explosive move follows
// Direction: momentum oscillator (MACD histogram slope)
function strategyVolatilitySqueeze(candles) {
  const closes = candles.map(c => c.close);
  const bb = bollingerBands(closes, 20, 2);
  const kc = keltnerChannels(candles, 20, 1.5);
  const { hist } = macd(closes, 12, 26, 9);

  const i = closes.length - 1;

  // Squeeze = BB inside KC
  const squeezed = bb.upper[i] < kc.upper[i] && bb.lower[i] > kc.lower[i];
  // Pre-squeeze: BB just expanded out of KC → fire
  const prevSqueezed = bb.upper[i-3] < kc.upper[i-3] && bb.lower[i-3] > kc.lower[i-3];
  const fired = prevSqueezed && !squeezed;

  const macdHist = hist[i];
  const macdHistPrev = hist[i - 1];
  const macdSlope = macdHist !== null && macdHistPrev !== null ? macdHist - macdHistPrev : 0;

  let signal = 'NEUTRAL', confidence = 0, reason = '';

  if (squeezed) {
    signal = 'NEUTRAL';
    confidence = 50;
    reason = `SQUEEZE ACTIVE — coiling · wait for expansion`;
  } else if (fired) {
    signal = macdSlope > 0 ? 'LONG' : 'SHORT';
    confidence = 75 + Math.min(15, Math.abs(macdSlope / (closes[i] * 0.0001)));
    reason = `Squeeze fired ${macdSlope > 0 ? 'upward' : 'downward'} · MACD hist slope ${macdSlope > 0 ? '+' : ''}${macdSlope.toFixed(4)}`;
  } else {
    reason = `No squeeze present · Normal volatility`;
  }

  return {
    name: 'Volatility Squeeze',
    icon: '⟐',
    iconBg: '#1a1020',
    desc: 'Bollinger/Keltner squeeze breakout — predicts explosive moves',
    signal, confidence: Math.min(95, confidence),
    reason, entry: closes[i],
    squeezed, fired, macdSlope
  };
}

// ──── STRATEGY 3: VWAP STATISTICAL REVERSION ─────────────────────────────────
// Price >2σ from VWAP = statistically overextended → revert to mean
// Used by prop desks, algo execution, HFT — the actual flow
function strategyVWAPReversion(candles) {
  const closes = candles.map(c => c.close);
  const vwapLine = vwap(candles);
  const diffs = closes.map((c, i) => c - vwapLine[i]);
  const diffStd = stddev(diffs, 20);

  const i = closes.length - 1;
  const dev = diffs[i] / (diffStd[i] || 1); // normalized z-score
  const lastClose = closes[i];
  const lastVWAP = vwapLine[i];
  const pctFromVWAP = ((lastClose - lastVWAP) / lastVWAP) * 100;

  let signal = 'NEUTRAL', confidence = 0, reason = '';

  if (dev > 1.8) {
    signal = 'SHORT';
    confidence = 55 + Math.min(35, (dev - 1.8) * 20);
    reason = `Price ${pctFromVWAP.toFixed(2)}% above VWAP · Z-score ${dev.toFixed(2)}σ · Revert down`;
  } else if (dev < -1.8) {
    signal = 'LONG';
    confidence = 55 + Math.min(35, (-dev - 1.8) * 20);
    reason = `Price ${Math.abs(pctFromVWAP).toFixed(2)}% below VWAP · Z-score ${dev.toFixed(2)}σ · Revert up`;
  } else {
    reason = `At ${pctFromVWAP.toFixed(2)}% from VWAP · Z: ${dev.toFixed(2)}σ — no edge`;
  }

  return {
    name: 'VWAP Statistical Reversion',
    icon: '⊙',
    iconBg: '#001a20',
    desc: 'Z-score deviation from VWAP — quantitative mean reversion edge',
    signal, confidence: Math.min(95, confidence),
    reason, entry: lastClose, vwapLevel: lastVWAP, zScore: dev
  };
}

// ──── STRATEGY 4: MARKET STRUCTURE MOMENTUM (Higher Highs / Higher Lows) ─────
// Pure price structure — no indicators. Uses swing points.
// HH + HL = confirmed uptrend. LH + LL = confirmed downtrend.
// With momentum divergence flip detection.
function strategyMarketStructure(candles) {
  const closes = candles.map(c => c.close);
  const highs = candles.map(c => c.high);
  const lows = candles.map(c => c.low);
  const n = candles.length;

  // Detect swing highs/lows using 5-bar pivot
  function findPivots(arr, type, lookback = 5) {
    let pivots = [];
    for (let i = lookback; i < arr.length - lookback; i++) {
      const slice = arr.slice(i - lookback, i + lookback + 1);
      const center = arr[i];
      if (type === 'high' && center === Math.max(...slice)) pivots.push({ idx: i, val: center });
      if (type === 'low' && center === Math.min(...slice)) pivots.push({ idx: i, val: center });
    }
    return pivots;
  }

  const swingHighs = findPivots(highs, 'high', 4);
  const swingLows = findPivots(lows, 'low', 4);

  // Last 3 swings
  const lastHighs = swingHighs.slice(-3).map(p => p.val);
  const lastLows = swingLows.slice(-3).map(p => p.val);

  let bullStruct = false, bearStruct = false;
  let structScore = 0;

  if (lastHighs.length >= 2 && lastLows.length >= 2) {
    const hhPattern = lastHighs[1] > lastHighs[0];
    const hlPattern = lastLows[1] > lastLows[0];
    const lhPattern = lastHighs[1] < lastHighs[0];
    const llPattern = lastLows[1] < lastLows[0];

    bullStruct = hhPattern && hlPattern;
    bearStruct = lhPattern && llPattern;

    if (bullStruct) structScore = hhPattern && hlPattern ? 80 : 60;
    if (bearStruct) structScore = lhPattern && llPattern ? 80 : 60;
  }

  // RSI divergence check for structure weakness
  const rsiVals = rsi(closes, 14);
  const lastRSI = rsiVals[n - 1];
  const rsi5 = rsiVals[n - 5];
  const divergence = (closes[n - 1] > closes[n - 5] && lastRSI < rsi5) ||
                     (closes[n - 1] < closes[n - 5] && lastRSI > rsi5);

  let signal = 'NEUTRAL', confidence = 0, reason = '';

  if (bullStruct && !divergence) {
    signal = 'LONG';
    confidence = structScore;
    reason = `HH/HL structure confirmed · No divergence · Trend intact`;
  } else if (bearStruct && !divergence) {
    signal = 'SHORT';
    confidence = structScore;
    reason = `LH/LL structure confirmed · No divergence · Trend intact`;
  } else if (divergence) {
    reason = `Structure ${bullStruct ? 'bullish' : bearStruct ? 'bearish' : 'undefined'} but RSI diverging — caution`;
    signal = 'NEUTRAL';
    confidence = 30;
  } else {
    reason = `No clear HH/HL or LH/LL pattern — mixed structure`;
  }

  return {
    name: 'Market Structure',
    icon: '△',
    iconBg: '#0a1a10',
    desc: 'Swing pivot HH/HL structure + RSI divergence filter',
    signal, confidence: Math.min(95, confidence),
    reason, entry: closes[n - 1],
    bullStruct, bearStruct, divergence, swingHighs, swingLows
  };
}

// ──── CONSENSUS ENGINE ───────────────────────────────────────────────────────
function computeConsensus(strategies, regime) {
  let longVotes = 0, shortVotes = 0, totalConf = 0;
  let weightedLong = 0, weightedShort = 0;

  // Weights: adjust per regime
  const weights = {
    'Adaptive Momentum':          regime === 'trending' ? 1.4 : 0.8,
    'Volatility Squeeze':         regime === 'volatile'  ? 1.3 : 1.0,
    'VWAP Statistical Reversion': regime === 'ranging'   ? 1.4 : 0.9,
    'Market Structure':           1.1,
  };

  strategies.forEach(s => {
    const w = weights[s.name] || 1;
    if (s.signal === 'LONG') { longVotes++; weightedLong += s.confidence * w; }
    if (s.signal === 'SHORT') { shortVotes++; weightedShort += s.confidence * w; }
  });

  const totalVotes = longVotes + shortVotes;
  if (totalVotes === 0) return { signal: 'NEUTRAL', confidence: 0 };

  if (weightedLong > weightedShort * 1.2) {
    return { signal: 'LONG', confidence: Math.min(95, weightedLong / (longVotes * 1.3)) };
  } else if (weightedShort > weightedLong * 1.2) {
    return { signal: 'SHORT', confidence: Math.min(95, weightedShort / (shortVotes * 1.3)) };
  }
  return { signal: 'NEUTRAL', confidence: 30 };
}

// ──── RISK LEVELS ────────────────────────────────────────────────────────────
function computeLevels(candles, signal, atrVal) {
  const close = candles.at(-1).close;
  const atr14 = atrVal || (close * 0.005);

  let entry = close;
  let sl, tp1, tp2;

  if (signal === 'LONG') {
    sl   = +(entry - 1.5 * atr14).toPrecision(6);
    tp1  = +(entry + 2.0 * atr14).toPrecision(6);
    tp2  = +(entry + 3.5 * atr14).toPrecision(6);
  } else if (signal === 'SHORT') {
    sl   = +(entry + 1.5 * atr14).toPrecision(6);
    tp1  = +(entry - 2.0 * atr14).toPrecision(6);
    tp2  = +(entry - 3.5 * atr14).toPrecision(6);
  } else {
    return null;
  }
  const rr = Math.abs((tp1 - entry) / (sl - entry));
  return { entry: +entry.toPrecision(6), sl, tp1, tp2, rr };
}

// ──── CHART RENDERER ─────────────────────────────────────────────────────────
function renderChart(candles, strategies, analysis) {
  const canvas = document.getElementById('chart');
  const ctx = canvas.getContext('2d');
  const dpr = window.devicePixelRatio || 1;

  const rect = canvas.parentElement.getBoundingClientRect();
  const W = rect.width;
  const H = canvas.parentElement.clientHeight - canvas.offsetTop - 60;

  canvas.width = W * dpr;
  canvas.height = H * dpr;
  canvas.style.width = W + 'px';
  canvas.style.height = H + 'px';
  ctx.scale(dpr, dpr);

  ctx.clearRect(0, 0, W, H);

  const pad = { left: 10, right: 70, top: 15, bottom: 30 };
  const cW = W - pad.left - pad.right;
  const cH = H - pad.top - pad.bottom;

  // Data range
  const visible = candles.slice(-120);
  const allVals = visible.flatMap(c => [c.high, c.low]);
  let minP = Math.min(...allVals), maxP = Math.max(...allVals);

  // Include indicator values
  const closes = candles.map(c => c.close);
  const ema8 = ema(closes, 8);
  const ema21 = ema(closes, 21);
  const ema55 = ema(closes, 55);
  const vwapLine = vwap(candles);
  const bb = bollingerBands(closes, 20, 2);

  const indSlice = (arr) => arr.slice(-120).filter(v => v !== null && !isNaN(v));
  const allInds = [...indSlice(ema8), ...indSlice(ema21), ...indSlice(ema55),
                   ...indSlice(vwapLine), ...indSlice(bb.upper), ...indSlice(bb.lower)];
  if (allInds.length) {
    minP = Math.min(minP, ...allInds);
    maxP = Math.max(maxP, ...allInds);
  }

  const pad2 = (maxP - minP) * 0.05;
  minP -= pad2; maxP += pad2;

  const xScale = (i) => pad.left + (i / (visible.length - 1)) * cW;
  const yScale = (p) => pad.top + cH - ((p - minP) / (maxP - minP)) * cH;

  const candleW = Math.max(2, (cW / visible.length) * 0.7);

  // ── Grid
  ctx.strokeStyle = 'rgba(26,45,69,0.5)';
  ctx.lineWidth = 0.5;
  for (let g = 0; g <= 5; g++) {
    const y = pad.top + (g / 5) * cH;
    ctx.beginPath(); ctx.moveTo(pad.left, y); ctx.lineTo(W - pad.right, y); ctx.stroke();
    const price = maxP - (g / 5) * (maxP - minP);
    ctx.fillStyle = '#4a6a8a';
    ctx.font = '9px JetBrains Mono';
    ctx.textAlign = 'left';
    ctx.fillText(formatPrice(price), W - pad.right + 4, y + 3);
  }

  // ── Bollinger Bands fill
  ctx.beginPath();
  const bbUpper = bb.upper.slice(-120);
  const bbLower = bb.lower.slice(-120);
  const startI = bbUpper.findIndex(v => v !== null);
  if (startI >= 0) {
    ctx.moveTo(xScale(startI), yScale(bbUpper[startI]));
    for (let i = startI; i < bbUpper.length; i++) {
      if (bbUpper[i] !== null) ctx.lineTo(xScale(i), yScale(bbUpper[i]));
    }
    for (let i = bbLower.length - 1; i >= startI; i--) {
      if (bbLower[i] !== null) ctx.lineTo(xScale(i), yScale(bbLower[i]));
    }
    ctx.closePath();
    ctx.fillStyle = 'rgba(0,212,255,0.04)';
    ctx.fill();
  }

  function drawLine(arr, color, width = 1, dash = []) {
    const sl = arr.slice(-120);
    ctx.beginPath();
    ctx.strokeStyle = color;
    ctx.lineWidth = width;
    ctx.setLineDash(dash);
    let started = false;
    sl.forEach((v, i) => {
      if (v === null || isNaN(v)) return;
      if (!started) { ctx.moveTo(xScale(i), yScale(v)); started = true; }
      else ctx.lineTo(xScale(i), yScale(v));
    });
    ctx.stroke();
    ctx.setLineDash([]);
  }

  // Draw indicators
  drawLine(bb.upper, 'rgba(0,212,255,0.25)', 0.8, [3, 3]);
  drawLine(bb.lower, 'rgba(0,212,255,0.25)', 0.8, [3, 3]);
  drawLine(bb.mid, 'rgba(0,212,255,0.2)', 0.6);
  drawLine(vwapLine, 'rgba(255,204,0,0.6)', 1.5, [4, 2]);
  drawLine(ema55, 'rgba(255,107,53,0.5)', 1.2);
  drawLine(ema21, 'rgba(0,255,157,0.5)', 1.0);
  drawLine(ema8, 'rgba(255,255,255,0.3)', 0.8);

  // ── Candles
  visible.forEach((c, i) => {
    const x = xScale(i);
    const bull = c.close >= c.open;
    const color = bull ? '#00ff9d' : '#ff3d5a';
    const bodyTop = yScale(Math.max(c.open, c.close));
    const bodyBot = yScale(Math.min(c.open, c.close));
    const bodyH = Math.max(1, bodyBot - bodyTop);

    // Wick
    ctx.strokeStyle = color;
    ctx.lineWidth = 1;
    ctx.beginPath();
    ctx.moveTo(x, yScale(c.high));
    ctx.lineTo(x, yScale(c.low));
    ctx.stroke();

    // Body
    ctx.fillStyle = bull ? 'rgba(0,255,157,0.8)' : 'rgba(255,61,90,0.8)';
    ctx.fillRect(x - candleW / 2, bodyTop, candleW, bodyH);
  });

  // ── Draw signal markers
  const levels = analysis.levels;
  if (levels) {
    const lastX = xScale(visible.length - 1);
    const entryY = yScale(levels.entry);
    const slY = yScale(levels.sl);
    const tp1Y = yScale(levels.tp1);

    // Entry line
    ctx.setLineDash([5, 3]);
    ctx.strokeStyle = 'rgba(0,212,255,0.7)';
    ctx.lineWidth = 1;
    ctx.beginPath();
    ctx.moveTo(pad.left, entryY);
    ctx.lineTo(W - pad.right, entryY);
    ctx.stroke();

    ctx.strokeStyle = 'rgba(255,61,90,0.5)';
    ctx.beginPath();
    ctx.moveTo(pad.left, slY);
    ctx.lineTo(W - pad.right, slY);
    ctx.stroke();

    ctx.strokeStyle = 'rgba(0,255,157,0.5)';
    ctx.beginPath();
    ctx.moveTo(pad.left, tp1Y);
    ctx.lineTo(W - pad.right, tp1Y);
    ctx.stroke();

    ctx.setLineDash([]);

    // Labels on right
    ctx.font = 'bold 9px JetBrains Mono';
    ctx.textAlign = 'right';
    ctx.fillStyle = 'rgba(0,212,255,0.9)';
    ctx.fillText(`ENTRY ${formatPrice(levels.entry)}`, W - 2, entryY - 3);
    ctx.fillStyle = 'rgba(255,61,90,0.9)';
    ctx.fillText(`SL ${formatPrice(levels.sl)}`, W - 2, slY + 10);
    ctx.fillStyle = 'rgba(0,255,157,0.9)';
    ctx.fillText(`TP ${formatPrice(levels.tp1)}`, W - 2, tp1Y - 3);

    // Arrow on last candle
    const arrow = analysis.consensus.signal === 'LONG' ? '▲' : '▼';
    const arrowColor = analysis.consensus.signal === 'LONG' ? '#00ff9d' : '#ff3d5a';
    ctx.font = '16px sans-serif';
    ctx.fillStyle = arrowColor;
    ctx.textAlign = 'center';
    ctx.fillText(arrow, lastX, analysis.consensus.signal === 'LONG' ? entryY + 20 : entryY - 8);
  }

  // Swing pivot dots
  const msStrat = strategies.find(s => s.name === 'Market Structure');
  if (msStrat && msStrat.swingHighs && msStrat.swingLows) {
    const startIdx = candles.length - 120;
    msStrat.swingHighs.filter(p => p.idx >= startIdx).forEach(p => {
      const x = xScale(p.idx - startIdx);
      const y = yScale(p.val);
      ctx.beginPath();
      ctx.arc(x, y, 3, 0, Math.PI * 2);
      ctx.fillStyle = 'rgba(255,204,0,0.7)';
      ctx.fill();
    });
    msStrat.swingLows.filter(p => p.idx >= startIdx).forEach(p => {
      const x = xScale(p.idx - startIdx);
      const y = yScale(p.val);
      ctx.beginPath();
      ctx.arc(x, y, 3, 0, Math.PI * 2);
      ctx.fillStyle = 'rgba(255,107,53,0.7)';
      ctx.fill();
    });
  }

  // Tooltip interaction
  canvas._chartData = { visible, xScale, yScale, pad, cW, cH };
}

// ──── FORMAT HELPERS ─────────────────────────────────────────────────────────
function formatPrice(p) {
  if (p === null || isNaN(p)) return '—';
  if (p > 1000) return p.toLocaleString('en', { maximumFractionDigits: 2 });
  if (p > 1) return p.toFixed(4);
  return p.toFixed(6);
}

function formatTime(ts) {
  return new Date(ts).toLocaleString('en', { month: 'short', day: 'numeric', hour: '2-digit', minute: '2-digit' });
}

// ──── TOOLTIP ───────────────────────────────────────────────────────────────
const canvas = document.getElementById('chart');
const tooltip = document.getElementById('tooltip');

canvas.addEventListener('mousemove', (e) => {
  const data = canvas._chartData;
  if (!data || !candles.length) return;
  const rect = canvas.getBoundingClientRect();
  const mx = e.clientX - rect.left;
  const { visible, xScale, pad, cW } = data;
  const idx = Math.round((mx - pad.left) / cW * (visible.length - 1));
  if (idx < 0 || idx >= visible.length) { tooltip.classList.remove('visible'); return; }
  const c = visible[idx];
  document.getElementById('tt-price').textContent = `O:${formatPrice(c.open)} H:${formatPrice(c.high)} L:${formatPrice(c.low)} C:${formatPrice(c.close)}`;
  document.getElementById('tt-time').textContent = formatTime(c.time);
  tooltip.style.left = (e.clientX + 12) + 'px';
  tooltip.style.top = (e.clientY - 30) + 'px';
  tooltip.classList.add('visible');
});
canvas.addEventListener('mouseleave', () => tooltip.classList.remove('visible'));

// ──── UI UPDATERS ────────────────────────────────────────────────────────────
function updateSignalCard(consensus, levels) {
  const container = document.getElementById('signal-container');
  const dir = consensus.signal;
  const conf = consensus.confidence;
  const rr = levels ? levels.rr.toFixed(2) : null;

  let levelsHTML = '';
  if (levels) {
    levelsHTML = `
      <div class="signal-levels">
        <div class="level-box">
          <div class="level-label">Entry</div>
          <div class="level-price entry">${formatPrice(levels.entry)}</div>
        </div>
        <div class="level-box">
          <div class="level-label">Stop Loss</div>
          <div class="level-price sl">${formatPrice(levels.sl)}</div>
        </div>
        <div class="level-box">
          <div class="level-label">Target 1</div>
          <div class="level-price tp">${formatPrice(levels.tp1)}</div>
        </div>
      </div>
      <div class="rr-display">
        <span class="rr-val">${rr}:1</span>
        Risk / Reward Ratio
      </div>`;
  }

  container.innerHTML = `
    <div class="signal-card ${dir}">
      <div class="signal-title">Consensus Signal</div>
      <div class="signal-direction ${dir}">${dir === 'LONG' ? '↑ LONG' : dir === 'SHORT' ? '↓ SHORT' : '⊙ NEUTRAL'}</div>
      <div class="signal-conf">Confidence: ${conf.toFixed(0)}%</div>
      <div class="conf-bar"><div class="conf-fill ${dir}" style="width:${conf}%"></div></div>
      ${levelsHTML}
    </div>`;
}

function updateStratCards(strategies) {
  const container = document.getElementById('strat-container');
  container.innerHTML = `<div class="strat-header">Strategy Breakdown</div>`;
  strategies.forEach(s => {
    const cls = s.signal === 'LONG' ? 'bull' : s.signal === 'SHORT' ? 'bear' : 'neutral';
    container.innerHTML += `
      <div class="strat-card">
        <div class="strat-icon" style="background:${s.iconBg}">${s.icon}</div>
        <div class="strat-info">
          <div class="strat-name">${s.name}</div>
          <div class="strat-desc">${s.reason || s.desc}</div>
        </div>
        <div class="strat-signal ${cls}">${s.signal}</div>
      </div>`;
  });
}

function updateMetrics(candles, regimeData) {
  const closes = candles.map(c => c.close);
  const atrVals = atr(candles, 14);
  const lastATR = atrVals.filter(v => v !== null).at(-1);
  const lastClose = closes.at(-1);
  const rsiVals = rsi(closes, 14);
  const lastRSI = rsiVals.filter(v => v !== null).at(-1);
  const { macdLine, signalLine } = macd(closes, 12, 26, 9);
  const macdVal = macdLine.at(-1);
  const sigVal = signalLine.filter(v => v !== null).at(-1);
  const vwapLine = vwap(candles);
  const vwapDev = ((lastClose - vwapLine.at(-1)) / vwapLine.at(-1) * 100);

  // RSI
  const rsiEl = document.getElementById('sig-rsi');
  rsiEl.textContent = lastRSI ? lastRSI.toFixed(1) : '—';
  rsiEl.className = 'sig-val ' + (lastRSI > 60 ? 'bull' : lastRSI < 40 ? 'bear' : 'neutral');

  // ATR
  document.getElementById('sig-atr').textContent = lastATR ? formatPrice(lastATR) : '—';

  // MACD
  const macdEl = document.getElementById('sig-macd');
  const macdDir = macdVal > sigVal ? 'bull' : 'bear';
  macdEl.textContent = macdVal !== null ? (macdVal > 0 ? '+' : '') + macdVal.toFixed(4) : '—';
  macdEl.className = 'sig-val ' + macdDir;

  // Regime
  const regEl = document.getElementById('sig-regime');
  regEl.textContent = regimeData.regime.toUpperCase();
  regEl.className = 'sig-val ' + (regimeData.regime === 'trending' ? 'bull' : regimeData.regime === 'volatile' ? 'bear' : 'neutral');

  // Trend
  const ema8v = ema(closes, 8).at(-1);
  const ema21v = ema(closes, 21).at(-1);
  const trendEl = document.getElementById('sig-trend');
  trendEl.textContent = ema8v > ema21v ? 'BULL' : 'BEAR';
  trendEl.className = 'sig-val ' + (ema8v > ema21v ? 'bull' : 'bear');

  // VWAP
  const vwapEl = document.getElementById('sig-vwap');
  vwapEl.textContent = (vwapDev > 0 ? '+' : '') + vwapDev.toFixed(2) + '%';
  vwapEl.className = 'sig-val ' + (Math.abs(vwapDev) > 1.5 ? (vwapDev > 0 ? 'bear' : 'bull') : 'neutral');

  // Metric boxes
  const atrPct = (lastATR / lastClose * 100);
  document.getElementById('m-atr').textContent = atrPct.toFixed(2) + '%';
  document.getElementById('m-atr').style.color = atrPct > 2 ? '#ff3d5a' : atrPct > 1 ? '#ffcc00' : '#00ff9d';
  document.getElementById('m-atr-sub').textContent = regimeData.regime;

  const momentum20 = ((lastClose / closes.at(-21) - 1) * 100);
  const momEl = document.getElementById('m-mom');
  momEl.textContent = (momentum20 > 0 ? '+' : '') + momentum20.toFixed(2) + '%';
  momEl.style.color = momentum20 > 0 ? '#00ff9d' : '#ff3d5a';
  document.getElementById('m-mom-sub').textContent = '20-candle ROC';

  const revScore = Math.max(0, 100 - Math.abs(vwapDev) * 15);
  document.getElementById('m-rev').textContent = revScore.toFixed(0);
  document.getElementById('m-rev').style.color = revScore > 70 ? '#00ff9d' : revScore > 40 ? '#ffcc00' : '#ff3d5a';
  document.getElementById('m-rev-sub').textContent = 'VWAP proximity';

  document.getElementById('m-str').textContent = regimeData.adx.toFixed(1);
  document.getElementById('m-str').style.color = regimeData.adx > 25 ? '#00ff9d' : regimeData.adx > 15 ? '#ffcc00' : '#ff3d5a';
  document.getElementById('m-str-sub').textContent = 'ADX trend strength';

  // Regime badge
  const badge = document.getElementById('regime-badge');
  badge.className = `regime-badge ${regimeData.regime}`;
  badge.textContent = `⊙ ${regimeData.regime.toUpperCase()}`;
}

// ──── MAIN ANALYSIS FLOW ─────────────────────────────────────────────────────
async function loadAndAnalyze() {
  const btn = document.getElementById('analyze-btn');
  btn.disabled = true;
  btn.textContent = '⌛ LOADING...';

  const symbol = document.getElementById('pair-select').value;
  const interval = document.getElementById('tf-select').value;

  const pairLabels = {
    BTCUSDT: 'BTC/USDT', ETHUSDT: 'ETH/USDT', SOLUSDT: 'SOL/USDT',
    BNBUSDT: 'BNB/USDT', XRPUSDT: 'XRP/USDT', EURUSDT: 'EUR/USD', XAUUSDT: 'XAU/USD — GOLD'
  };

  document.getElementById('pair-label').textContent = pairLabels[symbol] || symbol;
  document.getElementById('tf-label').textContent = `${interval.toUpperCase()} · BINANCE`;

  try {
    candles = await fetchBinanceKlines(symbol, interval, 300);

    const closes = candles.map(c => c.close);
    const last = closes.at(-1);
    const prev = closes.at(-2);
    const change = ((last - prev) / prev * 100);

    document.getElementById('current-price').textContent = formatPrice(last);
    const chEl = document.getElementById('price-change');
    chEl.textContent = `${change >= 0 ? '▲' : '▼'} ${Math.abs(change).toFixed(3)}%`;
    chEl.className = 'price-change ' + (change >= 0 ? 'up' : 'down');

    document.getElementById('last-update').textContent = new Date().toLocaleTimeString();

    // Run all strategies
    const strategies = [
      strategyMomentum(candles),
      strategyVolatilitySqueeze(candles),
      strategyVWAPReversion(candles),
      strategyMarketStructure(candles),
    ];

    // Detect regime
    const regimeData = detectRegime(candles);

    // Consensus
    const consensus = computeConsensus(strategies, regimeData.regime);

    // Risk levels
    const atrVals = atr(candles, 14);
    const lastATR = atrVals.filter(v => v !== null).at(-1);
    const levels = computeLevels(candles, consensus.signal, lastATR);

    analysisResult = { consensus, strategies, levels, regimeData };

    // Render chart
    renderChart(candles, strategies, analysisResult);

    // Update UI
    updateSignalCard(consensus, levels);
    updateStratCards(strategies);
    updateMetrics(candles, regimeData);

  } catch (err) {
    console.error(err);
    document.getElementById('signal-container').innerHTML = `
      <div class="error-msg">⚠ Error: ${err.message}<br><small>Check CORS / network / symbol availability</small></div>`;
  }

  btn.disabled = false;
  btn.textContent = '▶ ANALYZE';
}

// ──── PILL FILTER ────────────────────────────────────────────────────────────
document.querySelectorAll('.pill').forEach(p => {
  p.addEventListener('click', () => {
    document.querySelectorAll('.pill').forEach(x => x.classList.remove('active'));
    p.classList.add('active');
    // Re-filter strategy cards (future: filter by tag)
    if (analysisResult) updateStratCards(analysisResult.strategies);
  });
});

// ──── RESIZE ────────────────────────────────────────────────────────────────
let resizeTimer;
window.addEventListener('resize', () => {
  clearTimeout(resizeTimer);
  resizeTimer = setTimeout(() => {
    if (candles.length && analysisResult) {
      renderChart(candles, analysisResult.strategies, analysisResult);
    }
  }, 200);
});

// ──── BOOT ───────────────────────────────────────────────────────────────────
setTimeout(() => {
  document.getElementById('loader').classList.add('hidden');
  loadAndAnalyze();
}, 1800);
</script>
</body>
</html>
