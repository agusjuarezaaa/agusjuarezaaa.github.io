<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <style>
        body, html { margin: 0; padding: 0; background: transparent !important; overflow: hidden; font-family: sans-serif !important; }
        .contador-wrapper { position: fixed; top: 50px; left: 40px; pointer-events: none; color: #ffffff; }
        .titulo { font-size: 10px !important; letter-spacing: 0.3em !important; text-transform: uppercase !important; color: rgba(255, 255, 255, 0.6) !important; margin-bottom: 5px !important; font-weight: normal !important; }
        .numero { font-size: 32px !important; font-weight: 300 !important; line-height: 1 !important; color: #ffffff !important; }
    </style>
</head>
<body>
    <div class="contador-wrapper">
        <div class="titulo">Profundidad</div>
        <div id="valor-metros" class="numero">000m</div>
    </div>

    <script>
        // Este script detecta el scroll desde la página que contiene al iframe
        window.parent.addEventListener('scroll', () => {
            const scrollTotal = window.parent.document.documentElement.scrollHeight - window.parent.innerHeight;
            const percent = scrollTotal > 0 ? (window.parent.scrollY / scrollTotal) : 0;
            const maxDepth = 500; 
            const depth = Math.floor(percent * maxDepth);
            document.getElementById('valor-metros').innerText = depth.toString().padStart(3, '0') + 'm';
        });
    </script>
</body>
</html>
