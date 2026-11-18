<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Tercer Dia Novena de Aguinaldos</title>
    <style>
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            background: linear-gradient(135deg, #0f2027, #203a43, #2c5364);
            height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            overflow: hidden;
            color: #fff;
            position: relative;
        }

        /* --- EFECTO DE NIEVE ANIMADA --- */
        .snowflakes {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            overflow: hidden;
            z-index: 1;
        }

        .snowflake {
            position: absolute;
            top: -10px;
            background: #fff;
            border-radius: 50%;
            animation: fall linear infinite;
        }

        @keyframes fall {
            0% {
                transform: translateY(0) translateX(0);
                opacity: 1;
            }
            100% {
                transform: translateY(105vh) translateX(20px);
                opacity: 0.3;
            }
        }

        /* --- CONTENEDOR Y TARJETA --- */
        .container {
            text-align: center;
            perspective: 1000px;
            z-index: 2;
        }

        .card {
            width: 320px;
            height: 480px;
            background: #fff;
            border-radius: 15px;
            position: relative;
            transform-style: preserve-3d;
            transition: transform 1s ease;
            box-shadow: 0 15px 35px rgba(0,0,0,0.5);
            cursor: pointer;
            margin: 0 auto;
        }

        .card.open {
            transform: rotateY(180deg);
        }

        .card-face {
            position: absolute;
            width: 100%;
            height: 100%;
            backface-visibility: hidden;
            border-radius: 15px;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            padding: 20px;
            text-align: center;
        }

        .card-front {
            background: linear-gradient(135deg, #b30000, #ff1a1a);
            color: white;
            border: 4px solid #ffd700;
        }

        .card-front h1 {
            font-size: 2rem;
            margin-bottom: 15px;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.3);
        }

        .card-front p {
            font-size: 0.9rem;
            opacity: 0.9;
        }

        .card-back {
            background: #fdfbf7;
            color: #333;
            transform: rotateY(180deg);
            border: 4px solid #b30000;
        }

        .card-back h2 {
            color: #b30000;
            margin-bottom: 15px;
            padding-bottom: 10px;
            border-bottom: 2px solid #ddd;
            font-size: 1.5rem;
        }

        .card-back p {
            font-size: 0.95rem;
            line-height: 1.5;
            color: #555;
        }

        .tree-icon {
            font-size: 4rem;
            margin-bottom: 20px;
            animation: bounce 2s infinite;
        }

        @keyframes bounce {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-10px); }
        }

        .instruction {
            margin-top: 20px;
            font-size: 0.85rem;
            color: #aaa;
            letter-spacing: 1px;
        }

        /* --- BOTÓN DE MÚSICA --- */
        .music-control {
            position: absolute;
            bottom: 20px;
            right: 20px;
            z-index: 10;
            background: rgba(255, 255, 255, 0.2);
            border: 2px solid #fff;
            color: white;
            padding: 10px 15px;
            border-radius: 30px;
            cursor: pointer;
            font-size: 0.9rem;
            display: flex;
            align-items: center;
            gap: 8px;
            backdrop-filter: blur(5px);
            transition: background 0.3s;
        }

        .music-control:hover {
            background: rgba(255, 255, 255, 0.4);
        }
    </style>
</head>
<body>

    <!-- Animación de Nieve -->
    <div class="snowflakes" aria-hidden="true">
        <!-- Generamos varios copos de nieve con diferentes tamaños y velocidades -->
        <div class="snowflake" style="left: 10%; width: 8px; height: 8px; animation-duration: 5s; animation-delay: 0s;"></div>
        <div class="snowflake" style="left: 20%; width: 5px; height: 5px; animation-duration: 7s; animation-delay: 2s;"></div>
        <div class="snowflake" style="left: 30%; width: 10px; height: 10px; animation-duration: 4s; animation-delay: 1s;"></div>
        <div class="snowflake" style="left: 40%; width: 6px; height: 6px; animation-duration: 6s; animation-delay: 3s;"></div>
        <div class="snowflake" style="left: 50%; width: 9px; height: 9px; animation-duration: 5.5s; animation-delay: 0.5s;"></div>
        <div class="snowflake" style="left: 60%; width: 4px; height: 4px; animation-duration: 8s; animation-delay: 4s;"></div>
        <div class="snowflake" style="left: 70%; width: 7px; height: 7px; animation-duration: 4.5s; animation-delay: 1.5s;"></div>
        <div class="snowflake" style="left: 80%; width: 10px; height: 10px; animation-duration: 6.5s; animation-delay: 2.5s;"></div>
        <div class="snowflake" style="left: 90%; width: 6px; height: 6px; animation-duration: 5s; animation-delay: 3.5s;"></div>
    </div>

    <!-- Música de fondo (Audio libre de derechos de Navidad) -->
    <audio id="christmasAudio" loop>
    <source src="https://www.youtube.com/watch?v=woL6_wn7-rc&list=PL-xVUW9dZgbdX9bQ8TiLIZTjs6b9cnnqs" type="audio/mpeg">
    Tu navegador no soporta elementos de audio.
</audio>

    <!-- Botón para Activar/Desactivar Música -->
    <button class="music-control" onclick="toggleMusic()">
        🎵 <span id="musicText">Reproducir Música</span>
    </button>

    <div class="container">
        <div class="card" id="christmasCard" onclick="toggleCard()">
            <div class="card-face card-front">
                <div class="tree-icon">🎄</div>
                <h1>¡Invitación Novena!</h1>
                <p>Haz clic para abrir la invitación</p>
            </div>
            <div class="card-face card-back">
                <h2>¡La Familia Franco Manchego Te invita a celebrar el tercer dia de la Novena de Aguinaldos!</h2>
                <p>Acompáñanos a vivir la alegría de la novena, compartir en familia y disfrutar de este momento especial lleno de paz y unión.</p>
                <p style="margin-top: 20px; font-weight: bold; color: #b30000;">✨ ¡Confirma asistencia! ✨</p>
            </div>
        </div>
        <div class="instruction">Toca la tarjeta para Abrir</div>
    </div>

    <script>
        function toggleCard() {
            const card = document.getElementById('christmasCard');
            card.classList.toggle('open');
        }

        function toggleMusic() {
            const audio = document.getElementById('christmasAudio');
            const musicText = document.getElementById('musicText');

            if (audio.paused) {
                audio.play();
                musicText.textContent = "Silenciar Música";
            } else {
                audio.pause();
                musicText.textContent = "Reproducir Música";
            }
        }
    </script>

</body>
</html>
