<html lang="uk" class="dark">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Епічне Очікування ДА!</title>
    <!-- Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
    <script>
        tailwind.config = {
            darkMode: 'class',
            theme: {
                extend: {
                    animation: {
                        'pulse-slow': 'pulse 3s cubic-bezier(0.4, 0, 0.6, 1) infinite',
                        'float': 'float 4s ease-in-out infinite',
                        'spin-slow': 'spin 15s linear infinite',
                        'bounce-subtle': 'bounceSubtle 2s infinite',
                        'rainbow': 'rainbow 6s linear infinite',
                    },
                    keyframes: {
                        float: {
                            '0%, 100%': { transform: 'translateY(0px)' },
                            '50%': { transform: 'translateY(-15px)' },
                        },
                        bounceSubtle: {
                            '0%, 100%': { transform: 'translateY(-5%)', animationTimingFunction: 'cubic-bezier(0.8,0,1,1)' },
                            '50%': { transform: 'none', animationTimingFunction: 'cubic-bezier(0,0,0.2,1)' },
                        },
                        rainbow: {
                            '0%': { filter: 'hue-rotate(0deg)' },
                            '100%': { filter: 'hue-rotate(360deg)' },
                        }
                    }
                }
            }
        }
    </script>
    <!-- Google Fonts: Inter & Fredoka for playful headers -->
    <link href="https://fonts.googleapis.com/css2?family=Fredoka:wght@400;600;700&family=Inter:wght@400;500;700&display=swap" rel="stylesheet">
    <!-- FontAwesome for icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <!-- Tone.js for audio synthesis -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/tone/14.8.49/Tone.js"></script>
    <!-- Canvas Confetti -->
    <script src="https://cdn.jsdelivr.net/npm/canvas-confetti@1.6.0/dist/confetti.browser.min.js"></script>
    
    <style>
        body {
            font-family: 'Inter', sans-serif;
            user-select: none;
            overflow: hidden;
        }
        .font-fun {
            font-family: 'Fredoka', sans-serif;
        }
        .text-glow {
            text-shadow: 0 0 20px rgba(236, 72, 153, 0.6), 0 0 40px rgba(168, 85, 247, 0.4);
        }
        .rainbow-text {
            background: linear-gradient(to right, #ff0000, #ff7f00, #ffff00, #00ff00, #0000ff, #4b0082, #8b00ff);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-size: 400% 400%;
            animation: rainbowBG 6s ease infinite;
        }
        @keyframes rainbowBG {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }
        .glass-panel {
            background: rgba(17, 24, 39, 0.75);
            backdrop-filter: blur(16px);
            border: 1px solid rgba(255, 255, 255, 0.1);
        }
    </style>
</head>
<body class="bg-slate-950 text-slate-100 h-screen w-screen flex flex-col justify-between relative">

    <!-- Background Ambient Glows & Floating Stars -->
    <div class="absolute inset-0 overflow-hidden pointer-events-none z-0">
        <div class="absolute -top-40 -left-40 w-96 h-96 bg-purple-600/20 rounded-full blur-3xl animate-pulse-slow"></div>
        <div class="absolute top-1/2 -right-40 w-96 h-96 bg-pink-600/20 rounded-full blur-3xl animate-pulse-slow" style="animation-delay: 1s;"></div>
        <div class="absolute -bottom-40 left-1/3 w-96 h-96 bg-blue-600/20 rounded-full blur-3xl animate-pulse-slow" style="animation-delay: 2s;"></div>
        <canvas id="starCanvas" class="absolute inset-0 w-full h-full"></canvas>
    </div>

    <!-- Top Bar -->
    <header class="relative z-20 w-full p-4 flex justify-between items-center max-w-6xl mx-auto">
        <div class="flex items-center space-x-2">
            <span class="w-3 h-3 bg-pink-500 rounded-full animate-ping"></span>
            <h1 class="font-fun text-xl font-bold tracking-wider text-transparent bg-clip-text bg-gradient-to-r from-pink-400 to-purple-400">EPIC WAIT v2.0</h1>
        </div>
        <div class="flex items-center space-x-3">
            <button id="soundToggle" onclick="toggleAudio()" class="glass-panel px-4 py-2 rounded-xl text-sm font-medium hover:bg-slate-800 transition flex items-center space-x-2 shadow-lg">
                <i id="soundIcon" class="fa-solid fa-volume-xmark text-pink-400"></i>
                <span id="soundText">Звук: Вимк</span>
            </button>
            <button onclick="fastForwardForTesting()" class="glass-panel px-3 py-2 rounded-xl text-xs text-slate-400 hover:text-white hover:bg-slate-800 transition" title="Тест режим: прискорити">
                <i class="fa-solid fa-forward-fast"></i> Швидкий тест
            </button>
        </div>
    </header>

    <!-- Main Content Area -->
    <main class="relative z-10 flex-1 flex flex-col items-center justify-center px-4 max-w-2xl mx-auto w-full text-center">

        <!-- Loading / Countdown Screen -->
        <div id="loadingScreen" class="w-full flex flex-col items-center space-y-8 transition-opacity duration-700">
            
            <!-- Animated Spinner / Portal Icon -->
            <div class="relative w-36 h-36 flex items-center justify-center">
                <div class="absolute inset-0 rounded-full border-4 border-purple-500/30 border-t-pink-500 animate-spin-slow"></div>
                <div class="absolute inset-3 rounded-full border-4 border-blue-500/20 border-b-cyan-400 animate-spin" style="animation-direction: reverse; animation-duration: 8s;"></div>
                <div class="glass-panel w-24 h-24 rounded-full flex items-center justify-center shadow-2xl animate-float">
                    <i id="portalIcon" class="fa-solid fa-hourglass-half text-3xl text-pink-400 animate-pulse"></i>
                </div>
            </div>

            <!-- Timer & Percentage Display -->
            <div class="space-y-2">
                <div class="font-fun text-6xl md:text-7xl font-bold tracking-wider text-glow" id="timerDisplay">01:00</div>
                <p class="text-xs font-mono text-purple-300 tracking-widest uppercase">Залишилося часу до одкровення</p>
            </div>

            <!-- Dynamic Quirky Message Box -->
            <div class="glass-panel w-full p-5 rounded-2xl shadow-xl min-h-[90px] flex flex-col justify-center items-center relative overflow-hidden border border-purple-500/20">
                <div class="absolute top-0 left-0 h-1 bg-gradient-to-r from-pink-500 to-purple-500 transition-all duration-300" id="messageProgress"></div>
                <p id="quirkyText" class="text-slate-200 font-medium text-base md:text-lg transition-all duration-500 transform translate-y-0 opacity-100">
                    Ініціалізація квантового очікування... Будь ласка, не кліпайте очима! 👀
                </p>
                <div class="mt-2 text-xs text-slate-400 flex items-center space-status">
                    <i class="fa-solid fa-circle-notch fa-spin text-pink-400 mr-1.5"></i>
                    <span id="subStatusText">Опрацювання емоцій... (1/60 сек)</span>
                </div>
            </div>

            <!-- Progress Bar -->
            <div class="w-full space-y-2">
                <div class="w-full bg-slate-900/80 rounded-full h-4 p-0.5 border border-slate-700/50 shadow-inner overflow-hidden">
                    <div id="progressBar" class="bg-gradient-to-r from-pink-500 via-purple-500 to-indigo-500 h-full rounded-full transition-all duration-300 w-0 shadow-lg"></div>
                </div>
                <div class="flex justify-between text-xs text-slate-400 font-mono">
                    <span id="percentText">0%</span>
                    <span>Ціль: Епічне ДА!</span>
                    <span id="timeRemainingText">60с</span>
                </div>
            </div>

        </div>

        <!-- Final Reveal Screen (Hidden initially) -->
        <div id="revealScreen" class="hidden w-full flex flex-col items-center space-y-6 transition-all duration-1000 transform scale-95 opacity-0">
            
            <div class="relative py-4">
                <div class="absolute -inset-1 bg-gradient-to-r from-pink-600 via-purple-600 to-indigo-600 rounded-3xl blur-2xl opacity-75 animate-pulse"></div>
                <div class="relative glass-panel px-8 py-10 md:px-16 md:py-14 rounded-3xl shadow-2xl border border-white/20">
                    <h2 class="font-fun text-7xl md:text-9xl font-extrabold tracking-wider rainbow-text drop-shadow-[0_10px_20px_rgba(0,0,0,0.5)] transform hover:scale-105 transition duration-300">
                        ДА!
                    </h2>
                </div>
            </div>

            <p class="text-slate-300 text-lg md:text-xl font-medium max-w-md animate-fade-in">
                Місія успішно виконана! Очікування варте кожної секунди цього галактичного шоу. ✨
            </p>

            <div class="flex flex-wrap justify-center gap-4 pt-4">
                <button onclick="restartExperience()" class="px-6 py-3 bg-gradient-to-r from-pink-500 to-purple-600 hover:from-pink-600 hover:to-purple-700 font-fun font-bold rounded-xl shadow-lg transform hover:-translate-y-0.5 transition flex items-center space-x-2">
                    <i class="fa-solid fa-rotate-right"></i>
                    <span>Пройти знову</span>
                </button>
                <button onclick="triggerMegaConfetti()" class="px-6 py-3 glass-panel hover:bg-slate-800 font-fun font-bold rounded-xl shadow-lg border border-pink-500/30 text-pink-300 hover:text-white transition flex items-center space-x-2">
                    <i class="fa-solid fa-wand-magic-sparkles"></i>
                    <span>Більше святкування!</span>
                </button>
            </div>

        </div>

    </main>

    <!-- Floating Popups Notification Container -->
    <div id="popupContainer" class="fixed bottom-6 right-6 z-30 flex flex-col space-y-3 pointer-events-none"></div>

    <!-- Footer -->
    <footer class="relative z-20 w-full p-4 text-center text-xs text-slate-500">
        Створено для найкращого настрою та епічних моментів 🚀
    </footer>

    <script>
        // --- Starry Background Canvas ---
        const starCanvas = document.getElementById('starCanvas');
        const ctx = starCanvas.getContext('2d');
        let stars = [];

        function resizeCanvas() {
            starCanvas.width = window.innerWidth;
            starCanvas.height = window.innerHeight;
            initStars();
        }

        function initStars() {
            stars = [];
            const count = Math.floor((window.innerWidth * window.innerHeight) / 3000);
            for (let i = 0; i < count; i++) {
                stars.push({
                    x: Math.random() * starCanvas.width,
                    y: Math.random() * starCanvas.height,
                    radius: Math.random() * 1.5 + 0.5,
                    alpha: Math.random(),
                    speed: Math.random() * 0.02 + 0.005
                });
            }
        }

        function drawStars() {
            ctx.clearRect(0, 0, starCanvas.width, starCanvas.height);
            ctx.fillStyle = '#ffffff';
            stars.forEach(star => {
                ctx.globalAlpha = star.alpha;
                ctx.beginPath();
                ctx.arc(star.x, star.y, star.radius, 0, Math.PI * 2);
                ctx.fill();
                star.alpha += star.speed;
                if (star.alpha > 1 || star.alpha < 0.1) {
                    star.speed = -star.speed;
                }
            });
            requestAnimationFrame(drawStars);
        }

        window.addEventListener('resize', resizeCanvas);
        resizeCanvas();
        drawStars();

        // --- Quirky Messages Array ---
        const quirkyMessages = [
            "Ініціалізація квантового очікування... Будь ласка, не кліпайте очима! 👀",
            "Завантаження терпіння 74%... Залишилося ще трохи чаклунства ✨",
            "Перевіряємо чи готовий всесвіт до такого масштабного 'ДА!' 🌌",
            "Заварюємо цифрову каву для нейронів сайту ☕",
            "Обережно! Рівень крутості цього сайту починає зашкалювати 🔥",
            "Шукаємо загублені пікселі за диваном... 🛋️",
            "Ввічливо просимо планети вишикуватися в ідеальну лінію 🪐",
            "Катаємось на віртуальних американських гірках очікування 🎢",
            "Майже готово! Залишилося здути віртуальний пил з літер 💨",
            "Ще трохи магії, і станеться дещо грандіозне! 🦄"
        ];

        // --- Popup Fun Facts / Mini elements ---
        const popupsData = [
            { icon: "fa-cat", text: "Кіт-програміст схвалює це очікування! 🐾" },
            { icon: "fa-bolt", text: "А ви знали, що секунда триває рівно одну секунду? ⚡" },
            { icon: "fa-face-grin-stars", text: "Чудовий вибір часу для завісання в інтернеті! ⭐" },
            { icon: "fa-cookie-bite", text: "Віртуальне печиво додано до вашого кешу! 🍪" },
            { icon: "fa-rocket", text: "Ракетне паливо для емоцій майже заправлене 🚀" },
            { icon: "fa-heart", text: "Ваше терпіння заслуговує на медаль! 🏆" }
        ];

        // --- Audio with Tone.js ---
        let audioInitialized = false;
        let synth, chimeSynth, backgroundLoop;

        function initAudio() {
            if (audioInitialized) return;
            try {
                Tone.start();
                synth = new Tone.Synth({
                    oscillator: { type: "triangle" },
                    envelope: { attack: 0.05, decay: 0.2, sustain: 0.2, release: 0.8 }
                }).toDestination();

                chimeSynth = new Tone.PolySynth(Tone.Synth, {
                    oscillator: { type: "sine" },
                    envelope: { attack: 0.01, decay: 0.5, sustain: 0.1, release: 1 }
                }).toDestination();

                audioInitialized = true;
                console.log("Audio initialized successfully");
            } catch (e) {
                console.log("Audio init error:", e);
            }
        }

        function toggleAudio() {
            const soundIcon = document.getElementById('soundIcon');
            const soundText = document.getElementById('soundText');
            
            if (!audioInitialized) {
                initAudio();
                soundIcon.className = "fa-solid fa-volume-high text-pink-400";
                soundText.innerText = "Звук: Увімк";
                playBeep(440);
            } else {
                if (Tone.Destination.mute) {
                    Tone.Destination.mute = false;
                    soundIcon.className = "fa-solid fa-volume-high text-pink-400";
                    soundText.innerText = "Звук: Увімк";
                } else {
                    Tone.Destination.mute = true;
                    soundIcon.className = "fa-solid fa-volume-xmark text-slate-400";
                    soundText.innerText = "Звук: Вимк";
                }
            }
        }

        function playBeep(freq = 523.25) {
            if (!audioInitialized || Tone.Destination.mute) return;
            try {
                synth.triggerAttackRelease(freq, "8n");
            } catch (e) {}
        }

        function playVictoryChords() {
            if (!audioInitialized || Tone.Destination.mute) return;
            try {
                const now = Tone.now();
                chimeSynth.triggerAttackRelease(["C4", "E4", "G4", "C5"], "2n", now);
                chimeSynth.triggerAttackRelease(["F4", "A4", "C5", "F5"], "2n", now + 0.4);
                chimeSynth.triggerAttackRelease(["G4", "B4", "D5", "G5"], "1n", now + 0.8);
            } catch (e) {}
        }

        // --- Countdown State Management ---
        const TOTAL_TIME = 60; // 60 seconds
        let timeLeft = TOTAL_TIME;
        let timerInterval = null;
        let isFinished = false;

        const timerDisplay = document.getElementById('timerDisplay');
        const progressBar = document.getElementById('progressBar');
        const percentText = document.getElementById('percentText');
        const timeRemainingText = document.getElementById('timeRemainingText');
        const quirkyText = document.getElementById('quirkyText');
        const messageProgress = document.getElementById('messageProgress');
        const subStatusText = document.getElementById('subStatusText');
        const loadingScreen = document.getElementById('loadingScreen');
        const revealScreen = document.getElementById('revealScreen');
        const portalIcon = document.getElementById('portalIcon');

        function startCountdown() {
            if (timerInterval) clearInterval(timerInterval);

            timerInterval = setInterval(() => {
                if (isFinished) return;

                timeLeft--;
                updateUI();

                // Play tick sound every 5 seconds or every second in last 10 seconds
                if (timeLeft <= 10 || timeLeft % 5 === 0) {
                    playBeep(timeLeft <= 10 ? 659.25 : 523.25);
                }

                // Change quirky message every 6 seconds
                if (timeLeft % 6 === 0) {
                    rotateQuirkyMessage();
                }

                // Trigger random fun popup at specific intervals
                if (timeLeft === 45 || timeLeft === 30 || timeLeft === 15) {
                    showRandomPopup();
                }

                if (timeLeft <= 0) {
                    clearInterval(timerInterval);
                    triggerReveal();
                }
            }, 1000);
        }

        function updateUI() {
            const elapsed = TOTAL_TIME - timeLeft;
            const percentage = Math.floor((elapsed / TOTAL_TIME) * 100);

            // Format timer MM:SS
            const minutes = String(Math.floor(timeLeft / 60)).padStart(2, '0');
            const seconds = String(timeLeft % 60).padStart(2, '0');
            timerDisplay.innerText = `${minutes}:${seconds}`;

            // Progress bar
            progressBar.style.width = `${percentage}%`;
            percentText.innerText = `${percentage}%`;
            timeRemainingText.innerText = `${timeLeft}с`;
            subStatusText.innerText = `Опрацювання емоцій... (${elapsed}/60 сек)`;
            messageProgress.style.width = `${((timeLeft % 6) / 6) * 100}%`;
        }

        let messageIndex = 0;
        function rotateQuirkyMessage() {
            messageIndex = (messageIndex + 1) % quirkyMessages.length;
            quirkyText.style.opacity = '0';
            quirkyText.style.transform = 'translateY(10px)';
            setTimeout(() => {
                quirkyText.innerText = quirkyMessages[messageIndex];
                quirkyText.style.opacity = '1';
                quirkyText.style.transform = 'translateY(0)';
            }, 300);
        }

        function showRandomPopup() {
            const randomData = popupsData[Math.floor(Math.random() * popupsData.length)];
            const container = document.getElementById('popupContainer');
            
            const popup = document.createElement('div');
            popup.className = "glass-panel px-4 py-3 rounded-2xl shadow-2xl flex items-center space-x-3 pointer-events-auto transform translate-y-10 opacity-0 transition-all duration-500 border border-pink-500/30";
            popup.innerHTML = `
                <div class="w-10 h-10 rounded-xl bg-gradient-to-tr from-pink-500 to-purple-600 flex items-center justify-center text-white shadow-md">
                    <i class="fa-solid ${randomData.icon}"></i>
                </div>
                <div class="text-left">
                    <p class="text-xs font-bold text-pink-400 uppercase tracking-wider">Цікавинка</p>
                    <p class="text-sm text-slate-200 font-medium">${randomData.text}</p>
                </div>
            `;
            
            container.appendChild(popup);

            // Animate in
            setTimeout(() => {
                popup.classList.remove('translate-y-10', 'opacity-0');
            }, 50);

            // Remove after 4 seconds
            setTimeout(() => {
                popup.classList.add('translate-y-10', 'opacity-0');
                setTimeout(() => popup.remove(), 500);
            }, 4000);
        }

        function triggerReveal() {
            isFinished = true;
            playVictoryChords();

            // Fade out loading screen
            loadingScreen.style.opacity = '0';
            setTimeout(() => {
                loadingScreen.classList.add('hidden');
                
                // Show reveal screen
                revealScreen.classList.remove('hidden');
                setTimeout(() => {
                    revealScreen.classList.remove('scale-95', 'opacity-0');
                    revealScreen.classList.add('scale-100', 'opacity-100');
                }, 50);

                // Launch epic confetti
                triggerMegaConfetti();
            }, 700);
        }

        function triggerMegaConfetti() {
            // Multi-stage confetti explosion
            const duration = 3.5 * 1000;
            const animationEnd = Date.now() + duration;
            const defaults = { startVelocity: 30, spread: 360, ticks: 60, zIndex: 1000 };

            function randomInRange(min, max) {
                return Math.random() * (max - min) + min;
            }

            const interval = setInterval(function() {
                const timeLeftConfetti = animationEnd - Date.now();

                if (timeLeftConfetti <= 0) {
                    return clearInterval(interval);
                }

                const particleCount = 50 * (timeLeftConfetti / duration);
                confetti(Object.assign({}, defaults, { particleCount, origin: { x: randomInRange(0.1, 0.3), y: Math.random() - 0.2 } }));
                confetti(Object.assign({}, defaults, { particleCount, origin: { x: randomInRange(0.7, 0.9), y: Math.random() - 0.2 } }));
            }, 250);
        }

        // Fast forward testing helper
        function fastForwardForTesting() {
            timeLeft = 3;
            // Provide a quick subtle notification popup
            const container = document.getElementById('popupContainer');
            const popup = document.createElement('div');
            popup.className = "glass-panel px-4 py-2 rounded-xl text-xs text-yellow-300 border border-yellow-500/30 shadow-lg pointer-events-auto transition-all duration-300";
            popup.innerHTML = `<i class="fa-solid fa-bolt mr-1.5"></i> Швидкий тест активовано: перехід через 3 секунди!`;
            container.appendChild(popup);
            setTimeout(() => popup.remove(), 3000);
        }

        function restartExperience() {
            isFinished = false;
            timeLeft = TOTAL_TIME;
            revealScreen.classList.remove('scale-100', 'opacity-100');
            revealScreen.classList.add('scale-95', 'opacity-0');
            setTimeout(() => {
                revealScreen.classList.add('hidden');
                loadingScreen.classList.remove('hidden');
                loadingScreen.style.opacity = '1';
                updateUI();
                startCountdown();
            }, 500);
        }

        // Initialize on load
        window.onload = function() {
            updateUI();
            startCountdown();
            // Show first popup after 5 seconds
            setTimeout(showRandomPopup, 5000);
        };
    </script>
</body>
</html>
