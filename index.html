<!DOCTYPE html>
<html lang="en">
	<head>
		<meta charset="UTF-8">
			<title>S-Tier Live</title>
			<style>
:root{--g:#10b981;--r:#ef4444}
*{box-sizing:border-box}
body{margin:0;background:black;font-family:Inter,system-ui,sans-serif;overflow:hidden}
#o{position:fixed;top:20px;left:20px;width:300px;height:200px;background:rgba(15,23,42,.92);border-radius:16px;padding:14px;box-shadow:0 8px 32px -12px rgb(0 0 0 / .6),inset 0 1px 0 rgba(255,255,255,.1);backdrop-filter:blur(12px);display:flex;flex-direction:column}
.header{font-size:11px;font-weight:600;letter-spacing:.5px;color:#e2e8f0;opacity:.75;margin-bottom:8px;text-transform:uppercase;display:flex;align-items:center;gap:6px}
.header::before{content:'';width:6px;height:6px;background:var(--g);border-radius:50%;animation:ping 2s infinite}
.grid{display:grid;grid-template-columns:repeat(4,1fr);gap:10px;flex:1}
.s{display:flex;flex-direction:column;align-items:center;gap:4px}
.iw{width:56px;height:56px;border-radius:50%;border:5px solid var(--r);display:flex;align-items:center;justify-content:center;background:#0f172a;transition:all .3s cubic-bezier(.4,0,.2,1);position:relative}
.iw.on{border-color:var(--g);animation:livePulse 2s infinite}
.iw.checking{border-color:#64748b;animation:checkingSpin 1.2s linear infinite}
.iw img{width:46px;height:46px;border-radius:50%;object-fit:cover}
.iw:not(.on):not(.checking) img{filter:grayscale(60%) brightness(.85)}
.name{font-size:9.5px;font-weight:500;color:#e2e8f0;letter-spacing:.3px;max-width:55px;white-space:nowrap;overflow:hidden;text-overflow:ellipsis}
.last{font-size:9px;color:#64748b;margin-top:2px}
.iw.on::after{content:'';position:absolute;top:4px;right:4px;width:10px;height:10px;background:var(--g);border-radius:50%;border:2px solid #0f172a;animation:liveDot 1.5s infinite}
@keyframes livePulse{0%{box-shadow:0 0 0 0 rgba(16,185,129,.5)}70%{box-shadow:0 0 0 10px rgba(16,185,129,0)}100%{box-shadow:0 0 0 0 rgba(16,185,129,0)}}
@keyframes liveDot{0%,100%{opacity:1}50%{opacity:.3}}
@keyframes checkingSpin{to{transform:rotate(360deg)}}
</style>
		</head>
		<body>
			<div id="o">
				<div class="header">LIVE STATUS <span id="last" class="last"/>
				</div>
				<div id="g" class="grid"/>
			</div>
			<script>
// grug mode: real checks + last updated time
let streamers = [];
let twitchToken = null;
const TWITCH_CLIENT_ID = '3l5p1q1v5av0qkunjqsr18we0df3z3';     // ← YOUR CLIENT ID
const TWITCH_CLIENT_SECRET = 'jwb7pmf4hbs8tds6wqdz6tbmfl6jbo'; // ← YOUR CLIENT SECRET

async function getTwitchToken() {
    if (twitchToken) return twitchToken;
    if (!TWITCH_CLIENT_ID || !TWITCH_CLIENT_SECRET) return null;
    try {
        const res = await fetch('https://id.twitch.tv/oauth2/token', {
            method: 'POST',
            headers: {'Content-Type': 'application/x-www-form-urlencoded'},
            body: new URLSearchParams({client_id: TWITCH_CLIENT_ID, client_secret: TWITCH_CLIENT_SECRET, grant_type: 'client_credentials'})
        });
        const data = await res.json();
        if (data.access_token) twitchToken = data.access_token;
        return twitchToken;
    } catch(e) { return null; }
}

async function fetchKick(username) {
    try {
        const res = await fetch(`https://kick.com/api/v1/channels/${username}`);
        const data = await res.json();
        return {is_live: !!(data.livestream && data.livestream.is_live)};
    } catch(e) { return {is_live: false}; }
}

async function fetchTwitch(username) {
    const token = await getTwitchToken();
    if (!token) return {is_live: false};
    try {
        const res = await fetch(`https://api.twitch.tv/helix/streams?user_login=${username}`, {
            headers: {'Client-ID': TWITCH_CLIENT_ID, 'Authorization': `Bearer ${token}`}
        });
        const data = await res.json();
        return {is_live: !!(data.data && data.data.length > 0)};
    } catch(e) { return {is_live: false}; }
}

function updateLastTime() {
    const now = new Date();
    const time = now.getHours().toString().padStart(2,'0') + ':' + 
                 now.getMinutes().toString().padStart(2,'0');
    document.getElementById('last').textContent = `• checked ${time}`;
}

async function updateLiveStatuses() {
    updateLastTime();

    // show checking animation on all at once (simple & clean)
    document.querySelectorAll('.iw').forEach(iw => {
        iw.classList.add('checking');
        iw.classList.remove('on');
    });

    // check all at once (parallel)
    const promises = streamers.map(async s => {
        let status = s.platform === 'kick' ? 
            await fetchKick(s.username) : 
            await fetchTwitch(s.username);

        const el = document.getElementById(s.id);
        if (el) {
            const iw = el.querySelector('.iw');
            iw.classList.remove('checking');
            if (status.is_live) iw.classList.add('on');
        }
        return status;
    });

    await Promise.all(promises);
}

async function loadAndRender() {
    streamers = [
        {id:"kick-xqc", name:"xqc", platform:"kick", username:"xqc"},
        {id:"twitch-loltyler1", name:"loltyler1", platform:"twitch", username:"loltyler1"},
        {id:"twitch-ohnePixel", name:"ohnePixel", platform:"twitch", username:"ohnePixel"},
        {id:"twitch-Jerma985", name:"Jerma985", platform:"twitch", username:"Jerma985"},
        {id:"twitch-WowHobbs", name:"WowHobbs", platform:"twitch", username:"WowHobbs"},
        {id:"twitch-Thijs", name:"Thijs", platform:"twitch", username:"Thijs"},
        {id:"twitch-Trick2g", name:"Trick2g", platform:"twitch", username:"Trick2g"},
        {id:"twitch-Flight23white", name:"Flight23white", platform:"twitch", username:"Flight23white"}
    ];

    const g = document.getElementById('g');
    g.innerHTML = streamers.map(s => `
        <div class="s" id="${s.id}">
					<div class="iw">
						<img src="https://picsum.photos/id/${100 + streamers.indexOf(s)}/300/300" alt="${s.name}">
            </div>
						<div class="name">${s.name}</div>
					</div>
    `).join('');

    await updateLiveStatuses();   // first real check
}

window.onload = () => {
    loadAndRender();
    setInterval(updateLiveStatuses, 180000);  // every 3 minutes
};
</script>
			</body>
		</html>
