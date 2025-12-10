// <![CDATA[  <-- For SVG support
if ("WebSocket" in window) {
  (function () {
    function refreshCSS() {
      var sheets = [].slice.call(document.getElementsByTagName("link"));
      var head = document.getElementsByTagName("head")[0];
      for (var i = 0; i < sheets.length; ++i) {
        var elem = sheets[i];
        var parent = elem.parentElement || head;
        parent.removeChild(elem);
        var rel = elem.rel;
        if (
          (elem.href && typeof rel != "string") ||
          rel.length == 0 ||
          rel.toLowerCase() == "stylesheet"
        ) {
          var url = elem.href.replace(/(&|\?)_cacheOverride=\d+/, "");
          elem.href =
            url +
            (url.indexOf("?") >= 0 ? "&" : "?") +
            "_cacheOverride=" +
            new Date().valueOf();
        }
        parent.appendChild(elem);
      }
    }
    var protocol = window.location.protocol === "http:" ? "ws://" : "wss://";
    var address =
      protocol + window.location.host + window.location.pathname + "/ws";
    var socket = new WebSocket(address);
    socket.onmessage = function (msg) {
      if (msg.data == "reload") window.location.reload();
      else if (msg.data == "refreshcss") refreshCSS();
    };
    if (
      sessionStorage &&
      !sessionStorage.getItem("IsThisFirstTime_Log_From_LiveServer")
    ) {
      console.log("Live reload enabled.");
      sessionStorage.setItem("IsThisFirstTime_Log_From_LiveServer", true);
    }
  })();
} else {
  console.error(
    "Upgrade your browser. This Browser is NOT supported WebSocket for Live-Reloading."
  );
}
// ]]>

:root {
  --accent: #0b84ff;
  --bg: #0f1720;
  --card: #0b1220;
  --muted: #9aa6b2;
}
* {
  box-sizing: border-box;
}
body {
  margin: 0;
  font-family: Inter, system-ui, -apple-system, "Segoe UI", Roboto,
    "Helvetica Neue";
  background: linear-gradient(180deg, #071024 0%, #0f1720 100%);
  color: #e6eef6;
  line-height: 1.5;
}
.wrap {
  max-width: 980px;
  margin: 36px auto;
  padding: 28px;
}

header {
  display: flex;
  gap: 20px;
  align-items: center;
}

.avatar {
  width: 200px;
  height: 150px;
  border-radius: 14px;
  /* background: linear-gradient(90deg, var(--accent), #5ad0ff); */
  display: flex;
  align-items: center;
  justify-content: center;
  font-weight: 700;
  color: #021;
  box-shadow: 0 6px 20px rgba(11, 132, 255, 0.12);
}

.avatar img {
  width: 100%;
  height: 100%;
  border-radius: 14px;
  object-fit: cover;
}

h1 {
  margin: 0;
  font-size: 22px;
}

p.lead {
  margin: 6px 0 18px;
  color: var(--muted);
}

.grid {
  display: grid;
  grid-template-columns: 1fr 320px;
  gap: 24px;
  margin-top: 18px;
}

.card {
  background: linear-gradient(
    180deg,
    rgba(255, 255, 255, 0.02),
    rgba(255, 255, 255, 0.01)
  );
  border-radius: 12px;
  padding: 18px;
}

.section-title {
  color: var(--accent);
  font-weight: 600;
  margin-bottom: 12px;
}

.skills {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
}

.chip {
  background: #0a1220;
  padding: 8px 10px;
  border-radius: 999px;
  font-size: 13px;
  color: var(--muted);
  border: 1px solid rgba(255, 255, 255, 0.03);
}

.projects {
  display: flex;
  flex-direction: column;
  gap: 10px;
}

.project {
  padding: 12px;
  border-radius: 10px;
  background: rgba(255, 255, 255, 0.02);
  border: 1px solid rgba(255, 255, 255, 0.02);
}

a.btn {
  display: inline-block;
  padding: 10px 14px;
  border-radius: 10px;
  background: var(--accent);
  color: #021;
  text-decoration: none;
  font-weight: 600;
  margin-top: 12px;
}

footer {
  margin-top: 26px;
  color: var(--muted);
  font-size: 13px;
}

@media (max-width: 880px) {
  .grid {
    grid-template-columns: 1fr;
  }
  .avatar {
    width: 72px;
    height: 72px;
  }
}

<!-- index.html -->
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width,initial-scale=1" />
    <title>Eric NDENGUE — AI & Prompt Engineering</title>
    <meta
      name="description"
      content="AI Prompt Engineer • Chatbots • Automation • Front-End Dev — Based in Yaoundé, Cameroon"
    />
    <link rel="stylesheet" href="style.css" />
  </head>
  <body>
    <div class="wrap">
      <header>
        <div class="avatar">
          <img src="photo/Eric-profile.jpg" alt="" />
        </div>
        <div>
          <h1>Eric NDENGUE — AI • Prompt Engineer • Front-End Dev</h1>
          <p class="lead">
            I build AI chatbots, automations and intelligent web experiences for
            local businesses and international clients. Based in Yaoundé,
            Cameroon 🇨🇲 — Available for freelance work.
          </p>
          <a class="btn" href="mailto:ton.email@example.com"
            >Contact me — Let's talk</a
          >
        </div>
      </header>

      <div class="grid">
        <!-- Left column -->
        <div>
          <div class="card">
            <div class="section-title">About me</div>
            <p>
              Front-End developer & Prompt Engineer. I combine UI skills with AI
              prompt architecture to deliver chatbots, automations and content
              generation systems that help small businesses save time and
              increase revenue.
            </p>
          </div>

          <div class="card" style="margin-top: 14px">
            <div class="section-title">Key services</div>
            <ul style="margin: 0; padding-left: 18px; color: var(--muted)">
              <li>WhatsApp & Website Chatbots (Design + Integration)</li>
              <li>AI Automations (Make / Zapier)</li>
              <li>Prompt engineering & system prompts</li>
              <li>Content generation for social media</li>
              <li>Front-end development with AI features</li>
            </ul>
          </div>

          <div class="card" style="margin-top: 14px">
            <div class="section-title">
              Selected projects • Ready to deliver
            </div>
            <div class="projects">
              <div class="project">
                <strong>1.</strong> WhatsApp Chatbot for Restaurant — Menu,
                orders, reservations.
              </div>
              <div class="project">
                <strong>2.</strong> AI FAQ Widget for WordPress site — Instant
                answers, fallback to agent.
              </div>
              <div class="project">
                <strong>3.</strong> Social Content Generator — 30 posts +
                captions for local stores.
              </div>
              <div class="project">
                <strong>4.</strong> Appointment Bot — Booking + calendar sync
                for salons.
              </div>
            </div>
          </div>

          <div class="card" style="margin-top: 14px">
            <div class="section-title">How I work</div>
            <ol style="margin: 0; padding-left: 18px; color: var(--muted)">
              <li>Discovery call → understand the business</li>
              <li>Design conversation flow & system prompts</li>
              <li>Develop & test (WhatsApp / website)</li>
              <li>Deliver + training + 7-day support</li>
            </ol>
          </div>
        </div>

        <!-- Right column -->
        <aside>
          <div class="card">
            <div class="section-title">Skills</div>
            <div class="skills" style="margin-bottom: 12px">
              <span class="chip">Prompt Engineering</span>
              <span class="chip">Chatbot Design</span>
              <span class="chip">Make / Zapier</span>
              <span class="chip">HTML / CSS / JS</span>
              <span class="chip">React (basic)</span>
              <span class="chip">API integration</span>
              <span class="chip">Content Strategy</span>
            </div>

            <div class="section-title">Contact</div>
            <p style="margin: 0; color: var(--muted)">
              Email: <strong>ericmenelik@gmail.com</strong><br />WhatsApp:
              <strong>+237 699 66 57 56</strong><br />Location: Yaoundé,
              Cameroon
            </p>
            <a class="btn" href="mailto:ericmenelik@gmail.com">Hire me</a>
          </div>

          <div class="card" style="margin-top: 14px">
            <div class="section-title">Testimonials</div>
            <p style="margin: 0; color: var(--muted)">
              "Fast, professional and delivered a working chatbot that doubled
              our orders." — Local Restaurant
            </p>
          </div>

          <div class="card" style="margin-top: 14px">
            <div class="section-title">Rates (example)</div>
            <p style="margin: 0; color: var(--muted)">
              Small Bot — $30 • Full Bot (WhatsApp + Site) — $75+ • Custom
              automation — from $100
            </p>
          </div>
        </aside>
      </div>

      <footer>
        <p>
          © <strong>Eric NDENGUE</strong> — AI Prompt Engineer & Front-End
          Developer — Available for freelance work worldwide.
        </p>
      </footer>
    </div>
    <!-- Code injected by live-server -->
    <script src="app.js"></script>
  </body>
</html>
