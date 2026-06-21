<!DOCTYPE html>
<html>
<head>
    <style>
        body { margin: 0; padding: 0; background: transparent; overflow: hidden; }
        .c { position: absolute; top: 50px; left: 40px; font-family: sans-serif; color: #ffffff; pointer-events: none; }
        .t { font-size: 12px; letter-spacing: 0.2em; text-transform: uppercase; color: #ffffff; margin-bottom: 2px; }
        .n { font-size: 48px; font-weight: 300; line-height: 1; }
    </style>
</head>
<body>
    <div class="c">
        <div class="t">Profundidad</div>
        <div id="v" class="n">000m</div>
    </div>
    <script>
        window.addEventListener('message', (e) => {
            if (e.data.type === 'scroll') {
                const d = Math.floor(e.data.percent * 500);
                document.getElementById('v').innerText = d.toString().padStart(3, '0') + 'm';
            }
        });
    </script>
</body>
</html>
