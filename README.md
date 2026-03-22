<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Para el amor de mi vida</title>
    <style>
        body {
            margin: 0;
            height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            background: #fff0f3;
            font-family: 'Segoe UI', sans-serif;
            overflow: hidden;
        }

        .card {
            background: white;
            padding: 40px;
            border-radius: 25px;
            box-shadow: 0 20px 40px rgba(0,0,0,0.1);
            text-align: center;
            max-width: 400px;
            z-index: 100;
            border: 1px solid #ffccd5;
        }

        h1 { color: #ff4d6d; margin-bottom: 10px; font-size: 2.2rem; }
        p { color: #594d5b; line-height: 1.6; font-size: 1.1rem; }

        .btn-surprise {
            background: #ff4d6d;
            color: white;
            border: none;
            padding: 15px 35px;
            border-radius: 50px;
            font-size: 1.1rem;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s ease;
            box-shadow: 0 10px 20px rgba(255, 77, 109, 0.3);
            margin-top: 20px;
        }

        /* Corazones de la lluvia */
        .heart {
            position: fixed;
            top: -50px;
            font-size: 2rem;
            user-select: none;
            pointer-events: none;
            z-index: 10;
            animation: fall linear forwards;
        }

        @keyframes fall {
            to { transform: translateY(110vh) rotate(360deg); }
        }

        #extra-content {
            display: none;
            margin-top: 25px;
            animation: fadeIn 2s ease;
        }

        @keyframes fadeIn { from { opacity: 0; } to { opacity: 1; } }

        .final-text {
            display: block;
            margin-top: 15px;
            font-size: 1.5rem;
            color: #c9184a;
            font-weight: bold;
        }
    </style>
</head>
<body>

    <!-- Elemento de Audio Oculto -->
    <audio id="birthdaySong" loop>
        <!-- REEMPLAZA EL LINK DE ABAJO CON EL DE TU CANCIÓN (puede ser un link de Dropbox, Drive directo o un archivo .mp3 local) -->
        <source src="musica.mp3" type="audio/mpeg">
    </audio>

    <div class="card">
        <div style="font-size: 50px; margin-bottom: 10px;">❤️</div>
        <h1>¡Feliz Cumpleaños corazon!</h1>
        <p>Hoy celebro de todo corazon que existes y que haces mi mundo mucho más bonito.</p>
        
        <button class="btn-surprise" id="magicBtn" onclick="magicStart()">Presiona aqui ✨</button>

        <div id="extra-content">
            <p>Gracias por ser mi razón de sonreír cada mañana.</p>
            <span class="final-text">¡Te amo mucho att Darwin jeje! 🌹</span>
        </div>
    </div>

    <script>
        function createHeart() {
            const heart = document.createElement('div');
            heart.classList.add('heart');
            const emojis = ['❤️', '💖', '💕', '💗', '💘', '✨'];
            heart.innerText = emojis[Math.floor(Math.random() * emojis.length)];
            heart.style.left = Math.random() * 100 + "vw";
            heart.style.fontSize = Math.random() * 20 + 20 + "px";
            const duration = Math.random() * 3 + 2; 
            heart.style.animationDuration = duration + "s";
            document.body.appendChild(heart);
            setTimeout(() => { heart.remove(); }, duration * 1000);
        }

        function magicStart() {
            // 1. Reproducir Música
            const song = document.getElementById('birthdaySong');
            song.play().catch(error => console.log("Error al reproducir: ", error));

            // 2. Mostrar mensaje y ocultar botón
            document.getElementById('extra-content').style.display = 'block';
            document.getElementById('magicBtn').style.display = 'none';

            // 3. Explosión de corazones por TODA la pantalla
            for(let i = 0; i < 100; i++) {
                setTimeout(createHeart, i * 20);
            }

            // 4. Lluvia constante
            setInterval(createHeart, 150);
        }
    </script>
</body>
</html>
