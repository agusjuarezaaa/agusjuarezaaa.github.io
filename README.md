<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <link href="https://fonts.googleapis.com/css2?family=Lato:wght@300&display=swap" rel="stylesheet">
    <style>
        /* Reseteo extremo para que no afecte nada fuera */
        body, html { margin: 0; padding: 0; background: transparent !important; overflow: hidden; }
        
        /* Contenedor ultra específico para que los estilos no se escapen */
        .mi-contador-aislado {
            position: fixed; top: 50px; left: 40px;
            font-family: 'Lato', sans-serif !important;
            pointer-events: none;
            z-index: 999999;
        }
        .mi-contador-aislado .titulo-profundidad {
            font-size: 8px !important;
            letter-spacing: 0.3em !important;
            text-transform: uppercase !important;
            color: rgba(255, 255, 255, 0.4) !important;
            margin-bottom: 4px !important;
        }
        .mi-contador-aislado #valor-metros {
            font-size: 20px !important;
            font-weight: 300 !important;
            color: #ffffff !important;
            line-height: 1 !important;
        }
    </style>
</head>
<body>

    <div class="mi-contador-aislado">
        <div class="titulo-profundidad">Profundidad</div>
        <div id="valor-metros">000m</div>
    </div>

    <script>
        // Escucha la señal de scroll enviada desde la web principal
        window.addEventListener('message', (event) => {
            if (event.data.type === 'scroll') {
                const maxDepth = 500; // Ajusta este límite según prefieras
                const depth = Math.floor(event.data.percent * maxDepth);
                document.getElementById('valor-metros').innerText = depth.toString().padStart(3, '0') + 'm';
            }
        });
    </script>
</body>
</html>
