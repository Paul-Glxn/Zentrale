<!doctype html>
<html lang="de">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Zentrale — Dashboard</title>
  <style>
    :root{--bg:#0f1720;--panel:#0b1220;--accent:#5865f2;--muted:#9aa4b2;--card:#111827}
    *{box-sizing:border-box}
    html,body{height:100%;margin:0;font-family:Inter,system-ui,Segoe UI,Roboto,"Helvetica Neue",Arial;color:#e6eef6;background:linear-gradient(180deg,#071023 0%, #081324 100%)}
    .app{display:grid;grid-template-columns:260px 1fr;gap:18px;padding:20px;height:100vh}
    /* SIDEBAR */
    .sidebar{background:rgba(255,255,255,0.03);border-radius:12px;padding:16px;display:flex;flex-direction:column;gap:12px}
    .logo{font-weight:700;color:var(--accent);font-size:18px}
    .search{display:flex;gap:8px}
    .search input{flex:1;background:transparent;border:1px solid rgba(255,255,255,0.04);padding:8px;border-radius:8px;color:inherit}
    .channels{overflow:auto;padding-right:6px}
    .channel{padding:8px;border-radius:8px;cursor:pointer;display:flex;justify-content:space-between;align-items:center}
    .channel:hover{background:rgba(255,255,255,0.02)}
    .channel.active{background:rgba(88,101,242,0.12)}
    .members{margin-top:auto;font-size:13px;color:var(--muted)}
    /* MAIN */
    .main{display:flex;flex-direction:column;gap:12px}
    .topbar{display:flex;justify-content:space-between;align-items:center}
    .title{font-size:20px;font-weight:700}
    .controls{display:flex;gap:8px;align-items:center}
    .btn{background:var(--panel);padding:8px 12px;border-radius:8px;border:1px solid rgba(255,255,255,0.03);cursor:pointer}
    .card{background:rgba(255,255,255,0.03);padding:12px;border-radius:10px}
    /* collapsible */
    .item{border-radius:8px;overflow:hidden;border:1px solid rgba(255,255,255,0.02)}
    .item-head{display:flex;justify-content:space-between;align-items:center;padding:10px 12px;cursor:pointer}
    .chev{transition:transform .25s}
    .chev.open{transform:rotate(90deg)}
    .item-body{max-height:0;overflow:hidden;transition:max-height .28s ease;padding:0 12px}
    .item-body.open{padding:10px 12px;}
    .editable{min-height:60px;border-radius:6px;padding:8px;border:1px dashed rgba(255,255,255,0.04);outline:none}
    .meta{font-size:12px;color:var(--muted);display:flex;gap:10px;align-items:center}
    .inline{display:flex;gap:8px;align-items:center}
    /* small forms */
    .small-input{padding:6px;border-radius:6px;border:1px solid rgba(255,255,255,0.04);background:transparent;color:inherit}
    .hidden{display:none}
    .notice{font-size:13px;color:var(--muted)}
    footer{font-size:12px;color:var(--muted);text-align:right}
    /* responsive */
    @media(max-width:800px){.app{grid-template-columns:1fr;grid-auto-rows:auto;padding:12px}}
  </style>
</head>
<body>
<div class="app">
  <aside class="sidebar">
    <div class="logo">Zentrale</div>
    <div class="search"><input id="quickSearch" placeholder="Suche..." /></div>
    <div class="channels" id="channelsList">
      <div class="channel active" data-channel="all"># Übersicht</div>
      <div class="channel" data-channel="updates"># Updates</div>
      <div class="channel" data-channel="team"># Team</div>
      <div class="channel" data-channel="announcements"># Ankündigungen</div>
    </div>
    <div class="members">
      <div><strong>Mitglieder</strong></div>
      <div id="memberList">Lädt…</div>
    </div>
  </aside>

  <main class="main">
    <div class="topbar">
      <div class="title">Zentrale Dashboard</div>
      <div class="controls">
        <div class="notice">Local Save</div>
        <button class="btn" id="exportBtn">Export JSON</button>
        <button class="btn" id="importBtn">Import JSON</button>
        <input id="fileInput" type="file" class="hidden" accept="application/json" />
      </div>
    </div>

    <section class="card item" id="updatesItem">
      <div class="item-head" data-target="updatesBody">
        <div><strong>Updates</strong><div class="meta">Wichtige Änderungen & Versionshinweise</div></div>
        <div class="inline">
          <button class="btn" data-action="toggle">Anzeigen</button>
          <div class="chev">▶</div>
        </div>
      </div>
      <div class="item-body" id="updatesBody">
        <div class="meta">Dieser Bereich ist geschützt — nur mit Passwort editierbar.</div>
        <div style="height:8px"></div>
        <div id="updatesContent" class="editable" contenteditable="false">Keine Updates vorhanden. Klicke das Schloss, um Änderungen zu entsperren (PashaV).</div>
        <div style="height:8px"></div>
        <div style="display:flex;gap:8px;align-items:center">
          <input id="updatesPass" class="small-input" placeholder="Passwort eingeben" />
          <button class="btn" data-action="unlock" data-section="updates">Schloss öffnen</button>
          <button class="btn" data-action="save" data-section="updates">Speichern</button>
        </div>
      </div>
    </section>

    <section class="card item" id="teamItem">
      <div class="item-head" data-target="teamBody">
        <div><strong>Neues Team</strong><div class="meta">Hier neue Teammitglieder hinzufügen oder vorstellen</div></div>
        <div class="inline">
          <button class="btn" data-action="toggle">Anzeigen</button>
          <div class="chev">▶</div>
        </div>
      </div>
      <div class="item-body" id="teamBody">
        <div class="meta">Passwort-geschützt für Änderungen (nur wichtige Bereiche).</div>
        <div style="height:8px"></div>
        <div id="teamContent" class="editable" contenteditable="false">Keine neuen Team-Mitglieder.</div>
        <div style="height:8px"></div>
        <div style="display:flex;gap:8px;align-items:center">
          <input id="teamPass" class="small-input" placeholder="Passwort eingeben" />
          <button class="btn" data-action="unlock" data-section="team">Schloss öffnen</button>
          <button class="btn" data-action="save" data-section="team">Speichern</button>
        </div>
        <div style="height:6px"></div>
        <div style="display:flex;gap:8px">
          <input id="newMemberName" class="small-input" placeholder="Name hinzufügen" />
          <button class="btn" id="addMemberBtn">Hinzufügen</button>
        </div>
      </div>
    </section>

    <section class="card">
      <h3>Allgemeine Informationen</h3>
      <p class="notice">Diese Seite speichert alles lokal in deinem Browser (localStorage). Du kannst exportieren/importieren, oder die Datei auf GitHub Pages / Netlify hosten (kostenlos).</p>
    </section>

    <footer>Speichern: Automatisch beim Klick auf "Speichern". Passwort-Phrase: <strong>PashaV</strong></footer>
  </main>
</div>

<script>
(function(){
  // Constants
  const PASSWORD = 'PashaV'; // client-side check — nur lokal, nicht sicher
  const STORAGE_KEY = 'zentrale_data_v1';

  // Elements
  const channels = document.getElementById('channelsList');
  const memberList = document.getElementById('memberList');
  const updatesBody = document.getElementById('updatesBody');
  const teamBody = document.getElementById('teamBody');
  const updatesContent = document.getElementById('updatesContent');
  const teamContent = document.getElementById('teamContent');
  const exportBtn = document.getElementById('exportBtn');
  const importBtn = document.getElementById('importBtn');
  const fileInput = document.getElementById('fileInput');
  const addMemberBtn = document.getElementById('addMemberBtn');
  const newMemberName = document.getElementById('newMemberName');

  // initial data
  let state = {
    members: ['Admin'],
    updates: updatesContent.innerHTML,
    team: teamContent.innerHTML
  };

  // Load from localStorage if present
  function loadState(){
    try{
      const raw = localStorage.getItem(STORAGE_KEY);
      if(raw){
        const parsed = JSON.parse(raw);
        state = Object.assign(state, parsed);
      }
    }catch(e){console.warn('load error',e)}
    renderFromState();
  }

  function saveState(){
    try{
      state.updates = updatesContent.innerHTML;
      state.team = teamContent.innerHTML;
      localStorage.setItem(STORAGE_KEY, JSON.stringify(state));
      alert('Gespeichert (localStorage)');
    }catch(e){alert('Speicherfehler: '+e)}
  }

  function renderFromState(){
    memberList.innerText = state.members.join(', ');
    updatesContent.innerHTML = state.updates || 'Keine Updates vorhanden.';
    teamContent.innerHTML = state.team || 'Keine neuen Team-Mitglieder.';
  }

  // Collapse toggles
  document.querySelectorAll('.item-head').forEach(head=>{
    head.addEventListener('click', (e)=>{
      // if clicked on inputs/buttons inside head ignore
      if(e.target.tagName === 'BUTTON') return;
      const target = head.dataset.target;
      const body = document.getElementById(target);
      const chev = head.querySelector('.chev');
      if(body.classList.contains('open')){
        body.style.maxHeight = '0px';
        body.classList.remove('open');
        chev.classList.remove('open');
      }else{
        body.classList.add('open');
        body.style.maxHeight = body.scrollHeight + 40 + 'px';
        chev.classList.add('open');
      }
    });
  });

  // Buttons inside heads (toggle text)
  document.querySelectorAll('[data-action="toggle"]').forEach(btn=>{
    btn.addEventListener('click', (e)=>{
      e.stopPropagation();
      const head = btn.closest('.item-head');
      head.click();
    });
  });

  // Unlock and Save actions
  document.querySelectorAll('[data-action="unlock"]').forEach(btn=>{
    btn.addEventListener('click', ()=>{
      const section = btn.dataset.section;
      const passInput = document.getElementById(section + 'Pass');
      if(passInput.value === PASSWORD){
        if(section === 'updates') updatesContent.contentEditable = 'true';
        if(section === 'team') teamContent.contentEditable = 'true';
        alert('Bearbeiten freigeschaltet für: ' + section);
      }else{
        alert('Falsches Passwort');
      }
      passInput.value = '';
    });
  });

  document.querySelectorAll('[data-action="save"]').forEach(btn=>{
    btn.addEventListener('click', ()=>{
      saveState();
    });
  });

  // Add member (only works if teamContent is editable)
  addMemberBtn.addEventListener('click', ()=>{
    const name = newMemberName.value.trim();
    if(!name) return alert('Name eingeben');
    state.members.push(name);
    // update team content visually too
    const extra = '<div>• ' + escapeHtml(name) + '</div>';
    teamContent.innerHTML = teamContent.innerHTML + extra;
    newMemberName.value = '';
    renderFromState();
    saveState();
  });

  // Export/Import
  exportBtn.addEventListener('click', ()=>{
    const dataStr = JSON.stringify(state, null, 2);
    const blob = new Blob([dataStr], {type:'application/json'});
    const url = URL.createObjectURL(blob);
    const a = document.createElement('a');
    a.href = url; a.download = 'zentrale_export.json';
    document.body.appendChild(a); a.click(); a.remove();
    URL.revokeObjectURL(url);
  });

  importBtn.addEventListener('click', ()=>fileInput.click());
  fileInput.addEventListener('change', (e)=>{
    const f = e.target.files[0];
    if(!f) return;
    const reader = new FileReader();
    reader.onload = ()=>{
      try{
        const parsed = JSON.parse(reader.result);
        state = Object.assign(state, parsed);
        saveState();
        renderFromState();
        alert('Import erfolgreich');
      }catch(err){alert('Import fehlgeschlagen: ' + err)}
    };
    reader.readAsText(f);
  });

  // Simple search (filters channels list)
  document.getElementById('quickSearch').addEventListener('input', (e)=>{
    const q = e.target.value.toLowerCase();
    document.querySelectorAll('.channel').forEach(ch=>{
      ch.style.display = ch.innerText.toLowerCase().includes(q) ? 'flex' : 'none';
    });
  });

  // Channel click
  document.querySelectorAll('.channel').forEach(ch=>{
    ch.addEventListener('click', ()=>{
      document.querySelectorAll('.channel').forEach(c=>c.classList.remove('active'));
      ch.classList.add('active');
      const name = ch.dataset.channel;
      // basic behavior: focus certain section
      if(name === 'updates'){
        document.getElementById('updatesItem').scrollIntoView({behavior:'smooth'});
      }else if(name === 'team'){
        document.getElementById('teamItem').scrollIntoView({behavior:'smooth'});
      }
    });
  });

  // helpers
  function escapeHtml(s){return s.replace(/[&<>\"]/g,function(c){return {'&':'&amp;','<':'&lt;','>':'&gt;','"':'&quot;'}[c]})}

  // initial load
  loadState();

  // Expose for console (optional)
  window.__Zentrale = {state, saveState, loadState};
})();
</script>
</body>
</html>

