<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>RepowerStudio · GitHub</title>
    
    <link rel="icon" href="https://avatars.githubusercontent.com/repowerstudio?s=64" />
    <link rel="apple-touch-icon" href="https://avatars.githubusercontent.com/repowerstudio?s=192" />
    
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css" />
    
    <style>
        * { margin: 0; padding: 0; box-sizing: border-box; }
        html, body { width: 100%; min-height: 100vh; background: linear-gradient(180deg, #1a0a2e 0%, #2d1b3d 20%, #4a1942 35%, #6b2a4a 50%, #c45a3c 65%, #e8843a 75%, #f5b04a 85%, #ffd76a 100%); font-family: 'Segoe UI', system-ui, sans-serif; overflow-x: hidden; position: relative; margin: 0; padding: 0; }
        
        .wrapper { position: absolute; top: 50%; left: 50%; transform: translate(-50%, -50%); width: 100%; max-width: 1100px; padding: 1.5rem; z-index: 10; max-height: 98vh; overflow-y: auto; }
        .wrapper::-webkit-scrollbar { width: 4px; }
        .wrapper::-webkit-scrollbar-track { background: rgba(255,255,255,0.02); }
        .wrapper::-webkit-scrollbar-thumb { background: rgba(255,200,150,0.1); border-radius: 2px; }

        /* ===== ЗАКАТНЫЙ ФОН ===== */
        .sunset-bg { position: fixed; top: 0; left: 0; width: 100vw; height: 100vh; z-index: 0; pointer-events: none; overflow: hidden; }
        .sunset-gradient { position: absolute; width: 100%; height: 100%; background: linear-gradient(180deg, #1a0a2e 0%, #2d1b3d 20%, #4a1942 35%, #6b2a4a 50%, #c45a3c 65%, #e8843a 75%, #f5b04a 85%, #ffd76a 100%); animation: sunsetPulse 8s ease-in-out infinite alternate; }
        @keyframes sunsetPulse { 0% { opacity: 1; } 50% { opacity: 0.85; } 100% { opacity: 1; } }

        .sun { position: absolute; bottom: 15%; left: 50%; transform: translateX(-50%); width: 200px; height: 200px; border-radius: 50%; background: radial-gradient(circle, #ffd76a, #f5b04a, #e8843a); box-shadow: 0 0 100px rgba(255,200,100,0.4), 0 0 200px rgba(255,150,50,0.2), 0 0 400px rgba(255,100,50,0.1); animation: sunGlow 4s ease-in-out infinite alternate; }
        @keyframes sunGlow { 0% { transform: translateX(-50%) scale(1); box-shadow: 0 0 100px rgba(255,200,100,0.4), 0 0 200px rgba(255,150,50,0.2); } 100% { transform: translateX(-50%) scale(1.1); box-shadow: 0 0 150px rgba(255,200,100,0.6), 0 0 300px rgba(255,150,50,0.3); } }

        .clouds { position: absolute; top: 0; left: 0; width: 100%; height: 40%; pointer-events: none; overflow: hidden; }
        .cloud { position: absolute; height: 60px; background: radial-gradient(ellipse at 20% 50%, rgba(255,200,150,0.15) 0%, transparent 70%); border-radius: 50%; animation: cloudMove 25s linear infinite; }
        .cloud:nth-child(1) { width: 300px; top: 10%; left: -10%; animation-duration: 30s; }
        .cloud:nth-child(2) { width: 400px; top: 25%; left: 20%; animation-duration: 35s; animation-delay: -8s; }
        .cloud:nth-child(3) { width: 250px; top: 5%; left: 60%; animation-duration: 28s; animation-delay: -15s; }
        .cloud:nth-child(4) { width: 350px; top: 15%; left: 80%; animation-duration: 32s; animation-delay: -5s; }
        @keyframes cloudMove { 0% { transform: translateX(0); } 100% { transform: translateX(120vw); } }

        /* ===== ЗВЁЗДЫ ===== */
        .stars-bg { position: fixed; top: 0; left: 0; width: 100vw; height: 100vh; z-index: 0; pointer-events: none; overflow: hidden; }
        .stars-layer { position: absolute; width: 100%; height: 100%; background-image: radial-gradient(2px 2px at 10% 20%, rgba(255,255,255,0.6), transparent), radial-gradient(2px 2px at 30% 60%, rgba(255,255,255,0.4), transparent), radial-gradient(3px 3px at 50% 10%, rgba(255,255,255,0.8), transparent), radial-gradient(1px 1px at 70% 80%, rgba(255,255,255,0.3), transparent), radial-gradient(2px 2px at 90% 40%, rgba(255,255,255,0.5), transparent), radial-gradient(1px 1px at 15% 90%, rgba(255,255,255,0.3), transparent), radial-gradient(3px 3px at 45% 45%, rgba(255,255,255,0.7), transparent), radial-gradient(2px 2px at 80% 15%, rgba(255,255,255,0.4), transparent), radial-gradient(1px 1px at 55% 75%, rgba(255,255,255,0.2), transparent), radial-gradient(2px 2px at 25% 35%, rgba(255,255,255,0.5), transparent), radial-gradient(3px 3px at 65% 55%, rgba(255,255,255,0.6), transparent); background-size: 100% 100%; background-repeat: no-repeat; animation: starTwinkle 4s ease-in-out infinite alternate; }
        .stars-layer:nth-child(2) { background-image: radial-gradient(1px 1px at 12% 22%, rgba(255,255,255,0.4), transparent), radial-gradient(1px 1px at 33% 65%, rgba(255,255,255,0.3), transparent), radial-gradient(2px 2px at 52% 12%, rgba(255,255,255,0.6), transparent), radial-gradient(1px 1px at 72% 82%, rgba(255,255,255,0.2), transparent), radial-gradient(1px 1px at 92% 42%, rgba(255,255,255,0.3), transparent); background-size: 100% 100%; background-repeat: no-repeat; animation: starTwinkle 6s ease-in-out infinite alternate-reverse; opacity: 0.6; }
        .stars-layer:nth-child(3) { background-image: radial-gradient(3px 3px at 5% 15%, rgba(255,200,150,0.8), transparent), radial-gradient(4px 4px at 25% 55%, rgba(255,200,150,0.6), transparent), radial-gradient(5px 5px at 45% 5%, rgba(255,200,150,1), transparent), radial-gradient(3px 3px at 65% 75%, rgba(255,200,150,0.5), transparent), radial-gradient(4px 4px at 85% 35%, rgba(255,200,150,0.7), transparent); background-size: 100% 100%; background-repeat: no-repeat; animation: starTwinkle 3s ease-in-out infinite alternate; opacity: 0.5; }
        @keyframes starTwinkle { 0% { opacity: 0.4; transform: scale(1); } 50% { opacity: 0.8; transform: scale(1.02); } 100% { opacity: 0.5; transform: scale(0.98); } }

        .bright-star { position: absolute; border-radius: 50%; background: white; box-shadow: 0 0 20px rgba(255,200,150,0.6), 0 0 60px rgba(255,200,100,0.3); animation: brightPulse 2s ease-in-out infinite; pointer-events: none; }
        .bright-star:nth-child(1) { width: 6px; height: 6px; top: 8%; left: 15%; animation-delay: 0s; }
        .bright-star:nth-child(2) { width: 8px; height: 8px; top: 25%; right: 20%; animation-delay: 0.7s; }
        .bright-star:nth-child(3) { width: 5px; height: 5px; top: 45%; left: 8%; animation-delay: 1.4s; }
        .bright-star:nth-child(4) { width: 7px; height: 7px; bottom: 20%; right: 15%; animation-delay: 0.3s; }
        .bright-star:nth-child(5) { width: 9px; height: 9px; top: 60%; right: 8%; animation-delay: 1.8s; }
        .bright-star:nth-child(6) { width: 5px; height: 5px; top: 5%; right: 40%; animation-delay: 0.5s; }
        .bright-star:nth-child(7) { width: 7px; height: 7px; bottom: 35%; left: 25%; animation-delay: 1.1s; }
        .bright-star:nth-child(8) { width: 6px; height: 6px; top: 40%; left: 50%; animation-delay: 2.2s; }
        @keyframes brightPulse { 0%, 100% { transform: scale(0.8); opacity: 0.5; box-shadow: 0 0 15px rgba(255,200,150,0.4); } 50% { transform: scale(1.4); opacity: 1; box-shadow: 0 0 40px rgba(255,200,150,0.7), 0 0 80px rgba(255,200,100,0.3); } }

        /* ===== ПАДАЮЩИЕ ЗВЁЗДЫ ===== */
        .shooting-stars { position: fixed; top: 0; left: 0; width: 100vw; height: 100vh; z-index: 1; pointer-events: none; overflow: hidden; }
        .shooting-star { position: absolute; animation: shootStar 4s linear infinite; opacity: 0; }
        .shooting-star .star-dot { position: absolute; width: 3px; height: 3px; background: white; border-radius: 50%; box-shadow: 0 0 8px 3px rgba(255,200,150,0.4); top: 0; left: 0; }
        .shooting-star .star-tail { position: absolute; height: 2px; background: linear-gradient(to left, rgba(255,200,150,0.8), transparent); top: 0.5px; right: 3px; width: 80px; transform-origin: right center; }
        .shooting-star:nth-child(1) { top: 10%; left: 20%; animation-delay: 0s; animation-duration: 3.5s; }
        .shooting-star:nth-child(2) { top: 20%; left: 60%; animation-delay: 2s; animation-duration: 4s; }
        .shooting-star:nth-child(3) { top: 5%; left: 40%; animation-delay: 4s; animation-duration: 3s; }
        .shooting-star:nth-child(4) { top: 30%; left: 80%; animation-delay: 1s; animation-duration: 4.5s; }
        .shooting-star:nth-child(5) { top: 15%; left: 10%; animation-delay: 3s; animation-duration: 3.8s; }
        .shooting-star:nth-child(6) { top: 25%; left: 50%; animation-delay: 0.5s; animation-duration: 3.2s; }
        .shooting-star:nth-child(7) { top: 8%; left: 75%; animation-delay: 2.5s; animation-duration: 4.2s; }
        .shooting-star:nth-child(8) { top: 35%; left: 30%; animation-delay: 1.5s; animation-duration: 3.6s; }
        @keyframes shootStar { 0% { transform: translate(0,0) rotate(35deg) scale(0); opacity: 0; } 5% { opacity: 1; transform: translate(30px,30px) rotate(35deg) scale(0.5); } 15% { transform: translate(100px,100px) rotate(35deg) scale(1); opacity: 1; } 85% { opacity: 1; } 95% { opacity: 0.5; } 100% { transform: translate(380px,380px) rotate(35deg) scale(0.3); opacity: 0; } }

        /* ===== ГЛАВНОЕ СТЕКЛО ===== */
        .glass-card { background: linear-gradient(135deg, rgba(60,30,40,0.20), rgba(80,40,30,0.15)); backdrop-filter: blur(6px); -webkit-backdrop-filter: blur(6px); border-radius: 3rem; padding: 2.5rem; border: 1px solid rgba(255,200,150,0.08); box-shadow: 0 40px 80px rgba(0,0,0,0.6), inset 0 1px 0 rgba(255,200,150,0.05); animation: cardAppear 0.7s ease; transition: all 0.5s ease; width: 100%; position: relative; overflow: hidden; }
        .glass-card::before { content: ''; position: absolute; top: -50%; left: -50%; width: 200%; height: 200%; background: radial-gradient(circle at 30% 40%, rgba(255,200,150,0.03), transparent 60%); pointer-events: none; animation: glassShine 10s ease-in-out infinite; }
        @keyframes glassShine { 0%, 100% { transform: translate(0,0); } 50% { transform: translate(5%,8%); } }
        .glass-card:hover { box-shadow: 0 50px 100px rgba(0,0,0,0.7), inset 0 1px 0 rgba(255,200,150,0.08); background: linear-gradient(135deg, rgba(60,30,40,0.30), rgba(80,40,30,0.20)); }
        @keyframes cardAppear { 0% { opacity: 0; transform: translateY(30px) scale(0.97); } 100% { opacity: 1; transform: translateY(0) scale(1); } }

        .header { display: flex; align-items: center; justify-content: space-between; gap: 1.2rem; flex-wrap: wrap; margin-bottom: 1.5rem; width: 100%; }
        .header-left { display: flex; align-items: center; gap: 0.8rem; }
        .avatar-wrapper { position: relative; flex-shrink: 0; }
        .avatar-wrapper::after { content: ''; position: absolute; inset: -2px; border-radius: 50%; padding: 2px; background: linear-gradient(135deg, #f5b04a, #e8843a, #c45a3c); background-size: 300% 300%; animation: avatarBorder 3s ease-in-out infinite; -webkit-mask: linear-gradient(#fff 0 0) content-box, linear-gradient(#fff 0 0); mask: linear-gradient(#fff 0 0) content-box, linear-gradient(#fff 0 0); -webkit-mask-composite: xor; mask-composite: exclude; pointer-events: none; }
        @keyframes avatarBorder { 0%, 100% { background-position: 0% 50%; } 50% { background-position: 100% 50%; } }
        .avatar { width: 56px; height: 56px; border-radius: 50%; background: rgba(255,255,255,0.05); display: flex; align-items: center; justify-content: center; overflow: hidden; position: relative; z-index: 1; }
        .avatar img { width: 100%; height: 100%; object-fit: cover; transition: transform 0.5s ease; }
        .avatar:hover img { transform: scale(1.1); }
        .avatar .fallback-icon { font-size: 2.2rem; color: #f5b04a; opacity: 0.6; }

        .brand-wrapper { display: flex; flex-direction: column; }
        .brand { font-size: clamp(1.6rem, 4vw, 2.6rem); font-weight: 700; background: linear-gradient(145deg, #ffd76a, #f5b04a); -webkit-background-clip: text; background-clip: text; color: transparent; line-height: 1.1; position: relative; display: inline-block; }
        .brand::after { content: '✦'; position: absolute; right: -1.5rem; top: -0.2rem; font-size: 0.8rem; color: #f5b04a; opacity: 0.6; animation: sparkle 2s ease-in-out infinite; }
        @keyframes sparkle { 0%, 100% { opacity: 0.3; transform: scale(0.8) rotate(0deg); } 50% { opacity: 1; transform: scale(1.2) rotate(180deg); } }
        .brand-sub { font-size: 0.7rem; color: rgba(255,200,150,0.3); letter-spacing: 0.08em; text-transform: uppercase; }

        .badge-github { background: rgba(255,255,255,0.05); padding: 0.4rem 1rem; border-radius: 60px; font-size: 0.75rem; color: rgba(255,200,150,0.7); border: 1px solid rgba(255,200,150,0.06); display: flex; align-items: center; gap: 0.5rem; cursor: pointer; transition: all 0.3s ease; position: relative; overflow: hidden; flex-shrink: 0; }
        .badge-github::before { content: ''; position: absolute; inset: 0; background: linear-gradient(135deg, rgba(245,176,74,0.1), transparent); opacity: 0; transition: opacity 0.5s ease; }
        .badge-github:hover::before { opacity: 1; }
        .badge-github:hover { background: rgba(255,255,255,0.08); transform: scale(1.02) translateY(-1px); box-shadow: 0 4px 20px rgba(245,176,74,0.15); }
        .badge-github i { color: #f5b04a; position: relative; z-index: 1; }

        /* ===== ВЕРХНЕЕ МЕНЮ ===== */
        .top-menu { display: flex; gap: 0.5rem; flex-wrap: wrap; margin-bottom: 1.5rem; border-bottom: 1px solid rgba(255,200,150,0.04); padding-bottom: 0.8rem; }
        .top-menu button { background: transparent; border: none; color: rgba(255,200,150,0.3); padding: 0.4rem 1.2rem; border-radius: 60px; font-size: 0.85rem; cursor: pointer; transition: all 0.3s ease; display: flex; align-items: center; gap: 0.4rem; position: relative; }
        .top-menu button:hover { color: rgba(255,200,150,0.7); background: rgba(255,255,255,0.03); }
        .top-menu button.active { color: #f5b04a; background: rgba(245,176,74,0.08); box-shadow: 0 0 30px rgba(245,176,74,0.05); }

        /* ===== СТРАНИЦЫ ===== */
        .page { display: none; animation: fadePage 0.4s ease; }
        .page.active { display: block; }
        @keyframes fadePage { 0% { opacity: 0; transform: translateY(10px); } 100% { opacity: 1; transform: translateY(0); } }

        .tagline { display: flex; align-items: center; justify-content: center; gap: 0.8rem; flex-wrap: wrap; font-size: clamp(0.85rem, 2vw, 1.1rem); font-weight: 300; color: rgba(255,200,150,0.5); margin-bottom: 2rem; padding: 0.5rem 1rem; border-left: 3px solid rgba(245,176,74,0.2); border-right: 3px solid rgba(245,176,74,0.2); animation: taglinePulse 3s ease-in-out infinite; text-align: center; width: 100%; }
        @keyframes taglinePulse { 0%, 100% { border-color: rgba(245,176,74,0.2); } 50% { border-color: rgba(245,176,74,0.5); } }

        /* ===== СТРАНИЦА РЕПОЗИТОРИЕВ ===== */
        .repo-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(250px, 1fr)); gap: 1.2rem; margin: 1.8rem 0 2.2rem; min-height: 80px; width: 100%; }
        .repo-card { background: rgba(40,20,30,0.25); backdrop-filter: blur(2px); -webkit-backdrop-filter: blur(2px); border-radius: 1.8rem; padding: 1.4rem 1.2rem 1.2rem; border: 1px solid rgba(255,200,150,0.04); box-shadow: 0 6px 16px rgba(0,0,0,0.25); transition: all 0.3s ease; color: rgba(255,220,180,0.8); cursor: pointer; position: relative; overflow: hidden; animation: fadeUp 0.35s ease forwards; opacity: 0; transform: translateY(8px); display: flex; flex-direction: column; }
        .repo-card::before { content: ''; position: absolute; inset: 0; background: linear-gradient(135deg, rgba(245,176,74,0.05), transparent); opacity: 0; transition: opacity 0.5s ease; }
        .repo-card:hover::before { opacity: 1; }
        .repo-card:nth-child(1) { animation-delay: 0.02s; }
        .repo-card:nth-child(2) { animation-delay: 0.04s; }
        .repo-card:nth-child(3) { animation-delay: 0.06s; }
        .repo-card:nth-child(4) { animation-delay: 0.08s; }
        .repo-card:nth-child(5) { animation-delay: 0.10s; }
        .repo-card:nth-child(6) { animation-delay: 0.12s; }
        @keyframes fadeUp { to { opacity: 1; transform: translateY(0); } }
        .repo-card:hover { transform: translateY(-4px) scale(1.02); background: rgba(60,30,40,0.35); border-color: rgba(245,176,74,0.12); box-shadow: 0 16px 32px rgba(0,0,0,0.4); }
        .repo-card .repo-icon { font-size: 1.6rem; margin-bottom: 0.3rem; display: inline-block; color: #f5b04a; transition: transform 0.3s ease; width: 2rem; text-align: center; }
        .repo-card:hover .repo-icon { transform: scale(1.2) rotate(-5deg); }
        .repo-card h3 { font-size: 1.05rem; font-weight: 500; margin-bottom: 0.15rem; background: linear-gradient(to right, #ffd76a, #f5b04a); -webkit-background-clip: text; background-clip: text; color: transparent; }
        .repo-card .repo-desc { font-size: 0.75rem; opacity: 0.55; line-height: 1.3; margin: 0.15rem 0 0.4rem; min-height: 2.2rem; display: -webkit-box; -webkit-line-clamp: 2; -webkit-box-orient: vertical; overflow: hidden; flex: 1; }
        .repo-stats { display: flex; gap: 0.8rem; font-size: 0.65rem; color: rgba(255,200,150,0.3); margin-top: auto; flex-wrap: wrap; align-items: center; }
        .repo-stats span { display: flex; align-items: center; gap: 0.2rem; }
        .repo-stats i { color: #f5b04a; font-size: 0.55rem; }
        .repo-stats .lang-dot { display: inline-block; width: 8px; height: 8px; border-radius: 50%; flex-shrink: 0; }

        .btn-wrapper { display: flex; justify-content: center; gap: 0.8rem; flex-wrap: wrap; width: 100%; }
        .btn-primary { display: inline-flex; align-items: center; gap: 0.6rem; padding: 0.7rem 2rem; font-size: 0.95rem; font-weight: 600; background: linear-gradient(145deg, #6b2a4a, #4a1942); color: #ffd76a; border: none; border-radius: 60px; cursor: pointer; box-shadow: 0 6px 20px rgba(107,42,74,0.35); transition: all 0.3s ease; border: 1px solid rgba(255,200,150,0.06); text-decoration: none; position: relative; overflow: hidden; }
        .btn-primary::before { content: ''; position: absolute; inset: 0; background: linear-gradient(135deg, rgba(245,176,74,0.1), transparent); opacity: 0; transition: opacity 0.5s ease; }
        .btn-primary:hover::before { opacity: 1; }
        .btn-primary:hover { transform: scale(1.03); background: linear-gradient(145deg, #8a3a5a, #5a2a4a); box-shadow: 0 0 30px rgba(245,176,74,0.2); }

        /* ===== СТРАНИЦА О ПРОЕКТЕ ===== */
        .about-stats { display: grid; grid-template-columns: repeat(auto-fit, minmax(150px, 1fr)); gap: 1rem; margin: 1.5rem 0; }
        .about-stat { background: rgba(0,0,0,0.2); border-radius: 1rem; padding: 1.2rem; text-align: center; border: 1px solid rgba(255,200,150,0.04); transition: all 0.3s ease; }
        .about-stat:hover { transform: translateY(-2px); border-color: rgba(245,176,74,0.1); }
        .about-stat .stat-number { font-size: 2.2rem; font-weight: 700; color: #f5b04a; display: block; }
        .about-stat .stat-label { font-size: 0.7rem; color: rgba(255,200,150,0.3); margin-top: 0.2rem; text-transform: uppercase; letter-spacing: 0.05em; }

        .tech-stack { display: flex; gap: 0.8rem; flex-wrap: wrap; margin: 1rem 0; }
        .tech-tag { background: rgba(245,176,74,0.06); border: 1px solid rgba(245,176,74,0.06); padding: 0.3rem 0.8rem; border-radius: 20px; font-size: 0.7rem; color: rgba(255,200,150,0.5); transition: all 0.3s ease; cursor: default; }
        .tech-tag:hover { background: rgba(245,176,74,0.1); transform: scale(1.05); color: rgba(255,200,150,0.8); }

        /* ===== СТРАНИЦА НАСТРОЕК ===== */
        .settings-group { margin-bottom: 1.5rem; }
        .settings-group h4 { color: rgba(255,200,150,0.5); font-size: 0.8rem; margin-bottom: 0.8rem; letter-spacing: 0.05em; text-transform: uppercase; display: flex; align-items: center; gap: 0.5rem; }
        .settings-group h4 i { color: #f5b04a; }

        .setting-item { display: flex; align-items: center; justify-content: space-between; padding: 0.7rem 0; border-bottom: 1px solid rgba(255,200,150,0.03); }
        .setting-item .setting-label { color: rgba(255,200,150,0.5); font-size: 0.85rem; display: flex; align-items: center; gap: 0.6rem; }
        .setting-item .setting-label i { color: #f5b04a; width: 1.2rem; text-align: center; }

        .toggle { width: 44px; height: 24px; background: rgba(255,255,255,0.06); border-radius: 20px; cursor: pointer; transition: all 0.3s ease; position: relative; flex-shrink: 0; border: 1px solid rgba(255,255,255,0.03); }
        .toggle.active { background: rgba(245,176,74,0.25); border-color: rgba(245,176,74,0.15); }
        .toggle::after { content: ''; position: absolute; top: 2px; left: 2px; width: 18px; height: 18px; background: rgba(255,255,255,0.2); border-radius: 50%; transition: all 0.3s ease; }
        .toggle.active::after { left: 22px; background: #f5b04a; box-shadow: 0 0 20px rgba(245,176,74,0.2); }
        .toggle:hover { border-color: rgba(255,200,150,0.1); }

        .footer-links { margin-top: 2.2rem; display: flex; flex-wrap: wrap; align-items: center; justify-content: space-between; gap: 0.8rem; border-top: 1px solid rgba(255,200,150,0.04); padding-top: 1.5rem; width: 100%; }
        .social-icons { display: flex; gap: 0.8rem; }
        .social-icons a { color: rgba(255,200,150,0.25); font-size: 1.2rem; transition: all 0.3s ease; display: inline-block; }
        .social-icons a:hover { color: #f5b04a; transform: translateY(-3px) scale(1.1); filter: drop-shadow(0 0 20px rgba(245,176,74,0.2)); }

        .live-indicator { display: flex; align-items: center; gap: 0.4rem; color: rgba(255,200,150,0.2); font-size: 0.7rem; }
        .pulse-circle { width: 6px; height: 6px; border-radius: 50%; background: #f5b04a; box-shadow: 0 0 12px #e8843a; animation: pulse 2s infinite; }
        @keyframes pulse { 0% { opacity: 0.3; transform: scale(0.8); } 50% { opacity: 1; transform: scale(1.3); } 100% { opacity: 0.3; transform: scale(0.8); } }
        .footer-copy { font-size: 0.7rem; color: rgba(255,200,150,0.12); }

        .loader-small { display: inline-flex; align-items: center; gap: 0.4rem; font-size: 0.75rem; color: rgba(255,200,150,0.25); }
        .loader-small .loader-dots { display: inline-flex; gap: 0.2rem; }
        .loader-small .loader-dots span { width: 6px; height: 6px; border-radius: 50%; background: rgba(255,200,150,0.2); animation: dotPulse 1.4s ease-in-out infinite; }
        .loader-small .loader-dots span:nth-child(2) { animation-delay: 0.2s; }
        .loader-small .loader-dots span:nth-child(3) { animation-delay: 0.4s; }
        @keyframes dotPulse { 0%, 80%, 100% { transform: scale(0.6); opacity: 0.3; } 40% { transform: scale(1); opacity: 1; } }

        .loading-spinner { display: flex; flex-direction: column; align-items: center; justify-content: center; padding: 2rem 0; gap: 1rem; }
        .loading-spinner .spinner-ring { width: 40px; height: 40px; border-radius: 50%; border: 3px solid rgba(245,176,74,0.1); border-top: 3px solid #f5b04a; animation: spinnerRotate 0.8s linear infinite; }
        @keyframes spinnerRotate { 0% { transform: rotate(0deg); } 100% { transform: rotate(360deg); } }
        .loading-spinner span { color: rgba(255,200,150,0.2); font-size: 0.85rem; }

        #particles-canvas { position: fixed; top: 0; left: 0; width: 100vw; height: 100vh; z-index: 0; pointer-events: none; }

        /* ===== МОДАЛЬНОЕ ОКНО ===== */
        .modal-overlay { display: none; position: fixed; top: 0; left: 0; width: 100vw; height: 100vh; background: rgba(0,0,0,0.75); backdrop-filter: blur(10px); z-index: 1000; justify-content: center; align-items: center; padding: 1.5rem; }
        .modal-overlay.active { display: flex; }
        .modal-content { background: linear-gradient(145deg, rgba(40,20,30,0.96), rgba(60,30,40,0.92)); backdrop-filter: blur(16px); border-radius: 2rem; max-width: 850px; width: 100%; max-height: 85vh; padding: 2rem; border: 1px solid rgba(255,200,150,0.06); box-shadow: 0 40px 80px rgba(0,0,0,0.7); overflow-y: auto; animation: modalIn 0.3s ease; position: relative; }
        .modal-content::before { content: ''; position: absolute; top: -30%; right: -30%; width: 60%; height: 60%; background: radial-gradient(circle, rgba(245,176,74,0.03), transparent 70%); pointer-events: none; }
        @keyframes modalIn { 0% { opacity: 0; transform: scale(0.96) translateY(8px); } 100% { opacity: 1; transform: scale(1) translateY(0); } }
        .modal-close { position: sticky; top: 0; float: right; background: rgba(255,255,255,0.04); border: none; color: rgba(255,200,150,0.6); font-size: 1.2rem; width: 2.2rem; height: 2.2rem; border-radius: 50%; cursor: pointer; transition: all 0.3s ease; z-index: 10; display: flex; align-items: center; justify-content: center; line-height: 1; font-weight: 300; }
        .modal-close:hover { background: rgba(255,80,80,0.15); color: #ff8a8a; transform: rotate(90deg); }
        .modal-title { font-size: 1.6rem; font-weight: 600; margin-bottom: 0.2rem; background: linear-gradient(to right, #ffd76a, #f5b04a); -webkit-background-clip: text; background-clip: text; color: transparent; }
        .modal-desc { color: rgba(255,200,150,0.5); font-size: 0.95rem; margin-bottom: 1rem; line-height: 1.5; }
        .modal-stats { display: flex; gap: 1.2rem; flex-wrap: wrap; margin-bottom: 1.2rem; }
        .modal-stat { color: rgba(255,200,150,0.4); font-size: 0.8rem; }
        .modal-stat i { color: #f5b04a; margin-right: 0.3rem; }
        .modal-section { margin-bottom: 1rem; }
        .modal-section h4 { color: rgba(255,200,150,0.6); font-size: 0.9rem; font-weight: 500; margin-bottom: 0.5rem; display: flex; align-items: center; gap: 0.5rem; }
        .modal-section h4 i { color: #f5b04a; }

        .h-slider { position: relative; overflow: hidden; border-radius: 1rem; background: rgba(0,0,0,0.25); margin-top: 0.3rem; user-select: none; }
        .h-slider-track { display: flex; transition: transform 0.5s cubic-bezier(0.25,0.46,0.45,0.94); will-change: transform; touch-action: pan-y; }
        .h-slide { min-width: 100%; flex-shrink: 0; padding: 0.5rem; display: flex; flex-direction: column; align-items: center; }
        .h-slide img { width: 100%; max-height: 300px; object-fit: contain; border-radius: 0.6rem; background: rgba(0,0,0,0.2); display: block; pointer-events: none; }
        .h-slide .slide-name { text-align: center; color: rgba(255,200,150,0.2); font-size: 0.65rem; margin-top: 0.3rem; }
        .h-slide .slide-actions { display: flex; gap: 0.5rem; margin-top: 0.3rem; flex-wrap: wrap; justify-content: center; }
        .h-slide .slide-actions button { background: rgba(255,255,255,0.04); border: none; color: rgba(255,200,150,0.6); padding: 0.2rem 0.6rem; border-radius: 0.4rem; font-size: 0.6rem; cursor: pointer; transition: all 0.2s ease; }
        .h-slide .slide-actions button:hover { background: rgba(245,176,74,0.15); }
        .h-slider-btn { position: absolute; top: 50%; transform: translateY(-50%); background: linear-gradient(135deg, rgba(0,0,0,0.5), rgba(0,0,0,0.3)); border: 1px solid rgba(255,200,150,0.05); color: #fff; width: 2.5rem; height: 2.5rem; border-radius: 50%; cursor: pointer; transition: all 0.3s ease; z-index: 5; display: flex; align-items: center; justify-content: center; font-size: 1rem; backdrop-filter: blur(4px); box-shadow: 0 4px 15px rgba(0,0,0,0.3); }
        .h-slider-btn:hover { background: linear-gradient(135deg, rgba(245,176,74,0.3), rgba(245,176,74,0.15)); transform: translateY(-50%) scale(1.1); box-shadow: 0 0 30px rgba(245,176,74,0.15); }
        .h-slider-btn.prev { left: 0.5rem; }
        .h-slider-btn.next { right: 0.5rem; }
        .h-slider-dots { display: flex; justify-content: center; gap: 0.6rem; padding: 0.6rem 0; }
        .h-slider-dots button { width: 10px; height: 10px; border-radius: 50%; border: 2px solid rgba(255,200,150,0.15); background: transparent; cursor: pointer; transition: all 0.3s ease; padding: 0; }
        .h-slider-dots button.active { background: #f5b04a; border-color: #f5b04a; transform: scale(1.2); box-shadow: 0 0 15px rgba(245,176,74,0.2); }
        .h-slider-dots button:hover { border-color: rgba(245,176,74,0.4); }

        .v-slider { position: relative; border-radius: 1rem; background: linear-gradient(135deg, rgba(0,0,0,0.3), rgba(0,0,0,0.15)); margin-top: 0.3rem; border: 1px solid rgba(255,200,150,0.04); height: 400px; overflow: hidden; display: flex; flex-direction: column; }
        .v-slide { flex: 1; display: flex; flex-direction: column; padding: 1rem; overflow: hidden; min-height: 0; }
        .v-slide .v-header { display: flex; justify-content: space-between; align-items: center; margin-bottom: 0.5rem; padding-bottom: 0.3rem; border-bottom: 1px solid rgba(255,200,150,0.04); flex-shrink: 0; }
        .v-slide .v-header .v-name { color: rgba(255,200,150,0.4); font-size: 0.75rem; display: flex; align-items: center; gap: 0.4rem; }
        .v-slide .v-header .v-actions { display: flex; gap: 0.3rem; }
        .v-slide .v-header .v-actions button { background: rgba(255,255,255,0.03); border: none; color: rgba(255,200,150,0.5); padding: 0.15rem 0.5rem; border-radius: 0.3rem; font-size: 0.6rem; cursor: pointer; transition: all 0.2s ease; }
        .v-slide .v-header .v-actions button:hover { background: rgba(245,176,74,0.1); }
        .v-slide .v-content { background: rgba(0,0,0,0.2); border-radius: 0.5rem; padding: 0.8rem; font-family: 'Courier New', monospace; font-size: 0.7rem; color: rgba(255,200,150,0.6); white-space: pre-wrap; word-break: break-all; line-height: 1.4; flex: 1; overflow-y: auto; min-height: 0; }
        .v-slide .v-content::-webkit-scrollbar { width: 4px; }
        .v-slide .v-content::-webkit-scrollbar-track { background: rgba(255,255,255,0.01); }
        .v-slide .v-content::-webkit-scrollbar-thumb { background: rgba(255,200,150,0.1); border-radius: 2px; }

        .v-nav { display: flex; justify-content: center; align-items: center; gap: 0.8rem; padding: 0.6rem 0.8rem; flex-shrink: 0; background: rgba(0,0,0,0.2); border-top: 1px solid rgba(255,200,150,0.04); flex-wrap: wrap; }
        .v-nav button { background: rgba(255,255,255,0.04); border: none; color: rgba(255,200,150,0.5); padding: 0.3rem 0.8rem; border-radius: 0.4rem; font-size: 0.7rem; cursor: pointer; transition: all 0.2s ease; }
        .v-nav button:hover { background: rgba(245,176,74,0.1); }
        .v-nav button:disabled { opacity: 0.2; cursor: not-allowed; }
        .v-nav .v-counter { color: rgba(255,200,150,0.2); font-size: 0.7rem; min-width: 60px; text-align: center; }
        .v-nav .v-dots { display: flex; gap: 0.4rem; align-items: center; }
        .v-nav .v-dots button { width: 8px; height: 8px; border-radius: 50%; border: 1px solid rgba(255,200,150,0.12); background: transparent; cursor: pointer; transition: all 0.3s ease; padding: 0; min-width: auto; }
        .v-nav .v-dots button.active { background: #f5b04a; border-color: #f5b04a; transform: scale(1.2); box-shadow: 0 0 15px rgba(245,176,74,0.2); }
        .v-nav .v-dots button:hover { border-color: rgba(245,176,74,0.4); }

        .modal-files { display: flex; flex-direction: column; gap: 0.3rem; }
        .modal-file { background: rgba(0,0,0,0.15); padding: 0.35rem 0.7rem; border-radius: 0.5rem; display: flex; justify-content: space-between; align-items: center; border: 1px solid rgba(255,200,150,0.02); transition: all 0.2s ease; }
        .modal-file:hover { background: rgba(0,0,0,0.3); }
        .modal-file span { color: rgba(255,200,150,0.4); font-size: 0.75rem; display: flex; align-items: center; gap: 0.4rem; }
        .modal-file .file-actions { display: flex; gap: 0.2rem; }
        .modal-file .file-actions button { background: rgba(255,255,255,0.02); border: none; color: rgba(255,200,150,0.4); padding: 0.1rem 0.4rem; border-radius: 0.3rem; font-size: 0.6rem; cursor: pointer; transition: all 0.2s ease; }
        .modal-file .file-actions button:hover { background: rgba(245,176,74,0.1); }

        .modal-release { background: rgba(245,176,74,0.04); border: 1px solid rgba(245,176,74,0.06); border-radius: 0.7rem; padding: 0.6rem 0.8rem; margin-bottom: 0.4rem; display: flex; align-items: center; justify-content: space-between; flex-wrap: wrap; gap: 0.5rem; }
        .modal-release .release-info { flex: 1; }
        .modal-release .release-tag { color: #f5b04a; font-weight: 500; font-size: 0.85rem; }
        .modal-release .release-date { color: rgba(255,200,150,0.2); font-size: 0.65rem; margin-left: 0.6rem; }
        .modal-release .release-name { color: rgba(255,200,150,0.4); font-size: 0.8rem; margin-top: 0.1rem; }
        .modal-release .release-actions { display: flex; gap: 0.3rem; flex-shrink: 0; flex-wrap: wrap; }
        .modal-release .release-actions button { background: rgba(255,255,255,0.03); border: none; color: rgba(255,200,150,0.4); padding: 0.2rem 0.6rem; border-radius: 0.4rem; font-size: 0.6rem; cursor: pointer; transition: all 0.2s ease; }
        .modal-release .release-actions button:hover { background: rgba(245,176,74,0.1); }

        .toast { position: fixed; bottom: 2rem; right: 2rem; background: rgba(40,20,30,0.92); backdrop-filter: blur(8px); padding: 0.6rem 1rem; border-radius: 0.8rem; color: #fff; border: 1px solid rgba(255,200,150,0.06); box-shadow: 0 12px 24px rgba(0,0,0,0.4); z-index: 2000; animation: toastIn 0.3s ease; display: none; font-size: 0.85rem; }
        .toast.show { display: flex; align-items: center; gap: 0.5rem; }
        @keyframes toastIn { 0% { opacity: 0; transform: translateY(10px) scale(0.95); } 100% { opacity: 1; transform: translateY(0) scale(1); } }
        .toast i { color: #f5b04a; }

        .floating-particles { position: fixed; top: 0; left: 0; width: 100vw; height: 100vh; z-index: 0; pointer-events: none; overflow: hidden; }
        .floating-particle { position: absolute; width: 4px; height: 4px; border-radius: 50%; background: rgba(245,176,74,0.08); animation: floatParticle 20s linear infinite; }
        .floating-particle:nth-child(1) { left: 10%; animation-duration: 22s; animation-delay: 0s; width: 6px; height: 6px; }
        .floating-particle:nth-child(2) { left: 25%; animation-duration: 18s; animation-delay: 3s; width: 3px; height: 3px; }
        .floating-particle:nth-child(3) { left: 40%; animation-duration: 25s; animation-delay: 5s; width: 5px; height: 5px; }
        .floating-particle:nth-child(4) { left: 55%; animation-duration: 16s; animation-delay: 1s; width: 4px; height: 4px; }
        .floating-particle:nth-child(5) { left: 70%; animation-duration: 20s; animation-delay: 4s; width: 7px; height: 7px; }
        .floating-particle:nth-child(6) { left: 85%; animation-duration: 23s; animation-delay: 2s; width: 3px; height: 3px; }
        .floating-particle:nth-child(7) { left: 50%; animation-duration: 19s; animation-delay: 6s; width: 5px; height: 5px; }
        .floating-particle:nth-child(8) { left: 15%; animation-duration: 21s; animation-delay: 7s; width: 4px; height: 4px; }
        .floating-particle:nth-child(9) { left: 65%; animation-duration: 17s; animation-delay: 8s; width: 6px; height: 6px; }
        .floating-particle:nth-child(10) { left: 35%; animation-duration: 24s; animation-delay: 9s; width: 3px; height: 3px; }
        @keyframes floatParticle { 0% { transform: translateY(100vh) scale(0); opacity: 0; } 10% { opacity: 0.6; } 90% { opacity: 0.6; } 100% { transform: translateY(-10vh) scale(1); opacity: 0; } }

        .modal-content::-webkit-scrollbar { width: 4px; }
        .modal-content::-webkit-scrollbar-track { background: rgba(255,255,255,0.01); }
        .modal-content::-webkit-scrollbar-thumb { background: rgba(255,200,150,0.06); border-radius: 2px; }

        @media (max-width: 768px) {
            .wrapper { padding: 0.8rem; max-height: 96vh; position: relative; top: auto; left: auto; transform: none; margin: 0 auto; }
            .glass-card { padding: 1rem 0.8rem; border-radius: 1.8rem; }
            .header { flex-direction: column; align-items: flex-start; gap: 0.6rem; }
            .header-left { width: 100%; }
            .badge-github { width: 100%; justify-content: center; font-size: 0.7rem; }
            .repo-grid { gap: 0.6rem; grid-template-columns: 1fr; }
            .modal-content { padding: 1rem; }
            .modal-stats { gap: 0.6rem; }
            .h-slide img { max-height: 200px; }
            .h-slider-btn { width: 2rem; height: 2rem; font-size: 0.8rem; }
            .v-slider { height: 320px; }
            .modal-release { flex-direction: column; align-items: flex-start; }
            .modal-release .release-actions { width: 100%; justify-content: flex-start; }
            .brand::after { display: none; }
            .tagline { border-left: none; border-right: none; padding: 0.5rem 0; }
            .footer-links { flex-direction: column; align-items: center; text-align: center; }
            .repo-stats { gap: 0.5rem; font-size: 0.6rem; }
            .about-stats { grid-template-columns: 1fr 1fr; }
            .top-menu { gap: 0.3rem; }
            .top-menu button { font-size: 0.75rem; padding: 0.3rem 0.8rem; }
        }
        @media (max-height: 700px) {
            .glass-card { padding: 1.2rem; }
            .header { margin-bottom: 0.8rem; }
            .tagline { margin-bottom: 1rem; padding: 0.3rem 0.8rem; font-size: 0.85rem; }
            .repo-grid { margin: 1rem 0 1.2rem; gap: 0.8rem; }
            .repo-card { padding: 1rem 0.8rem 0.8rem; }
            .footer-links { margin-top: 1.2rem; padding-top: 1rem; }
            .brand { font-size: 1.4rem; }
            .avatar { width: 42px; height: 42px; }
            .avatar .fallback-icon { font-size: 1.6rem; }
            .h-slide img { max-height: 150px; }
            .v-slider { height: 280px; }
            .v-slide .v-content { font-size: 0.6rem; }
        }
        @media (min-width: 769px) {
            .wrapper { position: absolute; top: 50%; left: 50%; transform: translate(-50%, -50%); }
        }
    </style>
</head>
<body>

    <!-- ЗАКАТ -->
    <div class="sunset-bg">
        <div class="sunset-gradient"></div>
        <div class="sun"></div>
        <div class="clouds">
            <div class="cloud"></div>
            <div class="cloud"></div>
            <div class="cloud"></div>
            <div class="cloud"></div>
        </div>
    </div>

    <!-- ЗВЁЗДЫ -->
    <div class="stars-bg">
        <div class="stars-layer"></div>
        <div class="stars-layer"></div>
        <div class="stars-layer"></div>
        <div class="bright-star"></div>
        <div class="bright-star"></div>
        <div class="bright-star"></div>
        <div class="bright-star"></div>
        <div class="bright-star"></div>
        <div class="bright-star"></div>
        <div class="bright-star"></div>
        <div class="bright-star"></div>
    </div>

    <!-- ПАДАЮЩИЕ ЗВЁЗДЫ -->
    <div class="shooting-stars">
        <div class="shooting-star"><div class="star-dot"></div><div class="star-tail"></div></div>
        <div class="shooting-star"><div class="star-dot"></div><div class="star-tail"></div></div>
        <div class="shooting-star"><div class="star-dot"></div><div class="star-tail"></div></div>
        <div class="shooting-star"><div class="star-dot"></div><div class="star-tail"></div></div>
        <div class="shooting-star"><div class="star-dot"></div><div class="star-tail"></div></div>
        <div class="shooting-star"><div class="star-dot"></div><div class="star-tail"></div></div>
        <div class="shooting-star"><div class="star-dot"></div><div class="star-tail"></div></div>
        <div class="shooting-star"><div class="star-dot"></div><div class="star-tail"></div></div>
    </div>

    <canvas id="particles-canvas"></canvas>

    <div class="wrapper">
        <div class="glass-card">
            <!-- ШАПКА -->
            <div class="header">
                <div class="header-left">
                    <div class="avatar-wrapper">
                        <div class="avatar" id="avatarContainer">
                            <i class="fas fa-user-circle fallback-icon"></i>
                        </div>
                    </div>
                    <div class="brand-wrapper">
                        <span class="brand">RepowerStudio</span>
                        <span class="brand-sub">github.com/repowerstudio</span>
                    </div>
                </div>
                <div class="badge-github" id="refreshBadge">
                    <i class="fab fa-github"></i>
                    <span>Обновить</span>
                    <i class="fas fa-sync-alt" style="font-size:0.55rem;opacity:0.4;"></i>
                </div>
            </div>

            <!-- МЕНЮ -->
            <div class="top-menu">
                <button class="active" data-page="repos"><i class="fas fa-code"></i> Репозитории</button>
                <button data-page="about"><i class="fas fa-info-circle"></i> О проекте</button>
                <button data-page="settings"><i class="fas fa-sliders-h"></i> Настройки</button>
            </div>

            <!-- СТРАНИЦА РЕПОЗИТОРИЕВ -->
            <div class="page active" id="page-repos">
                <div class="tagline">
                    <i class="fas fa-code" style="color:rgba(245,176,74,0.3);"></i>
                    Инструменты для разработчиков · Open Source
                    <span class="loader-small" id="loaderIndicator">
                        <span class="loader-dots"><span></span><span></span><span></span></span>
                        загрузка
                    </span>
                </div>

                <div class="repo-grid" id="repoGrid">
                    <div style="grid-column:1/-1;text-align:center;color:rgba(255,200,150,0.2);padding:1.5rem 0;font-size:0.9rem;">
                        <div class="loading-spinner">
                            <div class="spinner-ring"></div>
                            <span>Загрузка репозиториев...</span>
                        </div>
                    </div>
                </div>

                <div class="btn-wrapper">
                    <a href="https://github.com/repowerstudio" target="_blank" class="btn-primary" id="exploreBtn">
                        <i class="fab fa-github"></i> Перейти в GitHub
                        <i class="fas fa-arrow-right"></i>
                    </a>
                </div>
            </div>

            <!-- СТРАНИЦА О ПРОЕКТЕ -->
            <div class="page" id="page-about">
                <div class="tagline">
                    <i class="fas fa-info-circle" style="color:rgba(245,176,74,0.3);"></i>
                    О проекте
                </div>
                <div style="color:rgba(255,200,150,0.5);line-height:1.8;padding:0.5rem 0;">
                    <p style="margin-bottom:0.8rem;">
                        <strong style="color:rgba(255,200,150,0.8);">RepowerStudio</strong> — это творческая студия, 
                        создающая инструменты для разработчиков и красивые веб-интерфейсы.
                    </p>
                    
                    <div class="about-stats">
                        <div class="about-stat">
                            <span class="stat-number" id="statRepos">0</span>
                            <span class="stat-label">Репозиториев</span>
                        </div>
                        <div class="about-stat">
                            <span class="stat-number">∞</span>
                            <span class="stat-label">Идей</span>
                        </div>
                        <div class="about-stat">
                            <span class="stat-number">✨</span>
                            <span class="stat-label">Креативности</span>
                        </div>
                    </div>

                    <div style="margin:1rem 0;">
                        <div style="color:rgba(255,200,150,0.3);font-size:0.8rem;margin-bottom:0.5rem;">Технологии</div>
                        <div class="tech-stack">
                            <span class="tech-tag"><i class="fab fa-js"></i> JavaScript</span>
                            <span class="tech-tag"><i class="fab fa-react"></i> React</span>
                            <span class="tech-tag"><i class="fab fa-python"></i> Python</span>
                            <span class="tech-tag"><i class="fab fa-node-js"></i> Node.js</span>
                            <span class="tech-tag"><i class="fab fa-github"></i> GitHub</span>
                            <span class="tech-tag"><i class="fas fa-cloud"></i> Cloud</span>
                        </div>
                    </div>

                    <p style="font-size:0.85rem;color:rgba(255,200,150,0.2);">
                        <i class="fas fa-code"></i> Сделано с ❤️ и ☕ в RepowerStudio
                    </p>
                </div>
            </div>

            <!-- СТРАНИЦА НАСТРОЕК -->
            <div class="page" id="page-settings">
                <div class="tagline">
                    <i class="fas fa-sliders-h" style="color:rgba(245,176,74,0.3);"></i>
                    Настройки интерфейса
                </div>

                <div class="settings-group">
                    <h4><i class="fas fa-eye"></i> Отображение</h4>
                    <div class="setting-item">
                        <span class="setting-label"><i class="fas fa-star"></i> Показывать звёзды</span>
                        <div class="toggle active" id="toggleStars"></div>
                    </div>
                    <div class="setting-item">
                        <span class="setting-label"><i class="fas fa-meteor"></i> Падающие звёзды</span>
                        <div class="toggle active" id="toggleShooting"></div>
                    </div>
                    <div class="setting-item">
                        <span class="setting-label"><i class="fas fa-cloud"></i> Облака</span>
                        <div class="toggle active" id="toggleClouds"></div>
                    </div>
                </div>

                <div class="settings-group">
                    <h4><i class="fas fa-magic"></i> Эффекты</h4>
                    <div class="setting-item">
                        <span class="setting-label"><i class="fas fa-blur"></i> Размытие стекла</span>
                        <div class="toggle active" id="toggleBlur"></div>
                    </div>
                </div>
            </div>

            <!-- ФУТЕР -->
            <div class="footer-links">
                <div class="live-indicator">
                    <span class="pulse-circle"></span>
                    <span id="repoCountStatus">репозитории: 0</span>
                </div>
                <div class="social-icons">
                    <a href="https://github.com/repowerstudio" target="_blank"><i class="fab fa-github"></i></a>
                    <a href="#"><i class="fab fa-twitter"></i></a>
                    <a href="#"><i class="fab fa-discord"></i></a>
                    <a href="#"><i class="fab fa-youtube"></i></a>
                </div>
                <div class="footer-copy">
                    <i class="fas fa-code"></i> 2026 · RepowerStudio
                </div>
            </div>
        </div>
    </div>

    <!-- МОДАЛЬНОЕ ОКНО -->
    <div class="modal-overlay" id="modalOverlay">
        <div class="modal-content" id="modalContent">
            <button class="modal-close" id="modalClose">✕</button>
            <div id="modalBody"></div>
        </div>
    </div>

    <!-- TOAST -->
    <div class="toast" id="toast">
        <i class="fas fa-check-circle"></i>
        <span id="toastMessage">Скопировано!</span>
    </div>

    <script>
        (function() {
            'use strict';

            // ===== ЧАСТИЦЫ =====
            const canvas = document.getElementById('particles-canvas');
            const ctx = canvas.getContext('2d');
            let w, h;
            let particles = [];
            const PARTICLE_COUNT = 30;

            function resize() {
                w = window.innerWidth;
                h = window.innerHeight;
                canvas.width = w;
                canvas.height = h;
            }
            window.addEventListener('resize', resize);
            resize();

            class Particle {
                constructor() { this.reset(); }
                reset() {
                    this.x = Math.random() * w;
                    this.y = Math.random() * h;
                    this.r = Math.random() * 1.5 + 0.5;
                    this.sx = (Math.random() - 0.5) * 0.15;
                    this.sy = (Math.random() - 0.5) * 0.15;
                    this.o = Math.random() * 0.2 + 0.05;
                }
                update() {
                    this.x += this.sx;
                    this.y += this.sy;
                    if (this.x < 0 || this.x > w) this.sx *= -1;
                    if (this.y < 0 || this.y > h) this.sy *= -1;
                }
                draw() {
                    ctx.beginPath();
                    ctx.arc(this.x, this.y, this.r, 0, Math.PI * 2);
                    ctx.fillStyle = `rgba(255,200,150,${this.o})`;
                    ctx.shadowColor = 'rgba(245,176,74,0.05)';
                    ctx.shadowBlur = 3;
                    ctx.fill();
                }
            }

            for (let i = 0; i < PARTICLE_COUNT; i++) particles.push(new Particle());

            function drawLines() {
                for (let i = 0; i < particles.length; i++) {
                    for (let j = i + 1; j < particles.length; j++) {
                        const dx = particles[i].x - particles[j].x;
                        const dy = particles[i].y - particles[j].y;
                        const d = Math.sqrt(dx * dx + dy * dy);
                        if (d < 60) {
                            const o = (1 - d / 60) * 0.05;
                            ctx.beginPath();
                            ctx.moveTo(particles[i].x, particles[i].y);
                            ctx.lineTo(particles[j].x, particles[j].y);
                            ctx.strokeStyle = `rgba(245,176,74,${o})`;
                            ctx.lineWidth = 0.3;
                            ctx.stroke();
                        }
                    }
                }
            }

            function animateParticles() {
                ctx.clearRect(0, 0, w, h);
                particles.forEach(p => { p.update();
                    p.draw(); });
                drawLines();
                requestAnimationFrame(animateParticles);
            }
            animateParticles();

            // ===== TOAST =====
            function showToast(msg, icon = 'fa-check-circle') {
                const t = document.getElementById('toast');
                document.getElementById('toastMessage').textContent = msg;
                t.querySelector('i').className = `fas ${icon}`;
                t.classList.add('show');
                clearTimeout(t._t);
                t._t = setTimeout(() => t.classList.remove('show'), 2000);
            }

            // ===== КОПИРОВАНИЕ =====
            async function copyText(text) {
                try {
                    await navigator.clipboard.writeText(text);
                    showToast('Скопировано!');
                } catch {
                    const ta = document.createElement('textarea');
                    ta.value = text;
                    document.body.appendChild(ta);
                    ta.select();
                    document.execCommand('copy');
                    document.body.removeChild(ta);
                    showToast('Скопировано!');
                }
            }

            function downloadFile(url, name) {
                const a = document.createElement('a');
                a.href = url;
                a.download = name;
                document.body.appendChild(a);
                a.click();
                document.body.removeChild(a);
                showToast('Скачивание начато!', 'fa-download');
            }

            // ===== DOM =====
            const grid = document.getElementById('repoGrid');
            const loader = document.getElementById('loaderIndicator');
            const countStatus = document.getElementById('repoCountStatus');
            const modalOverlay = document.getElementById('modalOverlay');
            const modalBody = document.getElementById('modalBody');
            const modalClose = document.getElementById('modalClose');
            const refreshBadge = document.getElementById('refreshBadge');

            const USERNAME = 'repowerstudio';

            function esc(html) {
                const d = document.createElement('div');
                d.textContent = html;
                return d.innerHTML;
            }

            // ===== АВАТАР =====
            async function loadAvatar() {
                const container = document.getElementById('avatarContainer');
                try {
                    const res = await fetch(`https://api.github.com/users/${USERNAME}`);
                    if (res.ok) {
                        const data = await res.json();
                        if (data.avatar_url) {
                            container.innerHTML = `<img src="${data.avatar_url}" alt="RepowerStudio" />`;
                        }
                    }
                } catch (e) {}
            }
            loadAvatar();

            // ===== ЦВЕТА ЯЗЫКОВ =====
            const langColors = {
                'javascript': '#f1e05a',
                'typescript': '#3178c6',
                'python': '#3572A5',
                'html': '#e34c26',
                'css': '#563d7c',
                'rust': '#dea584',
                'go': '#00ADD8',
                'java': '#b07219',
                'php': '#4F5D95',
                'ruby': '#701516',
                'c#': '#178600',
                'c++': '#f34b7d',
                'c': '#555555',
                'swift': '#ffac45',
                'kotlin': '#A97BFF',
                'dart': '#00B4AB',
                'vue': '#41b883',
                'react': '#61dafb',
                'angular': '#dd0031',
                'svelte': '#ff3e00'
            };

            function getLangColor(lang) {
                if (!lang) return '#f5b04a';
                const key = lang.toLowerCase();
                return langColors[key] || '#f5b04a';
            }

            function getLanguageIcon(lang) {
                if (!lang) return null;
                const l = lang.toLowerCase();
                const iconMap = {
                    'javascript': 'fab fa-js',
                    'js': 'fab fa-js',
                    'typescript': 'fab fa-js-square',
                    'ts': 'fab fa-js-square',
                    'python': 'fab fa-python',
                    'py': 'fab fa-python',
                    'html': 'fab fa-html5',
                    'css': 'fab fa-css3',
                    'rust': 'fab fa-rust',
                    'rs': 'fab fa-rust',
                    'go': 'fab fa-golang',
                    'golang': 'fab fa-golang',
                    'java': 'fab fa-java',
                    'php': 'fab fa-php',
                    'ruby': 'fab fa-ruby',
                    'rb': 'fab fa-ruby',
                    'c#': 'fab fa-cuttlefish',
                    'csharp': 'fab fa-cuttlefish',
                    'c++': 'fab fa-cuttlefish',
                    'cpp': 'fab fa-cuttlefish',
                    'swift': 'fab fa-swift',
                    'kotlin': 'fab fa-kotlin',
                    'dart': 'fab fa-dart',
                    'vue': 'fab fa-vuejs',
                    'vuejs': 'fab fa-vuejs',
                    'react': 'fab fa-react',
                    'angular': 'fab fa-angular',
                    'svelte': 'fab fa-svelte'
                };
                if (iconMap[l]) return iconMap[l];
                for (const [key, icon] of Object.entries(iconMap)) {
                    if (l.includes(key) || key.includes(l)) return icon;
                }
                return null;
            }

            // ===== КАРТОЧКА РЕПОЗИТОРИЯ =====
            function createCard(repo) {
                const card = document.createElement('div');
                card.className = 'repo-card';

                const iconClass = getLanguageIcon(repo.language);
                let iconHtml = '';
                if (iconClass) {
                    iconHtml = `<span class="repo-icon"><i class="${iconClass}"></i></span>`;
                }

                let langHtml = '';
                if (repo.language) {
                    const langColor = getLangColor(repo.language);
                    langHtml = `<span><span class="lang-dot" style="background:${langColor};"></span> ${esc(repo.language)}</span>`;
                }

                card.innerHTML = `
                    ${iconHtml}
                    <h3>${esc(repo.name)}</h3>
                    <div class="repo-desc">${esc(repo.description || 'Нет описания')}</div>
                    <div class="repo-stats">
                        <span><i class="fas fa-star"></i> ${repo.stargazers_count || 0}</span>
                        <span><i class="fas fa-code-branch"></i> ${repo.forks_count || 0}</span>
                        ${langHtml}
                    </div>
                `;

                card.addEventListener('click', () => openModal(repo));
                return card;
            }

            function renderRepos(data) {
                grid.innerHTML = '';
                data.sort((a, b) => b.stargazers_count - a.stargazers_count);
                data.forEach(r => grid.appendChild(createCard(r)));

                countStatus.textContent = `репозитории: ${data.length}`;
                loader.innerHTML = `<span style="color:#f5b04a;">●</span> ${data.length} загружено`;
                
                const statRepos = document.getElementById('statRepos');
                if (statRepos) statRepos.textContent = data.length;
            }

            // ===== ЗАГРУЗКА РЕПОЗИТОРИЕВ =====
            async function fetchRepos() {
                try {
                    const response = await fetch(`https://api.github.com/users/${USERNAME}/repos?sort=updated&per_page=15`);
                    if (!response.ok) throw new Error(`Ошибка API: ${response.status}`);
                    const data = await response.json();
                    if (data && data.length > 0) {
                        renderRepos(data);
                        showToast('Данные загружены через GitHub API', 'fa-check-circle');
                        return;
                    }
                    showToast('Нет репозиториев', 'fa-info-circle');
                } catch (err) {
                    console.error('Ошибка загрузки:', err);
                    showToast('Ошибка загрузки данных', 'fa-exclamation-circle');
                    grid.innerHTML = `
                        <div style="grid-column:1/-1;text-align:center;color:rgba(255,200,150,0.3);padding:2rem 0;">
                            <i class="fas fa-exclamation-triangle" style="font-size:2rem;display:block;margin-bottom:0.5rem;color:rgba(255,200,150,0.3);"></i>
                            Не удалось загрузить репозитории
                            <div style="font-size:0.8rem;margin-top:0.3rem;opacity:0.5;">${esc(err.message)}</div>
                        </div>
                    `;
                    loader.innerHTML = `<span style="color:#e8843a;">●</span> ошибка`;
                    countStatus.textContent = 'репозитории: —';
                }
            }

            // ===== СЛАЙДЕРЫ =====
            function initHSlider(container, items) {
                if (!container || !items.length) return;
                const track = container.querySelector('.h-slider-track');
                const dots = container.querySelector('.h-slider-dots');
                track.innerHTML = '';
                dots.innerHTML = '';
                let current = 0;
                const total = items.length;

                function updateSlider(index) {
                    current = index;
                    track.style.transform = `translateX(-${current * 100}%)`;
                    dots.querySelectorAll('button').forEach((btn, i) => {
                        btn.classList.toggle('active', i === current);
                    });
                }

                items.forEach((item, i) => {
                    const slide = document.createElement('div');
                    slide.className = 'h-slide';
                    slide.innerHTML = `
                        <img src="${item.download_url}" alt="${esc(item.name)}" loading="lazy" />
                        <div class="slide-name">${esc(item.name)}</div>
                        <div class="slide-actions">
                            <button class="copy-img-btn" data-url="${item.download_url}"><i class="fas fa-copy"></i> Копировать</button>
                            <button class="download-img-btn" data-url="${item.download_url}" data-name="${esc(item.name)}"><i class="fas fa-download"></i> Скачать</button>
                        </div>
                    `;
                    track.appendChild(slide);
                });

                for (let i = 0; i < total; i++) {
                    const btn = document.createElement('button');
                    btn.className = i === 0 ? 'active' : '';
                    btn.addEventListener('click', () => updateSlider(i));
                    dots.appendChild(btn);
                }

                const prevBtn = container.querySelector('.h-slider-btn.prev');
                const nextBtn = container.querySelector('.h-slider-btn.next');
                const newPrev = prevBtn.cloneNode(true);
                const newNext = nextBtn.cloneNode(true);
                prevBtn.parentNode.replaceChild(newPrev, prevBtn);
                nextBtn.parentNode.replaceChild(newNext, nextBtn);

                newPrev.addEventListener('click', () => updateSlider(current > 0 ? current - 1 : total - 1));
                newNext.addEventListener('click', () => updateSlider(current < total - 1 ? current + 1 : 0));
            }

            const fileCache = {};
            let vCurrentFile = 0;
            let vFiles = [];

            function initVSlider(container, files) {
                if (!container || !files.length) return;
                vFiles = files;
                vCurrentFile = 0;
                container.innerHTML = '';

                const slide = document.createElement('div');
                slide.className = 'v-slide';
                slide.id = 'vSlide';
                const nav = document.createElement('div');
                nav.className = 'v-nav';
                nav.id = 'vNav';
                container.appendChild(slide);
                container.appendChild(nav);
                updateVSlider(container);
            }

            function updateVSlider(container) {
                const slide = container.querySelector('#vSlide');
                const nav = container.querySelector('#vNav');
                if (!slide || !nav) return;

                const file = vFiles[vCurrentFile];
                const total = vFiles.length;
                const cached = fileCache[file.download_url];

                let nameHtml = `<i class="fas fa-file-code"></i> ${esc(file.name)}`;
                if (total > 1) nameHtml += ` <span style="opacity:0.3;font-size:0.6rem;">(${vCurrentFile+1}/${total})</span>`;

                slide.innerHTML = `
                    <div class="v-header">
                        <span class="v-name">${nameHtml}</span>
                        <div class="v-actions">
                            <button class="v-copy-btn" data-url="${file.download_url}"><i class="fas fa-copy"></i></button>
                            <button class="v-download-btn" data-url="${file.download_url}" data-name="${esc(file.name)}"><i class="fas fa-download"></i></button>
                        </div>
                    </div>
                    <div class="v-content">${cached ? esc(cached) : 'Загрузка содержимого...'}</div>
                `;

                if (!cached) {
                    fetch(file.download_url).then(res => res.text()).then(text => {
                        const content = slide.querySelector('.v-content');
                        const displayText = text.substring(0, 5000) + (text.length > 5000 ? '\n... (обрезано)' : '');
                        content.textContent = displayText;
                        fileCache[file.download_url] = displayText;
                    }).catch(() => {
                        const content = slide.querySelector('.v-content');
                        content.textContent = 'Ошибка загрузки файла';
                        content.style.color = 'rgba(255,150,150,0.4)';
                    });
                }

                let dotsHtml = '';
                for (let i = 0; i < total; i++) {
                    dotsHtml += `<button class="${i === vCurrentFile ? 'active' : ''}" data-index="${i}"></button>`;
                }

                nav.innerHTML = `
                    <button class="v-prev" ${vCurrentFile === 0 ? 'disabled' : ''}><i class="fas fa-chevron-up"></i></button>
                    <div class="v-dots">${dotsHtml}</div>
                    <span class="v-counter">${vCurrentFile+1} / ${total}</span>
                    <button class="v-next" ${vCurrentFile === total-1 ? 'disabled' : ''}><i class="fas fa-chevron-down"></i></button>
                `;

                slide.querySelector('.v-copy-btn').addEventListener('click', async (e) => {
                    e.stopPropagation();
                    const url = e.target.closest('button').dataset.url;
                    const cachedContent = fileCache[url];
                    if (cachedContent) { copyText(cachedContent); } else {
                        try { const res = await fetch(url);
                            const text = await res.text();
                            copyText(text); } catch { showToast('Ошибка загрузки', 'fa-exclamation-circle'); }
                    }
                });

                slide.querySelector('.v-download-btn').addEventListener('click', (e) => {
                    e.stopPropagation();
                    const btn = e.target.closest('button');
                    downloadFile(btn.dataset.url, btn.dataset.name);
                });

                nav.querySelectorAll('.v-dots button').forEach((btn, i) => {
                    btn.addEventListener('click', () => { vCurrentFile = i;
                        updateVSlider(container); });
                });

                nav.querySelector('.v-prev').addEventListener('click', () => {
                    if (vCurrentFile > 0) { vCurrentFile--;
                        updateVSlider(container); }
                });
                nav.querySelector('.v-next').addEventListener('click', () => {
                    if (vCurrentFile < vFiles.length - 1) { vCurrentFile++;
                        updateVSlider(container); }
                });
            }

            // ===== ОТКРЫТИЕ МОДАЛЬНОГО ОКНА =====
            async function openModal(repo) {
                modalOverlay.classList.add('active');
                modalBody.innerHTML = `
                    <div class="loading-spinner">
                        <div class="spinner-ring"></div>
                        <span>Загрузка данных...</span>
                    </div>
                `;

                try {
                    let files = [],
                        releases = [];
                    try {
                        const [contentsRes, releasesRes] = await Promise.all([
                            fetch(`https://api.github.com/repos/${USERNAME}/${repo.name}/contents`),
                            fetch(`https://api.github.com/repos/${USERNAME}/${repo.name}/releases?per_page=10`)
                        ]);
                        if (contentsRes.ok) files = await contentsRes.json();
                        if (releasesRes.ok) releases = await releasesRes.json();
                    } catch (e) {}

                    const images = [],
                        textFiles = [],
                        otherFiles = [];
                    if (Array.isArray(files)) {
                        files.forEach(f => {
                            const ext = f.name.split('.').pop().toLowerCase();
                            if (['png', 'jpg', 'jpeg', 'gif', 'svg', 'webp', 'bmp', 'ico'].includes(ext)) {
                                images.push(f);
                            } else if (['txt', 'md', 'json', 'yml', 'yaml', 'xml', 'csv', 'log', 'sh',
                                    'bash', 'py', 'js', 'ts', 'jsx', 'tsx', 'html', 'css', 'scss', 'less',
                                    'vue', 'svelte', 'go', 'rs', 'c', 'cpp', 'h', 'hpp', 'java', 'kt',
                                    'kts', 'dart', 'swift', 'rb', 'php', 'pl', 'pm', 'r', 'lua', 'sql',
                                    'prisma', 'graphql', 'gql'
                                ].includes(ext)) {
                                textFiles.push(f);
                            } else {
                                otherFiles.push(f);
                            }
                        });
                    }

                    const langColor = getLangColor(repo.language);
                    let html = `
                        <h2 class="modal-title"><i class="fas fa-folder-open" style="color:#f5b04a;margin-right:0.5rem;"></i>${esc(repo.name)}</h2>
                        <p class="modal-desc">${esc(repo.description || 'Нет описания')}</p>
                        <div class="modal-stats">
                            <span class="modal-stat"><i class="fas fa-star"></i> ${repo.stargazers_count || 0}</span>
                            <span class="modal-stat"><i class="fas fa-code-branch"></i> ${repo.forks_count || 0}</span>
                            ${repo.language ? `<span class="modal-stat"><i class="fas fa-circle" style="color:${langColor};"></i> ${esc(repo.language)}</span>` : ''}
                            <span class="modal-stat"><i class="fas fa-calendar-alt"></i> ${new Date().toLocaleDateString()}</span>
                        </div>
                    `;

                    // РЕЛИЗЫ
                    if (releases.length > 0) {
                        html += `<div class="modal-section"><h4><i class="fas fa-tag"></i> Релизы (${releases.length})</h4>`;
                        releases.slice(0, 10).forEach(r => {
                            const assets = r.assets || [];
                            html += `
                                <div class="modal-release">
                                    <div class="release-info">
                                        <span class="release-tag"><i class="fas fa-tag"></i> ${esc(r.tag_name)}</span>
                                        <span class="release-date">${new Date(r.published_at || r.created_at).toLocaleDateString()}</span>
                                        ${r.name ? `<div class="release-name">${esc(r.name)}</div>` : ''}
                                    </div>
                                    <div class="release-actions">
                                        ${assets.slice(0, 3).map(a => `
                                            <button class="download-release-btn" data-url="${a.browser_download_url}" data-name="${esc(a.name)}">
                                                <i class="fas fa-download"></i> ${esc(a.name.length > 12 ? a.name.substring(0, 12)+'…' : a.name)}
                                            </button>
                                        `).join('')}
                                        ${assets.length > 3 ? `<span style="font-size:0.6rem;color:rgba(255,200,150,0.15);">+${assets.length-3}</span>` : ''}
                                    </div>
                                </div>
                            `;
                        });
                        html += `</div>`;
                    } else {
                        html += `
                            <div class="modal-section">
                                <h4><i class="fas fa-tag"></i> Релизы</h4>
                                <div style="color:rgba(255,200,150,0.2);padding:0.5rem 0;font-size:0.85rem;text-align:center;">
                                    <i class="fas fa-inbox" style="display:block;margin-bottom:0.3rem;font-size:1.2rem;"></i>
                                    Нет релизов
                                </div>
                            </div>
                        `;
                    }

                    // ИЗОБРАЖЕНИЯ
                    if (images.length > 0) {
                        html += `
                            <div class="modal-section">
                                <h4><i class="fas fa-images"></i> Изображения (${images.length})</h4>
                                <div class="h-slider">
                                    <button class="h-slider-btn prev"><i class="fas fa-chevron-left"></i></button>
                                    <div class="h-slider-track"></div>
                                    <button class="h-slider-btn next"><i class="fas fa-chevron-right"></i></button>
                                    <div class="h-slider-dots"></div>
                                </div>
                            </div>
                        `;
                    }

                    // ТЕКСТОВЫЕ ФАЙЛЫ
                    if (textFiles.length > 0) {
                        html += `
                            <div class="modal-section">
                                <h4><i class="fas fa-file-alt"></i> Текстовые файлы (${textFiles.length})</h4>
                                <div class="v-slider" id="vSliderContainer"></div>
                            </div>
                        `;
                    }

                    // ДРУГИЕ ФАЙЛЫ
                    if (otherFiles.length > 0) {
                        html += `
                            <div class="modal-section">
                                <h4><i class="fas fa-file-code"></i> Другие файлы (${otherFiles.length})</h4>
                                <div class="modal-files">
                        `;
                        otherFiles.slice(0, 15).forEach(f => {
                            html += `
                                <div class="modal-file">
                                    <span><i class="fas fa-file" style="color:#f5b04a;"></i> ${esc(f.name)}</span>
                                    <div class="file-actions">
                                        <button class="copy-file-btn" data-url="${f.download_url}"><i class="fas fa-copy"></i></button>
                                        <button class="download-file-btn" data-url="${f.download_url}" data-name="${esc(f.name)}"><i class="fas fa-download"></i></button>
                                        <button class="view-file-btn" data-url="${f.download_url}" data-name="${esc(f.name)}"><i class="fas fa-eye"></i></button>
                                    </div>
                                </div>
                            `;
                        });
                        html += `</div></div>`;
                    }

                    if (!images.length && !textFiles.length && !otherFiles.length) {
                        html += `
                            <div style="text-align:center;color:rgba(255,200,150,0.15);padding:1rem 0;font-size:0.85rem;">
                                <i class="fas fa-inbox" style="font-size:1.5rem;display:block;margin-bottom:0.2rem;"></i>
                                Нет файлов для отображения
                            </div>
                        `;
                    }

                    modalBody.innerHTML = html;

                    // Инициализация слайдеров
                    const hSlider = modalBody.querySelector('.h-slider');
                    if (hSlider && images.length > 0) initHSlider(hSlider, images);

                    const vSliderContainer = modalBody.querySelector('#vSliderContainer');
                    if (vSliderContainer && textFiles.length > 0) initVSlider(vSliderContainer, textFiles);

                    // Обработчики для файлов
                    modalBody.querySelectorAll('.copy-file-btn').forEach(b => {
                        b.addEventListener('click', async (e) => {
                            e.stopPropagation();
                            try { const res = await fetch(b.dataset.url);
                                const text = await res.text();
                                copyText(text); } catch { showToast('Ошибка загрузки', 'fa-exclamation-circle'); }
                        });
                    });

                    modalBody.querySelectorAll('.download-file-btn').forEach(b => {
                        b.addEventListener('click', (e) => {
                            e.stopPropagation();
                            downloadFile(b.dataset.url, b.dataset.name);
                        });
                    });

                    modalBody.querySelectorAll('.download-release-btn').forEach(b => {
                        b.addEventListener('click', (e) => {
                            e.stopPropagation();
                            downloadFile(b.dataset.url, b.dataset.name);
                        });
                    });

                    modalBody.querySelectorAll('.view-file-btn').forEach(b => {
                        b.addEventListener('click', async (e) => {
                            e.stopPropagation();
                            try {
                                const res = await fetch(b.dataset.url);
                                const text = await res.text();
                                const vw = document.createElement('div');
                                vw.style.cssText =
                                    'position:fixed;top:0;left:0;width:100%;height:100%;background:rgba(0,0,0,0.85);z-index:3000;display:flex;align-items:center;justify-content:center;padding:1rem;';
                                vw.innerHTML = `
                                    <div style="background:linear-gradient(145deg,rgba(40,20,30,0.96),rgba(60,30,40,0.92));border-radius:1.2rem;padding:1.2rem;max-width:750px;width:100%;max-height:80vh;overflow-y:auto;position:relative;">
                                        <button style="position:sticky;top:0;float:right;background:rgba(255,255,255,0.04);border:none;color:#fff;font-size:1.3rem;width:2rem;height:2rem;border-radius:50%;cursor:pointer;">&times;</button>
                                        <h4 style="color:#f5b04a;margin-bottom:0.6rem;font-size:1rem;">${b.dataset.name}</h4>
                                        <pre style="background:rgba(0,0,0,0.25);border-radius:0.6rem;padding:0.6rem;color:rgba(255,200,150,0.6);font-family:monospace;font-size:0.75rem;white-space:pre-wrap;word-break:break-all;max-height:55vh;overflow-y:auto;">${esc(text)}</pre>
                                    </div>
                                `;
                                document.body.appendChild(vw);
                                vw.querySelector('button').addEventListener('click', () => document.body.removeChild(vw));
                                vw.addEventListener('click', (e) => { if (e.target === vw) document.body.removeChild(vw); });
                            } catch { showToast('Ошибка загрузки', 'fa-exclamation-circle'); }
                        });
                    });

                    modalBody.querySelectorAll('.copy-img-btn').forEach(b => {
                        b.addEventListener('click', (e) => { e.stopPropagation();
                            copyText(b.dataset.url); });
                    });
                    modalBody.querySelectorAll('.download-img-btn').forEach(b => {
                        b.addEventListener('click', (e) => { e.stopPropagation();
                            downloadFile(b.dataset.url, b.dataset.name); });
                    });

                } catch (err) {
                    modalBody.innerHTML = `
                        <div style="text-align:center;color:rgba(255,150,150,0.2);padding:1.5rem 0;">
                            <i class="fas fa-exclamation-triangle" style="font-size:1.8rem;display:block;margin-bottom:0.4rem;"></i>
                            Ошибка загрузки
                            <div style="font-size:0.8rem;margin-top:0.2rem;opacity:0.4;">${esc(err.message)}</div>
                        </div>
                    `;
                }
            }

            // ===== ЗАКРЫТИЕ МОДАЛЬНОГО =====
            modalClose.addEventListener('click', () => {
                modalOverlay.classList.remove('active');
            });

            modalOverlay.addEventListener('click', (e) => {
                if (e.target === modalOverlay) {
                    modalOverlay.classList.remove('active');
                }
            });

            // ===== ПЕРЕКЛЮЧЕНИЕ СТРАНИЦ =====
            document.querySelectorAll('.top-menu button').forEach(btn => {
                btn.addEventListener('click', function() {
                    document.querySelectorAll('.top-menu button').forEach(b => b.classList.remove('active'));
                    this.classList.add('active');

                    const page = this.dataset.page;
                    document.querySelectorAll('.page').forEach(p => p.classList.remove('active'));
                    document.getElementById(`page-${page}`).classList.add('active');
                });
            });

            // ===== НАСТРОЙКИ =====
            document.querySelectorAll('.toggle').forEach(toggle => {
                toggle.addEventListener('click', function(e) {
                    e.stopPropagation();
                    this.classList.toggle('active');
                    
                    const isActive = this.classList.contains('active');
                    const target = this.id;
                    
                    if (target === 'toggleStars') {
                        document.querySelectorAll('.stars-bg, .bright-star').forEach(el => {
                            el.style.display = isActive ? '' : 'none';
                        });
                    } else if (target === 'toggleShooting') {
                        document.querySelectorAll('.shooting-stars').forEach(el => {
                            el.style.display = isActive ? '' : 'none';
                        });
                    } else if (target === 'toggleClouds') {
                        document.querySelectorAll('.clouds, .cloud').forEach(el => {
                            el.style.display = isActive ? '' : 'none';
                        });
                    } else if (target === 'toggleBlur') {
                        document.querySelectorAll('.glass-card').forEach(el => {
                            el.style.backdropFilter = isActive ? 'blur(6px)' : 'none';
                            el.style.webkitBackdropFilter = isActive ? 'blur(6px)' : 'none';
                        });
                    }
                    
                    showToast(isActive ? 'Включено' : 'Выключено', 'fa-toggle-on');
                });
            });

            // ===== ОБНОВЛЕНИЕ =====
            refreshBadge.addEventListener('click', () => {
                const icon = refreshBadge.querySelector('.fa-sync-alt');
                icon.classList.add('fa-spin');
                fetchRepos().then(() => {
                    setTimeout(() => {
                        icon.classList.remove('fa-spin');
                        showToast('Обновлено!', 'fa-sync-alt');
                    }, 300);
                }).catch(() => icon.classList.remove('fa-spin'));
            });

            // ===== ЗАПУСК =====
            fetchRepos();

            document.getElementById('exploreBtn').addEventListener('click', function(e) {
                const orig = this.innerHTML;
                this.innerHTML = '<i class="fas fa-spinner fa-pulse"></i> Загрузка...';
                setTimeout(() => { this.innerHTML = orig; }, 500);
            });

            console.log('🌅 RepowerStudio · без тем и чёрного градиента');
        })();
    </script>
</body>
</html>
