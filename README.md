<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>U.C.L — Официальные Правила Боёв</title>
    <link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@400;500;600;700;800;900&family=Teko:wght@500;600;700&display=swap" rel="stylesheet">
    <style>
        :root {
            --bg-primary: #0a0c14;
            --bg-secondary: #121624;
            --bg-card: #181d2e;
            --bg-card-hover: #1f253d;
            --accent: #f39c12;
            --accent-glow: rgba(243, 156, 18, 0.3);
            --danger: #e74c3c;
            --danger-glow: rgba(231, 76, 60, 0.3);
            --success: #2ecc71;
            --info: #3498db;
            --text-main: #f0f3f8;
            --text-muted: #94a3b8;
            --border-color: #2a3450;
            --transition: all 0.3s ease;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }

        body {
            font-family: 'Montserrat', sans-serif;
            background-color: var(--bg-primary);
            color: var(--text-main);
            line-height: 1.6;
            overflow-x: hidden;
        }

        /* Header & Hero Section */
        header {
            position: relative;
            background: linear-gradient(135deg, rgba(18, 22, 36, 0.95), rgba(10, 12, 20, 0.98)), url('https://images.unsplash.com/photo-1542751371-adc38448a05e?auto=format&fit=crop&w=1920&q=80') center/cover no-repeat;
            border-bottom: 2px solid var(--accent);
            padding: 60px 20px 40px;
            text-align: center;
        }

        .hero-container {
            max-width: 1000px;
            margin: 0 auto;
        }

        .logo-badge {
            display: inline-block;
            background: var(--accent);
            color: #000;
            font-family: 'Teko', sans-serif;
            font-size: 1.5rem;
            font-weight: 700;
            padding: 2px 20px;
            border-radius: 4px;
            margin-bottom: 15px;
            letter-spacing: 2px;
            text-transform: uppercase;
            box-shadow: 0 0 15px var(--accent-glow);
        }

        h1 {
            font-family: 'Teko', sans-serif;
            font-size: 4.5rem;
            text-transform: uppercase;
            letter-spacing: 3px;
            color: #fff;
            margin-bottom: 10px;
            line-height: 1;
            text-shadow: 0 5px 15px rgba(0,0,0,0.5);
        }

        h1 span {
            color: var(--accent);
        }

        .subtitle {
            font-size: 1.1rem;
            color: var(--text-muted);
            max-width: 700px;
            margin: 0 auto 30px;
        }

        /* Quick Navigation Tabs */
        .nav-tabs {
            display: flex;
            justify-content: center;
            gap: 12px;
            flex-wrap: wrap;
            margin-top: 25px;
        }

        .nav-tab {
            background: var(--bg-secondary);
            border: 1px solid var(--border-color);
            color: var(--text-main);
            padding: 10px 20px;
            border-radius: 6px;
            cursor: pointer;
            font-weight: 600;
            font-size: 0.95rem;
            transition: var(--transition);
            text-decoration: none;
        }

        .nav-tab:hover, .nav-tab.active {
            background: var(--accent);
            color: #000;
            border-color: var(--accent);
            box-shadow: 0 0 10px var(--accent-glow);
        }

        /* Main Container */
        .container {
            max-width: 1200px;
            margin: 40px auto;
            padding: 0 20px;
        }

        section {
            margin-bottom: 50px;
        }

        .section-header {
            display: flex;
            align-items: center;
            gap: 15px;
            margin-bottom: 25px;
            border-bottom: 2px solid var(--border-color);
            padding-bottom: 12px;
        }

        .section-header h2 {
            font-family: 'Teko', sans-serif;
            font-size: 2.5rem;
            letter-spacing: 2px;
            color: #fff;
            text-transform: uppercase;
        }

        .section-header .icon {
            font-size: 2rem;
        }

        /* Grid Layout for Rules */
        .rules-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(360px, 1fr));
            gap: 25px;
        }

        .rule-card {
            background: var(--bg-card);
            border: 1px solid var(--border-color);
            border-radius: 12px;
            padding: 25px;
            transition: var(--transition);
            position: relative;
            overflow: hidden;
            display: flex;
            flex-direction: column;
            justify-content: space-between;
        }

        .rule-card:hover {
            border-color: var(--accent);
            transform: translateY(-4px);
            box-shadow: 0 10px 25px rgba(0,0,0,0.4);
            background: var(--bg-card-hover);
        }

        .rule-card.danger-border {
            border-left: 4px solid var(--danger);
        }

        .rule-card.warning-border {
            border-left: 4px solid var(--accent);
        }

        .rule-card.info-border {
            border-left: 4px solid var(--info);
        }

        .card-top {
            margin-bottom: 15px;
        }

        .rule-title {
            font-size: 1.35rem;
            font-weight: 700;
            color: #fff;
            margin-bottom: 8px;
            display: flex;
            align-items: center;
            justify-content: space-between;
        }

        .penalty-badge {
            font-size: 0.75rem;
            padding: 3px 8px;
            border-radius: 4px;
            font-weight: 700;
            text-transform: uppercase;
        }

        .penalty-badge.warning {
            background: rgba(243, 156, 18, 0.2);
            color: var(--accent);
            border: 1px solid var(--accent);
        }

        .penalty-badge.danger {
            background: rgba(231, 76, 60, 0.2);
            color: var(--danger);
            border: 1px solid var(--danger);
        }

        .rule-desc {
            font-size: 0.95rem;
            color: var(--text-muted);
            margin-bottom: 15px;
        }

        /* Rookie vs Pro Boxes */
        .guide-box {
            background: rgba(18, 22, 36, 0.7);
            border-radius: 8px;
            padding: 12px 15px;
            margin-top: 10px;
            font-size: 0.9rem;
            border: 1px dashed var(--border-color);
        }

        .guide-box.rookie {
            border-color: rgba(52, 152, 219, 0.4);
        }

        .guide-box.pro {
            border-color: rgba(46, 204, 113, 0.4);
        }

        .guide-title {
            font-weight: 700;
            font-size: 0.85rem;
            text-transform: uppercase;
            letter-spacing: 1px;
            margin-bottom: 4px;
            display: flex;
            align-items: center;
            gap: 6px;
        }

        .guide-box.rookie .guide-title {
            color: var(--info);
        }

        .guide-box.pro .guide-title {
            color: var(--success);
        }

        /* Ban Styles List */
        .bans-container {
            background: var(--bg-card);
            border: 1px solid var(--border-color);
            border-radius: 12px;
            padding: 30px;
        }

        .bans-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(220px, 1fr));
            gap: 15px;
            margin-top: 20px;
        }

        .ban-item {
            background: rgba(231, 76, 60, 0.1);
            border: 1px solid rgba(231, 76, 60, 0.3);
            border-radius: 8px;
            padding: 12px 16px;
            font-weight: 600;
            color: #ff8080;
            display: flex;
            align-items: center;
            gap: 10px;
            transition: var(--transition);
        }

        .ban-item:hover {
            background: rgba(231, 76, 60, 0.2);
            border-color: var(--danger);
        }

        /* Tournament Combat Rules Cards */
        .combat-rules-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(340px, 1fr));
            gap: 25px;
        }

        /* Footer */
        footer {
            background: var(--bg-secondary);
            border-top: 1px solid var(--border-color);
            text-align: center;
            padding: 30px 20px;
            color: var(--text-muted);
            font-size: 0.9rem;
            margin-top: 60px;
        }

        footer span {
            color: var(--accent);
            font-weight: 700;
        }

        /* Responsive */
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }

        .rule-card {
            animation: fadeIn 0.5s ease forwards;
        }
    </style>
</head>
<body>

    <header>
        <div class="hero-container">
            <div class="logo-badge">Official Rules & Regulations</div>
            <h1>Правила боёв <span>U.C.L</span></h1>
            <p class="subtitle">Полный свод регламента соревнований по боям. Разбор для новичков и профессиональные тактические нюансы.</p>
            
            <div class="nav-tabs">
                <a href="#pd" class="nav-tab">ПД Фишинг</a>
                <a href="#bugs" class="nav-tab">Багоюз</a>
                <a href="#combos" class="nav-tab">Медленные M1</a>
                <a href="#skating" class="nav-tab">С-кейтинг & Бекдеши</a>
                <a href="#audio" class="nav-tab">Звуки / Эффекты</a>
                <a href="#combat" class="nav-tab">Проведение боёв</a>
                <a href="#bans" class="nav-tab">Бан-стили</a>
            </div>
        </div>
    </header>

    <main class="container">

        <!-- СЕКЦИЯ 1: ПД ФИШИНГ -->
        <section id="pd">
            <div class="section-header">
                <span class="icon">⏱️</span>
                <h2>1. ПД Фишинг (Пассивное уклонение)</h2>
            </div>
            <div class="rules-grid">
                <div class="rule-card warning-border">
                    <div class="card-top">
                        <div class="rule-title">
                            Базовое понятие ПД Фишинга
                            <span class="penalty-badge warning">Фол / Предупреждение</span>
                        </div>
                        <div class="rule-desc">
                            Это когда игрок намеренно перестает бить/взаимодействовать, чтобы сделать идеальное уклонение (пассивное ожидание).
                        </div>
                    </div>
                    <div>
                        <div class="guide-box rookie">
                            <div class="guide-title">👶 Для новичков:</div>
                            Не стой столбом и не жди пока противник ударит, чтобы сделать красивый уклон. За это дают предупреждения.
                        </div>
                        <div class="guide-box pro">
                            <div class="guide-title">⚡ Для профи:</div>
                            Разрешено сделать два уклона подряд, если вас поймали на стагеринге или вы в безвыходном положении против спамящих комбо (особенно медленных стилей).
                        </div>
                    </div>
                </div>

                <div class="rule-card warning-border">
                    <div class="card-top">
                        <div class="rule-title">
                            Таймер порога (2.5 секунды)
                            <span class="penalty-badge warning">Фол за злоупотребление</span>
                        </div>
                        <div class="rule-desc">
                            Ждать удара можно максимум 2.5 секунды. Случайный выход за рамки — предупреждение, системное злоупотребление — фол. Правило также касается демпси ролла.
                        </div>
                    </div>
                    <div>
                        <div class="guide-box rookie">
                            <div class="guide-title">👶 Для новичков:</div>
                            Если вы зажались в угол и ждете дольше 2.5 секунд — это нарушение. Таймер также распространяется на «демпси ролл».
                        </div>
                        <div class="guide-box pro">
                            <div class="guide-title">⚡ Для профи:</div>
                            Таймер сбрасывается попыткой удара с получением контрудара, атакой, способностями возврата в нейтраль. Использование эмоций (кроме начала раунда) трактуется как попытка ПД!
                        </div>
                    </div>
                </div>

                <div class="rule-card warning-border">
                    <div class="card-top">
                        <div class="rule-title">
                            Правило дистанции
                            <span class="penalty-badge warning">Фол обоим</span>
                        </div>
                        <div class="rule-desc">
                            Если после таймера ПД оба игрока намеренно держатся на расстоянии, включается дополнительный 3-секундный счёт.
                        </div>
                    </div>
                    <div>
                        <div class="guide-box rookie">
                            <div class="guide-title">👶 Для новичков:</div>
                            Если вы оба отбежали друг от друга и никто не сближается — арбитр включит отсчет. Сближайтесь!
                        </div>
                        <div class="guide-box pro">
                            <div class="guide-title">⚡ Для профи:</div>
                            Если за 3 секунды после ПД-порога никто не идет на сближение — фол засчитывается обоим бойцам.
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- СЕКЦИЯ 2: БАГОЮЗ -->
        <section id="bugs">
            <div class="section-header">
                <span class="icon">🚫</span>
                <h2>2. Запрещенный багоюз</h2>
            </div>
            <div class="rules-grid">
                <div class="rule-card danger-border">
                    <div class="card-top">
                        <div class="rule-title">
                            Парирование ульты
                            <span class="penalty-badge danger">Вылет из реал. жизни</span>
                        </div>
                        <div class="rule-desc">
                            Прожатие блока в точный тайминг при летящей ульте, из-за чего она «сжирается» без урона.
                        </div>
                    </div>
                    <div>
                        <div class="guide-box rookie">
                            <div class="guide-title">👶 Для новичков:</div>
                            Строго запрещено пытаться заблокировать ультимейт багом таймингов блока.
                        </div>
                        <div class="guide-box pro">
                            <div class="guide-title">⚡ Для профи:</div>
                            Намеренное использование карается жестчайшими санкциями вплоть до дисквалификации.
                        </div>
                    </div>
                </div>

                <div class="rule-card danger-border">
                    <div class="card-top">
                        <div class="rule-title">
                            Нелегальный стаггеринг
                            <span class="penalty-badge warning">Предупреждение ➔ Фол</span>
                        </div>
                        <div class="rule-desc">
                            Ситуация, когда M1 удар регистрируется в серии, но задерживается, становится неуклоняемым и притягивает игрока вопреки кадрам уклонения.
                        </div>
                    </div>
                    <div>
                        <div class="guide-box rookie">
                            <div class="guide-title">👶 Для новичков:</div>
                            Если удар «липнет» к вам нечестным образом — это баг стаггеринга. Первое нарушение — устное предупреждение.
                        </div>
                        <div class="guide-box pro">
                            <div class="guide-title">⚡ Для профи:</div>
                            Обычный стаггеринг (тычки M1 для сбития темпа или миксапов) полностью разрешен! Наказывается именно «залипающий» нелегальный баг.
                        </div>
                    </div>
                </div>

                <div class="rule-card danger-border">
                    <div class="card-top">
                        <div class="rule-title">
                            Залипающие комбо
                            <span class="penalty-badge danger">Запрещено</span>
                        </div>
                        <div class="rule-desc">
                            Атаки, от которых невозможно увернуться (по типу смеша: M2, M1+M2).
                        </div>
                    </div>
                    <div>
                        <div class="guide-box rookie">
                            <div class="guide-title">👶 Для новичков:</div>
                            Неуклоняемые спам-комбо типа смешей (уже официально пофиксили в игре).
                        </div>
                        <div class="guide-box pro">
                            <div class="guide-title">⚡ Для профи:</div>
                            Эксплуатация старых уязвимостей движка пресекается мгновенно.
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- СЕКЦИЯ 3: МЕДЛЕННЫЕ КОМБО М1 -->
        <section id="combos">
            <div class="section-header">
                <span class="icon">🐢</span>
                <h2>3. Медленные комбо М1 (Слоу клики)</h2>
            </div>
            <div class="rules-grid">
                <div class="rule-card warning-border">
                    <div class="card-top">
                        <div class="rule-title">
                            Правила использования слоу кликов
                            <span class="penalty-badge warning">Фол за превышение</span>
                        </div>
                        <div class="rule-desc">
                            Медленные M1 разрешены <strong>только после попадания под ультимейт</strong>. Нельзя использовать после способностей (Focus, Stampede и т.д.).
                        </div>
                    </div>
                    <div>
                        <div class="guide-box rookie">
                            <div class="guide-title">👶 Для новичков:</div>
                            Просто так замедлять удары M1 нельзя. Только после того, как в вас прилетел ультимейт соперника.
                        </div>
                        <div class="guide-box pro">
                            <div class="guide-title">⚡ Для профи:</div>
                            Разрешено использовать слоу клики ровно для <strong>ОДНОЙ СЕРИИ УДАРОВ</strong>. Большее количество — фол.
                        </div>
                    </div>
                </div>

                <div class="rule-card info-border">
                    <div class="card-top">
                        <div class="rule-title">
                            Исключения для стилей
                            <span class="penalty-badge warning">Важные нюансы</span>
                        </div>
                        <div class="rule-desc">
                            Особенности баланса для конкретных боевых стилей после получения ульты.
                        </div>
                    </div>
                    <div>
                        <div class="guide-box rookie">
                            <div class="guide-title">👶 Для новичков:</div>
                            Стиль «Крюк» не имеет права использовать слоу клики даже после ульты.
                        </div>
                        <div class="guide-box pro">
                            <div class="guide-title">⚡ Для профи:</div>
                            Стиль «Айрон Фист» после ультимейта имеет право на выполнение ровно <strong>ДВУХ КОМБО</strong> слоу кликов.
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- СЕКЦИЯ 4: С-КЕЙТИНГ И БЕКДЕШИ -->
        <section id="skating">
            <div class="section-header">
                <span class="icon">⛸️</span>
                <h2>4. С-кейтинг, Бекдеши и ДД</h2>
            </div>
            <div class="rules-grid">
                <div class="rule-card warning-border">
                    <div class="card-top">
                        <div class="rule-title">
                            С-кейтинг и пассивный отход
                            <span class="penalty-badge warning">Фол</span>
                        </div>
                        <div class="rule-desc">
                            Уход назад зажатием клавиши S (направление назад). Разрешен только сразу после удачного попадания комбо.
                        </div>
                    </div>
                    <div>
                        <div class="guide-box rookie">
                            <div class="guide-title">👶 Для новичков:</div>
                            Нельзя просто идти назад и пассивно пропускать атаки соперника.
                        </div>
                        <div class="guide-box pro">
                            <div class="guide-title">⚡ Для профи:</div>
                            Если вы идете назад ничего не делая и пропускаете два действия противника — фол. Против демпси фишить можно, но С-кейтить назад нельзя. Против шотгана бекдеш на способность разрешен, если предшествовал обычный бекдеш.
                        </div>
                    </div>
                </div>

                <div class="rule-card warning-border">
                    <div class="card-top">
                        <div class="rule-title">
                            ДД (Дабл деш) правила
                            <span class="penalty-badge danger">Запреты / Разрешения</span>
                        </div>
                        <div class="rule-desc">
                            Регламент использования двойных и тройных рывков.
                        </div>
                    </div>
                    <div>
                        <div class="guide-box rookie">
                            <div class="guide-title">👶 For Beginners:</div>
                            Трипл-деш (три рывка) запрещен везде. Два деша подряд у спидстеров для уклона от финтов запрещены.
                        </div>
                        <div class="guide-box pro">
                            <div class="guide-title">⚡ Для профи:</div>
                            Разрешено делать ровно два деша после завершения двух атак. Дабл-деш подряд для уклонения от финтов карается фолом.
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- СЕКЦИЯ 5: ПОЛЬЗОВАТЕЛЬСКИЕ ЗВУКИ И ИЗОБРАЖЕНИЯ -->
        <section id="audio">
            <div class="section-header">
                <span class="icon">🎨</span>
                <h2>5. Кастомные звуки и изображения</h2>
            </div>
            <div class="rules-grid">
                <div class="rule-card warning-border">
                    <div class="card-top">
                        <div class="rule-title">
                            Звуки ПД (Идеального уклонения)
                            <span class="penalty-badge warning">На усмотрение судей</span>
                        </div>
                        <div class="rule-desc">
                            Кастомные звуки ПД остаются допустимыми, но судья может запросить их удаление во избежание нечестного преимущества от отвлечения.
                        </div>
                    </div>
                    <div>
                        <div class="guide-box rookie">
                            <div class="guide-title">👶 Для новичков:</div>
                            Ставьте кастомные звуки уклона аккуратно, чтобы они не мешали честной игре.
                        </div>
                    </div>
                </div>

                <div class="rule-card danger-border">
                    <div class="card-top">
                        <div class="rule-title">
                            Каунтеры (Контрудары) и Картинки
                            <span class="penalty-badge danger">Строго запрещено</span>
                        </div>
                        <div class="rule-desc">
                            Пользовательские звуковые эффекты каунтеров, а также любые кастомные изображения строго запрещены для официальных матчей.
                        </div>
                    </div>
                    <div>
                        <div class="guide-box rookie">
                            <div class="guide-title">👶 Для новичков:</div>
                            Уберите кастомные картинки и звуки контрударов перед матчем — они под запретом.
                        </div>
                        <div class="guide-box pro">
                            <div class="guide-title">⚡ Для профи:</div>
                            Кастомные звуки и картинки <strong>ультимативных способностей (ульт)</strong> разрешены без ограничений.
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- СЕКЦИЯ 6: ПРАВИЛА ПРОВЕДЕНИЯ БОЕВ U.C.L -->
        <section id="combat">
            <div class="section-header">
                <span class="icon">🏟️</span>
                <h2>6. Регламент проведения боёв U.C.L</h2>
            </div>
            <div class="combat-rules-grid">
                <div class="rule-card info-border">
                    <div class="card-top">
                        <div class="rule-title">🌐 Связь и вылеты</div>
                        <div class="rule-desc">
                            Если посреди матча пропало соединение или вылетела игра, дается ровно <strong>5 минут</strong> на возвращение. Иначе — аннулирование или технический нокаут (ТКО) по решению рефери.
                        </div>
                    </div>
                </div>

                <div class="rule-card info-border">
                    <div class="card-top">
                        <div class="rule-title">⚖️ Авторитет рефери</div>
                        <div class="rule-desc">
                            Вердикт судьи на ринге — закон во время боя. Споры запрещены. Однако грубые ошибки судей фиксируются и жестко караются администрацией после проверки.
                        </div>
                    </div>
                </div>

                <div class="rule-card info-border">
                    <div class="card-top">
                        <div class="rule-title">📅 Суточный лимит боёв</div>
                        <div class="rule-desc">
                            Чтобы бойцы не перегорали, введено строгое ограничение: один боец имеет право провести <strong>не более 3 боёв за одни сутки</strong>.
                        </div>
                    </div>
                </div>

                <div class="rule-card info-border">
                    <div class="card-top">
                        <div class="rule-title">📈 Смена дивизионов</div>
                        <div class="rule-desc">
                            При явном доминировании администрация может перевести вас выше принудительно. В стандартном порядке: завоюйте чемпионский пояс и проведите минимум 1 успешную защиту.
                        </div>
                    </div>
                </div>

                <div class="rule-card info-border">
                    <div class="card-top">
                        <div class="rule-title">👑 Вызов чемпиона</div>
                        <div class="rule-desc">
                            Бросить вызов королю могут только бойцы из <strong>Топ-5</strong> рейтинга. Боец из Топ-1 обладает эксклюзивным правом — чемпион обязан принять его вызов безоговорочно!
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- СЕКЦИЯ 7: БАН СТИЛИ -->
        <section id="bans">
            <div class="section-header">
                <span class="icon">❌</span>
                <h2>7. Список бан-стилей</h2>
            </div>
            <div class="bans-container">
                <p style="color: var(--text-muted); margin-bottom: 15px;">Следующие боевые стили (включая все их шайни/блестящие версии и эксклюзивные вариации) полностью запрещены на официальных турнирах:</p>
                <div class="bans-grid">
                    <div class="ban-item">🥊 Слаггер (Slugger)</div>
                    <div class="ban-item">🦅 Хоук (Hawk)</div>
                    <div class="ban-item">🔄 Свитч Хит (Switch Hit)</div>
                    <div class="ban-item">🔨 Хаммер (Hammer)</div>
                    <div class="ban-item">🐟 Драгонфиш (Dragonfish)</div>
                    <div class="ban-item">⚡ Вайт Эш (White Ash)</div>
                    <div class="ban-item">🐺 Вульф (Wolf)</div>
                    <div class="ban-item">🌀 Крюк (без слоу кликов)</div>
                    <div class="ban-item">🎯 Буллет (Bullet)</div>
                    <div class="ban-item">⏳ Хронос (без эмоций)</div>
                </div>
            </div>
        </section>

    </main>

    <footer>
        <p>Официальный регламент лиги <span>U.C.L Combat Rules</span>. Создано для игроков и профессионалов.</p>
    </footer>

</body>
</html>
