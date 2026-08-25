<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>RepowerStudio · GitHub</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css" />
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        html,
        body {
            width: 100%;
            min-height: 100vh;
            background: radial-gradient(ellipse at 30% 20%, #0a0f1a, #030508);
            font-family: 'Segoe UI', system-ui, -apple-system, sans-serif;
            overflow-x: hidden;
            position: relative;
            margin: 0;
            padding: 0;
        }

        .wrapper {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            width: 100%;
            max-width: 1100px;
            padding: 1.5rem;
            z-index: 10;
            max-height: 98vh;
            overflow-y: auto;
        }

        .wrapper::-webkit-scrollbar {
            width: 4px;
        }
        .wrapper::-webkit-scrollbar-track {
            background: rgba(255, 255, 255, 0.02);
        }
        .wrapper::-webkit-scrollbar-thumb {
            background: rgba(255, 255, 255, 0.06);
            border-radius: 2px;
        }

        /* ----- ЗВЁЗДНЫЙ ФОН ----- */
        .stars-bg {
            position: fixed;
            top: 0;
            left: 0;
            width: 100vw;
            height: 100vh;
            z-index: 0;
            pointer-events: none;
            overflow: hidden;
        }

        .stars-layer {
            position: absolute;
            width: 100%;
            height: 100%;
            background-image:
                radial-gradient(2px 2px at 10% 20%, rgba(255, 255, 255, 0.9), transparent),
                radial-gradient(2px 2px at 30% 60%, rgba(255, 255, 255, 0.7), transparent),
                radial-gradient(3px 3px at 50% 10%, rgba(255, 255, 255, 1), transparent),
                radial-gradient(1px 1px at 70% 80%, rgba(255, 255, 255, 0.5), transparent),
                radial-gradient(2px 2px at 90% 40%, rgba(255, 255, 255, 0.8), transparent),
                radial-gradient(1px 1px at 15% 90%, rgba(255, 255, 255, 0.4), transparent),
                radial-gradient(3px 3px at 45% 45%, rgba(255, 255, 255, 1), transparent),
                radial-gradient(2px 2px at 80% 15%, rgba(255, 255, 255, 0.6), transparent),
                radial-gradient(1px 1px at 55% 75%, rgba(255, 255, 255, 0.3), transparent),
                radial-gradient(2px 2px at 25% 35%, rgba(255, 255, 255, 0.7), transparent),
                radial-gradient(3px 3px at 65% 55%, rgba(255, 255, 255, 0.9), transparent),
                radial-gradient(1px 1px at 85% 85%, rgba(255, 255, 255, 0.5), transparent),
                radial-gradient(2px 2px at 5% 50%, rgba(255, 255, 255, 0.6), transparent),
                radial-gradient(2px 2px at 95% 30%, rgba(255, 255, 255, 0.8), transparent),
                radial-gradient(1px 1px at 35% 15%, rgba(255, 255, 255, 0.4), transparent),
                radial-gradient(3px 3px at 75% 70%, rgba(255, 255, 255, 1), transparent),
                radial-gradient(2px 2px at 20% 70%, rgba(255, 255, 255, 0.7), transparent),
                radial-gradient(1px 1px at 60% 25%, rgba(255, 255, 255, 0.5), transparent),
                radial-gradient(2px 2px at 40% 85%, rgba(255, 255, 255, 0.6), transparent),
                radial-gradient(3px 3px at 10% 5%, rgba(255, 255, 255, 0.9), transparent);
            background-size: 100% 100%;
            background-repeat: no-repeat;
            animation: starTwinkle 4s ease-in-out infinite alternate;
        }

        .stars-layer:nth-child(2) {
            background-image:
                radial-gradient(1px 1px at 12% 22%, rgba(255, 255, 255, 0.6), transparent),
                radial-gradient(1px 1px at 33% 65%, rgba(255, 255, 255, 0.4), transparent),
                radial-gradient(2px 2px at 52% 12%, rgba(255, 255, 255, 0.8), transparent),
                radial-gradient(1px 1px at 72% 82%, rgba(255, 255, 255, 0.3), transparent),
                radial-gradient(1px 1px at 92% 42%, rgba(255, 255, 255, 0.5), transparent),
                radial-gradient(2px 2px at 18% 92%, rgba(255, 255, 255, 0.7), transparent),
                radial-gradient(1px 1px at 48% 48%, rgba(255, 255, 255, 0.4), transparent),
                radial-gradient(2px 2px at 82% 18%, rgba(255, 255, 255, 0.6), transparent),
                radial-gradient(1px 1px at 58% 78%, rgba(255, 255, 255, 0.3), transparent),
                radial-gradient(1px 1px at 28% 38%, rgba(255, 255, 255, 0.5), transparent),
                radial-gradient(2px 2px at 68% 58%, rgba(255, 255, 255, 0.7), transparent),
                radial-gradient(1px 1px at 88% 88%, rgba(255, 255, 255, 0.4), transparent),
                radial-gradient(1px 1px at 8% 52%, rgba(255, 255, 255, 0.5), transparent),
                radial-gradient(2px 2px at 98% 32%, rgba(255, 255, 255, 0.6), transparent),
                radial-gradient(1px 1px at 38% 18%, rgba(255, 255, 255, 0.3), transparent),
                radial-gradient(2px 2px at 78% 72%, rgba(255, 255, 255, 0.8), transparent);
            background-size: 100% 100%;
            background-repeat: no-repeat;
            animation: starTwinkle 6s ease-in-out infinite alternate-reverse;
            opacity: 0.7;
        }

        .stars-layer:nth-child(3) {
            background-image:
                radial-gradient(3px 3px at 5% 15%, rgba(200, 220, 255, 1), transparent),
                radial-gradient(4px 4px at 25% 55%, rgba(180, 200, 255, 0.9), transparent),
                radial-gradient(5px 5px at 45% 5%, rgba(220, 235, 255, 1), transparent),
                radial-gradient(3px 3px at 65% 75%, rgba(200, 215, 255, 0.8), transparent),
                radial-gradient(4px 4px at 85% 35%, rgba(190, 210, 255, 0.9), transparent),
                radial-gradient(3px 3px at 10% 85%, rgba(210, 225, 255, 0.8), transparent),
                radial-gradient(5px 5px at 40% 40%, rgba(230, 240, 255, 1), transparent),
                radial-gradient(4px 4px at 75% 10%, rgba(200, 215, 255, 0.9), transparent),
                radial-gradient(3px 3px at 50% 70%, rgba(190, 210, 255, 0.8), transparent),
                radial-gradient(5px 5px at 20% 30%, rgba(220, 235, 255, 1), transparent),
                radial-gradient(4px 4px at 60% 50%, rgba(210, 225, 255, 0.9), transparent),
                radial-gradient(3px 3px at 80% 80%, rgba(200, 215, 255, 0.8), transparent);
            background-size: 100% 100%;
            background-repeat: no-repeat;
            animation: starTwinkle 3s ease-in-out infinite alternate;
            opacity: 0.9;
        }

        @keyframes starTwinkle {
            0% {
                opacity: 0.6;
                transform: scale(1);
            }
            50% {
                opacity: 1;
                transform: scale(1.02);
            }
            100% {
                opacity: 0.7;
                transform: scale(0.98);
            }
        }

        .bright-star {
            position: absolute;
            border-radius: 50%;
            background: white;
            box-shadow: 0 0 20px rgba(255, 255, 255, 0.8), 0 0 60px rgba(100, 180, 255, 0.4);
            animation: brightPulse 2s ease-in-out infinite;
            pointer-events: none;
        }

        .bright-star:nth-child(1) {
            width: 6px;
            height: 6px;
            top: 8%;
            left: 15%;
            animation-delay: 0s;
        }
        .bright-star:nth-child(2) {
            width: 8px;
            height: 8px;
            top: 25%;
            right: 20%;
            animation-delay: 0.7s;
        }
        .bright-star:nth-child(3) {
            width: 5px;
            height: 5px;
            top: 45%;
            left: 8%;
            animation-delay: 1.4s;
        }
        .bright-star:nth-child(4) {
            width: 7px;
            height: 7px;
            bottom: 20%;
            right: 15%;
            animation-delay: 0.3s;
        }
        .bright-star:nth-child(5) {
            width: 9px;
            height: 9px;
            top: 60%;
            right: 8%;
            animation-delay: 1.8s;
        }
        .bright-star:nth-child(6) {
            width: 5px;
            height: 5px;
            top: 5%;
            right: 40%;
            animation-delay: 0.5s;
        }
        .bright-star:nth-child(7) {
            width: 7px;
            height: 7px;
            bottom: 35%;
            left: 25%;
            animation-delay: 1.1s;
        }
        .bright-star:nth-child(8) {
            width: 6px;
            height: 6px;
            top: 40%;
            left: 50%;
            animation-delay: 2.2s;
        }

        @keyframes brightPulse {
            0%,
            100% {
                transform: scale(0.8);
                opacity: 0.6;
                box-shadow: 0 0 15px rgba(255, 255, 255, 0.4);
            }
            50% {
                transform: scale(1.4);
                opacity: 1;
                box-shadow: 0 0 40px rgba(255, 255, 255, 0.9), 0 0 80px rgba(100, 180, 255, 0.5);
            }
        }

        /* ----- ПАДАЮЩИЕ ЗВЁЗДЫ ----- */
        .shooting-stars {
            position: fixed;
            top: 0;
            left: 0;
            width: 100vw;
            height: 100vh;
            z-index: 1;
            pointer-events: none;
            overflow: hidden;
        }

        .shooting-star {
            position: absolute;
            animation: shootStar 4s linear infinite;
            opacity: 0;
        }

        .shooting-star .star-dot {
            position: absolute;
            width: 3px;
            height: 3px;
            background: white;
            border-radius: 50%;
            box-shadow: 0 0 8px 3px rgba(255, 255, 255, 0.4);
            top: 0;
            left: 0;
        }

        .shooting-star .star-tail {
            position: absolute;
            height: 2px;
            background: linear-gradient(to left, rgba(255, 255, 255, 0.9), transparent);
            top: 0.5px;
            right: 3px;
            width: 80px;
            transform-origin: right center;
        }

        .shooting-star:nth-child(1) {
            top: 10%;
            left: 20%;
            animation-delay: 0s;
            animation-duration: 3.5s;
        }
        .shooting-star:nth-child(2) {
            top: 20%;
            left: 60%;
            animation-delay: 2s;
            animation-duration: 4s;
        }
        .shooting-star:nth-child(3) {
            top: 5%;
            left: 40%;
            animation-delay: 4s;
            animation-duration: 3s;
        }
        .shooting-star:nth-child(4) {
            top: 30%;
            left: 80%;
            animation-delay: 1s;
            animation-duration: 4.5s;
        }
        .shooting-star:nth-child(5) {
            top: 15%;
            left: 10%;
            animation-delay: 3s;
            animation-duration: 3.8s;
        }
        .shooting-star:nth-child(6) {
            top: 25%;
            left: 50%;
            animation-delay: 0.5s;
            animation-duration: 3.2s;
        }
        .shooting-star:nth-child(7) {
            top: 8%;
            left: 75%;
            animation-delay: 2.5s;
            animation-duration: 4.2s;
        }
        .shooting-star:nth-child(8) {
            top: 35%;
            left: 30%;
            animation-delay: 1.5s;
            animation-duration: 3.6s;
        }

        @keyframes shootStar {
            0% {
                transform: translate(0, 0) rotate(35deg) scale(0);
                opacity: 0;
            }
            5% {
                opacity: 1;
                transform: translate(30px, 30px) rotate(35deg) scale(0.5);
            }
            15% {
                transform: translate(100px, 100px) rotate(35deg) scale(1);
                opacity: 1;
            }
            85% {
                opacity: 1;
            }
            95% {
                opacity: 0.5;
            }
            100% {
                transform: translate(380px, 380px) rotate(35deg) scale(0.3);
                opacity: 0;
            }
        }

        /* ----- МАТОВОЕ СТЕКЛО (СЛАБЫЙ BLUR) ----- */
        .glass-card {
            background: rgba(18, 30, 50, 0.20);
            backdrop-filter: blur(4px);
            -webkit-backdrop-filter: blur(4px);
            border-radius: 3rem;
            padding: 2.5rem;
            border: 1px solid rgba(255, 255, 255, 0.08);
            box-shadow: 0 40px 80px rgba(0, 0, 0, 0.6), inset 0 1px 0 rgba(255, 255, 255, 0.05);
            animation: cardAppear 0.7s ease;
            transition: all 0.5s ease;
            width: 100%;
        }

        .glass-card:hover {
            box-shadow: 0 50px 100px rgba(0, 0, 0, 0.7), inset 0 1px 0 rgba(255, 255, 255, 0.08);
            background: rgba(18, 30, 50, 0.25);
        }

        @keyframes cardAppear {
            0% {
                opacity: 0;
                transform: translateY(30px) scale(0.97);
            }
            100% {
                opacity: 1;
                transform: translateY(0) scale(1);
            }
        }

        .header {
            display: flex;
            align-items: center;
            justify-content: space-between;
            gap: 1.2rem;
            flex-wrap: wrap;
            margin-bottom: 1.5rem;
            width: 100%;
        }

        .header-left {
            display: flex;
            align-items: center;
            gap: 0.8rem;
        }

        .avatar-wrapper {
            position: relative;
            flex-shrink: 0;
        }

        .avatar-wrapper::after {
            content: '';
            position: absolute;
            inset: -2px;
            border-radius: 50%;
            padding: 2px;
            background: linear-gradient(135deg, #8ab4ff, #7a5cff, #8ab4ff);
            background-size: 300% 300%;
            animation: avatarBorder 3s ease-in-out infinite;
            -webkit-mask: linear-gradient(#fff 0 0) content-box, linear-gradient(#fff 0 0);
            mask: linear-gradient(#fff 0 0) content-box, linear-gradient(#fff 0 0);
            -webkit-mask-composite: xor;
            mask-composite: exclude;
            pointer-events: none;
        }

        @keyframes avatarBorder {
            0%,
            100% {
                background-position: 0% 50%;
            }
            50% {
                background-position: 100% 50%;
            }
        }

        .avatar {
            width: 56px;
            height: 56px;
            border-radius: 50%;
            background: rgba(255, 255, 255, 0.05);
            display: flex;
            align-items: center;
            justify-content: center;
            overflow: hidden;
            position: relative;
            z-index: 1;
        }

        .avatar img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            transition: transform 0.5s ease;
        }

        .avatar:hover img {
            transform: scale(1.1);
        }

        .avatar .fallback-icon {
            font-size: 2.2rem;
            color: #8ab4ff;
            opacity: 0.6;
        }

        .brand-wrapper {
            display: flex;
            flex-direction: column;
        }

        .brand {
            font-size: clamp(1.6rem, 4vw, 2.6rem);
            font-weight: 700;
            background: linear-gradient(145deg, #f0f5ff, #b0d0ff);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            line-height: 1.1;
            position: relative;
            display: inline-block;
        }

        .brand::after {
            content: '✦';
            position: absolute;
            right: -1.5rem;
            top: -0.2rem;
            font-size: 0.8rem;
            color: #8ab4ff;
            opacity: 0.6;
            animation: sparkle 2s ease-in-out infinite;
        }

        @keyframes sparkle {
            0%,
            100% {
                opacity: 0.3;
                transform: scale(0.8) rotate(0deg);
            }
            50% {
                opacity: 1;
                transform: scale(1.2) rotate(180deg);
            }
        }

        .brand-sub {
            font-size: 0.7rem;
            color: rgba(180, 200, 230, 0.3);
            letter-spacing: 0.08em;
            text-transform: uppercase;
        }

        .badge-github {
            background: rgba(255, 255, 255, 0.05);
            padding: 0.4rem 1rem;
            border-radius: 60px;
            font-size: 0.75rem;
            color: #b0caf0;
            border: 1px solid rgba(255, 255, 255, 0.05);
            display: flex;
            align-items: center;
            gap: 0.5rem;
            cursor: pointer;
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
            flex-shrink: 0;
        }

        .badge-github::before {
            content: '';
            position: absolute;
            inset: 0;
            background: linear-gradient(135deg, rgba(138, 180, 255, 0.1), transparent);
            opacity: 0;
            transition: opacity 0.5s ease;
        }

        .badge-github:hover::before {
            opacity: 1;
        }

        .badge-github:hover {
            background: rgba(255, 255, 255, 0.08);
            transform: scale(1.02) translateY(-1px);
            box-shadow: 0 4px 20px rgba(138, 180, 255, 0.15);
        }

        .badge-github i {
            color: #8ab4ff;
            position: relative;
            z-index: 1;
        }

        .badge-github span {
            position: relative;
            z-index: 1;
        }

        .tagline {
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 0.8rem;
            flex-wrap: wrap;
            font-size: clamp(0.85rem, 2vw, 1.1rem);
            font-weight: 300;
            color: rgba(200, 218, 255, 0.6);
            margin-bottom: 2rem;
            padding: 0.5rem 1rem;
            border-left: 3px solid rgba(120, 180, 255, 0.25);
            border-right: 3px solid rgba(120, 180, 255, 0.25);
            animation: taglinePulse 3s ease-in-out infinite;
            text-align: center;
            width: 100%;
        }

        @keyframes taglinePulse {
            0%,
            100% {
                border-color: rgba(120, 180, 255, 0.25);
            }
            50% {
                border-color: rgba(120, 180, 255, 0.6);
            }
        }

        .repo-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 1.2rem;
            margin: 1.8rem 0 2.2rem;
            min-height: 80px;
            width: 100%;
        }

        .repo-card {
            background: rgba(12, 24, 44, 0.20);
            backdrop-filter: blur(2px);
            -webkit-backdrop-filter: blur(2px);
            border-radius: 1.8rem;
            padding: 1.4rem 1.2rem 1.2rem;
            border: 1px solid rgba(255, 255, 255, 0.04);
            box-shadow: 0 6px 16px rgba(0, 0, 0, 0.25);
            transition: all 0.3s ease;
            color: #e0ecff;
            cursor: pointer;
            position: relative;
            overflow: hidden;
            animation: fadeUp 0.35s ease forwards;
            opacity: 0;
            transform: translateY(8px);
            display: flex;
            flex-direction: column;
        }

        .repo-card::before {
            content: '';
            position: absolute;
            inset: 0;
            background: linear-gradient(135deg, rgba(138, 180, 255, 0.05), transparent);
            opacity: 0;
            transition: opacity 0.5s ease;
        }

        .repo-card:hover::before {
            opacity: 1;
        }

        .repo-card:nth-child(1) { animation-delay: 0.02s; }
        .repo-card:nth-child(2) { animation-delay: 0.04s; }
        .repo-card:nth-child(3) { animation-delay: 0.06s; }
        .repo-card:nth-child(4) { animation-delay: 0.08s; }
        .repo-card:nth-child(5) { animation-delay: 0.10s; }
        .repo-card:nth-child(6) { animation-delay: 0.12s; }

        @keyframes fadeUp {
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .repo-card:hover {
            transform: translateY(-4px) scale(1.02);
            background: rgba(25, 45, 75, 0.35);
            border-color: rgba(160, 200, 255, 0.15);
            box-shadow: 0 16px 32px rgba(0, 10, 40, 0.4);
        }

        .repo-card .repo-icon {
            font-size: 1.6rem;
            margin-bottom: 0.3rem;
            display: inline-block;
            color: #8ab4ff;
            transition: transform 0.3s ease;
            width: 2rem;
            text-align: center;
        }

        .repo-card:hover .repo-icon {
            transform: scale(1.2) rotate(-5deg);
        }

        .repo-card h3 {
            font-size: 1.05rem;
            font-weight: 500;
            margin-bottom: 0.15rem;
            background: linear-gradient(to right, #d6e8ff, #aac4ff);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
        }

        .repo-card .repo-desc {
            font-size: 0.75rem;
            opacity: 0.55;
            line-height: 1.3;
            margin: 0.15rem 0 0.4rem;
            min-height: 2.2rem;
            display: -webkit-box;
            -webkit-line-clamp: 2;
            -webkit-box-orient: vertical;
            overflow: hidden;
            flex: 1;
        }

        .repo-stats {
            display: flex;
            gap: 0.8rem;
            font-size: 0.65rem;
            color: rgba(180, 200, 230, 0.4);
            margin-top: auto;
            flex-wrap: wrap;
            align-items: center;
        }

        .repo-stats span {
            display: flex;
            align-items: center;
            gap: 0.2rem;
        }

        .repo-stats i {
            color: #7aafff;
            font-size: 0.55rem;
        }

        .repo-stats .lang-dot {
            display: inline-block;
            width: 8px;
            height: 8px;
            border-radius: 50%;
            flex-shrink: 0;
        }

        .btn-wrapper {
            display: flex;
            justify-content: center;
            gap: 0.8rem;
            flex-wrap: wrap;
            width: 100%;
        }

        .btn-primary {
            display: inline-flex;
            align-items: center;
            gap: 0.6rem;
            padding: 0.7rem 2rem;
            font-size: 0.95rem;
            font-weight: 600;
            background: linear-gradient(145deg, #1f3f6a, #132a4a);
            color: #f0f6ff;
            border: none;
            border-radius: 60px;
            cursor: pointer;
            box-shadow: 0 6px 20px rgba(0, 30, 80, 0.35);
            transition: all 0.3s ease;
            border: 1px solid rgba(255, 255, 255, 0.05);
            text-decoration: none;
            position: relative;
            overflow: hidden;
        }

        .btn-primary::before {
            content: '';
            position: absolute;
            inset: 0;
            background: linear-gradient(135deg, rgba(138, 180, 255, 0.15), transparent);
            opacity: 0;
            transition: opacity 0.5s ease;
        }

        .btn-primary:hover::before {
            opacity: 1;
        }

        .btn-primary:hover {
            transform: scale(1.03);
            background: linear-gradient(145deg, #2c5180, #17305a);
            box-shadow: 0 0 30px rgba(60, 140, 255, 0.3);
        }

        .btn-primary i,
        .btn-primary span {
            position: relative;
            z-index: 1;
        }

        .footer-links {
            margin-top: 2.2rem;
            display: flex;
            flex-wrap: wrap;
            align-items: center;
            justify-content: space-between;
            gap: 0.8rem;
            border-top: 1px solid rgba(255, 255, 255, 0.03);
            padding-top: 1.5rem;
            width: 100%;
        }

        .social-icons {
            display: flex;
            gap: 0.8rem;
        }

        .social-icons a {
            color: rgba(180, 205, 240, 0.3);
            font-size: 1.2rem;
            transition: all 0.3s ease;
            display: inline-block;
        }

        .social-icons a:hover {
            color: #8ab4ff;
            transform: translateY(-3px) scale(1.1);
            filter: drop-shadow(0 0 20px rgba(138, 180, 255, 0.3));
        }

        .footer-copy {
            font-size: 0.7rem;
            color: rgba(180, 200, 230, 0.15);
        }

        .live-indicator {
            display: flex;
            align-items: center;
            gap: 0.4rem;
            color: rgba(180, 210, 255, 0.25);
            font-size: 0.7rem;
        }

        .pulse-circle {
            width: 6px;
            height: 6px;
            border-radius: 50%;
            background: #5bb8ff;
            box-shadow: 0 0 12px #3f8fff;
            animation: pulse 2s infinite;
        }

        @keyframes pulse {
            0% {
                opacity: 0.3;
                transform: scale(0.8);
            }
            50% {
                opacity: 1;
                transform: scale(1.3);
            }
            100% {
                opacity: 0.3;
                transform: scale(0.8);
            }
        }

        .loader-small {
            display: inline-flex;
            align-items: center;
            gap: 0.4rem;
            font-size: 0.75rem;
            color: rgba(180, 210, 255, 0.35);
        }

        .loader-small .loader-dots {
            display: inline-flex;
            gap: 0.2rem;
        }

        .loader-small .loader-dots span {
            width: 6px;
            height: 6px;
            border-radius: 50%;
            background: rgba(180, 210, 255, 0.3);
            animation: dotPulse 1.4s ease-in-out infinite;
        }

        .loader-small .loader-dots span:nth-child(2) {
            animation-delay: 0.2s;
        }
        .loader-small .loader-dots span:nth-child(3) {
            animation-delay: 0.4s;
        }

        @keyframes dotPulse {
            0%,
            80%,
            100% {
                transform: scale(0.6);
                opacity: 0.3;
            }
            40% {
                transform: scale(1);
                opacity: 1;
            }
        }

        #particles-canvas {
            position: fixed;
            top: 0;
            left: 0;
            width: 100vw;
            height: 100vh;
            z-index: 0;
            pointer-events: none;
        }

        /* ----- МОДАЛЬНОЕ ОКНО ----- */
        .modal-overlay {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100vw;
            height: 100vh;
            background: rgba(0, 0, 0, 0.75);
            backdrop-filter: blur(10px);
            z-index: 1000;
            justify-content: center;
            align-items: center;
            padding: 1.5rem;
        }

        .modal-overlay.active {
            display: flex;
        }

        .modal-content {
            background: rgba(18, 30, 50, 0.96);
            backdrop-filter: blur(16px);
            border-radius: 2rem;
            max-width: 850px;
            width: 100%;
            max-height: 85vh;
            padding: 2rem;
            border: 1px solid rgba(255, 255, 255, 0.06);
            box-shadow: 0 40px 80px rgba(0, 0, 0, 0.7);
            overflow-y: auto;
            animation: modalIn 0.3s ease;
            position: relative;
        }

        @keyframes modalIn {
            0% {
                opacity: 0;
                transform: scale(0.96) translateY(8px);
            }
            100% {
                opacity: 1;
                transform: scale(1) translateY(0);
            }
        }

        .modal-close {
            position: sticky;
            top: 0;
            float: right;
            background: rgba(255, 255, 255, 0.06);
            border: none;
            color: #b0caf0;
            font-size: 1.2rem;
            width: 2.2rem;
            height: 2.2rem;
            border-radius: 50%;
            cursor: pointer;
            transition: all 0.3s ease;
            z-index: 10;
            display: flex;
            align-items: center;
            justify-content: center;
            line-height: 1;
            font-weight: 300;
        }

        .modal-close:hover {
            background: rgba(255, 80, 80, 0.2);
            color: #ff8a8a;
            transform: rotate(90deg);
        }

        .modal-title {
            font-size: 1.6rem;
            font-weight: 600;
            margin-bottom: 0.2rem;
            background: linear-gradient(to right, #d6e8ff, #aac4ff);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
        }

        .modal-desc {
            color: rgba(200, 218, 255, 0.6);
            font-size: 0.95rem;
            margin-bottom: 1rem;
            line-height: 1.5;
        }

        .modal-stats {
            display: flex;
            gap: 1.2rem;
            flex-wrap: wrap;
            margin-bottom: 1.2rem;
        }

        .modal-stat {
            color: rgba(200, 218, 255, 0.5);
            font-size: 0.8rem;
        }

        .modal-stat i {
            color: #8ab4ff;
            margin-right: 0.3rem;
        }

        .modal-section {
            margin-bottom: 1rem;
        }

        .modal-section h4 {
            color: rgba(200, 218, 255, 0.7);
            font-size: 0.9rem;
            font-weight: 500;
            margin-bottom: 0.5rem;
            display: flex;
            align-items: center;
            gap: 0.5rem;
        }

        .modal-section h4 i {
            color: #8ab4ff;
        }

        .slider-container {
            position: relative;
            overflow: hidden;
            border-radius: 1rem;
            background: rgba(0, 0, 0, 0.3);
            margin-top: 0.3rem;
        }

        .slider-track {
            display: flex;
            transition: transform 0.4s cubic-bezier(0.25, 0.46, 0.45, 0.94);
            will-change: transform;
        }

        .slider-slide {
            min-width: 100%;
            flex-shrink: 0;
            padding: 0.5rem;
        }

        .slider-slide img {
            width: 100%;
            height: 250px;
            object-fit: contain;
            border-radius: 0.6rem;
            background: rgba(0, 0, 0, 0.2);
            display: block;
        }

        .slider-slide .slide-name {
            text-align: center;
            color: rgba(200, 218, 255, 0.3);
            font-size: 0.65rem;
            margin-top: 0.3rem;
        }

        .slider-btn {
            position: absolute;
            top: 50%;
            transform: translateY(-50%);
            background: rgba(0, 0, 0, 0.5);
            border: none;
            color: #fff;
            width: 2.2rem;
            height: 2.2rem;
            border-radius: 50%;
            cursor: pointer;
            transition: all 0.3s ease;
            z-index: 5;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 0.9rem;
        }

        .slider-btn:hover {
            background: rgba(70, 140, 255, 0.4);
            transform: translateY(-50%) scale(1.1);
        }

        .slider-btn.prev {
            left: 0.5rem;
        }
        .slider-btn.next {
            right: 0.5rem;
        }

        .slider-dots {
            display: flex;
            justify-content: center;
            gap: 0.4rem;
            padding: 0.5rem 0;
        }

        .slider-dots button {
            width: 8px;
            height: 8px;
            border-radius: 50%;
            border: none;
            background: rgba(255, 255, 255, 0.15);
            cursor: pointer;
            transition: all 0.3s ease;
            padding: 0;
        }

        .slider-dots button.active {
            background: #8ab4ff;
            transform: scale(1.2);
        }

        .slider-dots button:hover {
            background: rgba(138, 180, 255, 0.4);
        }

        .modal-code {
            background: rgba(0, 0, 0, 0.4);
            border-radius: 0.8rem;
            padding: 0.8rem;
            overflow-x: auto;
            font-family: 'Courier New', monospace;
            font-size: 0.75rem;
            color: #b0d0f0;
            white-space: pre-wrap;
            word-break: break-all;
            border: 1px solid rgba(255, 255, 255, 0.03);
            max-height: 200px;
            overflow-y: auto;
            position: relative;
        }

        .modal-code .code-actions {
            position: sticky;
            top: 0;
            float: right;
            display: flex;
            gap: 0.4rem;
            margin-bottom: 0.3rem;
        }

        .modal-code .code-actions button {
            background: rgba(255, 255, 255, 0.06);
            border: none;
            color: #b0caf0;
            padding: 0.2rem 0.7rem;
            border-radius: 0.4rem;
            cursor: pointer;
            font-size: 0.65rem;
            transition: all 0.2s ease;
        }

        .modal-code .code-actions button:hover {
            background: rgba(255, 255, 255, 0.12);
        }

        .modal-files {
            display: flex;
            flex-direction: column;
            gap: 0.3rem;
        }

        .modal-file {
            background: rgba(0, 0, 0, 0.15);
            padding: 0.35rem 0.7rem;
            border-radius: 0.5rem;
            display: flex;
            justify-content: space-between;
            align-items: center;
            border: 1px solid rgba(255, 255, 255, 0.02);
            transition: all 0.2s ease;
        }

        .modal-file:hover {
            background: rgba(0, 0, 0, 0.3);
        }

        .modal-file span {
            color: rgba(200, 218, 255, 0.55);
            font-size: 0.75rem;
            display: flex;
            align-items: center;
            gap: 0.4rem;
        }

        .modal-file .file-actions {
            display: flex;
            gap: 0.2rem;
        }

        .modal-file .file-actions button {
            background: rgba(255, 255, 255, 0.03);
            border: none;
            color: #b0caf0;
            padding: 0.1rem 0.4rem;
            border-radius: 0.3rem;
            font-size: 0.6rem;
            cursor: pointer;
            transition: all 0.2s ease;
        }

        .modal-file .file-actions button:hover {
            background: rgba(70, 140, 255, 0.15);
        }

        .modal-release {
            background: rgba(70, 180, 100, 0.04);
            border: 1px solid rgba(70, 180, 100, 0.06);
            border-radius: 0.7rem;
            padding: 0.6rem 0.8rem;
            margin-bottom: 0.4rem;
            display: flex;
            align-items: center;
            justify-content: space-between;
            flex-wrap: wrap;
            gap: 0.5rem;
        }

        .modal-release .release-info {
            flex: 1;
        }

        .modal-release .release-tag {
            color: #7aff9e;
            font-weight: 500;
            font-size: 0.85rem;
        }

        .modal-release .release-date {
            color: rgba(200, 218, 255, 0.3);
            font-size: 0.65rem;
            margin-left: 0.6rem;
        }

        .modal-release .release-name {
            color: rgba(200, 218, 255, 0.5);
            font-size: 0.8rem;
            margin-top: 0.1rem;
        }

        .modal-release .release-actions {
            display: flex;
            gap: 0.3rem;
            flex-shrink: 0;
            flex-wrap: wrap;
        }

        .modal-release .release-actions button {
            background: rgba(255, 255, 255, 0.04);
            border: none;
            color: #b0caf0;
            padding: 0.2rem 0.6rem;
            border-radius: 0.4rem;
            font-size: 0.6rem;
            cursor: pointer;
            transition: all 0.2s ease;
        }

        .modal-release .release-actions button:hover {
            background: rgba(70, 140, 255, 0.15);
        }

        .toast {
            position: fixed;
            bottom: 2rem;
            right: 2rem;
            background: rgba(18, 30, 50, 0.92);
            backdrop-filter: blur(8px);
            padding: 0.6rem 1rem;
            border-radius: 0.8rem;
            color: #fff;
            border: 1px solid rgba(255, 255, 255, 0.05);
            box-shadow: 0 12px 24px rgba(0, 0, 0, 0.4);
            z-index: 2000;
            animation: toastIn 0.3s ease;
            display: none;
            font-size: 0.85rem;
        }

        .toast.show {
            display: flex;
            align-items: center;
            gap: 0.5rem;
        }

        @keyframes toastIn {
            0% {
                opacity: 0;
                transform: translateY(10px) scale(0.95);
            }
            100% {
                opacity: 1;
                transform: translateY(0) scale(1);
            }
        }

        .toast i {
            color: #5bb8ff;
        }

        .modal-content::-webkit-scrollbar {
            width: 4px;
        }
        .modal-content::-webkit-scrollbar-track {
            background: rgba(255, 255, 255, 0.01);
        }
        .modal-content::-webkit-scrollbar-thumb {
            background: rgba(255, 255, 255, 0.06);
            border-radius: 2px;
        }

        .loading-spinner {
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            padding: 2rem 0;
            gap: 1rem;
        }

        .loading-spinner .spinner-ring {
            width: 40px;
            height: 40px;
            border-radius: 50%;
            border: 3px solid rgba(138, 180, 255, 0.1);
            border-top: 3px solid #8ab4ff;
            animation: spinnerRotate 0.8s linear infinite;
        }

        @keyframes spinnerRotate {
            0% {
                transform: rotate(0deg);
            }
            100% {
                transform: rotate(360deg);
            }
        }

        .loading-spinner span {
            color: rgba(200, 218, 255, 0.3);
            font-size: 0.85rem;
        }

        /* ----- АДАПТИВНОСТЬ ----- */
        @media (max-width: 768px) {
            .wrapper {
                padding: 0.8rem;
                max-height: 96vh;
                position: relative;
                top: auto;
                left: auto;
                transform: none;
                margin: 0 auto;
            }
            .glass-card {
                padding: 1rem 0.8rem;
                border-radius: 1.8rem;
            }
            .header {
                flex-direction: column;
                align-items: flex-start;
                gap: 0.6rem;
            }
            .header-left {
                width: 100%;
            }
            .badge-github {
                width: 100%;
                justify-content: center;
                font-size: 0.7rem;
            }
            .repo-grid {
                gap: 0.6rem;
                grid-template-columns: 1fr;
            }
            .modal-content {
                padding: 1rem;
            }
            .modal-stats {
                gap: 0.6rem;
            }
            .slider-slide img {
                height: 180px;
            }
            .modal-release {
                flex-direction: column;
                align-items: flex-start;
            }
            .modal-release .release-actions {
                width: 100%;
                justify-content: flex-start;
            }
            .brand::after {
                display: none;
            }
            .tagline {
                border-left: none;
                border-right: none;
                padding: 0.5rem 0;
            }
            .footer-links {
                flex-direction: column;
                align-items: center;
                text-align: center;
            }
            .repo-stats {
                gap: 0.5rem;
                font-size: 0.6rem;
            }
        }

        @media (max-height: 700px) {
            .glass-card {
                padding: 1.2rem;
            }
            .header {
                margin-bottom: 0.8rem;
            }
            .tagline {
                margin-bottom: 1rem;
                padding: 0.3rem 0.8rem;
                font-size: 0.85rem;
            }
            .repo-grid {
                margin: 1rem 0 1.2rem;
                gap: 0.8rem;
            }
            .repo-card {
                padding: 1rem 0.8rem 0.8rem;
            }
            .footer-links {
                margin-top: 1.2rem;
                padding-top: 1rem;
            }
            .brand {
                font-size: 1.4rem;
            }
            .avatar {
                width: 42px;
                height: 42px;
            }
            .avatar .fallback-icon {
                font-size: 1.6rem;
            }
        }

        @media (min-width: 769px) {
            .wrapper {
                position: absolute;
                top: 50%;
                left: 50%;
                transform: translate(-50%, -50%);
            }
        }
    </style>
</head>
<body>

    <!-- ЗВЁЗДНЫЙ ФОН -->
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
        <div class="shooting-star">
            <div class="star-dot"></div>
            <div class="star-tail"></div>
        </div>
        <div class="shooting-star">
            <div class="star-dot"></div>
            <div class="star-tail"></div>
        </div>
        <div class="shooting-star">
            <div class="star-dot"></div>
            <div class="star-tail"></div>
        </div>
        <div class="shooting-star">
            <div class="star-dot"></div>
            <div class="star-tail"></div>
        </div>
        <div class="shooting-star">
            <div class="star-dot"></div>
            <div class="star-tail"></div>
        </div>
        <div class="shooting-star">
            <div class="star-dot"></div>
            <div class="star-tail"></div>
        </div>
        <div class="shooting-star">
            <div class="star-dot"></div>
            <div class="star-tail"></div>
        </div>
        <div class="shooting-star">
            <div class="star-dot"></div>
            <div class="star-tail"></div>
        </div>
    </div>

    <canvas id="particles-canvas"></canvas>

    <!-- ОСНОВНОЙ КОНТЕЙНЕР -->
    <div class="wrapper">
        <div class="glass-card">
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

            <div class="tagline">
                <i class="fas fa-code" style="color:rgba(120,180,255,0.3);"></i>
                Инструменты для разработчиков · Open Source
                <span class="loader-small" id="loaderIndicator">
                    <span class="loader-dots">
                        <span></span>
                        <span></span>
                        <span></span>
                    </span>
                    загрузка
                </span>
            </div>

            <div class="repo-grid" id="repoGrid">
                <div style="grid-column:1/-1;text-align:center;color:rgba(200,218,255,0.2);padding:1.5rem 0;font-size:0.9rem;">
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

    <div class="modal-overlay" id="modalOverlay">
        <div class="modal-content" id="modalContent">
            <button class="modal-close" id="modalClose">✕</button>
            <div id="modalBody"></div>
        </div>
    </div>

    <div class="toast" id="toast">
        <i class="fas fa-check-circle"></i>
        <span id="toastMessage">Скопировано!</span>
    </div>

    <script>
        (function() {
            'use strict';

            const canvas = document.getElementById('particles-canvas');
            const ctx = canvas.getContext('2d');
            let w, h;
            let particles = [];
            const COUNT = 30;

            function resize() {
                w = window.innerWidth;
                h = window.innerHeight;
                canvas.width = w;
                canvas.height = h;
            }
            window.addEventListener('resize', resize);
            resize();

            class Particle {
                constructor() {
                    this.reset();
                }
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
                    ctx.fillStyle = `rgba(180,215,255,${this.o})`;
                    ctx.shadowColor = 'rgba(100,180,255,0.05)';
                    ctx.shadowBlur = 3;
                    ctx.fill();
                }
            }

            for (let i = 0; i < COUNT; i++) particles.push(new Particle());

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
                            ctx.strokeStyle = `rgba(140,190,255,${o})`;
                            ctx.lineWidth = 0.3;
                            ctx.stroke();
                        }
                    }
                }
            }

            function animate() {
                ctx.clearRect(0, 0, w, h);
                particles.forEach(p => { p.update();
                    p.draw(); });
                drawLines();
                requestAnimationFrame(animate);
            }
            animate();

            function showToast(msg, icon = 'fa-check-circle') {
                const t = document.getElementById('toast');
                document.getElementById('toastMessage').textContent = msg;
                t.querySelector('i').className = `fas ${icon}`;
                t.classList.add('show');
                clearTimeout(t._t);
                t._t = setTimeout(() => t.classList.remove('show'), 2000);
            }

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

            async function loadAvatar() {
                const container = document.getElementById('avatarContainer');
                try {
                    const res = await fetch(`https://api.github.com/users/repowerstudio`);
                    if (res.ok) {
                        const data = await res.json();
                        if (data.avatar_url) {
                            container.innerHTML = `<img src="${data.avatar_url}" alt="RepowerStudio" />`;
                        }
                    }
                } catch (e) {}
            }
            loadAvatar();

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

            // Цвета для языков программирования
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
                'svelte': '#ff3e00',
                'jupyter': '#DA5B0B',
                'shell': '#89e051',
                'dockerfile': '#384d54',
                'markdown': '#083fa1',
                'json': '#292929',
                'yaml': '#cb171e',
                'xml': '#0060ac'
            };

            function getLangColor(lang) {
                if (!lang) return '#7aafff';
                const key = lang.toLowerCase();
                return langColors[key] || '#7aafff';
            }

            // Определение иконки по языку (только для популярных)
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
                    'svelte': 'fab fa-svelte',
                    'dockerfile': 'fab fa-docker',
                    'docker': 'fab fa-docker'
                };

                if (iconMap[l]) return iconMap[l];

                for (const [key, icon] of Object.entries(iconMap)) {
                    if (l.includes(key) || key.includes(l)) {
                        return icon;
                    }
                }

                return null; // Возвращаем null для неизвестных языков
            }

            function createCard(repo) {
                const card = document.createElement('div');
                card.className = 'repo-card';

                const iconClass = getLanguageIcon(repo.language);

                // Строим иконку только если есть подходящий язык
                let iconHtml = '';
                if (iconClass) {
                    iconHtml = `<span class="repo-icon"><i class="${iconClass}"></i></span>`;
                }

                // Строим строку с языком только если он есть
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

            async function fetchRepos() {
                try {
                    const res = await fetch(`https://api.github.com/users/${USERNAME}/repos?sort=updated&per_page=15`);
                    if (!res.ok) throw new Error(`Ошибка ${res.status}`);
                    const data = await res.json();
                    if (!data.length) throw new Error('Репозитории не найдены');

                    grid.innerHTML = '';
                    data.sort((a, b) => b.stargazers_count - a.stargazers_count);
                    data.forEach(r => grid.appendChild(createCard(r)));

                    countStatus.textContent = `репозитории: ${data.length}`;
                    loader.innerHTML = `
                        <span style="color:#5bb8ff;">●</span>
                        ${data.length} загружено
                    `;
                } catch (err) {
                    grid.innerHTML = `
                        <div style="grid-column:1/-1;text-align:center;color:rgba(200,180,200,0.3);padding:1.5rem 0;font-size:0.9rem;">
                            <i class="fas fa-exclamation-triangle" style="font-size:1.8rem;display:block;margin-bottom:0.4rem;"></i>
                            ${esc(err.message)}
                        </div>
                    `;
                    loader.innerHTML = `<span style="color:#ff8a8a;">●</span> ошибка`;
                    countStatus.textContent = 'репозитории: —';
                }
            }

            let sliderInstances = [];

            function initSlider(container, images) {
                if (!container || !images.length) return;

                const track = container.querySelector('.slider-track');
                const dots = container.querySelector('.slider-dots');
                let current = 0;
                const total = images.length;

                function updateSlider(index) {
                    current = index;
                    track.style.transform = `translateX(-${current * 100}%)`;
                    dots.querySelectorAll('button').forEach((btn, i) => {
                        btn.classList.toggle('active', i === current);
                    });
                }

                images.forEach((img, i) => {
                    const slide = document.createElement('div');
                    slide.className = 'slider-slide';
                    slide.innerHTML = `
                        <img src="${img.download_url}" alt="${esc(img.name)}" loading="lazy" />
                        <div class="slide-name">${esc(img.name)}</div>
                        <div style="display:flex;justify-content:center;gap:0.3rem;margin-top:0.3rem;">
                            <button class="copy-img-btn" data-url="${img.download_url}" style="background:rgba(255,255,255,0.06);border:none;color:#b0caf0;padding:0.15rem 0.5rem;border-radius:0.3rem;font-size:0.6rem;cursor:pointer;">📋 Копировать</button>
                            <button class="download-img-btn" data-url="${img.download_url}" data-name="${esc(img.name)}" style="background:rgba(255,255,255,0.06);border:none;color:#b0caf0;padding:0.15rem 0.5rem;border-radius:0.3rem;font-size:0.6rem;cursor:pointer;">⬇ Скачать</button>
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

                const prevBtn = container.querySelector('.slider-btn.prev');
                const nextBtn = container.querySelector('.slider-btn.next');

                prevBtn.addEventListener('click', () => {
                    updateSlider(current > 0 ? current - 1 : total - 1);
                });

                nextBtn.addEventListener('click', () => {
                    updateSlider(current < total - 1 ? current + 1 : 0);
                });

                container._keyHandler = (e) => {
                    if (e.key === 'ArrowLeft') prevBtn.click();
                    if (e.key === 'ArrowRight') nextBtn.click();
                };
                document.addEventListener('keydown', container._keyHandler);

                sliderInstances.push(container);
            }

            async function openModal(repo) {
                modalOverlay.classList.add('active');
                modalBody.innerHTML = `
                    <div class="loading-spinner">
                        <div class="spinner-ring"></div>
                        <span>Загрузка данных...</span>
                    </div>
                `;

                try {
                    const [contentsRes, releasesRes] = await Promise.all([
                        fetch(`https://api.github.com/repos/${USERNAME}/${repo.name}/contents`),
                        fetch(`https://api.github.com/repos/${USERNAME}/${repo.name}/releases?per_page=10`)
                    ]);

                    let files = [];
                    let releases = [];
                    if (contentsRes.ok) files = await contentsRes.json();
                    if (releasesRes.ok) releases = await releasesRes.json();

                    const images = [];
                    const otherFiles = [];
                    if (Array.isArray(files)) {
                        files.forEach(f => {
                            const ext = f.name.split('.').pop().toLowerCase();
                            if (['png', 'jpg', 'jpeg', 'gif', 'svg', 'webp', 'bmp', 'ico'].includes(ext)) {
                                images.push(f);
                            } else {
                                otherFiles.push(f);
                            }
                        });
                    }

                    const iconClass = getLanguageIcon(repo.language);
                    const langColor = getLangColor(repo.language);

                    let html = `
                        <h2 class="modal-title"><i class="fas fa-folder-open" style="color:#8ab4ff;margin-right:0.5rem;"></i>${esc(repo.name)}</h2>
                        <p class="modal-desc">${esc(repo.description || 'Нет описания')}</p>
                        <div class="modal-stats">
                            <span class="modal-stat"><i class="fas fa-star"></i> ${repo.stargazers_count || 0}</span>
                            <span class="modal-stat"><i class="fas fa-code-branch"></i> ${repo.forks_count || 0}</span>
                            ${repo.language ? `<span class="modal-stat"><i class="fas fa-circle" style="color:${langColor};"></i> ${esc(repo.language)}</span>` : ''}
                            <span class="modal-stat"><i class="fas fa-calendar-alt"></i> ${new Date(repo.updated_at).toLocaleDateString()}</span>
                        </div>
                    `;

                    if (images.length > 0) {
                        html += `
                            <div class="modal-section">
                                <h4><i class="fas fa-images"></i> Изображения (${images.length})</h4>
                                <div class="slider-container">
                                    <button class="slider-btn prev"><i class="fas fa-chevron-left"></i></button>
                                    <div class="slider-track"></div>
                                    <button class="slider-btn next"><i class="fas fa-chevron-right"></i></button>
                                    <div class="slider-dots"></div>
                                </div>
                            </div>
                        `;
                    }

                    if (releases.length > 0) {
                        html += `
                            <div class="modal-section">
                                <h4><i class="fas fa-tag"></i> Релизы (${releases.length})</h4>
                        `;
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
                                        ${assets.length > 3 ? `<span style="font-size:0.6rem;color:rgba(200,218,255,0.2);">+${assets.length-3}</span>` : ''}
                                    </div>
                                </div>
                            `;
                        });
                        html += `</div>`;
                    }

                    const readme = files.find(f => f.name.toLowerCase() === 'readme.md');
                    if (readme) {
                        try {
                            const rRes = await fetch(readme.download_url);
                            const text = await rRes.text();
                            html += `
                                <div class="modal-section">
                                    <h4><i class="fas fa-file-alt"></i> README.md</h4>
                                    <div class="modal-code">
                                        <div class="code-actions">
                                            <button class="copy-btn" data-code="${encodeURIComponent(text)}"><i class="fas fa-copy"></i> Копировать</button>
                                            <button class="download-btn" data-url="${readme.download_url}" data-name="README.md"><i class="fas fa-download"></i> Скачать</button>
                                        </div>
                                        <pre>${esc(text.substring(0, 1500))}${text.length > 1500 ? '\n... (обрезано)' : ''}</pre>
                                    </div>
                                </div>
                            `;
                        } catch (e) {}
                    }

                    if (otherFiles.length > 0) {
                        html += `
                            <div class="modal-section">
                                <h4><i class="fas fa-file-code"></i> Файлы (${otherFiles.length})</h4>
                                <div class="modal-files">
                        `;
                        otherFiles.slice(0, 15).forEach(f => {
                            html += `
                                <div class="modal-file">
                                    <span><i class="fas fa-file" style="color:#8ab4ff;"></i> ${esc(f.name)}</span>
                                    <div class="file-actions">
                                        <button class="copy-file-btn" data-url="${f.download_url}" title="Копировать"><i class="fas fa-copy"></i></button>
                                        <button class="download-file-btn" data-url="${f.download_url}" data-name="${esc(f.name)}" title="Скачать"><i class="fas fa-download"></i></button>
                                        <button class="view-file-btn" data-url="${f.download_url}" data-name="${esc(f.name)}" title="Просмотр"><i class="fas fa-eye"></i></button>
                                    </div>
                                </div>
                            `;
                        });
                        html += `</div></div>`;
                    }

                    if (!images.length && !otherFiles.length && !readme && !releases.length) {
                        html += `
                            <div style="text-align:center;color:rgba(200,218,255,0.2);padding:1rem 0;font-size:0.85rem;">
                                <i class="fas fa-inbox" style="font-size:1.5rem;display:block;margin-bottom:0.2rem;"></i>
                                Нет файлов для отображения
                            </div>
                        `;
                    }

                    modalBody.innerHTML = html;

                    const sliderContainer = modalBody.querySelector('.slider-container');
                    if (sliderContainer && images.length > 0) {
                        initSlider(sliderContainer, images);
                    }

                    modalBody.querySelectorAll('.copy-btn').forEach(b => {
                        b.addEventListener('click', (e) => {
                            e.stopPropagation();
                            copyText(decodeURIComponent(b.dataset.code));
                        });
                    });

                    modalBody.querySelectorAll('.download-btn').forEach(b => {
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

                    modalBody.querySelectorAll('.copy-img-btn').forEach(b => {
                        b.addEventListener('click', (e) => {
                            e.stopPropagation();
                            copyText(b.dataset.url);
                        });
                    });

                    modalBody.querySelectorAll('.download-img-btn').forEach(b => {
                        b.addEventListener('click', (e) => {
                            e.stopPropagation();
                            downloadFile(b.dataset.url, b.dataset.name);
                        });
                    });

                    modalBody.querySelectorAll('.copy-file-btn').forEach(b => {
                        b.addEventListener('click', async (e) => {
                            e.stopPropagation();
                            try {
                                const res = await fetch(b.dataset.url);
                                const text = await res.text();
                                copyText(text);
                            } catch {
                                showToast('Ошибка загрузки', 'fa-exclamation-circle');
                            }
                        });
                    });

                    modalBody.querySelectorAll('.download-file-btn').forEach(b => {
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
                                    <div style="background:rgba(18,30,50,0.96);border-radius:1.2rem;padding:1.2rem;max-width:750px;width:100%;max-height:80vh;overflow-y:auto;position:relative;">
                                        <button style="position:sticky;top:0;float:right;background:rgba(255,255,255,0.04);border:none;color:#fff;font-size:1.3rem;width:2rem;height:2rem;border-radius:50%;cursor:pointer;">&times;</button>
                                        <h4 style="color:#b0caf0;margin-bottom:0.6rem;font-size:1rem;">${b.dataset.name}</h4>
                                        <pre style="background:rgba(0,0,0,0.25);border-radius:0.6rem;padding:0.6rem;color:#b0d0f0;font-family:monospace;font-size:0.75rem;white-space:pre-wrap;word-break:break-all;max-height:55vh;overflow-y:auto;">${esc(text)}</pre>
                                    </div>
                                `;
                                document.body.appendChild(vw);
                                vw.querySelector('button').addEventListener('click', () => document.body.removeChild(vw));
                                vw.addEventListener('click', (e) => { if (e.target === vw) document.body.removeChild(vw); });
                            } catch {
                                showToast('Ошибка загрузки', 'fa-exclamation-circle');
                            }
                        });
                    });

                } catch (err) {
                    modalBody.innerHTML = `
                        <div style="text-align:center;color:rgba(255,150,150,0.3);padding:1.5rem 0;">
                            <i class="fas fa-exclamation-triangle" style="font-size:1.8rem;display:block;margin-bottom:0.4rem;"></i>
                            Ошибка загрузки
                            <div style="font-size:0.8rem;margin-top:0.2rem;opacity:0.4;">${esc(err.message)}</div>
                        </div>
                    `;
                }
            }

            modalClose.addEventListener('click', () => {
                sliderInstances.forEach(s => {
                    if (s._keyHandler) document.removeEventListener('keydown', s._keyHandler);
                });
                sliderInstances = [];
                modalOverlay.classList.remove('active');
            });

            modalOverlay.addEventListener('click', (e) => {
                if (e.target === modalOverlay) {
                    sliderInstances.forEach(s => {
                        if (s._keyHandler) document.removeEventListener('keydown', s._keyHandler);
                    });
                    sliderInstances = [];
                    modalOverlay.classList.remove('active');
                }
            });

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

            fetchRepos();

            document.getElementById('exploreBtn').addEventListener('click', function(e) {
                const orig = this.innerHTML;
                this.innerHTML = '<i class="fas fa-spinner fa-pulse"></i> Загрузка...';
                setTimeout(() => {
                    this.innerHTML = orig;
                }, 500);
            });

            console.log('✨ RepowerStudio · слабый blur, иконки только для популярных языков');
        })();
    </script>
</body>
</html>
