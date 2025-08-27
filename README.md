//first code of me
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Logo Butterfly Animation</title>
    <style>
        #logo {
            width: 150px;
            display: block;
            position: relative;
            transition: transform 2s cubic-bezier(.68,-0.55,.27,1.55);
            cursor: pointer;
        }
        #question-tab {
            background: #f0f0f0;
            padding: 10px;
            margin-bottom: 15px;
            border-radius: 8px;
            font-family: sans-serif;
            font-size: 1.1em;
        }
        @keyframes butterfly-fly {
            0%   { transform: translate(0, 0) rotate(0deg);}
            10%  { transform: translate(30px, -20px) rotate(-10deg);}
            20%  { transform: translate(60px, -40px) rotate(10deg);}
            30%  { transform: translate(90px, -60px) rotate(-10deg);}
            40%  { transform: translate(120px, -80px) rotate(10deg);}
            50%  { transform: translate(150px, -100px) rotate(-10deg);}
            60%  { transform: translate(120px, -80px) rotate(10deg);}
            70%  { transform: translate(90px, -60px) rotate(-10deg);}
            80%  { transform: translate(60px, -40px) rotate(10deg);}
            90%  { transform: translate(30px, -20px) rotate(-10deg);}
            100% { transform: translate(0, 0) rotate(0deg);}
        }
        .butterfly {
            animation: butterfly-fly 2s cubic-bezier(.68,-0.55,.27,1.55);
        }
        #input-section {
            margin: 20px 0 0 0;
            display: flex;
            flex-direction: column;
            align-items: flex-start;
            font-family: sans-serif;
        }
        #member-input {
            padding: 6px 10px;
            font-size: 1em;
            border-radius: 5px;
            border: 1px solid #ccc;
        }
        #enter-btn {
            padding: 6px 12px;
            font-size: 1em;
            border: none;
            border-radius: 5px;
            background: #4B3426;
            color: white;
            cursor: pointer;
            transition: background 0.3s;
        }
        #enter-btn:hover {
            background: #6b4a34;
        }
        #hearts {
            margin-top: 40px;
            display: none;
            align-items: center;
            justify-content: center;
            gap: 40px;
            width: 100vw;
            position: fixed;
            top: 40%;
            left: 0;
            z-index: 1000;
        }
        .heart {
            font-size: 2.5em;
            color: red;
            margin-right: 10px;
        }
        .heart-svg {
            width: 180px !important;
            height: 180px !important;
            margin-right: 30px;
            animation: heart-beat 1s infinite;
        }
        .love-text {
            font-size: 3.6em !important;
            color: #d32f2f;
            font-weight: bold;
        }
        @keyframes heart-beat {
            0%, 100% { transform: scale(1);}
            20% { transform: scale(1.15);}
            40% { transform: scale(0.95);}
            60% { transform: scale(1.1);}
            80% { transform: scale(0.98);}
        }
    </style>
</head>
<body>
    <div id="logo-container" style="display: flex; flex-direction: column; align-items: center;">
        <!-- Inline SVG logo -->
        <svg id="logo" viewBox="0 0 400 250" width="150" style="background: white; border-radius: 50%; cursor:pointer;">
            <!-- Roof -->
            <polyline points="70,110 200,30 330,110" fill="none" stroke="#4B3426" stroke-width="12" stroke-linecap="round"/>
            <!-- Left circle -->
            <circle cx="120" cy="120" r="20" fill="#E6D3A3"/>
            <!-- Right circle -->
            <circle cx="280" cy="120" r="20" fill="#4B3426"/>
            <!-- Left body -->
            <path d="M140,170 Q110,200 200,240 Q200,240 200,170 Q200,140 170,140 Q140,140 140,170 Z" fill="#E6D3A3"/>
            <!-- Right body -->
            <path d="M260,170 Q290,200 200,240 Q200,240 200,170 Q200,140 230,140 Q260,140 260,170 Z" fill="#4B3426"/>
        </svg>
        <div id="question-tab">
            What kind of THC you want bro?
        </div>
    </div>

    <div id="input-section">
        <label for="member-input">Enter your name:</label>
        <div style="display:flex; align-items:center; gap:10px; margin-top:5px;">
            <input type="text" id="member-input" autocomplete="off" />
            <button id="enter-btn">Enter</button>
        </div>
    </div>

    <div id="hearts">
        <span class="heart">❤️</span>
        <span class="heart">❤️</span>
        <span class="love-text">I love you</span>
    </div>

    <script>
    // Elements
    const logo = document.getElementById('logo');
    const memberInput = document.getElementById('member-input');
    const enterBtn = document.getElementById('enter-btn');
    const hearts = document.getElementById('hearts');

    // Allowed member names
    const members = ['ali', 'mmad', 'hosi', 'feri', 'miti', 'nazi'];

    // Replace static hearts with animated SVG
    hearts.innerHTML = `
        <svg class="heart-svg" width="60" height="60" viewBox="0 0 60 60">
            <path d="M30 52 C 10 32, 10 12, 30 20 C 50 12, 50 32, 30 52 Z" fill="red">
                <animate attributeName="d" dur="1s" repeatCount="indefinite"
                    values="M30 52 C 10 32, 10 12, 30 20 C 50 12, 50 32, 30 52 Z;
                            M30 54 C 8 34, 12 10, 30 18 C 48 10, 52 34, 30 54 Z;
                            M30 52 C 10 32, 10 12, 30 20 C 50 12, 50 32, 30 52 Z" />
            </path>
        </svg>
        <svg class="heart-svg" width="60" height="60" viewBox="0 0 60 60">
            <path d="M30 52 C 10 32, 10 12, 30 20 C 50 12, 50 32, 30 52 Z" fill="red">
                <animate attributeName="d" dur="1s" repeatCount="indefinite"
                    values="M30 52 C 10 32, 10 12, 30 20 C 50 12, 50 32, 30 52 Z;
                            M30 54 C 8 34, 12 10, 30 18 C 48 10, 52 34, 30 54 Z;
                            M30 52 C 10 32, 10 12, 30 20 C 50 12, 50 32, 30 52 Z" />
            </path>
        </svg>
        <span class="love-text">I love you</span>
    `;

    // Show love message
    function showLoveMessage() {
        const value = memberInput.value.trim().toLowerCase();
        if (members.includes(value)) {
            hearts.style.display = 'flex';
            const loveText = hearts.querySelector('.love-text');
            loveText.textContent = `I love you ${value}`;
        } else {
            hearts.style.display = 'none';
        }
    }

    // Desktop + mobile input handling
    memberInput.addEventListener('keydown', (e) => {
        if (e.key === 'Enter') showLoveMessage();
    });
    memberInput.addEventListener('change', showLoveMessage);
    enterBtn.addEventListener('click', showLoveMessage);
    memberInput.addEventListener('input', () => {
        hearts.style.display = 'none';
    });

    // Butterfly transformation
    let isButterfly = false;
    function morphToButterfly() {
        logo.innerHTML = `
            <g>
                <ellipse id="left-wing" cx="120" cy="120" rx="60" ry="30" fill="#E6D3A3" opacity="0.8"/>
                <ellipse id="right-wing" cx="280" cy="120" rx="60" ry="30" fill="#4B3426" opacity="0.8"/>
                <rect x="190" y="100" width="20" height="80" rx="10" fill="#4B3426"/>
                <circle cx="200" cy="95" r="15" fill="#E6D3A3"/>
                <path d="M200 80 Q190 70 195 90" stroke="#4B3426" stroke-width="3" fill="none"/>
                <path d="M200 80 Q210 70 205 90" stroke="#4B3426" stroke-width="3" fill="none"/>
            </g>`;
        logo.classList.add('butterfly-wings', 'butterfly');
        setTimeout(() => logo.classList.remove('butterfly'), 2000);
    }
    function morphToLogo() {
        logo.innerHTML = `
            <polyline points="70,110 200,30 330,110" fill="none" stroke="#4B3426" stroke-width="12" stroke-linecap="round"/>
            <circle cx="120" cy="120" r="20" fill="#E6D3A3"/>
            <circle cx="280" cy="120" r="20" fill="#4B3426"/>
            <path d="M140,170 Q110,200 200,240 Q200,240 200,170 Q200,140 170,140 Q140,140 140,170 Z" fill="#E6D3A3"/>
            <path d="M260,170 Q290,200 200,240 Q200,240 200,170 Q200,140 230,140 Q260,140 260,170 Z" fill="#4B3426"/>`;
        logo.classList.remove('butterfly-wings');
        logo.classList.add('butterfly');
        setTimeout(() => logo.classList.remove('butterfly'), 2000);
    }

    // Wing animation
    const butterflyStyle = document.createElement('style');
    butterflyStyle.textContent = `
        #logo.butterfly-wings #left-wing {
            transform-origin: 120px 120px;
            animation: left-wing-flap 1.2s infinite;
        }
        #logo.butterfly-wings #right-wing {
            transform-origin: 280px 120px;
            animation: right-wing-flap 1.2s infinite;
        }
        @keyframes left-wing-flap {
            0%,100% { transform: rotate(-10deg);}
            50% { transform: rotate(-40deg);}
        }
        @keyframes right-wing-flap {
            0%,100% { transform: rotate(10deg);}
            50% { transform: rotate(40deg);}
        }
    `;
    document.head.appendChild(butterflyStyle);

    // Tap or click toggle
    logo.addEventListener('click', () => {
        if (!isButterfly) {
            morphToButterfly();
            isButterfly = true;
        } else {
            morphToLogo();
            isButterfly = false;
        }
    });
    </script>
</body>
</html>
