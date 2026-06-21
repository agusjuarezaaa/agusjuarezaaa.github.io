<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <style>
        /* Estilos aislados, sin tocar etiquetas globales */
        .contador-wrapper {
            position: fixed; top: 0; left: 0;
            font-family: 'Arial', sans-serif !important;
            pointer-events: none;
        }
        .titulo {
            font-size: 8px !important;
            text-transform: uppercase !important;
            letter-spacing: 0.3em !important;
            color: #ffffff !important;
            margin-bottom: 4px !important;
        }
        .metros {
            font-size: 20px !important;
            color: #ffffff !important;
        }
    </style>
</head>
<body style="margin:0; padding:0; background:transparent !important;">

    <div class="contador-wrapper">
        <div class="titulo">Profundidad</div>
        <div id="valor-metros" class="metros">000m</div>
    </div>

    <script>
        window.addEventListener('message', (event) => {
            if (event.data.type === 'scroll') {
                const maxDepth = 500;
                const depth = Math.floor(event.data.percent * maxDepth);
                document.getElementById('valor-metros').innerText = depth.toString().padStart(3, '0') + 'm';
            }
        });
    </script>
</body>
</html>
