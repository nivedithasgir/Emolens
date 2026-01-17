<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Emo-Lens Team Portal</title>

<link href="https://fonts.googleapis.com/css2?family=DM+Sans:wght@400;500;700&family=Playfair+Display:wght@600;700&display=swap" rel="stylesheet">

  <div class="page">
    <div class="content">
      <!-- your main content -->
    </div>

    <a href="index.html" class="bottom-link">Let's chat</a>
  </div>

<style>
:root{
  --primary:#7c6cff;
  --card-bg:rgba(255,255,255,0.92);
  --peach:#fde2e4;
  --mint:#dcfce7;
  --lavender:#ede9fe;
  --butter:#fef3c7;
  --text:#374151;
}

/* BASE */
html,body{
  margin:0;
  height:100%;
  font-family:"DM Sans",sans-serif;
  overflow:hidden;
}

body{
  background:linear-gradient(135deg,#fff7ed,#fdf2f8,#f0fdf4);
  display:flex;
  justify-content:center;
  align-items:center;
  position:relative;
}

/* FLOATING DECORATIONS */
.decor{
  position:absolute;
  width:80px;
  opacity:0.25;
  animation: floatSlow 12s infinite ease-in-out;
}

.decor.leaf{ filter:hue-rotate(80deg); }
.decor.flower{ filter:hue-rotate(330deg); }

.decor.one{ top:10%; left:5%; animation-duration:14s; }
.decor.two{ bottom:15%; right:6%; animation-duration:16s; }
.decor.three{ top:20%; right:10%; animation-duration:18s; }
.decor.four{ bottom:20%; left:10%; animation-duration:20s; }

@keyframes floatSlow{
  0%,100%{ transform:translateY(0) rotate(0deg); }
  50%{ transform:translateY(-20px) rotate(8deg); }
}

/* SPARKLES */
.sparkle{
  position:absolute;
  width:6px;
  height:6px;
  background:#fff;
  border-radius:50%;
  opacity:0.4;
  animation: twinkle 4s infinite alternate;
}

@keyframes twinkle{
  from{ transform:scale(0.6); opacity:0.3; }
  to{ transform:scale(1.2); opacity:0.8; }
}

/* CARD */
.box{
  width:450px;
  background:var(--card-bg);
  backdrop-filter:blur(16px);
  border-radius:26px;
  padding:36px;
  box-shadow:0 30px 70px rgba(0,0,0,0.12);
  text-align:center;
  z-index:2;
  position:relative;
}

.hidden{display:none}

/* TEXT */
h2,h3,h4{
  font-family:"Playfair Display",serif;
  color:var(--text);
}
h2{font-size:32px}
h3{font-size:24px}
h4{font-size:18px}

p{font-size:15px;color:#4b5563}
small{font-size:12px;color:#6b7280}

/* INPUTS */
input,select{
  width:100%;
  padding:14px;
  margin-top:12px;
  border-radius:16px;
  border:1px solid #e5e7eb;
  background:#fff;
}

/* BUTTON */
button{
  width:100%;
  padding:16px;
  margin-top:20px;
  border:none;
  border-radius:18px;
  background:linear-gradient(135deg,#7c6cff,#a594ff);
  color:white;
  font-weight:700;
  cursor:pointer;
  transition:0.3s;
}

button:hover{
  transform:translateY(-2px);
  box-shadow:0 10px 30px rgba(124,108,255,0.35);
}
.bottom-link {
  position: fixed;
  bottom: 5px;
  left: 50%;
  transform: translateX(-50%);
}

/* TABS */
.tab-btn{
  width:50%;
  display:inline-block;
  padding:12px;
  font-weight:600;
  cursor:pointer;
  border-bottom:2px solid transparent;
}

.tab-btn.active{
  border-bottom:2px solid var(--primary);
}

/* MEMBER CARDS */
.member{
  padding:14px;
  border-radius:18px;
  margin:10px 0;
}

.high{background:var(--peach)}
.medium{background:var(--butter)}
.low{background:var(--mint)}

/* PROGRESS */
.progress{
  height:16px;
  background:#e5e7eb;
  border-radius:999px;
  overflow:hidden;
  margin:14px 0;
}

.bar{
  height:100%;
  width:0%;
  background:linear-gradient(90deg,#7c6cff,#a594ff);
}

/* IMAGES */
.hero-img{
  width:180px;
  margin:10px auto 20px;
  animation: floatHero 6s infinite ease-in-out;
}

.analysis-img{
  width:140px;
  margin:10px auto;
  animation:pulse 3s infinite;
}

@keyframes floatHero{
  50%{transform:translateY(-14px)}
}

@keyframes pulse{
  50%{transform:scale(1.05)}
}
</style>
</head>

<body>

<!-- DECOR ELEMENTS -->
<img class="decor leaf one" src="https://img.icons8.com/ios-filled/100/leaf.png">
<img class="decor flower two" src="https://img.icons8.com/ios-filled/100/flower.png">
<img class="decor leaf three" src="https://img.icons8.com/ios-filled/100/leaf.png">
<img class="decor flower four" src="https://img.icons8.com/ios-filled/100/flower.png">

<div class="sparkle" style="top:20%;left:40%"></div>
<div class="sparkle" style="top:60%;left:20%"></div>
<div class="sparkle" style="top:30%;right:30%"></div>

<!-- WELCOME -->
<div class="box" id="welcomePage">
  <img class="hero-img" src="https://img.freepik.com/free-vector/mental-health-awareness-concept-illustration_114360-6222.jpg">
  <h2>Emo-Lens</h2>
  <p><strong>Perceive emotional load before burnout begins.</strong></p>
  <button onclick="showLoginCreate()">Get Started</button>
</div>

<!-- LOGIN / CREATE -->
<div class="box hidden" id="loginCreateBox">
  <h3>Team Portal</h3>
  <div>
    <span id="loginTab" class="tab-btn active" onclick="switchTab('login')">Login</span>
    <span id="createTab" class="tab-btn" onclick="switchTab('create')">Create Team</span>
  </div>

  <div id="loginForm">
    <select id="memberSelect"><option>Select Member</option></select>
    <button onclick="loginMember()">Login</button>
    <p id="loginMessage"></p>
  </div>

  <div id="createForm" class="hidden">
    <input id="teamName" placeholder="Team Name">
    <input id="domain" placeholder="Work Domain">
    <input id="memberCount" type="number" min="1" placeholder="Number of Members">
    <button onclick="startMemberDetails()">Continue</button>
  </div>
</div>

<!-- MEMBER DETAILS -->
<div class="box hidden" id="membersBox">
  <h3>Enter Member Details</h3>
  <div id="currentMemberSection"></div>
  <button id="nextMemberBtn" onclick="nextMember()">Next</button>
</div>

<!-- SURVEY -->
<div class="box hidden" id="surveyBox">
  <img class="analysis-img" src="https://img.freepik.com/free-vector/analyzing-process-concept-illustration_114360-1487.jpg">
  <h3>Gentle Check-in 🌿</h3>

  <p>How do you feel after work?</p>
  <select id="q1"><option value="10">Recharged</option><option value="20">Neutral</option><option value="30">Drained</option><option value="40">Exhausted</option></select>

  <p>If you had one free hour?</p>
  <select id="q2"><option value="10">Something fun</option><option value="20">Light chores</option><option value="30">Rest</option><option value="40">Sleep</option></select>

  <p>Tired even after sleep?</p>
  <select id="q3"><option value="10">Rarely</option><option value="20">Sometimes</option><option value="30">Often</option></select>

  <p>Starting enjoyable tasks?</p>
  <select id="q4"><option value="10">Excited</option><option value="20">Reluctant</option><option value="30">Avoid</option></select>

  <p>Postponing tasks?</p>
  <select id="q5"><option value="10">Rarely</option><option value="20">Sometimes</option><option value="30">Frequently</option></select>

  <button onclick="submitSurvey()">Submit</button>
</div>

<!-- DASHBOARD -->
<div class="box hidden" id="dashboardBox">
  <h3 id="teamTitle"></h3>
  <small id="teamMeta"></small>
  <p id="eliStatus">Analyzing emotional balance…</p>
  <div class="progress"><div class="bar" id="progressBar"></div></div>
  <h4 id="eliScore">Your ELI: 0</h4>
  <hr>
  <h4>Team Members</h4>
  <div id="teamList"></div>
</div>

<script>
    
let team = { members: [] }, currentMemberIndex = 0, loggedMember = null, completedCount = 0;

// Show Login/Create page
function showLoginCreate() {
  welcomePage.classList.add('hidden');
  loginCreateBox.classList.remove('hidden');
  switchTab('login');
}

// Switch tabs
function switchTab(t) {
  loginForm.classList.toggle('hidden', t !== 'login');
  createForm.classList.toggle('hidden', t !== 'create');
  loginTab.classList.toggle('active', t === 'login');
  createTab.classList.toggle('active', t === 'create');
  if (t === 'login') populateLogin();
}

// Start entering member details
function startMemberDetails() {
  if (!teamName.value || !domain.value || memberCount.value < 1) {
    alert("Please enter valid team details");
    return;
  }

  team = {
    name: teamName.value,
    domain: domain.value,
    memberCount: +memberCount.value,
    members: []
  };
  currentMemberIndex = 0;
  completedCount = 0;
  loginCreateBox.classList.add('hidden');
  membersBox.classList.remove('hidden');
  showMemberForm();
}

// Show member form
function showMemberForm() {
  let i = currentMemberIndex + 1;
  currentMemberSection.innerHTML = `
    <p><b>Member ${i} of ${team.memberCount}</b></p>
    <input id="mName" placeholder="Name">
    <input id="mAge" type="number" placeholder="Age">
    <input id="mRole" placeholder="Role">
  `;
  nextMemberBtn.innerText = i === team.memberCount ? 'Finish' : 'Next';
}

// Save member and move to next
function nextMember() {
  let n = mName.value, a = mAge.value, r = mRole.value;
  if (!n || !a || !r) return alert("Fill all fields");

  team.members.push({
    name: n,
    age: a,
    role: r,
    eli: 0,
    surveyed: false
  });

  currentMemberIndex++;
  if (currentMemberIndex < team.memberCount) {
    showMemberForm();
  } else {
    membersBox.classList.add('hidden');
    loginCreateBox.classList.remove('hidden');
    switchTab('login');
  }
}

// Populate login select
function populateLogin() {
  memberSelect.innerHTML = '<option>Select Member</option>';
  team.members.forEach(m => {
    if (!m.surveyed) memberSelect.innerHTML += `<option>${m.name}</option>`;
  });
}

// Login member to take survey
function loginMember() {
  loggedMember = team.members.find(m => m.name === memberSelect.value);
  if (!loggedMember) return;

  surveyBox.classList.remove('hidden');
  loginCreateBox.classList.add('hidden');
}

// Submit survey
function submitSurvey() {
  loggedMember.eli =
    +q1.value + +q2.value + +q3.value + +q4.value + +q5.value;
  loggedMember.surveyed = true;
  completedCount++;

  surveyBox.classList.add('hidden');
  showDashboard();
}

// Show dashboard
function showDashboard() {
  dashboardBox.classList.remove('hidden');
  teamTitle.innerText = team.name;

  // Determine if it's the last member
  const isLastMember = completedCount === team.memberCount;

  teamList.innerHTML = '';

  if (!isLastMember) {
    // Show only current member
    teamMeta.innerText = `${team.domain} · Individual Check-in`;
    teamList.innerHTML = `
      <div class="member ${loggedMember.eli >= 70 ? 'high' : loggedMember.eli >= 40 ? 'medium' : 'low'}">
        <b>${loggedMember.name}</b><br>${loggedMember.role} · ELI: ${loggedMember.eli}
      </div>
    `;
  } else {
    // Show overall team summary
    const avgELI = Math.round(team.members.reduce((sum, m) => sum + m.eli, 0) / team.members.length);
    teamMeta.innerText = `${team.domain} · Team Summary · Avg ELI: ${avgELI}`;

    team.members.forEach(m => {
      teamList.innerHTML += `
        <div class="member ${m.eli >= 70 ? 'high' : m.eli >= 40 ? 'medium' : 'low'}">
          <b>${m.name}</b><br>${m.role} · ELI: ${m.eli}
        </div>
      `;
    });

    // Show highest ELI
    const top = team.members.reduce((max, m) => m.eli > max.eli ? m : max);
    teamList.innerHTML += `
      <div class="member high">
        🌟 <b>Highest ELI</b><br>
        ${top.name} (${top.role})<br>
        ELI: ${top.eli}
      </div>
    `;
  }

  // Animate progress bar for logged-in member
  let target = Math.min(loggedMember.eli, 100);
  let p = 0;
  let i = setInterval(() => {
    p++;
    progressBar.style.width = p + '%';
    if (p >= target) {
      clearInterval(i);
      eliStatus.innerText = eliLabel(loggedMember.eli);
      eliScore.innerText = `Your ELI: ${loggedMember.eli}`;

      // After 3s, go to next member or sign-out message
      setTimeout(() => {
        dashboardBox.classList.add('hidden');
        if (!isLastMember) {
          loginCreateBox.classList.remove('hidden');
          switchTab('login');
        } else {
          // All done: show sign-out message
          welcomePage.classList.remove('hidden');
          welcomePage.innerHTML = `
            <h2>Thank you for completing the check-in! 🌿</h2>
            <p>All members have submitted their surveys.</p>
            <button onclick="location.reload()">Sign Out</button>
          `;
        }
      }, 3000);
    }
  }, 15);
}

// Convert ELI score to meaningful text
function eliLabel(score) {
  if (score >= 70) return "High emotional load ⚠️";
  if (score >= 40) return "Moderate emotional strain 🌤️";
  return "Healthy emotional balance 🌱";
}
</script>


<body>


<head>
<meta charset="UTF-8">
<title>EmoLens Chatbot</title>
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<link href="https://fonts.googleapis.com/css2?family=DM+Sans:wght@400;500;700&display=swap" rel="stylesheet">

<style>
  body {
    margin: 0;
    height: 100vh;
    background: linear-gradient(135deg, #a18cd1, #fbc2eb);
    font-family: 'DM Sans', sans-serif;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .chat-card {
    width: 380px;
    height: 100%;
    background: rgba(255,255,255,0.25);
    backdrop-filter: blur(16px);
    border-radius: 22px;
    box-shadow: 0 30px 60px rgba(0,0,0,0.15);
    display: flex;
    flex-direction: column;
    overflow: hidden;
  }

  .chat-header {
    padding: 18px;
    font-weight: 700;
    font-size: 18px;
    text-align: center;
    color: #fff;
  }

  .chat-body {
    flex: 1;
    padding: 14px;
    overflow-y: auto;
  }

  .msg {
    max-width: 75%;
    margin-bottom: 10px;
    padding: 10px 14px;
    border-radius: 14px;
    font-size: 14px;
    line-height: 1.4;
  }

  .user {
    background: #7c6cff;
    color: #fff;
    align-self: flex-end;
    border-bottom-right-radius: 4px;
  }

  .bot {
    background: #ffffff;
    color: #333;
    align-self: flex-start;
    border-bottom-left-radius: 4px;
  }

  .chat-input {
    display: flex;
    gap: 10px;
    padding: 12px;
    background: rgba(255,255,255,0.35);
  }

  .chat-input textarea {
    display: block;
   flex: 1;
   width:100%;
  min-height: 42px;
  max-height: 90px;
  resize: none;
  border: none;
  border-radius: 14px;
  padding: 10px 12px;
  outline: none;
  font-size: 14px;
  font-family: inherit;
  background: #ffffff;
  color: #333;
}

.chat-input textarea::placeholder {
  color: #888;
}

.chat-input textarea:focus {
  box-shadow: 0 0 0 2px rgba(124,108,255,0.4);
}
  .chat-input button {
    margin-left: 8px;
    border: none;
    border-radius: 12px;
    background: #7c6cff;
    color: #fff;
    padding: 0 16px;
    font-weight: 600;
    cursor: pointer;
  }
</style>
</head>

<body>

<a href="index.html"></a>

<script>
async function send() {
  const input = document.getElementById("input");
  const chat = document.getElementById("chat");
  const text = input.value.trim();
  if (!text) return;

  chat.innerHTML += `<div class="msg user">${text}</div>`;
  input.value = "";
  chat.scrollTop = chat.scrollHeight;

  const typing = document.createElement("div");
  typing.className = "msg bot";
  typing.innerText = "Typing...";
  chat.appendChild(typing);

  try {
    const res = await fetch("http://localhost:3000/chat", {
      method: "POST",
      headers: { "Content-Type": "application/json" },
      body: JSON.stringify({ message: text })
    });

    const data = await res.json();
    typing.innerText = data.reply;

  } catch {
    typing.innerText = "⚠️ Unable to connect to EmoLens";
  }

  chat.scrollTop = chat.scrollHeight;
}
</script>


</body>

</html>
