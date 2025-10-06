<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>TryHackMe — Beginning Your Learning Journey</title>
  <style>
    :root{
      --accent:#0b84ff;
      --bg:#0f1720;
      --card:#0b1220;
      --text:#e6eef8;
      --muted:#9fb3cf;
      --glass: rgba(255,255,255,0.03);
      --maxw:1100px;
      font-family: Inter, "Segoe UI", Roboto, "Helvetica Neue", Arial;
    }
    html,body{height:100%}
    body{
      margin:0;
      background: linear-gradient(180deg,#071024 0%, #071b2a 100%);
      color:var(--text);
      -webkit-font-smoothing:antialiased;
      -moz-osx-font-smoothing:grayscale;
      line-height:1.5;
      padding:28px;
      display:flex;
      justify-content:center;
      font-size:16px;
    }
    .wrap{
      width:100%;
      max-width:var(--maxw);
      background: linear-gradient(180deg, rgba(255,255,255,0.02), rgba(255,255,255,0.01));
      border-radius:12px;
      box-shadow: 0 8px 30px rgba(2,8,23,0.6);
      padding:28px;
      box-sizing:border-box;
      border:1px solid rgba(255,255,255,0.03);
    }
    header{display:flex;gap:18px;align-items:center}
    header h1{margin:0;font-size:22px}
    header p{margin:0;color:var(--muted);font-size:13px}
    nav{margin-top:18px; display:flex; gap:8px; flex-wrap:wrap}
    nav a{
      text-decoration:none;
      color:var(--accent);
      border:1px dashed rgba(11,132,255,0.12);
      padding:6px 10px;border-radius:8px;font-size:13px;
    }
    section{margin-top:20px;background:var(--glass);padding:18px;border-radius:10px;border:1px solid rgba(255,255,255,0.02)}
    h2{margin-top:0;color:#dff0ff}
    .muted{color:var(--muted);font-size:14px}
    pre.command{
      background:rgba(0,0,0,0.35);
      padding:12px;border-radius:8px;overflow:auto;color:#dff;
      border:1px solid rgba(255,255,255,0.02);
      margin:12px 0;font-family:ui-monospace, SFMono-Regular, Menlo, Monaco, "Roboto Mono", monospace;
    }
    .grid{display:grid;grid-template-columns:1fr 360px;gap:18px}
    @media(max-width:980px){ .grid{grid-template-columns:1fr} .side{order:2} }
    .card{background:linear-gradient(180deg, rgba(255,255,255,0.01), rgba(255,255,255,0.00)); padding:14px;border-radius:10px;border:1px solid rgba(255,255,255,0.02)}
    .thumb{width:100%;border-radius:8px;box-shadow:0 6px 20px rgba(2,8,23,0.6);border:1px solid rgba(255,255,255,0.02)}
    .video-wrap{border-radius:10px; overflow:hidden; border:1px solid rgba(255,255,255,0.03)}
    .flag{display:inline-block;background:rgba(11,132,255,0.12); padding:6px 10px;border-radius:999px;color:var(--accent);font-weight:600}
    footer{margin-top:18px;color:var(--muted);font-size:13px}
    ul.clean{padding-left:18px}
    .small{font-size:13px;color:var(--muted)}
    .note{background:rgba(255,255,255,0.02); padding:10px;border-radius:8px;border-left:4px solid rgba(11,132,255,0.16); margin:12px 0}
  </style>
</head>
<body>
  <div class="wrap" role="main">
    <header>
      <div>
        <h1>TryHackMe — Beginning Your Learning Journey</h1>
        <p class="muted">A short walkthrough documenting Gobuster usage, the hidden bank-transfer page and the lab flag.</p>
      </div>
    </header>

    <nav>
      <a href="#overview">Overview</a>
      <a href="#answers">Quick answers / flags</a>
      <a href="#prereqs">Prerequisites</a>
      <a href="#gobuster">Gobuster</a>
      <a href="#media">Screenshots & Video</a>
      <a href="#notes">Ethics</a>
    </nav>

    <div class="grid" style="margin-top:18px">
      <main>
        <section id="overview" class="card">
          <h2>Overview</h2>
          <p class="muted">This TryHackMe room demonstrates how to enumerate a target web application to find hidden pages (admin portals, transfer endpoints, etc.). The main tool in this exercise is <strong>Gobuster</strong>.</p>

          <ul class="clean">
            <li>Use Gobuster to find hidden pages on <code>fakebank.thm</code>.</li>
            <li>Locate the hidden transfer page <code>/bank-transfer</code>.</li>
            <li>Use the page to perform a transfer and obtain the challenge flag.</li>
          </ul>
        </section>

        <section id="answers" class="card" style="margin-top:16px">
          <h2>Quick answers / flags</h2>
          <p><strong>Which process simulates a hacker's actions to find vulnerabilities?</strong><br>
            <span class="flag">Offensive Security</span> <span class="small"> (you typed: <code>offsensive security</code> — corrected)</span>
          </p>

          <p style="margin-top:10px"><strong>Flag found after bank transfer:</strong><br>
            <code>bank-hacked</code></p>
        </section>

        <section id="prereqs" class="card">
          <h2>Prerequisites</h2>
          <ul>
            <li>TryHackMe lab machine (browser + VM)</li>
            <li>Terminal access in the lab</li>
            <li>Gobuster installed (or install it on the VM)</li>
            <li>A wordlist file (e.g., <code>wordlist.txt</code>)</li>
          </ul>
        </section>

        <section id="gobuster" class="card" style="margin-top:16px">
          <h2>Your First Hack — Gobuster</h2>

          <h3>Step 1 — Open a terminal</h3>
          <p class="muted">In the lab environment, open the Terminal window available to your TryHackMe instance.</p>

          <h3>Step 2 — Run Gobuster to discover hidden pages</h3>
          <pre class="command">gobuster dir -u http://fakebank.thm -w wordlist.txt</pre>
          <p class="muted">Explanation: <code>dir</code> is the directory enumeration mode, <code>-u</code> specifies the URL and <code>-w</code> provides the wordlist file.</p>

          <h3>Step 3 — Use the discovered page</h3>
          <p>When Gobuster finds <code>/bank-transfer</code>, open it in the browser:</p>
          <pre class="command">http://fakebank.thm/bank-transfer</pre>

          <p>Perform the transfer:</p>
          <ul>
            <li><strong>From:</strong> <code>2276</code></li>
            <li><strong>To:</strong> <code>8881</code></li>
            <li><strong>Amount:</strong> <code>2000</code></li>
          </ul>

          <p>Then check your account page — the flag <code>bank-hacked</code> should appear above your balance (you may need to refresh).</p>

          <h4 style="margin-top:12px">Example Gobuster output (simulated)</h4>
          <pre class="command">/admin (Status: 200)
/images (Status: 200)
/bank-transfer (Status: 200)</pre>

        </section>

        <section id="media" class="card" style="margin-top:16px">
          <h2>Screenshots & Recording (playable)</h2>

          <p class="small">The video is hosted in your GitHub repo and served via <code>raw.githubusercontent.com</code>. When viewed in a browser the HTML5 player will play the MP4 directly.</p>

          <div class="video-wrap" style="margin-top:12px">
            <!-- Raw GitHub raw URL -->
            <video controls width="100%" preload="metadata">
              <source src="https://raw.githubusercontent.com/nihanth6721/TryHackme_blogs/main/Pre%20Security/Storage/Offensive%20security/Screen%20Recording%202025-10-06%20213952.mp4" type="video/mp4">
              Your browser does not support the video element. Open the recording here:
              <a href="https://github.com/nihanth6721/TryHackme_blogs/blob/main/Pre%20Security/Storage/Offensive%20security/Screen%20Recording%202025-10-06%20213952.mp4" target="_blank" rel="noopener">Open on GitHub</a>
            </video>
          </div>

          <div style="display:grid; grid-template-columns:repeat(auto-fit,minmax(200px,1fr)); gap:12px; margin-top:14px">
            <figure>
              <img class="thumb" alt="Gobuster / terminal screenshot" src="https://raw.githubusercontent.com/nihanth6721/TryHackme_blogs/main/Pre%20Security/Storage/Offensive%20security/Screenshot%202025-10-06%20214150.png">
              <figcaption class="small muted" style="margin-top:6px">Gobuster / terminal screenshot</figcaption>
            </figure>

            <figure>
              <img class="thumb" alt="bank-transfer page screenshot" src="https://raw.githubusercontent.com/nihanth6721/TryHackme_blogs/main/Pre%20Security/Storage/Offensive%20security/Screenshot%202025-10-06%20214409.png">
              <figcaption class="small muted" style="margin-top:6px">bank-transfer page</figcaption>
            </figure>

            <figure>
              <img class="thumb" alt="transfer confirmation screenshot" src="https://raw.githubusercontent.com/nihanth6721/TryHackme_blogs/main/Pre%20Security/Storage/Offensive%20security/Screenshot%202025-10-06%20214434.png">
              <figcaption class="small muted" style="margin-top:6px">transfer confirmation</figcaption>
            </figure>

            <figure>
              <img class="thumb" alt="account page with flag screenshot" src="https://raw.githubusercontent.com/nihanth6721/TryHackme_blogs/main/Pre%20Security/Storage/Offensive%20security/Screenshot%202025-10-06%20214531.png">
              <figcaption class="small muted" style="margin-top:6px">account page with the flag</figcaption>
            </figure>
          </div>
        </section>

        <section id="notes" class="card" style="margin-top:16px">
          <h2>Notes & Ethical Reminders</h2>
          <div class="note">
            <strong>Important:</strong> This is a controlled lab environment. Do not run these techniques against real websites without explicit written permission. As an ethical hacker you should report vulnerabilities responsibly.
          </div>

          <p class="small muted">If you'd like this page turned into a GitHub Pages site, I can provide a minimal <code>_config.yml</code> and optional CSS tweaks so it looks even cleaner on pages.github.io.</p>
        </section>

        <footer>
          <p class="small muted">Prepared for your TryHackMe lab notes. Video & screenshots are pulled from your repository's raw assets.</p>
        </footer>
      </main>

      <aside class="side">
        <div class="card">
          <h3>Quick reference</h3>
          <p class="muted small"><strong>Gobuster command</strong></p>
          <pre class="command">gobuster dir -u http://fakebank.thm -w wordlist.txt</pre>

          <p class="muted small" style="margin-top:8px"><strong>Transfer inputs</strong></p>
          <ul class="small">
            <li>From: <code>2276</code></li>
            <li>To: <code>8881</code></li>
            <li>Amount: <code>2000</code></li>
          </ul>

          <hr style="border:none;border-top:1px solid rgba(255,255,255,0.02);margin:12px 0">

          <p class="small muted">Raw media links (for editing):</p>
          <p class="small"><a class="small" href="https://raw.githubusercontent.com/nihanth6721/TryHackme_blogs/main/Pre%20Security/Storage/Offensive%20security/Screen%20Recording%202025-10-06%20213952.mp4" target="_blank" rel="noopener">Video (raw)</a></p>
          <p class="small"><a class="small" href="https://raw.githubusercontent.com/nihanth6721/TryHackme_blogs/main/Pre%20Security/Storage/Offensive%20security/Screenshot%202025-10-06%20214150.png" target="_blank" rel="noopener">Screenshot 1</a></p>
          <p class="small"><a class="small" href="https://raw.githubusercontent.com/nihanth6721/TryHackme_blogs/main/Pre%20Security/Storage/Offensive%20security/Screenshot%202025-10-06%20214409.png" target="_blank" rel="noopener">Screenshot 2</a></p>
          <p class="small"><a class="small" href="https://raw.githubusercontent.com/nihanth6721/TryHackme_blogs/main/Pre%20Security/Storage/Offensive%20security/Screenshot%202025-10-06%20214434.png" target="_blank" rel="noopener">Screenshot 3</a></p>
          <p class="small"><a class="small" href="https://raw.githubusercontent.com/nihanth6721/TryHackme_blogs/main/Pre%20Security/Storage/Offensive%20security/Screenshot%202025-10-06%20214531.png" target="_blank" rel="noopener">Screenshot 4</a></p>
        </div>
      </aside>
    </div>
  </div>
</body>
</html>
