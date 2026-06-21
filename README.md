<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Profundidad</title>
<link href="https://fonts.googleapis.com/css2?family=Lato:wght@300;400&display=swap" rel="stylesheet">
<style>
  * { margin: 0; padding: 0; box-sizing: border-box; }

  html, body { height: 100%; background: transparent; }

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
    gap: 4px;
    user-select: none;
  }

  .line {
    width: 1px;
    height: 24px;
    background: rgba(255,255,255,0.2);
    margin-bottom: 4px;
  }

  .label {
    font-family: 'Lato', sans-serif;
    font-weight: 300;
    font-size: 9px;
    letter-spacing: 0.3em;
    text-transform: uppercase;
    color: rgba(255,255,255,0.45);
  }

  .depth {
    font-family: 'Lato', sans-serif;
    font-weight: 300;
    font-size: 28px;
    letter-spacing: 0.08em;
    color: #ffffff;
    line-height: 1;
    font-variant-numeric: tabular-nums;
  }

  .unit {
    font-size: 14px;
    color: rgba(255,255,255,0.35);
    margin-left: 3px;
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
