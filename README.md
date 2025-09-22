# Digital Business Card for Local Shops

```
/ (root)
├─ index.html         # single-file UI for the digital card + admin editor (static)
├─ styles.css         # styles
├─ script.js          # client-side logic (localStorage persistence)
├─ images/            # optional product/shop images
└─ README.md          # quickstart + deploy to GitHub Pages
```

---

## Goals / Problems this solves

* **Low technical ability:** shop owners can edit their card directly in the browser using a built-in editor (no servers required).
* **Cost & maintenance:** static site that can be hosted free on GitHub Pages.
* **Discoverability:** shareable link + QR code for offline promotion.
* **Timely updates:** update offers/promotions instantly and save locally (or commit to GitHub for permanent changes).
* **Direct contact:** one-tap Call / WhatsApp buttons for customers.

---

## `index.html`

```html
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Digital Card — Local Shop</title>
  <link rel="stylesheet" href="styles.css">
</head>
<body>
  <header class="top">
    <div class="wrap">
      <h1 id="shopName">My Local Shop</h1>
      <button id="editBtn" class="small">Edit</button>
    </div>
  </header>

  <main class="wrap card">
    <div class="row">
      <div class="left">
        <img id="shopLogo" src="images/default-shop.png" alt="logo" class="logo" onerror="this.style.display='none'">
        <p id="tagline">Quality products • Friendly service</p>

        <div class="contact">
          <a id="callBtn" class="action" href="#">📞 Call</a>
          <a id="waBtn" class="action" href="#">💬 WhatsApp</a>
          <a id="mapBtn" class="action" href="#" target="_blank">📍 Directions</a>
        </div>

        <h3>About</h3>
        <p id="about">We are a family-run neighbourhood shop offering daily essentials and friendly service.</p>

        <h3>Hours</h3>
        <p id="hours">Mon–Sun • 9:00 AM – 9:00 PM</p>

        <h3>Offers / Announcements</h3>
        <div id="offers" class="offers">
          <p>No current offers — click Edit to add one.</p>
        </div>

        <div class="qr">
          <h4>Share / Print QR</h4>
          <img id="qrImg" src="" alt="QR code" />
          <p class="note">Scan to open this card in a browser</p>
        </div>
      </div>

      <aside class="right">
        <h3>Products</h3>
        <div id="products" class="products">
          <p>Add products in Edit mode — include image filename if you uploaded images/</p>
        </div>

        <h3>Social</h3>
        <div id="social" class="social">
          <p>No social links set.</p>
        </div>

        <h3>Share</h3>
        <div class="share">
          <button id="copyLink" class="small">Copy link</button>
          <a id="openNew" class="small" target="_blank">Open in new tab</a>
        </div>
      </aside>
    </div>
  </main>

  <!-- Editor modal (simple) -->
  <div id="editor" class="modal" aria-hidden="true">
    <div class="modal-inner">
      <h2>Edit Digital Card</h2>
      <form id="editorForm">
        <label>Shop name<input name="shopName" required></label>
        <label>Tagline<input name="tagline"></label>
        <label>Phone (with country code)<input name="phone" placeholder="+91xxxxxxxxxx"></label>
        <label>WhatsApp (phone or leave blank)<input name="whatsapp" placeholder="+91xxxxxxxxxx"></label>
        <label>Address<textarea name="address" rows="2"></textarea></label>
        <label>Hours<input name="hours"></label>
        <label>About<textarea name="about" rows="3"></textarea></label>
        <label>Offers (one per line)<textarea name="offers" rows="3"></textarea></label>
        <label>Products (format: title|price|imageFilename — one per line)<textarea name="products" rows="4" placeholder="Tea|₹20|tea.jpg\nBiscuit|₹10|biscuit.jpg"></textarea></label>
        <label>Social Links (JSON or key:value lines)<textarea name="social" rows="3" placeholder="instagram:https://..\nfacebook:https://.."></textarea></label>
        <label>Logo image filename (place file in images/)<input name="logo"></label>
        <div class="modal-actions">
          <button type="button" id="cancel">Cancel</button>
          <button type="submit" class="primary">Save</button>
          <button type="button" id="resetBtn">Reset data</button>
        </div>
      </form>
    </div>
  </div>

  <footer class="foot">
    <div class="wrap">Built for local shops • Host on GitHub Pages • Edit locally & commit for permanent public changes</div>
  </footer>

  <script src="script.js"></script>
</body>
</html>
```

---

## `styles.css`

```css
:root{--bg:#f7f9fc;--card:#fff;--accent:#0b74de;--muted:#666}
*{box-sizing:border-box}
body{margin:0;font-family:Inter,system-ui,Arial;background:var(--bg);color:#111}
.wrap{max-width:980px;margin:0 auto;padding:18px}
.top{background:#fff;border-bottom:1px solid #e6eef7}
.top .wrap{display:flex;align-items:center;justify-content:space-between}
.logo{width:100%;max-width:160px;border-radius:8px;margin-bottom:8px}
.card{padding:22px}
.row{display:flex;gap:20px}
.left{flex:1;background:var(--card);padding:18px;border-radius:12px;box-shadow:0 8px 24px rgba(12,24,48,0.06)}
.right{width:320px}
.contact{display:flex;gap:8px;margin:8px 0}
.action{display:inline-block;padding:8px 12px;border-radius:10px;text-decoration:none;background:linear-gradient(90deg,var(--accent),#1078d8);color:white}
.offers p{background:#fff3e0;padding:8px;border-radius:8px}
.products .item{display:flex;gap:10px;align-items:center;padding:8px;border-radius:8px;background:#fff;margin-bottom:8px}
.products img{width:64px;height:64px;object-fit:cover;border-radius:8px}
.small{padding:6px 8px;border-radius:8px}
.foot{padding:12px;text-align:center;color:var(--muted)}
.modal{position:fixed;inset:0;background:rgba(6,10,20,0.4);display:none;align-items:center;justify-content:center}
.modal[aria-hidden="false"]{display:flex}
.modal-inner{background:var(--card);padding:18px;border-radius:12px;max-width:720px;width:100%}
.modal form label{display:block;margin-bottom:8px}
.modal input,.modal textarea{width:100%;padding:8px;border-radius:6px;border:1px solid #e6edf6}
.modal-actions{display:flex;gap:8px;justify-content:flex-end;margin-top:8px}
.primary{background:var(--accent);color:#fff;border:none;padding:8px 12px;border-radius:8px}
.note{font-size:0.85rem;color:#666}
@media (max-width:880px){.row{flex-direction:column}.right{width:auto}}
```

---

## `script.js`

```js
// Simple client-side digital business card with localStorage persistence
const DEFAULT = {
  shopName: 'My Local Shop',
  tagline: 'Quality products • Friendly service',
  phone: '',
  whatsapp: '',
  address: '',
  hours: 'Mon–Sun • 9:00 AM – 9:00 PM',
  about: 'We are a family-run neighbourhood shop offering daily essentials and friendly service.',
  offers: [],
  products: [],
  social: {},
  logo: ''
}

function qs(sel){return document.querySelector(sel)}
function qsa(sel){return Array.from(document.querySelectorAll(sel))}

const E = {
  shopName: qs('#shopName'),
  tagline: qs('#tagline'),
  callBtn: qs('#callBtn'),
  waBtn: qs('#waBtn'),
  mapBtn: qs('#mapBtn'),
  about: qs('#about'),
  hours: qs('#hours'),
  offers: qs('#offers'),
  products: qs('#products'),
  social: qs('#social'),
  qrImg: qs('#qrImg'),
  openNew: qs('#openNew'),
  copyLink: qs('#copyLink'),
  editBtn: qs('#editBtn'),
  editor: qs('#editor'),
  editorForm: qs('#editorForm'),
  cancel: qs('#cancel'),
  resetBtn: qs('#resetBtn'),
  shopLogo: qs('#shopLogo')
}

function load(){
  const raw = localStorage.getItem('digitalCard_v1');
  return raw ? JSON.parse(raw) : DEFAULT;
}

function save(state){
  localStorage.setItem('digitalCard_v1', JSON.stringify(state));
}

function render(){
  const st = load();
  E.shopName.textContent = st.shopName || DEFAULT.shopName;
  E.tagline.textContent = st.tagline || '';
  E.about.textContent = st.about || '';
  E.hours.textContent = st.hours || '';

  // Contact
  E.callBtn.href = st.phone ? `tel:${st.phone}` : '#';
  E.callBtn.textContent = st.phone ? `📞 Call ${st.phone}` : '📞 Call';
  if(st.whatsapp){
    E.waBtn.href = `https://wa.me/${st.whatsapp.replace(/\D/g,'')}`;
    E.waBtn.textContent = '💬 WhatsApp';
    E.waBtn.style.display = '';
  } else {
    E.waBtn.style.display = 'none';
  }

  if(st.address){
    const q = encodeURIComponent(st.address + ' India');
    E.mapBtn.href = `https://www.google.com/maps/search/?api=1&query=${q}`;
    E.mapBtn.style.display = '';
  } else {
    E.mapBtn.style.display = 'none';
  }

  // Offers
  E.offers.innerHTML = '';
  if(st.offers && st.offers.length){
    st.offers.forEach(o => {
      const p = document.createElement('p'); p.textContent = o; E.offers.appendChild(p);
    })
  } else {
    E.offers.innerHTML = '<p>No current offers — click Edit to add one.</p>';
  }

  // Products
  E.products.innerHTML = '';
  if(st.products && st.products.length){
    st.products.forEach(prod => {
      const wrap = document.createElement('div'); wrap.className='item';
      const img = document.createElement('img'); img.src = prod.image || 'images/default-item.png'; img.onerror = ()=>{img.style.display='none'};
      const info = document.createElement('div');
      const t = document.createElement('div'); t.textContent = prod.title; t.style.fontWeight='600';
      const pr = document.createElement('div'); pr.textContent = prod.price || '';
      info.appendChild(t); info.appendChild(pr);
      wrap.appendChild(img); wrap.appendChild(info);
      E.products.appendChild(wrap);
    })
  } else {
    E.products.innerHTML = '<p>Add products in Edit mode — include image filename if you uploaded images/</p>';
  }

  // Social
  E.social.innerHTML = '';
  if(st.social && Object.keys(st.social).length){
    Object.entries(st.social).forEach(([k,v])=>{
      const a = document.createElement('a'); a.href=v; a.target='_blank'; a.textContent = k; a.style.display='block'; E.social.appendChild(a);
    })
  } else {
    E.social.innerHTML = '<p>No social links set.</p>';
  }

  // Logo
  if(st.logo){
    E.shopLogo.src = `images/${st.logo}`; E.shopLogo.style.display='block';
  } else { E.shopLogo.style.display='none' }

  // QR code points to current page URL
  const url = window.location.href;
  // Using Google Chart API for QR (simple, no server)
  E.qrImg.src = `https://chart.googleapis.com/chart?cht=qr&chs=240x240&chl=${encodeURIComponent(url)}`;

  // Share controls
  E.openNew.href = url; E.openNew.textContent = 'Open this card';
  E.copyLink.onclick = async ()=>{
    try{ await navigator.clipboard.writeText(url); alert('Link copied to clipboard') }catch(e){ prompt('Copy link', url) }
  }
}

// Editor behavior
E.editBtn.onclick = ()=>{
  const st = load();
  E.editorForm.shopName.value = st.shopName || '';
  E.editorForm.tagline.value = st.tagline || '';
  E.editorForm.phone.value = st.phone || '';
  E.editorForm.whatsapp.value = st.whatsapp || '';
  E.editorForm.address.value = st.address || '';
  E.editorForm.hours.value = st.hours || '';
  E.editorForm.about.value = st.about || '';
  E.editorForm.offers.value = (st.offers || []).join('\n');
  E.editorForm.products.value = (st.products || []).map(p=>`${p.title}|${p.price||''}|${p.image||''}`).join('\n');
  E.editorForm.social.value = Object.entries(st.social||{}).map(([k,v])=>`${k}:${v}`).join('\n');
  E.editorForm.logo.value = st.logo || '';
  E.editor.setAttribute('aria-hidden','false');
}

E.cancel.onclick = ()=>{ E.editor.setAttribute('aria-hidden','true') }

E.editorForm.onsubmit = (ev)=>{
  ev.preventDefault();
  const form = new FormData(E.editorForm);
  const st = load();
  st.shopName = form.get('shopName');
  st.tagline = form.get('tagline');
  st.phone = form.get('phone');
  st.whatsapp = form.get('whatsapp');
  st.address = form.get('address');
  st.hours = form.get('hours');
  st.about = form.get('about');
  st.offers = (form.get('offers')||'').split('\n').map(s=>s.trim()).filter(Boolean);
  st.products = (form.get('products')||'').split('\n').map(line=>{
    const [title,price,image] = line.split('|').map(s=>s?.trim());
    return title ? {title,price,image} : null;
  }).filter(Boolean);
  const soc = {};
  (form.get('social')||'').split('\n').map(l=>l.split(':')).forEach(parts=>{ if(parts[0] && parts[1]) soc[parts[0].trim()]=parts.slice(1).join(':').trim() });
  st.social = soc;
  st.logo = form.get('logo') || '';
  save(st); render();
  E.editor.setAttribute('aria-hidden','true');
}

E.resetBtn.onclick = ()=>{
  if(confirm('Reset data to defaults?')){ localStorage.removeItem('digitalCard_v1'); render(); }
}

// init
render();
```

---

## `README.md` (quickstart + deploy)

```markdown
# Digital Business Card — Local Shop Starter

This small static project helps shop owners create a shareable digital card. It's static (no server) and persists edits locally in the browser using `localStorage`. To make edits public, edit files and push to GitHub (or use a simple admin flow).

## Quickstart (locally)
1. Clone or download repository.
2. Optionally add images to `images/` (logo, product images). Default placeholder images are used if missing.
3. Open `index.html` in a browser. Click **Edit** to enter shop details, offers, and products.

## Deploy to GitHub Pages
1. Create a new repository on GitHub.
2. Push the files from this folder to the `main` branch.
3. In repo Settings → Pages: choose `main` branch and root `/` folder, Save.
4. Your site will be available at `https://<your-username>.github.io/<repo>/`.

## Making changes public
- Edits made in the in-browser editor are stored in localStorage only (per-device). To make them public to all visitors, update the `index.html` and `script.js` data defaults, or commit a JSON file and adjust code to fetch it.

## Ideas for enhancements
- Add serverless backend (Firebase) to store each shop's data persistently.
- Offer custom domains, analytics, and booking/inventory features under a paid plan.
- Multi-language UI and localized templates for different regions.

---

If you'd like, I can:
- create a ZIP of these files for download,
- convert this into a small React single-file app,
- write a GitHub Actions workflow to auto-deploy on pushes,
- or provide the exact git commands to push to your GitHub repo and enable Pages.

Happy to help — tell me which step you want next!

```
