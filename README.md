<!doctype html>
<html lang="de">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width,initial-scale=1">
<title>Zentrale — Discord Homepage</title>
<style>
:root{
  --bg:#f5f5f5; --card:#ffffff; --text:#111; --muted:#555; --accent:#5865f2; --shadow:rgba(0,0,0,0.1);
}
*{box-sizing:border-box;margin:0;padding:0;font-family:sans-serif;}
body{background:var(--bg);color:var(--text);}
a{text-decoration:none;color:inherit;}
.container{max-width:1000px;margin:20px auto;padding:10px;}
header{display:flex;justify-content:space-between;align-items:center;padding:10px;}
.logo{font-weight:bold;font-size:24px;color:var(--accent);}
nav a{margin-left:10px;padding:6px 10px;border-radius:6px;background:#e0e0e0;font-size:14px;}
nav button{margin-left:10px;padding:6px 10px;border-radius:6px;background:var(--accent);color:white;border:none;cursor:pointer;}
.hero{background:#eaf1ff;padding:20px;border-radius:12px;margin-top:10px;box-shadow:0 4px 10px var(--shadow);}
.hero h1{font-size:28px;margin-bottom:10px;}
.hero p{margin-bottom:10px;}
.btn{background:var(--accent);color:white;padding:8px 12px;border:none;border-radius:6px;cursor:pointer;}
.card{background:var(--card);padding:15px;border-radius:10px;margin-top:12px;box-shadow:0 2px 6px var(--shadow);}
.editable{border:1px dashed #ccc;padding:6px;border-radius:6px;min-height:24px;}
.team-member{display:flex;justify-content:space-between;align-items:center;padding:6px 0;border-bottom:1px solid #eee;}
select, input[type=text]{padding:4px 6px;border-radius:6px;border:1px solid #ccc;}
section h2{margin-bottom:8px;color:var(--accent);}
footer{margin-top:20px;text-align:center;color:var(--muted);font-size:13px;}
</style>
</head>
<body>
<div class="container">
  <header>
    <div class="logo">Zentrale</div>
    <nav>
      <a href="#about">Über</a>
      <a href="#updates">Updates</a>
      <a href="#team">Team</a>
      <a href="#rules">Regeln</a>
      <button id="loginBtn">Admin Login</button>
    </nav>
  </header>

  <div class="hero">
    <h1>Willkommen bei Zentrale 👋</h1>
    <p>Hey, wir sind Zentrale! Bei uns kannst du Spaß haben, neue Leute kennenlernen und coole Events erleben.</p>
    <ul>
      <li>😄 Spaßiger Ort für jeden</li>
      <li>🌍 24/7 nette Teamler</li>
      <li>🚓 Eigener FiveM Roleplay Server</li>
      <li>🎮 Minigames & Community</li>
    </ul>
    <a class="btn" href="https://discord.gg/xrUYstHgy2" target="_blank">Discord beitreten</a>
  </div>

  <section id="about" class="card">
    <h2>Über uns</h2>
    <div id="aboutText" class="editable" contenteditable="false">
      Wir sind die Zentrale — dein Platz für Spaß, Roleplay und Community. Unser Team ist 24/7 für dich da!
    </div>
  </section>

  <section id="updates" class="card">
    <h2>Updates</h2>
    <div id="updatesText" class="editable" contenteditable="false">Keine Updates verfügbar.</div>
  </section>

  <section id="rules" class="card">
    <h2>Regeln</h2>
    <div id="rulesText" class="editable" contenteditable="false">
      1) Respektiere andere<br>
      2) Keine Werbung ohne Erlaubnis<br>
      3) Folge den Moderatoren
    </div>
  </section>

  <section id="team" class="card">
    <h2>Team</h2>
    <div id="teamList"></div>
    <div style="margin-top:8px;">
      <input type="text" id="newName" placeholder="Name hinzufügen" disabled>
      <select id="newRole" disabled>
        <option>Owner</option>
        <option>Administrator</option>
        <option>Entwickler</option>
        <option>Supporter</option>
        <option>Test Supporter</option>
      </select>
      <button id="addMemberBtn" disabled>Hinzufügen</button>
    </div>
  </section>

  <div style="margin-top:20px;">
    <button id="saveBtn" class="btn" disabled>Änderungen speichern</button>
    <button id="exportBtn" class="btn" disabled>Export JSON</button>
    <input type="file" id="importFile" style="display:none">
    <button id="importBtn" class="btn" disabled>Import JSON</button>
  </div>

  <footer>© 2025 Zentrale Discord Community</footer>
</div>

<script>
const PASSWORD='PashaV';
let admin=false;
let state={
  about: document.getElementById('aboutText').innerHTML,
  updates: document.getElementById('updatesText').innerHTML,
  rules: document.getElementById('rulesText').innerHTML,
  team:[{name:'Admin',role:'Owner'}]
};

function renderTeam(){
  const teamDiv=document.getElementById('teamList');
  teamDiv.innerHTML='';
  state.team.forEach((m,i)=>{
    const div=document.createElement('div');
    div.className='team-member';
    div.innerHTML=\`<span>\${m.name} (\${m.role})</span>
      <span>\${admin? '<button onclick="editRole('+i+')">✏️</button><button onclick="removeMember('+i+')">❌</button>':''}</span>\`;
    teamDiv.appendChild(div);
  });
}

function enableAdmin(on){
  admin=on;
  ['aboutText','updatesText','rulesText'].forEach(id=>{
    document.getElementById(id).contentEditable=on;
  });
  ['newName','newRole','addMemberBtn','saveBtn','exportBtn','importBtn'].forEach(id=>{
    document.getElementById(id).disabled=!on;
  });
  renderTeam();
}

document.getElementById('loginBtn').addEventListener('click',()=>{
  const pw=prompt('Passwort eingeben:');
  if(pw===PASSWORD){
    enableAdmin(true);
    alert('Admin aktiviert!');
  } else alert('Falsches Passwort');
});

document.getElementById('addMemberBtn').addEventListener('click',()=>{
  const name=document.getElementById('newName').value.trim();
  const role=document.getElementById('newRole').value;
  if(name){ state.team.push({name,role}); document.getElementById('newName').value=''; renderTeam(); }
});

function editRole(i){
  const newRole=prompt('Neue Rolle auswählen:\nOwner,Administrator,Entwickler,Supporter,Test Supporter',state.team[i].role);
  if(newRole) state.team[i].role=newRole; renderTeam();
}

function removeMember(i){
  if(confirm('Entfernen?')){ state.team.splice(i,1); renderTeam(); }
}

document.getElementById('saveBtn').addEventListener('click',()=>{
  state.about=document.getElementById('aboutText').innerHTML;
  state.updates=document.getElementById('updatesText').innerHTML;
  state.rules=document.getElementById('rulesText').innerHTML;
  localStorage.setItem('zentrale_state',JSON.stringify(state));
  alert('Gespeichert!');
});

document.getElementById('exportBtn').addEventListener('click',()=>{
  const blob=new Blob([JSON.stringify(state,null,2)],{type:'application/json'});
  const a=document.createElement('a'); a.href=URL.createObjectURL(blob); a.download='zentrale_backup.json'; a.click();
});

document.getElementById('importBtn').addEventListener('click',()=>document.getElementById('importFile').click());
document.getElementById('importFile').addEventListener('change',e=>{
  const file=e.target.files[0]; if(!file) return;
  const reader=new FileReader();
  reader.onload=()=>{ state=JSON.parse(reader.result); document.getElementById('aboutText').innerHTML=state.about; document.getElementById('updatesText').innerHTML=state.updates; document.getElementById('rulesText').innerHTML=state.rules; renderTeam(); }
  reader.readAsText(file);
});

// load saved
const saved=localStorage.getItem('zentrale_state');
if(saved) state=JSON.parse(saved);
document.getElementById('aboutText').innerHTML=state.about;
document.getElementById('updatesText').innerHTML=state.updates;
document.getElementById('rulesText').innerHTML=state.rules;
renderTeam();
</script>
</body>
</html>
