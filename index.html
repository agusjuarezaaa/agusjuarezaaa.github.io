<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Profundidad</title>
<link href="https://fonts.googleapis.com/css2?family=Lato:wght@300;400&display=swap" rel="stylesheet">
<style>
  * { margin: 0; padding: 0; box-sizing: border-box; }

  html, body {
    width: 100%;
    height: 100%;
    overflow: hidden;
    background: transparent;
  }

  #scroller {
    position: absolute;
    top: 0; left: 0;
    width: calc(100% + 20px);
    height: 100%;
    overflow-y: scroll;
    scrollbar-width: none;
    -ms-overflow-style: none;
    z-index: 1;
  }
  #scroller::-webkit-scrollbar { display: none; }

  #track { height: 500vh; }

  #ui {
    position: fixed;
    top: 0; left: 0;
    width: 100%;
    height: 100%;
    pointer-events: none;
    z-index: 2;
  }

  .counter {
    position: absolute;
    left: 50%;
    transform: translateX(-50%);
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 4px;
    user-select: none;
    transition: top 0.05s linear;
  }

  .label {
    font-family: 'Lato', sans-serif;
    font-weight: 300;
    font-size: 9px;
    letter-spacing: 0.3em;
    text-transform: uppercase;
    color: rgba(255,255,255,0.5);
  }

  .depth {
    font-family: 'Lato', sans-serif;
    font-weight: 300;
    font-size: 36px;
    letter-spacing: 0.06em;
    color: #ffffff;
    line-height: 1;
    font-variant-numeric: tabular-nums;
  }

  .unit {
    font-size: 16px;
    color: rgba(255,255,255,0.35);
    margin-left: 3px;
  }
</style>
</head>
<body>

<div id="scroller">
  <div id="track"></div>
</div>

<div id="ui">
  <div class="counter" id="counter">
    <div class="label">Profundidad</div>
    <div class="depth"><span id="num">000</span><span class="unit">m</span></div>
  </div>
</div>

<script>
  const el = document.getElementById('num');
  const counter = document.getElementById('counter');
  const scroller = document.getElementById('scroller');
  let current = 0, target = 0, rafId = null;

  function pad(n) { return String(Math.round(n)).padStart(3, '0'); }

  function animate() {
    if (Math.abs(current - target) < 0.5) {
      current = target;
      el.textContent = pad(current);
      rafId = null;
      return;
    }
    current += (target - current) * 0.1;
    el.textContent = pad(current);
    rafId = requestAnimationFrame(animate);
  }

  function setDepth(v) {
    target = Math.max(0, Math.min(1000, v));
    if (!rafId) rafId = requestAnimationFrame(animate);
  }

  scroller.addEventListener('scroll', function() {
    var total = scroller.scrollHeight - scroller.clientHeight;
    var pct = total > 0 ? scroller.scrollTop / total : 0;

    // número baja
    setDepth(pct * 1000);

    // contador se mueve hacia abajo: empieza en 10% y llega al 80% del alto
    var topPct = 10 + (pct * 70);
    counter.style.top = topPct + '%';

  }, { passive: true });

  counter.style.top = '10%';
</script>
</body>
</html>
