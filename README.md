# my-Ai-forex-and-BTCUSD-
Ai forex 
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>ChartAI - AI Chart Scanner</title>
<script src="https://cdn.tailwindcss.com"></script>
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700;800&display=swap" rel="stylesheet">
<style>
body{font-family:'Inter',sans-serif;background:#0a0e13;color:white}
.card{background:#131a22;border:1px solid #1e2a36;border-radius:18px}
.neon-text{color:#3dd5d0}
.gauge{stroke-dasharray: 219;stroke-dashoffset: 54;transform:rotate(-90deg);transform-origin:50% 50%}
.sell-glow{box-shadow:0 0 30px rgba(255,77,109,0.15);border:1px solid #ff4d6d}
</style>
</head>
<body class="max-w-[420px] mx-auto min-h-screen pb-10">

<!-- SCREEN 2 : SCANNER -->
<div id="screen-scanner">
  <div class="p-5">
    <p class="text-[11px] tracking-[0.2em] neon-text font-bold">AI CHART SCANNER</p>
    <h1 class="text-[26px] font-bold leading-tight mt-1">Read any chart in seconds</h1>
    <p class="text-[13px] text-gray-400 mt-2">Screenshot a chart, pick your strategy, and get an entry, stop and target.</p>
    
    <div class="card mt-4 p-3 flex items-center gap-3 w-fit">
      <div class="w-6 h-6 rounded-full bg-[#1a2a2e] flex items-center justify-center">✦</div>
      <div><p class="text-[10px] text-gray-400">FREE SCANS</p><p class="text-[13px] font-bold neon-text">9 of 10 left</p></div>
    </div>

    <div class="mt-7 flex items-center gap-2"><div class="w-7 h-7 rounded-full bg-[#1a2f35] flex items-center justify-center text-xs">1</div><p class="text-sm text-gray-300">Pair and strategy</p></div>
    <div class="grid grid-cols-2 gap-3 mt-3">
      <div class="card p-3"><p class="text-[10px] tracking-widest text-gray-400">SYMBOL</p><p class="neon-text font-bold mt-1">BTCUSD</p><p class="text-[11px] text-gray-500">Tap to type</p></div>
      <div class="card p-3"><p class="text-[10px] tracking-widest text-gray-400">STRATEGY</p><p class="neon-text font-bold mt-1">⚡ Scalping</p><p class="text-[11px] text-gray-500">Tap to change</p></div>
    </div>

    <div class="mt-6 flex items-center gap-2"><div class="w-7 h-7 rounded-full bg-[#1a2f35] flex items-center justify-center text-xs">2</div><p class="text-sm text-gray-300">Your chart</p></div>
    <div class="card mt-3 p-2 overflow-hidden">
      <img id="preview" class="w-full h-[210px] object-cover rounded-xl hidden">
      <div id="placeholder" class="w-full h-[210px] bg-[#0a0e13] rounded-xl grid place-items-center text-gray-500 text-sm">No chart selected</div>
    </div>
    <div class="grid grid-cols-2 gap-3 mt-3">
      <button onclick="document.getElementById('file').click()" class="card py-4 text-center"><p>📷</p><p class="neon-text text-xs font-bold tracking-widest mt-1">CAMERA</p></button>
      <button onclick="document.getElementById('file').click()" class="card py-4 text-center"><p>🖼️</p><p class="neon-text text-xs font-bold tracking-widest mt-1">GALLERY</p></button>
      <input type="file" id="file" accept="image/*" class="hidden">
    </div>

    <div class="mt-6 flex items-center gap-2"><div class="w-7 h-7 rounded-full bg-[#1a2f35] flex items-center justify-center text-xs">3</div><p class="text-sm text-gray-300">Run the scan</p></div>
    <button id="scanBtn" class="w-full mt-3 py-4 rounded-full bg-gradient-to-b from-[#3dd5d0] to-[#00a8b5] text-black font-bold tracking-widest text-sm">○ SCAN CHART</button>
    <p class="text-[10px] text-center text-gray-500 mt-3">AI signals are educational. Always verify before trading.</p>
  </div>
</div>

<!-- SCREEN 1 : RESULT -->
<div id="screen-result" class="hidden">
  <div class="p-4">
    <div class="flex items-center gap-3"><button onclick="show('scanner')">←</button><p class="neon-text font-bold tracking-widest text-sm">SCAN RESULT</p></div>
    
    <div class="card sell-glow mt-5 p-6 text-center bg-[#1a1216]">
      <div class="w-12 h-12 mx-auto rounded-full bg-[#ff3b5c] shadow-[0_0_20px_#ff3b5c]"></div>
      <h1 id="res-direction" class="text-[32px] font-extrabold tracking-[0.2em] text-[#ff4d6d] mt-3">SELL</h1>
      <div class="flex justify-center gap-2 mt-3"><span class="bg-[#1e1e1e] px-3 py-1 rounded text-[11px]">BTCUSD</span><span class="bg-[#1e1e1e] px-3 py-1 rounded text-[11px]">Scalping</span></div>
      <p class="text-[11px] text-gray-400 mt-2">M15</p>
    </div>

    <div class="card mt-4 p-4">
      <div class="flex justify-between text-xs"><span class="text-green-400">25%</span><span class="text-[#ff4d6d]">75%</span></div>
      <div class="w-full h-2 bg-[#1e1e1e] rounded mt-1 flex overflow-hidden"><div id="bar-buy" class="h-full bg-[#00ff88]" style="width:25%"></div><div id="bar-sell" class="h-full bg-[#ff4d6d]" style="width:75%"></div></div>
      <div class="flex justify-center mt-5">
        <div class="relative w-36 h-36"><svg class="w-full h-full"><circle cx="72" cy="72" r="58" stroke="#1e2a36" stroke-width="10" fill="none"/><circle id="conf-circle" cx="72" cy="72" r="58" stroke="#00ff88" stroke-width="10" fill="none" stroke-linecap="round" class="gauge"/></svg><div class="absolute inset-0 grid place-items-center"><div><p id="conf-text" class="text-4xl font-bold">75%</p><p class="text-[10px] text-gray-400 text-center">CONFIDENCE</p></div></div></div>
      </div>
    </div>

    <div class="card mt-4 p-3"><p id="res-desc" class="text-[12px] italic text-gray-300">"Strong bearish momentum after breaking key support, looking for a quick bounce then continuation down."</p></div>

    <p class="neon-text text-[11px] tracking-widest font-bold mt-5">DETECTED PATTERNS</p>
    <div class="flex gap-2 mt-2 flex-wrap"><span class="card px-3 py-1.5 text-[11px] text-[#6ebfff]">bearish momentum burst</span><span class="card px-3 py-1.5 text-[11px] text-[#6ebfff]">rejection of previous support</span></div>

    <p class="neon-text text-[11px] tracking-widest font-bold mt-5">KEY LEVELS</p>
    <div class="grid grid-cols-2 gap-3 mt-2">
      <div class="card p-3"><p class="text-[10px] tracking-widest text-green-400">SUPPORT</p><p id="res-support" class="font-bold mt-1">82881.967</p></div>
      <div class="card p-3"><p class="text-[10px] tracking-widest text-[#ff4d6d]">RESISTANCE</p><p id="res-resist" class="font-bold mt-1">83621.420</p></div>
    </div>

    <div class="grid grid-cols-2 gap-3 mt-6"><button class="card py-3 text-xs neon-text">↗ SHARE</button><button onclick="goDetail()" class="card py-3 text-xs neon-text">VIEW DETAILS →</button></div>
    <button onclick="show('scanner')" class="w-full mt-3 card py-3 text-xs neon-text">↻ SCAN AGAIN</button>
  </div>
</div>

<!-- SCREEN 3 : CHARTAI DETAIL -->
<div id="screen-detail" class="hidden">
  <div class="p-4 bg-black min-h-screen">
    <div class="flex justify-between items-center"><button onclick="show('result')">‹ Back</button><h1 class="font-bold text-lg">ChartAI</h1><button>⎙</button></div>
    
    <div class="card mt-5 p-4 !bg-[#1a1a1a]">
      <div class="flex justify-between text-[10px] tracking-widest"><span class="text-gray-400">WHICH WAY IS IT LEANING?</span><span id="detail-lean" class="text-[#ff4d6d] font-bold">STRONGLY DOWN</span></div>
      <div class="relative mt-4 h-8 rounded-full overflow-hidden flex"><div class="flex-1 bg-[#ff4d5a]"></div><div class="flex-1 bg-[#7a2e2e]"></div><div class="flex-1 bg-[#8a6a2e]"></div><div class="flex-1 bg-[#2e7a3a]"></div><div class="flex-1 bg-[#00ff66]"></div><div id="slider" class="absolute top-0 w-3 h-full bg-white rounded-full shadow" style="left:18%"></div></div>
      <div class="flex justify-between text-[10px] mt-2"><span class="text-[#ff4d5a]">Strongly Down</span><span class="text-gray-500">Mixed</span><span class="text-green-400">Strongly Up</span></div>
    </div>

    <div class="card mt-4 p-4 flex justify-between items-center"><div class="flex items-center gap-3"><div class="flex gap-1"><div class="w-4 h-2 bg-white rounded"></div><div class="w-4 h-2 bg-white rounded"></div><div class="w-4 h-2 bg-white rounded"></div></div><div><p class="text-xs font-bold">HIGH confidence</p><p class="text-[11px] text-gray-400">Most signals point the same way</p></div></div><div>ⓘ</div></div>

    <div class="card mt-4 p-4 border border-[#2dd4bf]/30"><p class="neon-text text-[11px] tracking-widest">👁 WHAT TO WATCH NEXT</p><p id="detail-watch" class="text-sm mt-2">Watch how the next 4-hour candle closes around 50,933 — a break below keeps the down-read intact.</p></div>

    <div class="grid grid-cols-2 gap-3 mt-3">
      <div class="card p-3 !bg-[#0f1f15] !border-green-900"><p class="text-[10px] text-green-400 tracking-widest">↗ WATCH ABOVE</p><p class="text-xs mt-2">reclaims 51,784 resistance zone with conviction</p></div>
      <div class="card p-3 !bg-[#1f1212] !border-red-900"><p class="text-[10px] text-red-400 tracking-widest">↘ WATCH BELOW</p><p class="text-xs mt-2">closes below 50,891 on H4 timeframe</p></div>
    </div>

    <div class="flex gap-2 mt-4"><span class="card px-3 py-2 text-xs">🌊 Downtrend</span><span class="card px-3 py-2 text-xs">〰️ High (choppy)</span><span class="card px-3 py-2 text-xs bg-[#1f152e]">👥 Bearish</span></div>

    <div class="card mt-5 p-4">
      <p class="text-[11px] tracking-widest text-gray-400">☐ WHAT TO DO NEXT</p>
      <div class="grid grid-cols-2 gap-2 mt-3"><button class="py-2 rounded-full bg-[#3a1a1a] text-[#ff4d6d] text-xs font-bold border border-[#ff4d6d]">Down</button><button class="py-2 rounded-full bg-[#1a1a1a] text-gray-400 text-xs">Up</button></div>
      <div class="mt-4 text-[13px] leading-relaxed text-gray-200 border-l-2 border-gray-700 pl-3">Watch for the current or next 4-hour candle to close below 50,891 with a solid red body. A clean break confirms sellers are extending the downward impulse move.</div>
      <p class="text-xs mt-4 text-gray-400"><span class="text-red-400">✕ Read fails at</span> 51,784 flip zone — acceptable above refutes short-term breakdown.</p>
      <p class="text-xs mt-2 text-gray-400"><span class="text-green-400">⊕ Next zone to study</span> 50,000 psychological level — next major round-number zone to observe.</p>
    </div>
  </div>
</div>

<script>
const file = document.getElementById('file');
const preview = document.getElementById('preview');
const placeholder = document.getElementById('placeholder');
let lastSell = true;

file.onchange = e => {
  const f = e.target.files[0]; if(!f) return;
  preview.src = URL.createObjectURL(f);
  preview.classList.remove('hidden'); placeholder.classList.add('hidden');
}

document.getElementById('scanBtn').onclick = () => {
  if(preview.classList.contains('hidden')) return alert('Upload a chart first');
  // Fake AI logic: random but looks real
  const confidence = 68 + Math.floor(Math.random()*20);
  const isSell = Math.random() > 0.3;
  lastSell = isSell;
  document.getElementById('res-direction').textContent = isSell ? 'SELL' : 'BUY';
  document.getElementById('res-direction').className = `text-[32px] font-extrabold tracking-[0.2em] mt-3 ${isSell?'text-[#ff4d6d]':'text-[#00ff88]'}`;
  document.getElementById('conf-text').textContent = confidence+'%';
  document.getElementById('bar-buy').style.width = (100-confidence)+'%';
  document.getElementById('bar-sell').style.width = confidence+'%';
  if(!isSell){ document.getElementById('bar-buy').style.width = confidence+'%'; document.getElementById('bar-sell').style.width = (100-confidence)+'%'; }
  const offset = 219 - (219*confidence/100);
  document.getElementById('conf-circle').style.strokeDashoffset = offset;
  document.getElementById('conf-circle').setAttribute('stroke', isSell ? '#00ff88' : '#00ff88');
  const price = 83600 + Math.random()*500;
  document.getElementById('res-support').textContent = (price-700).toFixed(3);
  document.getElementById('res-resist').textContent = price.toFixed(3);
  document.getElementById('res-desc').textContent = isSell ? '"Strong bearish momentum after breaking key support, looking for a quick bounce then continuation down."' : '"Bullish reversal forming after strong support hold, momentum shifting up."';
  show('result');
}

function show(name){
  document.getElementById('screen-scanner').classList.add('hidden');
  document.getElementById('screen-result').classList.add('hidden');
  document.getElementById('screen-detail').classList.add('hidden');
  document.getElementById('screen-'+name).classList.remove('hidden');
}
function goDetail(){
  document.getElementById('detail-lean').textContent = lastSell ? 'STRONGLY DOWN' : 'STRONGLY UP';
  document.getElementById('detail-lean').className = lastSell ? 'text-[#ff4d6d] font-bold' : 'text-[#00ff88] font-bold';
  document.getElementById('slider').style.left = lastSell ? '18%' : '80%';
  show('detail');
}
</script>
</body>
</html>