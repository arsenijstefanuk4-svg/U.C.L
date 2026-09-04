
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Untitled CIS League (U.C.L)</title>
    <link rel="canonical" href="https://arsenijstefanuk4-svg.github.io/UCL/">
    <style>
        :root {
            --bg-color: #0b0b0e;
            --card-bg: rgba(20, 20, 28, 0.7);
            --border-grid: rgba(255, 255, 255, 0.08);
            --red: #ff0055;
            --gold: #ffb700;
            --green: #00e676;
            --blue: #00bfff;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Inter', sans-serif;
        }

        body {
            background-color: var(--bg-color);
            color: #fff;
            overflow-x: hidden;
        }

        /* --- Punch Stage & Loader --- */
        #loader {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: var(--bg-color);
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            z-index: 9999;
            transition: opacity 0.5s ease;
        }

        .punch-stage {
            position: relative;
            display: flex;
            align-items: center;
            justify-content: center;
            margin-bottom: 20px;
        }

        .glove-left, .glove-right {
            font-size: 3.5rem;
            position: relative;
            z-index: 2;
            animation: punchLeft 0.8s ease-in-out infinite alternate;
        }

        .glove-right {
            animation: punchRight 0.8s ease-in-out infinite alternate;
        }

        @keyframes punchLeft {
            0% { transform: rotate(-10deg) translate(0, 0); }
            100% { transform: rotate(15deg) translate(25px, -5px); }
        }

        @keyframes punchRight {
            0% { transform: rotate(10deg) translate(0, 0); }
            100% { transform: rotate(-15deg) translate(-25px, -5px); }
        }

        .impact-spark {
            position: absolute;
            width: 80px;
            height: 80px;
            border-radius: 50%;
            background: radial-gradient(circle, #fff, var(--red), transparent);
            box-shadow: 0 0 25px var(--red);
            animation: sparkImpact 0.8s ease-in-out infinite;
            z-index: 1;
        }

        @keyframes sparkImpact {
            0% { transform: scale(0.2); opacity: 0; }
            50% { opacity: 1; }
            100% { transform: scale(1.5); opacity: 0; }
        }

        #loadTimer {
            font-size: 1.2rem;
            color: var(--gold);
            margin-top: 10px;
            font-weight: 700;
        }

        /* --- Top Progress Bar --- */
        #progress-bar {
            position: fixed;
            top: 0;
            left: 0;
            height: 3px;
            background: linear-gradient(90deg, var(--red), var(--gold));
            width: 0%;
            z-index: 10000;
        }

        /* --- Running Marquee --- */
        .marquee-wrapper {
            background: linear-gradient(90deg, var(--red), var(--gold), var(--red));
            color: #000;
            font-weight: 800;
            text-transform: uppercase;
            font-size: 0.85rem;
            letter-spacing: 1px;
            padding: 6px 0;
            overflow: hidden;
            white-space: nowrap;
        }

        .marquee-content {
            display: inline-block;
            animation: marquee 20s linear infinite;
        }

        @keyframes marquee {
            0% { transform: translateX(0); }
            100% { transform: translateX(-50%); }
        }

        /* --- Header & Badges --- */
        header {
            padding: 20px;
            max-width: 1200px;
            margin: 0 auto;
        }

        .status-container {
            display: flex;
            align-items: center;
            gap: 12px;
            margin-bottom: 15px;
            flex-wrap: wrap;
        }

        .status-badge, .online-badge {
            display: inline-flex;
            align-items: center;
            gap: 8px;
            background: rgba(255, 255, 255, 0.05);
            border: 1px solid var(--border-grid);
            padding: 6px 14px;
            border-radius: 20px;
            font-size: 13px;
            backdrop-filter: blur(10px);
        }

        .radar-dot {
            width: 8px;
            height: 8px;
            border-radius: 50%;
        }

        .radar-dot.open {
            background-color: var(--green);
            box-shadow: 0 0 8px var(--green);
        }

        .radar-dot.closed {
            background-color: var(--red);
            box-shadow: 0 0 8px var(--red);
        }

        .online-dot {
            width: 8px;
            height: 8px;
            background-color: var(--blue);
            border-radius: 50%;
            box-shadow: 0 0 8px var(--blue);
            animation: blink 1.2s infinite alternate;
        }

        @keyframes blink {
            0% { opacity: 0.3; }
            100% { opacity: 1; }
        }

        .title-badge {
            font-size: 0.9rem;
            color: var(--gold);
            text-transform: uppercase;
            letter-spacing: 2px;
            margin-bottom: 5px;
        }

        h1 {
            font-size: 2.5rem;
            font-weight: 900;
        }

        h1 span {
            color: var(--red);
            text-shadow: 0 0 15px var(--red);
        }

        /* --- Search & Nav --- */
        .search-wrapper {
            margin: 20px 0;
        }

        .search-input {
            width: 100%;
            padding: 12px 20px;
            background: rgba(255, 255, 255, 0.05);
            border: 1px solid var(--border-grid);
            border-radius: 8px;
            color: #fff;
            font-size: 1rem;
            outline: none;
            transition: 0.3s;
        }

        .search-input:focus {
            border-color: var(--red);
            box-shadow: 0 0 10px rgba(255, 0, 85, 0.3);
        }

        .nav-links {
            display: flex;
            flex-wrap: wrap;
            gap: 10px;
            margin-top: 15px;
        }

        .nav-link {
            color: #aaa;
            text-decoration: none;
            font-size: 0.85rem;
            padding: 6px 12px;
            background: rgba(255, 255, 255, 0.03);
            border: 1px solid var(--border-grid);
            border-radius: 6px;
            transition: 0.2s;
        }

        .nav-link:hover {
            color: #fff;
            border-color: var(--red);
            background: rgba(255, 0, 85, 0.1);
        }

        /* --- Cards & Rules --- */
        main {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px 40px;
        }

        .section-header {
            display: flex;
            align-items: center;
            gap: 10px;
            margin: 35px 0 15px;
            border-bottom: 1px solid var(--border-grid);
            padding-bottom: 8px;
        }

        .rule-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 15px;
        }

        .rule-card {
            background: var(--card-bg);
            border: 1px solid var(--border-grid);
            border-radius: 10px;
            padding: 18px;
            backdrop-filter: blur(5px);
            cursor: pointer;
            transition: 0.3s;
        }

        .rule-card:hover {
            border-color: rgba(255, 255, 255, 0.2);
            transform: translateY(-2px);
        }

        .card-top {
            display: flex;
            justify-content: space-between;
            align-items: flex-start;
            margin-bottom: 10px;
        }

        .card-title {
            font-weight: 700;
            font-size: 1.1rem;
        }

        .badge-penalty {
            font-size: 0.75rem;
            padding: 2px 8px;
            border-radius: 4px;
        }

        .badge-penalty.warn {
            background: rgba(255, 183, 0, 0.1);
            color: var(--gold);
            border: 1px solid rgba(255, 183, 0, 0.3);
        }

        .badge-penalty.danger {
            background: rgba(255, 0, 85, 0.1);
            color: var(--red);
            border: 1px solid rgba(255, 0, 85, 0.3);
        }

        .badge-penalty.info {
            background: rgba(0, 191, 255, 0.1);
            color: var(--blue);
            border: 1px solid rgba(0, 191, 255, 0.3);
        }

        .card-desc {
            color: #ccc;
            font-size: 0.9rem;
            line-height: 1.5;
        }

        /* --- Ban Boxes --- */
        .bans-flex {
            display: flex;
            flex-wrap: wrap;
            gap: 10px;
            margin-top: 15px;
        }

        .ban-box {
            background: rgba(255, 0, 85, 0.12);
            border: 1px solid rgba(255, 0, 85, 0.3);
            color: #ff4d88;
            padding: 8px 16px;
            border-radius: 6px;
            font-size: 0.85rem;
            font-weight: 700;
            text-transform: uppercase;
            cursor: pointer;
        }

        /* --- Footer & UI Components --- */
        #scrollTop {
            position: fixed;
            bottom: 20px;
            right: 20px;
            width: 40px;
            height: 40px;
            border-radius: 50%;
            background: var(--red);
            color: #fff;
            border: none;
            font-size: 1.2rem;
            cursor: pointer;
            display: none;
            align-items: center;
            justify-content: center;
            box-shadow: 0 0 10px rgba(255, 0, 85, 0.5);
            z-index: 1000;
        }

        #toast {
            position: fixed;
            bottom: 20px;
            left: 50%;
            transform: translateX(-50%) translateY(100px);
            background: var(--red);
            color: #fff;
            padding: 10px 20px;
            border-radius: 6px;
            font-weight: 600;
            transition: 0.3s ease;
            opacity: 0;
            z-index: 10000;
            box-shadow: 0 0 15px rgba(255, 0, 85, 0.5);
        }

        #toast.show {
            transform: translateX(-50%) translateY(0);
            opacity: 1;
        }

        footer {
            text-align: center;
            padding: 30px;
            border-top: 1px solid var(--border-grid);
            color: #777;
            font-size: 0.85rem;
        }

        footer span {
            color: var(--red);
            font-weight: 700;
        }
    </style>
</head>
<body>

    <div id="progress-bar"></div>

    <div id="loader">
        <div class="punch-stage">
            <div class="glove-left">🥊</div>
            <div class="impact-spark"></div>
            <div class="glove-right">🥊</div>
        </div>
        <div style="font-weight: 700; letter-spacing: 2px;">ПОДГОТОВКА АРЕНЫ U.C.L...</div>
        <div id="loadTimer">Загрузка: 5 сек</div>
    </div>

    <div id="toast">Правило скопировано в буфер!</div>

    <div class="marquee-wrapper">
        <div class="marquee-content">
            ⚡ ПРАВИЛА БОЁВ U.C.L • ОФИЦИАЛЬНЫЙ РЕГЛАМЕНТ • СОБЛЮДАЙТЕ ПРАВИЛА ЛИГИ • ⚡ ПРАВИЛА БОЁВ U.C.L • ОФИЦИАЛЬНЫЙ РЕГЛАМЕНТ • СОБЛЮДАЙТЕ ПРАВИЛА ЛИГИ • ⚡
        </div>
    </div>

    <header>
        <div class="status-container">
            <div class="status-badge">
                <div id="radarDot" class="radar-dot"></div>
                <span id="radarText">Проверка арены...</span>
            </div>

            <div class="online-badge">
                <div class="online-dot"></div>
                <span>На сайте: <strong id="onlineCountNumber">1</strong> чел.</span>
            </div>
        </div>

        <div>
            <div class="title-badge">Untitled CIS League</div>
            <h1>Правила боёв <span>U.C.L</span></h1>
        </div>

        <div class="search-wrapper">
            <input type="text" id="searchInput" class="search-input" placeholder="🔍 Поиск правил (пассив, деш, баг, фол)..." oninput="searchRules()">
        </div>

        <div class="nav-links">
            <a href="#pd" class="nav-link">1. Пассив</a>
            <a href="#bugs" class="nav-link">2. Багоюз</a>
            <a href="#combos" class="nav-link">3. Медленные комбо M1</a>
            <a href="#skating" class="nav-link">4. С-кейтинг и бекдеши</a>
            <a href="#dd" class="nav-link">5. ДД (дабл деш)</a>
            <a href="#audio" class="nav-link">6. Звуки / Изображения</a>
            <a href="#title" class="nav-link">7. Титульные бои</a>
            <a href="#combat" class="nav-link">8. Регламент боев</a>
            <a href="#bans" class="nav-link">9. Бан стили</a>
        </div>
    </header>

    <main>
        <section id="pd">
            <div class="section-header">
                <h2>1. Пассив</h2>
            </div>
            <div class="rule-grid">
                <div class="rule-card searchable" onclick="copyCardText(this)">
                    <div class="card-top">
                        <div class="card-title">ПД Фишинг</div>
                        <span class="badge-penalty info">Определение</span>
                    </div>
                    <div class="card-desc">
                        ПД Фишинг— это когда игрок намеренно перестает бить/взаимодействовать, чтобы сделать идеальное уклонение.<br><br>
                        Если вас ловят на стаггеринге или вы ничего не можете сделать кроме уклона, то можете выждать момент и сделать два уклона, если по вам делают спамящие комбо (особенно касается медленных стилей).
                    </div>
                </div>

                <div class="rule-card searchable" onclick="copyCardText(this)">
                    <div class="card-top">
                        <div class="card-title">Таймеры и Ограничения</div>
                        <span class="badge-penalty warn">Предупреждение / Фол</span>
                    </div>
                    <div class="card-desc">
                        Ждать удара можно максимум <strong>2 секунды</strong>. Вы можете случайно выйти за рамки времени и будет только предупреждение, но если вы злоупотребляете этим — получите фол. Это касается и Демпси Ролла — вы не можете злоупотреблять им больше чем <strong>2 секунды</strong>.<br><br>
                        Если вы первым ждёте удар и ПД-фишите больше двух раз (даже в рамки 2 секунд) — даётся фол.
                    </div>
                </div>

                <div class="rule-card searchable" onclick="copyCardText(this)">
                    <div class="card-top">
                        <div class="card-title">Сброс таймера, Эмоции и Стамина</div>
                        <span class="badge-penalty danger">2 Фола</span>
                    </div>
                    <div class="card-desc">
                        Попытка удара и получение контрудара сбрасывают таймер ПД-фиша. Также атака и способности, возвращающие бойцов на нейтральное положение, сбрасывают таймер.<br><br>
                        Использование эмоций приравнивается к бездействию (кроме начала раунда).<br><br>
                        Если вы пассивите или ПД-фишите в конце боя, чтобы нанести ульту — это приравнивается к <strong>двум фолам</strong>.<br><br>
                        ПД-фишить можно, когда у бойца закончилась стамина <strong>ПОЛНОСТЬЮ</strong>.
                    </div>
                </div>
            </div>
        </section>

        <section id="bugs">
            <div class="section-header">
                <h2>2. Багоюз</h2>
            </div>
            <div class="rule-grid">
                <div class="rule-card searchable" onclick="copyCardText(this)">
                    <div class="card-top">
                        <div class="card-title">Парирование ульты</div>
                        <span class="badge-penalty danger">Вылет из лиги</span>
                    </div>
                    <div class="card-desc">
                        Когда в вас летит ульта и вы в тайминг прожимаете блок, из-за чего ульта сжирается (если сделаете это намеренно — будет дисквалификация).
                    </div>
                </div>

                <div class="rule-card searchable" onclick="copyCardText(this)">
                    <div class="card-top">
                        <div class="card-title">Нелегальный стаггеринг</div>
                        <span class="badge-penalty warn">Предупреждение ➔ Фол</span>
                    </div>
                    <div class="card-desc">
                        Это когда удар M1 все еще регистрируется в серии, но задерживается и становится неуклоняемым, а также притягивает игрока обратно, несмотря на уклонение.<br><br>
                        Первое нарушение — устное предупреждение. Последующие приведут к фолу.
                    </div>
                </div>

                <div class="rule-card searchable" onclick="copyCardText(this)">
                    <div class="card-top">
                        <div class="card-title">Разрешенный стаггеринг</div>
                        <span class="badge-penalty info">Разрешено</span>
                    </div>
                    <div class="card-desc">
                        Стаггеринг (тыкать М1, когда хочешь перебить атаку противника) с целью смены темпа или миксапов разрешен.
                    </div>
                </div>
            </div>
        </section>

        <section id="combos">
            <div class="section-header">
                <h2>3. Медленные комбо М1 (слоу клики)</h2>
            </div>
            <div class="rule-grid">
                <div class="rule-card searchable" onclick="copyCardText(this)">
                    <div class="card-top">
                        <div class="card-title">Правила применения</div>
                        <span class="badge-penalty warn">Фол при нарушении</span>
                    </div>
                    <div class="card-desc">
                        Медленные удары M1 разрешены только после того, как игрок попал под ультимейт. Медленные M1 нельзя использовать после способностей (Focus, Stampede и т.д.). Игрокам разрешено использовать медленные M1 только для <strong>ОДНОЙ СЕРИИ УДАРОВ</strong>, большее количество приведет к фолу.
                    </div>
                </div>

                <div class="rule-card searchable" onclick="copyCardText(this)">
                    <div class="card-top">
                        <div class="card-title">Исключения для стилей</div>
                        <span class="badge-penalty info">Исключения</span>
                    </div>
                    <div class="card-desc">
                        <strong>ИСКЛЮЧЕНИЕ:</strong> нельзя использовать стилю Крюк слоу-клики после ультимейта.<br><br>
                        После ультимейта Айрон Фиста можно делать <strong>ДВА КОМБО СЛОУ-КЛИКА</strong>.
                    </div>
                </div>
            </div>
        </section>

        <section id="skating">
            <div class="section-header">
                <h2>4. С-кейтинг и бекдеши</h2>
            </div>
            <div class="rule-grid">
                <div class="rule-card searchable" onclick="copyCardText(this)">
                    <div class="card-top">
                        <div class="card-title">С-кейтинг</div>
                        <span class="badge-penalty warn">Фол</span>
                    </div>
                    <div class="card-desc">
                        С-кейтинг — уход назад от противника (зажатие кнопки S / джойстика назад). Можно использовать после попадания удара по сопернику. Если вы идете назад и ничего не делаете, пропуская два действия противника — фол.
                    </div>
                </div>

                <div class="rule-card searchable" onclick="copyCardText(this)">
                    <div class="card-top">
                        <div class="card-title">Обоюдный кайтинг</div>
                        <span class="badge-penalty danger">Фол обоим</span>
                    </div>
                    <div class="card-desc">
                        Если оба игрока намеренно держатся на расстоянии, включается 3-секундный счёт. Если никто из игроков не приближается — оба получают фол.
                    </div>
                </div>

                <div class="rule-card searchable" onclick="copyCardText(this)">
                    <div class="card-top">
                        <div class="card-title">Против Демпси и Шотгана</div>
                        <span class="badge-penalty info">Особые условия</span>
                    </div>
                    <div class="card-desc">
                        Против Демпси можно фишить, но нельзя уходить назад (С-кейтить).<br><br>
                        Против Шотгана можно использовать бекдеш на способность, если вы до этого сделали бекдеш.
                    </div>
                </div>
            </div>
        </section>

        <section id="dd">
            <div class="section-header">
                <h2>5. ДД (дабл деш)</h2>
            </div>
            <div class="rule-grid">
                <div class="rule-card searchable" onclick="copyCardText(this)">
                    <div class="card-top">
                        <div class="card-title">Дабл деш подряд (спидстеры)</div>
                        <span class="badge-penalty warn">Запрещено (Фол)</span>
                    </div>
                    <div class="card-desc">
                        Дабл-деш подряд (для спидстеров), который используется для уклона от финтов — запрещён, даётся фол.
                    </div>
                </div>

                <div class="rule-card searchable" onclick="copyCardText(this)">
                    <div class="card-top">
                        <div class="card-title">Правила Дешей</div>
                        <span class="badge-penalty info">Разрешено / Запрещено</span>
                    </div>
                    <div class="card-desc">
                        Два деша после двух атак — разрешено.<br><br>
                        Трипл-деш — строго запрещён.
                    </div>
                </div>
            </div>
        </section>

        <section id="audio">
            <div class="section-header">
                <h2>6. Пользовательские звуки / изображения</h2>
            </div>
            <div class="rule-grid">
                <div class="rule-card searchable" onclick="copyCardText(this)">
                    <div class="card-top">
                        <div class="card-title">Общие правила</div>
                        <span class="badge-penalty warn">Предупреждение</span>
                    </div>
                    <div class="card-desc">
                        Использование раздражающих звуковых эффектов и изображений, отвлекающих игроков, запрещено. Несоблюдение приведёт к предупреждению.
                    </div>
                </div>

                <div class="rule-card searchable" onclick="copyCardText(this)">
                    <div class="card-top">
                        <div class="card-title">Звуки ПД (Идеальное уклонение)</div>
                        <span class="badge-penalty info">На усмотрение</span>
                    </div>
                    <div class="card-desc">
                        Звуковые эффекты ПД остаются на усмотрение игроков, но может быть запрошено их удаление при создании помех.
                    </div>
                </div>

                <div class="rule-card searchable" onclick="copyCardText(this)">
                    <div class="card-top">
                        <div class="card-title">Контрудары и Ульта</div>
                        <span class="badge-penalty danger">Запрещено / Разрешено</span>
                    </div>
                    <div class="card-desc">
                        Звуки контрударов (каунтер) и посторонние изображения <strong>строго запрещены</strong>.<br><br>
                        Звуки и визуальные эффекты ультимативных способностей (ульта) <strong>разрешены</strong>.
                    </div>
                </div>
            </div>
        </section>

        <section id="title">
            <div class="section-header">
                <h2>7. Титульные бои</h2>
            </div>
            <div class="rule-grid">
                <div class="rule-card searchable" onclick="copyCardText(this)">
                    <div class="card-top">
                        <div class="card-title">Формат боев и оценивание</div>
                        <span class="badge-penalty info">Формат BO3</span>
                    </div>
                    <div class="card-desc">
                        Проводятся в формате BO3 (до 2 побед). Игрок может сменить стиль только после поражения; победитель сохраняет текущий стиль.<br><br>
                        За боем наблюдают 3 рефери по 10-балльной системе. За пассивную игру рефери могут отдать победу сопернику.
                    </div>
                </div>

                <div class="rule-card searchable" onclick="copyCardText(this)">
                    <div class="card-top">
                        <div class="card-title">Защита титулов</div>
                        <span class="badge-penalty info">Сроки защиты</span>
                    </div>
                    <div class="card-desc">
                        • <strong>ЗАЩИТА ТИТУЛА UNF:</strong> КАЖДУЮ НЕДЕЛЮ<br>
                        • <strong>ЗАЩИТА ТИТУЛА UNC:</strong> КАЖДЫЕ 2 НЕДЕЛИ<br>
                        • <strong>ЗАЩИТА ТИТУЛА UCL:</strong> КАЖДЫЕ 2.5 НЕДЕЛИ
                    </div>
                </div>
            </div>
        </section>

        <section id="combat">
            <div class="section-header">
                <h2>8. Правила проведения боев U.C.L</h2>
            </div>
            <div class="rule-grid">
                <div class="rule-card searchable" onclick="copyCardText(this)">
                    <div class="card-top">
                        <div class="card-title">Проблемы со связью и вылеты</div>
                        <span class="badge-penalty warn">5 минут дедлайн</span>
                    </div>
                    <div class="card-desc">
                        При разрыве соединения даётся ровно 5 минут на возвращение. В противном случае засчитывается технический нокаут (ТКО) или аннулирование боя.
                    </div>
                </div>

                <div class="rule-card searchable" onclick="copyCardText(this)">
                    <div class="card-top">
                        <div class="card-title">Авторитет рефери</div>
                        <span class="badge-penalty danger">Закон на ринге</span>
                    </div>
                    <div class="card-desc">
                        Вердикт судьи на ринге не обсуждается во время боя. Однако явные грубые ошибки судейства жестко караются администрацией после проверки.
                    </div>
                </div>

                <div class="rule-card searchable" onclick="copyCardText(this)">
                    <div class="card-top">
                        <div class="card-title">Суточный лимит на поединки</div>
                        <span class="badge-penalty info">Макс 3 боя</span>
                    </div>
                    <div class="card-desc">
                        Не стоит перегорать на ринге. Введено строгое ограничение: один боец имеет право провести не более 3 боев за одни сутки.
                    </div>
                </div>

                <div class="rule-card searchable" onclick="copyCardText(this)">
                    <div class="card-top">
                        <div class="card-title">Смена дивизионов и путевка наверх</div>
                        <span class="badge-penalty info">Продвижение</span>
                    </div>
                    <div class="card-desc">
                        Если вы буквально аннигилируете соперников, администрация может принудительно перевести вас в более высокий рейтинг. В обычном порядке нужно сначала завоевать чемпионский пояс текущего рейтинга и провести как минимум одну успешную защиту.
                    </div>
                </div>

                <div class="rule-card searchable" onclick="copyCardText(this)">
                    <div class="card-top">
                        <div class="card-title">Право на вызов чемпиона</div>
                        <span class="badge-penalty info">Топ-5 / Топ-1</span>
                    </div>
                    <div class="card-desc">
                        Бросить вызов действующему чемпиону могут только бойцы из первой пятерки (Топ-5) рейтинга. При этом первому номеру таблицы (Топ-1) чемпион обязан принять вызов безоговорочно!
                    </div>
                </div>
            </div>
        </section>

        <section id="bans">
            <div class="section-header">
                <h2>9. Бан стили</h2>
            </div>
            <div class="bans-flex">
                <div class="ban-box searchable" onclick="copyCardText(this)">slugger</div>
                <div class="ban-box searchable" onclick="copyCardText(this)">hawk</div>
                <div class="ban-box searchable" onclick="copyCardText(this)">hammer</div>
                <div class="ban-box searchable" onclick="copyCardText(this)">dragonfish</div>
                <div class="ban-box searchable" onclick="copyCardText(this)">white ash</div>
                <div class="ban-box searchable" onclick="copyCardText(this)">wolf</div>
                <div class="ban-box searchable" onclick="copyCardText(this)">hitman</div>
                <div class="ban-box searchable" onclick="copyCardText(this)">shotgun</div>
                <div class="ban-box searchable" onclick="copyCardText(this)">corkscrew</div>
                <div class="ban-box searchable" onclick="copyCardText(this)">bullet</div>
                <div class="ban-box searchable" onclick="copyCardText(this)">chronos</div>
                <div class="ban-box searchable" onclick="copyCardText(this)">all shinies</div>
                <div class="ban-box searchable" onclick="copyCardText(this)">exclusive styles</div>
            </div>
        </section>

    </main>

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

        // Живой отсчёт онлайна
        function simulateOnlineCounter() {
            const countElement = document.getElementById('onlineCountNumber');
            if (!countElement) return;

            let baseCount = Math.floor(Math.random() * 4) + 3;
            countElement.innerText = baseCount;

            setInterval(() => {
                let variation = Math.floor(Math.random() * 3) - 1;
                let current = parseInt(countElement.innerText) + variation;
                if (current < 1) current = 1;
                countElement.innerText = current;
            }, 7000);
        }
        simulateOnlineCounter();
    </script>
</body>
</html>
