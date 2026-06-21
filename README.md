<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <link href="https://fonts.googleapis.com/css2?family=Lato:wght@300&display=swap" rel="stylesheet">
    <style>
        body { background: transparent !important; margin: 0; overflow: hidden; }
        
        .viewport-container {
            position: fixed; top: 0; left: 0; width: 100vw; height: 100vh;
            pointer-events: none;
        }

        /* Título y números más grandes y visibles */
        .panel {
            position: absolute; left: 40px; top: 50px;
            display: flex; flex-direction: column; gap: 10px;
        }

        .titulo {
            font-family: 'Lato', sans-serif !important;
            font-size: 12px !important; 
            letter-spacing: 0.3em !important; 
            text-transform: uppercase; 
            color: rgba(255,255,255,0.6);
        }

        #meter { 
            font-family: 'Lato', sans-serif !important; 
            font-size: 24px !important; 
            font-weight: 300 !important; 
            color: #ffffff !important;
        }

        .linea {
            position: absolute; left: 45px; top: 100px; bottom: 50px;
            width: 1px; background: rgba(255,255,255,0.2);
        }
    </style>
</head>
<body>

    <div class="viewport-container">
        <div class="panel">
            <div class="titulo">Profundidad</div>
            <div id="meter">000m</div>
        </div>
        <div class="linea"></div>
    </div>

    <script>
        const meterEl = document.getElementById('meter');

        window.addEventListener('scroll', () => {
            const scrollTotal = document.documentElement.scrollHeight - window.innerHeight;
            const scrollActual = window.scrollY;
            
            // Calculamos profundidad de 0 a 1000
            const porcentaje = scrollTotal > 0 ? (scrollActual / scrollTotal) : 0;
            const depth = Math.floor(porcentaje * 1000);
            
            // Actualizamos el texto
            meterEl.innerText = depth.toString().padStart(3, '0') + 'm';
        });
    </script>
</body>
</html>
