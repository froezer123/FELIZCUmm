﻿<!DOCTYPE html>
<html lang="es">

<head>
    <meta charset="UTF-8">
    <title>Joshua</title>
    <style>
        body {
            font-family: 'Arial', sans-serif;
            text-align: center;
            margin-top: 50px;
            background-color: #ffe0e0;
            padding: 20px;
        }

        #container {
            max-width: 600px;
            margin: auto;
            padding: 20px;
            background-color: #fff;
            border-radius: 10px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
        }

        h2 {
            color: #d6336c;
            font-size: 24px;
            margin-bottom: 30px;
        }

        button {
            padding: 15px 30px;
            font-size: 18px;
            cursor: pointer;
            border: none;
            border-radius: 5px;
        }

        #siButton {
            background-color: #4CAF50;
            color: white;
            margin-left: 20px;
        }

        #noButton {
            background-color: #f44336;
            color: white;
            margin-left: 20px;
        }

        #result img {
            max-width: 100%;
            height: auto;
            margin-top: 20px;
        }

        .heart {
            position: fixed;
            bottom: 20px;
            animation: float 5s ease-in-out infinite;
            font-size: 24px;
            opacity: 0;
        }

        @keyframes float {
            0% {
                transform: translateY(-850px);
                opacity: 1;
            }

            100% {
                transform: translateY(0px) rotate(360deg);
                opacity: 0;
            }
        }
    </style>
</head>

<body>

    <div id="container">
        <h2>¿YA COMISTE VERDA AMORCITO?</h2>
        <button id="siButton">Sí</button>
        <button id="noButton">No</button>
        <div id="result"></div>
    </div>

    <script>
        let clickCount = 0;
        const container = document.getElementById('container');
        const result = document.getElementById('result');

        const frasesGraciosas = [
            "Porque no lo haz echo, te vas enfermar!",
            "Aunque sea un vasito de agua pura plis",
            "Que hago si te enfermas nomas por no comer",
            "come si no me pongo triste",
            "si comes te voy a dar muchos abrazos",
            "come, asi estas mas chula de lo que eres porfi",
            "le voy a escribir a tu mama que te pegue",
            
        ];

        document.getElementById('noButton').addEventListener('click', () => {
            clickCount++;
            noButton.style.filter = `blur(${clickCount / 3}px)`;

            let fontSize = parseInt(window.getComputedStyle(siButton).fontSize);
            let paddingVert = parseInt(window.getComputedStyle(siButton).paddingTop);
            let paddingHoriz = parseInt(window.getComputedStyle(siButton).paddingRight);

            siButton.style.fontSize = `${fontSize + 1}px`;
            siButton.style.padding = `${paddingVert + 1}px ${paddingHoriz + 5}px`;

            let randomNumber = Math.floor(Math.random() * frasesGraciosas.length);
            let randomNumberImg = Math.floor(Math.random() * 10 + 1);
            result.innerHTML = `<p>${frasesGraciosas[randomNumber]}</p><img src="images/${randomNumberImg}.jpg" width="200px" height="100px">`;
        });

        document.getElementById('siButton').addEventListener('click', () => {

            siButton.style.padding = `15px 30px`;
            siButton.style.fontSize = `18px`;

            noButton.style.filter = 'none';
            clickCount = 0;

            result.innerHTML = `<p>Sabía que me harias caso (o talvez te obligo tu mama jsjs) ❤️</p><img src="images/happy.jpg" width="200px" height="100px">`;
            for (let i = 0; i < 300; i++) {
                createHeart();
            }
        });

        function createHeart() {
            const heart = document.createElement('div');
            heart.className = 'heart';
            heart.innerHTML = '❤️';
            document.body.appendChild(heart);
            heart.style.left = Math.random() * 100 + 'vw';
            heart.style.animationDuration = Math.random() * 2 + 3 + 's'; // Duración entre 3-5s
            heart.addEventListener('animationend', function () {
                heart.remove();
            });
        }

    </script>

</body>

</html>
