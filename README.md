[index.html](https://github.com/user-attachments/files/34522523/index.html)
<!DOCTYPE html>
<html lang="zh-Hant">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>2027 SoloTrip｜一個人的旅行</title>

    <style>
        :root {
            --primary: #416b62;
            --secondary: #e9f0eb;
            --bg: #f6f7f3;
            --text: #26352f;
            --muted: #829089;
            --white: #ffffff;
            --border: #e5eae5;
            --orange: #e9a36e;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }

        body {
            font-family: "Noto Sans TC", sans-serif;
            background: var(--bg);
            color: var(--text);
        }

        button,
        input,
        select,
        textarea {
            font: inherit;
        }

        button {
            cursor: pointer;
        }

        .layout {
            display: flex;
            min-height: 100vh;
        }

        .sidebar {
            width: 245px;
            background: white;
            padding: 28px 18px;
            position: fixed;
            height: 100vh;
            border-right: 1px solid var(--border);
            z-index: 10;
        }

        .logo {
            font-size: 22px;
            font-weight: 900;
            color: var(--primary);
            padding: 5px 12px;
        }

        .logo small {
            display: block;
            font-size: 10px;
            letter-spacing: 3px;
            color: var(--muted);
            margin-top: 5px;
        }

        .nav-title {
            font-size: 11px;
            color: #a3ada7;
            margin: 35px 12px 12px;
            letter-spacing: 2px;
        }

        .nav-btn {
            width: 100%;
            padding: 13px 14px;
            border: none;
            background: transparent;
            text-align: left;
            border-radius: 10px;
            color: #6e7b73;
            margin-bottom: 5px;
            transition: .2s;
        }

        .nav-btn:hover,
        .nav-btn.active {
            background: var(--secondary);
            color: var(--primary);
            font-weight: bold;
        }

        .sidebar-bottom {
            position: absolute;
            bottom: 25px;
            left: 22px;
            right: 22px;
            font-size: 12px;
            color: var(--muted);
            line-height: 2;
        }

        .main {
            margin-left: 245px;
            width: calc(100% - 245px);
            padding: 32px 5%;
            max-width: 1600px;
        }

        .topbar {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 30px;
            gap: 12px;
        }

        .topbar h2 {
            font-size: 23px;
        }

        .topbar p {
            font-size: 12px;
            color: var(--muted);
            margin-top: 5px;
        }

        .year-tag {
            background: white;
            padding: 10px 17px;
            border-radius: 30px;
            color: var(--primary);
            font-weight: bold;
            font-size: 13px;
        }

        .page {
            display: none;
        }

        .page.active {
            display: block;
        }

        .hero {
            min-height: 260px;
            padding: 42px;
            border-radius: 22px;
            background: linear-gradient(120deg, #355d51, #789c86);
            color: white;
            display: flex;
            flex-direction: column;
            justify-content: center;
            position: relative;
            overflow: hidden;
        }

        .hero::after {
            content: "✈";
            position: absolute;
            right: 8%;
            top: 35px;
            font-size: 125px;
            opacity: .13;
            transform: rotate(-15deg);
        }

        .hero small {
            letter-spacing: 3px;
            color: #d4e4d9;
        }

        .hero h1 {
            font-size: clamp(28px, 5vw, 44px);
            margin: 16px 0;
        }

        .hero p {
            line-height: 1.8;
            color: #e1eee6;
            max-width: 480px;
            font-size: 14px;
        }

        .hero button {
            width: fit-content;
            margin-top: 24px;
            background: white;
            color: var(--primary);
            border: none;
            border-radius: 9px;
            padding: 12px 22px;
            font-weight: bold;
        }

        .stats {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 15px;
            margin: 22px 0;
        }

        .stat,
        .card {
            background: white;
            border-radius: 15px;
            padding: 22px;
            border: 1px solid var(--border);
        }

        .stat span {
            color: var(--muted);
            font-size: 13px;
        }

        .stat h2 {
            font-size: 27px;
            margin-top: 12px;
            color: var(--primary);
        }

        .section-title {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin: 32px 0 17px;
            gap: 10px;
        }

        .section-title h3 {
            font-size: 19px;
        }

        .grid {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 17px;
        }

        .card h3 {
            margin-bottom: 15px;
        }

        .card p {
            font-size: 13px;
            color: var(--muted);
            line-height: 1.8;
        }

        .btn {
            background: var(--primary);
            color: white;
            padding: 11px 18px;
            border: none;
            border-radius: 9px;
            font-weight: bold;
        }

        .btn-light {
            background: var(--secondary);
            color: var(--primary);
            padding: 10px 15px;
            border: none;
            border-radius: 9px;
        }

        .form-grid {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 17px;
        }

        .field {
            margin-bottom: 17px;
        }

        .field label {
            display: block;
            font-size: 13px;
            font-weight: bold;
            margin-bottom: 8px;
        }

        .field input,
        .field select,
        .field textarea {
            width: 100%;
            padding: 12px;
            border: 1px solid var(--border);
            border-radius: 9px;
            outline: none;
            background: white;
            color: var(--text);
        }

        .field input:focus,
        .field textarea:focus {
            border-color: var(--primary);
        }

        .field textarea {
            resize: vertical;
            min-height: 90px;
        }

        .full {
            grid-column: 1 / -1;
        }

        .trip-item {
            background: white;
            padding: 20px;
            border-radius: 13px;
            margin-bottom: 12px;
            border: 1px solid var(--border);
        }

        .trip-item h3 {
            margin-bottom: 8px;
        }

        .trip-item p {
            color: var(--muted);
            font-size: 13px;
            line-height: 1.9;
        }

        .trip-actions {
            display: flex;
            gap: 8px;
            margin-top: 13px;
            flex-wrap: wrap;
        }

        .day-card {
            background: white;
            padding: 20px;
            border-radius: 13px;
            border-left: 4px solid var(--primary);
            margin-bottom: 13px;
        }

        .day-card h3 {
            margin-bottom: 10px;
        }

        .day-card input {
            width: 100%;
            border: 1px solid var(--border);
            padding: 10px;
            border-radius: 8px;
            margin: 5px 0;
        }

        .check-item {
            display: flex;
            align-items: center;
            gap: 12px;
            padding: 14px;
            border-bottom: 1px solid var(--border);
            font-size: 14px;
        }

        .check-item input {
            accent-color: var(--primary);
            width: 17px;
            height: 17px;
        }

        .check-item.done span {
            text-decoration: line-through;
            color: #9da69f;
        }

        .progress {
            background: #e9eee9;
            height: 9px;
            border-radius: 10px;
            margin: 15px 0;
            overflow: hidden;
        }

        .progress div {
            height: 100%;
            background: var(--primary);
            width: 0;
            transition: .3s;
        }

        .budget-number {
            font-size: 30px;
            font-weight: bold;
            color: var(--primary);
            margin: 15px 0;
        }

        .budget-row {
            display: flex;
            justify-content: space-between;
            padding: 13px 0;
            border-bottom: 1px solid var(--border);
            font-size: 14px;
        }

        .diary {
            width: 100%;
            min-height: 130px;
            padding: 14px;
            border: 1px solid var(--border);
            border-radius: 10px;
        }

        .mobile-menu {
            display: none;
        }

        .empty {
            padding: 30px;
            text-align: center;
            color: var(--muted);
            background: white;
            border-radius: 13px;
        }

        footer {
            text-align: center;
            margin-top: 45px;
            color: var(--muted);
            font-size: 12px;
            line-height: 2;
        }

        @media(max-width:850px) {
            .sidebar {
                width: 210px;
            }

            .main {
                margin-left: 210px;
                width: calc(100% - 210px);
                padding: 25px;
            }
        }

        @media(max-width:650px) {
            .sidebar {
                display: none;
                width: 250px;
                box-shadow: 5px 0 25px #0002;
            }

            .sidebar.open {
                display: block;
            }

            .main {
                margin-left: 0;
                width: 100%;
                padding: 18px;
            }

            .mobile-menu {
                display: block;
                border: none;
                background: white;
                padding: 9px 13px;
                border-radius: 8px;
            }

            .stats {
                grid-template-columns: 1fr;
            }

            .grid,
            .form-grid {
                grid-template-columns: 1fr;
            }

            .hero {
                padding: 28px;
                min-height: 250px;
            }

            .hero::after {
                right: 0;
                font-size: 85px;
            }

            .topbar h2 {
                font-size: 19px;
            }
        }
    </style>
</head>

<body>

    <div class="layout">

        <aside class="sidebar" id="sidebar">
            <div class="logo">
                SoloTrip.
                <small>YOUR OWN JOURNEY · 2027</small>
            </div>

            <div class="nav-title">TRAVEL MENU</div>

            <button class="nav-btn active" onclick="showPage('home',this)">⌂　旅行首頁</button>
            <button class="nav-btn" onclick="showPage('create',this)">＋　建立旅行</button>
            <button class="nav-btn" onclick="showPage('trips',this)">▤　我的旅行</button>
            <button class="nav-btn" onclick="showPage('itinerary',this)">◎　每日行程</button>
            <button class="nav-btn" onclick="showPage('budget',this)">＄　預算管理</button>
            <button class="nav-btn" onclick="showPage('checklist',this)">✓　行李清單</button>
            <button class="nav-btn" onclick="showPage('safety',this)">♡　安全中心</button>
            <button class="nav-btn" onclick="showPage('diary',this)">✎　旅行日記</button>

            <div class="sidebar-bottom">
                SOLOTRIP 2027<br>
                一個人的旅行，也可以很精彩。
            </div>
        </aside>

        <main class="main">

            <header class="topbar">
                <div>
                    <button class="mobile-menu" onclick="toggleMenu()">☰</button>
                    <h2 id="pageTitle">旅行首頁</h2>
                    <p id="today"></p>
                </div>
                <div class="year-tag">✈ 2027 SOLO TRAVEL</div>
            </header>

            <!-- 首頁 -->
            <section class="page active" id="home">

                <div class="hero">
                    <small>2027 · SOLO TRAVEL JOURNEY</small>
                    <h1>一個人的旅行，<br>探索更大的世界。</h1>
                    <p>
                        不必等待別人，不必配合誰的時間。
                        安排自己的旅程，走向想去的地方。
                    </p>
                    <button onclick="showPage('create')">＋ 開始規劃旅行</button>
                </div>

                <div class="stats">
                    <div class="stat">
                        <span>我的旅行計畫</span>
                        <h2 id="tripCount">0</h2>
                    </div>
                    <div class="stat">
                        <span>預計旅行天數</span>
                        <h2 id="totalDays">0</h2>
                    </div>
                    <div class="stat">
                        <span>旅行總預算</span>
                        <h2 id="totalBudget">NT$0</h2>
                    </div>
                </div>

                <div class="section-title">
                    <h3>我的旅行計畫</h3>
                    <button class="btn-light" onclick="showPage('trips')">查看全部 →</button>
                </div>

                <div id="homeTrips"></div>

                <div class="section-title">
                    <h3>一個人旅行的小提醒</h3>
                </div>

                <div class="grid">
                    <div class="card">
                        <h3>✈ 出發前</h3>
                        <p>確認交通、住宿、旅遊保險及重要證件。</p>
                    </div>
                    <div class="card">
                        <h3>📍 旅途中</h3>
                        <p>注意周遭環境，適時向可信任的人分享行程。</p>
                    </div>
                </div>

            </section>

            <!-- 建立旅行 -->
            <section class="page" id="create">

                <div class="card">
                    <h3>建立專屬旅行計畫</h3>
                    <p>填寫以下資訊，開始規劃 2027 年的旅行。</p>

                    <form id="tripForm" style="margin-top:25px">

                        <div class="form-grid">

                            <div class="field">
                                <label>旅行名稱</label>
                                <input id="tripName" placeholder="例如：2027 一個人的東京旅行" required>
                            </div>

                            <div class="field">
                                <label>旅行目的地</label>
                                <input id="destination" placeholder="例如：日本東京" required>
                            </div>

                            <div class="field">
                                <label>出發日期</label>
                                <input type="date" id="startDate" min="2027-01-01" max="2027-12-31" required>
                            </div>

                            <div class="field">
                                <label>回程日期</label>
                                <input type="date" id="endDate" min="2027-01-01" max="2027-12-31" required>
                            </div>

                            <div class="field">
                                <label>旅行人數</label>
                                <select id="people">
                                    <option value="1">1 人（獨自旅行）</option>
                                </select>
                            </div>

                            <div class="field">
                                <label>旅行方式</label>
                                <select id="travelType">
                                    <option>自由行</option>
                                    <option>城市探索</option>
                                    <option>自然景觀</option>
                                    <option>美食旅行</option>
                                    <option>文化體驗</option>
                                    <option>放鬆度假</option>
                                </select>
                            </div>

                            <div class="field">
                                <label>預計總預算（新台幣）</label>
                                <input type="number" id="budget" min="0" placeholder="例如：30000" required>
                            </div>

                            <div class="field">
                                <label>旅行備註</label>
                                <input id="note" placeholder="例如：想去迪士尼、吃美食">
                            </div>

                        </div>

                        <button class="btn" type="submit">建立我的旅行 →</button>

                    </form>
                </div>

            </section>

            <!-- 我的旅行 -->
            <section class="page" id="trips">

                <div class="section-title">
                    <h3>我的旅行清單</h3>
                    <button class="btn" onclick="showPage('create')">＋ 新增旅行</button>
                </div>

                <div id="tripList"></div>

            </section>

            <!-- 每日行程 -->
            <section class="page" id="itinerary">

                <div class="card">
                    <h3>每日旅行行程</h3>
                    <div class="field" style="margin-top:18px">
                        <label>選擇旅行</label>
                        <select id="itineraryTrip" onchange="renderItinerary()"></select>
                    </div>
                    <p>你可以自由編輯每一天的行程安排。</p>
                </div>

                <div class="section-title">
                    <h3>每日安排</h3>
                    <button class="btn-light" onclick="generateItinerary()">重新產生天數</button>
                </div>

                <div id="itineraryList"></div>

            </section>

            <!-- 預算 -->
            <section class="page" id="budget">

                <div class="card">
                    <h3>旅行預算管理</h3>

                    <div class="field" style="margin-top:20px">
                        <label>選擇旅行</label>
                        <select id="budgetTrip" onchange="renderBudget()"></select>
                    </div>

                    <p>預計旅行預算</p>
                    <div class="budget-number" id="budgetLimit">NT$0</div>

                    <p>目前已記錄支出</p>
                    <div class="budget-number" id="budgetSpent">NT$0</div>

                    <div class="progress">
                        <div id="budgetProgress"></div>
                    </div>

                    <p id="budgetMessage">尚未建立預算紀錄。</p>
                </div>

                <div class="card" style="margin-top:18px">
                    <h3>新增旅行支出</h3>

                    <form id="expenseForm" style="margin-top:18px">
                        <div class="form-grid">
                            <div class="field">
                                <label>支出項目</label>
                                <input id="expenseName" placeholder="例如：住宿費" required>
                            </div>
                            <div class="field">
                                <label>支出金額（NT$）</label>
                                <input type="number" id="expenseAmount" min="1" required>
                            </div>
                            <div class="field full">
                                <label>支出類別</label>
                                <select id="expenseCategory">
                                    <option>交通</option>
                                    <option>住宿</option>
                                    <option>飲食</option>
                                    <option>景點門票</option>
                                    <option>購物</option>
                                    <option>其他</option>
                                </select>
                            </div>
                        </div>
                        <button class="btn">新增支出</button>
                    </form>
                </div>

                <div class="card" style="margin-top:18px">
                    <h3>支出明細</h3>
                    <div id="expenseList"></div>
                </div>

            </section>

            <!-- 行李清單 -->
            <section class="page" id="checklist">

                <div class="card">
                    <h3>旅行行李準備清單</h3>
                    <p>出發前確認自己的物品是否準備完成。</p>

                    <div class="progress">
                        <div id="checkProgress"></div>
                    </div>

                    <p id="checkCount"></p>

                    <div id="checkList"></div>

                    <div style="display:flex;gap:8px;margin-top:20px">
                        <input id="newCheck" placeholder="新增自訂物品"
                            style="flex:1;min-width:0;padding:12px;border:1px solid var(--border);border-radius:9px">
                        <button class="btn" onclick="addCheck()">新增</button>
                    </div>

                </div>

            </section>

            <!-- 安全中心 -->
            <section class="page" id="safety">

                <div class="card">
                    <h3>一個人旅行安全中心</h3>
                    <p>出發前先準備好重要聯絡資訊。</p>

                    <form id="safetyForm" style="margin-top:22px">

                        <div class="field">
                            <label>緊急聯絡人姓名</label>
                            <input id="emergencyName" placeholder="聯絡人姓名">
                        </div>

                        <div class="field">
                            <label>緊急聯絡電話</label>
                            <input id="emergencyPhone" type="tel" placeholder="聯絡電話">
                        </div>

                        <div class="field">
                            <label>住宿地址</label>
                            <textarea id="hotelAddress" placeholder="填寫住宿名稱與地址"></textarea>
                        </div>

                        <div class="field">
                            <label>其他重要資訊</label>
                            <textarea id="safetyNote" placeholder="例如：保險資訊、重要提醒"></textarea>
                        </div>

                        <button class="btn">儲存安全資訊</button>

                    </form>
                </div>

                <div class="card" style="margin-top:18px">
                    <h3>出發前安全檢查</h3>
                    <div class="check-item">✓ 將旅行計畫分享給可信任的人</div>
                    <div class="check-item">✓ 確認住宿及交通資訊</div>
                    <div class="check-item">✓ 確認旅遊保險及證件</div>
                    <div class="check-item">✓ 記下當地緊急求助電話</div>
                    <div class="check-item">✓ 準備備用聯絡方式及緊急資金</div>
                </div>

            </section>

            <!-- 旅行日記 -->
            <section class="page" id="diary">

                <div class="card">
                    <h3>我的旅行日記</h3>
                    <p>記錄旅途中值得珍藏的回憶。</p>

                    <form id="diaryForm" style="margin-top:20px">
                        <div class="field">
                            <label>選擇旅行</label>
                            <select id="diaryTrip"></select>
                        </div>

                        <div class="field">
                            <label>日記日期</label>
                            <input type="date" id="diaryDate" required>
                        </div>

                        <div class="field">
                            <label>今天的心情</label>
                            <select id="diaryMood">
                                <option>😊 開心</option>
                                <option>🥰 感動</option>
                                <option>😌 放鬆</option>
                                <option>😎 興奮</option>
                                <option>😴 疲憊</option>
                            </select>
                        </div>

                        <div class="field">
                            <label>今天的旅行故事</label>
                            <textarea id="diaryContent" class="diary" placeholder="今天去了哪裡？看見了什麼？有什麼特別的回憶？"
                                required></textarea>
                        </div>

                        <button class="btn">儲存旅行日記</button>
                    </form>
                </div>

                <div class="section-title">
                    <h3>旅行回憶</h3>
                </div>

                <div id="diaryList"></div>

            </section>

            <footer>
                SOLOTRIP © 2027<br>
                TRAVEL ALONE · DISCOVER YOURSELF<br>
                一個人的旅行，也是一場認識自己的旅程。
            </footer>

        </main>
    </div>

    <script>
        const KEY = "solotrip_2027_data";

        let data = JSON.parse(localStorage.getItem(KEY) || "{}");

        data.trips ||= [];
        data.expenses ||= {};
        data.itineraries ||= {};
        data.diaries ||= [];
        data.checks ||= [
            "身分證 / 護照",
            "機票 / 車票",
            "住宿確認資料",
            "手機及充電器",
            "行動電源",
            "錢包及現金",
            "信用卡",
            "換洗衣物",
            "個人盥洗用品",
            "常備用品",
            "耳機",
            "旅遊保險資料"
        ];
        data.checked ||= [];
        data.safety ||= {};

        function save() {
            localStorage.setItem(KEY, JSON.stringify(data));
            renderHome();
        }

        function money(n) {
            return "NT$" + Number(n || 0).toLocaleString("zh-TW");
        }

        function dateDays(a, b) {
            const start = new Date(a + "T00:00:00");
            const end = new Date(b + "T00:00:00");
            return Math.round((end - start) / 86400000) + 1;
        }

        function showPage(id, btn) {
            document.querySelectorAll(".page").forEach(p => p.classList.remove("active"));
            document.getElementById(id).classList.add("active");

            document.querySelectorAll(".nav-btn").forEach(b => b.classList.remove("active"));
            if (btn) btn.classList.add("active");
            else {
                const target = [...document.querySelectorAll(".nav-btn")]
                    .find(b => b.getAttribute("onclick")?.includes("'" + id + "'"));
                if (target) target.classList.add("active");
            }

            const titles = {
                home: "旅行首頁",
                create: "建立旅行",
                trips: "我的旅行",
                itinerary: "每日行程",
                budget: "預算管理",
                checklist: "行李清單",
                safety: "安全中心",
                diary: "旅行日記"
            };

            document.getElementById("pageTitle").textContent = titles[id];
            document.getElementById("sidebar").classList.remove("open");

            if (id === "home") renderHome();
            if (id === "trips") renderTrips();
            if (id === "itinerary") refreshSelects("itineraryTrip");
            if (id === "budget") {
                refreshSelects("budgetTrip");
                renderBudget();
            }
            if (id === "checklist") renderChecks();
            if (id === "diary") {
                refreshSelects("diaryTrip");
                renderDiaries();
            }
            if (id === "safety") loadSafety();
        }

        function toggleMenu() {
            document.getElementById("sidebar").classList.toggle("open");
        }

        document.getElementById("today").textContent =
            new Date().toLocaleDateString("zh-TW", {
                year: "numeric", month: "long", day: "numeric"
            });

        // 建立旅行
        document.getElementById("tripForm").addEventListener("submit", e => {
            e.preventDefault();

            const start = document.getElementById("startDate").value;
            const end = document.getElementById("endDate").value;

            if (start > end) {
                alert("回程日期不能早於出發日期！");
                return;
            }

            if (!start.startsWith("2027-") || !end.startsWith("2027-")) {
                alert("請選擇 2027 年的旅行日期！");
                return;
            }

            const trip = {
                id: Date.now(),
                name: tripName.value,
                destination: destination.value,
                start,
                end,
                people: 1,
                type: travelType.value,
                budget: Number(budget.value),
                note: note.value
            };

            data.trips.push(trip);
            data.expenses[trip.id] = [];
            data.itineraries[trip.id] = [];

            save();
            e.target.reset();

            alert("旅行計畫建立成功！");
            showPage("trips");
        });

        // 選單
        function refreshSelects(id) {
            const select = document.getElementById(id);
            const old = select.value;

            select.innerHTML = "";

            data.trips.forEach(t => {
                const option = document.createElement("option");
                option.value = t.id;
                option.textContent = t.name;
                select.appendChild(option);
            });

            if (data.trips.some(t => String(t.id) === old))
                select.value = old;
        }

        // 首頁
        function renderHome() {
            const trips = data.trips;

            document.getElementById("tripCount").textContent = trips.length;

            document.getElementById("totalDays").textContent =
                trips.reduce((s, t) => s + Math.max(0, dateDays(t.start, t.end)), 0);

            document.getElementById("totalBudget").textContent =
                money(trips.reduce((s, t) => s + t.budget, 0));

            const el = document.getElementById("homeTrips");

            if (!trips.length) {
                el.innerHTML = '<div class="empty">還沒有旅行計畫，開始建立你的第一趟旅程吧！</div>';
                return;
            }

            el.innerHTML = trips.slice(-3).reverse().map(t => `
    <div class="trip-item">
      <h3>✈ ${escapeHTML(t.name)}</h3>
      <p>📍 ${escapeHTML(t.destination)}</p>
      <p>📅 ${t.start} ～ ${t.end}</p>
      <p>💰 預算：${money(t.budget)}</p>
    </div>
  `).join("");
        }

        // 我的旅行
        function renderTrips() {
            const el = document.getElementById("tripList");

            if (!data.trips.length) {
                el.innerHTML = '<div class="empty">目前沒有旅行計畫。</div>';
                return;
            }

            el.innerHTML = data.trips.map(t => `
    <div class="trip-item">
      <h3>✈ ${escapeHTML(t.name)}</h3>
      <p>目的地：${escapeHTML(t.destination)}</p>
      <p>日期：${t.start} ～ ${t.end}</p>
      <p>天數：${Math.max(0, dateDays(t.start, t.end))} 天</p>
      <p>旅行方式：${escapeHTML(t.type)}</p>
      <p>預算：${money(t.budget)}</p>
      <p>備註：${escapeHTML(t.note || "無")}</p>

      <div class="trip-actions">
        <button class="btn-light" onclick="openTrip(${t.id},'itinerary')">查看行程</button>
        <button class="btn-light" onclick="exportTrip(${t.id})">匯出計畫</button>
        <button class="btn-light" onclick="deleteTrip(${t.id})">刪除旅行</button>
      </div>
    </div>
  `).join("");
        }

        function openTrip(id, page) {
            showPage(page);
            const select = document.getElementById(
                page === "itinerary" ? "itineraryTrip" : "budgetTrip"
            );
            select.value = id;
            if (page === "itinerary") renderItinerary();
            else renderBudget();
        }

        function deleteTrip(id) {
            if (!confirm("確定刪除這趟旅行及相關紀錄嗎？")) return;

            data.trips = data.trips.filter(t => t.id !== id);
            delete data.expenses[id];
            delete data.itineraries[id];
            data.diaries = data.diaries.filter(d => d.tripId !== id);

            save();
            renderTrips();
        }

        // 每日行程
        function generateItinerary() {
            const id = document.getElementById("itineraryTrip").value;
            const trip = data.trips.find(t => String(t.id) === id);
            if (!trip) return alert("請先建立旅行！");

            if (!confirm("重新產生行程會覆蓋目前這趟旅行的每日安排，確定嗎？")) return;

            const days = Math.max(1, dateDays(trip.start, trip.end));

            data.itineraries[id] = Array.from({ length: days }, (_, i) => ({
                date: new Date(new Date(trip.start + "T00:00:00").getTime() + i * 86400000)
                    .toISOString().slice(0, 10),
                morning: "",
                afternoon: "",
                evening: "",
                transport: "",
                note: ""
            }));

            save();
            renderItinerary();
        }

        function renderItinerary() {
            const id = document.getElementById("itineraryTrip").value;
            const list = data.itineraries[id] || [];
            const el = document.getElementById("itineraryList");

            if (!id || !list.length) {
                el.innerHTML = '<div class="empty">請選擇旅行，並按下「重新產生天數」建立行程。</div>';
                return;
            }

            el.innerHTML = list.map((d, i) => `
    <div class="day-card">
      <h3>DAY ${i + 1} · ${d.date}</h3>

      <div class="field">
        <label>☀️ 上午行程</label>
        <input value="${escapeAttr(d.morning)}"
          onchange="updateDay('${id}',${i},'morning',this.value)"
          placeholder="例如：參觀博物館">
      </div>

      <div class="field">
        <label>🌤 下午行程</label>
        <input value="${escapeAttr(d.afternoon)}"
          onchange="updateDay('${id}',${i},'afternoon',this.value)"
          placeholder="例如：逛街、拍照">
      </div>

      <div class="field">
        <label>🌙 晚上行程</label>
        <input value="${escapeAttr(d.evening)}"
          onchange="updateDay('${id}',${i},'evening',this.value)"
          placeholder="例如：品嚐當地美食">
      </div>

      <div class="field">
        <label>🚆 交通方式</label>
        <input value="${escapeAttr(d.transport)}"
          onchange="updateDay('${id}',${i},'transport',this.value)"
          placeholder="例如：地鐵、步行">
      </div>

      <div class="field">
        <label>備註</label>
        <input value="${escapeAttr(d.note)}"
          onchange="updateDay('${id}',${i},'note',this.value)"
          placeholder="其他注意事項">
      </div>
    </div>
  `).join("");
        }

        function updateDay(id, index, key, value) {
            data.itineraries[id][index][key] = value;
            save();
        }

        // 預算
        function renderBudget() {
            const id = document.getElementById("budgetTrip").value;
            const trip = data.trips.find(t => String(t.id) === id);

            if (!trip) {
                budgetLimit.textContent = money(0);
                budgetSpent.textContent = money(0);
                expenseList.innerHTML = '<div class="empty">請先建立旅行。</div>';
                return;
            }

            const expenses = data.expenses[id] || [];
            const total = expenses.reduce((s, e) => s + e.amount, 0);
            const percent = trip.budget ? Math.min(total / trip.budget * 100, 100) : 0;

            budgetLimit.textContent = money(trip.budget);
            budgetSpent.textContent = money(total);
            budgetProgress.style.width = percent + "%";

            budgetMessage.textContent = trip.budget === 0
                ? "尚未設定預算。"
                : total > trip.budget
                    ? "⚠ 已超出預算 " + money(total - trip.budget)
                    : "目前剩餘預算 " + money(trip.budget - total);

            expenseList.innerHTML = expenses.length ? expenses.map((e, i) => `
    <div class="budget-row">
      <span>${escapeHTML(e.name)} · ${escapeHTML(e.category)}</span>
      <span>${money(e.amount)}
      <button class="btn-light" onclick="deleteExpense('${id}',${i})">✕</button></span>
    </div>
  `).join("") : '<div class="empty">尚無支出紀錄。</div>';
        }

        document.getElementById("expenseForm").addEventListener("submit", e => {
            e.preventDefault();

            const id = document.getElementById("budgetTrip").value;
            if (!id) return alert("請先建立旅行！");

            data.expenses[id] ||= [];
            data.expenses[id].push({
                name: expenseName.value,
                amount: Number(expenseAmount.value),
                category: expenseCategory.value
            });

            save();
            e.target.reset();
            renderBudget();
        });

        function deleteExpense(id, i) {
            data.expenses[id].splice(i, 1);
            save();
            renderBudget();
        }

        // 行李清單
        function renderChecks() {
            const el = document.getElementById("checkList");

            el.innerHTML = data.checks.map((item, i) => `
    <label class="check-item ${data.checked.includes(i) ? "done" : ""}">
      <input type="checkbox" ${data.checked.includes(i) ? "checked" : ""}
        onchange="toggleCheck(${i},this.checked)">
      <span>${escapeHTML(item)}</span>
      <button type="button" class="btn-light"
        onclick="removeCheck(${i})">刪除</button>
    </label>
  `).join("");

            const done = data.checked.length;
            const percent = data.checks.length ? done / data.checks.length * 100 : 0;

            checkProgress.style.width = percent + "%";
            checkCount.textContent = `已完成 ${done} / ${data.checks.length} 項`;
        }

        function toggleCheck(i, checked) {
            if (checked && !data.checked.includes(i)) data.checked.push(i);
            if (!checked) data.checked = data.checked.filter(x => x !== i);
            save();
            renderChecks();
        }

        function addCheck() {
            const value = newCheck.value.trim();
            if (!value) return;

            data.checks.push(value);
            newCheck.value = "";
            save();
            renderChecks();
        }

        function removeCheck(i) {
            data.checks.splice(i, 1);
            data.checked = data.checked
                .filter(x => x !== i)
                .map(x => x > i ? x - 1 : x);

            save();
            renderChecks();
        }

        // 安全中心
        function loadSafety() {
            emergencyName.value = data.safety.name || "";
            emergencyPhone.value = data.safety.phone || "";
            hotelAddress.value = data.safety.address || "";
            safetyNote.value = data.safety.note || "";
        }

        document.getElementById("safetyForm").addEventListener("submit", e => {
            e.preventDefault();

            data.safety = {
                name: emergencyName.value,
                phone: emergencyPhone.value,
                address: hotelAddress.value,
                note: safetyNote.value
            };

            save();
            alert("安全資訊已儲存！");
        });

        // 日記
        document.getElementById("diaryForm").addEventListener("submit", e => {
            e.preventDefault();

            const id = document.getElementById("diaryTrip").value;
            if (!id) return alert("請先建立旅行！");

            data.diaries.push({
                id: Date.now(),
                tripId: id,
                date: diaryDate.value,
                mood: diaryMood.value,
                content: diaryContent.value
            });

            save();
            e.target.reset();
            renderDiaries();
            alert("旅行日記已儲存！");
        });

        function renderDiaries() {
            const el = document.getElementById("diaryList");

            const list = data.diaries.slice().reverse();

            el.innerHTML = list.length ? list.map(d => `
    <div class="trip-item">
      <p>${d.date} · ${escapeHTML(d.mood)}</p>
      <p>${escapeHTML(data.trips.find(t => String(t.id) === String(d.tripId))?.name || "已刪除的旅行")}</p>
      <h3 style="margin-top:12px">旅行回憶</h3>
      <p>${escapeHTML(d.content)}</p>
      <button class="btn-light" style="margin-top:12px"
        onclick="deleteDiary(${d.id})">刪除日記</button>
    </div>
  `).join("") : '<div class="empty">還沒有旅行日記。</div>';
        }

        function deleteDiary(id) {
            data.diaries = data.diaries.filter(d => d.id !== id);
            save();
            renderDiaries();
        }

        // 匯出旅行
        function exportTrip(id) {
            const t = data.trips.find(x => x.id === id);
            if (!t) return;

            const days = data.itineraries[id] || [];
            const expenses = data.expenses[id] || [];

            let content =
                `2027 SOLOTRIP 旅行計畫

旅行名稱：${t.name}
目的地：${t.destination}
日期：${t.start} ～ ${t.end}
天數：${dateDays(t.start, t.end)} 天
旅行方式：${t.type}
總預算：${money(t.budget)}
備註：${t.note}

========== 每日行程 ==========

`;

            days.forEach((d, i) => {
                content += `
DAY ${i + 1} (${d.date})
上午：${d.morning}
下午：${d.afternoon}
晚上：${d.evening}
交通：${d.transport}
備註：${d.note}

`;
            });

            content += "========== 支出明細 ==========\n";

            expenses.forEach(e => {
                content += `${e.name} / ${e.category} / ${money(e.amount)}\n`;
            });

            content += `
========== 安全資訊 ==========
聯絡人：${data.safety.name || ""}
電話：${data.safety.phone || ""}
住宿：${data.safety.address || ""}
`;

            const blob = new Blob(["\uFEFF" + content], {
                type: "text/plain;charset=utf-8"
            });

            const url = URL.createObjectURL(blob);
            const a = document.createElement("a");
            a.href = url;
            a.download = "SoloTrip_" + t.name + ".txt";
            a.click();
            URL.revokeObjectURL(url);
        }

        // HTML 安全處理
        function escapeHTML(value) {
            return String(value ?? "").replace(/[&<>"']/g, c => ({
                "&": "&amp;",
                "<": "&lt;",
                ">": "&gt;",
                '"': "&quot;",
                "'": "&#39;"
            })[c]);
        }

        function escapeAttr(value) {
            return escapeHTML(value);
        }

        // 初始化
        renderHome();
        renderTrips();
        renderChecks();
        loadSafety();
        refreshSelects("itineraryTrip");
        refreshSelects("budgetTrip");
        refreshSelects("diaryTrip");

    </script>

</body>

</html>
