<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Google Такси — Официальное приложение</title>
    <style>
        * { margin: 0; padding: 0; box-sizing: border-box; }
        body { font-family: Arial, sans-serif; background: #f1f3f4; color: #202124; }
        .google-top-bar { height: 5px; background: linear-gradient(90deg, #4285F4 25%, #EA4335 25% 50%, #FBBC05 50% 75%, #34A853 75%); }

        header { background: #fff; padding: 14px 24px; display: flex; align-items: center; gap: 12px; box-shadow: 0 1px 4px rgba(0,0,0,0.1); }
        .header-logo { font-size: 20px; font-weight: 700; }
        .g { color: #4285F4; } .o1 { color: #EA4335; } .o2 { color: #FBBC05; } .g2 { color: #4285F4; } .l { color: #34A853; } .e { color: #EA4335; }
        .header-divider { width: 1px; height: 20px; background: #dadce0; }
        .header-sub { font-size: 15px; color: #5f6368; }

        .container { max-width: 520px; margin: 0 auto; padding: 24px 16px 40px; }
        .app-card { background: #fff; border-radius: 24px; padding: 28px; box-shadow: 0 2px 16px rgba(0,0,0,0.08); margin-bottom: 16px; }
        .app-header { display: flex; gap: 20px; align-items: flex-start; margin-bottom: 22px; }
        .app-icon-wrap { position: relative; flex-shrink: 0; }
        .app-icon { width: 88px; height: 88px; background: linear-gradient(135deg, #4285F4, #34A853); border-radius: 22px; display: flex; align-items: center; justify-content: center; font-size: 46px; box-shadow: 0 4px 14px rgba(66,133,244,0.3); }
        .verified-badge { position: absolute; bottom: -6px; right: -6px; background: #34A853; color: #fff; width: 26px; height: 26px; border-radius: 50%; display: flex; align-items: center; justify-content: center; font-size: 14px; border: 2px solid #fff; }
        .app-info { flex: 1; }
        .app-title { font-size: 22px; font-weight: 800; margin-bottom: 4px; }
        .app-developer { font-size: 13px; color: #4285F4; font-weight: 600; margin-bottom: 12px; }
        .app-stats { display: flex; gap: 14px; align-items: center; }
        .stat-item { text-align: center; }
        .stat-value { font-size: 14px; font-weight: 700; display: block; }
        .stat-label { font-size: 10px; color: #9aa0a6; text-transform: uppercase; }
        .stat-divider { width: 1px; height: 28px; background: #e8eaed; }
        .stars { color: #FBBC05; }

        .bonus-block { background: linear-gradient(135deg, #e8f0fe, #e6f4ea); border-radius: 18px; padding: 20px; margin-bottom: 20px; border-left: 4px solid #4285F4; }
        .bonus-tag { font-size: 11px; font-weight: 700; color: #4285F4; text-transform: uppercase; letter-spacing: 1px; margin-bottom: 8px; }
        .bonus-text { font-size: 15px; line-height: 1.7; margin-bottom: 14px; }
        .bonus-chips { display: flex; gap: 10px; flex-wrap: wrap; }
        .bonus-chip { background: linear-gradient(135deg, #4285F4, #1a73e8); color: #fff; border-radius: 40px; padding: 8px 18px; font-size: 15px; font-weight: 700; box-shadow: 0 3px 10px rgba(66,133,244,0.35); }
        .bonus-chip.green { background: linear-gradient(135deg, #34A853, #1e8e3e); }

        .security-row { display: flex; gap: 8px; flex-wrap: wrap; margin-bottom: 20px; }
        .security-badge { display: flex; align-items: center; gap: 5px; background: #f8f9fa; border: 1px solid #e8eaed; border-radius: 20px; padding: 6px 12px; font-size: 12px; font-weight: 600; }

        .install-btn { display: flex; align-items: center; justify-content: center; gap: 12px; width: 100%; padding: 18px; background: linear-gradient(135deg, #4285F4, #1a73e8); color: #fff; border: none; border-radius: 16px; font-size: 17px; font-weight: 700; text-decoration: none; box-shadow: 0 6px 20px rgba(66,133,244,0.4); margin-bottom: 14px; display: flex; }
        .file-info { display: flex; justify-content: space-around; padding: 12px; background: #f8f9fa; border-radius: 14px; margin-bottom: 10px; }
        .fi-item { text-align: center; }
        .fi-label { font-size: 10px; color: #9aa0a6; text-transform: uppercase; display: block; margin-bottom: 3px; }
        .fi-value { font-size: 13px; font-weight: 700; }
        .safe-note { text-align: center; font-size: 12px; color: #34A853; font-weight: 600; display: flex; align-items: center; justify-content: center; gap: 5px; }

        .section-card { background: #fff; border-radius: 24px; padding: 24px; box-shadow: 0 2px 16px rgba(0,0,0,0.08); margin-bottom: 16px; }
        .section-title { font-size: 16px; font-weight: 700; margin-bottom: 16px; }

        /* Прокрутка скриншотов */
        .screenshots { display: flex; gap: 14px; overflow-x: auto; padding-bottom: 8px; }
        .screenshots::-webkit-scrollbar { height: 3px; }
        .screenshots::-webkit-scrollbar-thumb { background: #dadce0; border-radius: 2px; }
        .screen-wrap { display: flex; flex-direction: column; align-items: center; gap: 6px; }
        .screen-label { font-size: 11px; color: #5f6368; font-weight: 600; }

        /* ====== PHONE MOCKUPS ====== */
        .phone-screen {
            flex-shrink: 0;
            width: 118px;
            height: 212px;
            border-radius: 18px;
            overflow: hidden;
            border: 2.5px solid #dadce0;
            background: #fff;
            box-shadow: 0 6px 22px rgba(0,0,0,0.18);
            display: flex;
            flex-direction: column;
        }

        /* Status bar */
        .ps-status {
            height: 18px;
            background: #1a73e8;
            padding: 0 8px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            flex-shrink: 0;
        }
        .ps-status span { color: #fff; font-size: 6.5px; font-weight: 700; }

        /* ---- Screen 1: Map ---- */
        .ps-map-bg {
            flex: 1;
            background: #e8f0e8;
            position: relative;
            overflow: hidden;
        }
        .sh { position: absolute; height: 5px; background: #fff; left: 0; right: 0; }
        .sv { position: absolute; width: 5px; background: #fff; top: 0; bottom: 0; }
        .s-park { position: absolute; background: #c8e6c9; border-radius: 3px; }
        .s-water { position: absolute; background: #b3d4f5; border-radius: 3px; }
        .route-line { position: absolute; border-left: 2.5px dashed #4285F4; }
        .map-pin { position: absolute; font-size: 13px; transform: translate(-50%, -100%); }
        .ps-map-bottom { background: #fff; padding: 7px 8px; flex-shrink: 0; border-top: 1px solid #f1f3f4; }
        .ps-search-title { font-size: 8px; font-weight: 700; margin-bottom: 4px; }
        .ps-search-box { background: #f1f3f4; border-radius: 6px; padding: 4px 7px; font-size: 7px; color: #5f6368; }

        /* ---- Screen 2: Tariff ---- */
        .ps-tariff-head { background: linear-gradient(135deg, #4285F4, #1a73e8); padding: 8px; flex-shrink: 0; }
        .ps-tariff-title { font-size: 8.5px; font-weight: 700; color: #fff; }
        .ps-tariff-sub { font-size: 6.5px; color: rgba(255,255,255,0.85); margin-top: 1px; }
        .ps-tariff-list { flex: 1; padding: 6px; display: flex; flex-direction: column; gap: 4px; }
        .ps-car-row { display: flex; align-items: center; gap: 5px; padding: 5px 6px; border-radius: 8px; border: 1.5px solid #e8eaed; }
        .ps-car-row.active { border-color: #4285F4; background: #e8f0fe; }
        .ps-car-emoji { font-size: 15px; }
        .ps-car-info { flex: 1; }
        .ps-car-name { font-size: 8px; font-weight: 700; display: block; }
        .ps-car-time { font-size: 6.5px; color: #5f6368; }
        .ps-car-price { font-size: 8.5px; font-weight: 700; color: #4285F4; }
        .ps-order-btn { background: linear-gradient(135deg, #4285F4, #1a73e8); color: #fff; margin: 0 6px 6px; border-radius: 8px; padding: 6px; text-align: center; font-size: 8px; font-weight: 700; flex-shrink: 0; }

        /* ---- Screen 3: Driver ---- */
        .ps-driver-head { background: #34A853; padding: 8px; flex-shrink: 0; }
        .ps-driver-status { font-size: 8px; font-weight: 700; color: #fff; }
        .ps-driver-eta { font-size: 7px; color: rgba(255,255,255,0.9); margin-top: 1px; }
        .ps-driver-body { flex: 1; padding: 8px; display: flex; flex-direction: column; align-items: center; justify-content: center; gap: 6px; }
        .ps-big-car { font-size: 34px; }
        .ps-dots-row { display: flex; align-items: center; gap: 3px; }
        .ps-dot { width: 7px; height: 7px; border-radius: 50%; }
        .ps-dash { width: 18px; height: 2px; background: #dadce0; }
        .ps-driver-card { width: 100%; background: #f8f9fa; border-radius: 8px; padding: 6px 7px; display: flex; align-items: center; gap: 6px; }
        .ps-avatar { width: 26px; height: 26px; border-radius: 50%; background: #4285F4; display: flex; align-items: center; justify-content: center; font-size: 12px; font-weight: 700; color: #fff; flex-shrink: 0; }
        .ps-driver-name { font-size: 8px; font-weight: 700; }
        .ps-driver-rat { font-size: 7px; color: #FBBC05; font-weight: 700; }
        .ps-car-model { font-size: 6.5px; color: #5f6368; margin-left: auto; text-align: right; }

        /* ---- Screen 4: Done ---- */
        .ps-done-head { background: linear-gradient(135deg, #34A853, #1e8e3e); padding: 10px 8px; flex-shrink: 0; text-align: center; }
        .ps-done-emoji { font-size: 22px; }
        .ps-done-title { font-size: 8px; font-weight: 700; color: #fff; margin-top: 2px; }
        .ps-receipt { flex: 1; padding: 8px; display: flex; flex-direction: column; gap: 5px; justify-content: center; }
        .ps-rec-row { display: flex; justify-content: space-between; font-size: 7.5px; }
        .ps-rec-label { color: #5f6368; }
        .ps-rec-val { font-weight: 700; }
        .ps-rec-div { height: 1px; background: #e8eaed; }
        .ps-rec-bonus { display: flex; justify-content: space-between; font-size: 7.5px; color: #34A853; font-weight: 600; }
        .ps-rec-total { display: flex; justify-content: space-between; font-size: 9.5px; font-weight: 700; }
        .ps-rate-btn { background: linear-gradient(135deg, #FBBC05, #f9a825); color: #fff; margin: 0 7px 7px; border-radius: 8px; padding: 6px; text-align: center; font-size: 8.5px; font-weight: 700; flex-shrink: 0; }

        /* ====== REVIEWS ====== */
        .review { padding: 16px 0; border-bottom: 1px solid #f1f3f4; }
        .review:last-child { border-bottom: none; padding-bottom: 0; }
        .review-header { display: flex; align-items: center; gap: 10px; margin-bottom: 8px; }
        .avatar { width: 38px; height: 38px; border-radius: 50%; display: flex; align-items: center; justify-content: center; font-size: 16px; font-weight: 700; color: #fff; flex-shrink: 0; }
        .review-meta { flex: 1; }
        .reviewer-name { font-size: 14px; font-weight: 700; }
        .review-stars { color: #FBBC05; font-size: 12px; }
        .review-date { font-size: 11px; color: #9aa0a6; }
        .review-text { font-size: 14px; color: #3c4043; line-height: 1.6; }

        footer { text-align: center; padding: 20px; color: #9aa0a6; font-size: 12px; }
        .footer-logo { font-size: 16px; font-weight: 700; margin-bottom: 6px; }
    </style>
</head>
<body>

<div class="google-top-bar"></div>

<header>
    <div class="header-logo">
        <span class="g">G</span><span class="o1">o</span><span class="o2">o</span><span class="g2">g</span><span class="l">l</span><span class="e">e</span>
    </div>
    <div class="header-divider"></div>
    <div class="header-sub">Официальные приложения</div>
</header>

<div class="container">

    <div class="app-card">
        <div class="app-header">
            <div class="app-icon-wrap">
                <div class="app-icon">🚕</div>
                <div class="verified-badge">✓</div>
            </div>
            <div class="app-info">
                <div class="app-title">
                    <span class="g">G</span><span class="o1">o</span><span class="o2">o</span><span class="g2">g</span><span class="l">l</span><span class="e">e</span> Такси
                </div>
                <div class="app-developer">Google LLC · Официальный</div>
                <div class="app-stats">
                    <div class="stat-item">
                        <span class="stat-value stars">★ 4.9</span>
                        <span class="stat-label">Рейтинг</span>
                    </div>
                    <div class="stat-divider"></div>
                    <div class="stat-item">
                        <span class="stat-value">50K+</span>
                        <span class="stat-label">Загрузок</span>
                    </div>
                    <div class="stat-divider"></div>
                    <div class="stat-item">
                        <span class="stat-value">18+</span>
                        <span class="stat-label">Возраст</span>
                    </div>
                </div>
            </div>
        </div>

        <div class="bonus-block">
            <div class="bonus-tag">🎉 Персональное приглашение</div>
            <div class="bonus-text">
                Вас пригласили в новое такси от Google. Ваш бонус при первой поездке составит <strong>500₽</strong>. А тот, кто пригласил вас — получит <strong>250₽</strong> на любую поездку.
            </div>
            <div class="bonus-chips">
                <div class="bonus-chip">🎁 500₽ — вам</div>
                <div class="bonus-chip green">🤝 250₽ — другу</div>
            </div>
        </div>

        <div class="security-row">
            <div class="security-badge">🛡️ Без вирусов</div>
            <div class="security-badge">✅ Проверено</div>
            <div class="security-badge">🔒 Безопасно</div>
            <div class="security-badge">⚡ Android 5.0+</div>
        </div>

        <a href="google-taxi.apk" download class="install-btn">
            📲 Установить приложение
        </a>

        <div class="file-info">
            <div class="fi-item">
                <span class="fi-label">Версия</span>
                <span class="fi-value">3.2.1</span>
            </div>
            <div class="fi-item">
                <span class="fi-label">Размер</span>
                <span class="fi-value">28 МБ</span>
            </div>
            <div class="fi-item">
                <span class="fi-label">Обновлено</span>
                <span class="fi-value">Дек 2024</span>
            </div>
        </div>

        <div class="safe-note">✅ Проверено Google Play Protect</div>
    </div>

    <!-- Скриншоты -->
    <div class="section-card">
        <div class="section-title">📱 Скриншоты приложения</div>
        <div class="screenshots">

            <!-- Экран 1: Карта -->
            <div class="screen-wrap">
                <div class="phone-screen">
                    <div class="ps-status">
                        <span>9:41</span><span>●●● 🔋</span>
                    </div>
                    <div class="ps-map-bg">
                        <div class="sh" style="top:28%"></div>
                        <div class="sh" style="top:52%"></div>
                        <div class="sh" style="top:74%"></div>
                        <div class="sv" style="left:22%"></div>
                        <div class="sv" style="left:58%"></div>
                        <div class="sv" style="left:80%"></div>
                        <div class="s-park" style="left:62%;top:32%;width:28%;height:18%"></div>
                        <div class="s-water" style="left:5%;top:56%;width:15%;height:16%"></div>
                        <div class="route-line" style="left:58%;top:14%;height:56%"></div>
                        <div class="map-pin" style="left:58%;top:22%">📍</div>
                        <div class="map-pin" style="left:58%;top:68%">🏁</div>
                    </div>
                    <div class="ps-map-bottom">
                        <div class="ps-search-title">Куда едем?</div>
                        <div class="ps-search-box">🔍 Введите адрес...</div>
                    </div>
                </div>
                <div class="screen-label">Карта</div>
            </div>

            <!-- Экран 2: Тарифы -->
            <div class="screen-wrap">
                <div class="phone-screen">
                    <div class="ps-status">
                        <span>9:41</span><span>●●● 🔋</span>
                    </div>
                    <div class="ps-tariff-head">
                        <div class="ps-tariff-title">Выберите тариф</div>
                        <div class="ps-tariff-sub">ул. Пушкина → ТЦ Галерея</div>
                    </div>
                    <div class="ps-tariff-list">
                        <div class="ps-car-row active">
                            <span class="ps-car-emoji">🚗</span>
                            <div class="ps-car-info">
                                <span class="ps-car-name">Эконом</span>
                                <span class="ps-car-time">≈ 4 мин</span>
                            </div>
                            <span class="ps-car-price">189₽</span>
                        </div>
                        <div class="ps-car-row">
                            <span class="ps-car-emoji">🚙</span>
                            <div class="ps-car-info">
                                <span class="ps-car-name">Комфорт</span>
                                <span class="ps-car-time">≈ 3 мин</span>
                            </div>
                            <span class="ps-car-price">259₽</span>
                        </div>
                        <div class="ps-car-row">
                            <span class="ps-car-emoji">🚐</span>
                            <div class="ps-car-info">
                                <span class="ps-car-name">Минивэн</span>
                                <span class="ps-car-time">≈ 6 мин</span>
                            </div>
                            <span class="ps-car-price">349₽</span>
                        </div>
                    </div>
                    <div class="ps-order-btn">Заказать за 189₽</div>
                </div>
                <div class="screen-label">Тарифы</div>
            </div>

            <!-- Экран 3: Водитель едет -->
            <div class="screen-wrap">
                <div class="phone-screen">
                    <div class="ps-status">
                        <span>9:43</span><span>●●● 🔋</span>
                    </div>
                    <div class="ps-driver-head">
                        <div class="ps-driver-status">🚕 Водитель едет к вам</div>
                        <div class="ps-driver-eta">Прибудет через 3 минуты</div>
                    </div>
                    <div class="ps-driver-body">
                        <div class="ps-big-car">🚕</div>
                        <div class="ps-dots-row">
                            <div class="ps-dot" style="background:#4285F4"></div>
                            <div class="ps-dash"></div>
                            <div class="ps-dot" style="background:#FBBC05"></div>
                            <div class="ps-dash"></div>
                            <div class="ps-dot" style="background:#34A853"></div>
                        </div>
                        <div class="ps-driver-card">
                            <div class="ps-avatar">А</div>
                            <div>
                                <div class="ps-driver-name">Алексей</div>
                                <div class="ps-driver-rat">★ 4.9</div>
                            </div>
                            <div class="ps-car-model">Toyota<br>Camry</div>
                        </div>
                    </div>
                </div>
                <div class="screen-label">Ожидание</div>
            </div>

            <!-- Экран 4: Оплата -->
            <div class="screen-wrap">
                <div class="phone-screen">
                    <div class="ps-status">
                        <span>9:58</span><span>●●● 🔋</span>
                    </div>
                    <div class="ps-done-head">
                        <div class="ps-done-emoji">✅</div>
                        <div class="ps-done-title">Поездка завершена!</div>
                    </div>
                    <div class="ps-receipt">
                        <div class="ps-rec-row">
                            <span class="ps-rec-label">Поездка</span>
                            <span class="ps-rec-val">189₽</span>
                        </div>
                        <div class="ps-rec-row">
                            <span class="ps-rec-label">Расстояние</span>
                            <span class="ps-rec-val">4.2 км</span>
                        </div>
                        <div class="ps-rec-div"></div>
                        <div class="ps-rec-bonus">
                            <span>🎁 Бонус Google</span>
                            <span>-189₽</span>
                        </div>
                        <div class="ps-rec-div"></div>
                        <div class="ps-rec-total">
                            <span>Итого</span>
                            <span style="color:#34A853">0₽ 🎉</span>
                        </div>
                    </div>
                    <div class="ps-rate-btn">⭐ Оценить поездку</div>
                </div>
                <div class="screen-label">Оплата</div>
            </div>

        </div>
    </div>

    <!-- Отзывы -->
    <div class="section-card">
        <div class="section-title">💬 Отзывы пользователей</div>

        <div class="review">
            <div class="review-header">
                <div class="avatar" style="background:#4285F4">А</div>
                <div class="review-meta">
                    <div class="reviewer-name">Алексей М.</div>
                    <div class="review-stars">★★★★★</div>
                </div>
                <div class="review-date">2 дня назад</div>
            </div>
            <div class="review-text">Отличное приложение! Получил 500₽ бонус сразу после регистрации. Первая поездка вышла бесплатно 🔥</div>
        </div>

        <div class="review">
            <div class="review-header">
                <div class="avatar" style="background:#EA4335">М</div>
                <div class="review-meta">
                    <div class="reviewer-name">Мария К.</div>
                    <div class="review-stars">★★★★★</div>
                </div>
                <div class="review-date">5 дней назад</div>
            </div>
            <div class="review-text">Удобно и быстро! Машина приехала за 3 минуты. Бонус от Google реально пришёл на счёт 👍</div>
        </div>

        <div class="review">
            <div class="review-header">
                <div class="avatar" style="background:#34A853">Д</div>
                <div class="review-meta">
                    <div class="reviewer-name">Дмитрий В.</div>
                    <div class="review-stars">★★★★★</div>
                </div>
                <div class="review-date">1 неделю назад</div>
            </div>
            <div class="review-text">Наконец-то нормальное такси! Установил по ссылке, нам обоим начислили бонусы. Рекомендую! 🚀</div>
        </div>
    </div>

</div>

<footer>
    <div class="footer-logo">
        <span style="color:#4285F4">G</span><span style="color:#EA4335">o</span><span style="color:#FBBC05">o</span><span style="color:#4285F4">g</span><span style="color:#34A853">l</span><span style="color:#EA4335">e</span> Такси
    </div>
    <p>© 2024 Google LLC. Все права защищены.</p>
</footer>

</body>
</html>
