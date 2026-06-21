<!DOCTYPE html>
<html>
<head>
    <style>
        /* Estilos exactos para que se vea como en tu imagen */
        body { margin: 0; padding: 0; background: transparent !important; overflow: hidden; }
        .c { position: fixed; top: 50px; left: 40px; pointer-events: none; color: #ffffff; font-family: sans-serif; }
        .t { font-size: 12px; letter-spacing: 0.2em; text-transform: uppercase; color: #ffffff; margin-bottom: 2px; }
        .n { font-size: 48px; font-weight: 300; line-height: 1; }
        .m { font-size: 24px; }
    </style>
</head>
<body>
    <div class="c">
        <div class="t">Profundidad</div>
        <div id="v" class="n">000<span class="m">m</span></div>
    </div>
    <script>
        // Escucha el scroll de la página padre (Readymag)
        window.parent.addEventListener('scroll', () => {
            const totalScroll = window.parent.document.documentElement.scrollHeight - window.parent.innerHeight;
            const scrollPos = window.parent.scrollY;
            const percent = totalScroll > 0 ? (scrollPos / totalScroll) : 0;
            
            // Cambia 500 por el número de metros máximo que quieras llegar
            const depth = Math.floor(percent * 500);
            
            document.getElementById('v').innerHTML = depth.toString().padStart(3, '0') + '<span class="m">m</span>';
        });
    </script>
</body>
</html>
