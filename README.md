<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>SpiceMart – Premium Spices & Masalas</title>
  <meta name="description" content="Shop premium, ethically sourced spices & masalas. Fresh aroma, secure checkout, fast delivery." />
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700;900&display=swap" rel="stylesheet">
  <style>
    :root{
      --bg:#fffaf3;            /* background */
      --surface:#ffffff;        /* cards */
      --text:#221c15;           /* primary text */
      --muted:#6b5f54;          /* secondary text */
      --ring: #ffd46a;          /* focus ring */
      --primary:#e67e22;        /* saffron */
      --primary-600:#cc6f1e;
      --primary-700:#b96119;
      --accent:#b02a30;         /* chili */
      --ok:#2e7d32;             /* cardamom green */
      --shadow: 0 10px 30px rgba(0,0,0,.08);
      --radius: 18px;
      --chip:#fff2df;
      --chip-text:#7a4a10;
    }
    /* Chili theme */
    .theme-chili{ --primary:#b02a30; --primary-600:#9b242a; --primary-700:#851e24; --ring:#ff9aa7; --chip:#ffe6e8; --chip-text:#7a1e23; }
    /* Cardamom theme */
    .theme-cardamom{ --primary:#2e7d32; --primary-600:#256628; --primary-700:#1e5221; --ring:#a6e3a1; --chip:#eaf7eb; --chip-text:#1f4b22; }

    *{box-sizing:border-box}
    html,body{height:100%}
    body{margin:0; font-family:Inter,system-ui,Segoe UI,Roboto,Arial; background:var(--bg); color:var(--text)}

    /* Utilities */
    .container{max-width:1200px; margin-inline:auto; padding:0 20px}
    .btn{display:inline-flex; align-items:center; gap:.6rem; padding:.85rem 1.2rem; border-radius:calc(var(--radius) - 6px); border:1px solid transparent; cursor:pointer; font-weight:600; transition:.2s ease; text-decoration:none}
    .btn-primary{background:var(--primary); color:#fff}
    .btn-primary:hover{background:var(--primary-600)}
    .btn-outline{background:transparent; border-color:var(--primary); color:var(--primary)}
    .btn-outline:hover{background:var(--chip)}
    .tag{background:var(--chip); color:var(--chip-text); padding:.35rem .65rem; border-radius:999px; font-size:.8rem; font-weight:600}
    .card{background:var(--surface); border-radius:var(--radius); box-shadow:var(--shadow)}
    .grid{display:grid; gap:22px}
    .grid-3{grid-template-columns:repeat(3,minmax(0,1fr))}
    @media (max-width:1000px){.grid-3{grid-template-columns:repeat(2,minmax(0,1fr))}}
    @media (max-width:640px){.grid-3{grid-template-columns:1fr}}
    .hidden{display:none}
    .sr-only{position:absolute;width:1px;height:1px;padding:0;margin:-1px;overflow:hidden;clip:rect(0,0,0,0);white-space:nowrap;border:0}
    .pill{border-radius:999px}
    .ring:focus{outline:3px solid var(--ring); outline-offset:2px}

    /* Header */
    header{position:sticky; top:0; z-index:20; backdrop-filter:saturate(140%) blur(8px); background:color-mix(in oklab, var(--bg) 86%, white 14%); border-bottom:1px solid #f0e7da}
    .nav{display:flex; align-items:center; justify-content:space-between; height:70px}
    .brand{display:flex; gap:.7rem; align-items:center; font-weight:900; letter-spacing:.3px}
    .brand .logo{width:36px; height:36px; border-radius:12px; background:linear-gradient(135deg,var(--primary), var(--accent)); display:grid; place-items:center; color:#fff; font-weight:900}
    .nav-actions{display:flex; align-items:center; gap:10px}
    .search{display:flex; align-items:center; gap:.6rem; background:var(--surface); border:1px solid #efe6d9; padding:.55rem .8rem; border-radius:12px; width:min(460px, 55vw)}
    .search input{flex:1; border:0; outline:0; background:transparent; font:inherit}
    .icon{width:20px; height:20px}
    .theme-picker{display:flex; gap:8px; align-items:center}
    .swatch{width:22px;height:22px;border-radius:999px;border:2px solid #fff; box-shadow:0 0 0 2px rgba(0,0,0,.1); cursor:pointer}
    .swatch.saffron{background:#e67e22}
    .swatch.chili{background:#b02a30}
    .swatch.cardamom{background:#2e7d32}

    /* Hero */
    .hero{padding:40px 0 22px}
    .hero-wrap{display:grid; grid-template-columns:1.3fr .7fr; gap:26px; align-items:center}
    @media (max-width:900px){.hero-wrap{grid-template-columns:1fr}}
    .hero h1{font-size:clamp(34px, 3.4vw, 56px); line-height:1.05; margin:0}
    .hero p{color:var(--muted); font-size:1.05rem; margin:.9rem 0 1.2rem}
    .hero .banner{position:relative; overflow:hidden; min-height:260px; border-radius:var(--radius)}
    .hero .banner::before{content:""; position:absolute; inset:0; background:conic-gradient(from 120deg at 20% 20%, var(--primary) 0%, var(--accent) 35%, #ffb703 65%, var(--ok) 100%); filter:blur(40px); opacity:.35}
    .hero .banner img{position:absolute; inset:0; width:100%; height:100%; object-fit:cover; mix-blend:multiply}

    /* Category bar */
    .cats{display:flex; gap:10px; overflow:auto; padding-bottom:6px}
    .cats button{background:var(--surface); border:1px solid #efe6d9; padding:.6rem .9rem; border-radius:999px; font-weight:600; cursor:pointer}
    .cats button.active{background:var(--primary); color:#fff; border-color:transparent}

    /* Product card */
    .product{display:flex; flex-direction:column}
    .product .img{position:relative; aspect-ratio:1/1; overflow:hidden; border-radius:14px}
    .product .img img{width:100%; height:100%; object-fit:cover; transition: transform .35s ease}
    .product:hover .img img{transform:scale(1.05)}
    .badge{position:absolute; top:10px; left:10px}
    .price{display:flex; align-items:baseline; gap:.5rem; margin:.5rem 0 0}
    .price .mrp{color:#9c8f81; text-decoration:line-through; font-size:.95rem}
    .stars{color:#f59e0b; font-size:.95rem}

    /* Cart drawer */
    .drawer{position:fixed; inset:0; display:grid; grid-template-columns:1fr min(420px, 92vw); visibility:hidden}
    .drawer[open]{visibility:visible}
    .drawer .backdrop{background:rgba(0,0,0,.45)}
    .drawer .panel{background:var(--surface); box-shadow:var(--shadow); padding:20px; overflow:auto}
    .cart-item{display:grid; grid-template-columns:64px 1fr auto; gap:12px; align-items:center}
    .cart-item img{width:64px; height:64px; object-fit:cover; border-radius:12px}
    .qty{display:flex; align-items:center; gap:8px}
    .qty button{width:28px;height:28px; border-radius:8px; border:1px solid #e8ddd0; background:#fff; cursor:pointer}

    /* Sections */
    section{padding:24px 0}
    .section-head{display:flex; align-items:center; justify-content:space-between; margin-bottom:10px}
    .section-head h2{margin:0; font-size:1.4rem}

    /* Footer */
    footer{margin-top:30px; padding:32px 0 60px; border-top:1px solid #efe6d9; color:var(--muted)}

    /* Mini helpers */
    .chipbar{display:flex; gap:10px; flex-wrap:wrap}
    .chip{background:var(--chip); color:var(--chip-text); padding:.45rem .7rem; border-radius:999px; font-weight:600; cursor:pointer}
    .chip.active{background:var(--primary); color:#fff}
    .divider{height:1px; background:#efe6d9; margin:12px 0}
  </style>
</head>
<body>
  <header>
    <div class="container nav">
      <a class="brand" href="#" aria-label="SpiceMart Home">
        <div class="logo">🌶️</div>
        <div>
          <div style="font-size:1.1rem; line-height:1">SpiceMart</div>
          <div style="font-size:.78rem; color:var(--muted); margin-top:-2px">Premium • Fresh • Pure</div>
        </div>
      </a>

      <label class="search" for="q">
        <svg class="icon" viewBox="0 0 24 24" fill="none" stroke="currentColor"><circle cx="11" cy="11" r="7" stroke-width="2"/><path d="m20 20-3.5-3.5" stroke-width="2"/></svg>
        <input id="q" class="ring" type="search" placeholder="Search spices, masalas, brands…" />
      </label>

      <div class="nav-actions">
        <div class="theme-picker" title="Theme colors">
          <div class="swatch saffron" data-theme="saffron" aria-label="Saffron theme" tabindex="0"></div>
          <div class="swatch chili" data-theme="chili" aria-label="Chili theme" tabindex="0"></div>
          <div class="swatch cardamom" data-theme="cardamom" aria-label="Cardamom theme" tabindex="0"></div>
        </div>
        <button class="btn btn-outline" id="btnLogin">Sign in</button>
        <button class="btn btn-primary" id="btnCart" aria-haspopup="dialog" aria-controls="cartDrawer">
          <svg class="icon" viewBox="0 0 24 24" fill="none" stroke="currentColor"><path d="M4 6h17l-2 10H6L4 6Z" stroke-width="2"/><circle cx="9" cy="20" r="1.6"/><circle cx="17" cy="20" r="1.6"/></svg>
          <span id="cartCount">0</span>
        </button>
      </div>
    </div>
  </header>

  <main>
    <!-- HERO -->
    <section class="hero">
      <div class="container hero-wrap">
        <div>
          <div class="tag">New Harvest • 2025</div>
          <h1>Bring home the aroma of <span style="color:var(--primary)">real spices</span>.</h1>
          <p>Single-origin lots, stone-ground masalas, and freshly sealed packs. Add a pinch of magic to every recipe.</p>
          <div style="display:flex; gap:10px; flex-wrap:wrap">
            <a href="#products" class="btn btn-primary">Shop Bestsellers</a>
            <a href="#collections" class="btn btn-outline">Explore Collections</a>
          </div>
          <div class="chipbar" style="margin-top:16px">
            <span class="chip" data-filter="all">All</span>
            <span class="chip" data-filter="whole">Whole Spices</span>
            <span class="chip" data-filter="ground">Ground</span>
            <span class="chip" data-filter="blend">Masala Blends</span>
            <span class="chip" data-filter="organic">Organic</span>
          </div>
        </div>
        <div class="banner card">
          <!-- royalty-free image suggestion -->
          <img alt="Assorted whole and ground spices in bowls" src="https://images.unsplash.com/photo-1604908176997-431d67a8a2aa?q=80&w=1600&auto=format&fit=crop"/>
        </div>
      </div>
    </section>

    <!-- CATEGORIES -->
    <section class="container" id="collections">
      <div class="section-head">
        <h2>Shop by Category</h2>
      </div>
      <div class="cats">
        <button class="pill active" data-cat="all">All</button>
        <button class="pill" data-cat="whole">Whole Spices</button>
        <button class="pill" data-cat="ground">Ground</button>
        <button class="pill" data-cat="blend">Masala Blends</button>
        <button class="pill" data-cat="organic">Organic</button>
        <button class="pill" data-cat="gift">Gifting</button>
      </div>
    </section>

    <!-- PRODUCTS -->
    <section id="products" class="container">
      <div class="section-head">
        <h2>Featured Products</h2>
        <a href="#" class="btn btn-outline">View all</a>
      </div>
      <div id="productGrid" class="grid grid-3"></div>
    </section>

    <!-- BENEFITS -->
    <section class="container">
      <div class="grid grid-3">
        <div class="card" style="padding:18px">
          <strong>Ethically Sourced</strong>
          <p style="color:var(--muted); margin:.4rem 0 0">Direct trade with small farms ensures quality and fair pay.</p>
        </div>
        <div class="card" style="padding:18px">
          <strong>Freshness Guarantee</strong>
          <p style="color:var(--muted); margin:.4rem 0 0">Roasted & packed weekly. Full refund if aroma fades.</p>
        </div>
        <div class="card" style="padding:18px">
          <strong>Secure Checkout</strong>
          <p style="color:var(--muted); margin:.4rem 0 0">PCI-compliant payments and quick doorstep delivery.</p>
        </div>
      </div>
    </section>

    <!-- NEWSLETTER -->
    <section class="container">
      <div class="card" style="padding:20px; display:flex; gap:16px; align-items:center; justify-content:space-between; flex-wrap:wrap">
        <div>
          <div class="tag">Save 10% today</div>
          <h3 style="margin:.4rem 0 0">Join our Spice Club</h3>
          <p style="color:var(--muted); margin:.2rem 0 0">Get recipes, early drops, and exclusive deals.</p>
        </div>
        <form id="newsletter" style="display:flex; gap:10px">
          <label class="sr-only" for="email">Email</label>
          <input id="email" class="ring" type="email" placeholder="you@example.com" required style="padding:.85rem 1rem; border-radius:12px; border:1px solid #efe6d9; background:#fff; min-width:240px"/>
          <button class="btn btn-primary" type="submit">Subscribe</button>
        </form>
      </div>
    </section>
  </main>

  <footer>
    <div class="container" style="display:grid; gap:18px; grid-template-columns:2fr 1fr 1fr">
      <div>
        <div class="brand"><div class="logo">🌶️</div><strong>SpiceMart</strong></div>
        <p style="max-width:46ch">Your destination for vibrant, high‑quality spices and handcrafted masalas. Taste the difference freshness makes.</p>
      </div>
      <div>
        <strong>Support</strong>
        <ul style="list-style:none; padding:0; margin:.6rem 0 0; line-height:1.9">
          <li><a href="#" style="color:inherit; text-decoration:none">Shipping & Returns</a></li>
          <li><a href="#" style="color:inherit; text-decoration:none">FAQ</a></li>
          <li><a href="#" style="color:inherit; text-decoration:none">Contact</a></li>
        </ul>
      </div>
      <div>
        <strong>Company</strong>
        <ul style="list-style:none; padding:0; margin:.6rem 0 0; line-height:1.9">
          <li><a href="#" style="color:inherit; text-decoration:none">About</a></li>
          <li><a href="#" style="color:inherit; text-decoration:none">Sourcing</a></li>
          <li><a href="#" style="color:inherit; text-decoration:none">Careers</a></li>
        </ul>
      </div>
    </div>
  </footer>

  <!-- CART DRAWER -->
  <dialog id="cartDrawer" class="drawer">
    <div class="backdrop" data-close></div>
    <div class="panel">
      <div style="display:flex; justify-content:space-between; align-items:center">
        <h3 style="margin:0">Your Cart</h3>
        <button class="btn" data-close aria-label="Close cart">✕</button>
      </div>
      <div class="divider"></div>
      <div id="cartItems" style="display:grid; gap:14px"></div>
      <div class="divider"></div>
      <div style="display:flex; justify-content:space-between; align-items:center">
        <strong>Total</strong>
        <strong id="cartTotal">₹0</strong>
      </div>
      <div style="display:flex; gap:10px; margin-top:14px">
        <button class="btn btn-outline" data-close>Continue shopping</button>
        <button class="btn btn-primary" id="checkoutBtn">Checkout</button>
      </div>
    </div>
  </dialog>

  <script>
    // --- Sample Catalog Data ---
    const products = [
      {id:'turmeric', name:'Lakadong Turmeric Powder', cat:['ground','organic'], price:199, mrp:249, rating:4.9, img:'https://images.unsplash.com/photo-1615486364201-6bc4c22f3d36?q=80&w=1200&auto=format&fit=crop', badge:'Bestseller'},
      {id:'pepper', name:'Whole Black Pepper (Malabar)', cat:['whole','organic'], price:299, mrp:349, rating:4.8, img:'https://images.unsplash.com/photo-1590080876475-c4b1c2b67cde?q=80&w=1200&auto=format&fit=crop', badge:'Fresh crop'},
      {id:'cumin', name:'Cumin Seeds (Jeera)', cat:['whole'], price:149, mrp:199, rating:4.7, img:'https://images.unsplash.com/photo-1615485737651-c5c12c7d794d?q=80&w=1200&auto=format&fit=crop'},
      {id:'chili', name:'Byadgi Chili Powder', cat:['ground'], price:179, mrp:229, rating:4.6, img:'https://images.unsplash.com/photo-1505576399279-565b52d4ac71?q=80&w=1200&auto=format&fit=crop'},
      {id:'garam', name:'Garam Masala – Stone Ground', cat:['blend'], price:219, mrp:269, rating:4.8, img:'https://images.unsplash.com/photo-1601004890684-d8cbf643f5f2?q=80&w=1200&auto=format&fit=crop', badge:'Chef’s pick'},
      {id:'chaat', name:'Chaat Masala', cat:['blend'], price:149, mrp:189, rating:4.5, img:'https://images.unsplash.com/photo-1544025162-d76694265947?q=80&w=1200&auto=format&fit=crop'},
      {id:'cardamom', name:'Green Cardamom (Elaichi)', cat:['whole','gift'], price:499, mrp:549, rating:4.9, img:'https://images.unsplash.com/photo-1628463374071-7e39f7b85dd6?q=80&w=1200&auto=format&fit=crop'},
      {id:'coriander', name:'Coriander Powder (Dhania)', cat:['ground'], price:129, mrp:159, rating:4.4, img:'https://images.unsplash.com/photo-1630333967249-6d9fc7b103fe?q=80&w=1200&auto=format&fit=crop'},
      {id:'giftbox', name:'Spice Gift Box – Essentials', cat:['gift','blend'], price:899, mrp:1099, rating:4.7, img:'https://images.unsplash.com/photo-1596040033229-9f5d5b7c87b9?q=80&w=1200&auto=format&fit=crop', badge:'Great gift'}
    ];

    const state = { cart:new Map(), filter:'all', search:'' };

    const grid = document.getElementById('productGrid');
    const q = document.getElementById('q');

    function formatINR(n){
      return new Intl.NumberFormat('en-IN',{style:'currency', currency:'INR'}).format(n);
    }

    function renderStars(r){
      const full = '★'.repeat(Math.floor(r));
      const rest = '☆'.repeat(5-Math.floor(r));
      return `<span class="stars" aria-label="${r} out of 5">${full}${rest}</span>`
    }

    function matches(p){
      const byCat = state.filter==='all' || p.cat.includes(state.filter);
      const bySearch = !state.search || p.name.toLowerCase().includes(state.search);
      return byCat && bySearch;
    }

    function renderProducts(){
      grid.innerHTML = products.filter(matches).map(p => `
        <article class="product card" data-id="${p.id}">
          <div class="img">
            <img src="${p.img}" alt="${p.name}">
            ${p.badge?`<span class="badge tag">${p.badge}</span>`:''}
          </div>
          <div style="padding:14px">
            <div style="display:flex; justify-content:space-between; align-items:flex-start; gap:6px">
              <h3 style="margin:.1rem 0 0; font-size:1.05rem">${p.name}</h3>
              <button class="btn btn-outline" data-add="${p.id}" aria-label="Add ${p.name} to cart">Add</button>
            </div>
            <div class="price">
              <strong>${formatINR(p.price)}</strong>
              <span class="mrp">${formatINR(p.mrp)}</span>
            </div>
            ${renderStars(p.rating)}
            <div style="color:var(--muted); font-size:.92rem; margin-top:.4rem">${p.cat.map(c=>`#${c}`).join(' ')}</div>
          </div>
        </article>`).join('');
    }

    function updateCartBadge(){
      const count = Array.from(state.cart.values()).reduce((a,b)=>a+b,0);
      document.getElementById('cartCount').textContent = String(count);
    }

    function openCart(){ document.getElementById('cartDrawer').showModal(); }
    function closeCart(){ document.getElementById('cartDrawer').close(); }

    function renderCart(){
      const wrap = document.getElementById('cartItems');
      if(!state.cart.size){ wrap.innerHTML = '<p>Your cart is empty.</p>'; document.getElementById('cartTotal').textContent = formatINR(0); return; }
      let total=0;
      wrap.innerHTML = Array.from(state.cart.entries()).map(([id,qty])=>{
        const p = products.find(x=>x.id===id);
        total += p.price*qty;
        return `
          <div class="cart-item">
            <img src="${p.img}" alt="${p.name}">
            <div>
              <div style="display:flex; justify-content:space-between; gap:10px">
                <strong>${p.name}</strong>
                <button class="btn" data-remove="${p.id}">Remove</button>
              </div>
              <div class="qty">
                <button data-dec="${p.id}">–</button>
                <span>${qty}</span>
                <button data-inc="${p.id}">+</button>
              </div>
            </div>
            <div><strong>${formatINR(p.price*qty)}</strong></div>
          </div>`
      }).join('');
      document.getElementById('cartTotal').textContent = formatINR(total);
    }

    // Event: add to cart
    grid.addEventListener('click', e=>{
      const add = e.target.closest('[data-add]');
      if(add){
        const id = add.getAttribute('data-add');
        state.cart.set(id, (state.cart.get(id)||0)+1);
        updateCartBadge();
        add.textContent = 'Added ✓';
        setTimeout(()=>add.textContent='Add', 900);
      }
    });

    // Search
    q.addEventListener('input', ()=>{ state.search = q.value.trim().toLowerCase(); renderProducts(); });

    // Category chips
    document.querySelector('.cats').addEventListener('click', (e)=>{
      const btn = e.target.closest('button');
      if(!btn) return;
      document.querySelectorAll('.cats button').forEach(b=>b.classList.remove('active'));
      btn.classList.add('active');
      state.filter = btn.dataset.cat;
      renderProducts();
    });

    // Hero chips (secondary filter)
    document.querySelector('.chipbar').addEventListener('click', (e)=>{
      const chip = e.target.closest('.chip');
      if(!chip) return;
      document.querySelectorAll('.chipbar .chip').forEach(c=>c.classList.remove('active'));
      chip.classList.add('active');
      state.filter = chip.dataset.filter;
      renderProducts();
    });

    // Cart drawer controls
    document.getElementById('btnCart').addEventListener('click', ()=>{ renderCart(); openCart(); });
    document.getElementById('cartDrawer').addEventListener('click', e=>{
      if(e.target.hasAttribute('data-close')) closeCart();
      const r = e.target.closest('[data-remove]');
      const i = e.target.closest('[data-inc]');
      const d = e.target.closest('[data-dec]');
      if(r){ state.cart.delete(r.getAttribute('data-remove')); renderCart(); updateCartBadge(); }
      if(i){ const id=i.getAttribute('data-inc'); state.cart.set(id,(state.cart.get(id)||0)+1); renderCart(); updateCartBadge(); }
      if(d){ const id=d.getAttribute('data-dec'); const v=(state.cart.get(id)||0)-1; if(v<=0) state.cart.delete(id); else state.cart.set(id,v); renderCart(); updateCartBadge(); }
    });

    // Newsletter (demo)
    document.getElementById('newsletter').addEventListener('submit', (e)=>{
      e.preventDefault();
      const email = document.getElementById('email').value.trim();
      alert('Subscribed: '+email+' — welcome to Spice Club!');
      e.target.reset();
    });

    // Theme switcher
    const root = document.documentElement;
    function setTheme(name){
      root.classList.remove('theme-chili','theme-cardamom');
      if(name==='chili') root.classList.add('theme-chili');
      if(name==='cardamom') root.classList.add('theme-cardamom');
      localStorage.setItem('spiceTheme', name);
    }
    document.querySelectorAll('.swatch').forEach(s=>{
      s.addEventListener('click', ()=> setTheme(s.dataset.theme));
      s.addEventListener('keypress', (e)=>{ if(e.key==='Enter') setTheme(s.dataset.theme); });
    });
    (function init(){
      const saved = localStorage.getItem('spiceTheme'); if(saved) setTheme(saved);
      renderProducts(); updateCartBadge();
    })();
  </script>
</body>
</html>
