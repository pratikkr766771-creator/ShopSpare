import { useState, useEffect } from "react";
import {
  LineChart, Line, XAxis, YAxis, Tooltip,
  ResponsiveContainer, CartesianGrid
} from "recharts";
import {
  Search, Bell, Heart, Star, Filter,
  ArrowRight, X, Package, AlertCircle,
  Zap, Shield, Clock, TrendingDown,
  ShoppingCart, User, ChevronDown,
  CheckCircle, BarChart2, Home
} from "lucide-react";

/* ─────────────────────────────────────────
   GLOBAL STYLES
───────────────────────────────────────── */
const GlobalStyles = () => (
  <style>{`
    @import url('https://fonts.googleapis.com/css2?family=DM+Serif+Display:ital@0;1&family=DM+Sans:opsz,wght@9..40,300;9..40,400;9..40,500;9..40,600&display=swap');

    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
    html { scroll-behavior: smooth; }
    body { font-family: 'DM Sans', sans-serif; background: #f7f6f3; color: #1a1a1a; }
    ::-webkit-scrollbar { width: 5px; }
    ::-webkit-scrollbar-track { background: #f7f6f3; }
    ::-webkit-scrollbar-thumb { background: #ddd; border-radius: 4px; }

    :root {
      --bg: #f7f6f3;
      --surface: #ffffff;
      --border: #e6e2db;
      --text: #1a1a1a;
      --muted: #847e76;
      --accent: #c0392b;
      --accent-light: #fdf0ee;
      --navy: #1c2b4a;
      --navy-light: #eef1f7;
      --green: #217a4f;
      --green-light: #eaf5ef;
      --amber: #b45309;
      --amber-light: #fef3c7;
      --tag-bg: #f0ece6;
      --radius: 14px;
    }

    .serif { font-family: 'DM Serif Display', serif; }

    @keyframes fadeUp {
      from { opacity:0; transform:translateY(20px); }
      to   { opacity:1; transform:translateY(0); }
    }
    @keyframes fadeIn {
      from { opacity:0; } to { opacity:1; }
    }
    @keyframes scaleIn {
      from { opacity:0; transform:scale(.97); }
      to   { opacity:1; transform:scale(1); }
    }

    .anim-1 { animation: fadeUp .45s .05s ease both; }
    .anim-2 { animation: fadeUp .45s .15s ease both; }
    .anim-3 { animation: fadeUp .45s .25s ease both; }
    .anim-4 { animation: fadeUp .45s .35s ease both; }
    .anim-5 { animation: fadeUp .45s .45s ease both; }
    .fade-in { animation: fadeIn .35s ease both; }
    .scale-in { animation: scaleIn .35s ease both; }

    /* ── NAV ── */
    .nav {
      position: sticky; top: 0; z-index: 200;
      background: rgba(247,246,243,.93);
      backdrop-filter: blur(14px);
      border-bottom: 1px solid var(--border);
      height: 60px;
      display: flex; align-items: center; justify-content: space-between;
      padding: 0 48px;
    }
    .nav-logo {
      display: flex; align-items: center; gap: 9px;
      cursor: pointer; user-select: none;
    }
    .nav-logo-box {
      width: 32px; height: 32px; background: var(--navy);
      border-radius: 8px; display: flex; align-items: center; justify-content: center;
    }
    .nav-tabs { display: flex; gap: 2px; }
    .nav-tab {
      padding: 6px 14px; border-radius: 8px; border: none;
      background: transparent; font-family: 'DM Sans', sans-serif;
      font-size: 13.5px; font-weight: 500; color: var(--muted);
      cursor: pointer; transition: all .15s; display: flex; align-items: center; gap: 5px;
    }
    .nav-tab:hover { background: var(--tag-bg); color: var(--text); }
    .nav-tab.active { background: var(--navy-light); color: var(--navy); }
    .nav-right { display: flex; align-items: center; gap: 10px; }

    /* ── BUTTONS ── */
    .btn {
      display: inline-flex; align-items: center; gap: 6px;
      padding: 10px 20px; border-radius: 10px; font-family: 'DM Sans', sans-serif;
      font-size: 14px; font-weight: 500; cursor: pointer; border: none;
      transition: all .18s; white-space: nowrap;
    }
    .btn-navy { background: var(--navy); color: #fff; }
    .btn-navy:hover { background: #243660; transform: translateY(-1px); box-shadow: 0 4px 14px rgba(28,43,74,.22); }
    .btn-accent { background: var(--accent); color: #fff; }
    .btn-accent:hover { background: #a93226; transform: translateY(-1px); }
    .btn-outline { background: transparent; color: var(--text); border: 1.5px solid var(--border); }
    .btn-outline:hover { background: var(--tag-bg); border-color: #ccc; }
    .btn-ghost { background: transparent; color: var(--muted); border: none; }
    .btn-ghost:hover { color: var(--text); background: var(--tag-bg); border-radius: 8px; }
    .btn-sm { padding: 7px 14px; font-size: 13px; }
    .btn-icon { padding: 8px; border-radius: 9px; }

    /* ── CARDS ── */
    .card {
      background: var(--surface); border: 1px solid var(--border);
      border-radius: var(--radius); transition: box-shadow .2s, transform .2s;
    }
    .card:hover { box-shadow: 0 8px 28px rgba(0,0,0,.07); }
    .card-lift:hover { transform: translateY(-3px); box-shadow: 0 10px 32px rgba(0,0,0,.09); }

    /* ── SEARCH BAR ── */
    .search-bar {
      display: flex; align-items: center; gap: 0;
      background: var(--surface); border: 1.5px solid var(--border);
      border-radius: 12px; overflow: hidden;
      transition: border-color .2s, box-shadow .2s;
    }
    .search-bar:focus-within {
      border-color: var(--navy);
      box-shadow: 0 0 0 3px rgba(28,43,74,.09);
    }
    .search-bar input {
      border: none; outline: none; background: transparent;
      padding: 12px 16px; font-size: 14.5px;
      font-family: 'DM Sans', sans-serif; color: var(--text); flex: 1;
    }
    .search-bar input::placeholder { color: #b5aea5; }

    /* ── TAGS / BADGES ── */
    .badge {
      display: inline-flex; align-items: center; gap: 4px;
      padding: 3px 9px; border-radius: 20px;
      font-size: 11.5px; font-weight: 500; letter-spacing: .2px;
    }
    .badge-default { background: var(--tag-bg); color: var(--muted); }
    .badge-green  { background: var(--green-light); color: var(--green); }
    .badge-red    { background: var(--accent-light); color: var(--accent); }
    .badge-navy   { background: var(--navy-light); color: var(--navy); }
    .badge-amber  { background: var(--amber-light); color: var(--amber); }

    /* ── COMPARISON TABLE ── */
    .cmp-table { width: 100%; border-collapse: collapse; }
    .cmp-table th {
      background: var(--navy); color: #fff;
      padding: 13px 20px; text-align: left;
      font-size: 13px; font-weight: 500;
    }
    .cmp-table th:first-child { border-radius: 12px 0 0 0; }
    .cmp-table th:last-child  { border-radius: 0 12px 0 0; }
    .cmp-table td {
      padding: 13px 20px; border-bottom: 1px solid var(--border);
      font-size: 14px;
    }
    .cmp-table tr:hover td { background: #faf9f7; }
    .cmp-table tr.best td { background: var(--green-light); }
    .cmp-table tr.best td:first-child { border-left: 3px solid var(--green); }

    /* ── RANGE ── */
    input[type=range] {
      -webkit-appearance: none; width: 100%; height: 3px;
      background: var(--border); border-radius: 2px; outline: none;
    }
    input[type=range]::-webkit-slider-thumb {
      -webkit-appearance: none; width: 15px; height: 15px;
      background: var(--navy); border-radius: 50%; cursor: pointer;
    }

    /* ── CHECKBOX ── */
    .chk { display: flex; align-items: center; gap: 8px; cursor: pointer; font-size: 13.5px; padding: 4px 0; }
    .chk input { accent-color: var(--navy); width: 15px; height: 15px; cursor: pointer; }

    /* ── DASHBOARD STAT ── */
    .stat-card {
      background: var(--surface); border: 1px solid var(--border);
      border-radius: var(--radius); padding: 22px 24px;
    }

    /* ── TOAST ── */
    .toast {
      position: fixed; bottom: 28px; right: 28px; z-index: 999;
      background: var(--navy); color: #fff;
      padding: 12px 20px; border-radius: 12px; font-size: 14px;
      display: flex; align-items: center; gap: 8px;
      box-shadow: 0 8px 24px rgba(28,43,74,.28);
      animation: fadeUp .3s ease;
    }

    /* ── HERO ── */
    .hero-bg {
      background: var(--navy);
      position: relative; overflow: hidden;
    }
    .hero-bg::before {
      content: '';
      position: absolute; inset: 0;
      background: radial-gradient(ellipse 80% 60% at 70% 50%, rgba(192,57,43,.18) 0%, transparent 70%);
      pointer-events: none;
    }
    .hero-dot {
      position: absolute; border-radius: 50%;
      background: rgba(255,255,255,.035);
    }

    /* ── PRODUCT CARD ── */
    .product-card {
      background: var(--surface); border: 1px solid var(--border);
      border-radius: var(--radius); overflow: hidden;
      cursor: pointer; transition: all .2s;
    }
    .product-card:hover { transform: translateY(-3px); box-shadow: 0 10px 32px rgba(0,0,0,.09); }
    .product-img {
      width: 100%; aspect-ratio: 1;
      background: var(--tag-bg);
      display: flex; align-items: center; justify-content: center;
      font-size: 52px; overflow: hidden;
    }

    @media (max-width: 768px) {
      .nav { padding: 0 20px; }
      .hide-mob { display: none !important; }
    }
  `}</style>
);

/* ─────────────────────────────────────────
   MOCK DATA
───────────────────────────────────────── */
const PRODUCTS = [
  { id:1, emoji:"🎧", name:"boAt Rockerz 450 BT Headphones", brand:"boAt", cat:"Electronics", rating:4.3, rev:12840,
    prices:{ amazon:1499, flipkart:1349, myntra:1599, meesho:1279 }, mrp:2999,
    history:[
      {d:"Oct",amazon:1799,flipkart:1699,meesho:1499},
      {d:"Nov",amazon:1699,flipkart:1599,meesho:1399},
      {d:"Dec",amazon:1599,flipkart:1499,meesho:1349},
      {d:"Jan",amazon:1549,flipkart:1399,meesho:1299},
      {d:"Feb",amazon:1499,flipkart:1349,meesho:1279},
      {d:"Mar",amazon:1499,flipkart:1349,meesho:1279},
    ]
  },
  { id:2, emoji:"👟", name:"Nike Air Max 270 Running Shoes", brand:"Nike", cat:"Footwear", rating:4.6, rev:8320,
    prices:{ amazon:7499, flipkart:6999, myntra:7299, meesho:6799 }, mrp:9995,
    history:[
      {d:"Oct",amazon:8999,flipkart:8499,meesho:7999},
      {d:"Nov",amazon:8499,flipkart:7999,meesho:7499},
      {d:"Dec",amazon:7999,flipkart:7499,meesho:7199},
      {d:"Jan",amazon:7699,flipkart:7199,meesho:6999},
      {d:"Feb",amazon:7499,flipkart:6999,meesho:6799},
      {d:"Mar",amazon:7499,flipkart:6999,meesho:6799},
    ]
  },
  { id:3, emoji:"📱", name:"Redmi Note 13 Pro 5G (8GB/256GB)", brand:"Redmi", cat:"Electronics", rating:4.5, rev:23100,
    prices:{ amazon:23999, flipkart:22999, myntra:null, meesho:22499 }, mrp:29999,
    history:[
      {d:"Oct",amazon:27999,flipkart:26999,meesho:25999},
      {d:"Nov",amazon:25999,flipkart:24999,meesho:24499},
      {d:"Dec",amazon:24499,flipkart:23999,meesho:23499},
      {d:"Jan",amazon:23999,flipkart:23299,meesho:22999},
      {d:"Feb",amazon:23999,flipkart:22999,meesho:22499},
      {d:"Mar",amazon:23999,flipkart:22999,meesho:22499},
    ]
  },
  { id:4, emoji:"⌚", name:"Fastrack Reflex Zing Smartwatch", brand:"Fastrack", cat:"Wearables", rating:4.1, rev:5670,
    prices:{ amazon:2299, flipkart:2099, myntra:2399, meesho:1999 }, mrp:3995,
    history:[
      {d:"Oct",amazon:2799,flipkart:2599,meesho:2399},
      {d:"Nov",amazon:2599,flipkart:2399,meesho:2199},
      {d:"Dec",amazon:2399,flipkart:2199,meesho:2099},
      {d:"Jan",amazon:2299,flipkart:2099,meesho:1999},
      {d:"Feb",amazon:2299,flipkart:2099,meesho:1999},
      {d:"Mar",amazon:2299,flipkart:2099,meesho:1999},
    ]
  },
  { id:5, emoji:"💻", name:"HP Pavilion 15 Laptop (i5/16GB/512GB)", brand:"HP", cat:"Electronics", rating:4.4, rev:3890,
    prices:{ amazon:58990, flipkart:56999, myntra:null, meesho:55499 }, mrp:69990,
    history:[
      {d:"Oct",amazon:64990,flipkart:62999,meesho:61499},
      {d:"Nov",amazon:62990,flipkart:60999,meesho:59499},
      {d:"Dec",amazon:60990,flipkart:58999,meesho:57499},
      {d:"Jan",amazon:59990,flipkart:57999,meesho:56499},
      {d:"Feb",amazon:58990,flipkart:56999,meesho:55499},
      {d:"Mar",amazon:58990,flipkart:56999,meesho:55499},
    ]
  },
  { id:6, emoji:"🎮", name:"PS5 DualSense Wireless Controller", brand:"Sony", cat:"Gaming", rating:4.8, rev:9210,
    prices:{ amazon:5990, flipkart:5799, myntra:null, meesho:5699 }, mrp:6990,
    history:[
      {d:"Oct",amazon:6490,flipkart:6299,meesho:6199},
      {d:"Nov",amazon:6290,flipkart:6099,meesho:5999},
      {d:"Dec",amazon:6090,flipkart:5899,meesho:5799},
      {d:"Jan",amazon:5990,flipkart:5799,meesho:5699},
      {d:"Feb",amazon:5990,flipkart:5799,meesho:5699},
      {d:"Mar",amazon:5990,flipkart:5799,meesho:5699},
    ]
  },
];

const PLATFORMS = ["Amazon","Flipkart","Myntra","Meesho"];
const PLATFORM_COLORS = { Amazon:"#f90", Flipkart:"#2874f0", Myntra:"#ff3f6c", Meesho:"#a80060" };

const TRENDING = [
  { emoji:"📺", name:"Samsung 43\" 4K TV", savings:"₹4,200" },
  { emoji:"🧴", name:"Mamaearth Vitamin C Serum", savings:"₹180" },
  { emoji:"🎒", name:"Wildcraft Backpack 45L", savings:"₹650" },
  { emoji:"🔋", name:"Anker 20000mAh Power Bank", savings:"₹320" },
  { emoji:"👗", name:"H&M Cotton Maxi Dress", savings:"₹400" },
];

const fmt = (n) => n ? `₹${n.toLocaleString("en-IN")}` : "—";
const minPrice = (prices) => Math.min(...Object.values(prices).filter(Boolean));
const minPlatform = (prices) =>
  Object.entries(prices).filter(([,v])=>v).sort((a,b)=>a[1]-b[1])[0][0];
const discount = (prices, mrp) =>
  Math.round(((mrp - minPrice(prices)) / mrp) * 100);

/* ─────────────────────────────────────────
   TOAST
───────────────────────────────────────── */
function Toast({ msg, onClose }) {
  useEffect(() => { const t = setTimeout(onClose, 2800); return () => clearTimeout(t); }, []);
  return (
    <div className="toast">
      <CheckCircle size={15} />
      {msg}
    </div>
  );
}

/* ─────────────────────────────────────────
   NAVBAR
───────────────────────────────────────── */
function Nav({ page, setPage, wishlist, onSearch }) {
  const [q, setQ] = useState("");
  return (
    <nav className="nav">
      <div className="nav-logo" onClick={() => setPage("home")}>
        <div className="nav-logo-box">
          <ShoppingCart size={16} color="#fff" />
        </div>
        <span className="serif" style={{ fontSize:17, color:"var(--navy)", letterSpacing:".5px" }}>
          ShopSpare
        </span>
      </div>

      {/* centre search — hidden on home */}
      {page !== "home" && (
        <div className="search-bar hide-mob" style={{ width:320 }}>
          <Search size={15} style={{ marginLeft:14, color:"var(--muted)", flexShrink:0 }} />
          <input
            value={q}
            onChange={e => setQ(e.target.value)}
            onKeyDown={e => { if(e.key==="Enter" && q.trim()) { onSearch(q.trim()); setQ(""); }}}
            placeholder="Search products…"
          />
        </div>
      )}

      <div className="nav-tabs hide-mob">
        {[["home","Home"],["results","Search"],["compare","Compare"],["dashboard","Dashboard"]].map(([k,label])=>(
          <button key={k} className={`nav-tab ${page===k?"active":""}`} onClick={()=>setPage(k)}>
            {label}
          </button>
        ))}
      </div>

      <div className="nav-right">
        <button className="btn btn-ghost btn-icon" style={{ position:"relative" }} onClick={()=>setPage("dashboard")}>
          <Heart size={17} />
          {wishlist.length > 0 && (
            <span style={{
              position:"absolute", top:4, right:4,
              width:8, height:8, background:"var(--accent)",
              borderRadius:"50%", border:"2px solid var(--bg)"
            }} />
          )}
        </button>
        <button className="btn btn-ghost btn-icon" onClick={()=>setPage("dashboard")}>
          <Bell size={17} />
        </button>
        <button className="btn btn-navy btn-sm hide-mob" onClick={()=>setPage("dashboard")}>
          <User size={14} /> Account
        </button>
      </div>
    </nav>
  );
}

/* ─────────────────────────────────────────
   ① HOME / LANDING PAGE
───────────────────────────────────────── */
function HomePage({ setPage, setQuery, setSelected }) {
  const [q, setQ] = useState("");
  const suggestions = ["boAt headphones","Nike shoes","iPhone 15","Samsung TV","Redmi Note"];

  const doSearch = (val) => {
    if (!val.trim()) return;
    setQuery(val);
    setPage("results");
  };

  return (
    <div className="fade-in">
      {/* Hero */}
      <div className="hero-bg" style={{ padding:"80px 48px 72px" }}>
        {/* decorative dots */}
        {[[320,80,200],[580,200,120],[100,180,90],[-40,40,160],[700,320,60]].map(([x,y,s],i)=>(
          <div key={i} className="hero-dot" style={{ left:x, top:y, width:s, height:s }} />
        ))}
        <div style={{ maxWidth:640, margin:"0 auto", textAlign:"center", position:"relative" }}>
          <div className="badge badge-red anim-1" style={{ marginBottom:18 }}>
            <Zap size={11} /> Compare prices across 4 platforms instantly
          </div>
          <h1 className="serif anim-2" style={{ fontSize:"clamp(36px,6vw,56px)", color:"#fff", lineHeight:1.15, marginBottom:20 }}>
            Stop overpaying.<br />
            <span style={{ color:"#f2a58e" }}>Find the best price.</span>
          </h1>
          <p className="anim-3" style={{ color:"rgba(255,255,255,.62)", fontSize:16, marginBottom:36, lineHeight:1.65 }}>
            ShopSpare scans Amazon, Flipkart, Myntra &amp; Meesho in real-time
            and shows you the lowest price — all in one place.
          </p>

          <div className="anim-4" style={{ display:"flex", gap:10, maxWidth:520, margin:"0 auto 24px" }}>
            <div className="search-bar" style={{ flex:1 }}>
              <Search size={15} style={{ marginLeft:14, color:"var(--muted)", flexShrink:0 }} />
              <input
                value={q}
                onChange={e => setQ(e.target.value)}
                onKeyDown={e => { if(e.key==="Enter") doSearch(q); }}
                placeholder='Try "boAt headphones" or "Nike shoes"'
              />
            </div>
            <button className="btn btn-accent" onClick={() => doSearch(q)}>
              Search <ArrowRight size={15} />
            </button>
          </div>

          <div className="anim-5" style={{ display:"flex", gap:8, flexWrap:"wrap", justifyContent:"center" }}>
            {suggestions.map(s => (
              <button key={s} className="btn btn-ghost btn-sm"
                style={{ background:"rgba(255,255,255,.09)", color:"rgba(255,255,255,.7)", borderRadius:20, fontSize:13 }}
                onClick={() => doSearch(s)}>
                {s}
              </button>
            ))}
          </div>
        </div>
      </div>

      {/* Platform trust strip */}
      <div style={{ background:"var(--surface)", borderBottom:"1px solid var(--border)", padding:"14px 48px" }}>
        <div style={{ maxWidth:900, margin:"0 auto", display:"flex", alignItems:"center", gap:24, justifyContent:"center", flexWrap:"wrap" }}>
          <span style={{ fontSize:12, color:"var(--muted)", marginRight:8 }}>Comparing prices on</span>
          {PLATFORMS.map(p => (
            <span key={p} style={{ display:"flex", alignItems:"center", gap:6, fontSize:13, fontWeight:600, color: PLATFORM_COLORS[p] }}>
              <span style={{ width:8, height:8, background:PLATFORM_COLORS[p], borderRadius:"50%", display:"inline-block" }} />
              {p}
            </span>
          ))}
        </div>
      </div>

      <div style={{ maxWidth:1100, margin:"0 auto", padding:"52px 48px" }}>

        {/* Trending */}
        <div style={{ marginBottom:48 }}>
          <div style={{ display:"flex", alignItems:"center", justifyContent:"space-between", marginBottom:24 }}>
            <h2 className="serif" style={{ fontSize:26 }}>Trending Deals</h2>
            <button className="btn btn-outline btn-sm" onClick={() => setPage("results")}>
              View all <ArrowRight size={13} />
            </button>
          </div>
          <div style={{ display:"grid", gridTemplateColumns:"repeat(auto-fill,minmax(190px,1fr))", gap:14 }}>
            {TRENDING.map((t, i) => (
              <div key={i} className="card card-lift"
                style={{ padding:"20px 16px", cursor:"pointer", textAlign:"center" }}
                onClick={() => doSearch(t.name)}>
                <div style={{ fontSize:38, marginBottom:10 }}>{t.emoji}</div>
                <div style={{ fontSize:13, fontWeight:500, marginBottom:6, lineHeight:1.4 }}>{t.name}</div>
                <div className="badge badge-green" style={{ fontSize:11 }}>
                  Save up to {t.savings}
                </div>
              </div>
            ))}
          </div>
        </div>

        {/* Features */}
        <div>
          <h2 className="serif" style={{ fontSize:26, marginBottom:24, textAlign:"center" }}>Why ShopSpare?</h2>
          <div style={{ display:"grid", gridTemplateColumns:"repeat(auto-fill,minmax(230px,1fr))", gap:16 }}>
            {[
              { icon:<TrendingDown size={20} />, title:"Price History", desc:"Track 90-day price trends so you know when to buy." },
              { icon:<Bell size={20} />, title:"Price Alerts", desc:"Get notified the moment a product drops to your target price." },
              { icon:<Shield size={20} />, title:"Always Accurate", desc:"Prices fetched live, not cached stale data." },
              { icon:<Clock size={20} />, title:"Save Time", desc:"One search beats 10 open tabs. Find the best deal instantly." },
            ].map((f,i) => (
              <div key={i} className="card" style={{ padding:"24px 22px" }}>
                <div style={{ width:40, height:40, background:"var(--navy-light)", borderRadius:10,
                  display:"flex", alignItems:"center", justifyContent:"center", color:"var(--navy)", marginBottom:14 }}>
                  {f.icon}
                </div>
                <div style={{ fontWeight:600, marginBottom:6 }}>{f.title}</div>
                <div style={{ fontSize:13.5, color:"var(--muted)", lineHeight:1.6 }}>{f.desc}</div>
              </div>
            ))}
          </div>
        </div>
      </div>
    </div>
  );
}

/* ─────────────────────────────────────────
   ② SEARCH RESULTS PAGE
───────────────────────────────────────── */
function ResultsPage({ query, setPage, setSelected, wishlist, toggleWish, showToast }) {
  const [maxPrice, setMaxPrice] = useState(100000);
  const [platforms, setPlatforms] = useState({ Amazon:true, Flipkart:true, Myntra:true, Meesho:true });
  const [minRating, setMinRating] = useState(0);
  const [sort, setSort] = useState("relevance");
  const [filterOpen, setFilterOpen] = useState(true);

  const togglePlatform = p => setPlatforms(prev => ({ ...prev, [p]: !prev[p] }));

  const filtered = PRODUCTS.filter(p => {
    const min = minPrice(p.prices);
    if (min > maxPrice) return false;
    if (p.rating < minRating) return false;
    const activePlats = Object.keys(platforms).filter(k => platforms[k]);
    if (!activePlats.some(pl => p.prices[pl.toLowerCase()])) return false;
    return true;
  }).sort((a,b) => {
    if (sort === "price_asc")  return minPrice(a.prices) - minPrice(b.prices);
    if (sort === "price_desc") return minPrice(b.prices) - minPrice(a.prices);
    if (sort === "rating")     return b.rating - a.rating;
    return 0;
  });

  return (
    <div className="fade-in" style={{ maxWidth:1200, margin:"0 auto", padding:"32px 40px" }}>
      <div style={{ marginBottom:22 }}>
        <h2 className="serif" style={{ fontSize:24 }}>
          {query ? `Results for "${query}"` : "All Products"}
        </h2>
        <p style={{ color:"var(--muted)", fontSize:14, marginTop:4 }}>{filtered.length} products found</p>
      </div>

      <div style={{ display:"flex", gap:24 }}>
        {/* Sidebar */}
        <div style={{ width:220, flexShrink:0 }}>
          <div className="card" style={{ padding:"18px 20px" }}>
            <div style={{ display:"flex", justifyContent:"space-between", alignItems:"center", marginBottom:16 }}>
              <span style={{ fontWeight:600, fontSize:14 }}>Filters</span>
              <button className="btn btn-ghost btn-sm" style={{ fontSize:12, padding:"4px 8px" }}
                onClick={() => { setMaxPrice(100000); setPlatforms({Amazon:true,Flipkart:true,Myntra:true,Meesho:true}); setMinRating(0); }}>
                Reset
              </button>
            </div>

            {/* Price range */}
            <div style={{ borderTop:"1px solid var(--border)", paddingTop:14, marginBottom:14 }}>
              <div style={{ fontWeight:500, fontSize:13, marginBottom:10 }}>Max Price</div>
              <input type="range" min={1000} max={100000} step={500}
                value={maxPrice} onChange={e => setMaxPrice(+e.target.value)} />
              <div style={{ display:"flex", justifyContent:"space-between", fontSize:12, color:"var(--muted)", marginTop:6 }}>
                <span>₹1,000</span><span style={{ fontWeight:600, color:"var(--navy)" }}>{fmt(maxPrice)}</span>
              </div>
            </div>

            {/* Platforms */}
            <div style={{ borderTop:"1px solid var(--border)", paddingTop:14, marginBottom:14 }}>
              <div style={{ fontWeight:500, fontSize:13, marginBottom:8 }}>Platform</div>
              {PLATFORMS.map(p => (
                <label key={p} className="chk">
                  <input type="checkbox" checked={platforms[p]} onChange={() => togglePlatform(p)} />
                  <span style={{ color: PLATFORM_COLORS[p], fontWeight:500 }}>{p}</span>
                </label>
              ))}
            </div>

            {/* Rating */}
            <div style={{ borderTop:"1px solid var(--border)", paddingTop:14 }}>
              <div style={{ fontWeight:500, fontSize:13, marginBottom:8 }}>Min Rating</div>
              {[0,3,4,4.5].map(r => (
                <label key={r} className="chk">
                  <input type="radio" name="rating" checked={minRating===r} onChange={() => setMinRating(r)}
                    style={{ accentColor:"var(--navy)" }} />
                  <span style={{ fontSize:13 }}>{r === 0 ? "Any" : `${r}+ ⭐`}</span>
                </label>
              ))}
            </div>
          </div>
        </div>

        {/* Results grid */}
        <div style={{ flex:1 }}>
          {/* Sort bar */}
          <div style={{ display:"flex", justifyContent:"flex-end", marginBottom:16 }}>
            <select value={sort} onChange={e => setSort(e.target.value)}
              style={{ padding:"8px 14px", borderRadius:9, border:"1px solid var(--border)",
                fontFamily:"DM Sans,sans-serif", fontSize:13, background:"var(--surface)", cursor:"pointer" }}>
              <option value="relevance">Sort: Relevance</option>
              <option value="price_asc">Price: Low to High</option>
              <option value="price_desc">Price: High to Low</option>
              <option value="rating">Top Rated</option>
            </select>
          </div>

          <div style={{ display:"grid", gridTemplateColumns:"repeat(auto-fill,minmax(210px,1fr))", gap:16 }}>
            {filtered.map(p => {
              const best = minPrice(p.prices);
              const plat = minPlatform(p.prices);
              const off  = discount(p.prices, p.mrp);
              const wished = wishlist.includes(p.id);
              return (
                <div key={p.id} className="product-card"
                  onClick={() => { setSelected(p); setPage("compare"); }}>
                  <div className="product-img">{p.emoji}</div>
                  <div style={{ padding:"14px 14px 16px" }}>
                    <div className="badge badge-default" style={{ marginBottom:6, fontSize:11 }}>{p.cat}</div>
                    <div style={{ fontWeight:500, fontSize:13.5, lineHeight:1.4, marginBottom:8, minHeight:38 }}>{p.name}</div>
                    <div style={{ display:"flex", alignItems:"center", gap:5, marginBottom:10 }}>
                      <span style={{ fontSize:12, background:"#fef9e7", color:"#b8860b", padding:"2px 6px", borderRadius:5, fontWeight:600 }}>
                        ★ {p.rating}
                      </span>
                      <span style={{ fontSize:11, color:"var(--muted)" }}>({(p.rev/1000).toFixed(1)}k)</span>
                    </div>
                    <div style={{ display:"flex", alignItems:"baseline", gap:8, marginBottom:6 }}>
                      <span style={{ fontWeight:700, fontSize:17, color:"var(--green)" }}>{fmt(best)}</span>
                      <span style={{ fontSize:12, textDecoration:"line-through", color:"var(--muted)" }}>{fmt(p.mrp)}</span>
                    </div>
                    <div style={{ display:"flex", alignItems:"center", justifyContent:"space-between" }}>
                      <span className="badge badge-red" style={{ fontSize:11 }}>{off}% off</span>
                      <button
                        className="btn btn-ghost btn-icon"
                        style={{ padding:"5px", color: wished ? "var(--accent)" : "var(--muted)" }}
                        onClick={e => { e.stopPropagation(); toggleWish(p.id); showToast(wished ? "Removed from wishlist" : "Added to wishlist"); }}>
                        <Heart size={16} fill={wished ? "var(--accent)" : "none"} />
                      </button>
                    </div>
                  </div>
                </div>
              );
            })}
          </div>
          {filtered.length === 0 && (
            <div style={{ textAlign:"center", padding:"60px 20px", color:"var(--muted)" }}>
              <Package size={40} style={{ marginBottom:12, opacity:.4 }} />
              <p>No products match your filters.</p>
            </div>
          )}
        </div>
      </div>
    </div>
  );
}

/* ─────────────────────────────────────────
   ③ PRODUCT COMPARISON PAGE
───────────────────────────────────────── */
function ComparePage({ product, wishlist, toggleWish, showToast }) {
  if (!product) return (
    <div style={{ textAlign:"center", padding:"80px 20px", color:"var(--muted)" }}>
      <BarChart2 size={44} style={{ marginBottom:14, opacity:.35 }} />
      <p style={{ fontSize:16 }}>Select a product from search to compare prices.</p>
    </div>
  );

  const p = product;
  const best = minPrice(p.prices);
  const bestPlat = minPlatform(p.prices);
  const off = discount(p.prices, p.mrp);
  const wished = wishlist.includes(p.id);

  const rows = PLATFORMS.map(pl => ({
    platform: pl,
    price: p.prices[pl.toLowerCase()],
    isBest: p.prices[pl.toLowerCase()] === best,
  })).filter(r => r.price);

  return (
    <div className="fade-in" style={{ maxWidth:1000, margin:"0 auto", padding:"36px 40px" }}>

      {/* Product header */}
      <div className="card anim-1" style={{ padding:"28px 32px", marginBottom:24, display:"flex", gap:24, alignItems:"flex-start" }}>
        <div style={{ width:90, height:90, background:"var(--tag-bg)", borderRadius:12,
          display:"flex", alignItems:"center", justifyContent:"center", fontSize:46, flexShrink:0 }}>
          {p.emoji}
        </div>
        <div style={{ flex:1 }}>
          <div className="badge badge-default" style={{ marginBottom:8 }}>{p.cat}</div>
          <h2 style={{ fontSize:20, fontWeight:600, marginBottom:6, lineHeight:1.35 }}>{p.name}</h2>
          <div style={{ display:"flex", alignItems:"center", gap:12, flexWrap:"wrap" }}>
            <span style={{ fontSize:13, background:"#fef9e7", color:"#b8860b", padding:"3px 8px", borderRadius:6, fontWeight:600 }}>
              ★ {p.rating}
            </span>
            <span style={{ fontSize:13, color:"var(--muted)" }}>{p.rev.toLocaleString()} reviews</span>
            <span className="badge badge-green">Best: {fmt(best)} on {bestPlat}</span>
            <span className="badge badge-red">{off}% off MRP</span>
          </div>
        </div>
        <button
          className={`btn ${wished ? "btn-accent" : "btn-outline"}`}
          onClick={() => { toggleWish(p.id); showToast(wished ? "Removed from wishlist" : "Saved to wishlist"); }}>
          <Heart size={14} fill={wished ? "#fff" : "none"} />
          {wished ? "Wishlisted" : "Wishlist"}
        </button>
      </div>

      {/* Comparison table */}
      <div className="card anim-2" style={{ overflow:"hidden", marginBottom:24 }}>
        <div style={{ padding:"20px 24px 0", fontWeight:600, fontSize:15 }}>Price Comparison</div>
        <div style={{ padding:"16px 20px 20px", overflowX:"auto" }}>
          <table className="cmp-table">
            <thead>
              <tr>
                <th>Platform</th>
                <th>Current Price</th>
                <th>Discount</th>
                <th>Savings</th>
                <th>Action</th>
              </tr>
            </thead>
            <tbody>
              {rows.sort((a,b) => a.price - b.price).map(r => (
                <tr key={r.platform} className={r.isBest ? "best" : ""}>
                  <td>
                    <div style={{ display:"flex", alignItems:"center", gap:8 }}>
                      <span style={{ width:9, height:9, borderRadius:"50%",
                        background: PLATFORM_COLORS[r.platform], display:"inline-block" }} />
                      <span style={{ fontWeight: r.isBest ? 600 : 400 }}>{r.platform}</span>
                      {r.isBest && <span className="badge badge-green" style={{ fontSize:10 }}>Best</span>}
                    </div>
                  </td>
                  <td style={{ fontWeight: r.isBest ? 700 : 500, color: r.isBest ? "var(--green)" : "var(--text)" }}>
                    {fmt(r.price)}
                  </td>
                  <td>{Math.round(((p.mrp - r.price)/p.mrp)*100)}%</td>
                  <td style={{ color:"var(--green)" }}>You save {fmt(p.mrp - r.price)}</td>
                  <td>
                    <button className={`btn btn-sm ${r.isBest ? "btn-navy" : "btn-outline"}`}
                      onClick={() => showToast(`Opening ${r.platform}…`)}>
                      Buy <ArrowRight size={12} />
                    </button>
                  </td>
                </tr>
              ))}
            </tbody>
          </table>
        </div>
      </div>

      {/* Price history chart */}
      <div className="card anim-3" style={{ padding:"22px 26px" }}>
        <div style={{ fontWeight:600, fontSize:15, marginBottom:4 }}>90-Day Price History</div>
        <div style={{ fontSize:13, color:"var(--muted)", marginBottom:20 }}>Track how prices changed over the last 6 months</div>
        <ResponsiveContainer width="100%" height={230}>
          <LineChart data={p.history} margin={{ top:5, right:10, bottom:5, left:0 }}>
            <CartesianGrid strokeDasharray="3 3" stroke="#f0ece6" />
            <XAxis dataKey="d" tick={{ fontSize:12, fill:"#9b9590" }} axisLine={false} tickLine={false} />
            <YAxis tick={{ fontSize:12, fill:"#9b9590" }} axisLine={false} tickLine={false}
              tickFormatter={v => `₹${(v/1000).toFixed(0)}k`} />
            <Tooltip
              formatter={(v, name) => [fmt(v), name]}
              contentStyle={{ borderRadius:10, border:"1px solid var(--border)", fontSize:13 }}
            />
            {["amazon","flipkart","meesho"].map((pl,i) => (
              <Line key={pl} type="monotone" dataKey={pl}
                stroke={[PLATFORM_COLORS.Amazon, PLATFORM_COLORS.Flipkart, PLATFORM_COLORS.Meesho][i]}
                strokeWidth={2} dot={false} activeDot={{ r:5 }} />
            ))}
          </LineChart>
        </ResponsiveContainer>
        <div style={{ display:"flex", gap:16, justifyContent:"center", marginTop:12 }}>
          {["amazon","flipkart","meesho"].map((pl,i) => (
            <div key={pl} style={{ display:"flex", alignItems:"center", gap:6, fontSize:12, color:"var(--muted)" }}>
              <span style={{ width:24, height:3, background:[PLATFORM_COLORS.Amazon,PLATFORM_COLORS.Flipkart,PLATFORM_COLORS.Meesho][i], borderRadius:2, display:"inline-block" }} />
              {pl.charAt(0).toUpperCase()+pl.slice(1)}
            </div>
          ))}
        </div>
      </div>
    </div>
  );
}

/* ─────────────────────────────────────────
   ④ USER DASHBOARD
───────────────────────────────────────── */
function DashboardPage({ wishlist, toggleWish, setPage, setSelected, showToast }) {
  const wishedProducts = PRODUCTS.filter(p => wishlist.includes(p.id));
  const alerts = [
    { id:1, product:"boAt Rockerz 450", target:1200, current:1279, platform:"Meesho" },
    { id:2, product:"Redmi Note 13 Pro", target:21999, current:22499, platform:"Meesho" },
  ];

  return (
    <div className="fade-in" style={{ maxWidth:1100, margin:"0 auto", padding:"36px 40px" }}>
      <h2 className="serif anim-1" style={{ fontSize:28, marginBottom:8 }}>My Dashboard</h2>
      <p className="anim-2" style={{ color:"var(--muted)", fontSize:14, marginBottom:32 }}>
        Manage your wishlist, alerts, and savings.
      </p>

      {/* Stats */}
      <div className="anim-2" style={{ display:"grid", gridTemplateColumns:"repeat(auto-fill,minmax(180px,1fr))", gap:14, marginBottom:32 }}>
        {[
          { label:"Wishlist Items", value: wishedProducts.length, color:"var(--navy)", icon:<Heart size={18}/> },
          { label:"Active Alerts", value: alerts.length, color:"var(--accent)", icon:<Bell size={18}/> },
          { label:"Total Saved", value:"₹6,480", color:"var(--green)", icon:<TrendingDown size={18}/> },
          { label:"Searches", value:"24", color:"var(--amber)", icon:<Search size={18}/> },
        ].map((s,i) => (
          <div key={i} className="stat-card">
            <div style={{ width:38, height:38, background:s.color+"15", borderRadius:9,
              display:"flex", alignItems:"center", justifyContent:"center", color:s.color, marginBottom:12 }}>
              {s.icon}
            </div>
            <div style={{ fontWeight:700, fontSize:24, color:s.color }}>{s.value}</div>
            <div style={{ fontSize:13, color:"var(--muted)", marginTop:2 }}>{s.label}</div>
          </div>
        ))}
      </div>

      <div style={{ display:"grid", gridTemplateColumns:"1fr 1fr", gap:24 }}>
        {/* Wishlist */}
        <div className="card anim-3" style={{ padding:"22px 24px" }}>
          <div style={{ display:"flex", justifyContent:"space-between", alignItems:"center", marginBottom:18 }}>
            <span style={{ fontWeight:600, fontSize:15 }}>❤️ Wishlist</span>
            <button className="btn btn-outline btn-sm" onClick={() => setPage("results")}>
              + Add more
            </button>
          </div>
          {wishedProducts.length === 0 ? (
            <div style={{ textAlign:"center", padding:"32px 0", color:"var(--muted)" }}>
              <Heart size={28} style={{ marginBottom:8, opacity:.3 }} />
              <p style={{ fontSize:13 }}>Your wishlist is empty.<br />Save products while browsing!</p>
            </div>
          ) : (
            <div style={{ display:"flex", flexDirection:"column", gap:10 }}>
              {wishedProducts.map(p => (
                <div key={p.id} style={{ display:"flex", alignItems:"center", gap:12,
                  padding:"10px 12px", borderRadius:10, border:"1px solid var(--border)",
                  cursor:"pointer", transition:"background .15s" }}
                  onClick={() => { setSelected(p); setPage("compare"); }}>
                  <span style={{ fontSize:26 }}>{p.emoji}</span>
                  <div style={{ flex:1, minWidth:0 }}>
                    <div style={{ fontSize:13, fontWeight:500, whiteSpace:"nowrap", overflow:"hidden", textOverflow:"ellipsis" }}>{p.name}</div>
                    <div style={{ fontSize:12, color:"var(--green)", fontWeight:600 }}>{fmt(minPrice(p.prices))}</div>
                  </div>
                  <button className="btn btn-ghost btn-icon" style={{ color:"var(--accent)", flexShrink:0 }}
                    onClick={e => { e.stopPropagation(); toggleWish(p.id); showToast("Removed from wishlist"); }}>
                    <X size={14} />
                  </button>
                </div>
              ))}
            </div>
          )}
        </div>

        {/* Price Alerts */}
        <div className="card anim-4" style={{ padding:"22px 24px" }}>
          <div style={{ display:"flex", justifyContent:"space-between", alignItems:"center", marginBottom:18 }}>
            <span style={{ fontWeight:600, fontSize:15 }}>🔔 Price Alerts</span>
            <span className="badge badge-amber">{alerts.length} active</span>
          </div>
          <div style={{ display:"flex", flexDirection:"column", gap:12 }}>
            {alerts.map(a => {
              const diff = a.current - a.target;
              const pct = Math.round((diff / a.current) * 100);
              return (
                <div key={a.id} style={{ padding:"14px 16px", borderRadius:10, border:"1px solid var(--border)" }}>
                  <div style={{ fontWeight:500, fontSize:13.5, marginBottom:6 }}>{a.product}</div>
                  <div style={{ display:"flex", alignItems:"center", gap:8, flexWrap:"wrap" }}>
                    <span style={{ fontSize:13, color:"var(--muted)" }}>Target: <b style={{ color:"var(--green)" }}>{fmt(a.target)}</b></span>
                    <span style={{ fontSize:13, color:"var(--muted)" }}>Now: <b>{fmt(a.current)}</b></span>
                    <span className="badge badge-amber" style={{ fontSize:11 }}>
                      <AlertCircle size={10} /> {pct}% above target
                    </span>
                  </div>
                  <div style={{ marginTop:8, height:4, background:"var(--border)", borderRadius:2, overflow:"hidden" }}>
                    <div style={{ height:"100%", width:`${100 - pct}%`, background:"var(--amber)", borderRadius:2, transition:"width .4s" }} />
                  </div>
                </div>
              );
            })}
            <button className="btn btn-outline btn-sm" style={{ alignSelf:"flex-start", marginTop:4 }}
              onClick={() => showToast("Alert settings coming soon!")}>
              + Set new alert
            </button>
          </div>
        </div>
      </div>

      {/* Recent activity */}
      <div className="card anim-5" style={{ padding:"22px 24px", marginTop:24 }}>
        <div style={{ fontWeight:600, fontSize:15, marginBottom:16 }}>📋 Recent Activity</div>
        <div style={{ display:"flex", flexDirection:"column", gap:0 }}>
          {[
            { action:"Viewed price comparison", product:"boAt Rockerz 450", time:"2 hours ago", color:"var(--navy)" },
            { action:"Added to wishlist", product:"Nike Air Max 270", time:"Yesterday", color:"var(--accent)" },
            { action:"Price dropped!", product:"Redmi Note 13 Pro — ₹500 drop on Flipkart", time:"2 days ago", color:"var(--green)" },
            { action:"Set price alert", product:"PS5 DualSense Controller", time:"3 days ago", color:"var(--amber)" },
          ].map((a,i) => (
            <div key={i} style={{ display:"flex", alignItems:"flex-start", gap:12,
              padding:"12px 0", borderBottom: i < 3 ? "1px solid var(--border)" : "none" }}>
              <div style={{ width:8, height:8, borderRadius:"50%", background:a.color, flexShrink:0, marginTop:5 }} />
              <div>
                <span style={{ fontSize:13.5, fontWeight:500 }}>{a.action}: </span>
                <span style={{ fontSize:13.5, color:"var(--muted)" }}>{a.product}</span>
                <div style={{ fontSize:11.5, color:"var(--muted)", marginTop:2 }}>{a.time}</div>
              </div>
            </div>
          ))}
        </div>
      </div>
    </div>
  );
}

/* ─────────────────────────────────────────
   ROOT APP
───────────────────────────────────────── */
export default function App() {
  const [page, setPage] = useState("home");
  const [query, setQuery] = useState("");
  const [selected, setSelected] = useState(null);
  const [wishlist, setWishlist] = useState([1, 3]);
  const [toast, setToast] = useState(null);

  const toggleWish = (id) =>
    setWishlist(prev => prev.includes(id) ? prev.filter(x => x !== id) : [...prev, id]);

  const showToast = (msg) => {
    setToast(msg);
    setTimeout(() => setToast(null), 2800);
  };

  const handleSearch = (q) => {
    setQuery(q);
    setPage("results");
  };

  return (
    <>
      <GlobalStyles />
      <div style={{ minHeight:"100vh", display:"flex", flexDirection:"column" }}>
        <Nav page={page} setPage={setPage} wishlist={wishlist} onSearch={handleSearch} />
        <main style={{ flex:1 }}>
          {page === "home" && (
            <HomePage setPage={setPage} setQuery={setQuery} setSelected={setSelected} />
          )}
          {page === "results" && (
            <ResultsPage
              query={query} setPage={setPage} setSelected={setSelected}
              wishlist={wishlist} toggleWish={toggleWish} showToast={showToast}
            />
          )}
          {page === "compare" && (
            <ComparePage
              product={selected} wishlist={wishlist}
              toggleWish={toggleWish} showToast={showToast}
            />
          )}
          {page === "dashboard" && (
            <DashboardPage
              wishlist={wishlist} toggleWish={toggleWish}
              setPage={setPage} setSelected={setSelected} showToast={showToast}
            />
          )}
        </main>

        {/* Footer */}
        <footer style={{ borderTop:"1px solid var(--border)", padding:"20px 48px",
          display:"flex", justifyContent:"space-between", alignItems:"center",
          background:"var(--surface)", fontSize:13, color:"var(--muted)" }}>
          <div style={{ display:"flex", alignItems:"center", gap:8 }}>
            <div style={{ width:22, height:22, background:"var(--navy)", borderRadius:5,
              display:"flex", alignItems:"center", justifyContent:"center" }}>
              <ShoppingCart size={11} color="#fff" />
            </div>
            <span className="serif" style={{ fontSize:14, color:"var(--navy)" }}>ShopSpare</span>
          </div>
          <span>IIT Patna · Capstone-I · Group 75</span>
          <span>Built with React + Recharts</span>
        </footer>
      </div>

      {toast && <Toast msg={toast} onClose={() => setToast(null)} />}
    </>
  );
}