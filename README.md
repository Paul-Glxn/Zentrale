
<html lang="de">
<head>
  <meta charset="UTF-8">
  <title>Zentrum – Community</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <style>
    /* ===== Reset & Base ===== */
    * {margin:0;padding:0;box-sizing:border-box;}
    body {
      font-family: "Segoe UI", Arial, sans-serif;
      background:#f8f9fc;
      color:#222;
      line-height:1.6;
    }
    a {color:#5865F2;text-decoration:none;}
    h1,h2,h3 {font-weight:600;margin-bottom:10px;color:#111;}

    /* ===== Layout ===== */
    header {
      text-align:center;
      padding:60px 20px;
      background:linear-gradient(135deg,#5865F2,#8892f6);
      color:white;
    }
    header h1 {font-size:2.8rem;margin-bottom:10px;}
    header p {font-size:1.2rem;margin-bottom:20px;}
    header a {
      display:inline-block;
      background:white;
      color:#5865F2;
      padding:12px 24px;
      border-radius:8px;
      font-weight:600;
      transition:0.3s;
    }
    header a:hover {background:#e7e9ff;}

    main {max-width:900px;margin:40px auto;padding:0 20px;}
    section {background:white;margin-bottom:30px;padding:25px;border-radius:12px;box-shadow:0 4px 12px rgba(0,0,0,0.05);}
    section h2 {margin-bottom:15px;color:#5865F2;}

    /* Team Styling */
    #team h3 {margin-top:15px;color:#333;}
    #team ul {list-style:none;padding-left:15px;}
    #team li {padding:3px 0;}

    /* Updates editable */
    #updates[contenteditable="true"] {
      outline:2px dashed #5865F2;
      background:#f0f2ff;
    }

    /* Footer */
    footer {
      text-align:center;
      padding:20px;
      font-size:0.9rem;
      color:#555;
    }

    /* Button */
    .btn {
      display:inline-block;
      padding:8px 16px;
      background:#5865F2;
      color:white !important;
      border-radius:6px;
      font-size:0.9rem;
      cursor:pointer;
      transition:0.3s;
    }
    .btn:hover {background:#4752c4;}
  </style>
</head>
<body>

  <header>
    <h1>Zentrum</h1>
    <p>Dein Platz für Spaß, Community & Roleplay</p>
    <a href="https://discord.gg/xrUYstHgy2" target="_blank">💬 Discord beitreten</a>
  </header>

  <main>
    <!-- Über uns -->
    <section id="about">
      <h2>Über uns</h2>
      <p>
        Hey 👋 wir sind <b>Zentrum</b>!  
        Bei uns findest du eine bunte Community mit viel Spaß, 24/7 aktiven Teamlern
        und jeder Menge Unterhaltung. Ob unser eigener FiveM Roleplay Server, spannende Minigames,
        Events oder einfach nur chillige Gespräche – hier ist für jeden etwas dabei.  
        Tauche ein, lerne neue Leute kennen und werde Teil unseres Teams!
      </p>
    </section>

    <!-- Updates -->
    <section id="updates-section">
      <h2>Updates</h2>
      <div id="updates">✏️ Melde dich als Admin an, um hier Updates einzutragen!</div>
      <button class="btn" onclick="login()">🔒 Admin Login</button>
    </section>

    <!-- Regeln -->
    <section id="rules">
      <h2>Regeln</h2>
      <h3>1. Respekt und Fairness:</h3>
      <p>Behandle alle Mitglieder mit Höflichkeit. Keine Beleidigungen, Diskriminierung oder Mrown-Larp.</p>

      <h3>2. Keine Nacktheit oder schädliche Inhalte:</h3>
      <p>Keine pornografischen, gewaltverherrlichenden oder illegalen Materialien.</p>

      <h3>3. Relevanz:</h3>
      <p>Poste themenbezogen in den passenden Channels. Spam vermeiden.</p>

      <h3>4. Privatsphäre:</h3>
      <p>Keine Weitergabe persönlicher Daten anderer ohne Zustimmung.</p>

      <h3>5. Moderationsrespekt:</h3>
      <p>Folge Anweisungen des Moderationsteams. Konflikte ruhig melden.</p>

      <h3>6. Sicherheit:</h3>
      <p>Keine Aufforderung zu illegalen Aktivitäten; keine Hacks oder Anleitungen dazu.</p>

      <h3>7. Werbung:</h3>
      <p>Keine Eigenwerbung ohne Erlaubnis der Moderation.</p>

      <h3>8. Sprache:</h3>
      <p>Klare, freundliche Kommunikation; Vermeide Troll-Verhalten.</p>

      <h3>9. Channel-Regeln:</h3>
      <p>Nutze spezielle Channels nur für deren Zweck (Ankündigungen, Diskussion, Hilfe, etc.).</p>

      <h3>10. Datenschutz & Transparenz:</h3>
      <p>Wichtige Moderationsentscheidungen werden erklärt; Feedback willkommen.</p>

      <p>👉 Lies auch die offiziellen <a href="https://discord.com/terms" target="_blank">Discord ToS</a>.</p>
    </section>

    <!-- Team -->
    <section id="team">
      <h2>👥 Unser Zentrum Team</h2>
      <p>Hier findest du alle unsere Teammitglieder</p>

      <h3>👑 Owner</h3>
      <ul><li>[₲ⱠӾ₦] ₴Ɇ₵ɄⱤł₮Ɏ</li></ul>

      <h3>🛠 Administrator</h3>
      <ul><li>Julian</li></ul>

      <h3>💻 Entwickler</h3>
      <ul>
        <li>[₲ⱠӾ₦] 𝐁𝐥𝐱𝐳𝐞</li>
        <li>[₲ⱠӾ₦] Paul</li>
      </ul>

      <h3>🛡 Moderator</h3>
      <ul><li>[₲ⱠӾ₦] Contrax</li></ul>

      <h3>🙋 Supporter</h3>
      <ul>
        <li>[₲ⱠӾ₦] alocinelia_YT</li>
        <li>[₲ⱠӾ₦] 𝐒𝐇𝐀𝐃𝐎𝐖</li>
        <li>! [₲ⱠӾ₦] Anonyme</li>
      </ul>

      <h3>🧪 Test Supporter</h3>
      <ul>
        <li>DerZocker1707</li>
        <li>PokelotlYT</li>
        <li>ENDMAGIER</li>
        <li>Alex Gaming pro YT</li>
        <li>MaxTechTV</li>
        <li>LUKASHDD</li>
        <li>Z | Waggon</li>
        <li>ZyqroX</li>
        <li>LustigeKatze</li>
        <li>Leo_the_real</li>
        <li>YourCuteFemboy</li>
      </ul>
    </section>
  </main>

  <footer>
    Zentrum © 2025 – Alle Rechte vorbehalten
  </footer>

  <script>
    // Admin Login
    function login() {
      const pw = prompt("Bitte Admin-Passwort eingeben:");
      if (pw === "PashaV") {
        document.getElementById("updates").setAttribute("contenteditable","true");
        alert("✅ Admin-Modus aktiviert. Du kannst nun Updates bearbeiten.");
      } else {
        alert("❌ Falsches Passwort!");
      }
    }

    // Speicherung in localStorage
    const updatesDiv = document.getElementById("updates");
    if(localStorage.getItem("updatesContent")){
      updatesDiv.innerHTML = localStorage.getItem("updatesContent");
    }
    updatesDiv.addEventListener("input", () => {
      localStorage.setItem("updatesContent", updatesDiv.innerHTML);
    });
  </script>
</body>
</html>
