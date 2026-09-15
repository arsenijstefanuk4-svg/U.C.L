<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>U.C.L - Официальный регламент</title>
    <style>
        :root {
            --bg-color: #0b0f19;
            --card-bg: #131b2e;
            --accent: #3b82f6;
            --red: #ef4444;
            --green: #22c55e;
            --text: #f3f4f6;
            --text-muted: #9ca3af;
            --border: #1e293b;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            background-color: var(--bg-color);
            color: var(--text);
            line-height: 1.6;
            padding-bottom: 50px;
        }

        #progress-bar {
            position: fixed;
            top: 0;
            left: 0;
            height: 4px;
            background: var(--accent);
            width: 0%;
            z-index: 1000;
            transition: width 0.1s;
        }

        #loader {
            position: fixed;
            inset: 0;
            background: var(--bg-color);
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            z-index: 9999;
            transition: opacity 0.5s ease, visibility 0.5s ease;
        }

        .spinner {
            width: 50px;
            height: 50px;
            border: 4px solid var(--border);
            border-top: 4px solid var(--accent);
            border-radius: 50%;
            animation: spin 1s linear infinite;
            margin-bottom: 15px;
        }

        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }

        header {
            text-align: center;
            padding: 60px 20px 30px;
            background: linear-gradient(to bottom, #172554, var(--bg-color));
        }

        header h1 {
            font-size: 2.5rem;
            margin-bottom: 10px;
            color: #fff;
            text-transform: uppercase;
            letter-spacing: 2px;
        }

        header p {
            color: var(--text-muted);
            font-size: 1.1rem;
        }

        .container {
            max-width: 900px;
            margin: 0 auto;
            padding: 0 20px;
        }

        .search-container {
            margin: 30px 0;
            position: relative;
        }

        #searchInput {
            width: 100%;
            padding: 15px 20px;
            background: var(--card-bg);
            border: 1px solid var(--border);
            border-radius: 8px;
            color: var(--text);
            font-size: 1rem;
            outline: none;
            transition: border-color 0.3s;
        }

        #searchInput:focus {
            border-color: var(--accent);
        }

        .arena-status {
            display: flex;
            align-items: center;
            gap: 10px;
            background: var(--card-bg);
            padding: 12px 20px;
            border-radius: 8px;
            border: 1px solid var(--border);
            margin-bottom: 30px;
            font-weight: 600;
        }

        .radar-dot {
            width: 12px;
            height: 12px;
            border-radius: 50%;
        }

        .radar-dot.open { background: var(--green); box-shadow: 0 0 10px var(--green); }
        .radar-dot.closed { background: var(--red); box-shadow: 0 0 10px var(--red); }

        section {
            margin-bottom: 40px;
        }

        .section-header {
            display: flex;
            align-items: center;
            gap: 15px;
            margin-bottom: 20px;
        }

        .header-line {
            width: 4px;
            height: 24px;
            background: var(--accent);
            border-radius: 2px;
        }

        h2 {
            font-size: 1.5rem;
            color: #fff;
        }

        .rules-grid {
            display: grid;
            grid-template-columns: 1fr;
            gap: 15px;
        }

        .rule-card {
            background: var(--card-bg);
            border: 1px solid var(--border);
            border-radius: 8px;
            padding: 20px;
            cursor: pointer;
            transition: transform 0.2s, border-color 0.2s;
            position: relative;
        }

        .rule-card:hover {
            transform: translateY(-2px);
            border-color: var(--accent);
        }

        .card-title {
            font-size: 1.1rem;
            font-weight: bold;
            color: #fff;
            margin-bottom: 8px;
        }

        .card-desc {
            color: var(--text-muted);
            font-size: 0.95rem;
            white-space: pre-line;
        }

        .bans-flex {
            display: flex;
            flex-wrap: wrap;
            gap: 10px;
        }

        .ban-box {
            background: var(--card-bg);
            border: 1px solid var(--border);
            padding: 10px 18px;
            border-radius: 6px;
            font-weight: 600;
            color: var(--red);
            text-transform: uppercase;
            font-size: 0.9rem;
        }

        #toast {
            position: fixed;
            bottom: 30px;
            right: 30px;
            background: #22c55e;
            color: #fff;
            padding: 12px 24px;
            border-radius: 6px;
            font-weight: 600;
            box-shadow: 0 5px 15px rgba(0,0,0,0.3);
            transform: translateY(100px);
            opacity: 0;
            transition: all 0.3s ease;
            z-index: 1000;
        }

        #toast.show {
            transform: translateY(0);
            opacity: 1;
        }

        #scrollTop {
            position: fixed;
            bottom: 30px;
            left: 30px;
            width: 45px;
            height: 45px;
            background: var(--card-bg);
            color: #fff;
            border: 1px solid var(--border);
            border-radius: 50%;
            cursor: pointer;
            display: none;
            justify-content: center;
            align-items: center;
            font-size: 1.2rem;
            z-index: 999;
            transition: background 0.2s;
        }

        #scrollTop:hover {
            background: var(--accent);
        }

        footer {
            text-align: center;
            padding-top: 40px;
            color: var(--text-muted);
            font-size: 0.9rem;
            border-top: 1px solid var(--border);
            margin-top: 50px;
        }

        footer span {
            color: var(--accent);
            font-weight: bold;
        }
    </style>
</head>
<body>

    <div id="progress-bar"></div>

    <div id="loader">
        <div class="spinner"></div>
        <div id="loadTimer" style="font-weight: bold; color: var(--text-muted);">Загрузка: 5 сек</div>
    </div>

    <div id="toast">Скопировано в буфер обмена!</div>

    <header>
        <h1>U.C.L Регламент</h1>
        <p>Официальные правила соревновательной лиги</p>
    </header>

    <div class="container">
        
        <div class="arena-status">
            <div id="radarDot" class="radar-dot"></div>
            <div id="radarText">Проверка статуса арены...</div>
        </div>

        <div class="search-container">
            <input type="text" id="searchInput" onkeyup="searchRules()" placeholder="Поиск по правилам или бан-стилям...">
        </div>

        <main>
            <!-- 1. Пассив / ПД Фишинг -->
            <section id="passiv">
                <div class="section-header">
                    <div class="header-line"></div>
                    <h2>1. Пассив и ПД Фишинг</h2>
                </div>
                <div class="rules-grid">
                    <div class="rule-card searchable" onclick="copyCardText(this)">
                        <div class="card-title">ПД Фишинг</div>
                        <div class="card-desc">Это когда игрок намеренно перестает бить/взаимодействовать, чтобы сделать идеальное уклонение.
Если вас ловят на стагеринге или вы ничего не можете сделать кроме уклона, то можете выждать момент и сделать два уклона, если по вам делают спамящие комбо (особенно касается медленных стилей).
Пдфишить можно когда у бойца закончилась стамина.</div>
                    </div>
                    <div class="rule-card searchable" onclick="copyCardText(this)">
                        <div class="card-title">Тайминги и ограничения</div>
                        <div class="card-desc">ТКО даётся за 2 фола.
Ждать удара можно максимум 3 секунды (можете случайно выйти за рамки времени — будет только предупреждение, но за злоупотребление начисляется фол).
Попытка удара и получение контрудара сбрасывают таймер порога ПД фиша (таймер 3 сек). Также атака и способности, возвращающие бойцов на нейтральное положение, сбрасывают таймер. 
Использование эмоций приравнивается к бездействию (кроме начала раунда).</div>
                    </div>
                </div>
            </section>

            <!-- 2. Багоюз -->
            <section id="bugs">
                <div class="section-header">
                    <div class="header-line"></div>
                    <h2>2. Багоюз</h2>
                </div>
                <div class="rules-grid">
                    <div class="rule-card searchable" onclick="copyCardText(this)">
                        <div class="card-title">Запрещенные баги</div>
                        <div class="card-desc">• Парирование ульты — когда в вас летит ульта и вас должны пробить, но вы в тайминг прожимаете блок и ульта сжирается (при намеренном использовании будет вылет из реальной жизни).
• Нелегальный стаггеринг — когда удар M1 все еще регистрируется в серии, но задерживается и становится неуклоняемым, а также притягивает игрока обратно, несмотря на уклонение и срабатывание кадров. (Первое нарушение — устное предупреждение, далее — фол).</div>
                    </div>
                    <div class="rule-card searchable" onclick="copyCardText(this)">
                        <div class="card-title">Разрешенный стаггеринг</div>
                        <div class="card-desc">Стаггеринг (тыкать М1 когда хочешь перебить атаку противника) с целью смены темпа или миксапов разрешен.</div>
                    </div>
                </div>
            </section>

            <!-- 3. Медленные комбо М1 -->
            <section id="slow-clicks">
                <div class="section-header">
                    <div class="header-line"></div>
                    <h2>3. Медленные комбо М1 (Слоу-клики)</h2>
                </div>
                <div class="rules-grid">
                    <div class="rule-card searchable" onclick="copyCardText(this)">
                        <div class="card-title">Правила слоу-кликов</div>
                        <div class="card-desc">Медленные удары M1 разрешены только после того, как игрок попал под ультимейт. Медленные M1 нельзя использовать после способностей (например, Focus, Stampede и т.д.). Игрокам разрешено использовать медленные M1 только для ОДНОЙ СЕРИИ УДАРОВ, большее количество приведет к фолу.
ИСКЛЮЧЕНИЕ: нельзя использовать стиль «крюк» для слоу кликов после ультимейта. После ультимейта «айрон фист» можно делать ДВА КОМБО СЛОУ КЛИКА.</div>
                    </div>
                </div>
            </section>

            <!-- 4. С-кейтинг и бекдеши -->
            <section id="movement">
                <div class="section-header">
                    <div class="header-line"></div>
                    <h2>4. С-кейтинг и бекдеши</h2>
                </div>
                <div class="rules-grid">
                    <div class="rule-card searchable" onclick="copyCardText(this)">
                        <div class="card-title">Правила движения назад</div>
                        <div class="card-desc">С-кейтинг — уход назад от противника зажатием кнопки S (направление джойстика назад). Можно использовать после попадания удара или комбо по сопернику, но если вы идете назад и ничего не делаете, пропуская два действия противника — фол. Аналогично с бекдешом.
Если оба игрока намеренно держатся на расстоянии, включается 3-секундный счёт (после порога ПД). ЕСЛИ никто из игроков не приближается — фол обоим.
Против демпси можно фишить, но нельзя уходить назад (С-кейтить). Против шотгана можно использовать бекдеш на способность, если вы до этого сделали бекдеш.</div>
                    </div>
                </div>
            </section>

            <!-- 5. ДД и ТД -->
            <section id="dashes">
                <div class="section-header">
                    <div class="header-line"></div>
                    <h2>5. Дэши</h2>
                </div>
                <div class="rules-grid">
                    <div class="rule-card searchable" onclick="copyCardText(this)">
                        <div class="card-title">Дабл и Трипл деш</div>
                        <div class="card-desc">ДД (дабл деш) — используйте как хотите.
Трипл деш (тройной деш) — 1 фол.</div>
                    </div>
                </div>
            </section>

            <!-- 6. Пользовательские звуки и изображения -->
            <section id="customs">
                <div class="section-header">
                    <div class="header-line"></div>
                    <h2>6. Пользовательские звуки и изображения</h2>
                </div>
                <div class="rules-grid">
                    <div class="rule-card searchable" onclick="copyCardText(this)">
                        <div class="card-title">Кастомный контент</div>
                        <div class="card-desc">Использование неприятных или раздражающих звуковых эффектов и изображений отвлекает игроков:
• Звуковые эффекты идеального уклонения (ПД) остаются на усмотрение игроков, но может быть запрошено их удаление во избежание несправедливого преимущества.
• Пользовательские звуковые эффекты контрударов (каунтер), а также изображения СТРОГО ЗАПРЕЩЕНЫ и должны быть удалены для официальных матчей.
• Пользовательские звуковые эффекты и изображения ультимативных способностей (ульта) разрешены.</div>
                    </div>
                </div>
            </section>

            <!-- 7. Титульные бои -->
            <section id="title-fights">
                <div class="section-header">
                    <div class="header-line"></div>
                    <h2>7. Титульные бои</h2>
                </div>
                <div class="rules-grid">
                    <div class="rule-card searchable" onclick="copyCardText(this)">
                        <div class="card-title">Формат и регламент титулов</div>
                        <div class="card-desc">Проводятся в формате бо3 (3 боя). Игрок может сменить стиль только после поражения; победитель должен сохранять текущий стиль до проигрыша. Правила такие же, как и в обычных боях.
За боем наблюдает один рефери высшей категории.
Каждый бой (не раунд) счётчик фолов аннулируется. В зависимости от количества фолов рефери может поменять итог боя.

ЗАЩИТА ТИТУЛА:
• UNF: Каждую неделю
• UNC: Каждые 2 недели
• UCL: Каждые 2.5 недели</div>
                    </div>
                </div>
            </section>

            <!-- 8. Проведение боев и лимиты -->
            <section id="general-rules">
                <div class="section-header">
                    <div class="header-line"></div>
                    <h2>8. Проведение боев U.C.L</h2>
                </div>
                <div class="rules-grid">
                    <div class="rule-card searchable" onclick="copyCardText(this)">
                        <div class="card-title">Связь, авторитет и лимиты</div>
                        <div class="card-desc">• Проблемы со связью: 5 минут на немедленное возвращение при вылете, иначе ТКО или аннулирование поединка.
• Авторитет рефери: Вердикт судьи — закон. Грубые ошибки судей строго караются после проверки.
• Суточный лимит: Не более 3 боев за одни сутки на одного бойца.
• Смена дивизионов: При доминировании администрация может перевести выше принудительно. В обычном порядке — завоюй пояс текущего рейтинга и проведи 1 защиту.
• Право на вызов чемпиона: Бросить вызов могут только бойцы из Топ-5. Топ-1 обладает эксклюзивной привилегией — чемпион обязан принять его вызов безоговорочно!</div>
                    </div>
                </div>
            </section>

            <!-- 9. Бан стили -->
            <section id="bans">
                <div class="section-header">
                    <div class="header-line"></div>
                    <h2>9. Бан стили</h2>
                </div>
                <div class="bans-flex">
                    <div class="ban-box searchable">slugger</div>
                    <div class="ban-box searchable">hawk</div>
                    <div class="ban-box searchable">hammer</div>
                    <div class="ban-box searchable">switch hit (не может отменять ульту)</div>
                    <div class="ban-box searchable">dragonfish</div>
                    <div class="ban-box searchable">white ash</div>
                    <div class="ban-box searchable">wolf</div>
                    <div class="ban-box searchable">shotgun</div>
                    <div class="ban-box searchable">corkscrew</div>
                    <div class="ban-box searchable">bullet</div>
                    <div class="ban-box searchable">chronos</div>
                    <div class="ban-box searchable">deimos</div>
                    <div class="ban-box searchable">all shinies</div>
                    <div class="ban-box searchable">exclusive styles</div>
                </div>
            </section>

        </main>
    </div>

    <button id="scrollTop" onclick="window.scrollTo({top:0, behavior:'smooth'})">↑</button>

    <footer>
        <p>Официальный регламент соревновательной лиги <span>U.C.L</span> &copy; 2026</p>
    </footer>

    <script>
        let timeLeft = 5;
        const timerElement = document.getElementById('loadTimer');
        
        const countdown = setInterval(() => {
            timeLeft--;
            if (timeLeft > 0) {
                timerElement.textContent = `Загрузка: ${timeLeft} сек`;
            } else {
                clearInterval(countdown);
                timerElement.textContent = `Готово!`;
                const loader = document.getElementById('loader');
                loader.style.opacity = '0';
                setTimeout(() => loader.style.visibility = 'hidden', 500);
            }
        }, 1000);

        function checkArenaStatus() {
            const now = new Date();
            const utc = now.getTime() + (now.getTimezoneOffset() * 60000);
            const msk = new Date(utc + (3600000 * 3));
            const hours = msk.getHours();

            const dot = document.getElementById('radarDot');
            const text = document.getElementById('radarText');

            if (hours >= 12 && hours < 22) {
                dot.className = 'radar-dot open';
                text.textContent = 'Арена открыта (12:00 - 22:00 МСК)';
                text.style.color = '#00e676';
            } else {
                dot.className = 'radar-dot closed';
                text.textContent = 'Арена закрыта (Открытие в 12:00 МСК)';
                text.style.color = 'var(--red)';
            }
        }
        checkArenaStatus();
        setInterval(checkArenaStatus, 30000);

        function searchRules() {
            const query = document.getElementById('searchInput').value.toLowerCase().trim();
            const items = document.querySelectorAll('.searchable');

            items.forEach(item => {
                const text = item.textContent.toLowerCase();
                if (text.includes(query)) {
                    item.style.display = "";
                } else {
                    item.style.display = "none";
                }
            });
        }

        function copyCardText(card) {
            const title = card.querySelector('.card-title') ? card.querySelector('.card-title').innerText : 'Бан стиль';
            const desc = card.querySelector('.card-desc') ? card.querySelector('.card-desc').innerText : card.innerText;
            const textToCopy = `📌 [U.C.L Rule] ${title}: ${desc}`;
            
            navigator.clipboard.writeText(textToCopy).then(() => {
                const toast = document.getElementById('toast');
                toast.classList.add('show');
                setTimeout(() => toast.classList.remove('show'), 2000);
            });
        }

        window.onscroll = () => {
            const winScroll = document.documentElement.scrollTop;
            const height = document.documentElement.scrollHeight - document.documentElement.clientHeight;
            const scrolled = (winScroll / height) * 100;
            document.getElementById("progress-bar").style.width = scrolled + "%";
            document.getElementById("scrollTop").style.display = winScroll > 300 ? "flex" : "none";
        };
    </script>
</body>
</html>
