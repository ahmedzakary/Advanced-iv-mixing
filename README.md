<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>المحاكي الاحترافي: تحضير أدوية العلاج الكيميائي</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Cairo:wght@300;400;500;600;700;800&display=swap" rel="stylesheet">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            font-family: 'Cairo', sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            overflow-x: hidden;
        }
        
        body::before {
            content: '';
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: url("image/svg+xml,%3Csvg width='60' height='60' viewBox='0 0 60 60' xmlns='http://www.w3.org/2000/svg'%3E%3Cg fill='none' fill-rule='evenodd'%3E%3Cg fill='%23ffffff' fill-opacity='0.05'%3E%3Cpath d='M36 34v-4h-2v4h-4v2h4v4h2v-4h4v-2h-4zm0-30V0h-2v4h-4v2h4v4h2V6h4V4h-4zM6 34v-4H4v4H0v2h4v4h2v-4h4v-2H6zM6 4V0H4v4H0v2h4v4h2V6h4V4H6z'/%3E%3C/g%3E%3C/g%3E%3C/svg%3E");
            pointer-events: none;
            z-index: 0;
        }
        
        .step-container {
            display: none;
            animation: stepFadeIn 0.6s cubic-bezier(0.4, 0, 0.2, 1);
        }
        
        .step-container.active {
            display: block;
        }
        
        @keyframes stepFadeIn {
            from { 
                opacity: 0; 
                transform: translateY(30px) scale(0.98);
            }
            to { 
                opacity: 1; 
                transform: translateY(0) scale(1);
            }
        }
        
        .check-item {
            position: relative;
            overflow: hidden;
        }
        
        .check-item::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255,255,255,0.3), transparent);
            transition: left 0.5s ease;
        }
        
        .check-item:hover::before {
            left: 100%;
        }
        
        .check-item.checked {
            background: linear-gradient(135deg, #d1fae5 0%, #a7f3d0 100%);
            border-color: #10b981;
            color: #065f46;
            box-shadow: 0 4px 15px rgba(16, 185, 129, 0.3);
        }
        
        .check-item.checked::after {
            content: '✓';
            position: absolute;
            left: 15px;
            font-weight: bold;
            font-size: 1.2em;
            animation: checkPop 0.3s cubic-bezier(0.4, 0, 0.2, 1);
        }
        
        @keyframes checkPop {
            0% { transform: scale(0); }
            50% { transform: scale(1.3); }
            100% { transform: scale(1); }
        }
        
        .progress-bar {
            transition: width 0.8s cubic-bezier(0.4, 0, 0.2, 1);
            background: linear-gradient(90deg, #3b82f6, #8b5cf6, #3b82f6);
            background-size: 200% 100%;
            animation: progressShine 2s linear infinite;
        }
        
        @keyframes progressShine {
            0% { background-position: 200% 0; }
            100% { background-position: -200% 0; }
        }
        
        .btn-primary {
            background: linear-gradient(135deg, #0ea5e9 0%, #0284c7 50%, #0369a1 100%);
            position: relative;
            overflow: hidden;
        }
        
        .btn-primary::before {
            content: '';
            position: absolute;
            top: 50%;
            left: 50%;
            width: 0;
            height: 0;
            background: rgba(255,255,255,0.2);
            border-radius: 50%;
            transform: translate(-50%, -50%);
            transition: width 0.6s ease, height 0.6s ease;
        }
        
        .btn-primary:hover::before {
            width: 300px;
            height: 300px;
        }
        
        .btn-primary:hover:not(:disabled) {
            transform: translateY(-2px);
            box-shadow: 0 10px 25px rgba(14, 165, 233, 0.4);
        }
        
        /* Enhanced Syringe Animation */
        .syringe-container {
            position: relative;
            width: 340px;
            height: 450px;
            margin: 0 auto;
            filter: drop-shadow(0 10px 30px rgba(0,0,0,0.2));
        }
        
        .syringe-barrel {
            position: absolute;
            left: 50%;
            transform: translateX(-50%);
            width: 70px;
            height: 220px;
            background: linear-gradient(90deg, #e0e7ff 0%, #ffffff 30%, #ffffff 70%, #e0e7ff 100%);
            border: 3px solid #6366f1;
            border-radius: 6px;
            top: 50px;
            box-shadow: 
                inset 0 0 30px rgba(99, 102, 241, 0.15),
                0 8px 25px rgba(99, 102, 241, 0.3),
                inset 2px 0 10px rgba(255,255,255,0.8);
        }
        
        .syringe-barrel::before {
            content: '';
            position: absolute;
            top: 5px;
            left: 5px;
            right: 5px;
            bottom: 5px;
            border: 1px solid rgba(99, 102, 241, 0.3);
            border-radius: 4px;
            pointer-events: none;
        }
        
        .syringe-plunger {
            position: absolute;
            left: 50%;
            transform: translateX(-50%);
            width: 45px;
            height: 170px;
            background: linear-gradient(90deg, #3b82f6 0%, #2563eb 50%, #1d4ed8 100%);
            border-radius: 4px;
            top: 85px;
            transition: top 0.5s cubic-bezier(0.34, 1.56, 0.64, 1);
            cursor: pointer;
            box-shadow: 
                0 4px 20px rgba(59, 130, 246, 0.5),
                inset 0 2px 10px rgba(255,255,255,0.2);
        }
        
        .syringe-plunger:hover {
            box-shadow: 
                0 6px 25px rgba(59, 130, 246, 0.7),
                inset 0 2px 10px rgba(255,255,255,0.3);
            transform: translateX(-50%) scale(1.02);
        }
        
        .syringe-plunger-head {
            position: absolute;
            bottom: -22px;
            left: 50%;
            transform: translateX(-50%);
            width: 95px;
            height: 22px;
            background: linear-gradient(180deg, #1d4ed8 0%, #1e40af 50%, #1e3a8a 100%);
            border-radius: 6px;
            box-shadow: 
                0 3px 15px rgba(29, 78, 216, 0.6),
                inset 0 2px 5px rgba(255,255,255,0.2);
        }
        
        .syringe-plunger-head::before {
            content: '';
            position: absolute;
            top: 3px;
            left: 10%;
            right: 10%;
            height: 4px;
            background: linear-gradient(90deg, transparent, rgba(255,255,255,0.4), transparent);
            border-radius: 2px;
        }
        
        .syringe-plunger-top {
            position: absolute;
            top: -18px;
            left: 50%;
            transform: translateX(-50%);
            width: 55px;
            height: 18px;
            background: linear-gradient(180deg, #3b82f6 0%, #2563eb 100%);
            border-radius: 4px 4px 0 0;
            box-shadow: 0 -2px 10px rgba(59, 130, 246, 0.4);
        }
        
        .syringe-needle {
            position: absolute;
            left: 50%;
            transform: translateX(-50%);
            width: 6px;
            height: 70px;
            background: linear-gradient(90deg, #4b5563 0%, #9ca3af 30%, #e5e7eb 50%, #9ca3af 70%, #4b5563 100%);
            bottom: -70px;
            box-shadow: 3px 0 8px rgba(0,0,0,0.3);
        }
        
        .syringe-needle::before {
            content: '';
            position: absolute;
            bottom: 0;
            left: 50%;
            transform: translateX(-50%);
            width: 0;
            height: 0;
            border-left: 3px solid transparent;
            border-right: 3px solid transparent;
            border-bottom: 8px solid #6b7280;
        }
        
        .syringe-needle-hub {
            position: absolute;
            left: 50%;
            transform: translateX(-50%);
            width: 26px;
            height: 28px;
            background: linear-gradient(180deg, #06b6d4 0%, #0891b2 50%, #0e7490 100%);
            bottom: -40px;
            border-radius: 3px;
            box-shadow: 0 2px 10px rgba(6, 182, 212, 0.5);
        }
        
        .syringe-needle-hub::before {
            content: '';
            position: absolute;
            top: 5px;
            left: 3px;
            right: 3px;
            height: 3px;
            background: linear-gradient(90deg, transparent, rgba(255,255,255,0.5), transparent);
            border-radius: 2px;
        }
        
        .vial {
            position: absolute;
            left: 50%;
            transform: translateX(-50%);
            width: 95px;
            height: 135px;
            bottom: 0;
        }
        
        .vial-body {
            width: 100%;
            height: 115px;
            background: linear-gradient(90deg, 
                rgba(255,255,255,0.15) 0%, 
                rgba(255,255,255,0.4) 20%,
                rgba(255,255,255,0.9) 50%, 
                rgba(255,255,255,0.4) 80%,
                rgba(255,255,255,0.15) 100%);
            border: 2px solid #9ca3af;
            border-radius: 12px 12px 6px 6px;
            position: relative;
            overflow: hidden;
            box-shadow: 
                inset 0 0 25px rgba(0,0,0,0.1),
                0 6px 20px rgba(0,0,0,0.15),
                inset 3px 0 15px rgba(255,255,255,0.5);
        }
        
        .vial-body::before {
            content: '';
            position: absolute;
            top: 10px;
            left: 8px;
            width: 15px;
            height: 80px;
            background: linear-gradient(90deg, rgba(255,255,255,0.6), transparent);
            border-radius: 10px;
            filter: blur(2px);
        }
        
        .vial-liquid {
            position: absolute;
            bottom: 0;
            width: 100%;
            height: 70%;
            transition: height 0.6s cubic-bezier(0.34, 1.56, 0.64, 1);
            box-shadow: inset 0 0 30px rgba(0,0,0,0.2);
        }
        
        .vial-liquid::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            height: 15px;
            background: linear-gradient(180deg, rgba(255,255,255,0.5) 0%, transparent 100%);
            animation: liquidWave 3s ease-in-out infinite;
        }
        
        @keyframes liquidWave {
            0%, 100% { transform: scaleX(1); }
            50% { transform: scaleX(1.08); }
        }
        
        .vial-liquid::after {
            content: '';
            position: absolute;
            bottom: 5px;
            left: 10%;
            right: 10%;
            height: 5px;
            background: linear-gradient(90deg, transparent, rgba(255,255,255,0.3), transparent);
            border-radius: 50%;
            filter: blur(1px);
        }
        
        .vial-cap {
            width: 100%;
            height: 28px;
            background: linear-gradient(180deg, #4b5563 0%, #374151 50%, #1f2937 100%);
            border-radius: 6px 6px 0 0;
            position: absolute;
            top: 0;
            box-shadow: 
                0 3px 10px rgba(0,0,0,0.4),
                inset 0 2px 5px rgba(255,255,255,0.2);
        }
        
        .vial-cap::before {
            content: '';
            position: absolute;
            top: 6px;
            left: 8%;
            right: 8%;
            height: 4px;
            background: linear-gradient(90deg, transparent, rgba(255,255,255,0.4), transparent);
            border-radius: 2px;
        }
        
        .vial-cap::after {
            content: '';
            position: absolute;
            bottom: 0;
            left: 0;
            right: 0;
            height: 3px;
            background: linear-gradient(90deg, #6b7280, #9ca3af, #6b7280);
            border-radius: 0 0 4px 4px;
        }
        
        .vial-label {
            position: absolute;
            top: 22px;
            left: 5px;
            right: 5px;
            background: linear-gradient(180deg, #ffffff 0%, #f3f4f6 100%);
            padding: 5px;
            font-size: 9px;
            text-align: center;
            border-radius: 4px;
            box-shadow: 0 2px 8px rgba(0,0,0,0.15);
            border: 1px solid #e5e7eb;
        }
        
        .liquid-in-syringe {
            position: absolute;
            bottom: 0;
            width: 100%;
            height: 0%;
            transition: height 0.5s cubic-bezier(0.34, 1.56, 0.64, 1);
            border-radius: 0 0 4px 4px;
            box-shadow: inset 0 0 20px rgba(0,0,0,0.15);
        }
        
        .liquid-in-syringe::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            height: 12px;
            background: linear-gradient(180deg, rgba(255,255,255,0.4) 0%, transparent 100%);
            animation: syringeLiquidWave 2s ease-in-out infinite;
        }
        
        @keyframes syringeLiquidWave {
            0%, 100% { transform: scaleY(1); }
            50% { transform: scaleY(1.1); }
        }
        
        .measurement-lines {
            position: absolute;
            right: 5px;
            top: 12px;
            bottom: 12px;
            width: 25px;
        }
        
        .measurement-line {
            position: absolute;
            right: 0;
            height: 2px;
            background: linear-gradient(90deg, #6366f1, #4f46e5);
            width: 12px;
            box-shadow: 1px 0 3px rgba(99, 102, 241, 0.5);
        }
        
        .measurement-line.major {
            width: 18px;
            background: linear-gradient(90deg, #4f46e5, #4338ca);
            box-shadow: 1px 0 5px rgba(79, 70, 229, 0.7);
        }
        
        .measurement-line::before {
            content: '';
            position: absolute;
            left: -3px;
            top: 50%;
            transform: translateY(-50%);
            width: 3px;
            height: 3px;
            background: #6366f1;
            border-radius: 50%;
        }
        
        /* Air bubbles in syringe */
        .air-bubble {
            position: absolute;
            background: radial-gradient(circle at 30% 30%, rgba(255,255,255,0.9), rgba(255,255,255,0.4));
            border-radius: 50%;
            box-shadow: inset 0 -2px 4px rgba(0,0,0,0.1);
            animation: bubbleRise 2s ease-in infinite;
        }
        
        @keyframes bubbleRise {
            0%, 100% { transform: translateY(0) scale(1); }
            50% { transform: translateY(-10px) scale(1.1); }
        }
        
        /* Air flow animation */
        .air-flow {
            position: absolute;
            width: 4px;
            height: 20px;
            background: linear-gradient(180deg, transparent, rgba(255,255,255,0.6), transparent);
            border-radius: 2px;
            animation: airFlowDown 0.5s linear infinite;
        }
        
        @keyframes airFlowDown {
            0% { transform: translateY(-20px); opacity: 0; }
            50% { opacity: 1; }
            100% { transform: translateY(30px); opacity: 0; }
        }
        
        .iv-bag {
            position: relative;
            width: 135px;
            height: 200px;
            cursor: pointer;
            transition: transform 0.4s cubic-bezier(0.34, 1.56, 0.64, 1);
        }
        
        .iv-bag:hover {
            transform: scale(1.03) translateY(-3px);
        }
        
        .iv-bag-body {
            width: 100%;
            height: 160px;
            background: linear-gradient(180deg, 
                rgba(200,230,255,0.35) 0%, 
                rgba(180,220,255,0.6) 40%,
                rgba(150,200,255,0.85) 100%);
            border: 2px solid #3b82f6;
            border-radius: 12px 12px 24px 24px;
            position: relative;
            overflow: hidden;
            box-shadow: 
                inset 0 0 30px rgba(59, 130, 246, 0.25),
                0 8px 25px rgba(59, 130, 246, 0.3),
                inset 4px 0 20px rgba(255,255,255,0.5);
        }
        
        .iv-bag-body::before {
            content: '';
            position: absolute;
            top: 15px;
            left: 12px;
            width: 20px;
            height: 120px;
            background: linear-gradient(90deg, rgba(255,255,255,0.7), transparent);
            border-radius: 15px;
            filter: blur(3px);
        }
        
        .iv-liquid {
            position: absolute;
            bottom: 0;
            width: 100%;
            height: 60%;
            transition: all 0.6s cubic-bezier(0.34, 1.56, 0.64, 1);
            box-shadow: inset 0 0 25px rgba(0,0,0,0.12);
        }
        
        .iv-liquid::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            height: 20px;
            background: linear-gradient(180deg, rgba(255,255,255,0.5) 0%, transparent 100%);
            animation: ivWave 4s ease-in-out infinite;
        }
        
        @keyframes ivWave {
            0%, 100% { transform: scaleX(1) translateY(0); }
            25% { transform: scaleX(1.05) translateY(-2px); }
            50% { transform: scaleX(1) translateY(0); }
            75% { transform: scaleX(1.05) translateY(2px); }
        }
        
        .iv-liquid::after {
            content: '';
            position: absolute;
            bottom: 8px;
            left: 15%;
            right: 15%;
            height: 8px;
            background: linear-gradient(90deg, transparent, rgba(255,255,255,0.4), transparent);
            border-radius: 50%;
            filter: blur(2px);
        }
        
        .iv-port {
            position: absolute;
            bottom: -18px;
            left: 50%;
            transform: translateX(-50%);
            width: 36px;
            height: 24px;
            background: linear-gradient(180deg, #06b6d4 0%, #0891b2 50%, #0e7490 100%);
            border-radius: 5px;
            box-shadow: 
                0 3px 10px rgba(6, 182, 212, 0.5),
                inset 0 2px 8px rgba(255,255,255,0.3);
        }
        
        .iv-port::before {
            content: '';
            position: absolute;
            top: 4px;
            left: 5px;
            right: 5px;
            height: 4px;
            background: linear-gradient(90deg, transparent, rgba(255,255,255,0.5), transparent);
            border-radius: 2px;
        }
        
        .drop-animation {
            position: absolute;
            width: 10px;
            height: 10px;
            border-radius: 50%;
            animation: dropFall 1.4s cubic-bezier(0.4, 0, 0.2, 1) infinite;
            box-shadow: 0 0 10px currentColor;
        }
        
        @keyframes dropFall {
            0% { 
                opacity: 1; 
                transform: translateY(0) scale(1);
            }
            60% {
                opacity: 0.8;
                transform: translateY(40px) scale(0.95);
            }
            100% { 
                opacity: 0; 
                transform: translateY(60px) scale(0.3);
            }
        }
        
        .interactive-btn {
            transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
        }
        
        .interactive-btn:hover:not(:disabled) {
            transform: translateY(-3px) scale(1.02);
            box-shadow: 0 8px 25px rgba(0,0,0,0.2);
        }
        
        .interactive-btn:active:not(:disabled) {
            transform: translateY(-1px) scale(0.98);
        }
        
        .shake {
            animation: shake 0.6s cubic-bezier(0.36, 0.07, 0.19, 0.97);
        }
        
        @keyframes shake {
            0%, 100% { transform: translateX(0) rotate(0deg); }
            10% { transform: translateX(-12px) rotate(-7deg); }
            20% { transform: translateX(12px) rotate(7deg); }
            30% { transform: translateX(-12px) rotate(-7deg); }
            40% { transform: translateX(12px) rotate(7deg); }
            50% { transform: translateX(-10px) rotate(-5deg); }
            60% { transform: translateX(10px) rotate(5deg); }
            70% { transform: translateX(-8px) rotate(-4deg); }
            80% { transform: translateX(8px) rotate(4deg); }
            90% { transform: translateX(-4px) rotate(-2deg); }
        }
        
        .mixing-active {
            animation: mixRotate 0.5s cubic-bezier(0.34, 1.56, 0.64, 1);
        }
        
        @keyframes mixRotate {
            0%, 100% { 
                transform: rotate(0deg) scale(1);
            }
            25% { 
                transform: rotate(-8deg) scale(1.03);
            }
            50% { 
                transform: rotate(0deg) scale(1);
            }
            75% { 
                transform: rotate(8deg) scale(1.03);
            }
        }
        
        .glow-success {
            animation: successGlow 1.2s cubic-bezier(0.4, 0, 0.2, 1);
        }
        
        @keyframes successGlow {
            0%, 100% { 
                box-shadow: 0 0 10px #10b981;
                transform: scale(1);
            }
            50% { 
                box-shadow: 0 0 40px #10b981, 0 0 20px #10b981;
                transform: scale(1.05);
            }
        }
        
        .drug-card {
            transition: all 0.4s cubic-bezier(0.34, 1.56, 0.64, 1);
            cursor: pointer;
            background: white;
        }
        
        .drug-card:hover {
            transform: translateY(-12px) scale(1.03);
            box-shadow: 0 25px 50px rgba(0,0,0,0.2);
        }
        
        .drug-card.selected {
            border-color: #0ea5e9;
            background: linear-gradient(135deg, #e0f2fe 0%, #bae6fd 100%);
            box-shadow: 0 0 0 3px #0ea5e9, 0 20px 40px rgba(14, 165, 233, 0.3);
            transform: scale(1.05);
        }
        
        .drug-card img {
            transition: transform 0.4s cubic-bezier(0.34, 1.56, 0.64, 1), filter 0.3s ease;
            filter: drop-shadow(0 4px 10px rgba(0,0,0,0.15));
        }
        
        .drug-card:hover img {
            transform: scale(1.12) rotate(-3deg);
        }
        
        .calc-input {
            transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
        }
        
        .calc-input:focus {
            border-color: #0ea5e9;
            box-shadow: 0 0 0 4px rgba(14, 165, 233, 0.15);
            transform: translateY(-1px);
        }
        
        .pulse-animation {
            animation: pulse 2.5s cubic-bezier(0.4, 0, 0.6, 1) infinite;
        }
        
        @keyframes pulse {
            0%, 100% { 
                opacity: 1; 
                transform: scale(1);
            }
            50% { 
                opacity: 0.6; 
                transform: scale(1.08);
            }
        }
        
        .swirl-particle {
            position: absolute;
            width: 12px;
            height: 12px;
            border-radius: 50%;
            animation: swirl 1.8s cubic-bezier(0.4, 0, 0.2, 1) infinite;
            box-shadow: 0 0 15px currentColor;
        }
        
        @keyframes swirl {
            0% { 
                transform: rotate(0deg) translateX(35px) rotate(0deg); 
                opacity: 1;
                scale: 1;
            }
            50% {
                opacity: 0.6;
                scale: 0.8;
            }
            100% { 
                transform: rotate(360deg) translateX(35px) rotate(-360deg); 
                opacity: 0;
                scale: 0.3;
            }
        }
        
        .modal-content {
            max-height: 70vh;
            overflow-y: auto;
            scrollbar-width: thin;
            scrollbar-color: #0ea5e9 #e0f2fe;
        }
        
        .modal-content::-webkit-scrollbar {
            width: 8px;
        }
        
        .modal-content::-webkit-scrollbar-track {
            background: #e0f2fe;
            border-radius: 10px;
        }
        
        .modal-content::-webkit-scrollbar-thumb {
            background: linear-gradient(180deg, #0ea5e9, #0284c7);
            border-radius: 10px;
        }
        
        .mix-counter {
            font-size: 3rem;
            font-weight: 800;
            background: linear-gradient(135deg, #7c3aed, #a855f7);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            text-shadow: 0 4px 20px rgba(124, 58, 237, 0.5);
            animation: counterPulse 0.3s cubic-bezier(0.34, 1.56, 0.64, 1);
        }
        
        @keyframes counterPulse {
            0% { transform: scale(0.5); opacity: 0; }
            50% { transform: scale(1.2); }
            100% { transform: scale(1); opacity: 1; }
        }
        
        .mix-progress {
            transition: width 0.4s cubic-bezier(0.34, 1.56, 0.64, 1);
            background: linear-gradient(90deg, #7c3aed, #a855f7, #c084fc, #7c3aed);
            background-size: 300% 100%;
            animation: progressFlow 2s linear infinite;
            box-shadow: 0 0 20px rgba(124, 58, 237, 0.6);
        }
        
        @keyframes progressFlow {
            0% { background-position: 0% 50%; }
            100% { background-position: 300% 50%; }
        }
        
        .click-hint {
            animation: bounce 1.2s cubic-bezier(0.34, 1.56, 0.64, 1) infinite;
        }
        
        @keyframes bounce {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-12px); }
        }
        
        .success-particle {
            position: fixed;
            width: 10px;
            height: 10px;
            border-radius: 50%;
            animation: successPop 0.9s cubic-bezier(0.34, 1.56, 0.64, 1) forwards;
            pointer-events: none;
            z-index: 9999;
        }
        
        @keyframes successPop {
            0% { 
                transform: scale(0) translate(0, 0); 
                opacity: 1;
            }
            30% {
                transform: scale(1.5) translate(var(--tx), var(--ty));
                opacity: 1;
            }
            100% { 
                transform: scale(0) translate(calc(var(--tx) * 2), calc(var(--ty) * 2)); 
                opacity: 0;
            }
        }
        
        .floating {
            animation: float 3s ease-in-out infinite;
        }
        
        @keyframes float {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-10px); }
        }
        
        .shimmer {
            position: relative;
            overflow: hidden;
        }
        
        .shimmer::after {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255,255,255,0.3), transparent);
            animation: shimmer 2s infinite;
        }
        
        @keyframes shimmer {
            0% { left: -100%; }
            100% { left: 100%; }
        }
        
        .card-hover {
            transition: all 0.4s cubic-bezier(0.34, 1.56, 0.64, 1);
        }
        
        .card-hover:hover {
            transform: translateY(-5px);
            box-shadow: 0 20px 40px rgba(0,0,0,0.15);
        }
        
        .gradient-text {
            background: linear-gradient(135deg, #667eea, #764ba2);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }
        
        .glass-effect {
            background: rgba(255, 255, 255, 0.95);
            backdrop-filter: blur(20px);
            border: 1px solid rgba(255, 255, 255, 0.3);
        }
        
        .header-glass {
            background: rgba(255, 255, 255, 0.98);
            backdrop-filter: blur(15px);
            box-shadow: 0 4px 30px rgba(0, 0, 0, 0.1);
        }
        
        .step-indicator {
            transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
        }
        
        .step-indicator.active {
            background: linear-gradient(135deg, #0ea5e9, #0284c7);
            color: white;
            transform: scale(1.1);
            box-shadow: 0 4px 15px rgba(14, 165, 233, 0.4);
        }
        
        .loading-spinner {
            width: 40px;
            height: 40px;
            border: 4px solid #e0e7ff;
            border-top-color: #0ea5e9;
            border-radius: 50%;
            animation: spin 1s linear infinite;
        }
        
        @keyframes spin {
            to { transform: rotate(360deg); }
        }
        
        .tooltip {
            position: relative;
        }
        
        .tooltip::before {
            content: attr(data-tooltip);
            position: absolute;
            bottom: 100%;
            left: 50%;
            transform: translateX(-50%) translateY(-5px);
            background: #1f2937;
            color: white;
            padding: 8px 12px;
            border-radius: 8px;
            font-size: 12px;
            white-space: nowrap;
            opacity: 0;
            visibility: hidden;
            transition: all 0.3s ease;
        }
        
        .tooltip:hover::before {
            opacity: 1;
            visibility: visible;
            transform: translateX(-50%) translateY(-10px);
        }
        
        /* Credit Section */
        .credit-section {
            background: linear-gradient(135deg, #1e3a8a 0%, #3730a3 100%);
            color: white;
        }
        
        .credit-card {
            background: rgba(255,255,255,0.1);
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255,255,255,0.2);
        }
        
        /* PPE Animation Styles - Improved */
        .ppe-animation-container {
            width: 280px;
            height: 320px;
            margin: 0 auto;
            position: relative;
        }
        
        .ppe-figure {
            position: relative;
            width: 100%;
            height: 100%;
        }
        
        .ppe-item {
            transition: all 0.6s cubic-bezier(0.34, 1.56, 0.64, 1);
            opacity: 0;
        }
        
        .ppe-item.show {
            opacity: 1;
        }
        
        .ppe-hair-cover {
            transform: translateY(-30px) scale(0.5);
        }
        
        .ppe-hair-cover.show {
            transform: translateY(0) scale(1);
        }
        
        .ppe-goggles {
            transform: translateX(-50px) scale(0.5);
        }
        
        .ppe-goggles.show {
            transform: translateX(0) scale(1);
        }
        
        .ppe-mask {
            transform: translateX(50px) scale(0.5);
        }
        
        .ppe-mask.show {
            transform: translateX(0) scale(1);
        }
        
        .ppe-gown {
            transform: translateY(40px) scale(0.5);
        }
        
        .ppe-gown.show {
            transform: translateY(0) scale(1);
        }
        
        .ppe-gloves-left {
            transform: translate(-40px, 30px) scale(0.5) rotate(-30deg);
        }
        
        .ppe-gloves-left.show {
            transform: translate(0, 0) scale(1) rotate(0deg);
        }
        
        .ppe-gloves-right {
            transform: translate(40px, 30px) scale(0.5) rotate(30deg);
        }
        
        .ppe-gloves-right.show {
            transform: translate(0, 0) scale(1) rotate(0deg);
        }
        
        /* Disposal Animation - Improved with Centered Bin */
        .disposal-animation-container {
            width: 350px;
            height: 350px;
            margin: 0 auto;
            position: relative;
        }
        
        .disposal-item {
            transition: all 0.7s cubic-bezier(0.34, 1.56, 0.64, 1);
            opacity: 1;
        }
        
        .disposal-item.disposed {
            opacity: 0;
            transform: translate(0px, 140px) scale(0.2) rotate(180deg);
        }
        
        .disposal-bin {
            position: absolute;
            bottom: 20px;
            left: 50%;
            transform: translateX(-50%);
        }
        
        .disposal-needle {
            position: absolute;
            top: 40px;
            left: 30px;
        }
        
        .disposal-syringe {
            position: absolute;
            top: 40px;
            left: 160px;
        }
        
        .disposal-vial {
            position: absolute;
            top: 40px;
            right: 160px;
        }
        
        .disposal-gloves {
            position: absolute;
            top: 40px;
            right: 30px;
        }
        
        /* Hand Washing Animation */
        .hand-wash-container {
            width: 300px;
            height: 300px;
            margin: 0 auto;
            position: relative;
        }
        
        .water-drop {
            position: absolute;
            width: 8px;
            height: 12px;
            background: linear-gradient(180deg, #60a5fa, #3b82f6);
            border-radius: 0 50% 50% 50%;
            animation: waterDrop 1s ease-in infinite;
            opacity: 0;
        }
        
        @keyframes waterDrop {
            0% {
                transform: translateY(0) scale(1);
                opacity: 1;
            }
            100% {
                transform: translateY(80px) scale(0.5);
                opacity: 0;
            }
        }
        
        .soap-bubble {
            position: absolute;
            background: radial-gradient(circle at 30% 30%, rgba(255,255,255,0.9), rgba(255,255,255,0.4));
            border-radius: 50%;
            animation: soapFloat 2s ease-in-out infinite;
        }
        
        @keyframes soapFloat {
            0%, 100% { transform: translateY(0) scale(1); }
            50% { transform: translateY(-15px) scale(1.1); }
        }
        
        .hand-icon {
            transition: all 0.3s ease;
        }
        
        .hand-icon.washing {
            animation: handRub 0.5s ease-in-out infinite;
        }
        
        @keyframes handRub {
            0%, 100% { transform: translateX(0); }
            50% { transform: translateX(-10px); }
        }
    </style>
</head>
<body class="min-h-screen flex flex-col">

    <!-- Header -->
    <header class="header-glass py-4 px-6 sticky top-0 z-50 border-b border-gray-200/50">
        <div class="max-w-7xl mx-auto flex justify-between items-center">
            <div class="flex items-center gap-4">
                <div class="bg-gradient-to-br from-blue-500 to-purple-600 p-3 rounded-2xl shadow-lg">
                    <svg class="w-8 h-8 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19.428 15.428a2 2 0 00-1.022-.547l-2.384-.477a6 6 0 00-3.86.517l-.318.158a6 6 0 01-3.86.517L6.05 15.21a2 2 0 00-1.806.547M8 4h8l-1 1v5.172a2 2 0 00.586 1.414l5 5c1.26 1.26.367 3.414-1.415 3.414H4.828c-1.782 0-2.674-2.154-1.414-3.414l5-5A2 2 0 009 10.172V5L8 4z"></path>
                    </svg>
                </div>
                <div>
                    <h1 class="text-xl md:text-2xl font-bold gradient-text">المحاكي الاحترافي لتحضير العلاج الكيميائي</h1>
                    <p class="text-xs text-gray-500 font-medium">IV Chemotherapy Mixing Simulator - للصيادلة المحترفين</p>
                </div>
            </div>
            <div class="flex items-center gap-4">
                <div class="hidden md:flex items-center gap-2 bg-gradient-to-r from-blue-50 to-purple-50 px-4 py-2 rounded-full border border-blue-200">
                    <div class="w-3 h-3 bg-green-500 rounded-full animate-pulse"></div>
                    <span class="text-sm font-semibold text-gray-700">الخطوة <span id="current-step-num" class="text-blue-600">1</span> من <span id="total-steps">10</span></span>
                </div>
            </div>
        </div>
        <div class="max-w-7xl mx-auto mt-4">
            <div class="flex items-center gap-4">
                <div class="flex-1 bg-gray-200/80 rounded-full h-3 overflow-hidden shadow-inner">
                    <div id="progress-bar" class="h-3 rounded-full progress-bar" style="width: 10%"></div>
                </div>
                <span id="progress-percent" class="text-sm font-bold text-blue-600 min-w-[50px]">10%</span>
            </div>
        </div>
    </header>

    <!-- Main Content -->
    <main class="flex-grow container mx-auto px-4 py-8 max-w-7xl relative z-10">
        
        <!-- Step 1: Drug Selection -->
        <div id="step-1" class="step-container active">
            <div class="glass-effect rounded-3xl shadow-2xl p-6 md:p-10 border border-white/50">
                <div class="text-center mb-8">
                    <div class="inline-flex items-center justify-center w-16 h-16 bg-gradient-to-br from-blue-500 to-purple-600 rounded-2xl shadow-lg mb-4 floating">
                        <span class="text-3xl">📋</span>
                    </div>
                    <h2 class="text-3xl font-bold text-gray-800 mb-3">الخطوة 1: اختيار بروتوكول العلاج</h2>
                    <p class="text-gray-600 text-lg">اختر بروتوكول العلاج الكيميائي الذي تريد التدرب عليه</p>
                </div>
                
                <div class="grid md:grid-cols-2 lg:grid-cols-4 gap-6 mb-8">
                    <!-- Cisplatin Card -->
                    <div onclick="selectDrug('cisplatin')" id="drug-cisplatin" class="drug-card border-2 border-gray-200 rounded-2xl p-5 card-hover shimmer">
                        <div class="h-36 bg-gradient-to-br from-yellow-50 to-yellow-100 rounded-xl mb-4 flex items-center justify-center overflow-hidden border border-yellow-200">
                            <img src="https://image.qwenlm.ai/public_source/a19eb0bf-f4ce-4bc1-9193-96bbe9311fcb/16ffb4102-ca38-412c-83d5-62f91f2a0313.png" alt="Cisplatin" class="h-32 object-contain">
                        </div>
                        <h3 class="font-bold text-gray-800 text-lg">Cisplatin</h3>
                        <p class="text-sm text-gray-600 mb-3">سيسبلاتين</p>
                        <div class="space-y-2 text-xs bg-yellow-50 p-3 rounded-xl border border-yellow-200">
                            <div class="flex justify-between">
                                <span class="text-gray-600">الجرعة:</span>
                                <span class="font-bold text-gray-800">75 mg/m²</span>
                            </div>
                            <div class="flex justify-between">
                                <span class="text-gray-600">المحلول:</span>
                                <span class="font-bold text-gray-800">NS 0.9%</span>
                            </div>
                        </div>
                        <button onclick="event.stopPropagation(); showDrugInfo('cisplatin')" class="mt-4 w-full text-xs bg-gradient-to-r from-blue-500 to-blue-600 text-white py-2 rounded-xl hover:from-blue-600 hover:to-blue-700 transition-all font-semibold shadow-md">
                            ℹ️ معلومات الدواء
                        </button>
                    </div>
                    
                    <!-- Doxorubicin Card -->
                    <div onclick="selectDrug('doxorubicin')" id="drug-doxorubicin" class="drug-card border-2 border-gray-200 rounded-2xl p-5 card-hover shimmer">
                        <div class="h-36 bg-gradient-to-br from-red-50 to-red-100 rounded-xl mb-4 flex items-center justify-center overflow-hidden border border-red-200">
                            <img src="https://image.qwenlm.ai/public_source/a19eb0bf-f4ce-4bc1-9193-96bbe9311fcb/196239f19-537c-4cd6-8171-9fd47476283e.png" alt="Doxorubicin" class="h-32 object-contain">
                        </div>
                        <h3 class="font-bold text-gray-800 text-lg">Doxorubicin</h3>
                        <p class="text-sm text-gray-600 mb-3">دوكسوروبيسين</p>
                        <div class="space-y-2 text-xs bg-red-50 p-3 rounded-xl border border-red-200">
                            <div class="flex justify-between">
                                <span class="text-gray-600">الجرعة:</span>
                                <span class="font-bold text-gray-800">60 mg/m²</span>
                            </div>
                            <div class="flex justify-between">
                                <span class="text-gray-600">المحلول:</span>
                                <span class="font-bold text-gray-800">NS 0.9%</span>
                            </div>
                        </div>
                        <button onclick="event.stopPropagation(); showDrugInfo('doxorubicin')" class="mt-4 w-full text-xs bg-gradient-to-r from-blue-500 to-blue-600 text-white py-2 rounded-xl hover:from-blue-600 hover:to-blue-700 transition-all font-semibold shadow-md">
                            ℹ️ معلومات الدواء
                        </button>
                    </div>
                    
                    <!-- Paclitaxel Card -->
                    <div onclick="selectDrug('paclitaxel')" id="drug-paclitaxel" class="drug-card border-2 border-gray-200 rounded-2xl p-5 card-hover shimmer">
                        <div class="h-36 bg-gradient-to-br from-purple-50 to-purple-100 rounded-xl mb-4 flex items-center justify-center overflow-hidden border border-purple-200">
                            <img src="https://image.qwenlm.ai/public_source/a19eb0bf-f4ce-4bc1-9193-96bbe9311fcb/18a5b6b6c-79bb-46ed-8d0b-ce124b21489b.png" alt="Paclitaxel" class="h-32 object-contain">
                        </div>
                        <h3 class="font-bold text-gray-800 text-lg">Paclitaxel</h3>
                        <p class="text-sm text-gray-600 mb-3">باكليتاكسيل</p>
                        <div class="space-y-2 text-xs bg-purple-50 p-3 rounded-xl border border-purple-200">
                            <div class="flex justify-between">
                                <span class="text-gray-600">الجرعة:</span>
                                <span class="font-bold text-gray-800">175 mg/m²</span>
                            </div>
                            <div class="flex justify-between">
                                <span class="text-gray-600">المحلول:</span>
                                <span class="font-bold text-gray-800">NS 0.9%</span>
                            </div>
                        </div>
                        <button onclick="event.stopPropagation(); showDrugInfo('paclitaxel')" class="mt-4 w-full text-xs bg-gradient-to-r from-blue-500 to-blue-600 text-white py-2 rounded-xl hover:from-blue-600 hover:to-blue-700 transition-all font-semibold shadow-md">
                            ℹ️ معلومات الدواء
                        </button>
                    </div>

                    <!-- 5FU Card -->
                    <div onclick="selectDrug('fu')" id="drug-fu" class="drug-card border-2 border-gray-200 rounded-2xl p-5 card-hover shimmer">
                        <div class="h-36 bg-gradient-to-br from-green-50 to-green-100 rounded-xl mb-4 flex items-center justify-center overflow-hidden border border-green-200">
                            <img src="https://image.qwenlm.ai/public_source/a19eb0bf-f4ce-4bc1-9193-96bbe9311fcb/17c6a4486-cc4f-48b4-8bfa-ab8d7ac60400.png" alt="5-FU" class="h-32 object-contain">
                        </div>
                        <h3 class="font-bold text-gray-800 text-lg">5-Fluorouracil</h3>
                        <p class="text-sm text-gray-600 mb-3">فلورويوراسيل</p>
                        <div class="space-y-2 text-xs bg-green-50 p-3 rounded-xl border border-green-200">
                            <div class="flex justify-between">
                                <span class="text-gray-600">الجرعة:</span>
                                <span class="font-bold text-gray-800">400 mg/m²</span>
                            </div>
                            <div class="flex justify-between">
                                <span class="text-gray-600">المحلول:</span>
                                <span class="font-bold text-gray-800">D5W</span>
                            </div>
                        </div>
                        <button onclick="event.stopPropagation(); showDrugInfo('fu')" class="mt-4 w-full text-xs bg-gradient-to-r from-blue-500 to-blue-600 text-white py-2 rounded-xl hover:from-blue-600 hover:to-blue-700 transition-all font-semibold shadow-md">
                            ℹ️ معلومات الدواء
                        </button>
                    </div>
                </div>
                
                <div id="drug-warning" class="hidden bg-gradient-to-r from-red-50 to-orange-50 border-r-4 border-red-500 p-5 rounded-2xl mb-6 shadow-lg">
                    <div class="flex items-start gap-3">
                        <span class="text-2xl">⚠️</span>
                        <div>
                            <h4 class="font-bold text-red-800 mb-2">تحذير خاص بهذا الدواء:</h4>
                            <p id="drug-warning-text" class="text-sm text-red-700 leading-relaxed"></p>
                        </div>
                    </div>
                </div>
                
                <button onclick="confirmDrugSelection()" id="confirm-drug-btn" disabled class="w-full py-5 btn-primary text-white rounded-2xl font-bold text-lg shadow-xl disabled:opacity-50 disabled:cursor-not-allowed">
                    ✅ تأكيد اختيار الدواء والانتقال لحساب الجرعة
                </button>
            </div>
        </div>

        <!-- Step 2: Patient Data & BSA Calculation -->
        <div id="step-2" class="step-container">
            <div class="glass-effect rounded-3xl shadow-2xl p-6 md:p-10 border border-white/50">
                <div class="text-center mb-8">
                    <div class="inline-flex items-center justify-center w-16 h-16 bg-gradient-to-br from-green-500 to-emerald-600 rounded-2xl shadow-lg mb-4 floating">
                        <span class="text-3xl">🧮</span>
                    </div>
                    <h2 class="text-3xl font-bold text-gray-800 mb-3">الخطوة 2: حساب مساحة سطح الجسم (BSA)</h2>
                    <p class="text-gray-600 text-lg">أدخل بيانات المريض لحساب BSA باستخدام معادلة Mosteller</p>
                </div>
                
                <div class="grid md:grid-cols-2 gap-8">
                    <div>
                        <div class="bg-gradient-to-br from-blue-50 to-indigo-50 rounded-2xl p-6 mb-6 border border-blue-100 shadow-lg">
                            <h3 class="font-bold text-blue-800 mb-5 flex items-center gap-2 text-lg">
                                <span>📊</span> بيانات المريض
                            </h3>
                            <div class="space-y-5">
                                <div>
                                    <label class="block text-sm font-semibold text-gray-700 mb-2">الوزن (kg)</label>
                                    <input type="number" id="patient-weight" value="70" class="calc-input w-full px-5 py-4 border-2 border-gray-200 rounded-xl focus:outline-none font-semibold text-lg" onchange="calculateBSA()">
                                </div>
                                <div>
                                    <label class="block text-sm font-semibold text-gray-700 mb-2">الطول (cm)</label>
                                    <input type="number" id="patient-height" value="175" class="calc-input w-full px-5 py-4 border-2 border-gray-200 rounded-xl focus:outline-none font-semibold text-lg" onchange="calculateBSA()">
                                </div>
                            </div>
                        </div>
                        
                        <div class="bg-gradient-to-r from-green-50 to-emerald-50 border-r-4 border-green-500 p-5 rounded-2xl shadow-lg">
                            <h4 class="font-bold text-green-800 mb-3 flex items-center gap-2">
                                <span>📐</span> معادلة Mosteller:
                            </h4>
                            <p class="text-sm text-green-700 font-mono bg-white p-3 rounded-xl shadow-inner">BSA = √(الطول × الوزن / 3600)</p>
                        </div>
                    </div>
                    
                    <div class="bg-gradient-to-br from-gray-50 to-blue-50 rounded-2xl p-8 flex flex-col justify-center items-center border border-gray-200 shadow-xl">
                        <div class="text-center mb-6">
                            <p class="text-gray-600 mb-3 font-medium">مساحة سطح الجسم المحسوبة:</p>
                            <div class="text-6xl font-black bg-gradient-to-r from-blue-600 to-purple-600 bg-clip-text text-transparent" id="bsa-result">1.87</div>
                            <p class="text-sm text-gray-500 mt-2 font-semibold">m²</p>
                        </div>
                        
                        <div class="w-full bg-white rounded-2xl p-5 mb-6 shadow-lg border border-gray-100">
                            <p class="text-sm text-gray-600 mb-2 font-medium">الدواء المختار:</p>
                            <p class="font-bold text-xl text-gray-800" id="selected-drug-name">-</p>
                            <p class="text-sm text-gray-500" id="selected-drug-dose">-</p>
                        </div>
                        
                        <button onclick="confirmBSA()" id="confirm-bsa-btn" class="w-full py-4 btn-primary text-white rounded-2xl font-bold shadow-xl interactive-btn">
                            ✅ تأكيد وحساب الجرعة
                        </button>
                    </div>
                </div>
            </div>
        </div>

        <!-- Step 3: Dose Calculation -->
        <div id="step-3" class="step-container">
            <div class="glass-effect rounded-3xl shadow-2xl p-6 md:p-10 border border-white/50">
                <div class="text-center mb-8">
                    <div class="inline-flex items-center justify-center w-16 h-16 bg-gradient-to-br from-purple-500 to-pink-600 rounded-2xl shadow-lg mb-4 floating">
                        <span class="text-3xl">💊</span>
                    </div>
                    <h2 class="text-3xl font-bold text-gray-800 mb-3">الخطوة 3: حساب جرعة الدواء</h2>
                    <p class="text-gray-600 text-lg">احسب الجرعة النهائية بناءً على BSA وتركيز الدواء</p>
                </div>
                
                <div class="grid md:grid-cols-3 gap-6 mb-8">
                    <div class="bg-gradient-to-br from-blue-50 to-blue-100 rounded-2xl p-6 text-center shadow-lg border border-blue-200 card-hover">
                        <div class="w-12 h-12 bg-blue-500 rounded-xl flex items-center justify-center mx-auto mb-3 shadow-lg">
                            <span class="text-2xl">📏</span>
                        </div>
                        <p class="text-sm text-gray-600 mb-2 font-medium">BSA المحسوبة</p>
                        <p class="text-4xl font-black text-blue-600" id="calc-bsa">1.87</p>
                        <p class="text-xs text-gray-500 mt-1 font-semibold">m²</p>
                    </div>
                    <div class="bg-gradient-to-br from-yellow-50 to-yellow-100 rounded-2xl p-6 text-center shadow-lg border border-yellow-200 card-hover">
                        <div class="w-12 h-12 bg-yellow-500 rounded-xl flex items-center justify-center mx-auto mb-3 shadow-lg">
                            <span class="text-2xl">💉</span>
                        </div>
                        <p class="text-sm text-gray-600 mb-2 font-medium">الجرعة القياسية</p>
                        <p class="text-4xl font-black text-yellow-600" id="calc-standard-dose">75</p>
                        <p class="text-xs text-gray-500 mt-1 font-semibold">mg/m²</p>
                    </div>
                    <div class="bg-gradient-to-br from-green-50 to-green-100 rounded-2xl p-6 text-center shadow-lg border border-green-200 card-hover">
                        <div class="w-12 h-12 bg-green-500 rounded-xl flex items-center justify-center mx-auto mb-3 shadow-lg">
                            <span class="text-2xl">✨</span>
                        </div>
                        <p class="text-sm text-gray-600 mb-2 font-medium">الجرعة الكلية</p>
                        <p class="text-4xl font-black text-green-600" id="calc-total-dose">140.25</p>
                        <p class="text-xs text-gray-500 mt-1 font-semibold">mg</p>
                    </div>
                </div>
                
                <div class="bg-white border-2 border-gray-200 rounded-2xl p-6 mb-8 shadow-xl">
                    <h3 class="font-bold text-gray-800 mb-5 flex items-center gap-2 text-xl">
                        <span>📝</span> تفاصيل الحساب:
                    </h3>
                    <div class="space-y-4 font-mono text-sm">
                        <div class="flex justify-between items-center p-4 bg-gradient-to-r from-gray-50 to-gray-100 rounded-xl shadow-inner">
                            <span class="font-medium text-gray-700">الجرعة الكلية = BSA × الجرعة القياسية</span>
                            <span class="font-bold text-gray-900" id="calc-formula-1">1.87 × 75 = 140.25 mg</span>
                        </div>
                        <div class="flex justify-between items-center p-4 bg-gradient-to-r from-gray-50 to-gray-100 rounded-xl shadow-inner">
                            <span class="font-medium text-gray-700">تركيز الدواء المتوفر</span>
                            <span class="font-bold text-gray-900" id="calc-concentration">1 mg/mL</span>
                        </div>
                        <div class="flex justify-between items-center p-4 bg-gradient-to-r from-green-50 to-emerald-100 rounded-xl border-2 border-green-400 shadow-lg">
                            <span class="font-bold text-green-800 text-lg">الحجم المطلوب سحبه</span>
                            <span class="font-black text-green-700 text-2xl" id="calc-volume">140.25 mL</span>
                        </div>
                    </div>
                </div>
                
                <button onclick="confirmDose()" id="confirm-dose-btn" class="w-full py-5 btn-primary text-white rounded-2xl font-bold text-lg shadow-xl interactive-btn">
                    ✅ تأكيد الجرعة والانتقال للتحضير
                </button>
            </div>
        </div>

        <!-- Step 4: PPE with Improved Animations -->
        <div id="step-4" class="step-container">
            <div class="glass-effect rounded-3xl shadow-2xl overflow-hidden border border-white/50">
                <div class="md:flex">
                    <div class="md:w-1/2 p-6 md:p-10">
                        <h2 class="text-3xl font-bold text-gray-800 mb-4">الخطوة 4: معدات الوقاية الشخصية</h2>
                        <p class="text-gray-600 mb-6 leading-relaxed text-lg">
                            قبل الدخول إلى غرفة التحضير والتعامل مع الأدوية الخطرة، يجب ارتداء معدات الوقاية الكاملة.
                        </p>
                        
                        <!-- PPE Animation Display - Improved -->
                        <div class="bg-gradient-to-br from-blue-50 to-indigo-50 rounded-2xl p-6 mb-6 border border-blue-200">
                            <p class="text-center text-gray-700 font-semibold mb-4">👤 اضغط على كل عنصر لارتدائه</p>
                            <div class="ppe-animation-container">
                                <svg class="ppe-figure" viewBox="0 0 280 320">
                                    <!-- Body Base (Silhouette) -->
                                    <defs>
                                        <linearGradient id="bodyGrad" x1="0%" y1="0%" x2="100%" y2="100%">
                                            <stop offset="0%" style="stop-color:#fca5a5"/>
                                            <stop offset="100%" style="stop-color:#f87171"/>
                                        </linearGradient>
                                    </defs>
                                    
                                    <!-- Body -->
                                    <ellipse cx="140" cy="280" rx="50" ry="30" fill="url(#bodyGrad)" opacity="0.4"/>
                                    <rect x="115" y="140" width="50" height="120" rx="8" fill="url(#bodyGrad)" opacity="0.4"/>
                                    <circle cx="140" cy="100" r="40" fill="url(#bodyGrad)" opacity="0.4"/>
                                    
                                    <!-- Hair Cover -->
                                    <g class="ppe-item ppe-hair-cover" id="ppe-hair-cover">
                                        <ellipse cx="140" cy="65" rx="45" ry="32" fill="#60a5fa" stroke="#2563eb" stroke-width="3"/>
                                        <path d="M100 70 Q140 50 180 70" fill="none" stroke="#2563eb" stroke-width="2" opacity="0.5"/>
                                        <path d="M105 75 Q140 58 175 75" fill="none" stroke="#2563eb" stroke-width="2" opacity="0.4"/>
                                        <ellipse cx="140" cy="60" rx="35" ry="22" fill="#93c5fd" opacity="0.5"/>
                                    </g>
                                    
                                    <!-- Goggles -->
                                    <g class="ppe-item ppe-goggles" id="ppe-goggles">
                                        <rect x="95" y="88" width="90" height="28" rx="6" fill="#60a5fa" stroke="#2563eb" stroke-width="3"/>
                                        <rect x="100" y="92" width="38" height="20" rx="3" fill="#dbeafe" opacity="0.8"/>
                                        <rect x="147" y="92" width="38" height="20" rx="3" fill="#dbeafe" opacity="0.8"/>
                                        <rect x="140" y="95" width="5" height="14" fill="#2563eb"/>
                                        <path d="M95 102 Q85 105 75 100" stroke="#2563eb" stroke-width="3" fill="none"/>
                                        <path d="M185 102 Q195 105 205 100" stroke="#2563eb" stroke-width="3" fill="none"/>
                                    </g>
                                    
                                    <!-- Mask -->
                                    <g class="ppe-item ppe-mask" id="ppe-mask">
                                        <rect x="105" y="118" width="70" height="38" rx="6" fill="#60a5fa" stroke="#2563eb" stroke-width="3"/>
                                        <path d="M112 128 L128 128" stroke="#2563eb" stroke-width="2" opacity="0.6"/>
                                        <path d="M112 138 L128 138" stroke="#2563eb" stroke-width="2" opacity="0.6"/>
                                        <path d="M112 148 L128 148" stroke="#2563eb" stroke-width="2" opacity="0.6"/>
                                        <path d="M105 130 Q95 135 90 125" stroke="#2563eb" stroke-width="3" fill="none"/>
                                        <path d="M175 130 Q185 135 190 125" stroke="#2563eb" stroke-width="3" fill="none"/>
                                        <ellipse cx="140" cy="145" rx="15" ry="8" fill="#3b82f6" opacity="0.4"/>
                                    </g>
                                    
                                    <!-- Gown -->
                                    <g class="ppe-item ppe-gown" id="ppe-gown">
                                        <path d="M100 155 L180 155 L195 260 L85 260 Z" fill="#60a5fa" stroke="#2563eb" stroke-width="3"/>
                                        <rect x="130" y="165" width="20" height="85" fill="#3b82f6" opacity="0.3"/>
                                        <circle cx="140" cy="180" r="5" fill="#2563eb"/>
                                        <circle cx="140" cy="205" r="5" fill="#2563eb"/>
                                        <circle cx="140" cy="230" r="5" fill="#2563eb"/>
                                        <path d="M100 155 L110 200" stroke="#2563eb" stroke-width="2" opacity="0.5"/>
                                        <path d="M180 155 L170 200" stroke="#2563eb" stroke-width="2" opacity="0.5"/>
                                    </g>
                                    
                                    <!-- Left Glove -->
                                    <g class="ppe-item ppe-gloves-left" id="ppe-gloves-left">
                                        <path d="M55 210 Q45 225 50 245 L70 245 Q80 225 75 210 Q70 200 65 200 Q60 200 55 210" fill="#60a5fa" stroke="#2563eb" stroke-width="3"/>
                                        <circle cx="58" cy="220" r="4" fill="#2563eb"/>
                                        <circle cx="65" cy="235" r="3" fill="#2563eb"/>
                                        <circle cx="72" cy="235" r="3" fill="#2563eb"/>
                                    </g>
                                    
                                    <!-- Right Glove -->
                                    <g class="ppe-item ppe-gloves-right" id="ppe-gloves-right">
                                        <path d="M225 210 Q235 225 230 245 L210 245 Q200 225 205 210 Q210 200 215 200 Q220 200 225 210" fill="#60a5fa" stroke="#2563eb" stroke-width="3"/>
                                        <circle cx="222" cy="220" r="4" fill="#2563eb"/>
                                        <circle cx="215" cy="235" r="3" fill="#2563eb"/>
                                        <circle cx="208" cy="235" r="3" fill="#2563eb"/>
                                    </g>
                                </svg>
                            </div>
                        </div>
                        
                        <div class="space-y-3">
                            <p class="font-semibold text-gray-700 mb-4 text-lg">اضغط لتأكيد ارتداء كل عنصر:</p>
                            <button onclick="togglePPE(this, 4, 'hair-cover')" class="check-item w-full text-right p-4 border-2 border-gray-200 rounded-xl relative hover:border-blue-300 transition-all text-base font-medium shadow-sm">
                                👒 قبعة واقية للشعر (Hair Cover)
                            </button>
                            <button onclick="togglePPE(this, 4, 'goggles')" class="check-item w-full text-right p-4 border-2 border-gray-200 rounded-xl relative hover:border-blue-300 transition-all text-base font-medium shadow-sm">
                                👓 نظارات واقية (Goggles)
                            </button>
                            <button onclick="togglePPE(this, 4, 'mask')" class="check-item w-full text-right p-4 border-2 border-gray-200 rounded-xl relative hover:border-blue-300 transition-all text-base font-medium shadow-sm">
                                😷 كمامة N95 أو ما يعادلها
                            </button>
                            <button onclick="togglePPE(this, 4, 'gown')" class="check-item w-full text-right p-4 border-2 border-gray-200 rounded-xl relative hover:border-blue-300 transition-all text-base font-medium shadow-sm">
                                🥼 مريول واقٍ (Gown)
                            </button>
                            <button onclick="togglePPE(this, 4, 'gloves')" class="check-item w-full text-right p-4 border-2 border-gray-200 rounded-xl relative hover:border-blue-300 transition-all text-base font-medium shadow-sm">
                                🧤 قفازات مزدوجة (Double Gloves)
                            </button>
                        </div>
                        <p id="step4-msg" class="text-green-600 text-base mt-5 font-bold hidden flex items-center gap-2">
                            <span>✅</span> ممتاز! أنت الآن محمي بشكل كامل
                        </p>
                    </div>
                    <div class="md:w-1/2 relative h-72 md:h-auto bg-gradient-to-br from-blue-50 to-cyan-50 flex items-center justify-center p-8">
                        <img src="https://image.qwenlm.ai/public_source/a19eb0bf-f4ce-4bc1-9193-96bbe9311fcb/1be0ce8e6-b9e9-4dbe-a07a-2ab89dcd54b0.png" alt="Pharmacist PPE" class="max-h-80 object-contain drop-shadow-xl">
                    </div>
                </div>
            </div>
        </div>

        <!-- Step 5: Hand Washing Interactive -->
        <div id="step-5" class="step-container">
            <div class="glass-effect rounded-3xl shadow-2xl overflow-hidden border border-white/50">
                <div class="md:flex">
                    <div class="md:w-1/2 p-6 md:p-10 order-2 md:order-1">
                        <h2 class="text-3xl font-bold text-gray-800 mb-4">الخطوة 5: غسل اليدين وتعقيم الخزانة</h2>
                        <p class="text-gray-600 mb-6 leading-relaxed text-lg">
                            يجب غسل اليدين جيداً قبل الدخول إلى غرفة التحضير، ثم تنظيف خزانة السلامة البيولوجية.
                        </p>
                        
                        <!-- Hand Washing Interactive Animation -->
                        <div class="bg-gradient-to-br from-blue-50 to-cyan-50 rounded-2xl p-6 mb-6 border border-blue-200">
                            <p class="text-center text-gray-700 font-semibold mb-4">👐 اضغط على الزر لغسل اليدين (20 ثانية)</p>
                            <div class="hand-wash-container relative">
                                <svg viewBox="0 0 300 300" class="w-full h-full">
                                    <!-- Water Faucet -->
                                    <rect x="135" y="20" width="30" height="40" fill="#9ca3af" stroke="#6b7280" stroke-width="2"/>
                                    <rect x="125" y="60" width="50" height="15" fill="#6b7280" stroke="#4b5563" stroke-width="2"/>
                                    <path d="M140 75 L140 100" stroke="#3b82f6" stroke-width="4" stroke-linecap="round" class="water-stream" id="water-stream" style="opacity: 0;"/>
                                    
                                    <!-- Water Drops -->
                                    <g id="water-drops" style="opacity: 0;">
                                        <circle class="water-drop" cx="130" cy="110" style="animation-delay: 0s;"/>
                                        <circle class="water-drop" cx="140" cy="110" style="animation-delay: 0.2s;"/>
                                        <circle class="water-drop" cx="150" cy="110" style="animation-delay: 0.4s;"/>
                                        <circle class="water-drop" cx="135" cy="115" style="animation-delay: 0.1s;"/>
                                        <circle class="water-drop" cx="145" cy="115" style="animation-delay: 0.3s;"/>
                                    </g>
                                    
                                    <!-- Hands -->
                                    <g class="hand-icon" id="left-hand" style="opacity: 0;">
                                        <ellipse cx="110" cy="200" rx="35" ry="50" fill="#fca5a5" stroke="#f87171" stroke-width="2"/>
                                        <ellipse cx="95" cy="220" rx="12" ry="25" fill="#fca5a5" stroke="#f87171" stroke-width="2"/>
                                        <ellipse cx="110" cy="225" rx="12" ry="25" fill="#fca5a5" stroke="#f87171" stroke-width="2"/>
                                        <ellipse cx="125" cy="220" rx="12" ry="25" fill="#fca5a5" stroke="#f87171" stroke-width="2"/>
                                    </g>
                                    <g class="hand-icon" id="right-hand" style="opacity: 0;">
                                        <ellipse cx="190" cy="200" rx="35" ry="50" fill="#fca5a5" stroke="#f87171" stroke-width="2"/>
                                        <ellipse cx="175" cy="220" rx="12" ry="25" fill="#fca5a5" stroke="#f87171" stroke-width="2"/>
                                        <ellipse cx="190" cy="225" rx="12" ry="25" fill="#fca5a5" stroke="#f87171" stroke-width="2"/>
                                        <ellipse cx="205" cy="220" rx="12" ry="25" fill="#fca5a5" stroke="#f87171" stroke-width="2"/>
                                    </g>
                                    
                                    <!-- Soap Bubbles -->
                                    <g id="soap-bubbles" style="opacity: 0;">
                                        <circle class="soap-bubble" cx="130" cy="180" r="8" fill="white"/>
                                        <circle class="soap-bubble" cx="150" cy="190" r="6" fill="white"/>
                                        <circle class="soap-bubble" cx="140" cy="210" r="10" fill="white"/>
                                        <circle class="soap-bubble" cx="160" cy="200" r="7" fill="white"/>
                                        <circle class="soap-bubble" cx="145" cy="175" r="5" fill="white"/>
                                    </g>
                                    
                                    <!-- Sink -->
                                    <ellipse cx="150" cy="260" rx="80" ry="30" fill="#e5e7eb" stroke="#9ca3af" stroke-width="2"/>
                                    <path d="M70 260 Q150 280 230 260" fill="none" stroke="#9ca3af" stroke-width="2"/>
                                </svg>
                            </div>
                            
                            <div class="text-center mt-4">
                                <div class="inline-flex items-center gap-2 bg-white px-4 py-2 rounded-xl shadow">
                                    <span class="text-gray-600">الوقت المتبقي:</span>
                                    <span id="wash-timer" class="text-2xl font-bold text-blue-600">20</span>
                                    <span class="text-gray-600">ثانية</span>
                                </div>
                            </div>
                            
                            <button onclick="startHandWash()" id="wash-btn" class="w-full mt-4 py-4 bg-gradient-to-r from-blue-500 to-cyan-500 text-white rounded-xl font-bold text-lg shadow-lg interactive-btn">
                                🧼 ابدأ غسل اليدين
                            </button>
                            <p id="wash-complete-msg" class="text-center text-green-600 font-bold mt-3 hidden">✅ تم غسل اليدين بنجاح!</p>
                        </div>

                        <button onclick="cleanHood()" id="clean-btn" disabled class="w-full py-5 bg-gradient-to-r from-gray-100 to-gray-200 text-gray-600 rounded-2xl font-bold border-2 border-dashed border-gray-300 hover:from-blue-50 hover:to-indigo-50 hover:border-blue-400 hover:text-blue-600 transition-all interactive-btn text-lg shadow-lg disabled:opacity-50">
                            🧽 اضغط لتنظيف الخزانة وتعقيم القوارير
                        </button>
                        <p id="clean-msg" class="text-center text-green-600 font-bold mt-3 hidden">✨ تم التعقيم بنجاح! البيئة جاهزة للتحضير</p>
                    </div>
                    <div class="md:w-1/2 relative h-72 md:h-auto order-1 md:order-2 bg-gradient-to-br from-blue-50 to-cyan-50 flex items-center justify-center p-8">
                        <div class="text-center">
                            <div class="w-40 h-40 mx-auto mb-6 relative">
                                <div class="absolute inset-0 bg-blue-400/20 rounded-full pulse-animation"></div>
                                <svg class="w-40 h-40 mx-auto text-blue-500 relative z-10" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M19.428 15.428a2 2 0 00-1.022-.547l-2.384-.477a6 6 0 00-3.86.517l-.318.158a6 6 0 01-3.86.517L6.05 15.21a2 2 0 00-1.806.547M8 4h8l-1 1v5.172a2 2 0 00.586 1.414l5 5c1.26 1.26.367 3.414-1.415 3.414H4.828c-1.782 0-2.674-2.154-1.414-3.414l5-5A2 2 0 009 10.172V5L8 4z"></path>
                                </svg>
                            </div>
                            <p class="text-gray-700 font-bold text-xl mb-2">خزانة السلامة البيولوجية Class II</p>
                            <p class="text-sm text-gray-500 font-medium">Biosafety Cabinet</p>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <!-- Step 6: Vial Cleaning -->
        <div id="step-6" class="step-container">
            <div class="glass-effect rounded-3xl shadow-2xl p-6 md:p-10 border border-white/50">
                <div class="text-center mb-8">
                    <div class="inline-flex items-center justify-center w-16 h-16 bg-gradient-to-br from-amber-500 to-orange-600 rounded-2xl shadow-lg mb-4 floating">
                        <span class="text-3xl">🧽</span>
                    </div>
                    <h2 class="text-3xl font-bold text-gray-800 mb-3">الخطوة 6: مسح قارورة الدواء</h2>
                    <p class="text-gray-500 text-lg">امسح غطاء القارورة بالكحول 70% قبل الوخز</p>
                </div>

                <div class="bg-gradient-to-r from-amber-50 to-orange-50 border-r-4 border-amber-500 p-5 rounded-2xl mb-8 shadow-lg">
                    <div class="flex items-start gap-3">
                        <span class="text-2xl">💡</span>
                        <div>
                            <h4 class="font-bold text-amber-800 mb-2">لماذا نمسح القارورة؟</h4>
                            <p class="text-sm text-amber-700 leading-relaxed">
                                مسح غطاء القارورة بالكحول يزيل أي ملوثات أو جزيئات قد تدخل إلى الدواء عند الوخز. هذه خطوة حاسمة للحفاظ على التعقيم ومنع التلوث الميكروبي.
                            </p>
                        </div>
                    </div>
                </div>

                <div class="flex flex-col items-center">
                    <!-- Vial Cleaning Animation -->
                    <div class="syringe-container bg-gradient-to-b from-blue-50 to-white rounded-3xl border-2 border-blue-200 p-6 mb-8 shadow-2xl">
                        <!-- Vial -->
                        <div class="vial">
                            <div class="vial-cap" id="vial-cap-clean"></div>
                            <div class="vial-body">
                                <div class="vial-liquid" style="height: 70%;"></div>
                                <div class="vial-label">
                                    <strong id="vial-drug-name-clean">Cisplatin</strong><br>
                                    <span id="vial-concentration-clean">1 mg/mL</span><br>
                                    <span id="vial-volume-clean">50 mL</span>
                                </div>
                            </div>
                        </div>
                        
                        <!-- Alcohol Swab -->
                        <div id="alcohol-swab" class="absolute left-1/2 transform -translate-x-1/2 transition-all duration-500" style="bottom: 150px; opacity: 0;">
                            <svg width="80" height="40" viewBox="0 0 80 40">
                                <rect x="10" y="15" width="60" height="10" rx="5" fill="#60a5fa" stroke="#2563eb" stroke-width="2"/>
                                <rect x="5" y="12" width="10" height="16" rx="2" fill="#f3f4f6" stroke="#9ca3af" stroke-width="2"/>
                                <text x="40" y="23" text-anchor="middle" font-size="8" fill="white" font-weight="bold">70% Alcohol</text>
                            </svg>
                        </div>
                        
                        <!-- Clean Sparkles -->
                        <div id="clean-sparkles" class="absolute inset-0 pointer-events-none"></div>
                    </div>

                    <!-- Controls -->
                    <div class="text-center space-y-5 w-full max-w-md">
                        <button onclick="cleanVial()" id="clean-vial-btn" class="w-full px-8 py-4 bg-gradient-to-r from-amber-500 to-orange-600 text-white rounded-2xl font-bold text-lg shadow-xl interactive-btn">
                            🧽 امسح غطاء القارورة بالكحول
                        </button>
                        
                        <p id="vial-clean-msg" class="text-green-600 font-bold text-lg hidden flex items-center justify-center gap-2">
                            <span>✅</span> تم تعقيم القارورة بنجاح!
                        </p>
                        
                        <button onclick="proceedToAirInject()" id="air-inject-proceed-btn" disabled class="w-full px-8 py-4 bg-gradient-to-r from-green-500 to-emerald-600 text-white rounded-2xl font-bold text-lg shadow-xl interactive-btn disabled:opacity-50 disabled:cursor-not-allowed hidden">
                            ➡️ الانتقال لحقن الهواء
                        </button>
                    </div>
                </div>
            </div>
        </div>

        <!-- Step 7: Inject Air into Vial -->
        <div id="step-7" class="step-container">
            <div class="glass-effect rounded-3xl shadow-2xl p-6 md:p-10 border border-white/50">
                <div class="text-center mb-8">
                    <div class="inline-flex items-center justify-center w-16 h-16 bg-gradient-to-br from-cyan-500 to-blue-600 rounded-2xl shadow-lg mb-4 floating">
                        <span class="text-3xl">💨</span>
                    </div>
                    <h2 class="text-3xl font-bold text-gray-800 mb-3">الخطوة 7: حقن الهواء في القارورة</h2>
                    <p class="text-gray-500 text-lg">حقن كمية من الهواء تساوي حجم الجرعة المطلوبة لتسهيل السحب</p>
                </div>

                <div class="bg-gradient-to-r from-amber-50 to-orange-50 border-r-4 border-amber-500 p-5 rounded-2xl mb-8 shadow-lg">
                    <div class="flex items-start gap-3">
                        <span class="text-2xl">💡</span>
                        <div>
                            <h4 class="font-bold text-amber-800 mb-2">لماذا نحقق الهواء أولاً؟</h4>
                            <p class="text-sm text-amber-700 leading-relaxed">
                                حقن الهواء يخلق ضغطاً إيجابياً داخل القارورة المغلقة، مما يسهل سحب الدواء بدقة وبدون تكون فراغ يعيق السحب. هذه خطوة أساسية في تقنية التحضير العقيم.
                            </p>
                        </div>
                    </div>
                </div>

                <div class="flex flex-col items-center">
                    <!-- Enhanced Syringe and Vial Interactive Area -->
                    <div class="syringe-container bg-gradient-to-b from-blue-50 to-white rounded-3xl border-2 border-blue-200 p-6 mb-8 shadow-2xl">
                        <!-- Syringe -->
                        <div class="syringe-barrel">
                            <div class="liquid-in-syringe" id="syringe-liquid"></div>
                            <!-- Air bubbles container -->
                            <div id="air-bubbles-container" class="absolute inset-0 pointer-events-none"></div>
                            <div class="measurement-lines">
                                <div class="measurement-line major" style="top: 10%"></div>
                                <div class="measurement-line" style="top: 20%"></div>
                                <div class="measurement-line major" style="top: 30%"></div>
                                <div class="measurement-line" style="top: 40%"></div>
                                <div class="measurement-line major" style="top: 50%"></div>
                                <div class="measurement-line" style="top: 60%"></div>
                                <div class="measurement-line major" style="top: 70%"></div>
                                <div class="measurement-line" style="top: 80%"></div>
                                <div class="measurement-line major" style="top: 90%"></div>
                            </div>
                            <div class="syringe-plunger" id="plunger" onclick="injectAir()">
                                <div class="syringe-plunger-top"></div>
                                <div class="syringe-plunger-head"></div>
                            </div>
                            <div class="syringe-needle-hub"></div>
                            <div class="syringe-needle"></div>
                        </div>
                        
                        <!-- Vial -->
                        <div class="vial">
                            <div class="vial-cap"></div>
                            <div class="vial-body">
                                <div class="vial-liquid" id="vial-liquid"></div>
                                <!-- Air bubbles in vial -->
                                <div id="vial-bubbles-container" class="absolute inset-0 pointer-events-none"></div>
                                <div class="vial-label" id="vial-label-content">
                                    <strong id="vial-drug-name">Cisplatin</strong><br>
                                    <span id="vial-concentration">1 mg/mL</span><br>
                                    <span id="vial-volume">50 mL</span>
                                </div>
                            </div>
                        </div>
                    </div>

                    <!-- Controls -->
                    <div class="text-center space-y-5 w-full max-w-md">
                        <div class="flex items-center justify-center gap-4 flex-wrap">
                            <div class="bg-gradient-to-br from-blue-50 to-blue-100 px-5 py-3 rounded-2xl border border-blue-200 shadow-lg">
                                <span class="text-sm text-blue-800 font-medium">الهواء المطلوب: </span>
                                <strong class="text-blue-700 text-lg" id="required-air">140.25</strong>
                                <span class="text-blue-600">mL</span>
                            </div>
                            <div class="bg-gradient-to-br from-cyan-50 to-cyan-100 px-5 py-3 rounded-2xl border border-cyan-200 shadow-lg">
                                <span class="text-sm text-cyan-800 font-medium">الهواء المحقون: </span>
                                <strong class="text-cyan-700 text-lg" id="air-injected">0</strong>
                                <span class="text-cyan-600">mL</span>
                            </div>
                        </div>
                        
                        <button onclick="injectAir()" id="inject-air-btn" class="w-full px-8 py-4 bg-gradient-to-r from-cyan-500 to-blue-600 text-white rounded-2xl font-bold text-lg shadow-xl interactive-btn disabled:opacity-50">
                            💨 اضغط لحقن الهواء (اضغط متكرر)
                        </button>
                        
                        <p id="air-msg" class="text-green-600 font-bold text-lg hidden flex items-center justify-center gap-2">
                            <span>✅</span> تم حقن الهواء بنجاح! الآن يمكنك سحب الدواء
                        </p>
                        
                        <button onclick="proceedToDraw()" id="draw-proceed-btn" disabled class="w-full px-8 py-4 bg-gradient-to-r from-green-500 to-emerald-600 text-white rounded-2xl font-bold text-lg shadow-xl interactive-btn disabled:opacity-50 disabled:cursor-not-allowed hidden">
                            ➡️ الانتقال لسحب الدواء
                        </button>
                    </div>
                </div>
            </div>
        </div>

        <!-- Step 8: Drawing Drug -->
        <div id="step-8" class="step-container">
            <div class="glass-effect rounded-3xl shadow-2xl p-6 md:p-10 border border-white/50">
                <div class="text-center mb-8">
                    <div class="inline-flex items-center justify-center w-16 h-16 bg-gradient-to-br from-indigo-500 to-blue-600 rounded-2xl shadow-lg mb-4 floating">
                        <span class="text-3xl">💉</span>
                    </div>
                    <h2 class="text-3xl font-bold text-gray-800 mb-3">الخطوة 8: سحب الدواء من القارورة</h2>
                    <p class="text-gray-500 text-lg">اقلب القارورة واسحب الجرعة المطلوبة بدقة</p>
                </div>

                <div class="flex flex-col items-center">
                    <!-- Enhanced Syringe and Vial Interactive Area -->
                    <div class="syringe-container bg-gradient-to-b from-blue-50 to-white rounded-3xl border-2 border-blue-200 p-6 mb-8 shadow-2xl">
                        <!-- Syringe -->
                        <div class="syringe-barrel">
                            <div class="liquid-in-syringe" id="syringe-liquid-draw"></div>
                            <div class="measurement-lines">
                                <div class="measurement-line major" style="top: 10%"></div>
                                <div class="measurement-line" style="top: 20%"></div>
                                <div class="measurement-line major" style="top: 30%"></div>
                                <div class="measurement-line" style="top: 40%"></div>
                                <div class="measurement-line major" style="top: 50%"></div>
                                <div class="measurement-line" style="top: 60%"></div>
                                <div class="measurement-line major" style="top: 70%"></div>
                                <div class="measurement-line" style="top: 80%"></div>
                                <div class="measurement-line major" style="top: 90%"></div>
                            </div>
                            <div class="syringe-plunger" id="plunger-draw" onclick="drawDrug()">
                                <div class="syringe-plunger-top"></div>
                                <div class="syringe-plunger-head"></div>
                            </div>
                            <div class="syringe-needle-hub"></div>
                            <div class="syringe-needle"></div>
                        </div>
                        
                        <!-- Vial (inverted visually) -->
                        <div class="vial" style="bottom: 280px;">
                            <div class="vial-cap"></div>
                            <div class="vial-body">
                                <div class="vial-liquid" id="vial-liquid-draw"></div>
                                <div class="vial-label" id="vial-label-draw">
                                    <strong id="vial-drug-name-draw">Cisplatin</strong><br>
                                    <span id="vial-concentration-draw">1 mg/mL</span><br>
                                    <span id="vial-volume-draw">50 mL</span>
                                </div>
                            </div>
                        </div>
                    </div>

                    <!-- Controls -->
                    <div class="text-center space-y-5 w-full max-w-md">
                        <div class="flex items-center justify-center gap-4 flex-wrap">
                            <div class="bg-gradient-to-br from-yellow-50 to-yellow-100 px-5 py-3 rounded-2xl border border-yellow-200 shadow-lg">
                                <span class="text-sm text-yellow-800 font-medium">الدواء في القارورة: </span>
                                <strong class="text-yellow-700 text-lg" id="vial-amount-draw">140.25</strong>
                                <span class="text-yellow-600">mL</span>
                            </div>
                            <div class="bg-gradient-to-br from-blue-50 to-blue-100 px-5 py-3 rounded-2xl border border-blue-200 shadow-lg">
                                <span class="text-sm text-blue-800 font-medium">في السرنجة: </span>
                                <strong class="text-blue-700 text-lg" id="syringe-amount-draw">0</strong>
                                <span class="text-blue-600">mL</span>
                            </div>
                        </div>
                        
                        <button onclick="drawDrug()" id="draw-btn" class="w-full px-8 py-4 btn-primary text-white rounded-2xl font-bold text-lg shadow-xl interactive-btn disabled:opacity-50">
                            💉 اسحب الدواء (اضغط متكرر)
                        </button>
                        
                        <p id="draw-msg" class="text-green-600 font-bold text-lg hidden flex items-center justify-center gap-2">
                            <span>✅</span> تم سحب الجرعة المطلوبة بنجاح!
                        </p>
                        
                        <button onclick="proceedToInject()" id="inject-proceed-btn" disabled class="w-full px-8 py-4 bg-gradient-to-r from-green-500 to-emerald-600 text-white rounded-2xl font-bold text-lg shadow-xl interactive-btn disabled:opacity-50 disabled:cursor-not-allowed hidden">
                            ➡️ الانتقال للحقن في الكيس
                        </button>
                    </div>
                </div>
            </div>
        </div>

        <!-- Step 9: Injecting into IV Bag -->
        <div id="step-9" class="step-container">
            <div class="glass-effect rounded-3xl shadow-2xl p-6 md:p-10 border border-white/50">
                <div class="text-center mb-8">
                    <div class="inline-flex items-center justify-center w-16 h-16 bg-gradient-to-br from-red-500 to-pink-600 rounded-2xl shadow-lg mb-4 floating">
                        <span class="text-3xl">💧</span>
                    </div>
                    <h2 class="text-3xl font-bold text-gray-800 mb-3">الخطوة 9: حقن الدواء في الكيس الوريدي</h2>
                    <p class="text-gray-500 text-lg">اضغط لحقن الدواء من السرنجة إلى كيس المحلول</p>
                </div>

                <div class="flex flex-col items-center">
                    <!-- Enhanced IV Bag and Syringe -->
                    <div class="relative w-full max-w-md h-96 md:h-[450px] bg-gradient-to-b from-blue-50 to-white rounded-3xl border-2 border-blue-200 p-6 mb-8 flex items-end justify-center shadow-2xl">
                        <!-- IV Stand Hook -->
                        <div class="absolute top-6 left-1/2 transform -translate-x-1/2">
                            <svg class="w-24 md:w-28 h-16 md:h-20 text-gray-400" fill="none" stroke="currentColor" viewBox="0 0 100 60">
                                <defs>
                                    <linearGradient id="hookGrad" x1="0%" y1="0%" x2="100%" y2="0%">
                                        <stop offset="0%" style="stop-color:#9ca3af"/>
                                        <stop offset="50%" style="stop-color:#d1d5db"/>
                                        <stop offset="100%" style="stop-color:#9ca3af"/>
                                    </linearGradient>
                                </defs>
                                <path stroke="url(#hookGrad)" stroke-width="5" d="M50 0 L50 40 M50 40 Q50 55 35 55 M50 40 Q50 55 65 55" stroke-linecap="round"/>
                            </svg>
                        </div>
                        
                        <!-- IV Bag - Clickable for mixing -->
                        <div class="iv-bag relative z-10" id="iv-bag-element" onclick="handleMixClick()">
                            <div class="iv-bag-body">
                                <div class="iv-liquid" id="iv-liquid"></div>
                                <div class="absolute top-5 left-1/2 transform -translate-x-1/2 bg-white px-3 md:px-4 py-2 rounded-xl text-xs font-bold text-gray-700 border-2 border-gray-200 text-center shadow-lg">
                                    <span id="iv-solution-name">NS 0.9%</span><br>
                                    <span id="iv-solution-volume">500 mL</span>
                                </div>
                                <!-- Enhanced Bubbles/Swirl animation container -->
                                <div id="bubbles-container" class="absolute inset-0 pointer-events-none"></div>
                            </div>
                            <div class="iv-port" id="iv-port"></div>
                            <!-- Mix counter overlay -->
                            <div id="mix-counter-overlay" class="hidden absolute inset-0 bg-black/70 rounded-2xl flex items-center justify-center backdrop-blur-sm">
                                <div class="text-white text-center">
                                    <div class="mix-counter" id="mix-count-display">0</div>
                                    <div class="text-sm font-medium">قلبة</div>
                                </div>
                            </div>
                        </div>
                        
                        <!-- Enhanced Syringe positioned at port -->
                        <div class="absolute bottom-20 md:bottom-24 left-1/2 transform -translate-x-1/2">
                            <svg class="w-20 md:w-24 h-36 md:h-40" viewBox="0 0 60 120">
                                <!-- Gradients -->
                                <defs>
                                    <linearGradient id="barrelGrad" x1="0%" y1="0%" x2="100%" y2="0%">
                                        <stop offset="0%" style="stop-color:#e0e7ff"/>
                                        <stop offset="50%" style="stop-color:#ffffff"/>
                                        <stop offset="100%" style="stop-color:#e0e7ff"/>
                                    </linearGradient>
                                    <linearGradient id="plungerGrad" x1="0%" y1="0%" x2="100%" y2="0%">
                                        <stop offset="0%" style="stop-color:#3b82f6"/>
                                        <stop offset="100%" style="stop-color:#1d4ed8"/>
                                    </linearGradient>
                                    <linearGradient id="needleGrad" x1="0%" y1="0%" x2="100%" y2="0%">
                                        <stop offset="0%" style="stop-color:#6b7280"/>
                                        <stop offset="50%" style="stop-color:#e5e7eb"/>
                                        <stop offset="100%" style="stop-color:#6b7280"/>
                                    </linearGradient>
                                </defs>
                                <!-- Syringe barrel -->
                                <rect x="15" y="20" width="30" height="70" fill="url(#barrelGrad)" stroke="#6366f1" stroke-width="2.5" rx="4"/>
                                <!-- Liquid in syringe -->
                                <rect x="17" y="70" width="26" height="18" fill="#f59e0b" id="syringe-inject-liquid"/>
                                <!-- Plunger -->
                                <rect x="20" y="30" width="20" height="50" fill="url(#plungerGrad)" id="inject-plunger"/>
                                <rect x="10" y="85" width="40" height="10" fill="#1d4ed8" rx="3"/>
                                <!-- Needle hub -->
                                <rect x="25" y="90" width="10" height="18" fill="#06b6d4"/>
                                <!-- Needle -->
                                <rect x="28" y="108" width="4" height="12" fill="url(#needleGrad)"/>
                            </svg>
                        </div>
                    </div>

                    <!-- Controls -->
                    <div class="text-center space-y-5 w-full max-w-md">
                        <div class="flex items-center justify-center gap-4 flex-wrap">
                            <div class="bg-gradient-to-br from-blue-50 to-blue-100 px-5 py-3 rounded-2xl border border-blue-200 shadow-lg">
                                <span class="text-sm text-blue-800 font-medium">حجم الكيس: </span>
                                <strong class="text-blue-700 text-lg" id="iv-volume-display">500</strong>
                                <span class="text-blue-600">mL</span>
                            </div>
                            <div class="bg-gradient-to-br from-yellow-50 to-yellow-100 px-5 py-3 rounded-2xl border border-yellow-200 shadow-lg">
                                <span class="text-sm text-yellow-800 font-medium">الدواء المضاف: </span>
                                <strong class="text-yellow-700 text-lg" id="drug-added">0</strong>
                                <span class="text-yellow-600">mL</span>
                            </div>
                        </div>
                        
                        <button onclick="injectIntoBag()" id="inject-btn" class="w-full px-8 py-4 bg-gradient-to-r from-red-500 to-red-600 text-white rounded-2xl font-bold text-lg shadow-xl interactive-btn">
                            💉 حقن الدواء في الكيس
                        </button>
                        
                        <p id="inject-msg" class="text-green-600 font-bold text-lg hidden flex items-center justify-center gap-2">
                            <span>✅</span> تم حقن الدواء بنجاح! الآن قم بخلط الكيس
                        </p>
                        
                        <!-- Enhanced Mixing Instructions -->
                        <div id="mix-instruction" class="hidden bg-gradient-to-br from-purple-50 to-pink-50 border-2 border-purple-300 rounded-2xl p-6 mt-4 shadow-xl">
                            <p class="text-sm text-purple-800 font-bold mb-3 flex items-center gap-2 text-lg">
                                <span>📌</span> تعليمات الخلط:
                            </p>
                            <p class="text-sm text-purple-700 mb-4 leading-relaxed">اضغط على الكيس الوريدي أو الزر 10 مرات لخلط الدواء بشكل صحيح</p>
                            
                            <!-- Progress bar for mixing -->
                            <div class="w-full bg-gray-200 rounded-full h-6 mb-3 shadow-inner overflow-hidden">
                                <div id="mix-progress-bar" class="h-6 rounded-full mix-progress shadow-lg" style="width: 0%"></div>
                            </div>
                            <p class="text-sm text-purple-700 font-bold">التقدم: <span id="mix-progress-text" class="text-purple-600 text-lg">0</span> / 10 قلبات</p>
                            
                            <!-- Mix button as alternative -->
                            <button onclick="handleMixClick()" id="mix-btn-alt" class="mt-4 w-full px-6 py-4 bg-gradient-to-r from-purple-600 to-purple-700 text-white rounded-2xl font-bold text-lg shadow-xl interactive-btn click-hint">
                                🔄 اضغط هنا لخلط الكيس (10 مرات)
                            </button>
                        </div>
                        
                        <p id="mix-msg" class="text-green-600 font-bold text-xl hidden flex items-center justify-center gap-2">
                            <span>✅</span> تم الخلط بنجاح! الدواء موزع بشكل متجانس
                        </p>
                    </div>
                </div>
            </div>
        </div>

        <!-- Step 10: Disposal & Labeling with Centered Bin -->
        <div id="step-10" class="step-container">
            <div class="glass-effect rounded-3xl shadow-2xl overflow-hidden border border-white/50">
                <div class="md:flex">
                    <div class="md:w-1/2 p-6 md:p-10">
                        <h2 class="text-3xl font-bold text-gray-800 mb-4">الخطوة 10: التخلص الآمن والتسمية</h2>
                        <p class="text-gray-600 mb-6 leading-relaxed text-lg">
                            تخلص من جميع المواد الملوثة في الحاويات المخصصة وأضف الملصق التحذيري على الكيس.
                        </p>
                        
                        <!-- Disposal Animation Display - Centered Bin -->
                        <div class="bg-gradient-to-br from-red-50 to-orange-50 rounded-2xl p-6 mb-6 border border-red-200">
                            <p class="text-center text-gray-700 font-semibold mb-4">🗑️ اضغط على كل عنصر للتخلص منه</p>
                            <div class="disposal-animation-container">
                                <svg viewBox="0 0 350 350">
                                    <!-- Disposal Bin - CENTERED and LARGER -->
                                    <g class="disposal-bin">
                                        <!-- Shadow -->
                                        <ellipse cx="175" cy="325" rx="90" ry="15" fill="#000000" opacity="0.3"/>
                                        <!-- Bin Body - Larger -->
                                        <rect x="115" y="180" width="120" height="140" rx="10" fill="#fbbf24" stroke="#d97706" stroke-width="5"/>
                                        <!-- Bin Gradient Overlay -->
                                        <rect x="115" y="180" width="120" height="140" rx="10" fill="url(#binGrad)" opacity="0.3"/>
                                        <defs>
                                            <linearGradient id="binGrad" x1="0%" y1="0%" x2="100%" y2="100%">
                                                <stop offset="0%" style="stop-color:#ffffff;stop-opacity:0.3"/>
                                                <stop offset="100%" style="stop-color:#000000;stop-opacity:0.1"/>
                                            </linearGradient>
                                        </defs>
                                        <!-- Biohazard Symbol - Larger -->
                                        <circle cx="175" cy="240" r="40" fill="#fef3c7" stroke="#d97706" stroke-width="4"/>
                                        <circle cx="175" cy="240" r="15" fill="#d97706"/>
                                        <circle cx="175" cy="205" r="17" fill="#d97706"/>
                                        <circle cx="175" cy="275" r="17" fill="#d97706"/>
                                        <circle cx="145" cy="240" r="17" fill="#d97706"/>
                                        <circle cx="205" cy="240" r="17" fill="#d97706"/>
                                        <circle cx="153" cy="215" r="13" fill="#d97706"/>
                                        <circle cx="197" cy="215" r="13" fill="#d97706"/>
                                        <circle cx="153" cy="265" r="13" fill="#d97706"/>
                                        <circle cx="197" cy="265" r="13" fill="#d97706"/>
                                        <!-- Bin Lid - Larger -->
                                        <rect x="110" y="160" width="130" height="25" rx="6" fill="#f59e0b" stroke="#d97706" stroke-width="4"/>
                                        <rect x="155" y="140" width="40" height="22" rx="5" fill="#f59e0b" stroke="#d97706" stroke-width="4"/>
                                        <!-- Warning Label - Larger -->
                                        <rect x="135" y="285" width="80" height="25" rx="5" fill="#fef3c7" stroke="#d97706" stroke-width="2"/>
                                        <text x="175" y="302" text-anchor="middle" font-size="11" fill="#d97706" font-weight="bold">BIOHAZARD</text>
                                    </g>
                                    
                                    <!-- Disposal Items - Arranged Around Center -->
                                    <g class="disposal-item disposal-needle" id="disposal-needle">
                                        <!-- Needle Body -->
                                        <rect x="25" y="50" width="55" height="14" rx="5" fill="#9ca3af" stroke="#6b7280" stroke-width="3"/>
                                        <!-- Needle Point -->
                                        <polygon points="80,57 100,57 90,50 90,64" fill="#6b7280"/>
                                        <!-- Needle Hub -->
                                        <rect x="15" y="46" width="16" height="22" rx="4" fill="#06b6d4" stroke="#0891b2" stroke-width="3"/>
                                        <!-- Shadow -->
                                        <ellipse cx="55" cy="78" rx="35" ry="8" fill="#000000" opacity="0.2"/>
                                    </g>
                                    
                                    <g class="disposal-item disposal-syringe" id="disposal-syringe">
                                        <!-- Barrel -->
                                        <rect x="145" y="45" width="70" height="24" rx="5" fill="#e0e7ff" stroke="#6366f1" stroke-width="3"/>
                                        <!-- Plunger -->
                                        <rect x="165" y="48" width="38" height="18" fill="#3b82f6"/>
                                        <!-- Flange -->
                                        <rect x="140" y="49" width="14" height="16" fill="#1d4ed8"/>
                                        <!-- Hub -->
                                        <rect x="215" y="50" width="18" height="14" fill="#06b6d4"/>
                                        <!-- Needle -->
                                        <rect x="233" y="52" width="18" height="8" fill="#9ca3af"/>
                                        <!-- Shadow -->
                                        <ellipse cx="180" cy="78" rx="45" ry="9" fill="#000000" opacity="0.2"/>
                                    </g>
                                    
                                    <g class="disposal-item disposal-vial" id="disposal-vial">
                                        <!-- Vial Body -->
                                        <rect x="245" y="45" width="50" height="65" rx="8" fill="rgba(255,255,255,0.7)" stroke="#9ca3af" stroke-width="3"/>
                                        <!-- Cap -->
                                        <rect x="240" y="38" width="60" height="15" rx="5" fill="#374151"/>
                                        <!-- Liquid -->
                                        <rect x="252" y="65" width="36" height="38" fill="#f59e0b" opacity="0.7" rx="4"/>
                                        <!-- Label -->
                                        <rect x="254" y="48" width="34" height="17" fill="white" opacity="0.95" rx="3"/>
                                        <text x="271" y="60" text-anchor="middle" font-size="8" fill="#374151" font-weight="bold">RX</text>
                                        <!-- Shadow -->
                                        <ellipse cx="270" cy="118" rx="30" ry="9" fill="#000000" opacity="0.2"/>
                                    </g>
                                    
                                    <g class="disposal-item disposal-gloves" id="disposal-gloves">
                                        <!-- Left Glove -->
                                        <path d="M45 50 Q30 70 37 95 L58 95 Q73 70 66 50 Q58 35 50 35 Q42 35 45 50" fill="#60a5fa" stroke="#3b82f6" stroke-width="3"/>
                                        <circle cx="42" cy="58" r="6" fill="#3b82f6"/>
                                        <circle cx="37" cy="78" r="5" fill="#3b82f6"/>
                                        <circle cx="50" cy="78" r="5" fill="#3b82f6"/>
                                        <circle cx="60" cy="70" r="5" fill="#3b82f6"/>
                                        <!-- Right Glove -->
                                        <path d="M285 50 Q270 70 277 95 L298 95 Q313 70 306 50 Q298 35 290 35 Q282 35 285 50" fill="#60a5fa" stroke="#3b82f6" stroke-width="3"/>
                                        <circle cx="282" cy="58" r="6" fill="#3b82f6"/>
                                        <circle cx="277" cy="78" r="5" fill="#3b82f6"/>
                                        <circle cx="290" cy="78" r="5" fill="#3b82f6"/>
                                        <circle cx="300" cy="70" r="5" fill="#3b82f6"/>
                                        <!-- Shadow -->
                                        <ellipse cx="175" cy="102" rx="80" ry="12" fill="#000000" opacity="0.2"/>
                                    </g>
                                </svg>
                            </div>
                        </div>
                        
                        <div class="space-y-3 mb-8">
                            <button onclick="disposeItem(this, 'needle')" class="w-full text-right p-4 border-2 border-gray-200 rounded-xl relative hover:border-red-300 transition-all interactive-btn text-base font-medium shadow-sm">
                                🗑️ التخلص من الإبرة في حاوية النفايات الحادة
                            </button>
                            <button onclick="disposeItem(this, 'syringe')" class="w-full text-right p-4 border-2 border-gray-200 rounded-xl relative hover:border-red-300 transition-all interactive-btn text-base font-medium shadow-sm">
                                🗑️ التخلص من السرنجة في النفايات الخطرة
                            </button>
                            <button onclick="disposeItem(this, 'vial')" class="w-full text-right p-4 border-2 border-gray-200 rounded-xl relative hover:border-red-300 transition-all interactive-btn text-base font-medium shadow-sm">
                                🗑️ التخلص من القارورة الفارغة
                            </button>
                            <button onclick="disposeItem(this, 'gloves')" class="w-full text-right p-4 border-2 border-gray-200 rounded-xl relative hover:border-red-300 transition-all interactive-btn text-base font-medium shadow-sm">
                                🗑️ التخلص من القفازات الملوثة
                            </button>
                            <button onclick="labelBag()" id="label-btn" class="w-full text-right p-4 border-2 border-gray-200 rounded-xl relative hover:border-green-300 transition-all interactive-btn text-base font-medium shadow-sm">
                                🏷️ إضافة ملصق التحذير على الكيس
                            </button>
                        </div>

                        <button onclick="finishProcess()" id="finish-btn" disabled class="w-full py-5 btn-primary text-white font-bold text-lg rounded-2xl shadow-2xl interactive-btn disabled:opacity-50 disabled:cursor-not-allowed">
                            ✅ إنهاء العملية وتسليم الدواء
                        </button>
                    </div>
                    <div class="md:w-1/2 relative h-72 md:h-auto bg-gradient-to-br from-gray-100 to-gray-200 flex items-center justify-center p-8">
                        <img src="https://image.qwenlm.ai/public_source/a19eb0bf-f4ce-4bc1-9193-96bbe9311fcb/188554173-8943-407b-95fa-37726846d78d.png" alt="Biohazard Waste Bin" class="max-h-72 object-contain drop-shadow-2xl">
                    </div>
                </div>
            </div>
        </div>

        <!-- Credit Section -->
        <div class="credit-section rounded-3xl shadow-2xl p-8 md:p-12 mt-8">
            <div class="text-center">
                <div class="inline-flex items-center justify-center w-20 h-20 bg-white/20 rounded-full mb-6 mx-auto">
                    <svg class="w-10 h-10 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 6.253v13m0-13C10.832 5.477 9.246 5 7.5 5S4.168 5.477 3 6.253v13C4.168 18.477 5.754 18 7.5 18s3.332.477 4.5 1.253m0-13C13.168 5.477 14.754 5 16.5 5c1.747 0 3.332.477 4.5 1.253v13C19.832 18.477 18.247 18 16.5 18c-1.746 0-3.332.477-4.5 1.253"></path>
                    </svg>
                </div>
                <h2 class="text-3xl font-bold mb-4">تم تطوير هذا المحاكي بواسطة</h2>
                <div class="credit-card rounded-2xl p-8 max-w-2xl mx-auto">
                    <h3 class="text-2xl md:text-3xl font-bold mb-2">د. أحمد زكريا</h3>
                    <p class="text-xl text-white/90 mb-4">Dr. Ahmed Zakaryia</p>
                    <div class="flex flex-col md:flex-row items-center justify-center gap-4 text-white/80">
                        <span class="flex items-center gap-2">
                            <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 21V5a2 2 0 00-2-2H7a2 2 0 00-2 2v16m14 0h2m-2 0h-5m-9 0H3m2 0h5M9 7h1m-1 4h1m4-4h1m-1 4h1m-5 10v-5a1 1 0 011-1h2a1 1 0 011 1v5m-4 0h4"></path>
                            </svg>
                            كلية الصيدلة
                        </span>
                        <span class="hidden md:inline">•</span>
                        <span class="flex items-center gap-2">
                            <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17.657 16.657L13.414 20.9a1.998 1.998 0 01-2.827 0l-4.244-4.243a8 8 0 1111.314 0z"></path>
                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 11a3 3 0 11-6 0 3 3 0 016 0z"></path>
                            </svg>
                            جامعة عين شمس
                        </span>
                    </div>
                    <p class="mt-6 text-white/70 text-sm">
                        محاكي تدريبي احترافي لتطوير مهارات الصيادلة في تحضير أدوية العلاج الكيميائي بأمان ودقة
                    </p>
                </div>
            </div>
        </div>

    </main>

    <!-- Footer Navigation -->
    <footer class="header-glass border-t border-gray-200/50 py-5 px-6 sticky bottom-0 z-50">
        <div class="max-w-7xl mx-auto flex justify-between items-center">
            <button id="prev-btn" onclick="changeStep(-1)" class="px-8 py-3 rounded-2xl border-2 border-gray-300 text-gray-600 font-bold hover:bg-gray-50 disabled:opacity-50 disabled:cursor-not-allowed interactive-btn transition-all" disabled>
                ⬅️ السابق
            </button>
            
            <div class="text-sm text-gray-400 hidden md:block font-medium">
                محاكي تدريبي احترافي للصيادلة
            </div>

            <button id="next-btn" onclick="changeStep(1)" class="px-8 py-3 btn-primary text-white rounded-2xl font-bold shadow-lg disabled:opacity-50 disabled:cursor-not-allowed interactive-btn">
                التالي ➡️
            </button>
        </div>
    </footer>

    <!-- Drug Info Modal -->
    <div id="drug-info-modal" class="fixed inset-0 bg-black/80 z-[70] hidden flex items-center justify-center p-4 backdrop-blur-sm">
        <div class="bg-white rounded-3xl p-8 max-w-2xl w-full max-h-[85vh] overflow-y-auto shadow-2xl">
            <div class="flex justify-between items-center mb-6">
                <h2 class="text-2xl font-bold gradient-text" id="modal-drug-name">معلومات الدواء</h2>
                <button onclick="closeDrugInfo()" class="text-gray-400 hover:text-gray-600 transition p-2 hover:bg-gray-100 rounded-xl">
                    <svg class="w-7 h-7" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"></path></svg>
                </button>
            </div>
            <div id="modal-drug-content" class="modal-content space-y-4">
                <!-- Content will be injected here -->
            </div>
            <button onclick="closeDrugInfo()" class="mt-8 w-full py-4 bg-gradient-to-r from-gray-800 to-gray-900 text-white rounded-2xl font-bold hover:from-gray-900 hover:to-black transition shadow-lg">
                إغلاق
            </button>
        </div>
    </div>

    <!-- Success Modal -->
    <div id="success-modal" class="fixed inset-0 bg-black/80 z-[60] hidden flex items-center justify-center p-4 backdrop-blur-sm">
        <div class="bg-white rounded-3xl p-8 max-w-md w-full text-center transform scale-100 transition-transform glow-success shadow-2xl">
            <div class="w-24 h-24 bg-gradient-to-br from-green-400 to-emerald-500 rounded-full flex items-center justify-center mx-auto mb-6 shadow-xl">
                <svg class="w-12 h-12 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2.5" d="M5 13l4 4L19 7"></path></svg>
            </div>
            <h2 class="text-2xl md:text-3xl font-black text-gray-800 mb-3">🎉 أحسنت يا صيدلي!</h2>
            <p class="text-gray-600 mb-6 text-base leading-relaxed">لقد أكملت عملية تحضير العلاج الكيميائي بنجاح وفقاً للمعايير الطبية والسلامة المطلوبة.</p>
            <div class="bg-gradient-to-br from-blue-50 to-indigo-50 rounded-2xl p-6 mb-6 text-right border border-blue-200 shadow-lg">
                <p class="text-sm text-blue-800 font-bold mb-3">📋 ملخص العملية:</p>
                <ul class="text-sm text-blue-700 space-y-2">
                    <li class="flex items-center gap-2">
                        <span class="w-2 h-2 bg-green-500 rounded-full"></span>
                        الدواء: <span id="summary-drug" class="font-bold">-</span>
                    </li>
                    <li class="flex items-center gap-2">
                        <span class="w-2 h-2 bg-green-500 rounded-full"></span>
                        BSA: <span id="summary-bsa" class="font-bold">-</span> m²
                    </li>
                    <li class="flex items-center gap-2">
                        <span class="w-2 h-2 bg-green-500 rounded-full"></span>
                        الجرعة: <span id="summary-dose" class="font-bold">-</span> mg
                    </li>
                    <li class="flex items-center gap-2">
                        <span class="w-2 h-2 bg-green-500 rounded-full"></span>
                        الحجم: <span id="summary-volume" class="font-bold">-</span> mL
                    </li>
                    <li class="flex items-center gap-2">
                        <span class="w-2 h-2 bg-green-500 rounded-full"></span>
                        جميع خطوات السلامة مكتملة
                    </li>
                </ul>
            </div>
            <button onclick="location.reload()" class="w-full py-4 bg-gradient-to-r from-gray-800 to-gray-900 text-white rounded-2xl font-bold hover:from-gray-900 hover:to-black transition shadow-xl interactive-btn">
                🔄 إعادة التدريب بدواء آخر
            </button>
        </div>
    </div>

    <script>
        let currentStep = 1;
        const totalSteps = 10;
        let stepRequirements = {
            1: false,
            2: false,
            3: false,
            4: 0,
            5: false,
            6: false,
            7: false,
            8: false,
            9: false,
            10: 0
        };
        
        // Drug data
        const drugs = {
            cisplatin: {
                name: 'Cisplatin',
                nameAr: 'سيسبلاتين',
                standardDose: 75,
                concentration: 1,
                solution: 'NS 0.9%',
                solutionVolume: 500,
                vialVolume: 50,
                color: '#f59e0b',
                image: 'https://image.qwenlm.ai/public_source/a19eb0bf-f4ce-4bc1-9193-96bbe9311fcb/16ffb4102-ca38-412c-83d5-62f91f2a0313.png',
                warning: '⚠️ يجب الترطيب الجيد للمريض قبل الإعطاء. مراقبة وظائف الكلى.',
                uses: 'سرطان الرئة، سرطان المثانة، سرطان المبيض، سرطان الخصية، سرطان الرأس والرقبة',
                mechanism: 'يعمل عن طريق تكوين روابط متصالبة مع DNA الخلية السرطانية، مما يمنع انقسام الخلية ويؤدي إلى موتها المبرمج (Apoptosis). ينتمي لمجموعة أدوية Platinum-based.',
                sideEffects: 'الغثيان والقيء الشديد، السمية الكلوية، السمية السمعية، الاعتلال العصبي المحيطي، نقص المغنيسيوم',
                stability: 'مستقر في درجة حرارة الغرفة. يجب حمايته من الضوء. يجب التخلص خلال 24 ساعة.'
            },
            doxorubicin: {
                name: 'Doxorubicin',
                nameAr: 'دوكسوروبيسين',
                standardDose: 60,
                concentration: 2,
                solution: 'NS 0.9%',
                solutionVolume: 250,
                vialVolume: 25,
                color: '#dc2626',
                image: 'https://image.qwenlm.ai/public_source/a19eb0bf-f4ce-4bc1-9193-96bbe9311fcb/196239f19-537c-4cd6-8171-9fd47476283e.png',
                warning: '⚠️ دواء ناسج للأنسجة! تجنب التسرب خارج الوريد. مراقبة وظائف القلب.',
                uses: 'سرطان الثدي، سرطان الدم (Leukemia)، اللمفوما، سرطان الرئة، سرطان المبيض، ساركوما',
                mechanism: 'ينتمي لمجموعة Anthracyclines. يعمل عن طريق التداخل مع إنزيم Topoisomerase II ومنع إعادة ربط سلاسل DNA، كما يولد جذور حرة تسبب تلف DNA. أيضاً يثبط تخليق DNA و RNA.',
                sideEffects: 'تثبيط نخاع العظم، تساقط الشعر، الغثيان، السمية القلبية (Cardiotoxicity)، البول الأحمر (غير ضار)',
                stability: 'يحتاج تبريد (2-8°C). حساس للضوء. يجب حمايته من الضوء المباشر.'
            },
            paclitaxel: {
                name: 'Paclitaxel',
                nameAr: 'باكليتاكسيل',
                standardDose: 175,
                concentration: 6,
                solution: 'NS 0.9% أو D5W',
                solutionVolume: 500,
                vialVolume: 50,
                color: '#7c3aed',
                image: 'https://image.qwenlm.ai/public_source/a19eb0bf-f4ce-4bc1-9193-96bbe9311fcb/18a5b6b6c-79bb-46ed-8d0b-ce124b21489b.png',
                warning: '⚠️ يجب إعطاء بريدنيزولون وديفينهيدرامين قبل الجرعة للوقاية من الحساسية.',
                uses: 'سرطان الثدي، سرطان الرئة، سرطان المبيض، سرطان البنكرياس، سرطان المعدة',
                mechanism: 'ينتمي لمجموعة Taxanes. يعمل عن طريق تثبيت الأنابيب الدقيقة (Microtubules) ومنع تفككها، مما يوقف انقسام الخلية في طور الطور الاستوائي (Metaphase) من الانقسام الخلوي.',
                sideEffects: 'تفاعلات فرط الحساسية، الاعتلال العصبي المحيطي، تثبيط نخاع العظم، آلام المفاصل والعضلات، تساقط الشعر',
                stability: 'مستقر في درجة حرارة الغرفة. لا يهز بقوة لتجنب الرغوة. يجب استخدام فلتر 0.22 micron عند الإعطاء.'
            },
            fu: {
                name: '5-Fluorouracil',
                nameAr: 'فلورويوراسيل (5-FU)',
                standardDose: 400,
                concentration: 50,
                solution: 'D5W',
                solutionVolume: 500,
                vialVolume: 10,
                color: '#22c55e',
                image: 'https://image.qwenlm.ai/public_source/a19eb0bf-f4ce-4bc1-9193-96bbe9311fcb/17c6a4486-cc4f-48b4-8bfa-ab8d7ac60400.png',
                warning: '⚠️ يمكن إعطاؤه كجرعة وريدية أو تسريب مستمر. مراقبة علامات السمية.',
                uses: 'سرطان القولون والمستقيم، سرطان المعدة، سرطان البنكرياس، سرطان الثدي، سرطان الرأس والرقبة',
                mechanism: 'ينتمي لمجموعة Antimetabolites (Pyrimidine analog). يعمل كمضاد للأيض عن طريق التداخل مع تخليق DNA و RNA. يثبط إنزيم Thymidylate synthase مما يمنع تكوين Thymidine اللازم لتخليق DNA.',
                sideEffects: 'تثبيط نخاع العظم، التهاب الغشاء المخاطي للفم، الإسهال، متلازمة اليد-القدم، السمية القلبية (نادرة)',
                stability: 'يحتاج تخزين في الثلاجة (2-8°C). قد يتبلور في البرودة - يسخن في الماء الدافئ ويهز ليذوب.'
            }
        };
        
        let selectedDrug = null;
        let patientWeight = 70;
        let patientHeight = 175;
        let bsa = 1.87;
        let totalDose = 0;
        let requiredVolume = 0;
        
        // Step 5 variables
        let handWashComplete = false;
        let washTimer = 20;
        let washInterval = null;
        
        // Step 6 variables
        let vialCleaned = false;
        
        // Step 7 variables - Air Injection
        let airInjected = 0;
        const airIncrement = 20;
        
        // Step 8 variables
        let drugDrawn = 0;
        const drawIncrement = 15;
        
        // Step 9 variables
        let drugInjected = 0;
        let isMixed = false;
        let mixingComplete = false;
        let mixCount = 0;
        const requiredMixes = 10;
        
        // Step 10 variables
        let disposedItems = 0;
        let isLabeled = false;

        function updateUI() {
            document.querySelectorAll('.step-container').forEach(el => el.classList.remove('active'));
            document.getElementById(`step-${currentStep}`).classList.add('active');
            
            document.getElementById('current-step-num').innerText = currentStep;
            
            const progress = (currentStep / totalSteps) * 100;
            document.getElementById('progress-bar').style.width = `${progress}%`;
            document.getElementById('progress-percent').innerText = `${Math.round(progress)}%`;

            document.getElementById('prev-btn').disabled = currentStep === 1;
            
            const nextBtn = document.getElementById('next-btn');
            if (currentStep === totalSteps) {
                nextBtn.style.display = 'none';
            } else {
                nextBtn.style.display = 'block';
                let canProceed = false;
                if (currentStep === 1) canProceed = stepRequirements[1];
                if (currentStep === 2) canProceed = stepRequirements[2];
                if (currentStep === 3) canProceed = stepRequirements[3];
                if (currentStep === 4) canProceed = stepRequirements[4] === 5;
                if (currentStep === 5) canProceed = stepRequirements[5];
                if (currentStep === 6) canProceed = stepRequirements[6];
                if (currentStep === 7) canProceed = stepRequirements[7];
                if (currentStep === 8) canProceed = stepRequirements[8];
                if (currentStep === 9) canProceed = stepRequirements[9];
                if (currentStep === 10) canProceed = stepRequirements[10] >= 5;

                nextBtn.disabled = !canProceed;
                if(!canProceed) {
                    nextBtn.classList.add('opacity-50', 'cursor-not-allowed');
                    nextBtn.innerText = "أكمل المهمة أولاً";
                } else {
                    nextBtn.classList.remove('opacity-50', 'cursor-not-allowed');
                    nextBtn.innerText = "التالي ➡️";
                }
            }
        }

        function changeStep(direction) {
            currentStep += direction;
            updateUI();
            window.scrollTo({ top: 0, behavior: 'smooth' });
        }

        // Step 1 Logic - Drug Selection
        function selectDrug(drugKey) {
            selectedDrug = drugKey;
            
            document.querySelectorAll('.drug-card').forEach(card => {
                card.classList.remove('selected');
                card.style.borderColor = '#e5e7eb';
            });
            
            const selectedCard = document.getElementById(`drug-${drugKey}`);
            selectedCard.classList.add('selected');
            selectedCard.style.borderColor = '#0ea5e9';
            
            document.getElementById('drug-warning').classList.remove('hidden');
            document.getElementById('drug-warning-text').innerText = drugs[drugKey].warning;
            
            document.getElementById('confirm-drug-btn').disabled = false;
        }

        function confirmDrugSelection() {
            stepRequirements[1] = true;
            
            document.getElementById('selected-drug-name').innerText = `${drugs[selectedDrug].nameAr} (${drugs[selectedDrug].name})`;
            document.getElementById('selected-drug-dose').innerText = `${drugs[selectedDrug].standardDose} mg/m²`;
            
            document.getElementById('vial-drug-name').innerText = drugs[selectedDrug].name;
            document.getElementById('vial-concentration').innerText = `${drugs[selectedDrug].concentration} mg/mL`;
            document.getElementById('vial-volume').innerText = `${drugs[selectedDrug].vialVolume} mL`;
            
            document.getElementById('vial-drug-name-clean').innerText = drugs[selectedDrug].name;
            document.getElementById('vial-concentration-clean').innerText = `${drugs[selectedDrug].concentration} mg/mL`;
            document.getElementById('vial-volume-clean').innerText = `${drugs[selectedDrug].vialVolume} mL`;
            
            document.getElementById('vial-drug-name-draw').innerText = drugs[selectedDrug].name;
            document.getElementById('vial-concentration-draw').innerText = `${drugs[selectedDrug].concentration} mg/mL`;
            document.getElementById('vial-volume-draw').innerText = `${drugs[selectedDrug].vialVolume} mL`;
            
            const drugColor = drugs[selectedDrug].color;
            document.getElementById('syringe-liquid').style.background = `linear-gradient(180deg, ${drugColor}ee 0%, ${drugColor} 100%)`;
            document.getElementById('vial-liquid').style.background = `linear-gradient(180deg, ${drugColor}ee 0%, ${drugColor} 100%)`;
            document.getElementById('syringe-liquid-draw').style.background = `linear-gradient(180deg, ${drugColor}ee 0%, ${drugColor} 100%)`;
            document.getElementById('vial-liquid-draw').style.background = `linear-gradient(180deg, ${drugColor}ee 0%, ${drugColor} 100%)`;
            document.getElementById('iv-liquid').style.background = `linear-gradient(180deg, ${drugColor}55 0%, ${drugColor}aa 100%)`;
            
            changeStep(1);
        }

        // Step 2 Logic - BSA Calculation
        function calculateBSA() {
            patientWeight = parseFloat(document.getElementById('patient-weight').value) || 70;
            patientHeight = parseFloat(document.getElementById('patient-height').value) || 175;
            
            bsa = Math.sqrt((patientHeight * patientWeight) / 3600);
            bsa = Math.round(bsa * 100) / 100;
            
            document.getElementById('bsa-result').innerText = bsa.toFixed(2);
        }

        function confirmBSA() {
            stepRequirements[2] = true;
            
            document.getElementById('calc-bsa').innerText = bsa.toFixed(2);
            document.getElementById('calc-standard-dose').innerText = drugs[selectedDrug].standardDose;
            
            totalDose = bsa * drugs[selectedDrug].standardDose;
            totalDose = Math.round(totalDose * 100) / 100;
            document.getElementById('calc-total-dose').innerText = totalDose.toFixed(2);
            
            requiredVolume = totalDose / drugs[selectedDrug].concentration;
            requiredVolume = Math.round(requiredVolume * 100) / 100;
            document.getElementById('calc-volume').innerText = `${requiredVolume.toFixed(2)} mL`;
            
            document.getElementById('calc-formula-1').innerText = `${bsa.toFixed(2)} × ${drugs[selectedDrug].standardDose} = ${totalDose.toFixed(2)} mg`;
            document.getElementById('calc-concentration').innerText = `${drugs[selectedDrug].concentration} mg/mL`;
            
            document.getElementById('iv-solution-name').innerText = drugs[selectedDrug].solution;
            document.getElementById('iv-solution-volume').innerText = `${drugs[selectedDrug].solutionVolume} mL`;
            
            document.getElementById('required-air').innerText = requiredVolume.toFixed(2);
            document.getElementById('vial-amount-draw').innerText = requiredVolume.toFixed(2);
            
            changeStep(1);
        }

        // Step 3 Logic - Confirm Dose
        function confirmDose() {
            stepRequirements[3] = true;
            changeStep(1);
        }

        // Step 4 Logic - PPE with Improved Animations
        function togglePPE(btn, step, itemType) {
            if (btn.classList.contains('checked')) return;
            btn.classList.add('checked');
            
            if (itemType === 'hair-cover') {
                document.getElementById('ppe-hair-cover').classList.add('show');
            } else if (itemType === 'goggles') {
                document.getElementById('ppe-goggles').classList.add('show');
            } else if (itemType === 'mask') {
                document.getElementById('ppe-mask').classList.add('show');
            } else if (itemType === 'gown') {
                document.getElementById('ppe-gown').classList.add('show');
            } else if (itemType === 'gloves') {
                document.getElementById('ppe-gloves-left').classList.add('show');
                document.getElementById('ppe-gloves-right').classList.add('show');
            }
            
            stepRequirements[step]++;
            if (stepRequirements[step] === 5) {
                document.getElementById(`step${step}-msg`).classList.remove('hidden');
                createSuccessParticles(btn);
            }
            updateUI();
        }

        // Step 5 Logic - Hand Washing Interactive
        function startHandWash() {
            if (handWashComplete) return;
            
            const washBtn = document.getElementById('wash-btn');
            washBtn.disabled = true;
            washBtn.innerText = '🧼 جاري غسل اليدين...';
            
            // Show water and hands
            document.getElementById('water-stream').style.opacity = '1';
            document.getElementById('water-drops').style.opacity = '1';
            document.getElementById('left-hand').style.opacity = '1';
            document.getElementById('right-hand').style.opacity = '1';
            document.getElementById('soap-bubbles').style.opacity = '1';
            
            // Add washing animation
            document.getElementById('left-hand').classList.add('washing');
            document.getElementById('right-hand').classList.add('washing');
            
            // Start timer
            washTimer = 20;
            document.getElementById('wash-timer').innerText = washTimer;
            
            washInterval = setInterval(() => {
                washTimer--;
                document.getElementById('wash-timer').innerText = washTimer;
                
                if (washTimer <= 0) {
                    clearInterval(washInterval);
                    handWashComplete = true;
                    stepRequirements[5] = true;
                    
                    // Stop animations
                    document.getElementById('left-hand').classList.remove('washing');
                    document.getElementById('right-hand').classList.remove('washing');
                    document.getElementById('water-stream').style.opacity = '0';
                    document.getElementById('water-drops').style.opacity = '0';
                    document.getElementById('soap-bubbles').style.opacity = '0';
                    
                    washBtn.innerText = '✅ تم غسل اليدين';
                    washBtn.classList.add('from-green-500', 'to-emerald-600');
                    document.getElementById('wash-complete-msg').classList.remove('hidden');
                    
                    // Enable clean hood button
                    document.getElementById('clean-btn').disabled = false;
                    
                    createSuccessParticles(washBtn);
                    updateUI();
                }
            }, 1000);
        }

        function cleanHood() {
            const btn = document.getElementById('clean-btn');
            btn.innerHTML = '<span class="loading-spinner inline-block w-5 h-5 mr-2"></span> جاري التعقيم...';
            btn.disabled = true;
            setTimeout(() => {
                btn.classList.add('bg-gradient-to-r', 'from-green-100', 'to-emerald-100', 'border-green-500', 'text-green-700');
                btn.innerHTML = '✨ تم التعقيم بنجاح';
                document.getElementById('clean-msg').classList.remove('hidden');
                createSuccessParticles(btn);
                updateUI();
            }, 1500);
        }

        // Step 6 Logic - Vial Cleaning
        function cleanVial() {
            if (vialCleaned) return;
            
            const swab = document.getElementById('alcohol-swab');
            const vialCap = document.getElementById('vial-cap-clean');
            
            // Show swab
            swab.style.opacity = '1';
            swab.style.bottom = '120px';
            
            // Animate wiping motion
            setTimeout(() => {
                swab.style.transform = 'translateX(-50%) rotate(-30deg)';
            }, 300);
            
            setTimeout(() => {
                swab.style.transform = 'translateX(-50%) rotate(30deg)';
            }, 600);
            
            setTimeout(() => {
                swab.style.transform = 'translateX(-50%) rotate(-30deg)';
            }, 900);
            
            setTimeout(() => {
                // Clean effect
                vialCap.style.background = 'linear-gradient(180deg, #10b981 0%, #059669 50%, #047857 100%)';
                
                // Create sparkles
                const sparklesContainer = document.getElementById('clean-sparkles');
                for (let i = 0; i < 8; i++) {
                    const sparkle = document.createElement('div');
                    sparkle.style.position = 'absolute';
                    sparkle.style.width = '10px';
                    sparkle.style.height = '10px';
                    sparkle.style.background = 'radial-gradient(circle, #fbbf24, transparent)';
                    sparkle.style.borderRadius = '50%';
                    sparkle.style.left = `${40 + Math.random() * 40}%`;
                    sparkle.style.top = `${10 + Math.random() * 30}%`;
                    sparkle.style.animation = `successPop 0.6s ease-out forwards`;
                    sparkle.style.animationDelay = `${i * 0.1}s`;
                    sparklesContainer.appendChild(sparkle);
                    
                    setTimeout(() => sparkle.remove(), 1000);
                }
                
                vialCleaned = true;
                stepRequirements[6] = true;
                
                document.getElementById('clean-vial-btn').disabled = true;
                document.getElementById('clean-vial-btn').innerText = '✅ تم تعقيم القارورة';
                document.getElementById('clean-vial-btn').classList.add('from-green-500', 'to-emerald-600');
                document.getElementById('vial-clean-msg').classList.remove('hidden');
                document.getElementById('air-inject-proceed-btn').classList.remove('hidden');
                
                createSuccessParticles(document.getElementById('clean-vial-btn'));
                updateUI();
            }, 1200);
        }

        function proceedToAirInject() {
            changeStep(1);
        }

        // Step 7 Logic - Inject Air into Vial
        function injectAir() {
            if (airInjected >= requiredVolume) return;
            
            airInjected = Math.min(airInjected + airIncrement, requiredVolume);
            
            document.getElementById('air-injected').innerText = airInjected.toFixed(2);
            
            const plunger = document.getElementById('plunger');
            plunger.style.top = `${85 + (airInjected / requiredVolume) * 50}px`;
            
            createAirBubblesInVial();
            
            if (airInjected >= requiredVolume) {
                document.getElementById('inject-air-btn').disabled = true;
                document.getElementById('inject-air-btn').innerText = '✅ اكتمل حقن الهواء';
                document.getElementById('air-msg').classList.remove('hidden');
                document.getElementById('draw-proceed-btn').classList.remove('hidden');
                stepRequirements[7] = true;
                createSuccessParticles(document.getElementById('inject-air-btn'));
                updateUI();
            }
        }

        function createAirBubblesInVial() {
            const container = document.getElementById('vial-bubbles-container');
            for (let i = 0; i < 3; i++) {
                const bubble = document.createElement('div');
                bubble.className = 'air-bubble';
                bubble.style.width = `${8 + Math.random() * 12}px`;
                bubble.style.height = bubble.style.width;
                bubble.style.left = `${20 + Math.random() * 60}%`;
                bubble.style.bottom = `${10 + Math.random() * 50}%`;
                bubble.style.animationDelay = `${Math.random() * 0.5}s`;
                container.appendChild(bubble);
                
                setTimeout(() => {
                    bubble.remove();
                }, 2000);
            }
        }

        function proceedToDraw() {
            changeStep(1);
        }

        // Step 8 Logic - Drawing Drug
        function drawDrug() {
            if (drugDrawn >= requiredVolume) return;
            
            drugDrawn = Math.min(drugDrawn + drawIncrement, requiredVolume);
            
            const syringeLiquidPercent = (drugDrawn / requiredVolume) * 100;
            document.getElementById('syringe-liquid-draw').style.height = `${syringeLiquidPercent}%`;
            
            const vialLiquidPercent = 70 - ((drugDrawn / requiredVolume) * 70);
            document.getElementById('vial-liquid-draw').style.height = `${Math.max(vialLiquidPercent, 10)}%`;
            
            document.getElementById('vial-amount-draw').innerText = (requiredVolume - drugDrawn).toFixed(2);
            document.getElementById('syringe-amount-draw').innerText = drugDrawn.toFixed(2);
            
            const plunger = document.getElementById('plunger-draw');
            plunger.style.top = `${85 + (drugDrawn / requiredVolume) * 50}px`;
            
            if (drugDrawn >= requiredVolume) {
                document.getElementById('draw-btn').disabled = true;
                document.getElementById('draw-btn').innerText = '✅ اكتمل السحب';
                document.getElementById('draw-msg').classList.remove('hidden');
                document.getElementById('inject-proceed-btn').classList.remove('hidden');
                stepRequirements[8] = true;
                createSuccessParticles(document.getElementById('draw-btn'));
                updateUI();
            }
        }

        function proceedToInject() {
            mixCount = 0;
            mixingComplete = false;
            isMixed = false;
            drugInjected = 0;
            
            document.getElementById('inject-btn').disabled = false;
            document.getElementById('inject-btn').innerText = '💉 حقن الدواء في الكيس';
            document.getElementById('inject-msg').classList.add('hidden');
            document.getElementById('mix-instruction').classList.add('hidden');
            document.getElementById('mix-msg').classList.add('hidden');
            document.getElementById('mix-progress-bar').style.width = '0%';
            document.getElementById('mix-progress-text').innerText = '0';
            document.getElementById('bubbles-container').innerHTML = '';
            
            document.getElementById('inject-plunger').setAttribute('y', '30');
            document.getElementById('syringe-inject-liquid').setAttribute('height', '18');
            document.getElementById('syringe-inject-liquid').setAttribute('y', '70');
            
            changeStep(1);
        }

        // Step 9 Logic - Injecting into IV Bag
        function injectIntoBag() {
            if (drugInjected >= drugDrawn) return;
            
            drugInjected = drugDrawn;
            
            const injectPlunger = document.getElementById('inject-plunger');
            const syringeInjectLiquid = document.getElementById('syringe-inject-liquid');
            
            injectPlunger.setAttribute('y', '50');
            syringeInjectLiquid.setAttribute('height', '0');
            syringeInjectLiquid.setAttribute('y', '88');
            
            const ivLiquidPercent = 60 + ((drugInjected / drugs[selectedDrug].solutionVolume) * 30);
            document.getElementById('iv-liquid').style.height = `${Math.min(ivLiquidPercent, 90)}%`;
            
            const bubblesContainer = document.getElementById('bubbles-container');
            bubblesContainer.innerHTML = '';
            for (let i = 0; i < 15; i++) {
                const bubble = document.createElement('div');
                bubble.className = 'drop-animation';
                bubble.style.left = `${30 + Math.random() * 40}%`;
                bubble.style.top = `${20 + Math.random() * 30}%`;
                bubble.style.background = drugs[selectedDrug].color;
                bubble.style.animationDelay = `${i * 0.08}s`;
                bubble.style.color = drugs[selectedDrug].color;
                bubblesContainer.appendChild(bubble);
            }
            
            document.getElementById('drug-added').innerText = drugInjected.toFixed(2);
            
            setTimeout(() => {
                document.getElementById('inject-btn').disabled = true;
                document.getElementById('inject-btn').innerText = '✅ تم الحقن';
                document.getElementById('inject-msg').classList.remove('hidden');
                document.getElementById('mix-instruction').classList.remove('hidden');
                createSuccessParticles(document.getElementById('inject-btn'));
            }, 500);
        }

        // Step 9 Mixing Logic
        function handleMixClick() {
            if (mixingComplete) return;
            
            mixCount++;
            
            document.getElementById('mix-count-display').innerText = mixCount;
            document.getElementById('mix-progress-text').innerText = mixCount;
            
            const progressPercent = (mixCount / requiredMixes) * 100;
            document.getElementById('mix-progress-bar').style.width = `${progressPercent}%`;
            
            const counterOverlay = document.getElementById('mix-counter-overlay');
            counterOverlay.classList.remove('hidden');
            setTimeout(() => {
                counterOverlay.classList.add('hidden');
            }, 400);
            
            const ivBag = document.getElementById('iv-bag-element');
            ivBag.classList.add('mixing-active');
            setTimeout(() => {
                ivBag.classList.remove('mixing-active');
            }, 500);
            
            const bubblesContainer = document.getElementById('bubbles-container');
            for (let i = 0; i < 5; i++) {
                const swirl = document.createElement('div');
                swirl.className = 'swirl-particle';
                swirl.style.left = `${20 + Math.random() * 60}%`;
                swirl.style.top = `${20 + Math.random() * 60}%`;
                swirl.style.background = drugs[selectedDrug].color;
                swirl.style.color = drugs[selectedDrug].color;
                bubblesContainer.appendChild(swirl);
                
                setTimeout(() => {
                    swirl.remove();
                }, 1800);
            }
            
            if (mixCount >= requiredMixes) {
                mixingComplete = true;
                isMixed = true;
                stepRequirements[9] = true;
                
                document.getElementById('mix-btn-alt').disabled = true;
                document.getElementById('mix-btn-alt').classList.remove('from-purple-600', 'to-purple-700', 'click-hint');
                document.getElementById('mix-btn-alt').classList.add('from-green-600', 'to-green-700');
                document.getElementById('mix-btn-alt').innerText = '✅ تم الخلط بنجاح';
                document.getElementById('mix-msg').classList.remove('hidden');
                
                createSuccessParticles(document.getElementById('mix-btn-alt'));
                
                setTimeout(() => {
                    bubblesContainer.innerHTML = '';
                }, 2000);
                
                updateUI();
            }
        }

        // Success Particles Effect
        function createSuccessParticles(element) {
            const rect = element.getBoundingClientRect();
            const centerX = rect.left + rect.width / 2;
            const centerY = rect.top + rect.height / 2;
            
            for (let i = 0; i < 16; i++) {
                const particle = document.createElement('div');
                particle.className = 'success-particle';
                const angle = (i / 16) * 360;
                const distance = 80 + Math.random() * 40;
                const tx = Math.cos(angle * Math.PI / 180) * distance;
                const ty = Math.sin(angle * Math.PI / 180) * distance;
                
                particle.style.left = `${centerX}px`;
                particle.style.top = `${centerY}px`;
                particle.style.setProperty('--tx', `${tx}px`);
                particle.style.setProperty('--ty', `${ty}px`);
                particle.style.background = `hsl(${120 + Math.random() * 60}, 80%, 50%)`;
                particle.style.animationDelay = `${i * 0.03}s`;
                
                document.body.appendChild(particle);
                
                setTimeout(() => {
                    particle.remove();
                }, 900);
            }
        }

        // Step 10 Logic - Disposal with Centered Bin
        function disposeItem(btn, item) {
            if (btn.classList.contains('checked')) return;
            btn.classList.add('checked');
            btn.style.backgroundColor = '#fef2f2';
            btn.style.borderColor = '#ef4444';
            
            const disposalItem = document.getElementById(`disposal-${item}`);
            if (disposalItem) {
                disposalItem.classList.add('disposed');
            }
            
            disposedItems++;
            createSuccessParticles(btn);
            
            if (disposedItems >= 4) {
                document.getElementById('label-btn').disabled = false;
            }
        }

        function labelBag() {
            if (isLabeled) return;
            isLabeled = true;
            stepRequirements[10] = 5;
            
            const btn = document.getElementById('label-btn');
            btn.classList.add('checked');
            btn.style.backgroundColor = '#d1fae5';
            btn.style.borderColor = '#10b981';
            btn.innerHTML = '✅ تم إضافة الملصق التحذيري';
            createSuccessParticles(btn);
            
            document.getElementById('finish-btn').disabled = false;
            updateUI();
        }

        function finishProcess() {
            document.getElementById('summary-drug').innerText = `${drugs[selectedDrug].nameAr} (${drugs[selectedDrug].name})`;
            document.getElementById('summary-bsa').innerText = bsa.toFixed(2);
            document.getElementById('summary-dose').innerText = totalDose.toFixed(2);
            document.getElementById('summary-volume').innerText = requiredVolume.toFixed(2);
            
            document.getElementById('success-modal').classList.remove('hidden');
        }

        // Drug Info Modal
        function showDrugInfo(drugKey) {
            const drug = drugs[drugKey];
            const modal = document.getElementById('drug-info-modal');
            const content = document.getElementById('modal-drug-content');
            
            document.getElementById('modal-drug-name').innerText = `${drug.nameAr} (${drug.name})`;
            
            content.innerHTML = `
                <div class="flex justify-center mb-6">
                    <div class="w-40 h-40 bg-gradient-to-br from-blue-50 to-indigo-50 rounded-2xl flex items-center justify-center border-2 border-blue-200 shadow-lg">
                        <img src="${drug.image}" alt="${drug.name}" class="h-36 object-contain">
                    </div>
                </div>
                <div class="bg-gradient-to-r from-blue-50 to-indigo-50 p-5 rounded-2xl border border-blue-200">
                    <h3 class="font-bold text-blue-800 mb-3 flex items-center gap-2">📋 الاستخدامات الطبية:</h3>
                    <p class="text-sm text-blue-700 leading-relaxed">${drug.uses}</p>
                </div>
                
                <div class="bg-gradient-to-r from-purple-50 to-pink-50 p-5 rounded-2xl border border-purple-200">
                    <h3 class="font-bold text-purple-800 mb-3 flex items-center gap-2">🔬 آلية العمل:</h3>
                    <p class="text-sm text-purple-700 leading-relaxed">${drug.mechanism}</p>
                </div>
                
                <div class="bg-gradient-to-r from-red-50 to-orange-50 p-5 rounded-2xl border border-red-200">
                    <h3 class="font-bold text-red-800 mb-3 flex items-center gap-2">⚠️ الآثار الجانبية:</h3>
                    <p class="text-sm text-red-700 leading-relaxed">${drug.sideEffects}</p>
                </div>
                
                <div class="bg-gradient-to-r from-green-50 to-emerald-50 p-5 rounded-2xl border border-green-200">
                    <h3 class="font-bold text-green-800 mb-3 flex items-center gap-2">📦 الثبات والتخزين:</h3>
                    <p class="text-sm text-green-700 leading-relaxed">${drug.stability}</p>
                </div>
                
                <div class="bg-gradient-to-r from-yellow-50 to-amber-50 p-5 rounded-2xl border border-yellow-200">
                    <h3 class="font-bold text-yellow-800 mb-3 flex items-center gap-2">💊 معلومات الجرعة:</h3>
                    <div class="grid grid-cols-2 gap-3 text-sm text-yellow-700">
                        <div><span class="font-medium">الجرعة القياسية:</span> ${drug.standardDose} mg/m²</div>
                        <div><span class="font-medium">التركيز:</span> ${drug.concentration} mg/mL</div>
                        <div><span class="font-medium">المحلول:</span> ${drug.solution}</div>
                    </div>
                </div>
            `;
            
            modal.classList.remove('hidden');
        }

        function closeDrugInfo() {
            document.getElementById('drug-info-modal').classList.add('hidden');
        }

        // Initialize
        calculateBSA();
        updateUI();
    </script>
</body>
</html>

