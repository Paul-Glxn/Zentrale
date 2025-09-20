<!doctype html>
<html lang="de">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Zentrale — Discord Homepage</title>
  <meta name="description" content="Offizielle Info-Seite für unseren Discord. Updates, Team, Regeln und Ankündigungen. Bearbeiten nur mit Passwort." />
  <style>
    :root{--bg:#0b1020;--card:#0f1726;--muted:#9fb0c8;--accent:#5865f2;--glass:rgba(255,255,255,0.03);--glass-2:rgba(255,255,255,0.02)}
    *{box-sizing:border-box}
    html,body{height:100%;margin:0;font-family:Inter,ui-sans-serif,system-ui,-apple-system,"Segoe UI",Roboto,"Helvetica Neue",Arial;color:#e6eef6;background:linear-gradient(180deg,#030417 0%, #071022 100%)}
    a{color:inherit}
    .container{max-width:1100px;margin:28px auto;padding:20px;}
    header{display:flex;justify-content:space-between;align-items:center;gap:12px}
    .brand{display:flex;align-items:center;gap:12px}
    .logo{width:44px;height:44px;border-radius:10px;background:linear-gradient(135deg,var(--accent),#314cff);display:flex;align-items:center;justify-content:center;font-weight:700}
    h1{margin:0;font-size:20px}
    nav{display:flex;gap:10px}
    nav a{padding:8px 12px;border-radius:10px;background:var(--glass);text-decoration:none;font-size:14px}
    .hero{display:grid;grid-template-columns:1fr 360px;gap:20px;margin-top:20px}
    .card{background:linear-gradient(180deg,var(--card),rgba(10,16,28,0.8));padding:18px;border-radius:14px;box-shadow:0 6px 24px rgba(2,6,23,0.6)}
    .hero-left h2{margin:0 0 8px 0}
    .lead{color:var(--muted);margin-bottom:12px}
    .cta{display:flex;gap:8px;margin-top:12px}
    .btn{background:var(--accent);color:white;padding:10px 14px;border-radius:10px;border:none;cursor:pointer}
    .btn.ghost{background:transparent;border:1px solid rgba(255,255,255,0.04)}
    .stats{display:flex;gap:10px;margin-top:12px}
    .stat{background:var(--glass);padding:10px;border-radius:8px;text-align:center;min-width:100px}

    .grid{display:grid;grid-template-columns:1fr 380px;gap:18px;margin-top:18px}
    .section-title{display:flex;justify-content:space-between;align-items:center}
    .collapsible{border-radius:10px;overflow:hidden;border:1px solid rgba(255,255,255,0.03)}
    .collapsible .head{display:flex;justify-content:space-between;align-items:center;padding:12px 14px;cursor:pointer;background:linear-gradient(90deg,rgba(0,0,0,0.25),transparent)}
    .chev{transition:transform .25s}
    .body{padding:14px;border-top:1px solid rgba(255,255,255,0.02);max-height:0;overflow:hidden;transition:max-height .28s ease}
    .body.open{max-height:1000px}
    .editable{min-height:80px;border-radius:8px;padding:10px;border:1px dashed rgba(255,255,255,0.04);outline:none;background:transparent}
    .meta{font-size:13px;color:var(--muted)}

    .right .card{margin-bottom:12px}
    .member-list{display:flex;flex-direction:column;gap:6px}
    .member{display:flex;justify-content:space-between;align-items:center;padding:8px;border-radius:8px;background:var(--glass-2)}

    footer{margin-top:18px;color:var(--muted);text-align:center;font-size:13px}

    .banner{background:linear-gradient(135deg,var(--accent),#314cff);padding:28px;border-radius:14px;margin-top:28px;color:white;text-align:center}
    .banner h2{margin:0 0 12px 0;font-size:26px}
    .banner p{margin:0;font-size:16px}

    @media(max-width:980px){.hero{grid-template-columns:1fr} .grid{grid-template-columns:1fr} .container{padding:12px}}
  </style>
</head>
<body>
  <div class="container">
    <header>
      <div class="brand">
        <div class="logo">Z</div>
        <div>
          <h1>Zentrale — Discord Info</h1>
          <div class="meta">Offizielle Infoseite für unseren Discord-Server</div>
        </div>
      </div>
      <nav>
        <a href="#about">Über</a>
        <a href="#updates">Updates</a>
        <a href="#team">Team</a>
        <a href="#rules">Regeln</a>
        <button class="btn ghost" id="editToggle">🔒 Bearbeiten</button>
      </nav>
    </header>

    <div class="hero">
      <div class="card hero-left">
        <h2>Willkommen auf der Zentrale</h2>
        <p class="lead">Hey 👋 wir sind <strong>Zentrale</strong>! Bei uns kannst du Spaß haben, neue Leute kennenlernen und in einer freundlichen Community abhängen.</p>
        <ul class="lead">
          <li>😄 Spaßiger Ort für jeden</li>
          <li>🌍 24/7 aktive und nette Teamler</li>
          <li>🚓 Eigener FiveM Roleplay Server</li>
          <li>🎮 Coole Minigames & Community-Events</li>
        </ul>
        <div class="cta">
          <!-- öffnet Invite in neuem Tab -->
          <a class="btn" href="https://discord.gg/xrUYstHgy2" target="_blank" rel="noopener noreferrer">Discord beitreten</a>
          <button class="btn ghost" id="exportBtn">Exportieren</button>
        </div>
        <div class="stats" style="margin-top:18px">
          <div class="stat"><div style="font-weight:700" id="statMembers">—</div><div class="meta">Mitglieder</div></div>
          <div class="stat"><div style="font-weight:700" id="statOnline">—</div><div class="meta">Online</div></div>
        </div>
      </div>

      <aside class="right">
        <div class="card" id="invite">
          <h3>Server Einladung</h3>
          <p class="meta">Kopiere den Einladungslink oder nutze den Beitreten-Button.</p>
          <div style="display:flex;gap:8px;margin-top:10px">
            <input id="inviteLink" class="editable" value="https://discord.gg/xrUYstHgy2" style="flex:1" />
            <button class="btn" id="copyInvite">Kopieren</button>
          </div>
        </div>

        <div class="card">
          <h3>Schnellzugriff</h3>
          <div style="display:flex;flex-direction:column;gap:8px;margin-top:8px">
            <button class="btn ghost" onclick="document.getElementById('updatesSec').scrollIntoView({behavior:'smooth'})">Updates</button>
            <button class="btn ghost" onclick="document.getElementById('teamSec').scrollIntoView({behavior:'smooth'})">Team</button>
            <button class="btn ghost" onclick="document.getElementById('rulesSec').scrollIntoView({behavior:'smooth'})">Regeln</button>
          </div>
        </div>
      </aside>
    </div>

    <div class="banner">
      <h2>Über uns 💡</h2>
      <p>Wir sind die <strong>Zentrale</strong> — dein Platz für Spaß, Roleplay und Community. Ob FiveM-Roleplay, Minigames oder einfach nette Gespräche: hier findest du alles. Unser Team ist 24/7 für dich da und freut sich auf dich!</p>
    </div>

    <div class="grid">
      <main>
        <section id="about" class="card">
          <div class="section-title"><h3>Über den Server</h3><div class="meta">Kurzbeschreibung</div></div>
          <p class="meta" id="aboutText">Dieser Server ist der zentrale Treffpunkt für unsere Community. Themen: Support, Events, Kooperationen und mehr.</p>
        </section>

        <section id="updatesSec" class="collapsible" style="margin-top:12px">
          <div class="head"><div><strong>Updates</strong><div class="meta">Wichtige Änderungen & Versionshinweise</div></div><div class="chev">▶</div></div>
          <div class="body" id="updatesBody">
            <div id="updatesContent" class="editable" contenteditable="false">Keine Updates vorhanden. Klicke "🔒 Bearbeiten" und gib das Passwort ein, um Inhalte zu ändern.</div>
            <div style="display:flex;gap:8px;margin-top:10px">
              <button class="btn ghost" id="saveUpdates">Speichern</button>
              <button class="btn" id="resetUpdates">Zurücksetzen</button>
            </div>
          </div>
        </section>

        <section id="teamSec" class="collapsible" style="margin-top:12px">
          <div class="head"><div><strong>Team</strong><div class="meta">Vorstellung unserer Moderatoren</div></div><div class="chev">▶</div></div>
          <div class="body" id="teamBody">
            <div id="teamContent" class="editable" contenteditable="false">Keine Teammitglieder. Entsperren mit Passwort, um Mitglieder hinzuzufügen.</div>
            <div style="display:flex;gap:8px;margin-top:10px;align-items:center">
              <input id="newMember" class="editable" placeholder="Name hinzufügen" style="flex:1" disabled />
              <button class="btn" id="addMember" disabled>Hinzufügen</button>
            </div>
            <div style="display:flex;gap:8px;margin-top:10px">
              <button class="btn ghost" id="saveTeam">Speichern</button>
            </div>
          </div>
        </section>

        <section id="rulesSec" class="collapsible" style="margin-top:12px">
          <div class="head"><div><strong>Regeln</strong><div class="meta">Server-Regeln & Verhaltenskodex</div></div><div class="chev">▶</div></div>
          <div class="body" id="rulesBody">
            <div id="rulesContent" class="editable" contenteditable="false">1) Respektiere andere. 2) Keine Werbung ohne Erlaubnis. 3) Folgen den Moderatoren.</div>
            <div style="display:flex;gap:8px;margin-top:10px">
              <button class="btn ghost" id="saveRules">Speichern</button>
            </div>
          </div>
        </section>

      </main>

      <aside class="right">
        <div class="card">
          <h3>Mitglieder</h3>
          <div class="member-list" id="membersBox">Lädt…</div>
        </div>

        <div class="card">
          <h3>Sicherung</h3>
          <div style="display:flex;gap:8px;margin-top:8px">
            <button class="btn" id="exportJson">Export JSON</button>
            <button class="btn ghost" id="importJsonBtn">Import</button>
            <input type="file" id="fileInput" accept="application/json" style="display:none" />
          </div>
          <div class="meta" style="margin-top:8px">Daten werden lokal im Browser gespeichert (localStorage). Exportiere regelmäßig als Backup.</div>
        </div>
      </aside>
    </div>

    <footer>Passwort für Bearbeitung: <strong>PashaV</strong> — Hinweis: Passwort-Prüfung ist clientseitig und eignet sich für lokale Nutzung. Für echte Sicherheit wird ein Server benötigt.</footer>
  </div>

  <script>
    (function(){
      const PASSWORD = 'PashaV';
      const STORAGE = 'zentrale_home_v2';

      // Elements
      const editToggle = document.getElementById('editToggle');
      const updatesContent = document.getElementById('updatesContent');
      const teamContent = document.getElementById('teamContent');
      const rulesContent = document.getElementById('rulesContent');
      const membersBox = document.getElementById('membersBox');
      const statMembers = document.getElementById('statMembers');
      const statOnline = document.getElementById('statOnline');
      const inviteLink = document.getElementById('inviteLink');

      // Buttons / inputs
      const addMemberBtn = document.getElementById('addMember');
      const newMemberInput = document.getElementById('newMember');
      const saveUpdatesBtn = document.getElementById('saveUpdates');
      const saveTeamBtn = document.getElementById('saveTeam');
      const saveRulesBtn = document.getElementById('saveRules');
      const resetUpdatesBtn = document.getElementById('resetUpdates');
      const exportJsonBtn = document.getElementById('exportJson');
      const exportBtnHero = document.getElementById('exportBtn');
      const importJsonBtn = document.getElementById('importJsonBtn');
      const fileInput = document.getElementById('fileInput');
      const copyInviteBtn = document.getElementById('copyInvite');

      // initial state
      let state = {
        about: document.getElementById('aboutText').innerText,
        updates: updatesContent.innerHTML,
        team: teamContent.innerHTML,
        rules: rulesContent.innerHTML,
        members: ['Admin'],
        invite: inviteLink.value || 'https://discord.gg/xrUYstHgy2'
      };

      // load saved state
      function load(){
        try{
          const raw = localStorage.getItem(STORAGE);
          if(raw){
            const parsed = JSON.parse(raw);
            state = Object.assign(state, parsed);
          }
        }catch(e){ console.warn('load error', e) }
        applyState();
      }

      function save(){
        try{
          state.updates = updatesContent.innerHTML;
          state.team = teamContent.innerHTML;
          state.rules = rulesContent.innerHTML;
          state.invite = inviteLink.value;
          localStorage.setItem(STORAGE, JSON.stringify(state));
          alert('Gespeichert (local)');
          renderMembers();
        }catch(e){ alert('Speicherfehler: ' + e) }
      }

      function applyState(){
        updatesContent.innerHTML = state.updates || 'Keine Updates.';
        teamContent.innerHTML = state.team || 'Kein Team.';
        rulesContent.innerHTML = state.rules || 'Keine Regeln definiert.';
        inviteLink.value = state.invite || 'https://discord.gg/xrUYstHgy2';
        renderMembers();
      }

      function renderMembers(){
        membersBox.innerHTML = '';
        state.members.forEach((m, i)=>{
          const el = document.createElement('div');
          el.className = 'member';
          el.innerHTML = '<div>'+escapeHtml(m)+'</div><div class="meta">'+(i===0? 'Owner' : 'Member')+'</div>';
          membersBox.appendChild(el);
        });
        statMembers.innerText = state.members.length;
        statOnline.innerText = Math.max(1, Math.floor(state.members.length/3));
      }

      function escapeHtml(s){ return String(s).replace(/[&<>\\"]/g, c=>({'&':'&amp;','<':'&lt;','>':'&gt;','"':'&quot;'}[c])); }

      // collapsible behaviour
      document.querySelectorAll('.collapsible .head').forEach(head=>{
        head.addEventListener('click', ()=>{
          const body = head.nextElementSibling;
          const chev = head.querySelector('.chev');
          if(body.classList.contains('open')){ body.classList.remove('open'); chev.style.transform = 'rotate(0)'; }
          else{ body.classList.add('open'); chev.style.transform = 'rotate(90deg)'; }
        });
      });

      // Edit toggle: prompt for password to enable, click again to disable
      editToggle.addEventListener('click', ()=>{
        const unlocked = editToggle.textContent.includes('🔓');
        if(unlocked){
          // lock without pw
          if(confirm('Bearbeitung deaktivieren? Alle ungespeicherten Änderungen gehen verloren.')) {
            enableEditing(false);
            alert('Bearbeitung deaktiviert.');
            // reload to restore from saved state (optional)
            load();
          }
          return;
        }
        const pw = prompt('Passwort eingeben, um Bearbeiten zu aktivieren:');
        if(pw === null) return;
        if(pw === PASSWORD){
          enableEditing(true);
          alert('Bearbeiten aktiviert — sichere dein Backup nach Änderungen.');
        }else{ alert('Falsches Passwort'); }
      });

      function enableEditing(on){
        [updatesContent, teamContent, rulesContent].forEach(el=>el.contentEditable = on ? 'true' : 'false');
        newMemberInput.disabled = !on;
        addMemberBtn.disabled = !on;
        editToggle.textContent = on ? '🔓 Bearbeiten' : '🔒 Bearbeiten';
      }

      // add member
      addMemberBtn.addEventListener('click', ()=>{
        const name = newMemberInput.value.trim();
        if(!name) return alert('Gib einen Namen ein');
        state.members.push(name);
        newMemberInput.value = '';
        renderMembers();
        save();
      });

      // save buttons
      saveUpdatesBtn.addEventListener('click', save);
      saveTeamBtn.addEventListener('click', save);
      saveRulesBtn.addEventListener('click', save);
      resetUpdatesBtn.addEventListener('click', ()=>{ if(confirm('Update-Inhalt zurücksetzen?')){ updatesContent.innerHTML = 'Keine Updates.'; save(); } });

      // export / import
      function exportJson(){
        const blob = new Blob([JSON.stringify(state, null, 2)], {type:'application/json'});
        const url = URL.createObjectURL(blob);
        const a = document.createElement('a'); a.href = url; a.download = 'zentrale_backup.json'; document.body.appendChild(a); a.click(); a.remove(); URL.revokeObjectURL(url);
      }
      exportJsonBtn.addEventListener('click', exportJson);
      exportBtnHero.addEventListener('click', exportJson);

      importJsonBtn.addEventListener('click', ()=>fileInput.click());
      fileInput.addEventListener('change', (e)=>{
        const f = e.target.files[0]; if(!f) return;
        const r = new FileReader(); r.onload = ()=>{
          try{
            const parsed = JSON.parse(r.result);
            // merge but prefer imported full structure
            state = Object.assign({}, state, parsed);
            save();
            applyState();
            alert('Import erfolgreich');
          }catch(err){ alert('Import fehlgeschlagen: ' + err) }
        }; r.readAsText(f);
      });

      // copy invite
      copyInviteBtn.addEventListener('click', ()=>{
        const val = inviteLink.value.trim();
        if(!val) return alert('Kein Link eingetragen');
        navigator.clipboard.writeText(val).then(()=>alert('Link kopiert'), ()=>alert('Kopieren nicht möglich'));
      });

      // hero "Discord beitreten" uses direct invite link (anchor) - nothing to do here

      // initial load
      load();
      enableEditing(false);

      // expose for debugging (optional)
      window.__ZentraleHome = {state, save, load};
    })();
  </script>
</body>
</html>
