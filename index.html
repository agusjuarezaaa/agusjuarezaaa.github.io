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
    height: 100%;
    background: transparent;
  }

  .scroll-track {
    height: 600vh;
    position: relative;
  }

  .sticky-wrap {
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
    gap: 6px;
    user-select: none;
  }

  .line {
    width: 1px;
    height: 40px;
    background: rgba(255,255,255,0.25);
    margin-bottom: 6px;
  }

  .label {
    font-family: 'Lato', sans-serif;
    font-weight: 300;
    font-size: 12px;
    letter-spacing: 0.3em;
    text-transform: uppercase;
    color: rgba(255,255,255,0.55);
  }

  .depth {
    font-family: 'Lato', sans-serif;
    font-weight: 300;
    font-size: 80px;
    letter-spacing: 0.04em;
    color: #ffffff;
    line-height: 1;
    font-variant-numeric: tabular-nums;
  }

  .unit {
    font-size: 34px;
    color: rgba(255,255,255,0.4);
    margin-left: 6px;
  }
</style>
</head>
<body>
<div class="scroll-track">
  <div class="sticky-wrap">
    <div class="counter">
      <div class="line"></div>
      <div class="label">Profundidad</div>
      <div class="depth"><span id="num">000</span><span class="unit">m</span></div>
    </div>
  </div>
</div>

<script>
  const el = document.getElementById('num');
  let current = 0;
  let target = 0;
  let rafId = null;

  function pad(n) {
    return String(Math.round(n)).padStart(3, '0');
  }

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

  function setDepth(value) {
    target = Math.max(0, Math.min(1000, value));
    if (!rafId) rafId = requestAnimationFrame(animate);
  }

  window.addEventListener('scroll', function() {
    const scrolled = window.scrollY;
    const total = document.documentElement.scrollHeight - window.innerHeight;
    const pct = total > 0 ? scrolled / total : 0;
    setDepth(pct * 1000);
  }, { passive: true });
</script>
</body>
</html>
