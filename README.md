
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>U.C.L — Ultimate Championship League Arena</title>
    <link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@400;700;900&family=Teko:wght@600;700&display=swap" rel="stylesheet">
    <style>
        :root {
            --bg-dark: #030407;
            --bg-card: rgba(13, 16, 28, 0.75);
            --gold: #ffb703;
            --gold-glow: rgba(255, 183, 3, 0.5);
            --red: #ff2a4b;
            --red-glow: rgba(255, 42, 75, 0.5);
            --cyan: #00f2fe;
            --cyan-glow: rgba(0, 242, 254, 0.5);
            --text-main: #f0f4f8;
            --text-sub: #94a3b8;
            --border-grid: rgba(255, 183, 3, 0.15);
        }

        * { box-sizing: border-box; margin: 0; padding: 0; }
        html { scroll-behavior: smooth; }
        
        body {
            font-family: 'Montserrat', sans-serif;
            background-color: var(--bg-dark);
            color: var(--text-main);
            line-height: 1.5;
            overflow-x: hidden;
            background-image: 
                radial-gradient(circle at 50% 0%, rgba(255, 183, 3, 0.15) 0%, transparent 50%),
                radial-gradient(circle at 100% 100%, rgba(255, 42, 75, 0.1) 0%, transparent 40%),
                linear-gradient(to right, rgba(255, 255, 255, 0.02) 1px, transparent 1px),
                linear-gradient(to bottom, rgba(255, 255, 255, 0.02) 1px, transparent 1px);
            background-size: 100% 100%, 100% 100%, 40px 40px, 40px 40px;
        }

        /* Top Progress Bar */
        #progress-bar {
            position: fixed; top: 0; left: 0; height: 3px;
            background: linear-gradient(90deg, var(--red), var(--gold), var(--cyan));
            width: 0%; z-index: 10000;
            box-shadow: 0 0 12px var(--gold);
        }

        /* Preloader */
        #loader {
            position: fixed; inset: 0; background: #020203;
            z-index: 99999; display: flex; flex-direction: column;
            align-items: center; justify-content: center;
            transition: opacity 0.4s ease, visibility 0.4s;
        }
        .boxing-glove-icon {
            font-size: 4rem; animation: punch 0.5s infinite alternate cubic-bezier(0.175, 0.885, 0.32, 1.275);
        }
        @keyframes punch {
            0% { transform: scale(0.85) rotate(-10deg); filter: drop-shadow(0 0 10px var(--red)); }
            100% { transform: scale(1.15) rotate(15deg); filter: drop-shadow(0 0 25px var(--gold)); }
        }
        .loader-text {
            font-family: 'Teko', sans-serif; font-size: 2.2rem;
            letter-spacing: 3px; color: var(--gold); margin-top: 10px;
            text-shadow: 0 0 15px var(--gold-glow);
        }

        /* Dynamic Ticker */
        .marquee-wrapper {
            background: linear-gradient(90deg, #111, var(--red), var(--gold), #111);
            color: #fff; font-weight: 900; font-size: 0.75rem;
            text-transform: uppercase; letter-spacing: 1.5px;
            padding: 8px 0; overflow: hidden; white-space: nowrap;
            box-shadow: 0 2px 15px rgba(0,0,0,0.8);
        }
        .marquee-content { display: inline-block; animation: marquee 18s linear infinite; }
        @keyframes marquee { 0% { transform: translateX(0%); } 100% { transform: translateX(-50%); } }

        /* Status Radar */
        .status-container { display: flex; justify-content: center; margin-top: 20px; }
        .status-badge {
            display: flex; align-items: center; gap: 10px;
            background: rgba(15, 18, 32, 0.85); border: 1px solid var(--gold);
            padding: 8px 18px; border-radius: 50px;
            box-shadow: 0 0 20px var(--gold-glow); backdrop-filter: blur(12px);
        }
        .radar-dot { width: 10px; height: 10px; border-radius: 50%; }
        .radar-dot.open { background: #00e676; box-shadow: 0 0 12px #00e676; }
        .radar-dot.closed { background: var(--red); box-shadow: 0 0 12px var(--red); }

        /* Header */
        header { text-align: center; padding: 20px 15px; }
        .main-badge {
            display: inline-block; background: linear-gradient(45deg, var(--red), #ff5252); color: #fff;
            font-family: 'Teko', sans-serif; font-size: 1.3rem; font-weight: 700;
            padding: 2px 16px; border-radius: 4px; text-transform: uppercase;
            letter-spacing: 2px; box-shadow: 0 0 15px var(--red-glow);
            transform: skewX(-8deg); margin-bottom: 12px;
        }
        h1 {
            font-family: 'Teko', sans-serif; font-size: 3.5rem;
            line-height: 0.95; text-transform: uppercase; letter-spacing: 2px;
        }
        h1 span { color: var(--gold); text-shadow: 0 0 20px var(--gold-glow); }

        /* Search Input */
        .search-wrapper { width: 100%; max-width: 650px; margin: 20px auto 0; padding: 0 10px; }
        .search-input {
            width: 100%; background: rgba(15, 18, 32, 0.9);
            border: 2px solid var(--border-grid);
            padding: 14px 20px; border-radius: 14px;
            color: #fff; font-size: 1rem; font-weight: 600;
            outline: none; transition: 0.3s ease; backdrop-filter: blur(10px);
        }
        .search-input:focus { border-color: var(--gold); box-shadow: 0 0 25px var(--gold-glow); }

        /* Nav Horizontal Scroller */
        .nav-scroller {
            display: flex; gap: 10px; overflow-x: auto;
            padding: 20px 10px 10px; scrollbar-width: none;
            justify-content: center; flex-wrap: wrap;
        }
        .nav-scroller::-webkit-scrollbar { display: none; }
        .nav-link {
            background: rgba(20, 25, 45, 0.7); border: 1px solid var(--border-grid);
            color: var(--text-sub); padding: 8px 16px; border-radius: 8px;
            font-weight: 700; font-size: 0.8rem; text-decoration: none;
            text-transform: uppercase; transition: 0.2s ease;
        }
        .nav-link:hover { border-color: var(--gold); color: #fff; transform: translateY(-2deg); }

        /* Main Container & Sections */
        .container { width: 100%; max-width: 1250px; margin: 30px auto; padding: 0 15px; }
        section { margin-bottom: 45px; }

        .section-header {
            display: flex; align-items: center; gap: 12px;
            margin-bottom: 22px; border-bottom: 2px solid var(--border-grid);
            padding-bottom: 8px;
        }
        .section-header h2 {
            font-family: 'Teko', sans-serif; font-size: 2.3rem;
            text-transform: uppercase; letter-spacing: 1px;
        }
        .header-line {
            height: 5px; width: 25px; background: var(--gold);
            box-shadow: 0 0 12px var(--gold-glow); border-radius: 2px;
        }

        /* Cards Grid */
        .rules-grid {
            display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 20px;
        }
        .rule-card {
            background: var(--bg-card); border: 1px solid var(--border-grid);
            border-radius: 16px; padding: 22px; backdrop-filter: blur(16px);
            display: flex; flex-direction: column; justify-content: space-between;
            transition: all 0.3s ease; cursor: pointer; position: relative;
        }
        .rule-card:hover {
            transform: translateY(-4deg);
            border-color: var(--gold);
            box-shadow: 0 8px 25px rgba(255, 183, 3, 0.15);
        }
        .rule-card.danger-card { border-color: rgba(255, 42, 75, 0.3); }
        .rule-card.danger-card:hover {
            border-color: var(--red);
            box-shadow: 0 8px 25px rgba(255, 42, 75, 0.2);
        }

        .card-top {
            display: flex; justify-content: space-between; align-items: flex-start;
            margin-bottom: 14px; gap: 10px;
        }
        .card-title { font-size: 1.1rem; font-weight: 800; line-height: 1.3; }

        .badge-penalty {
            font-size: 0.7rem; font-weight: 900; padding: 4px 10px;
            border-radius: 6px; text-transform: uppercase; white-space: nowrap;
        }
        .badge-penalty.warn { background: rgba(255, 183, 3, 0.15); color: var(--gold); border: 1px solid var(--gold); }
        .badge-penalty.danger { background: rgba(255, 42, 75, 0.15); color: var(--red); border: 1px solid var(--red); }
        .badge-penalty.info { background: rgba(0, 242, 254, 0.15); color: var(--cyan); border: 1px solid var(--cyan); }

        .card-desc { color: var(--text-sub); font-size: 0.92rem; }
        .card-desc strong { color: #fff; }

        /* Ban List */
        .bans-flex {
            display: grid; grid-template-columns: repeat(auto-fill, minmax(140px, 1fr)); gap: 12px;
        }
        .ban-box {
            background: rgba(255, 42, 75, 0.06); border: 1px solid rgba(255, 42, 75, 0.25);
            border-radius: 10px; padding: 14px 8px; text-align: center;
            font-weight: 800; color: #ff6b81; font-size: 0.85rem; transition: 0.2s;
        }
        .ban-box:hover { background: rgba(255, 42, 75, 0.2); transform: scale(1.03); }

        /* Notification Toast */
        #toast {
            position: fixed; bottom: 30px; left: 50%; transform: translateX(-50%) translateY(100px);
            background: var(--gold); color: #000; padding: 10px 24px; border-radius: 30px;
            font-weight: 800; font-size: 0.85rem; box-shadow: 0 0 20px var(--gold-glow);
            opacity: 0; transition: all 0.3s ease; z-index: 10000; pointer-events: none;
        }
        #toast.show { transform: translateX(-50%) translateY(0); opacity: 1; }

        /* Scroll Top Button */
        #scrollTop {
            position: fixed; bottom: 25px; right: 25px;
            width: 48px; height: 48px; background: var(--gold);
            color: #000; border: none; border-radius: 50%; cursor: pointer;
            display: none; align-items: center; justify-content: center;
            font-weight: 900; font-size: 1.3rem; z-index: 999;
            box-shadow: 0 0 20px var(--gold-glow); transition: 0.2s;
        }
        #scrollTop:hover { transform: scale(1.1); }

        footer {
            text-align: center; padding: 30px 15px;
            border-top: 1px solid var(--border-grid); color: var(--text-sub); font-size: 0.85rem;
        }
        footer span { color: var(--gold); font-weight: 800; }
    </style>
</head>
<body>

    <div id="loader">
        <div class="boxing-glove-icon">🥊</div>
        <div class="loader-text">U.C.L ARENA LOADING...</div>
    </div>

    <div id="progress-bar"></div>
    <div id="toast">Правило скопировано в буфер!</div>

    <div class="marquee-wrapper">
        <div class="marquee-content">
            ⚡ U.C.L OFFICIAL CHAMPIONSHIP RULES • 3 ФОЛА = ДИСКВАЛИФИКАЦИЯ • СОБЛЮДАЙТЕ РЕГЛАМЕНТ LIGA U.C.L • ⚡
        </div>
    </div>

    <header>
        <div class="status-container">
            <div class="status-badge">
                <div id="radarDot" class="radar-dot"></div>
                <span id="radarText" style="font-weight:800; font-size:0.8rem; text-transform:uppercase;">Проверка арены...</span>
            </div>
        </div>

        <div style="margin-top:20px;">
            <div class="main-badge">Ultimate Championship League</div>
            <h1>Официальный Регламент <span>U.C.L</span></h1>
        </div>

        <div class="search-wrapper">
            <input type="text" id="searchInput" class="search-input" placeholder="⚡ Поиск правил (фол, ПД, слоу клик...)" oninput="searchRules()">
        </div>

        <div class="nav-scroller">
            <a href="#pd" class="nav-link">1. Пассив / ПД</a>
            <a href="#bugs" class="nav-link">2. Багоюз</a>
            <a href="#combos" class="nav-link">3. Слоу клики</a>
            <a href="#skating" class="nav-link">4. С-кейтинг</a>
            <a href="#dd" class="nav-link">5. Дабл деш</a>
            <a href="#audio" class="nav-link">6. Звуки / Медиа</a>
            <a href="#title" class="nav-link">7. Титульные бои</a>
            <a href="#combat" class="nav-link">8. Регламент</a>
            <a href="#bans" class="nav-link">9. Бан стили</a>
        </div>
    </header>

    <main class="container">

        <section id="pd">
            <div class="section-header">
                <div class="header-line"></div>
                <h2>1. Пассив и ПД Фишинг</h2>
            </div>
            <div class="rules-grid">
                <div class="rule-card searchable" onclick="copyCardText(this)">
                    <div class="card-top">
                        <div class="card-title">Правила ПД Фишинга</div>
                        <span class="badge-penalty warn">Лимит 2 раза</span>
                    </div>
                    <div class="card-desc">ПД Фишинг — намеренный уклон от первого взаимодействия. Разрешен <strong>до 2 уклонов</strong> при стаггере или спам-комбо. ПД фиш без ударов соперника запрещен. ПД фиш разрешен, только если стамина слита <strong>полностью</strong>.</div>
                </div>
                <div class="rule-card searchable" onclick="copyCardText(this)">
                    <div class="card-top">
                        <div class="card-title">Таймер 2.5 сек и Dempsey</div>
                        <span class="badge-penalty warn">Фол</span>
                    </div>
                    <div class="card-desc">Максимум ожидания — <strong>2.5 сек</strong> (включая Dempsey Roll). Намерение жонглировать/фишить первым 2+ раза при таймере = <strong>фол</strong>. Эмоции засчитываются как бездействие.</div>
                </div>
                <div class="rule-card danger-card searchable" onclick="copyCardText(this)">
                    <div class="card-top">
                        <div class="card-title">Сброс таймера и Ульта</div>
                        <span class="badge-penalty danger">Фол / Дисквалификация</span>
                    </div>
                    <div class="card-desc">Удар, получение каунтера или скилл нейтрала <strong>сбрасывают 2.5s таймер</strong>. Пассив или ПД-фиш ради набивания ульта в конце боя = <strong>1 фол</strong>. <strong>3 фола = Дисквалификация (DQ)</strong>.</div>
                </div>
            </div>
        </section>

        <section id="bugs">
            <div class="section-header">
                <div class="header-line"></div>
                <h2>2. Запрещенный Багоюз</h2>
            </div>
            <div class="rules-grid">
                <div class="rule-card danger-card searchable" onclick="copyCardText(this)">
                    <div class="card-top">
                        <div class="card-title">Парирование ульты</div>
                        <span class="badge-penalty danger">1 Фол</span>
                    </div>
                    <div class="card-desc">Намеренный блок в тайминг при полете ульта, сжигающий ультимейт соперника без урона. Наказание: <strong>1 фол</strong>.</div>
                </div>
                <div class="rule-card searchable" onclick="copyCardText(this)">
                    <div class="card-top">
                        <div class="card-title">Нелегальный стаггеринг</div>
                        <span class="badge-penalty warn">Предупреждение / Фол</span>
                    </div>
                    <div class="card-desc">Задержка M1 в серии, при которой удар притягивает соперника и становится неуклоняемым. Наказание: <strong>предупреждение ➔ фол</strong>. Обычный стаггеринг (смена темпа/миксапы) <strong>разрешен</strong>.</div>
                </div>
            </div>
        </section>

        <section id="combos">
            <div class="section-header">
                <div class="header-line"></div>
                <h2>3. Медленные комбо M1 (Слоу клики)</h2>
            </div>
            <div class="rules-grid">
                <div class="rule-card searchable" onclick="copyCardText(this)">
                    <div class="card-top">
                        <div class="card-title">Лимиты M1 Слоу Кликов</div>
                        <span class="badge-penalty warn">Фол при превышении</span>
                    </div>
                    <div class="card-desc">Разрешено <strong>1 серия после навыка</strong> (1-3 клика) и <strong>до 2 серий после ульта</strong>. Любое превышение — <strong>фол</strong>.</div>
                </div>
                <div class="rule-card searchable" onclick="copyCardText(this)">
                    <div class="card-top">
                        <div class="card-title">Особые Стили и Исключения</div>
                        <span class="badge-penalty info">Ограничения</span>
                    </div>
                    <div class="card-desc">Стилю <strong>Крюк</strong> слоу клики <strong>полностью запрещены</strong>. <strong>Iron Fist</strong> разрешена только <strong>1 серия после навыка</strong>.</div>
                </div>
            </div>
        </section>

        <section id="skating">
            <div class="section-header">
                <div class="header-line"></div>
                <h2>4. С-кейтинг и бекдеши</h2>
            </div>
            <div class="rules-grid">
                <div class="rule-card searchable" onclick="copyCardText(this)">
                    <div class="card-top">
                        <div class="card-title">Уход назад и Пропуски</div>
                        <span class="badge-penalty warn">Фол</span>
                    </div>
                    <div class="card-desc">С-кейтинг (кнопка S) разрешен после успешного попадания. Уход назад с пропуском 2 действий соперника — <strong>фол</strong> (аналогично для бекдеша).</div>
                </div>
                <div class="rule-card searchable" onclick="copyCardText(this)">
                    <div class="card-top">
                        <div class="card-title">Против Dempsey и Shotgun</div>
                        <span class="badge-penalty warn">Фол обоим при затяжке</span>
                    </div>
                    <div class="card-desc">Против <strong>Dempsey Roll</strong> C-кейт <strong>строго запрещен</strong>. Против Shotgun разрешен бекдеш на скилл при пред-бекдеше. Обоюдный кайт включает 3-секундный отсчет после 2.5с ПД — фол обоим.</div>
                </div>
            </div>
        </section>

        <section id="dd">
            <div class="section-header">
                <div class="header-line"></div>
                <h2>5. Дабл деш (ДД)</h2>
            </div>
            <div class="rules-grid">
                <div class="rule-card danger-card searchable" onclick="copyCardText(this)">
                    <div class="card-top">
                        <div class="card-title">ДД Спидстеров</div>
                        <span class="badge-penalty danger">Запрещено (Фол)</span>
                    </div>
                    <div class="card-desc">Дабл деш подряд у спидстеров для уклона от финтов — <strong>запрещен (фол)</strong>.</div>
                </div>
                <div class="rule-card searchable" onclick="copyCardText(this)">
                    <div class="card-top">
                        <div class="card-title">Правила Дешей</div>
                        <span class="badge-penalty info">Правило 2 атак</span>
                    </div>
                    <div class="card-desc">Два деша подряд официально разрешены <strong>только после 2 атак</strong>. <strong>Трипл деш полностью запрещен</strong>.</div>
                </div>
            </div>
        </section>

        <section id="audio">
            <div class="section-header">
                <div class="header-line"></div>
                <h2>6. Звуки и Картинки</h2>
            </div>
            <div class="rules-grid">
                <div class="rule-card searchable" onclick="copyCardText(this)">
                    <div class="card-top">
                        <div class="card-title">Звуки Perfect Dodge</div>
                        <span class="badge-penalty warn">Ограничения</span>
                    </div>
                    <div class="card-desc">ПД звуки разрешены, но рефери вправе потребовать их отключить при создании помех сопернику.</div>
                </div>
                <div class="rule-card danger-card searchable" onclick="copyCardText(this)">
                    <div class="card-top">
                        <div class="card-title">Каунтеры и Ультимейты</div>
                        <span class="badge-penalty danger">Строгий Бан</span>
                    </div>
                    <div class="card-desc">Звуки каунтеров и сторонние картинки — <strong>строго запрещены</strong>. Звуки и картинки для <strong>ультимейтов разрешены</strong>.</div>
                </div>
            </div>
        </section>

        <section id="title">
            <div class="section-header">
                <div class="header-line"></div>
                <h2>7. Титульные Бои</h2>
            </div>
            <div class="rules-grid">
                <div class="rule-card searchable" onclick="copyCardText(this)">
                    <div class="card-top">
                        <div class="card-title">Формат Bo3 и Оценивание</div>
                        <span class="badge-penalty info">Bo3</span>
                    </div>
                    <div class="card-desc">Формат Bo3 (до 2 побед). Смена стиля — только после поражения. Бой судят 3 рефери (макс 10 баллов). За пассивную победу с минимальным отрывом очки могут быть отданы сопернику.</div>
                </div>
                <div class="rule-card searchable" onclick="copyCardText(this)">
                    <div class="card-top">
                        <div class="card-title">Сроки защиты поясов</div>
                        <span class="badge-penalty info">График</span>
                    </div>
                    <div class="card-desc">
                        • <strong>UNF:</strong> Защита каждую неделю<br>
                        • <strong>UNC:</strong> Защита каждые 2 недели<br>
                        • <strong>UCL:</strong> Защита каждые 2.5 недели
                    </div>
                </div>
            </div>
        </section>

        <section id="combat">
            <div class="section-header">
                <div class="header-line"></div>
                <h2>8. Общий Регламент</h2>
            </div>
            <div class="rules-grid">
                <div class="rule-card searchable" onclick="copyCardText(this)">
                    <div class="card-top">
                        <div class="card-title">Вылеты и Судейство</div>
                        <span class="badge-penalty warn">5 минут / 3 фола</span>
                    </div>
                    <div class="card-desc">При вылете дается <strong>5 минут</strong> на возврат. Нарушения: 2 фола = 1 варн, 2 варна = Поражение/DQ (3 фола = DQ). Решение рефери во время боя окончательно.</div>
                </div>
                <div class="rule-card searchable" onclick="copyCardText(this)">
                    <div class="card-top">
                        <div class="card-title">Лимиты и Продвижение</div>
                        <span class="badge-penalty warn">Макс 3 боя в день</span>
                    </div>
                    <div class="card-desc">Лимит: <strong>макс 3 боя в сутки</strong>. Вызов чемпиону бросают бойцы из <strong>Топ-5</strong>. <strong>Топ-1</strong> получает обязательный бой. Возможен принудительный перевод выше за доминирование.</div>
                </div>
            </div>
        </section>

        <section id="bans">
            <div class="section-header">
                <div class="header-line"></div>
                <h2>9. Запрещенные Стили (Banned)</h2>
            </div>
            <div class="bans-flex">
                <div class="ban-box searchable">Slugger</div>
                <div class="ban-box searchable">Hawk</div>
                <div class="ban-box searchable">Hammer</div>
                <div class="ban-box searchable">Dragon Fish</div>
                <div class="ban-box searchable">White Ash</div>
                <div class="ban-box searchable">Wolf</div>
                <div class="ban-box searchable">Hitman</div>
                <div class="ban-box searchable">Shotgun</div>
                <div class="ban-box searchable">Corkscrew</div>
                <div class="ban-box searchable">Chronos</div>
                <div class="ban-box searchable">Iron Fist (Restricted)</div>
                <div class="ban-box searchable">All Shinies</div>
                <div class="ban-box searchable">Custom / Unique / Exclusive</div>
            </div>
        </section>

    </main>

    <button id="scrollTop" onclick="window.scrollTo({top:0, behavior:'smooth'})">↑</button>

    <footer>
        <p>Официальный регламент соревновательной лиги <span>U.C.L</span> &copy; 2026</p>
    </footer>

    <script>
        // Smooth Preloader Hide
        window.addEventListener('load', () => {
            const loader = document.getElementById('loader');
            loader.style.opacity = '0';
            setTimeout(() => loader.style.visibility = 'hidden', 400);
        });

        // Arena Status Radar (MSK Time)
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

        // Advanced Live Search
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

        // Copy Card Text Action
        function copyCardText(card) {
            const title = card.querySelector('.card-title').innerText;
            const desc = card.querySelector('.card-desc').innerText;
            const textToCopy = `📌 [U.C.L Rule] ${title}: ${desc}`;
            
            navigator.clipboard.writeText(textToCopy).then(() => {
                const toast = document.getElementById('toast');
                toast.classList.add('show');
                setTimeout(() => toast.classList.remove('show'), 2000);
            });
        }

        // Scroll Progress & Scroll To Top Button
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
