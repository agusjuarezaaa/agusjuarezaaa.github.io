<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Profundidad</title>
<link href="https://fonts.googleapis.com/css2?family=Lato:wght@300;400&display=swap" rel="stylesheet">
<style>
  * { margin: 0; padding: 0; box-sizing: border-box; }

  html {
    scrollbar-width: none;
    -ms-overflow-style: none;
  }
  html::-webkit-scrollbar { display: none; }

  body { background: transparent; height: 100%; }

  .track { height: 500vh; }

  .sticky {
    position: sticky;
    top: 0;
    height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .counter {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 3px;
    user-select: none;
  }

  .line {
    width: 1px;
    height: 18px;
    background: rgba(255,255,255,0.2);
    margin-bottom: 3px;
  }

  .label {
    font-family: 'Lato', sans-serif;
    font-weight: 300;
    font-size: 8px;
    letter-spacing: 0.28em;
    text-transform: uppercase;
    color: rgba(255,255,255,0.4);
  }

  .depth {
    font-family: 'Lato', sans-serif;
    font-weight: 300;
    font-size: 18px;
    letter-spacing: 0.08em;
    color: #ffffff;
    line-height: 1;
    font-variant-numeric: tabular-nums;
  }

  .unit {
    font-size: 10px;
    color: rgba(255,255,255,0.3);
    margin-left: 2px;
  }
</style>
</head>
<body>
<div class="track">
  <div class="sticky">
    <div class="counter">
      <div class="line"></div>
      <div class="label">Profundidad</div>
      <div class="depth"><span id="num">000</span><span class="unit">m</span></div>
    </div>
  </div>
</div>

<script>
  const el = document.getElementById('num');
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

  window.addEventListener('scroll', function() {
    var total = document.documentElement.scrollHeight - window.innerHeight;
    var pct = total > 0 ? window.scrollY / total : 0;
    setDepth(pct * 1000);
  }, { passive: true });
</script>
</body>
</html>
