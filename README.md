
<html lang="de">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Zentrum</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      margin: 0;
      background: #f8f9fa;
      color: #222;
    }
    header {
      text-align: center;
      padding: 40px 20px;
      background: linear-gradient(135deg, #e9f1ff, #ffffff);
      border-bottom: 2px solid #ddd;
    }
    header img {
      height: 80px;
      vertical-align: middle;
      margin-right: 10px;
    }
    header h1 {
      display: inline-block;
      vertical-align: middle;
      font-size: 2.5rem;
      margin: 0;
    }
    header p {
      margin: 10px 0;
      font-size: 1.1rem;
    }
    header a {
      display: inline-block;
      margin-top: 15px;
      padding: 12px 24px;
      background: #5865F2;
      color: white;
      text-decoration: none;
      border-radius: 10px;
      font-weight: bold;
      transition: 0.3s;
    }
    header a:hover {
      background: #404EED;
    }
    section {
      max-width: 900px;
      margin: 30px auto;
      padding: 20px;
      background: white;
      border-radius: 15px;
      box-shadow: 0 4px 10px rgba(0,0,0,0.05);
    }
    section h2 {
      margin-top: 0;
      color: #333;
    }
    .updates-list div {
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 8px 0;
      border-bottom: 1px solid #eee;
    }
    ul {
      padding-left: 20px;
    }
    button {
      padding: 8px 16px;
      background: #5865F2;
      color: white;
      border: none;
      border-radius: 8px;
      cursor: pointer;
      margin-top: 10px;
      transition: 0.3s;
    }
    button:hover {
      background: #404EED;
    }
    .delete-btn {
      background: transparent;
      border: none;
      color: #e74c3c;
      font-size: 1.1rem;
      cursor: pointer;
    }
    input, textarea {
      width: 100%;
      padding: 10px;
      margin-top: 8px;
      border: 1px solid #ccc;
      border-radius: 8px;
      font-size: 1rem;
    }
    footer {
      text-align: center;
      padding: 20px;
      font-size: 0.9rem;
      color: #555;
    }
  </style>
</head>
<body>

  <!-- HEADER -->
  <header>
    <img src="zentrum2.0.png" alt="Zentrum Logo">
    <h1>Zentrum</h1>
    <p>Dein Platz für Spaß, Community & Roleplay</p>
    <a href="https://discord.gg/xrUYstHgy2" target="_blank">💬 Discord beitreten</a>
  </header>

  <!-- ÜBER UNS -->
  <section id="about">
    <h2>ℹ️ Über uns</h2>
    <p>
      Hey 👋 wir sind <strong>Zentrum</strong> – deine Community für Spaß, Gaming und gemeinsame Erlebnisse!  
      Bei uns findest du eine chillige Atmosphäre, coole Leute und ein engagiertes Team.  
      <br><br>
      ✨ <strong>Was wir bieten:</strong><br>
      🎉 Spaßiger Ort für jeden, 24/7 aktiv<br>
      👥 Nette und hilfsbereite Teammitglieder<br>
      🚓 Eigener FiveM Roleplay Server<br>
      🎮 Minigames, Events & mehr<br>
      🔔 Ständige Updates & News
    </p>
  </section>

  <!-- UPDATES -->
  <section id="updates">
    <h2>🆕 Updates</h2>
    <div class="updates-list" id="updatesList">
      <p>Keine Updates vorhanden.</p>
    </div>
    <div id="updateForm" style="display:none;">
      <input type="text" id="newUpdate" placeholder="Neues Update hinzufügen">
      <button onclick="addUpdate()">➕ Hinzufügen</button>
    </div>
    <button onclick="checkPassword()">🔑 Admin-Modus aktivieren</button>
  </section>

  <!-- REGELN -->
  <section id="rules">
    <h2>📜 Regeln</h2>
    <ul>
      <li><strong>1. Respekt und Fairness:</strong> Behandle alle Mitglieder höflich.</li>
      <li><strong>2. Keine Nacktheit oder schädliche Inhalte:</strong> Verbot von pornografischen, gewaltverherrlichenden oder illegalen Materialien.</li>
      <li><strong>3. Relevanz:</strong> Themenbezogen posten, kein Spam.</li>
      <li><strong>4. Privatsphäre:</strong> Keine Weitergabe privater Daten ohne Zustimmung.</li>
      <li><strong>5. Moderationsrespekt:</strong> Anweisungen des Teams befolgen.</li>
      <li><strong>6. Sicherheit:</strong> Keine illegalen Aktivitäten oder Hacks.</li>
      <li><strong>7. Werbung:</strong> Keine Eigenwerbung ohne Erlaubnis.</li>
      <li><strong>8. Sprache:</strong> Freundlich und klar kommunizieren.</li>
      <li><strong>9. Channel-Regeln:</strong> Channels nur zweckgemäß nutzen.</li>
      <li><strong>10. Datenschutz & Transparenz:</strong> Moderationsentscheidungen werden erklärt, Feedback willkommen.</li>
    </ul>
    <p>👉 Lies auch die offiziellen <a href="https://discord.com/terms" target="_blank">Discord ToS</a></p>
  </section>

  <!-- TEAM -->
  <section id="team">
    <h2>👥 Unser Zentrum Team</h2>
    <p>Hier findest du alle unsere Teammitglieder</p>

    <h3>👑 Owner</h3>
    <ul><li>[₲ⱠӾ₦] ₴Ɇ₵ɄⱤł₮Ɏ</li></ul>

    <h3>🛠 Administrator</h3>
    <ul><li>Julian</li></ul>

    <h3>💻 Entwickler</h3>
    <ul><li>[₲ⱠӾ₦] 𝐁𝐥𝐱𝐳𝐞</li><li>[₲ⱠӾ₦] Paul</li></ul>

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

  <!-- BEWERBUNG -->
  <section id="apply">
    <h2>🚀 Team bewerben</h2>
    <p>Du willst Teil des Teams werden? Bewirb dich direkt im Discord:</p>
    <a href="https://discordapp.com/channels/1340316561637900288/1415075487767859230" 
       target="_blank" class="btn">👥 Zum Bewerbungs-Channel</a>
  </section>

  <!-- KONTAKT -->
  <section id="contact">
    <h2>📩 Kontakt</h2>
    <p>Fragen oder Probleme mit der Website? Schreib uns hier:</p>
    <form action="https://formspree.io/f/xkgqwvgn" method="POST">
      <label for="name">Dein Name:</label><br>
      <input type="text" id="name" name="name" required><br><br>

      <label for="email">Deine E-Mail:</label><br>
      <input type="email" id="email" name="email" required><br><br>

      <label for="message">Deine Nachricht:</label><br>
      <textarea id="message" name="message" rows="5" required></textarea><br><br>

      <button type="submit">Absenden</button>
    </form>
  </section>

  <!-- FOOTER -->
  <footer>
    <p>© 2025 Zentrum – Alle Rechte vorbehalten.</p>
  </footer>

  <!-- SCRIPT -->
  <script>
    // Updates beim Laden anzeigen
    window.onload = function() {
      loadUpdates();
    };

    function loadUpdates() {
      const savedUpdates = JSON.parse(localStorage.getItem("zentrumUpdates")) || [];
      const updatesList = document.getElementById("updatesList");

      if (savedUpdates.length === 0) {
        updatesList.innerHTML = "<p>Keine Updates vorhanden.</p>";
      } else {
        updatesList.innerHTML = "";
        savedUpdates.forEach((update, index) => {
          addUpdateToDOM(update, index);
        });
      }
    }

    function checkPassword() {
      const pw = prompt("Bitte Admin-Passwort eingeben:");
      if (pw === "PashaV") {
        document.getElementById("updateForm").style.display = "block";
        alert("Admin-Modus aktiviert!");
      } else {
        alert("Falsches Passwort!");
      }
    }

    function addUpdate() {
      const input = document.getElementById("newUpdate");
      const text = input.value.trim();

      if (text) {
        let savedUpdates = JSON.parse(localStorage.getItem("zentrumUpdates")) || [];
        savedUpdates.push(text);
        localStorage.setItem("zentrumUpdates", JSON.stringify(savedUpdates));

        loadUpdates(); // Liste neu aufbauen
        input.value = "";
      }
    }

    function addUpdateToDOM(text, index) {
      const updatesList = document.getElementById("updatesList");

      const div = document.createElement("div");

      const p = document.createElement("span");
      p.textContent = text;

      const delBtn = document.createElement("button");
      delBtn.textContent = "❌";
      delBtn.classList.add("delete-btn");
      delBtn.onclick = function() {
        deleteUpdate(index);
      };

      div.appendChild(p);
      div.appendChild(delBtn);
      updatesList.appendChild(div);
    }

    function deleteUpdate(index) {
      let savedUpdates = JSON.parse(localStorage.getItem("zentrumUpdates")) || [];
      savedUpdates.splice(index, 1); // Löscht 1 Element
      localStorage.setItem("zentrumUpdates", JSON.stringify(savedUpdates));
      loadUpdates();
    }
  </script>

</body>
</html>
