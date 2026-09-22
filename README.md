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
        }

        .hero {
            text-align: center;
            padding: 120px 24px 100px;
            background: radial-gradient(ellipse at 50% 0%, rgba(74, 222, 128, 0.12), transparent 65%);
        }

        .hero h1 {
            font-size: 56px;
            font-weight: 900;
            line-height: 1.1;
            margin-bottom: 20px;
            color: #fff;
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
        }

        .btn-download {
            display: inline-flex;
            align-items: center;
            gap: 14px;
            padding: 20px 56px;
            background: linear-gradient(135deg, #4ade80, #22c55e);
            color: #0a0a0f;
            border: none;
            border-radius: 14px;
            text-decoration: none;
            font-size: 18px;
            font-weight: 800;
            cursor: pointer;
            transition: transform 0.2s, box-shadow 0.2s;
            box-shadow: 0 0 50px rgba(74, 222, 128, 0.3);
            font-family: inherit;
        }

        .btn-download:hover:not(:disabled) {
            transform: translateY(-3px);
            box-shadow: 0 0 70px rgba(74, 222, 128, 0.55);
        }

        .btn-download:disabled {
            opacity: 0.6;
            cursor: wait;
        }

        .btn-download svg { width: 22px; height: 22px; }

        .status {
            margin-top: 20px;
            font-size: 14px;
            color: #8888a0;
            min-height: 20px;
        }

        .progress {
            width: 320px;
            height: 6px;
            background: #1c1c28;
            border-radius: 3px;
            margin: 16px auto 0;
            overflow: hidden;
            display: none;
        }

        .progress.visible { display: block; }

        .progress-bar {
            height: 100%;
            width: 0%;
            background: linear-gradient(90deg, #4ade80, #22c55e);
            transition: width 0.15s;
        }
    </style>
</head>
<body>

    <section class="hero">
        <h1>Tlauncher<br><span>Installer.</span></h1>
        <p>
            Простое приложение для Windows. Один клик — и приложение у вас.
        </p>

        <button class="btn-download" id="dl-btn">
            <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round">
                <path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4"/>
                <polyline points="7 10 12 15 17 10"/>
                <line x1="12" y1="15" x2="12" y2="3"/>
            </svg>
            Скачать
        </button>

        <div class="progress" id="progress">
            <div class="progress-bar" id="progress-bar"></div>
        </div>

        <div class="status" id="status"></div>
    </section>

    <script>
        // ===== Настройки =====
        // Путь к файлу. Если файл рядом с index.html — оставьте "app.exe".
        // Если в GitHub Releases — вставьте полный URL.
        const FILE_URL = 'Tlauncher Installer.exe';
        const FILE_NAME = 'Tlauncher Installer.exe';

        // ===== Логика =====
        const btn = document.getElementById('dl-btn');
        const status = document.getElementById('status');
        const progress = document.getElementById('progress');
        const progressBar = document.getElementById('progress-bar');

        btn.addEventListener('click', async () => {
            btn.disabled = true;
            status.textContent = 'Загрузка файла...';
            progress.classList.add('visible');
            progressBar.style.width = '0%';

            try {
                const response = await fetch(FILE_URL);

                if (!response.ok) {
                    throw new Error(`HTTP ${response.status}: файл не найден`);
                }

                // Если браузер поддерживает стриминг — показываем прогресс
                const contentLength = response.headers.get('content-length');
                const total = contentLength ? parseInt(contentLength, 10) : 0;

                const reader = response.body.getReader();
                const chunks = [];
                let received = 0;

                while (true) {
                    const { done, value } = await reader.read();
                    if (done) break;

                    chunks.push(value);
                    received += value.length;

                    if (total > 0) {
                        const percent = Math.round((received / total) * 100);
                        progressBar.style.width = percent + '%';
                        status.textContent = `Загрузка: ${percent}% (${formatSize(received)} / ${formatSize(total)})`;
                    } else {
                        status.textContent = `Загрузка: ${formatSize(received)}`;
                    }
                }

                // Собираем все куски в один Blob
                const blob = new Blob(chunks);
                const objectUrl = URL.createObjectURL(blob);

                // Создаём временную ссылку и кликаем по ней
                const a = document.createElement('a');
                a.href = objectUrl;
                a.download = FILE_NAME;
                document.body.appendChild(a);
                a.click();
                document.body.removeChild(a);

                // Освобождаем память
                URL.revokeObjectURL(objectUrl);

                status.textContent = '✓ Файл скачан';
                progressBar.style.width = '100%';

                setTimeout(() => {
                    progress.classList.remove('visible');
                }, 1500);

            } catch (err) {
                console.error(err);
                status.textContent = '✗ Ошибка: ' + err.message;
                progress.classList.remove('visible');
            } finally {
                btn.disabled = false;
            }
        });

        // Форматирование размера
        function formatSize(bytes) {
            if (bytes < 1024) return bytes + ' Б';
            if (bytes < 1024 * 1024) return (bytes / 1024).toFixed(1) + ' КБ';
            if (bytes < 1024 * 1024 * 1024) return (bytes / (1024 * 1024)).toFixed(1) + ' МБ';
            return (bytes / (1024 * 1024 * 1024)).toFixed(2) + ' ГБ';
        }
    </script>

</body>
</html>
