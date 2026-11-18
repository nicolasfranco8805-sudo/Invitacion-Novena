<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>¡Feliz Navidad!</title>
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
        }

        .container {
            text-align: center;
            perspective: 1000px;
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
        }

        .instruction {
            margin-top: 20px;
            font-size: 0.85rem;
            color: #aaa;
            letter-spacing: 1px;
        }
    </style>
</head>
<body>

    <div class="container">
        <div class="card" id="christmasCard" onclick="toggleCard()">
            <div class="card-face card-front">
                <div class="tree-icon">🎄</div>
                <h1>¡Invitación Novena!</h1>
                <p>Haz clic para abrir la invitación</p>
            </div>
            <div class="card-face card-back">
                <h2>¡Familia Franco Manchego!</h2>
                <p>Que esta época navideña esté llena de alegría, paz y grandes momentos junto a tus seres queridos. !</p>Tenemos el placer de invitarlos a celebrar el tercer día de la Novena de Aguinaldos
                <p style="margin-top: 20px; font-weight: bold; color: #b30000;">✨ ¡Te Esperamos! ✨</p>
            </div>
        </div>
        <div class="instruction">Toca la tarjeta para voltearla</div>
    </div>

    <script>
        function toggleCard() {
            const card = document.getElementById('christmasCard');
            card.classList.toggle('open');
        }
    </script>

</body>
</html>
