<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <link href="https://fonts.googleapis.com/css2?family=Lato:wght@300&display=swap" rel="stylesheet">
    <style>
        .meter-wrapper { 
            position: fixed; top: 50px; left: 40px; 
            font-family: 'Lato', sans-serif !important; 
            pointer-events: none;
        }
        .meter-wrapper .titulo { 
            font-size: 8px !important; letter-spacing: 0.3em !important; 
            text-transform: uppercase; color: rgba(255,255,255,0.4); 
            margin-bottom: 4px;
        }
        .meter-wrapper #meter { 
            font-size: 20px !important; font-weight: 300 !important; 
            color: #ffffff !important; line-height: 1;
        }
    </style>
</head>
<body style="margin:0; background:transparent !important;">

    <div class="meter-wrapper">
        <div class="titulo">Profundidad</div>
        <div id="meter">000m</div>
    </div>

    <script>
        window.addEventListener('message', (event) => {
            if (event.data.type === 'scroll') {
                // Aquí cambiamos el 500 para que el número llegue hasta 500m máximo
                const maxDepth = 500; 
                const depth = Math.floor(event.data.percent * maxDepth);
                document.getElementById('meter').innerText = depth.toString().padStart(3, '0') + 'm';
            }
        });
    </script>
</body>
</html>
2. El iframe para Readymag
Este es el mismo código puente. Al usar pointer-events: none;, garantizamos que no interfiera con los clics ni el diseño de tu web.

HTML
<iframe id="depthFrame" src="https://agusjuarezaaa.github.io/" style="width:100%; height:100%; border:none; background:transparent; position:fixed; top:0; left:0; pointer-events:none; z-index:999999;" scrolling="no" allowtransparency="true"></iframe>

<script>
    window.addEventListener('scroll', () => {
        const scrollTotal = document.documentElement.scrollHeight - window.innerHeight;
        const percent = scrollTotal > 0 ? (window.scrollY / scrollTotal) : 0;
        const frame = document.getElementById('depthFrame');
        if (frame && frame.contentWindow) {
            frame.contentWindow.postMessage({type: 'scroll', percent: percent}, '*');
        }
    });
</script>
