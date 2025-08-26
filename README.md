<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Te Amo Isa 💗</title>
    <style>
        body {
            background-color: #ffe6f0;
            color: #d81b60;
            font-family: 'Arial', sans-serif;
            text-align: center;
            overflow: hidden;
            margin: 0;
            height: 100vh;
            width: 100vw;
            touch-action: manipulation;
        }
        .te-amo {
            position: absolute;
            font-size: 22px;
            opacity: 1;
            animation: fadeIn 1s forwards;
            user-select: none;
        }
        .heart {
            color: #ff66b2;
            font-size: 24px;
        }
        @keyframes fadeIn {
            0% { opacity: 0; transform: scale(0.8); }
            100% { opacity: 1; transform: scale(1); }
        }
        @keyframes explode {
            0% { transform: translate(0, 0); opacity: 1; }
            100% { transform: translate(var(--x), var(--y)); opacity: 0; }
        }
        .special {
            position: absolute;
            font-size: 28px;
            font-weight: bold;
            left: 50%;
            top: 50%;
            transform: translate(-50%, -50%);
            color: #c2185b;
            text-shadow: 2px 2px 5px rgba(255, 192, 203, 0.8);
            white-space: pre-line;
        }
    </style>
</head>
<body>
    <!-- Música de fondo -->
    <audio id="bg-music" autoplay loop>
        <source src="music.mp3" type="audio/mp3">
    </audio>

    <script>
        function createTeAmo(x, y, message) {
            const teAmo = document.createElement('div');
            teAmo.className = 'te-amo';
            teAmo.innerHTML = message + ' <span class="heart">💗</span>';
            teAmo.style.left = x + 'px';
            teAmo.style.top = y + 'px';

            const angle = Math.random() * 2 * Math.PI;
            const distance = Math.random() * 200 + 100;
            teAmo.style.setProperty('--x', `${Math.cos(angle) * distance}px`);
            teAmo.style.setProperty('--y', `${Math.sin(angle) * distance}px`);
            teAmo.style.animation = 'explode 3s forwards';

            document.body.appendChild(teAmo);

            setTimeout(() => teAmo.remove(), 3000);
        }

        function addTeAmo(event) {
            const numTeAmos = 10;
            for (let i = 0; i < numTeAmos; i++) {
                createTeAmo(event.clientX, event.clientY, 'Te amuuuu');
            }
        }

        const specialMessage = document.createElement('div');
        specialMessage.className = 'special';
        specialMessage.innerHTML = 'Isa 💕\nTe amuuuu muchooo con todo mi corazón\nEres la mejor persona del mundo 🌎💗';
        document.body.appendChild(specialMessage);

        document.body.addEventListener('click', addTeAmo);
        document.body.addEventListener('touchstart', (e) => {
            const touch = e.touches[0];
            addTeAmo({ clientX: touch.clientX, clientY: touch.clientY });
        });

        // Inicia la música al primer toque (por restricciones de celulares)
        document.body.addEventListener('click', () => {
            document.getElementById('bg-music').play();
        }, { once: true });
    </script>
</body>
</html>
