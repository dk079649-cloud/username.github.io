
<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Teddy Case</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            background: linear-gradient(135deg, #0c1445, #1a237e, #283593);
            color: white;
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            align-items: center;
            padding: 20px;
            position: relative;
            overflow-x: hidden;
        }

        .stars {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: 1;
        }

        .star {
            position: absolute;
            background: white;
            border-radius: 50%;
            animation: twinkle 5s infinite;
        }

        @keyframes twinkle {
            0%, 100% { opacity: 0.2; }
            50% { opacity: 1; }
        }

        .container {
            max-width: 500px;
            width: 100%;
            text-align: center;
            z-index: 10;
            position: relative;
        }

        .menu-container {
            width: 100%;
            display: flex;
            justify-content: center;
            gap: 8px;
            margin-bottom: 15px;
            flex-wrap: wrap;
        }

        .menu-button {
            background: linear-gradient(45deg, #f8c300, #ff8c00);
            border: none;
            border-radius: 50px;
            color: #000000;
            font-size: 0.9rem;
            font-weight: bold;
            padding: 8px 16px;
            cursor: pointer;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.3);
            transition: all 0.3s ease;
            z-index: 10;
            position: relative;
            animation: pulse 2s infinite;
        }

        .menu-button:hover {
            transform: translateY(-3px) scale(1.05);
            box-shadow: 0 6px 15px rgba(0, 0, 0, 0.4);
        }

        .profile-button {
            background: linear-gradient(45deg, #9b59b6, #8e44ad);
        }

        .promo-menu-button {
            background: linear-gradient(45deg, #27ae60, #2ecc71);
        }

        .inventory-button {
            background: linear-gradient(45deg, #e67e22, #d35400);
        }

        .market-button {
            background: linear-gradient(45deg, #0088cc, #00a2ff);
        }

        .tgk-button {
            background: linear-gradient(45deg, #3498db, #2980b9);
        }

        .support-button {
            background: linear-gradient(45deg, #e74c3c, #c0392b);
        }

        h1 {
            font-size: 1.8rem;
            margin-bottom: 15px;
            color: #f8c300;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.3);
            position: relative;
            z-index: 10;
        }

        .live-container {
            width: 100%;
            background: rgba(231, 76, 60, 0.8);
            border-radius: 10px;
            padding: 8px 15px;
            margin-bottom: 15px;
            display: flex;
            align-items: center;
            justify-content: space-between;
            border: 2px solid #e74c3c;
        }

        .live-badge {
            background: #e74c3c;
            color: white;
            padding: 4px 10px;
            border-radius: 20px;
            font-size: 0.8rem;
            font-weight: bold;
            animation: livePulse 1.5s infinite;
        }

        @keyframes livePulse {
            0%, 100% { opacity: 1; }
            50% { opacity: 0.7; }
        }

        .live-feed {
            flex-grow: 1;
            margin: 0 10px;
            overflow: hidden;
            height: 20px;
            position: relative;
        }

        .live-item {
            position: absolute;
            width: 100%;
            text-align: center;
            font-size: 0.8rem;
            opacity: 0;
            transform: translateY(20px);
        }

        .online-counter {
            background: rgba(52, 152, 219, 0.8);
            color: white;
            padding: 6px 12px;
            border-radius: 20px;
            font-size: 0.8rem;
            font-weight: bold;
            margin-bottom: 15px;
            display: inline-flex;
            align-items: center;
            gap: 5px;
            border: 2px solid #3498db;
        }

        .online-dot {
            width: 8px;
            height: 8px;
            background: #2ecc71;
            border-radius: 50%;
            animation: onlinePulse 2s infinite;
        }

        @keyframes onlinePulse {
            0%, 100% { opacity: 1; }
            50% { opacity: 0.5; }
        }

        .case-container {
            position: relative;
            width: 320px;
            height: 120px;
            margin: 20px auto;
            overflow: hidden;
            border: 3px solid #f8c300;
            border-radius: 15px;
            background: rgba(34, 34, 34, 0.8);
            box-shadow: 0 0 20px rgba(248, 195, 0, 0.5);
            z-index: 10;
        }

        .case-items {
            display: flex;
            position: absolute;
            height: 100%;
            transition: transform 2.5s cubic-bezier(0.1, 0.8, 0.2, 1);
        }

        .case-item {
            width: 100px;
            height: 100%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 50px;
            flex-shrink: 0;
            border-right: 1px solid rgba(255, 255, 255, 0.1);
        }

        .case-center {
            position: absolute;
            top: 0;
            left: 50%;
            transform: translateX(-50%);
            width: 4px;
            height: 100%;
            background: #f8c300;
            box-shadow: 0 0 10px #f8c300;
            z-index: 10;
        }

        .open-button {
            background: linear-gradient(45deg, #f8c300, #ff8c00);
            border: none;
            border-radius: 50px;
            color: #000000;
            font-size: 1.1rem;
            font-weight: bold;
            padding: 12px 35px;
            margin: 10px 0;
            cursor: pointer;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.3);
            transition: all 0.3s ease;
            z-index: 10;
            position: relative;
            animation: pulse 2s infinite;
        }

        .open-button:hover {
            transform: translateY(-3px) scale(1.05);
            box-shadow: 0 6px 15px rgba(0, 0, 0, 0.4);
        }

        .open-button:active {
            transform: translateY(1px);
        }

        .open-button:disabled {
            background: #444444;
            color: #777777;
            cursor: not-allowed;
            transform: none;
            box-shadow: none;
            animation: none;
        }

        .result {
            margin-top: 15px;
            font-size: 1.3rem;
            min-height: 60px;
            display: flex;
            align-items: center;
            justify-content: center;
            padding: 12px;
            border-radius: 10px;
            background: rgba(50, 50, 50, 0.7);
            width: 100%;
            border: 2px solid #f8c300;
            z-index: 10;
            position: relative;
        }

        .timer {
            margin-top: 12px;
            font-size: 0.9rem;
            color: #f8c300;
            background: rgba(50, 50, 50, 0.7);
            padding: 8px 15px;
            border-radius: 20px;
            z-index: 10;
            position: relative;
        }

        .win-animation {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.8);
            display: none;
            justify-content: center;
            align-items: center;
            z-index: 100;
            flex-direction: column;
        }

        .win-text {
            font-size: 3rem;
            color: #f8c300;
            text-shadow: 0 0 20px #ff8c00;
            animation: winPulse 1s infinite;
            margin-bottom: 30px;
        }

        .win-emoji {
            font-size: 8rem;
            animation: bounce 1s infinite;
        }

        @keyframes winPulse {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.1); }
        }

        @keyframes bounce {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-20px); }
        }

        @keyframes pulse {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.02); }
        }

        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.8);
            z-index: 100;
            justify-content: center;
            align-items: center;
        }

        .modal-content {
            background: #222222;
            padding: 25px;
            border-radius: 15px;
            width: 90%;
            max-width: 380px;
            text-align: center;
            border: 2px solid #f8c300;
            z-index: 101;
            animation: modalAppear 0.3s ease;
        }

        @keyframes modalAppear {
            from { transform: scale(0.8); opacity: 0; }
            to { transform: scale(1); opacity: 1; }
        }

        .modal h2 {
            color: #f8c300;
            margin-bottom: 15px;
            font-size: 1.3rem;
        }

        .promo-input {
            width: 100%;
            padding: 12px;
            margin: 12px 0;
            border: 2px solid #f8c300;
            border-radius: 10px;
            background: #333;
            color: white;
            font-size: 0.9rem;
            text-align: center;
        }

        .promo-input::placeholder {
            color: #888;
        }

        .modal-buttons {
            display: flex;
            gap: 12px;
            justify-content: center;
            margin-top: 15px;
        }

        .modal-button {
            padding: 10px 20px;
            border: none;
            border-radius: 50px;
            font-size: 0.9rem;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s ease;
        }

        .confirm-button {
            background: linear-gradient(45deg, #27ae60, #2ecc71);
            color: white;
        }

        .cancel-button {
            background: linear-gradient(45deg, #e74c3c, #c0392b);
            color: white;
        }

        .modal-button:hover {
            transform: translateY(-2px);
        }

        .game-section {
            display: none;
        }

        .profile-section {
            display: none;
            text-align: center;
        }

        .inventory-section {
            display: none;
            text-align: center;
        }

        .market-section {
            display: none;
            text-align: center;
        }

        .active-section {
            display: block;
        }

        .profile-info {
            background: rgba(50, 50, 50, 0.7);
            padding: 15px;
            border-radius: 15px;
            margin: 15px 0;
            border: 2px solid #9b59b6;
            z-index: 10;
            position: relative;
        }

        .balance-card {
            background: linear-gradient(135deg, #9b59b6, #8e44ad);
            padding: 15px;
            border-radius: 15px;
            margin: 15px 0;
            text-align: center;
            box-shadow: 0 4px 15px rgba(155, 89, 182, 0.4);
        }

        .stars-count {
            font-size: 2rem;
            color: #f8c300;
            margin: 5px 0;
            font-weight: bold;
        }

        .attempts-count {
            font-size: 1.1rem;
            color: #ffffff;
            margin: 5px 0;
        }

        .purchase-options {
            display: flex;
            flex-direction: column;
            gap: 12px;
            margin: 18px 0;
        }

        .purchase-option {
            background: rgba(50, 50, 50, 0.7);
            padding: 18px;
            border-radius: 15px;
            border: 2px solid #f8c300;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .purchase-info {
            text-align: left;
        }

        .purchase-title {
            font-size: 1.1rem;
            color: #f8c300;
            margin-bottom: 5px;
        }

        .purchase-price {
            font-size: 0.9rem;
            color: #27ae60;
        }

        .buy-button {
            background: linear-gradient(45deg, #27ae60, #2ecc71);
            border: none;
            border-radius: 50px;
            color: white;
            font-size: 0.9rem;
            font-weight: bold;
            padding: 8px 16px;
            cursor: pointer;
            transition: all 0.3s ease;
        }

        .buy-button:hover {
            transform: translateY(-2px);
        }

        .add-stars-button {
            background: linear-gradient(45deg, #f8c300, #ff8c00);
            border: none;
            border-radius: 50px;
            color: #000000;
            font-size: 1rem;
            font-weight: bold;
            padding: 10px 25px;
            margin: 12px 0;
            cursor: pointer;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.3);
            transition: all 0.3s ease;
            z-index: 10;
            position: relative;
            animation: pulse 2s infinite;
        }

        .add-stars-button:hover {
            transform: translateY(-3px) scale(1.05);
            box-shadow: 0 6px 15px rgba(0, 0, 0, 0.4);
        }

        .profile-history {
            margin-top: 20px;
            width: 100%;
            background: rgba(50, 50, 50, 0.7);
            border-radius: 10px;
            padding: 15px;
            text-align: left;
        }

        .profile-history h2 {
            font-size: 1.1rem;
            margin-bottom: 10px;
            color: #f8c300;
            text-align: center;
        }

        .history-item {
            padding: 8px;
            border-bottom: 1px solid #444444;
            display: flex;
            justify-content: space-between;
            font-size: 0.9rem;
        }

        .history-item:last-child {
            border-bottom: none;
        }

        .inventory-items {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 15px;
            margin: 20px 0;
        }

        .inventory-item {
            background: rgba(50, 50, 50, 0.7);
            border-radius: 15px;
            padding: 15px;
            border: 2px solid #f8c300;
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 10px;
        }

        .item-emoji {
            font-size: 3rem;
        }

        .item-name {
            font-size: 1rem;
            color: #f8c300;
            font-weight: bold;
        }

        .item-price {
            font-size: 0.9rem;
            color: #27ae60;
        }

        .sell-button {
            background: linear-gradient(45deg, #e74c3c, #c0392b);
            border: none;
            border-radius: 50px;
            color: white;
            font-size: 0.9rem;
            font-weight: bold;
            padding: 8px 16px;
            cursor: pointer;
            transition: all 0.3s ease;
            width: 100%;
        }

        .sell-button:hover {
            transform: translateY(-2px);
        }

        .share-button {
            background: linear-gradient(45deg, #0088cc, #00a2ff);
            border: none;
            border-radius: 50px;
            color: white;
            font-size: 0.9rem;
            font-weight: bold;
            padding: 8px 16px;
            cursor: pointer;
            transition: all 0.3s ease;
            width: 100%;
            margin-top: 5px;
        }

        .share-button:hover {
            transform: translateY(-2px);
        }

        .empty-inventory {
            text-align: center;
            padding: 40px;
            color: #888;
            font-size: 1.1rem;
        }

        .payment-methods {
            display: flex;
            flex-direction: column;
            gap: 12px;
            margin: 18px 0;
        }

        .payment-method {
            background: rgba(50, 50, 50, 0.7);
            padding: 18px;
            border-radius: 15px;
            border: 2px solid #f8c300;
            text-align: center;
        }

        .payment-title {
            font-size: 1.1rem;
            color: #f8c300;
            margin-bottom: 12px;
        }

        .payment-button {
            background: linear-gradient(45deg, #27ae60, #2ecc71);
            border: none;
            border-radius: 50px;
            color: white;
            font-size: 0.9rem;
            font-weight: bold;
            padding: 10px 20px;
            cursor: pointer;
            transition: all 0.3s ease;
            width: 100%;
            margin-top: 8px;
        }

        .payment-button:hover {
            transform: translateY(-2px);
        }

        .usdt-button {
            background: linear-gradient(45deg, #009688, #26a69a);
        }

        .stars-button {
            background: linear-gradient(45deg, #0088cc, #00a2ff);
        }

        .firework {
            position: absolute;
            width: 5px;
            height: 5px;
            border-radius: 50%;
            box-shadow: 0 0 10px #fff;
            z-index: 1;
        }

        @keyframes firework {
            0% { transform: translate(var(--x), var(--y)); width: 5px; height: 5px; opacity: 1; }
            50% { width: 3px; height: 3px; }
            100% { width: 150px; height: 150px; opacity: 0; }
        }

        .win {
            color: #f8c300;
            border-color: #f8c300;
        }

        .lose {
            color: #e74c3c;
            border-color: #e74c3c;
        }

        .attempts-info {
            margin: 8px 0;
            color: #f8c300;
            font-size: 0.9rem;
            z-index: 10;
            position: relative;
        }

        .market-items {
            display: flex;
            flex-direction: column;
            gap: 12px;
            margin: 20px 0;
        }

        .market-item {
            background: rgba(50, 50, 50, 0.7);
            border-radius: 15px;
            padding: 15px;
            border: 2px solid #0088cc;
            display: flex;
            align-items: center;
            gap: 15px;
        }

        .market-item-emoji {
            font-size: 2.5rem;
        }

        .market-item-info {
            flex-grow: 1;
            text-align: left;
        }

        .market-item-name {
            font-size: 1rem;
            color: #f8c300;
            font-weight: bold;
            margin-bottom: 5px;
        }

        .market-item-seller {
            font-size: 0.8rem;
            color: #ccc;
        }

        .market-item-price {
            font-size: 1.1rem;
            color: #27ae60;
            font-weight: bold;
        }

        .market-buy-button {
            background: linear-gradient(45deg, #27ae60, #2ecc71);
            border: none;
            border-radius: 50px;
            color: white;
            font-size: 0.9rem;
            font-weight: bold;
            padding: 8px 16px;
            cursor: pointer;
            transition: all 0.3s ease;
            white-space: nowrap;
        }

        .market-buy-button:hover {
            transform: translateY(-2px);
        }

        .market-sell-section {
            margin-top: 25px;
            padding: 20px;
            background: rgba(50, 50, 50, 0.7);
            border-radius: 15px;
            border: 2px solid #f8c300;
        }

        .sell-form {
            display: flex;
            flex-direction: column;
            gap: 12px;
        }

        .sell-select, .sell-input {
            width: 100%;
            padding: 12px;
            border: 2px solid #f8c300;
            border-radius: 10px;
            background: #333;
            color: white;
            font-size: 0.9rem;
        }

        .sell-button-form {
            background: linear-gradient(45deg, #f8c300, #ff8c00);
            border: none;
            border-radius: 50px;
            color: #000000;
            font-size: 1rem;
            font-weight: bold;
            padding: 12px;
            cursor: pointer;
            transition: all 0.3s ease;
        }

        .sell-button-form:hover {
            transform: translateY(-2px);
        }

        .refresh-button {
            background: linear-gradient(45deg, #3498db, #2980b9);
            border: none;
            border-radius: 50px;
            color: white;
            font-size: 0.9rem;
            font-weight: bold;
            padding: 8px 16px;
            cursor: pointer;
            transition: all 0.3s ease;
            margin-bottom: 15px;
        }

        .refresh-button:hover {
            transform: translateY(-2px);
        }
    </style>
</head>
<body>
    <div class="stars" id="stars"></div>

    <div class="win-animation" id="win-animation">
        <div class="win-text">Поздравляем!</div>
        <div class="win-emoji">🧸</div>
    </div>

    <div class="container">
        <div class="menu-container">
            <button class="menu-button" id="game-button">Кейс</button>
            <button class="menu-button profile-button" id="profile-button">Профиль</button>
            <button class="menu-button inventory-button" id="inventory-button">Инвентарь</button>
            <button class="menu-button market-button" id="market-button">Рынок</button>
            <button class="menu-button promo-menu-button" id="promo-menu-button">Промокод</button>
            <a href="https://t.me/starsfry" class="menu-button tgk-button" target="_blank">Тгк</a>
            <a href="https://t.me/M3ff337" class="menu-button support-button" target="_blank">Поддержка</a>
        </div>
        
        <div class="online-counter" id="online-counter">
            <div class="online-dot"></div>
            Онлайн: 0
        </div>
        
        <div class="game-section active-section" id="game-section">
            <h1>Teddy Case</h1>
            
            <div class="live-container">
                <div class="live-badge">LIVE</div>
                <div class="live-feed" id="live-feed"></div>
                <div class="live-badge">🎁</div>
            </div>
            
            <div class="case-container">
                <div class="case-center"></div>
                <div class="case-items" id="case-items"></div>
            </div>
            
            <div class="attempts-info" id="attempts-info">Доступные попытки: 1</div>
            
            <button class="open-button" id="open-button">Открыть кейс</button>
            
            <div class="result" id="result">Нажмите "Открыть кейс"</div>
            
            <div class="timer" id="timer"></div>
        </div>

        <div class="profile-section" id="profile-section">
            <h1>Профиль</h1>
            
            <div class="balance-card">
                <div style="font-size: 0.9rem; color: #ffffff;">Ваш баланс</div>
                <div class="stars-count" id="stars-count">0 ⭐</div>
                <div class="attempts-count" id="profile-attempts">Попытки: 1</div>
            </div>

            <button class="add-stars-button" id="add-stars-button">Пополнить звезды</button>

            <div class="purchase-options">
                <h2>Покупка попыток</h2>
                <div class="purchase-option">
                    <div class="purchase-info">
                        <div class="purchase-title">1 попытка</div>
                        <div class="purchase-price">Цена: 5 ⭐</div>
                    </div>
                    <button class="buy-button" data-attempts="1" data-price="5">Купить</button>
                </div>
                
                <div class="purchase-option">
                    <div class="purchase-info">
                        <div class="purchase-title">10 попыток</div>
                        <div class="purchase-price">Цена: 49 ⭐</div>
                    </div>
                    <button class="buy-button" data-attempts="10" data-price="49">Купить</button>
                </div>
            </div>

            <div class="profile-history">
                <h2>История открытий</h2>
                <div id="history-list"></div>
            </div>
        </div>

        <div class="inventory-section" id="inventory-section">
            <h1>Инвентарь</h1>
            <div class="inventory-items" id="inventory-items"></div>
        </div>

        <div class="market-section" id="market-section">
            <h1>Рынок подарков</h1>
            <button class="refresh-button" id="refresh-market">🔄 Обновить</button>
            
            <div class="market-items" id="market-items">
                <!-- Рыночные предложения будут загружаться здесь -->
            </div>

            <div class="market-sell-section">
                <h2>Выставить на продажу</h2>
                <div class="sell-form">
                    <select class="sell-select" id="sell-item-select">
                        <option value="">Выберите предмет</option>
                    </select>
                    <input type="number" class="sell-input" id="sell-price" placeholder="Цена в звездах" min="1" max="1000">
                    <button class="sell-button-form" id="sell-item-button">Выставить на продажу</button>
                </div>
            </div>
        </div>
    </div>

    <div class="modal" id="promo-modal">
        <div class="modal-content">
            <h2>Введите промокод</h2>
            <input type="text" class="promo-input" id="promo-input" placeholder="Введите промокод" maxlength="20">
            <div class="modal-buttons">
                <button class="modal-button confirm-button" id="confirm-promo">Активировать</button>
                <button class="modal-button cancel-button" id="cancel-promo">Отмена</button>
            </div>
            <div id="promo-result" style="margin-top: 15px; min-height: 20px;"></div>
        </div>
    </div>

    <div class="modal" id="stars-modal">
        <div class="modal-content">
            <h2>Пополнение звезд</h2>
            
            <div class="payment-methods">
                <div class="payment-method">
                    <div class="payment-title">Telegram Stars</div>
                    <p style="margin-bottom: 15px; color: #ccc; font-size: 0.9rem;">Мгновенное пополнение через встроенную систему Telegram</p>
                    <button class="payment-button stars-button" onclick="alert('Функция пополнения через Telegram Stars будет доступна после интеграции с ботом')">Пополнить через Stars</button>
                </div>
                
                <div class="payment-method">
                    <div class="payment-title">USDT (TRC-20)</div>
                    <p style="margin-bottom: 15px; color: #ccc; font-size: 0.9rem;">Пополнение через криптовалюту USDT</p>
                    <button class="payment-button usdt-button" onclick="alert('Для пополнения через USDT свяжитесь с администратором: @M3ff337')">Пополнить через USDT</button>
                </div>
            </div>
            
            <div class="modal-buttons">
                <button class="modal-button cancel-button" id="cancel-stars">Закрыть</button>
            </div>
        </div>
    </div>

    <script>
        document.addEventListener('DOMContentLoaded', function() {
            // Глобальные переменные для рынка
            let marketItems = [];
            let onlineUsers = 0;

            function createStars() {
                const starsContainer = document.getElementById('stars');
                const starsCount = 150;
                
                for (let i = 0; i < starsCount; i++) {
                    const star = document.createElement('div');
                    star.className = 'star';
                    
                    const size = Math.random() * 2 + 1;
                    star.style.width = `${size}px`;
                    star.style.height = `${size}px`;
                    
                    star.style.left = `${Math.random() * 100}%`;
                    star.style.top = `${Math.random() * 100}%`;
                    
                    star.style.animationDelay = `${Math.random() * 5}s`;
                    
                    starsContainer.appendChild(star);
                }
            }

            const gameButton = document.getElementById('game-button');
            const profileButton = document.getElementById('profile-button');
            const inventoryButton = document.getElementById('inventory-button');
            const marketButton = document.getElementById('market-button');
            const promoMenuButton = document.getElementById('promo-menu-button');
            const gameSection = document.getElementById('game-section');
            const profileSection = document.getElementById('profile-section');
            const inventorySection = document.getElementById('inventory-section');
            const marketSection = document.getElementById('market-section');
            const caseItems = document.getElementById('case-items');
            const openButton = document.getElementById('open-button');
            const resultElement = document.getElementById('result');
            const timerElement = document.getElementById('timer');
            const historyList = document.getElementById('history-list');
            const attemptsInfo = document.getElementById('attempts-info');
            const starsCount = document.getElementById('stars-count');
            const profileAttempts = document.getElementById('profile-attempts');
            const promoModal = document.getElementById('promo-modal');
            const promoInput = document.getElementById('promo-input');
            const confirmPromo = document.getElementById('confirm-promo');
            const cancelPromo = document.getElementById('cancel-promo');
            const promoResult = document.getElementById('promo-result');
            const addStarsButton = document.getElementById('add-stars-button');
            const starsModal = document.getElementById('stars-modal');
            const cancelStars = document.getElementById('cancel-stars');
            const winAnimation = document.getElementById('win-animation');
            const liveFeed = document.getElementById('live-feed');
            const inventoryItems = document.getElementById('inventory-items');
            const buyButtons = document.querySelectorAll('.buy-button');
            const onlineCounter = document.getElementById('online-counter');
            const marketItemsContainer = document.getElementById('market-items');
            const refreshMarketButton = document.getElementById('refresh-market');
            const sellItemSelect = document.getElementById('sell-item-select');
            const sellPriceInput = document.getElementById('sell-price');
            const sellItemButton = document.getElementById('sell-item-button');
            
            function generateUserId() {
                const savedId = localStorage.getItem('userId');
                if (savedId) {
                    return savedId;
                }
                const newId = 'USER' + Math.floor(10000 + Math.random() * 90000);
                localStorage.setItem('userId', newId);
                return newId;
            }
            
            const prizes = [
                { emoji: "🧸", name: "Мишка", color: "#27ae60", textColor: "#ffffff", type: "win", price: 10 },
                { emoji: "❌", name: "Крестик", color: "#e74c3c", textColor: "#ffffff", type: "lose", price: 0 },
                { emoji: "🧸", name: "Мишка", color: "#27ae60", textColor: "#ffffff", type: "win", price: 10 },
                { emoji: "❌", name: "Крестик", color: "#e74c3c", textColor: "#ffffff", type: "lose", price: 0 },
                { emoji: "🧸", name: "Мишка", color: "#27ae60", textColor: "#ffffff", type: "win", price: 10 },
                { emoji: "❌", name: "Крестик", color: "#e74c3c", textColor: "#ffffff", type: "lose", price: 0 },
                { emoji: "🧸", name: "Мишка", color: "#27ae60", textColor: "#ffffff", type: "win", price: 10 },
                { emoji: "❌", name: "Крестик", color: "#e74c3c", textColor: "#ffffff", type: "lose", price: 0 },
                { emoji: "❌", name: "Крестик", color: "#e74c3c", textColor: "#ffffff", type: "lose", price: 0 },
                { emoji: "❌", name: "Крестик", color: "#e74c3c", textColor: "#ffffff", type: "lose", price: 0 }
            ];
            
            const promoList = {
                'KOSMI1': { used: false, attempts: 1 },
                'BOB25': { used: false, attempts: 1 },
                'ZALYPIK17': { used: false, attempts: 1 },
                'NEKTO8': { used: false, attempts: 1 },
                'PODAROK12': { used: false, attempts: 1 }
            };
            
            const LAST_OPEN_KEY = 'lastOpenTime';
            const OPEN_HISTORY_KEY = 'openHistory';
            const PROMO_USED_KEY = 'promoUsed';
            const EXTRA_ATTEMPTS_KEY = 'extraAttempts';
            const STARS_COUNT_KEY = 'starsCount';
            const PROMO_LIST_KEY = 'promoList';
            const USER_ID_KEY = 'userId';
            const INVENTORY_KEY = 'inventory';
            const MARKET_ITEMS_KEY = 'marketItems';
            const ONLINE_USERS_KEY = 'onlineUsers';
            
            function initPromoCodes() {
                const savedPromos = localStorage.getItem(PROMO_LIST_KEY);
                if (!savedPromos) {
                    localStorage.setItem(PROMO_LIST_KEY, JSON.stringify(promoList));
                }
            }
            
            function getMoscowTime() {
                const now = new Date();
                const utc = now.getTime() + (now.getTimezoneOffset() * 60000);
                const moscowTime = new Date(utc + (3 * 3600000));
                return moscowTime;
            }
            
            function getStarsCount() {
                return parseInt(localStorage.getItem(STARS_COUNT_KEY) || '0');
            }
            
            function setStarsCount(count) {
                localStorage.setItem(STARS_COUNT_KEY, count.toString());
                updateStarsDisplay();
            }
            
            function updateStarsDisplay() {
                const stars = getStarsCount();
                starsCount.textContent = `${stars} ⭐`;
            }
            
            function getInventory() {
                return JSON.parse(localStorage.getItem(INVENTORY_KEY) || '[]');
            }
            
            function saveInventory(inventory) {
                localStorage.setItem(INVENTORY_KEY, JSON.stringify(inventory));
                updateInventoryDisplay();
                updateSellItemSelect();
            }
            
            function updateInventoryDisplay() {
                const inventory = getInventory();
                inventoryItems.innerHTML = '';
                
                if (inventory.length === 0) {
                    inventoryItems.innerHTML = '<div class="empty-inventory">Ваш инвентарь пуст</div>';
                    return;
                }
                
                inventory.forEach((item, index) => {
                    const inventoryItem = document.createElement('div');
                    inventoryItem.className = 'inventory-item';
                    
                    inventoryItem.innerHTML = `
                        <div class="item-emoji">${item.emoji}</div>
                        <div class="item-name">${item.name}</div>
                        <div class="item-price">Цена: ${item.price} ⭐</div>
                        <button class="sell-button" data-index="${index}">Продать</button>
                        <button class="share-button" data-index="${index}">Поделиться в Telegram</button>
                    `;
                    
                    inventoryItems.appendChild(inventoryItem);
                });
                
                document.querySelectorAll('.sell-button').forEach(button => {
                    button.addEventListener('click', function() {
                        const index = parseInt(this.getAttribute('data-index'));
                        sellItem(index);
                    });
                });
                
                document.querySelectorAll('.share-button').forEach(button => {
                    button.addEventListener('click', function() {
                        const index = parseInt(this.getAttribute('data-index'));
                        shareItem(index);
                    });
                });
            }
            
            function sellItem(index) {
                const inventory = getInventory();
                if (index >= 0 && index < inventory.length) {
                    const item = inventory[index];
                    const stars = getStarsCount();
                    
                    setStarsCount(stars + item.price);
                    inventory.splice(index, 1);
                    saveInventory(inventory);
                    
                    alert(`Вы успешно продали ${item.emoji} ${item.name} за ${item.price} звезд!`);
                }
            }
            
            function shareItem(index) {
                const inventory = getInventory();
                if (index >= 0 && index < inventory.length) {
                    const item = inventory[index];
                    const text = `🎉 Я выбил(а) ${item.emoji} ${item.name} в Teddy Case! 🎁\n\nПрисоединяйся: https://t.me/starsfry`;
                    
                    const url = `https://t.me/share/url?url=${encodeURIComponent('https://t.me/starsfry')}&text=${encodeURIComponent(text)}`;
                    window.open(url, '_blank');
                }
            }
            
            function addToInventory(item) {
                const inventory = getInventory();
                inventory.push(item);
                saveInventory(inventory);
            }
            
            // Функции для рынка
            function getMarketItems() {
                return JSON.parse(localStorage.getItem(MARKET_ITEMS_KEY) || '[]');
            }
            
            function saveMarketItems(items) {
                localStorage.setItem(MARKET_ITEMS_KEY, JSON.stringify(items));
                updateMarketDisplay();
            }
            
            function updateMarketDisplay() {
                const items = getMarketItems();
                marketItemsContainer.innerHTML = '';
                
                if (items.length === 0) {
                    marketItemsContainer.innerHTML = '<div class="empty-inventory">На рынке пока нет предложений</div>';
                    return;
                }
                
                items.forEach((item, index) => {
                    const marketItem = document.createElement('div');
                    marketItem.className = 'market-item';
                    
                    marketItem.innerHTML = `
                        <div class="market-item-emoji">${item.emoji}</div>
                        <div class="market-item-info">
                            <div class="market-item-name">${item.name}</div>
                            <div class="market-item-seller">Продавец: ${item.seller}</div>
                        </div>
                        <div class="market-item-price">${item.price} ⭐</div>
                        <button class="market-buy-button" data-index="${index}">Купить</button>
                    `;
                    
                    marketItemsContainer.appendChild(marketItem);
                });
                
                document.querySelectorAll('.market-buy-button').forEach(button => {
                    button.addEventListener('click', function() {
                        const index = parseInt(this.getAttribute('data-index'));
                        buyMarketItem(index);
                    });
                });
            }
            
            function buyMarketItem(index) {
                const items = getMarketItems();
                if (index >= 0 && index < items.length) {
                    const item = items[index];
                    const stars = getStarsCount();
                    
                    if (stars < item.price) {
                        alert('Недостаточно звезд для покупки!');
                        return;
                    }
                    
                    setStarsCount(stars - item.price);
                    
                    // Добавляем предмет в инвентарь покупателя
                    addToInventory({
                        emoji: item.emoji,
                        name: item.name,
                        price: Math.floor(item.price * 0.8) // При перепродаже цена будет ниже
                    });
                    
                    // Удаляем предмет с рынка
                    items.splice(index, 1);
                    saveMarketItems(items);
                    
                    alert(`Вы успешно купили ${item.emoji} ${item.name} за ${item.price} звезд!`);
                }
            }
            
            function updateSellItemSelect() {
                const inventory = getInventory();
                sellItemSelect.innerHTML = '<option value="">Выберите предмет</option>';
                
                inventory.forEach((item, index) => {
                    const option = document.createElement('option');
                    option.value = index;
                    option.textContent = `${item.emoji} ${item.name} (${item.price} ⭐)`;
                    sellItemSelect.appendChild(option);
                });
            }
            
            function sellOnMarket() {
                const selectedIndex = parseInt(sellItemSelect.value);
                const price = parseInt(sellPriceInput.value);
                
                if (isNaN(selectedIndex)) {
                    alert('Выберите предмет для продажи!');
                    return;
                }
                
                if (isNaN(price) || price < 1 || price > 1000) {
                    alert('Введите корректную цену (от 1 до 1000 звезд)');
                    return;
                }
                
                const inventory = getInventory();
                if (selectedIndex >= 0 && selectedIndex < inventory.length) {
                    const item = inventory[selectedIndex];
                    const marketItems = getMarketItems();
                    
                    // Добавляем предмет на рынок
                    marketItems.push({
                        emoji: item.emoji,
                        name: item.name,
                        price: price,
                        seller: localStorage.getItem('userId') || 'Аноним'
                    });
                    
                    saveMarketItems(marketItems);
                    
                    // Удаляем предмет из инвентаря
                    inventory.splice(selectedIndex, 1);
                    saveInventory(inventory);
                    
                    sellPriceInput.value = '';
                    alert(`Вы успешно выставили ${item.emoji} ${item.name} на рынок за ${price} звезд!`);
                }
            }
            
            function simulateOnlineUsers() {
                // Симуляция реальных пользователей онлайн
                const baseUsers = Math.floor(Math.random() * 50) + 20;
                onlineUsers = baseUsers;
                updateOnlineCounter();
                
                // Обновляем каждые 30 секунд
                setInterval(() => {
                    const change = Math.floor(Math.random() * 10) - 5;
                    onlineUsers = Math.max(10, onlineUsers + change);
                    updateOnlineCounter();
                }, 30000);
            }
            
            function updateOnlineCounter() {
                onlineCounter.textContent = `Онлайн: ${onlineUsers}`;
                onlineCounter.innerHTML = `<div class="online-dot"></div> Онлайн: ${onlineUsers}`;
            }
            
            function generateMarketActivity() {
                // Генерируем случайные рыночные предложения
                const items = getMarketItems();
                const possibleItems = [
                    { emoji: "🧸", name: "Мишка", basePrice: 15 },
                    { emoji: "🎁", name: "Подарок", basePrice: 25 },
                    { emoji: "⭐", name: "Золотая звезда", basePrice: 50 },
                    { emoji: "👑", name: "Корона", basePrice: 100 }
                ];
                
                // Добавляем случайные предложения если их мало
                if (items.length < 5) {
                    const randomItem = possibleItems[Math.floor(Math.random() * possibleItems.length)];
                    const price = randomItem.basePrice + Math.floor(Math.random() * 20);
                    const sellers = ['Игрок123', 'TopSeller', 'LuckyGamer', 'ProTrader', 'NewUser'];
                    
                    items.push({
                        emoji: randomItem.emoji,
                        name: randomItem.name,
                        price: price,
                        seller: sellers[Math.floor(Math.random() * sellers.length)]
                    });
                    
                    saveMarketItems(items);
                }
                
                // Удаляем старые предложения
                if (items.length > 10) {
                    items.splice(0, items.length - 8);
                    saveMarketItems(items);
                }
            }
            
            let liveIndex = 0;
            function updateLiveFeed() {
                const liveItems = [
                    "Игрок123 выбил 🧸 Мишку!",
                    "User456 получил ❌ Крестик",
                    "Winner789 открыл 🧸 Мишку!",
                    "Player111 выбил ❌ Крестик",
                    "Lucky222 получил 🧸 Мишку!"
                ];
                
                liveFeed.innerHTML = '';
                
                const liveItem = document.createElement('div');
                liveItem.className = 'live-item';
                liveItem.textContent = liveItems[liveIndex];
                liveItem.style.animation = `liveScroll 5s linear`;
                liveFeed.appendChild(liveItem);
                
                liveIndex = (liveIndex + 1) % liveItems.length;
                
                setTimeout(updateLiveFeed, 5000);
                
                setTimeout(() => {
                    liveItem.style.opacity = '1';
                    liveItem.style.transform = 'translateY(0)';
                    liveItem.style.transition = 'all 0.5s ease';
                }, 100);
                
                setTimeout(() => {
                    liveItem.style.opacity = '0';
                    liveItem.style.transform = 'translateY(-20px)';
                }, 4500);
            }
            
            function getAttemptsCount() {
                const extraAttempts = parseInt(localStorage.getItem(EXTRA_ATTEMPTS_KEY) || '0');
                const hasFreeAttempt = canOpenFree();
                return (hasFreeAttempt ? 1 : 0) + extraAttempts;
            }
            
            function canOpenFree() {
                const lastOpenTime = localStorage.getItem(LAST_OPEN_KEY);
                
                if (!lastOpenTime) {
                    return true;
                }
                
                const lastOpen = new Date(parseInt(lastOpenTime));
                const now = getMoscowTime();
                const diffMs = now - lastOpen;
                const diffHours = diffMs / (1000 * 60 * 60);
                
                return diffHours >= 24;
            }
            
            function updateAttemptsInfo() {
                const attempts = getAttemptsCount();
                const hasFreeAttempt = canOpenFree();
                
                if (hasFreeAttempt) {
                    attemptsInfo.textContent = `Доступные попытки: ${attempts} (1 бесплатная + ${attempts - 1} от промокода/покупки)`;
                    profileAttempts.textContent = `Попытки: ${attempts}`;
                } else {
                    attemptsInfo.textContent = `Доступные попытки: ${attempts} (от промокода/покупки)`;
                    profileAttempts.textContent = `Попытки: ${attempts}`;
                }
                
                if (attempts > 0) {
                    openButton.disabled = false;
                } else {
                    openButton.disabled = true;
                }
            }
            
            function useAttempt() {
                const hasFreeAttempt = canOpenFree();
                
                if (hasFreeAttempt) {
                    localStorage.setItem(LAST_OPEN_KEY, getMoscowTime().getTime().toString());
                } else {
                    let extraAttempts = parseInt(localStorage.getItem(EXTRA_ATTEMPTS_KEY) || '0');
                    if (extraAttempts > 0) {
                        extraAttempts--;
                        localStorage.setItem(EXTRA_ATTEMPTS_KEY, extraAttempts.toString());
                    }
                }
                
                updateAttemptsInfo();
                updateTimer();
            }
            
            function addAttempts(count) {
                let extraAttempts = parseInt(localStorage.getItem(EXTRA_ATTEMPTS_KEY) || '0');
                extraAttempts += count;
                localStorage.setItem(EXTRA_ATTEMPTS_KEY, extraAttempts.toString());
                updateAttemptsInfo();
            }
            
            function updateTimer() {
                const lastOpenTime = localStorage.getItem(LAST_OPEN_KEY);
                const attempts = getAttemptsCount();
                
                if (attempts > 0) {
                    timerElement.textContent = "Вы можете открыть кейс сейчас!";
                    return;
                }
                
                if (!lastOpenTime) {
                    timerElement.textContent = "Вы можете открыть кейс сейчас!";
                    return;
                }
                
                const lastOpen = new Date(parseInt(lastOpenTime));
                const now = getMoscowTime();
                const nextOpenTime = new Date(lastOpen.getTime() + (24 * 60 * 60 * 1000));
                
                if (now >= nextOpenTime) {
                    timerElement.textContent = "Вы можете открыть кейс сейчас!";
                } else {
                    const timeLeft = nextOpenTime - now;
                    const hours = Math.floor(timeLeft / (1000 * 60 * 60));
                    const minutes = Math.floor((timeLeft % (1000 * 60 * 60)) / (1000 * 60));
                    const seconds = Math.floor((timeLeft % (1000 * 60)) / 1000);
                    
                    timerElement.textContent = `Следующее открытие через: ${hours}ч ${minutes}м ${seconds}с`;
                    
                    setTimeout(updateTimer, 1000);
                }
            }
            
            function loadHistory() {
                const history = JSON.parse(localStorage.getItem(OPEN_HISTORY_KEY) || '[]');
                historyList.innerHTML = '';
                
                if (history.length === 0) {
                    historyList.innerHTML = '<div class="history-item">История открытий пуста</div>';
                    return;
                }
                
                const recentHistory = history.slice(-5).reverse();
                
                recentHistory.forEach(item => {
                    const historyItem = document.createElement('div');
                    historyItem.className = 'history-item';
                    
                    const date = new Date(item.time);
                    const formattedDate = date.toLocaleString('ru-RU', {
                        day: '2-digit',
                        month: '2-digit',
                        year: 'numeric',
                        hour: '2-digit',
                        minute: '2-digit'
                    });
                    
                    historyItem.innerHTML = `
                        <span>${formattedDate}</span>
                        <span>${item.result}</span>
                    `;
                    
                    historyList.appendChild(historyItem);
                });
            }
            
            function saveOpenResult(result) {
                const history = JSON.parse(localStorage.getItem(OPEN_HISTORY_KEY) || '[]');
                
                history.push({
                    time: getMoscowTime().getTime(),
                    result: result
                });
                
                localStorage.setItem(OPEN_HISTORY_KEY, JSON.stringify(history));
                loadHistory();
            }
            
            function createFireworks() {
                const colors = ['#f8c300', '#ff8c00', '#ff0000', '#00ff00', '#0000ff', '#ff00ff', '#ffff00'];
                const container = document.body;
                
                for (let i = 0; i < 50; i++) {
                    const firework = document.createElement('div');
                    firework.className = 'firework';
                    
                    const color = colors[Math.floor(Math.random() * colors.length)];
                    firework.style.background = color;
                    firework.style.boxShadow = `0 0 5px ${color}, 0 0 10px ${color}`;
                    
                    const x = Math.random() * window.innerWidth;
                    const y = Math.random() * window.innerHeight;
                    
                    firework.style.setProperty('--x', `${x}px`);
                    firework.style.setProperty('--y', `${y}px`);
                    
                    firework.style.animation = `firework 1s ease-out forwards`;
                    firework.style.animationDelay = `${Math.random() * 0.5}s`;
                    
                    container.appendChild(firework);
                    
                    setTimeout(() => {
                        if (firework.parentNode) {
                            firework.parentNode.removeChild(firework);
                        }
                    }, 1500);
                }
            }
            
            function createCaseItems() {
                caseItems.innerHTML = '';
                
                for (let i = 0; i < 3; i++) {
                    prizes.forEach(prize => {
                        const item = document.createElement('div');
                        item.className = 'case-item';
                        item.style.background = prize.color;
                        item.style.color = prize.textColor;
                        item.textContent = prize.emoji;
                        caseItems.appendChild(item);
                    });
                }
            }
            
            function openCase() {
                if (!getAttemptsCount()) {
                    resultElement.textContent = "У вас нет доступных попыток!";
                    return;
                }
                
                openButton.disabled = true;
                resultElement.textContent = "Открываем...";
                resultElement.className = "result";
                
                useAttempt();
                
                const randomValue = Math.random();
                const isWin = randomValue < 0.4;
                
                let prizeIndex;
                if (isWin) {
                    const winIndices = [0, 2, 4, 6];
                    prizeIndex = winIndices[Math.floor(Math.random() * winIndices.length)];
                } else {
                    const loseIndices = [1, 3, 5, 7, 8, 9];
                    prizeIndex = loseIndices[Math.floor(Math.random() * loseIndices.length)];
                }
                
                const prize = prizes[prizeIndex];
                
                const itemWidth = 100;
                const visibleItems = 3;
                const centerOffset = (visibleItems * itemWidth) / 2 - itemWidth / 2;
                const startPosition = prizes.length * itemWidth;
                const targetPosition = startPosition + (prizeIndex * itemWidth) - centerOffset;
                
                caseItems.style.transform = `translateX(-${startPosition}px)`;
                
                setTimeout(() => {
                    caseItems.style.transform = `translateX(-${targetPosition}px)`;
                }, 50);
                
                setTimeout(() => {
                    let resultText;
                    
                    if (isWin) {
                        addToInventory({
                            emoji: prize.emoji,
                            name: prize.name,
                            price: prize.price
                        });
                        
                        winAnimation.style.display = 'flex';
                        createFireworks();
                        
                        setTimeout(() => {
                            winAnimation.style.display = 'none';
                            resultText = `Поздравляем! Вы выиграли: ${prize.emoji} ${prize.name}`;
                            resultElement.textContent = resultText;
                            resultElement.className = "result win";
                        }, 3000);
                    } else {
                        resultText = `К сожалению, вы не выиграли`;
                        resultElement.textContent = resultText;
                        resultElement.className = "result lose";
                    }
                    
                    saveOpenResult(resultText);
                    updateTimer();
                }, 2550);
            }
            
            function activatePromo() {
                const promoValue = promoInput.value.trim().toUpperCase();
                promoResult.textContent = "";
                
                if (promoValue === '') {
                    promoResult.textContent = "Введите промокод!";
                    promoResult.style.color = "#e74c3c";
                    return;
                }
                
                const savedPromos = JSON.parse(localStorage.getItem(PROMO_LIST_KEY) || '{}');
                
                if (!savedPromos[promoValue]) {
                    promoResult.textContent = "Неверный промокод!";
                    promoResult.style.color = "#e74c3c";
                    return;
                }
                
                if (savedPromos[promoValue].used) {
                    promoResult.textContent = "Этот промокод уже использован!";
                    promoResult.style.color = "#e74c3c";
                    return;
                }
                
                savedPromos[promoValue].used = true;
                localStorage.setItem(PROMO_LIST_KEY, JSON.stringify(savedPromos));
                
                addAttempts(savedPromos[promoValue].attempts);
                
                promoResult.textContent = `Промокод активирован! +${savedPromos[promoValue].attempts} попытка`;
                promoResult.style.color = "#27ae60";
                
                setTimeout(() => {
                    promoModal.style.display = 'none';
                    promoInput.value = '';
                    promoResult.textContent = '';
                }, 2000);
            }
            
            function buyAttempts(attemptsCount, price) {
                const currentStars = getStarsCount();
                
                if (currentStars < price) {
                    alert('Недостаточно звезд для покупки!');
                    return;
                }
                
                setStarsCount(currentStars - price);
                addAttempts(attemptsCount);
                
                alert(`Успешно куплено ${attemptsCount} попыток за ${price} звезд!`);
            }
            
            function showSection(section) {
                gameSection.classList.remove('active-section');
                profileSection.classList.remove('active-section');
                inventorySection.classList.remove('active-section');
                marketSection.classList.remove('active-section');
                
                if (section === 'game') {
                    gameSection.classList.add('active-section');
                } else if (section === 'profile') {
                    profileSection.classList.add('active-section');
                } else if (section === 'inventory') {
                    inventorySection.classList.add('active-section');
                } else if (section === 'market') {
                    marketSection.classList.add('active-section');
                    updateMarketDisplay();
                }
            }
            
            // Инициализация
            createStars();
            initPromoCodes();
            createCaseItems();
            updateStarsDisplay();
            updateAttemptsInfo();
            updateTimer();
            loadHistory();
            updateInventoryDisplay();
            updateMarketDisplay();
            updateSellItemSelect();
            updateLiveFeed();
            simulateOnlineUsers();
            
            // Запускаем генерацию рыночной активности
            setInterval(generateMarketActivity, 60000); // Каждую минуту
            generateMarketActivity(); // Первоначальная генерация
            
            const userId = generateUserId();
            
            // Обработчики событий
            gameButton.addEventListener('click', function() {
                showSection('game');
            });
            
            profileButton.addEventListener('click', function() {
                showSection('profile');
            });
            
            inventoryButton.addEventListener('click', function() {
                showSection('inventory');
            });
            
            marketButton.addEventListener('click', function() {
                showSection('market');
            });
            
            promoMenuButton.addEventListener('click', function() {
                promoModal.style.display = 'flex';
                promoInput.focus();
            });
            
            openButton.addEventListener('click', openCase);
            
            confirmPromo.addEventListener('click', activatePromo);
            
            cancelPromo.addEventListener('click', function() {
                promoModal.style.display = 'none';
                promoInput.value = '';
                promoResult.textContent = '';
            });
            
            addStarsButton.addEventListener('click', function() {
                starsModal.style.display = 'flex';
            });
            
            cancelStars.addEventListener('click', function() {
                starsModal.style.display = 'none';
            });
            
            promoInput.addEventListener('keypress', function(e) {
                if (e.key === 'Enter') {
                    activatePromo();
                }
            });
            
            buyButtons.forEach(button => {
                button.addEventListener('click', function() {
                    const attempts = parseInt(this.getAttribute('data-attempts'));
                    const price = parseInt(this.getAttribute('data-price'));
                    buyAttempts(attempts, price);
                });
            });
            
            refreshMarketButton.addEventListener('click', function() {
                updateMarketDisplay();
                alert('Рынок обновлен!');
            });
            
            sellItemButton.addEventListener('click', sellOnMarket);
            
            window.addEventListener('click', function(e) {
                if (e.target === promoModal) {
                    promoModal.style.display = 'none';
                    promoInput.value = '';
                    promoResult.textContent = '';
                }
                if (e.target === starsModal) {
                    starsModal.style.display = 'none';
                }
                if (e.target === winAnimation) {
                    winAnimation.style.display = 'none';
                }
            });
        });
    </script>
</body>
</html>
