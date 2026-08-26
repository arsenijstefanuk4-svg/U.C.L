<!DOCTYPE html>
<html lang="ru">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>U.C.L. Official Rules & Hub</title>
  <link href="https://fonts.googleapis.com/css2?family=Teko:wght@600;700&family=Montserrat:wght@400;600;800;900&display=swap" rel="stylesheet">
  <style>
    :root {
      --accent-color: #ff1e27;
      --glow-color: rgba(255, 30, 39, 0.5);
      --bg-main: #060608;
      --bg-card: rgba(18, 18, 24, 0.85);
      --accent-gold: #ffb703;
      --text-main: #f0f0f5;
      --text-muted: #8a8a9e;
      --border-color: rgba(255, 255, 255, 0.1);
      --anim-speed: 0.3s;
    }

    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }

    body {
      background-color: var(--bg-main);
      color: var(--text-main);
      font-family: 'Montserrat', sans-serif;
      line-height: 1.6;
      overflow-x: hidden;
      min-height: 100vh;
    }

    .ring-bg {
      position: fixed;
      top: 0;
      left: 0;
      width: 100vw;
      height: 100vh;
      z-index: -1;
      pointer-events: none;
      background: 
        radial-gradient(circle at 50% 30%, var(--glow-color), transparent 70%),
        linear-gradient(to bottom, rgba(6,6,8,0.9), #060608);
    }

    #loader {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: #060608;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      z-index: 9999;
      transition: opacity 0.5s ease, visibility 0.5s;
    }

    .gloves-clash {
      display: flex;
      align-items: center;
      font-size: 4rem;
      gap: 10px;
      margin-bottom: 20px;
    }

    .glove-left {
      animation: clash-left 0.8s infinite alternate ease-in-out;
    }

    .glove-right {
      transform: scaleX(-1);
      animation: clash-right 0.8s infinite alternate ease-in-out;
    }

    @keyframes clash-left {
      0% { transform: translateX(-40px) rotate(-20deg); }
      100% { transform: translateX(10px) rotate(0deg); }
    }

    @keyframes clash-right {
      0% { transform: scaleX(-1) translateX(-40px) rotate(-20deg); }
      100% { transform: scaleX(-1) translateX(10px) rotate(0deg); }
    }

    .loader-title {
      font-family: 'Teko', sans-serif;
      font-size: 2.5rem;
      letter-spacing: 3px;
      color: var(--accent-color);
      text-shadow: 0 0 15px var(--glow-color);
    }

    .loader-bar {
      width: 200px;
      height: 4px;
      background: rgba(255,255,255,0.1);
      border-radius: 2px;
      overflow: hidden;
      margin-top: 15px;
    }

    .loader-progress {
      width: 0%;
      height: 100%;
      background: var(--accent-color);
      box-shadow: 0 0 10px var(--glow-color);
      animation: load 2.5s forwards ease-in-out;
    }

    @keyframes load {
      100% { width: 100%; }
    }

    header {
      background: rgba(12, 12, 16, 0.85);
      backdrop-filter: blur(15px);
      border-bottom: 1px solid var(--border-color);
      padding: 1.5rem 1rem;
      position: sticky;
      top: 0;
      z-index: 100;
    }

    .header-container {
      max-width: 1000px;
      margin: 0 auto;
      display: flex;
      flex-direction: column;
      align-items: center;
      gap: 15px;
    }

    .logo {
      font-family: 'Teko', sans-serif;
      font-size: 3.2rem;
      font-weight: 700;
      text-transform: uppercase;
      letter-spacing: 4px;
      color: #fff;
      text-shadow: 0 0 15px var(--glow-color);
      display: flex;
      align-items: center;
      gap: 10px;
      text-align: center;
    }

    .logo span {
      color: var(--accent-color);
    }

    .controls-panel {
      width: 100%;
      display: flex;
      flex-wrap: wrap;
      gap: 10px;
      justify-content: center;
      align-items: center;
    }

    .search-box {
      flex: 1;
      min-width: 260px;
      position: relative;
    }

    .search-box input {
      width: 100%;
      padding: 12px 20px 12px 42px;
      background: rgba(0, 0, 0, 0.6);
      border: 1px solid var(--border-color);
      border-radius: 10px;
      color: #fff;
      font-size: 0.95rem;
      outline: none;
      transition: all var(--anim-speed);
    }

    .search-box input:focus {
      border-color: var(--accent-color);
      box-shadow: 0 0 10px var(--glow-color);
    }

    .search-icon {
      position: absolute;
      left: 14px;
      top: 50%;
      transform: translateY(-50%);
      color: var(--text-muted);
    }

    .btn {
      background: rgba(255, 255, 255, 0.05);
      border: 1px solid var(--border-color);
      color: #fff;
      padding: 12px 16px;
      border-radius: 10px;
      font-weight: 700;
      cursor: pointer;
      display: flex;
      align-items: center;
      gap: 6px;
      font-size: 0.85rem;
      text-transform: uppercase;
      transition: all var(--anim-speed);
    }

    .btn:hover {
      border-color: var(--accent-color);
      box-shadow: 0 0 10px var(--glow-color);
    }

    .settings-drawer {
      width: 100%;
      max-width: 1000px;
      background: rgba(20, 20, 28, 0.95);
      border: 1px solid var(--border-color);
      border-radius: 12px;
      padding: 15px;
      margin: 15px auto 0;
      display: flex;
      flex-wrap: wrap;
      gap: 20px;
      align-items: center;
      justify-content: space-around;
    }

    .setting-item {
      display: flex;
      align-items: center;
      gap: 10px;
      font-weight: 600;
      font-size: 0.9rem;
    }

    .color-picker {
      -webkit-appearance: none;
      border: none;
      width: 32px;
      height: 32px;
      border-radius: 50%;
      cursor: pointer;
      background: transparent;
    }

    .color-picker::-webkit-color-swatch-wrapper {
      padding: 0;
    }

    .color-picker::-webkit-color-swatch {
      border: 2px solid #fff;
      border-radius: 50%;
    }

    main {
      max-width: 1000px;
      margin: 25px auto;
      padding: 0 15px;
    }

    .rules-grid {
      display: flex;
      flex-direction: column;
      gap: 20px;
    }

    .rule-card {
      background: var(--bg-card);
      backdrop-filter: blur(10px);
      border: 1px solid var(--border-color);
      border-left: 4px solid var(--accent-color);
      border-radius: 14px;
      padding: 22px 25px;
      position: relative;
      overflow: hidden;
      transition: transform 0.3s ease, border-color 0.3s ease, box-shadow 0.3s ease;
    }

    .anim-enabled .rule-card:hover {
      transform: translateY(-4px);
      border-color: var(--accent-color);
      box-shadow: 0 8px 25px rgba(0, 0, 0, 0.5), 0 0 15px var(--glow-color);
    }

    .rule-card.title-card {
      border-left-color: var(--accent-gold);
    }

    .rule-card.ban-card {
      border-left-color: #ff0055;
      background: linear-gradient(135deg, var(--bg-card) 0%, rgba(255, 0, 85, 0.08) 100%);
    }

    .card-header {
      display: flex;
      align-items: center;
      gap: 15px;
      margin-bottom: 12px;
      border-bottom: 1px solid var(--border-color);
      padding-bottom: 10px;
    }

    .card-number {
      font-family: 'Teko', sans-serif;
      font-size: 2.2rem;
      color: var(--accent-color);
      line-height: 1;
      font-weight: 700;
    }

    .rule-card.title-card .card-number {
      color: var(--accent-gold);
    }

    .card-title {
      font-size: 1.3rem;
      font-weight: 800;
      text-transform: uppercase;
      letter-spacing: 1px;
    }

    .card-content p {
      margin-bottom: 10px;
      color: var(--text-main);
      font-size: 0.95rem;
      word-wrap: break-word;
    }

    .card-content ul {
      list-style-position: inside;
      margin-left: 5px;
      margin-bottom: 10px;
    }

    .card-content li {
      margin-bottom: 6px;
      font-size: 0.95rem;
      word-wrap: break-word;
    }

    .highlight-bold {
      font-weight: 800;
      color: #fff;
    }

    .exception-block {
      background: rgba(255, 183, 3, 0.08);
      border: 1px solid rgba(255, 183, 3, 0.3);
      border-left: 4px solid var(--accent-gold);
      padding: 12px 15px;
      border-radius: 8px;
      margin-top: 10px;
      font-size: 0.9rem;
    }

    .protection-schedule {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(180px, 1fr));
      gap: 12px;
      margin-top: 15px;
    }

    .schedule-item {
      background: rgba(0,0,0,0.4);
      padding: 12px;
      border-radius: 10px;
      border: 1px solid var(--border-color);
      text-align: center;
      font-weight: 700;
      font-size: 0.85rem;
    }

    .schedule-item span {
      color: var(--accent-gold);
      display: block;
      font-size: 1rem;
      margin-top: 4px;
    }

    .ban-list {
      display: flex;
      flex-wrap: wrap;
      gap: 8px;
      margin-top: 12px;
    }

    .ban-tag {
      background: rgba(255, 30, 39, 0.12);
      border: 1px solid rgba(255, 30, 39, 0.4);
      color: #fff;
      padding: 5px 12px;
      border-radius: 6px;
      font-size: 0.85rem;
      font-weight: 700;
      text-transform: uppercase;
      word-break: break-all;
    }

    .hidden {
      display: none !important;
    }

    @media (max-width: 600px) {
      .logo {
        font-size: 2.2rem;
      }
      
      .controls-panel {
        flex-direction: column;
      }

      .search-box, .btn {
        width: 100%;
      }

      .rule-card {
        padding: 15px;
      }

      .card-title {
        font-size: 1.1rem;
      }

      .card-number {
        font-size: 1.8rem;
      }

      .settings-drawer {
        flex-direction: column;
        align-items: flex-start;
      }
    }

    footer {
      text-align: center;
      padding: 25px;
      color: var(--text-muted);
      border-top: 1px solid var(--border-color);
      margin-top: 40px;
      font-size: 0.85rem;
    }
  </style>
</head>
<body class="anim-enabled">

  <div id="loader">
    <div class="gloves-clash">
      <span class="glove-left">🥊</span>
      <span class="glove-right">🥊</span>
    </div>
    <div class="loader-title">U.C.L. LEAGUE HUB</div>
    <div class="loader-bar">
      <div class="loader-progress"></div>
    </div>
  </div>

  <div class="ring-bg"></div>

  <header>
    <div class="header-container">
      <div class="logo">
        🥊 UCL <span>RULES</span> 🥊
      </div>
      
      <div class="controls-panel">
        <div class="search-box">
          <span class="search-icon">🔍</span>
          <input type="text" id="searchInput" placeholder="Поиск по правилам...">
        </div>
        <button class="btn" id="toggleSettings">⚙️ Настройки</button>
        <button class="btn" id="animToggle">⚡ Анимации</button>
      </div>

      <div class="settings-drawer hidden" id="settingsDrawer">
        <div class="setting-item">
          <span>Цвет акцента:</span>
          <input type="color" id="accentPicker" class="color-picker" value="#ff1e27">
        </div>
      </div>
    </div>
  </header>

  <main>
    <div class="rules-grid" id="rulesGrid">

      <article class="rule-card" data-keywords="пассив пд фишинг уклонение стаггеринг демпси ролл эмоции ульта стамина">
        <div class="card-header">
          <div class="card-number">01</div>
          <h2 class="card-title">Пассив</h2>
        </div>
        <div class="card-content">
          <p><span class="highlight-bold">ПД Фишинг</span> — это когда игрок намеренно перестает бить/взаимодействовать, чтобы сделать идеальное уклонение.</p>
          <p>Если вас ловят на стагеринге или вы ничего не можете сделать кроме уклона то можете выждать момент и сделать два уклона если по вам делают спамящие комбо (особенно касается медленных стилей).</p>
          <p>Ждать удара можно максимум <span class="highlight-bold">2,5 секунды</span>, вы можете случайно выйти за рамки времени и будет только предупреждение, но если вы злоупотребляете этим то получите фол. Это касается и демпси ролла - вы не можете злоупотреблять им больше чем <span class="highlight-bold">2,5 секунды</span>.</p>
          <p>Попытка удара и получение контрудара сбрасывают таймер порога <span class="highlight-bold">ПД фиша</span> (таймер 2,5 секунды). Также атака и способности которые возвращают бойцов на нейтральное положение тоже сбрасывает таймер. Использование эмоций будет приравниваться к бездействию (кроме начала раунда).</p>
          <p>Если вы пассивите или пдфишите в конце боя чтобы нанести ульту это приравнивается как два фола. Пдфишить можно когда у бойца закончилась стамина ПОЛНОСТЬЮ.</p>
          <p>Если вы первым ждёте удар и пдфишите больше двух раз, даже если делаете это в таймер пдфиша (2.5 секунды), то даётся фол.</p>
        </div>
      </article>

      <article class="rule-card" data-keywords="запрещенные механики парирование ульты нелегальный стаггеринг m1 миксап фол">
        <div class="card-header">
          <div class="card-number">02</div>
          <h2 class="card-title">Использование багов (Запрещенные механики)</h2>
        </div>
        <div class="card-content">
          <p>Запрещены следующие уязвимости:</p>
          <ul>
            <li><span class="highlight-bold">Парирование ульты</span> — когда в вас летит ультимативная способность, которая должна пробить блок, и вы в тайминг прожимаете блок для её отмены (при намеренном использовании игрок дисквалифицируется с турнира).</li>
          </ul>
          <p><span class="highlight-bold">Нелегальный стаггеринг</span> — ситуация, когда удар M1 все еще регистрируется в серии, но задерживается и становится неуклоняемым, притягивая игрока обратно вопреки анимации.</p>
          <ul>
            <li><span class="highlight-bold">Стаггеринг</span> с целью смены темпа или миксапов разрешен.</li>
            <li>Первое нарушение влечет за собой предупреждение. Последующие приведут к фолу.</li>
          </ul>
        </div>
      </article>

      <article class="rule-card" data-keywords="медленные комбо m1 слоу клики ультимейт focus stampede крюк айрон фист">
        <div class="card-header">
          <div class="card-number">03</div>
          <h2 class="card-title">Медленные комбо М1 (слоу клики)</h2>
        </div>
        <div class="card-content">
          <p>Медленные удары <span class="highlight-bold">M1</span> разрешены только после того, как игрок попал под ультимейт. Медленные <span class="highlight-bold">M1</span> нельзя использовать после способностей (например, <span class="highlight-bold">Focus, Stampede</span> и т. д.). Игрокам разрешено использовать медленные M1 только для <span class="highlight-bold">ОДНОЙ СЕРИИ УДАРОВ</span>, большее количество приведет к фолу.</p>
          <div class="exception-block">
            <span class="highlight-bold">ИСКЛЮЧЕНИЕ:</span> нельзя использовать стилю Крюк слоу клики после ультимейта. После ультимейта Айрон Фиста можно делать <span class="highlight-bold">ДВА КОМБО СЛОУ КЛИКА</span>.
          </div>
        </div>
      </article>

      <article class="rule-card" data-keywords="с-кейтинг бекдеш s демпси шотган фол дистанция">
        <div class="card-header">
          <div class="card-number">04</div>
          <h2 class="card-title">С-кейтинг и бекдеши</h2>
        </div>
        <div class="card-content">
          <p><span class="highlight-bold">С-кейтинг</span> — уход назад от противника зажатием кнопки S (направление назад). Можно использовать после попадания удара или комбо по сопернику. Если вы идёте назад и пропускаете два действия противника — фол. Аналогично и с бекдешем.</p>
          <p>Если оба игрока намеренно держатся на расстоянии, включается <span class="highlight-bold">3-секундный счёт</span> после порога ПД. Если никто не приближается — фол обоим.</p>
          <p>Против Демпси можно фишить, но нельзя уходить назад (С-кейтить). Против Шотгана можно использовать бекдеш на способность, если вы до этого сделали бекдеш.</p>
        </div>
      </article>

      <article class="rule-card" data-keywords="дд дабл деш спидстеры финты трипл деш фол">
        <div class="card-header">
          <div class="card-number">05</div>
          <h2 class="card-title">ДД (Дабл деш)</h2>
        </div>
        <div class="card-content">
          <p>Имеются в виду два понятия:</p>
          <p><span class="highlight-bold">Дабл деш подряд (для спидстеров)</span> — используется для уклонения от финтов, запрещён (наказывается фолом). <span class="highlight-bold">Второе понятие:</span> два деша после двух атак разрешены. Трипл деш запрещён.</p>
        </div>
      </article>

      <article class="rule-card" data-keywords="звуки изображения пд каунтер ульта звуковые эффекты">
        <div class="card-header">
          <div class="card-number">06</div>
          <h2 class="card-title">Пользовательские звуки и изображения</h2>
        </div>
        <div class="card-content">
          <p>Использование отвлекающих звуков или изображений запрещено:</p>
          <ul>
            <li>Звуки ПД остаются на усмотрение игроков, но могут быть запрошены к удалению при сильном помехе.</li>
            <li>Звуки контрударов (каунтер) и кастомные изображения строго запрещены во время турнира.</li>
            <li>Звуки и изображения ультимативных способностей разрешены.</li>
          </ul>
        </div>
      </article>

      <article class="rule-card title-card" data-keywords="титульные бои bo3 рефери оценки unf unc ucl защита титула чемпион">
        <div class="card-header">
          <div class="card-number">07</div>
          <h2 class="card-title">Титульные бои</h2>
        </div>
        <div class="card-content">
          <ul>
            <li>Проводятся в формате <span class="highlight-bold">Bo3 (до 2 побед)</span>. Игрок может сменить стиль только после поражения; победитель сохраняет текущий стиль.</li>
            <li>За боем наблюдают три рефери высшей категории, выставляющие оценки по 10-балльной системе.</li>
            <li>Если победитель играл чрезмерно пассивно, рефери могут присудить победу оппоненту за активный стиль.</li>
          </ul>
          
          <div class="protection-schedule">
            <div class="schedule-item">
              UNF
              <span>КАЖДАЯ НЕДЕЛЯ</span>
            </div>
            <div class="schedule-item">
              UNC
              <span>КАЖДЫЕ 2 НЕДЕЛИ</span>
            </div>
            <div class="schedule-item">
              UCL
              <span>КАЖДЫЕ 2.5 НЕДЕЛИ</span>
            </div>
          </div>
        </div>
      </article>

      <article class="rule-card title-card" data-keywords="регламент проведения вылеты 5 минут тко рефери лимит 3 боя дивизионы топ-5 топ-1 вызов">
        <div class="card-header">
          <div class="card-number">08</div>
          <h2 class="card-title">ПРАВИЛА ПРОВЕДЕНИЯ БОЕВ U.C.L</h2>
        </div>
        <div class="card-content">
          <ul>
            <li><span class="highlight-bold">Проблемы со связью и вылеты:</span> При обрыве соединения даётся 5 минут на возвращение. В противном случае засчитывается поражение или ТКО.</li>
            <li><span class="highlight-bold">Авторитет рефери:</span> Решение судьи на ринге не оспаривается во время матча. Ошибки рефери разбираются администрацией после боя.</li>
            <li><span class="highlight-bold">Суточный лимит:</span> Один боец может провести не более 3 боёв за 24 часа.</li>
            <li><span class="highlight-bold">Смена дивизионов:</span> При полном доминировании администрация вправе перевести игрока в дивизион выше. Для обычного перехода нужно завоевать пояс и сделать 1 защиту.</li>
            <li><span class="highlight-bold">Право на вызов:</span> Вызывать чемпиона могут только участники Топ-5. Чемпион обязан принять вызов от Топ-1.</li>
          </ul>
        </div>
      </article>

      <article class="rule-card ban-card" data-keywords="бан стили slugger hawk hammer dragonfish white ash wolf hitman shotgun corkscrew bullet chronos shinies exclusive">
        <div class="card-header">
          <div class="card-number">09</div>
          <h2 class="card-title">ЗАПРЕЩЁННЫЕ СТИЛИ</h2>
        </div>
        <div class="card-content">
          <p>Стили, запрещённые к использованию на турнире:</p>
          <div class="ban-list">
            <span class="ban-tag">slugger</span>
            <span class="ban-tag">hawk</span>
            <span class="ban-tag">hammer</span>
            <span class="ban-tag">dragonfish</span>
            <span class="ban-tag">white ash</span>
            <span class="ban-tag">wolf</span>
            <span class="ban-tag">hitman</span>
            <span class="ban-tag">shotgun</span>
            <span class="ban-tag">corkscrew</span>
            <span class="ban-tag">bullet</span>
            <span class="ban-tag">chronos</span>
            <span class="ban-tag">all shinies</span>
            <span class="ban-tag">exclusive styles</span>
          </div>
        </div>
      </article>

    </div>
  </main>

  <footer>
    <p>© U.C.L. Official League. Все права защищены.</p>
  </footer>

  <script>
    window.addEventListener('load', () => {
      setTimeout(() => {
        const loader = document.getElementById('loader');
        loader.style.opacity = '0';
        setTimeout(() => loader.style.visibility = 'hidden', 500);
      }, 2500);
    });

    const searchInput = document.getElementById('searchInput');
    const ruleCards = document.querySelectorAll('.rule-card');

    searchInput.addEventListener('input', (e) => {
      const query = e.target.value.toLowerCase().trim();
      ruleCards.forEach(card => {
        const text = card.textContent.toLowerCase();
        const keywords = card.getAttribute('data-keywords') || '';
        if (text.includes(query) || keywords.includes(query)) {
          card.classList.remove('hidden');
        } else {
          card.classList.add('hidden');
        }
      });
    });

    const animToggle = document.getElementById('animToggle');
    animToggle.addEventListener('click', () => {
      document.body.classList.toggle('anim-enabled');
    });

    const toggleSettings = document.getElementById('toggleSettings');
    const settingsDrawer = document.getElementById('settingsDrawer');
    toggleSettings.addEventListener('click', () => {
      settingsDrawer.classList.toggle('hidden');
    });

    const accentPicker = document.getElementById('accentPicker');
    accentPicker.addEventListener('input', (e) => {
      const val = e.target.value;
      document.documentElement.style.setProperty('--accent-color', val);
      document.documentElement.style.setProperty('--glow-color', val + '80');
    });
  </script>
</body>
</html>
