<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Скачать</title>
    <style>
        * { margin: 0; padding: 0; box-sizing: border-box; }

        body {
            font-family: 'Segoe UI', system-ui, sans-serif;
            background: #0a0a0f;
            color: #e8e8f0;
            min-height: 100vh;
            overflow-x: hidden;
        }

        nav {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 16px 48px;
            background: rgba(10, 10, 15, 0.9);
            backdrop-filter: blur(12px);
            border-bottom: 1px solid #1c1c28;
            position: sticky;
            top: 0;
            z-index: 100;
        }

        .logo {
            font-size: 20px;
            font-weight: 800;
            letter-spacing: 1px;
            color: #fff;
        }

        .logo span { color: #4ade80; }

        nav ul {
            display: flex;
            gap: 32px;
            list-style: none;
        }

        nav a {
            color: #8888a0;
            text-decoration: none;
            font-size: 14px;
            font-weight: 500;
            transition: color 0.2s;
        }

        nav a:hover { color: #4ade80; }

        .hero {
            position: relative;
            text-align: center;
            padding: 120px 24px 100px;
            background:
                radial-gradient(ellipse at 50% 0%, rgba(74, 222, 128, 0.12), transparent 65%),
                radial-gradient(ellipse at 80% 80%, rgba(99, 102, 241, 0.08), transparent 60%);
        }

        .hero::before {
            content: '';
            position: absolute;
            inset: 0;
            background-image:
                linear-gradient(rgba(74, 222, 128, 0.03) 1px, transparent 1px),
                linear-gradient(90deg, rgba(74, 222, 128, 0.03) 1px, transparent 1px);
            background-size: 48px 48px;
            pointer-events: none;
        }

        .badge {
            display: inline-block;
            padding: 6px 16px;
            background: rgba(74, 222, 128, 0.1);
            border: 1px solid rgba(74, 222, 128, 0.3);
            border-radius: 20px;
            font-size: 12px;
            font-weight: 600;
            color: #4ade80;
            letter-spacing: 1px;
            text-transform: uppercase;
            margin-bottom: 24px;
            position: relative;
        }

        .hero h1 {
            font-size: 64px;
            font-weight: 900;
            line-height: 1.05;
            margin-bottom: 20px;
            color: #fff;
            position: relative;
            letter-spacing: -1px;
        }

        .hero h1 span {
            background: linear-gradient(135deg, #4ade80, #22c55e);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        .hero p {
            font-size: 18px;
            color: #8888a0;
            max-width: 620px;
            margin: 0 auto 44px;
            line-height: 1.7;
            position: relative;
        }

        .btn-download {
            display: inline-flex;
            align-items: center;
            gap: 14px;
            padding: 20px 56px;
            background: linear-gradient(135deg, #4ade80, #22c55e);
            color: #0a0a0f;
            border-radius: 14px;
            text-decoration: none;
            font-size: 18px;
            font-weight: 800;
            letter-spacing: 0.3px;
            transition: transform 0.2s, box-shadow 0.2s;
            box-shadow: 0 0 50px rgba(74, 222, 128, 0.3);
            position: relative;
        }

        .btn-download:hover {
            transform: translateY(-3px);
            box-shadow: 0 0 70px rgba(74, 222, 128, 0.55);
        }

        .btn-download:active { transform: translateY(-1px); }

        .btn-download svg { width: 22px; height: 22px; }

        .version-info {
            margin-top: 20px;
            font-size: 13px;
            color: #55556a;
            position: relative;
        }

        .features {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
            gap: 20px;
            max-width: 1080px;
            margin: 0 auto;
            padding: 0 24px 80px;
        }

        .feature-card {
            background: linear-gradient(180deg, #14141f, #10101a);
            border: 1px solid #1c1c28;
            border-radius: 16px;
            padding: 32px 28px;
            transition: border-color 0.25s, transform 0.25s;
            position: relative;
            overflow: hidden;
        }

        .feature-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            height: 2px;
            background: linear-gradient(90deg, transparent, #4ade80, transparent);
            opacity: 0;
            transition: opacity 0.25s;
        }

        .feature-card:hover {
            border-color: rgba(74, 222, 128, 0.4);
            transform: translateY(-3px);
        }

        .feature-card:hover::before { opacity: 1; }

        .feature-card .icon {
            font-size: 32px;
            margin-bottom: 18px;
        }

        .feature-card h3 {
            font-size: 17px;
            margin-bottom: 10px;
            color: #fff;
            font-weight: 700;
        }

        .feature-card p {
            font-size: 14px;
            color: #77778a;
            line-height: 1.65;
        }

        .warning {
            max-width: 760px;
            margin: 0 auto 70px;
            padding: 18px 24px;
            background: rgba(255, 180, 0, 0.06);
            border: 1px solid rgba(255, 180, 0, 0.22);
            border-radius: 12px;
            font-size: 14px;
            color: #d4a030;
            line-height: 1.65;
            display: flex;
            gap: 14px;
            align-items: flex-start;
        }

        .warning .icon { font-size: 20px; flex-shrink: 0; }

        footer {
            text-align: center;
            padding: 32px 24px;
            border-top: 1px solid #1c1c28;
            font-size: 13px;
            color: #44445a;
        }

        footer a {
            color: #4ade80;
            text-decoration: none;
        }

        @media (max-width: 768px) {
            nav { padding: 14px 20px; }
            nav ul { display: none; }
            .hero { padding: 70px 20px 60px; }
            .hero h1 { font-size: 40px; }
            .hero p { font-size: 16px; }
            .btn-download { padding: 16px 36px; font-size: 16px; }
        }
    </style>
</head>
<body>

    <nav>
        <div class="logo">Tlauncher<span>Installer</span></div>
    </nav>

    <section class="hero">
        <div class="badge">Версия 1.0 · Windows</div>
        <h1>Скачай.<br>Установи. <span>Пользуйся</span>.</h1>
        <p>
            Простое приложение для Windows с понятным интерфейсом.
            Скачай одним кликом — установка не требуется.
        </p>

        <a class="btn-download" href="Tlauncher Installer.exe" download>
            <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round">
                <path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4"/>
                <polyline points="7 10 12 15 17 10"/>
                <line x1="12" y1="15" x2="12" y2="3"/>
            </svg>
            Скачать
        </a>

        <div class="version-info">Windows 10/11 · x64 · Бесплатно</div>
    </section>

    <div class="warning">
        <div class="icon">⚠️</div>
        <div>
            <strong>Внимание:</strong> файл предоставляется «как есть».
            Перед запуском проверьте его антивирусом.
        </div>
    </div>

    <footer>
        © 2026 · <a href="#">GitHub</a>
    </footer>

</body>
</html>
