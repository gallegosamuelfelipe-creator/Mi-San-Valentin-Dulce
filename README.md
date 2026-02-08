# Mi-San-Valentin-Dulce
<!DOCTYPE html>

<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>💌 Una Pregunta Especial</title>
    <link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@1,400;1,600&family=Quicksand:wght@300;400;500&display=swap" rel="stylesheet">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

```
    body {
        font-family: 'Quicksand', sans-serif;
        overflow-x: hidden;
        min-height: 100vh;
        background: #0f1729;
        position: relative;
    }

    /* Estrellas */
    .stars {
        position: fixed;
        width: 100%;
        height: 100%;
        overflow: hidden;
    }

    .star {
        position: absolute;
        width: 2px;
        height: 2px;
        background: white;
        border-radius: 50%;
        animation: twinkle 3s infinite ease-in-out;
    }

    @keyframes twinkle {
        0%, 100% { opacity: 0.3; }
        50% { opacity: 1; }
    }

    /* Luna */
    .moon {
        position: fixed;
        top: 40px;
        right: 30px;
        width: 100px;
        height: 100px;
        background: radial-gradient(circle at 30% 30%, #fef9e7, #f4e7c3);
        border-radius: 50%;
        box-shadow: 0 0 60px rgba(254, 249, 231, 0.6),
                    inset -10px -10px 20px rgba(0, 0, 0, 0.1);
        animation: moonGlow 4s infinite ease-in-out;
    }

    @keyframes moonGlow {
        0%, 100% { box-shadow: 0 0 60px rgba(254, 249, 231, 0.6), inset -10px -10px 20px rgba(0, 0, 0, 0.1); }
        50% { box-shadow: 0 0 80px rgba(254, 249, 231, 0.8), inset -10px -10px 20px rgba(0, 0, 0, 0.1); }
    }

    /* Contenedor principal */
    .container {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        min-height: 100vh;
        position: relative;
        z-index: 10;
        padding: 20px;
    }

    /* Texto superior */
    .top-text {
        font-family: 'Quicksand', sans-serif;
        font-size: 24px;
        color: white;
        text-align: center;
        margin-bottom: 30px;
        font-weight: 400;
        line-height: 1.5;
        max-width: 90%;
    }

    /* Sobre cerrado */
    .envelope {
        position: relative;
        width: 90%;
        max-width: 320px;
        height: 200px;
        cursor: pointer;
        transition: transform 0.3s ease;
    }

    .envelope:hover {
        transform: scale(1.05);
    }

    /* Cuerpo principal del sobre */
    .envelope-body {
        position: absolute;
        width: 100%;
        height: 100%;
        background: linear-gradient(180deg, #f5c6cb 0%, #f5b7be 50%, #f5c6cb 100%);
        border-radius: 8px;
        z-index: 1;
        box-shadow: 0 10px 30px rgba(0, 0, 0, 0.5);
    }

    /* Parte trasera decorativa */
    .envelope-back {
        position: absolute;
        width: 100%;
        height: 100%;
        background: linear-gradient(180deg, #e8a5ad 0%, #d49099 100%);
        border-radius: 8px;
        z-index: 0;
    }

    /* Solapa superior */
    .envelope-flap {
        position: absolute;
        width: 100%;
        height: 40%;
        top: 0;
        left: 0;
        background: linear-gradient(180deg, #f5c6cb 0%, #f5b7be 100%);
        border-radius: 8px 8px 0 0;
        z-index: 2;
        box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
        border-bottom: 2px solid rgba(212, 144, 153, 0.3);
    }

    /* Línea divisoria del sobre */
    .envelope-body::after {
        content: '';
        position: absolute;
        width: 100%;
        height: 2px;
        background: rgba(212, 144, 153, 0.3);
        top: 40%;
        left: 0;
    }

    .envelope.opening .envelope-flap {
        transform: rotateX(-180deg);
        transition: transform 0.8s ease;
        transform-origin: top center;
    }

    /* Corazón en el centro */
    .heart-center {
        position: absolute;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
        font-size: 35px;
        z-index: 3;
        animation: heartPulse 2s infinite ease-in-out;
        transition: opacity 0.5s ease;
    }

    @keyframes heartPulse {
        0%, 100% { transform: translate(-50%, -50%) scale(1); }
        50% { transform: translate(-50%, -50%) scale(1.1); }
    }

    .envelope.opening .heart-center {
        opacity: 0;
    }

    /* Carta */
    .letter {
        position: absolute;
        width: 90%;
        max-width: 420px;
        min-height: 500px;
        background: linear-gradient(145deg, #fde8e9 0%, #f5d5d8 100%);
        border-radius: 15px;
        box-shadow: 0 20px 60px rgba(0, 0, 0, 0.5);
        padding: 50px 35px;
        opacity: 0;
        transform: translateY(100px) scale(0.8);
        pointer-events: none;
        border: 3px solid #8b2942;
        position: relative;
        overflow: hidden;
    }

    .letter::before {
        content: '';
        position: absolute;
        top: 0;
        left: 0;
        right: 0;
        bottom: 0;
        border: 15px solid transparent;
        border-image: repeating-linear-gradient(
            45deg,
            #8b2942 0px,
            #8b2942 10px,
            transparent 10px,
            transparent 20px,
            #d4979c 20px,
            #d4979c 30px,
            transparent 30px,
            transparent 40px
        ) 15;
        pointer-events: none;
        border-radius: 15px;
    }

    .letter.show {
        opacity: 1;
        transform: translateY(0) scale(1);
        pointer-events: all;
        animation: letterAppear 0.8s ease forwards;
    }

    @keyframes letterAppear {
        0% {
            opacity: 0;
            transform: translateY(100px) scale(0.8) rotateZ(-5deg);
        }
        100% {
            opacity: 1;
            transform: translateY(0) scale(1) rotateZ(0deg);
        }
    }

    .letter-content {
        position: relative;
        z-index: 2;
    }

    .letter h1 {
        font-family: 'Cormorant Garamond', serif;
        font-size: 48px;
        font-style: italic;
        color: #8b2942;
        text-align: center;
        margin-bottom: 30px;
        text-shadow: 2px 2px 4px rgba(139, 41, 66, 0.1);
    }

    .letter p {
        font-family: 'Quicksand', sans-serif;
        font-size: 24px;
        color: #6d2235;
        text-align: center;
        line-height: 1.6;
        margin-bottom: 40px;
    }

    .buttons {
        display: flex;
        gap: 15px;
        justify-content: center;
        flex-wrap: wrap;
    }

    .btn {
        font-family: 'Quicksand', sans-serif;
        font-weight: 500;
        padding: 15px 40px;
        border: none;
        border-radius: 50px;
        font-size: 20px;
        cursor: pointer;
        transition: all 0.4s ease;
        box-shadow: 0 5px 15px rgba(0, 0, 0, 0.3);
        text-transform: uppercase;
        letter-spacing: 1px;
    }

    .btn-yes {
        background: linear-gradient(135deg, #4CAF50 0%, #45a049 100%);
        color: white;
    }

    .btn-yes:hover {
        transform: translateY(-3px);
        box-shadow: 0 8px 25px rgba(76, 175, 80, 0.4);
    }

    .btn-yes.bigger {
        padding: 20px 60px;
        font-size: 26px;
        animation: pulse 1s ease-in-out;
    }

    .btn-no {
        background: linear-gradient(135deg, #f44336 0%, #da190b 100%);
        color: white;
    }

    .btn-no:hover {
        transform: translateY(-3px);
        box-shadow: 0 8px 25px rgba(244, 67, 54, 0.4);
    }

    .btn-no.smaller {
        padding: 10px 25px;
        font-size: 14px;
    }

    @keyframes pulse {
        0%, 100% { transform: scale(1); }
        50% { transform: scale(1.05); }
    }

    /* Respuesta */
    .response {
        position: fixed;
        width: 100%;
        height: 100%;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        opacity: 0;
        pointer-events: none;
        transition: opacity 0.5s ease;
        background: rgba(10, 14, 39, 0.95);
        z-index: 100;
        padding: 20px;
        top: 0;
        left: 0;
        cursor: pointer;
    }

    .response.show {
        opacity: 1;
        pointer-events: all;
    }

    .response h2 {
        font-family: 'Cormorant Garamond', serif;
        font-style: italic;
        font-size: 52px;
        color: #fef9e7;
        text-align: center;
        margin-bottom: 20px;
        animation: heartbeat 1.5s infinite ease-in-out;
        padding: 0 20px;
    }

    .response p {
        font-family: 'Quicksand', sans-serif;
        font-size: 24px;
        color: #f5d5d8;
        text-align: center;
        max-width: 90%;
        padding: 0 20px;
        line-height: 1.6;
    }

    .click-hint {
        font-family: 'Quicksand', sans-serif;
        font-size: 16px;
        color: rgba(255, 255, 255, 0.6);
        margin-top: 30px;
        animation: blink 2s infinite;
    }

    @keyframes blink {
        0%, 50%, 100% { opacity: 0.6; }
        25%, 75% { opacity: 1; }
    }

    /* Rosa */
    .rose {
        font-size: 120px;
        margin-top: 30px;
        animation: roseGrow 1s ease-out forwards;
        opacity: 0;
        display: none;
    }

    @keyframes roseGrow {
        0% {
            opacity: 0;
            transform: scale(0) rotate(-180deg);
        }
        60% {
            transform: scale(1.2) rotate(10deg);
        }
        100% {
            opacity: 1;
            transform: scale(1) rotate(0deg);
        }
    }

    /* Segunda carta - Poema */
    .poem-letter {
        position: fixed;
        width: 90%;
        max-width: 500px;
        max-height: 85vh;
        background: linear-gradient(145deg, #fde8e9 0%, #f5d5d8 100%);
        border-radius: 20px;
        box-shadow: 0 20px 60px rgba(0, 0, 0, 0.5);
        padding: 50px 40px;
        opacity: 0;
        transform: scale(0.8);
        pointer-events: none;
        border: 3px solid #8b2942;
        position: relative;
        overflow-y: auto;
        z-index: 150;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%) scale(0.8);
        transition: all 0.5s ease;
    }

    .poem-letter.show {
        opacity: 1;
        transform: translate(-50%, -50%) scale(1);
        pointer-events: all;
    }

    .poem-letter::before {
        content: '';
        position: absolute;
        top: 10px;
        left: 10px;
        right: 10px;
        bottom: 10px;
        border: 12px solid transparent;
        border-image: repeating-linear-gradient(
            45deg,
            #8b2942 0px,
            #8b2942 8px,
            transparent 8px,
            transparent 16px,
            #d4979c 16px,
            #d4979c 24px,
            transparent 24px,
            transparent 32px
        ) 12;
        pointer-events: none;
        border-radius: 15px;
    }

    .poem-content {
        position: relative;
        z-index: 2;
        text-align: center;
        color: #6d2235;
        line-height: 2;
    }

    .poem-title {
        font-size: 28px;
        margin-bottom: 25px;
        font-weight: 500;
    }

    .poem-text {
        font-size: 18px;
        white-space: pre-line;
        margin-bottom: 30px;
    }

    .poem-footer {
        font-family: 'Quicksand', sans-serif;
        font-size: 16px;
        font-style: italic;
        margin-top: 30px;
        padding-top: 20px;
        border-top: 2px solid rgba(139, 41, 66, 0.3);
        color: #8b2942;
    }

    /* Botón final Te Amo Dulce */
    .final-button {
        display: block;
        margin: 30px auto 20px;
        padding: 18px 50px;
        background: linear-gradient(135deg, #8b2942 0%, #6d2235 100%);
        color: white;
        border: none;
        border-radius: 50px;
        font-family: 'Cormorant Garamond', serif;
        font-size: 24px;
        font-style: italic;
        font-weight: 600;
        cursor: pointer;
        box-shadow: 0 8px 20px rgba(139, 41, 66, 0.4);
        transition: all 0.3s ease;
        position: relative;
        overflow: hidden;
    }

    .final-button::before {
        content: '💕';
        position: absolute;
        left: 15px;
        font-size: 22px;
    }

    .final-button::after {
        content: '💕';
        position: absolute;
        right: 15px;
        font-size: 22px;
    }

    .final-button:hover {
        transform: translateY(-3px) scale(1.05);
        box-shadow: 0 12px 30px rgba(139, 41, 66, 0.6);
    }

    .final-button:active {
        transform: translateY(-1px) scale(1.02);
    }

    /* Pantalla negra final */
    .black-screen {
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background: #000;
        z-index: 300;
        opacity: 0;
        pointer-events: none;
        transition: opacity 2s ease;
        display: flex;
        justify-content: center;
        align-items: center;
    }

    .black-screen.show {
        opacity: 1;
        pointer-events: all;
    }

    /* Yin Yang girando */
    .yin-yang {
        width: 200px;
        height: 200px;
        position: relative;
        opacity: 0;
        transform: scale(0);
        transition: all 1s ease;
        background: #fff;
        border-radius: 50%;
        box-shadow: 0 0 40px rgba(255, 255, 255, 0.3);
    }

    .black-screen.show .yin-yang {
        opacity: 1;
        transform: scale(1);
        transition-delay: 2s;
        animation: spin 4s linear infinite;
    }

    @keyframes spin {
        0% {
            transform: rotate(0deg) scale(1);
        }
        100% {
            transform: rotate(360deg) scale(1);
        }
    }

    /* Lado negro del yin yang */
    .yin-yang::before {
        content: '';
        position: absolute;
        top: 0;
        right: 0;
        width: 50%;
        height: 100%;
        background: #000;
        border-radius: 0 100% 100% 0 / 0 50% 50% 0;
    }

    /* Círculo superior blanco */
    .yin-yang::after {
        content: '';
        position: absolute;
        top: 0;
        left: 50%;
        transform: translateX(-50%);
        width: 50%;
        height: 50%;
        background: #fff;
        border-radius: 50%;
        border: 25px solid #000;
        box-sizing: border-box;
    }

    /* Círculo inferior negro */
    .yin-dot-white {
        position: absolute;
        bottom: 0;
        left: 50%;
        transform: translateX(-50%);
        width: 50%;
        height: 50%;
        background: #000;
        border-radius: 50%;
        border: 25px solid #fff;
        box-sizing: border-box;
    }

    /* Punto blanco en la parte negra */
    .yin-dot-white::after {
        content: '';
        position: absolute;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
        width: 15%;
        height: 15%;
        background: #fff;
        border-radius: 50%;
    }

    /* Punto negro en la parte blanca */
    .yin-dot-black {
        position: absolute;
        top: 25%;
        left: 50%;
        transform: translate(-50%, -50%);
        width: 15%;
        height: 15%;
        background: #000;
        border-radius: 50%;
        z-index: 10;
    }

    .yin-dot-black::after {
        display: none;
    }

    /* Responsive para yin yang */
    @media (max-width: 768px) {
        .yin-yang {
            width: 150px;
            height: 150px;
        }
    }

    @media (max-width: 480px) {
        .yin-yang {
            width: 120px;
            height: 120px;
        }
    }

    @keyframes roseGrow {
        0% {
            opacity: 0;
            transform: scale(0) rotate(-180deg);
        }
        60% {
            transform: scale(1.2) rotate(10deg);
        }
        100% {
            opacity: 1;
            transform: scale(1) rotate(0deg);
        }
    }

    /* Mensaje de error */
    .error-message {
        display: none;
        position: fixed;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
        background: rgba(244, 67, 54, 0.95);
        color: white;
        padding: 30px 40px;
        border-radius: 15px;
        font-family: 'Quicksand', sans-serif;
        font-size: 20px;
        text-align: center;
        z-index: 150;
        box-shadow: 0 10px 40px rgba(0, 0, 0, 0.5);
        animation: errorShake 0.5s ease;
        max-width: 90%;
    }

    .error-message.show {
        display: block;
    }

    @keyframes errorShake {
        0%, 100% { transform: translate(-50%, -50%) rotate(0deg); }
        25% { transform: translate(-50%, -50%) rotate(-5deg); }
        75% { transform: translate(-50%, -50%) rotate(5deg); }
    }

    @keyframes heartbeat {
        0%, 100% { transform: scale(1); }
        25% { transform: scale(1.05); }
        50% { transform: scale(1); }
        75% { transform: scale(1.05); }
    }

    /* Corazones flotantes */
    .floating-heart {
        position: fixed;
        top: -50px;
        font-size: 40px;
        z-index: 200;
        pointer-events: none;
        animation: fallDown 4s ease-in forwards;
        filter: drop-shadow(0 0 8px rgba(255, 255, 255, 0.5));
    }

    @keyframes fallDown {
        0% {
            transform: translateY(0) rotate(0deg);
            opacity: 0;
        }
        10% {
            opacity: 1;
        }
        90% {
            opacity: 1;
        }
        100% {
            transform: translateY(calc(100vh + 100px)) rotate(360deg);
            opacity: 0;
        }
    }

    /* Responsive */
    @media (max-width: 768px) {
        .moon {
            width: 70px;
            height: 70px;
            top: 30px;
            right: 20px;
        }

        .top-text {
            font-size: 20px;
            margin-bottom: 20px;
        }

        .envelope {
            width: 85%;
            max-width: 280px;
            height: 180px;
        }

        .heart-center {
            font-size: 30px;
        }

        .letter {
            width: 90%;
            max-width: 350px;
            padding: 40px 30px;
            min-height: auto;
        }

        .letter h1 {
            font-size: 36px;
        }

        .letter p {
            font-size: 18px;
        }

        .btn {
            padding: 12px 30px;
            font-size: 18px;
        }

        .btn-yes.bigger {
            padding: 16px 45px;
            font-size: 22px;
        }

        .btn-no.smaller {
            padding: 8px 20px;
            font-size: 12px;
        }

        .response h2 {
            font-size: 40px;
        }

        .response p {
            font-size: 20px;
        }

        .rose {
            font-size: 90px;
        }

        .error-message {
            font-size: 18px;
            padding: 25px 30px;
        }

        .poem-letter {
            width: 92%;
            padding: 40px 35px;
            max-height: 80vh;
        }

        .poem-title {
            font-size: 24px;
        }

        .poem-text {
            font-size: 16px;
            line-height: 1.8;
        }

        .poem-footer {
            font-size: 14px;
        }

        .final-button {
            font-size: 20px;
            padding: 15px 40px;
        }

        .final-button::before,
        .final-button::after {
            font-size: 18px;
        }
    }

    @media (max-width: 480px) {
        .top-text {
            font-size: 18px;
        }

        .letter h1 {
            font-size: 32px;
        }

        .letter p {
            font-size: 16px;
        }

        .response h2 {
            font-size: 36px;
        }

        .response p {
            font-size: 18px;
        }

        .poem-title {
            font-size: 22px;
        }

        .poem-text {
            font-size: 15px;
        }
    }
</style>
```

</head>
<body>
    <!-- Estrellas -->
    <div class="stars" id="stars"></div>

```
<!-- Luna -->
<div class="moon"></div>

<!-- Contenedor principal -->
<div class="container">
    <!-- Texto superior -->
    <div class="top-text">De parte de tu novio ingeniero 🫶</div>
    
    <!-- Sobre -->
    <div class="envelope" id="envelope">
        <div class="envelope-back"></div>
        <div class="envelope-body"></div>
        <div class="heart-center">❤️</div>
        <div class="envelope-flap"></div>
    </div>

    <!-- Carta -->
    <div class="letter" id="letter">
        <div class="letter-content">
            <h1>¿Quieres ser mi San Valentín?</h1>
            <p>Esta noche especial, bajo esta luna brillante, quiero preguntarte algo que mi corazón anhela...</p>
            <div class="buttons">
                <button class="btn btn-yes" onclick="responder('si')">Sí 💚</button>
                <button class="btn btn-no" onclick="responder('no')">No ❤️</button>
            </div>
        </div>
    </div>
</div>

<!-- Respuesta -->
<div class="response" id="response" onclick="mostrarPoema()">
    <h2 id="responseTitle"></h2>
    <p id="responseText"></p>
    <div class="rose" id="rose">🌹</div>
    <p class="click-hint" id="clickHint">Toca la pantalla para continuar...</p>
</div>

<!-- Mensaje de error -->
<div class="error-message" id="errorMessage">
    <h3 style="margin: 0 0 10px 0; font-size: 28px;">ERROR 404</h3>
    <p style="margin: 0;">No se cargó tu respuesta.<br>Inténtalo de nuevo.</p>
</div>

<!-- Segunda carta - Poema -->
<div class="poem-letter" id="poemLetter">
    <div class="poem-content">
        <div class="poem-title">🌸 𝓟𝓪𝓻𝓪 𝓓𝓾𝓵𝓬𝓮 🌸</div>
        <div class="poem-text">𝓓𝓾𝓵𝓬𝓮 𝓷𝓲ñ𝓪 𝓶í𝓪 💕,
```

𝓹𝓻𝓸𝓶𝓮𝓽𝓸 𝓺𝓾𝓮𝓭𝓪𝓻𝓶𝓮 🤍
𝓬𝓾𝓪𝓷𝓭𝓸 𝓮𝓵 𝓶𝓾𝓷𝓭𝓸 𝓽𝓲𝓮𝓶𝓫𝓵𝓮 🌪️
𝔂 𝓬𝓾𝓪𝓷𝓭𝓸 𝓽𝓸𝓭𝓸 𝓬𝓪𝓵𝓶𝓮 🌿

𝓜𝓲 𝓵𝓾𝓷𝓪 🌖 𝓬𝓾𝓪𝓻𝓽𝓸 𝓶𝓮𝓷𝓰𝓾𝓪𝓷𝓽𝓮,
𝓪 𝓿𝓮𝓬𝓮𝓼 𝓼𝓾𝓪𝓿𝓮 ✨, 𝓪 𝓿𝓮𝓬𝓮𝓼 𝓱𝓮𝓻𝓲𝓭𝓪 💔,
𝓹𝓮𝓻𝓸 𝓼𝓲𝓮𝓶𝓹𝓻𝓮 𝓫𝓻𝓲𝓵𝓵𝓪𝓷𝓽𝓮 🌟
𝓲𝓵𝓾𝓶𝓲𝓷𝓪𝓷𝓭𝓸 𝓶𝓲 𝓿𝓲𝓭𝓪 🕯️

𝓜𝓲 𝓓𝓾𝓵𝓬𝓮 𝓟𝓻𝓲𝓷𝓬𝓮𝓼𝓪 👑,
𝓬𝓸𝓻𝓪𝔃ó𝓷 𝓿𝓪𝓵𝓲𝓮𝓷𝓽𝓮 💖 𝔂 𝓼𝓲𝓷𝓬𝓮𝓻𝓸 🌷,
𝓼𝓲 𝓽𝓻𝓸𝓹𝓲𝓮𝔃𝓪𝓼, 𝓪𝓺𝓾í 𝓮𝓼𝓽𝓪𝓻é 🤲
𝓼𝓲 𝓼𝓸𝓷𝓻í𝓮𝓼 😊, 𝓽𝓪𝓶𝓫𝓲é𝓷 𝓵𝓸 𝓺𝓾𝓲𝓮𝓻𝓸 💫

𝓜𝓲𝓪𝓾𝓶𝓸𝓻 🐾💞,
𝓮𝓷 𝓬𝓪𝓭𝓪 𝓼𝓲𝓵𝓮𝓷𝓬𝓲𝓸 𝓽𝓮 𝓷𝓸𝓶𝓫𝓻𝓸 🤍,
𝓮𝓷 𝓬𝓪𝓭𝓪 𝓪𝓫𝓻𝓪𝔃𝓸 𝓽𝓮 𝓼𝓸𝓼𝓽𝓮𝓷𝓰𝓸 🤗,
𝓮𝓷 𝓬𝓪𝓭𝓪 𝓶𝓲𝓮𝓭𝓸 𝓽𝓮 𝓪𝓬𝓸𝓶𝓹𝓪ñ𝓸 🌙

𝓜𝓲 𝓓𝓾𝓵𝓬𝓮 𝓒𝓱𝓸𝓬𝓸𝓵𝓪𝓽𝓮 𝓐𝓶𝓪𝓻𝓰𝓸 🍫🖤,
𝓶𝓮𝔃𝓬𝓵𝓪 𝓹𝓮𝓻𝓯𝓮𝓬𝓽𝓪 𝓭𝓮 𝓵𝓾𝔃 ✨ 𝔂 𝓭𝓸𝓵𝓸𝓻 🌑,
𝓹𝓻𝓸𝓶𝓮𝓽𝓸 𝓮𝓼𝓽𝓪𝓻 𝓪 𝓽𝓾 𝓵𝓪𝓭𝓸 🫶
𝓮𝓷 𝓵𝓪 𝓻𝓲𝓼𝓪 😄, 𝓮𝓷 𝓵𝓪 𝓷𝓸𝓬𝓱𝓮 🌌, 𝓮𝓷 𝓮𝓵 𝓪𝓶𝓸𝓻 ❤️

𝓢𝓲𝓮𝓶𝓹𝓻𝓮 𝓪𝓺𝓾í ♾️,
𝓼𝓲𝓷 𝓬𝓸𝓷𝓭𝓲𝓬𝓲𝓸𝓷𝓮𝓼 🚫 𝓷𝓲 𝓯𝓲𝓷𝓪𝓵𝓮𝓼 🔒,
𝓹𝓸𝓻𝓺𝓾𝓮 𝓮𝓵𝓮𝓰𝓲𝓻𝓽𝓮 𝓬𝓪𝓭𝓪 𝓭í𝓪 🌅
𝓮𝓼 𝓶𝓲 𝓹𝓻𝓸𝓶𝓮𝓼𝓪 𝓶á𝓼 𝓻𝓮𝓪𝓵 💍💖</div>
<div class="poem-footer">Hoy te elegí como mi San Valentín 💝<br>pero eres mucho más que eso para mí</div>

```
        <button class="final-button" onclick="finalizar()">Te Amo Dulce</button>
    </div>
</div>

<!-- Pantalla negra final -->
<div class="black-screen" id="blackScreen">
    <div class="yin-yang">
        <div class="yin-dot-white"></div>
        <div class="yin-dot-black"></div>
    </div>
</div>

<script>
    // Crear estrellas
    const starsContainer = document.getElementById('stars');
    for (let i = 0; i < 150; i++) {
        const star = document.createElement('div');
        star.className = 'star';
        star.style.left = Math.random() * 100 + '%';
        star.style.top = Math.random() * 100 + '%';
        star.style.animationDelay = Math.random() * 3 + 's';
        starsContainer.appendChild(star);
    }

    // Crear y reproducir música de fondo romántica
    let backgroundMusic = null;
    let musicContext = null;
    
    function createBackgroundMusic() {
        try {
            musicContext = new (window.AudioContext || window.webkitAudioContext)();
            
            // Melodía romántica suave (notas de "Clair de Lune" simplificada)
            const romanticMelody = [
                // Frase 1
                {freq: 523.25, time: 0, duration: 0.8, volume: 0.08},      // C5
                {freq: 587.33, time: 0.9, duration: 0.8, volume: 0.08},    // D5
                {freq: 659.25, time: 1.8, duration: 1.2, volume: 0.1},     // E5
                {freq: 523.25, time: 3.1, duration: 0.6, volume: 0.08},    // C5
                
                // Frase 2
                {freq: 493.88, time: 3.8, duration: 0.8, volume: 0.08},    // B4
                {freq: 440.00, time: 4.7, duration: 0.8, volume: 0.08},    // A4
                {freq: 392.00, time: 5.6, duration: 1.2, volume: 0.1},     // G4
                {freq: 493.88, time: 6.9, duration: 0.6, volume: 0.08},    // B4
                
                // Frase 3
                {freq: 523.25, time: 7.6, duration: 0.8, volume: 0.08},    // C5
                {freq: 587.33, time: 8.5, duration: 0.8, volume: 0.08},    // D5
                {freq: 659.25, time: 9.4, duration: 1.6, volume: 0.1},     // E5
                
                // Final suave
                {freq: 523.25, time: 11.1, duration: 2.0, volume: 0.09},   // C5
            ];
            
            function playNote(frequency, startTime, duration, volume) {
                const now = musicContext.currentTime;
                const oscillator = musicContext.createOscillator();
                const gainNode = musicContext.createGain();
                
                oscillator.connect(gainNode);
                gainNode.connect(musicContext.destination);
                
                oscillator.frequency.value = frequency;
                oscillator.type = 'sine';
                
                gainNode.gain.setValueAtTime(0, now + startTime);
                gainNode.gain.linearRampToValueAtTime(volume, now + startTime + 0.1);
                gainNode.gain.setValueAtTime(volume, now + startTime + duration - 0.2);
                gainNode.gain.linearRampToValueAtTime(0.001, now + startTime + duration);
                
                oscillator.start(now + startTime);
                oscillator.stop(now + startTime + duration);
            }
            
            function playMelody() {
                if (musicContext.state === 'suspended') {
                    musicContext.resume();
                }
                
                romanticMelody.forEach(note => {
                    playNote(note.freq, note.time, note.duration, note.volume);
                });
                
                // Repetir la melodía cada 14 segundos
                setTimeout(playMelody, 14000);
            }
            
            playMelody();
            
        } catch (e) {
            console.log('Música de fondo no disponible:', e);
        }
    }
    
    // Iniciar música al interactuar con la página
    function initMusic() {
        if (!backgroundMusic && !musicContext) {
            createBackgroundMusic();
            backgroundMusic = true;
        }
    }
    
    // Iniciar música al hacer clic en cualquier parte
    document.addEventListener('click', initMusic, { once: true });
    
    // También intentar iniciar al cargar (algunos navegadores lo permiten)
    window.addEventListener('load', () => {
        setTimeout(initMusic, 100);
    });

    // Abrir sobre
    const envelope = document.getElementById('envelope');
    const letter = document.getElementById('letter');

    envelope.addEventListener('click', function() {
        initMusic(); // Asegurar que la música comience
        envelope.classList.add('opening');
        setTimeout(() => {
            envelope.style.opacity = '0';
            envelope.style.pointerEvents = 'none';
            letter.classList.add('show');
        }, 800);
    });

    // Crear sonido de celebración con Web Audio API
    function playCelebrationSound() {
        try {
            const audioContext = new (window.AudioContext || window.webkitAudioContext)();
            const now = audioContext.currentTime;
            
            // Función para crear un tono
            function playTone(frequency, startTime, duration, volume = 0.15) {
                const oscillator = audioContext.createOscillator();
                const gainNode = audioContext.createGain();
                
                oscillator.connect(gainNode);
                gainNode.connect(audioContext.destination);
                
                oscillator.frequency.value = frequency;
                oscillator.type = 'sine';
                
                gainNode.gain.setValueAtTime(volume, now + startTime);
                gainNode.gain.exponentialRampToValueAtTime(0.001, now + startTime + duration);
                
                oscillator.start(now + startTime);
                oscillator.stop(now + startTime + duration);
            }
            
            // Secuencia de celebración (notas alegres más cortas y pegajosas)
            playTone(523.25, 0, 0.2);      // C5
            playTone(659.25, 0.15, 0.2);   // E5
            playTone(783.99, 0.3, 0.2);    // G5
            playTone(1046.50, 0.45, 0.4);  // C6
            playTone(659.25, 0.7, 0.15);   // E5
            playTone(783.99, 0.85, 0.15);  // G5
            playTone(1046.50, 1.0, 0.5);   // C6
            
        } catch (e) {
            console.log('Audio no soportado:', e);
        }
    }

    // Responder
    function responder(respuesta) {
        const response = document.getElementById('response');
        const responseTitle = document.getElementById('responseTitle');
        const responseText = document.getElementById('responseText');
        const roseElement = document.getElementById('rose');
        const errorMessage = document.getElementById('errorMessage');
        const btnYes = document.querySelector('.btn-yes');
        const btnNo = document.querySelector('.btn-no');

        if (respuesta === 'si') {
            // Primero ocultar la carta
            const letter = document.getElementById('letter');
            letter.style.opacity = '0';
            letter.style.transform = 'scale(0.8)';
            
            setTimeout(() => {
                letter.style.display = 'none';
            }, 500);
            
            // Reproducir sonido de celebración
            setTimeout(() => {
                playCelebrationSound();
            }, 600);
            
            // Crear 40 corazones en cascada de diferentes tipos
            const heartTypes = ['❤️', '💕', '💖', '💗', '💓', '💝', '💞', '💘', '🩷', '🧡', '💙', '💚', '💛', '🤍', '🖤'];
            
            // Iniciar cascada después de que se oculte la carta
            setTimeout(() => {
                for (let i = 0; i < 40; i++) {
                    setTimeout(() => {
                        const heart = document.createElement('div');
                        heart.className = 'floating-heart';
                        heart.textContent = heartTypes[Math.floor(Math.random() * heartTypes.length)];
                        
                        // Posición aleatoria
                        heart.style.left = (Math.random() * 90 + 5) + '%';
                        
                        // Tamaño aleatorio
                        const size = 30 + Math.random() * 35;
                        heart.style.fontSize = size + 'px';
                        
                        // Duración aleatoria
                        const duration = 3 + Math.random() * 2;
                        heart.style.animationDuration = duration + 's';
                        
                        document.body.appendChild(heart);
                        
                        // Remover después de la animación
                        setTimeout(() => {
                            if (heart.parentNode) {
                                heart.remove();
                            }
                        }, (duration + 0.5) * 1000);
                    }, i * 100); // Un corazón cada 100ms
                }
            }, 700);
            
            // Mostrar el letrero después de 5 segundos
            setTimeout(() => {
                responseTitle.textContent = '¡Sabía que dirías que sí! 💕';
                responseText.textContent = '¡Has hecho de esta noche la más especial de todas! Mi corazón está lleno de felicidad. ¡Feliz San Valentín! ✨';
                response.classList.add('show');
                
                // Mostrar la rosa después de 1 segundo más
                setTimeout(() => {
                    roseElement.style.display = 'block';
                }, 1000);
            }, 5000);
            
        } else {
            // Mostrar mensaje de error
            errorMessage.classList.add('show');
            
            // Ocultar mensaje después de 2 segundos
            setTimeout(() => {
                errorMessage.classList.remove('show');
            }, 2000);
            
            // Hacer el botón Sí más grande y el No más pequeño
            btnYes.classList.add('bigger');
            btnNo.classList.add('smaller');
        }
    }

    // Mostrar el poema al hacer clic en la respuesta
    function mostrarPoema() {
        const poemLetter = document.getElementById('poemLetter');
        const clickHint = document.getElementById('clickHint');
        
        // Solo mostrar si la rosa ya apareció
        if (document.getElementById('rose').style.display === 'block') {
            clickHint.style.display = 'none';
            poemLetter.classList.add('show');
        }
    }

    // Función final - Pantalla negra
    function finalizar() {
        const blackScreen = document.getElementById('blackScreen');
        blackScreen.classList.add('show');
    }
</script>
```

</body>
</html>