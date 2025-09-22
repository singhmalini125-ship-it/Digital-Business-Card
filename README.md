# Digital-Business-Card
<!--
Digital Business Card - single-file website
Save this as `index.html` and push to a GitHub repo (root or gh-pages branch).
To publish on GitHub Pages: create a repo, push this file as index.html on main branch, then enable Pages in repo settings (Source: main / root). Your site will be at https://<username>.github.io/<repo>/

Customize: change the name, title, headline, photo (replace the data-src or use an image URL), social links, colors.
-->

<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Malini Singh — Digital Business Card</title>
  <meta name="description" content="Digital business card for Malini Singh — contact, links, and vCard download." />
  <link rel="icon" href="data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 100 100'%3E%3Ctext y='0.9em' font-size='90'%3E%F0%9F%92%BB%3C/text%3E%3C/svg%3E">
  <style>
    :root{--bg:#0f1724;--card:#0b1220;--muted:#98a0b3;--accent:#6ee7b7;--glass: rgba(255,255,255,0.04)}
    *{box-sizing:border-box}
    html,body{height:100%}
    body{margin:0;font-family:Inter,ui-sans-serif,system-ui,-apple-system,'Segoe UI',Roboto,'Helvetica Neue',Arial;color:#e6eef8;background:linear-gradient(180deg,#071029 0%, #041627 100%);display:flex;align-items:center;justify-content:center;padding:24px}
    .card{width:100%;max-width:920px;background:linear-gradient(180deg, rgba(255,255,255,0.02), rgba(255,255,255,0.01));border-radius:18px;padding:28px;display:grid;grid-template-columns:220px 1fr;gap:24px;box-shadow:0 10px 35px rgba(2,6,23,0.6)}
    .avatar{width:200px;height:200px;border-radius:16px;overflow:hidden;display:flex;align-items:center;justify-content:center;background:var(--glass);border:1px solid rgba(255,255,255,0.03)}
    .avatar img{width:100%;height:100%;object-fit:cover}
    header h1{margin:0;font-size:24px}
    header p{margin:6px 0 14px;color:var(--muted)}
    .roles{display:flex;gap:8px;flex-wrap:wrap;margin-bottom:16px}
    .role{background:rgba(255,255,255,0.03);padding:6px 10px;border-radius:999px;font-size:13px;color:var(--muted)}
    .links{display:flex;gap:12px;flex-wrap:wrap}
    .btn{display:inline-flex;align-items:center;gap:8px;padding:10px 14px;border-radius:12px;background:rgba(255,255,255,0.02);border:1px solid rgba(255,255,255,0.03);text-decoration:none;color:inherit;font-weight:600}
    .btn.small{padding:8px 10px;font-size:13px}
    .contact{display:flex;flex-direction:column;gap:10px;margin-top:12px}
    .meta{color:var(--muted);font-size:14px}
    .socials{display:flex;gap:8px;margin-top:8px}
    .icon-btn{width:44px;height:44px;border-radius:10px;display:inline-flex;align-items:center;justify-content:center;background:rgba(255,255,255,0.02);border:1px solid rgba(255,255,255,0.03);text-decoration:none;color:inherit}
    footer{margin-top:18px;color:var(--muted);font-size:13px}
    .copy{cursor:pointer}
    .actions{display:flex;gap:10px;flex-wrap:wrap;margin-top:10px}
    @media(max-width:720px){.card{grid-template-columns:1fr;align-items:center;text-align:center}.avatar{margin:0 auto}.contact{align-items:center}.links{justify-content:center}.socials{justify-content:center}}
  </style>
</head>
<body>
  <main class="card" role="main">
    <aside>
      <div class="avatar" aria-hidden="true">
        <img src="https://images.unsplash.com/photo-1545996124-1e1a2f6b2f0b?q=80&w=800&auto=format&fit=crop&crop=faces" alt="Malini Singh portrait"/>
      </div>
      <div class="contact" style="margin-top:14px">
        <div class="meta">Based in: <strong>New Delhi, India</strong></div>
        <div class="meta">Open to: <strong>Freelance / Collaborations</strong></div>
        <div class="actions">
          <a class="btn small" id="callBtn" href="tel:+911234567890">Call</a>
          <a class="btn small" id="emailBtn" href="mailto:hello@example.com">Email</a>
          <button class="btn small" id="copyBtn">Copy Email</button>
        </div>
      </div>
    </aside>

    <section>
      <header>
        <h1>Malini Singh <span style="font-weight:500;color:var(--muted);font-size:15px">— Product Designer</span></h1>
        <p>Designing delightful web & mobile experiences. Focused on UX strategy, prototyping and accessible interfaces.</p>
      </header>

      <div class="roles">
        <span class="role">UX Design</span>
        <span class="role">Product</span>
        <span class="role">Figma</span>
        <span class="role">Front-end</span>
      </div>

      <div class="links">
        <a class="btn" href="https://www.example.com" target="_blank" rel="noopener">Portfolio</a>
        <a class="btn" id="vcardBtn" href="#">Download vCard</a>
        <a class="btn" href="resume.pdf" target="_blank">Resume (PDF)</a>
      </div>

      <div style="margin-top:18px">
        <div style="display:flex;align-items:center;gap:12px;flex-wrap:wrap">
          <div style="min-width:0;flex:1">
            <strong>About</strong>
            <p class="meta" style="margin:6px 0 0">I help teams ship cleaner, more accessible products through user research, iterative prototyping and design systems.</p>
          </div>
        </div>

        <div class="socials" aria-label="social links">
          <a class="icon-btn" href="https://github.com/yourusername" target="_blank" rel="noopener" title="GitHub">
            <!-- GitHub SVG -->
            <svg width="18" height="18" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg" aria-hidden>
              <path d="M12 .5C5.73.5.9 5.33.9 11.6c0 4.78 3.09 8.84 7.38 10.27.54.1.74-.24.74-.53 0-.26-.01-.95-.01-1.86-3 .65-3.64-1.43-3.64-1.43-.49-1.25-1.19-1.58-1.19-1.58-.97-.67.07-.66.07-.66 1.07.08 1.63 1.1 1.63 1.1.95 1.62 2.5 1.15 3.11.88.1-.69.37-1.15.67-1.42-2.4-.27-4.93-1.2-4.93-5.34 0-1.18.42-2.14 1.11-2.9-.11-.27-.48-1.35.11-2.81 0 0 .91-.29 2.98 1.1.87-.24 1.8-.36 2.73-.36.93 0 1.86.12 2.73.36 2.07-1.39 2.98-1.1 2.98-1.1.59 1.46.22 2.54.11 2.81.69.76 1.11 1.72 1.11 2.9 0 4.15-2.54 5.07-4.96 5.33.38.33.72.98.72 1.98 0 1.43-.01 2.58-.01 2.93 0 .3.2.64.75.53C20 20.44 23.1 16.38 23.1 11.6 23.1 5.33 18.27.5 12 .5z" fill="currentColor"/>
            </svg>
          </a>
          <a class="icon-btn" href="https://www.linkedin.com/in/yourprofile" target="_blank" rel="noopener" title="LinkedIn">
            <!-- LinkedIn SVG -->
            <svg width="18" height="18" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg" aria-hidden>
              <path d="M4.98 3.5C4.98 4.88 3.88 6 2.5 6A2 2 0 010 4.99 2 2 0 012.5 3C3.88 3 4.98 4.12 4.98 5.5zM0 8.99h5V24H0V8.99zM8.5 8.99h4.8v2.05h.07c.67-1.26 2.3-2.59 4.74-2.59C23.2 8.45 24 11.08 24 14.63V24h-5.1v-8.05c0-1.92-.04-4.39-2.68-4.39-2.68 0-3.09 2.1-3.09 4.26V24H8.5V8.99z" fill="currentColor"/>
            </svg>
          </a>
          <a class="icon-btn" href="mailto:hello@example.com" title="Email" id="emailIcon">
            <!-- Mail SVG -->
            <svg width="18" height="18" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg" aria-hidden>
              <path d="M20 4H4c-1.1 0-2 .9-2 2v12c0 1.1.9 2 2 2h16c1.1 0 2-.9 2-2V6c0-1.1-.9-2-2-2zm0 4l-8 5-8-5V6l8 5 8-5v2z" fill="currentColor"/>
            </svg>
          </a>
        </div>
      </div>

      <footer>
        <div>Want this as a QR? <button class="btn small" id="qrBtn">Generate QR</button></div>
        <div style="margin-top:8px">Built with ❤️ · <span class="meta">You can host on GitHub Pages</span></div>
      </footer>
    </section>
  </main>

  <script>
    // Basic interactivity: copy email, generate vCard & QR
    const email = 'hello@example.com';
    const phone = '+91 12345 67890';
    document.getElementById('copyBtn').addEventListener('click', async ()=>{
      try{ await navigator.clipboard.writeText(email); alert('Email copied to clipboard'); }catch(e){ prompt('Copy email', email); }
    });
    document.getElementById('emailBtn').href = `mailto:${email}`;
    document.getElementById('callBtn').href = `tel:${phone.replace(/\s+/g,'')}`;

    // vCard generation and download
    document.getElementById('vcardBtn').addEventListener('click', (e)=>{
      e.preventDefault();
      const vcard = `BEGIN:VCARD\nVERSION:3.0\nN:Singh;Malini;;;\nFN:Malini Singh\nORG:Your Company\nTITLE:Product Designer\nTEL;TYPE=WORK,VOICE:${phone}\nEMAIL;TYPE=PREF,INTERNET:${email}\nURL:https://www.example.com\nADR:;;New Delhi;;;India\nEND:VCARD`;
      const blob = new Blob([vcard], {type: 'text/vcard'});
      const url = URL.createObjectURL(blob);
      const a = document.createElement('a'); a.href = url; a.download = 'MaliniSingh.vcf'; document.body.appendChild(a); a.click(); a.remove(); URL.revokeObjectURL(url);
    });

    // QR generation using Google Chart API (simple, no libs)
    document.getElementById('qrBtn').addEventListener('click', ()=>{
      const data = `MECARD:N:Malini Singh;ORG:Your Company;TEL:${phone};EMAIL:${email};;`;
      const src = `https://chart.googleapis.com/chart?cht=qr&chs=300x300&chl=${encodeURIComponent(data)}`;
      const w = window.open('', '_blank');
      w.document.write(`<title>QR - Malini Singh</title><img src="${src}" alt="QR code">`);
    });
  </script>
</body>
</html>



