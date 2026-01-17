<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Alicia | Studio Academic Planner</title>
    <style>
        /* --- 1. Theme Variables --- */
        :root {
            --bg: #fdf2f8; /* Soft Pink Base */
            --glass: rgba(255, 255, 255, 0.7);
            --accent: #f472b6; /* Coquette Pink */
            --text: #500724;
            --border: rgba(244, 114, 182, 0.2);
            --font-main: 'Inter', sans-serif;
        }

        /* Dark/Tech Theme Overrides */
        body.dark-theme {
            --bg: #020617;
            --glass: rgba(30, 41, 59, 0.7);
            --accent: #818cf8; /* Tech Indigo */
            --text: #f8fafc;
            --border: rgba(129, 140, 248, 0.2);
        }

        /* --- 2. Global Styles --- */
        * { box-sizing: border-box; margin: 0; padding: 0; }
        body {
            background: var(--bg);
            color: var(--text);
            font-family: var(--font-main);
            transition: all 0.5s ease;
            padding: 20px;
        }

        /* --- 3. Layout Structure --- */
        .dashboard {
            display: grid;
            grid-template-columns: 250px 1fr 300px;
            gap: 20px;
            max-width: 1400px;
            margin: 0 auto;
        }

        .glass-card {
            background: var(--glass);
            backdrop-filter: blur(15px);
            border: 1px solid var(--border);
            border-radius: 24px;
            padding: 20px;
            box-shadow: 0 8px 32px rgba(0, 0, 0, 0.05);
        }

        /* --- Sidebar & Navigation --- */
        .sidebar h1 { font-size: 1.2rem; margin-bottom: 30px; color: var(--accent); }
        .nav-list { list-style: none; }
        .nav-list li { padding: 12px; cursor: pointer; border-radius: 12px; transition: 0.3s; margin-bottom: 5px; }
        .nav-list li:hover { background: rgba(255, 255, 255, 0.3); color: var(--accent); }

        /* --- Center Section: Schedule & Courses --- */
        .main-content h2 { font-size: 1.5rem; margin-bottom: 20px; letter-spacing: -1px; }
        
        .course-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(180px, 1fr));
            gap: 15px;
            margin-top: 20px;
        }
        .course-card {
            text-align: center;
            padding: 20px;
            border: 1px dashed var(--accent);
            border-radius: 20px;
            transition: 0.3s;
        }
        .course-card:hover { background: var(--glass); transform: translateY(-5px); border-style: solid; }

        /* --- Pomodoro Timer --- */
        .timer-container { text-align: center; }
        .timer-display { font-size: 4rem; font-weight: 800; margin: 20px 0; color: var(--accent); }
        .btn-timer {
            background: var(--accent);
            color: white;
            border: none;
            padding: 10px 25px;
            border-radius: 50px;
            cursor: pointer;
            font-weight: bold;
        }

        /* --- Theme Toggle --- */
        .theme-switch {
            position: fixed; bottom: 20px; left: 20px;
            background: var(--accent); color: white;
            border: none; padding: 10px 20px; border-radius: 50px; cursor: pointer; z-index: 1000;
        }

        /* Responsive Mobile Layout */
        @media (max-width: 1024px) {
            .dashboard { grid-template-columns: 1fr; }
            .sidebar, .right-panel { display: none; }
        }
    </style>
</head>
<body>

    <button class="theme-switch" onclick="toggleTheme()">Switch Theme</button>

    <div class="dashboard">
        <aside class="glass-card sidebar">
            <h1>Alicia Studio.</h1>
            <ul class="nav-list">
                <li>🎀 Dashboard</li>
                <li>📚 Courses</li>
                <li>📝 Assignments</li>
                <li>📅 Exams</li>
                <li>⚙️ Settings</li>
            </ul>
            <div style="margin-top: 40px; padding: 15px; background: rgba(255,255,255,0.2); border-radius: 15px;">
                <p style="font-size: 0.8rem;">"Work for your goals."</p>
            </div>
        </aside>

        <main class="main-content">
            <div class="glass-card" style="margin-bottom: 20px;">
                <h2>Weekly Schedule</h2>
                <p style="font-size: 0.9rem; color: var(--accent);">Today is January 17, 2026</p>
                <div style="margin-top: 15px; opacity: 0.7;">
                    <p>08:00 - Study Session</p>
                    <p>12:00 - Lunch Break</p>
                    <p>14:00 - Coding Practice</p>
                </div>
            </div>

            <div class="glass-card">
                <h2>My Courses</h2>
                <div class="course-grid" id="courseGrid">
                    <div class="course-card">
                        <div style="font-size: 2rem; margin-bottom: 10px;">📖</div>
                        <h4>Course A</h4>
                        <p style="font-size: 0.7rem;">Active Tasks: 2</p>
                    </div>
                    <div class="course-card">
                        <div style="font-size: 2rem; margin-bottom: 10px;">🎨</div>
                        <h4>Course B</h4>
                        <p style="font-size: 0.7rem;">Active Tasks: 0</p>
                    </div>
                    <div class="course-card" style="border-style: dotted; cursor: pointer;">
                        <div style="font-size: 2rem; margin-bottom: 10px;">+</div>
                        <h4>Add New</h4>
                    </div>
                </div>
            </div>
        </main>

        <section class="right-panel">
            <div class="glass-card timer-container" style="margin-bottom: 20px;">
                <h2>Focus Timer</h2>
                <div class="timer-display" id="time">25:00</div>
                <button class="btn-timer" onclick="toggleTimer()">Start Focus</button>
            </div>

            <div class="glass-card">
                <h2>Academic Goals</h2>
                <ul style="list-style: none; margin-top: 15px; font-size: 0.9rem;">
                    <li style="margin-bottom: 10px;"><input type="checkbox"> Maintain 4.0 GPA</li>
                    <li style="margin-bottom: 10px;"><input type="checkbox"> Complete 1st Semester</li>
                    <li style="margin-bottom: 10px;"><input type="checkbox"> Learn a New Language</li>
                </ul>
            </div>
        </section>
    </div>

    <script>
        // 1. Theme Toggling Logic
        function toggleTheme() {
            document.body.classList.toggle('dark-theme');
        }

        // 2. Focus Timer Logic
        let timer;
        let isRunning = false;
        let timeLeft = 25 * 60;

        function toggleTimer() {
            const btn = document.querySelector('.btn-timer');
            if (isRunning) {
                clearInterval(timer);
                btn.innerText = "Start Focus";
            } else {
                timer = setInterval(updateTimer, 1000);
                btn.innerText = "Pause";
            }
            isRunning = !isRunning;
        }

        function updateTimer() {
            let minutes = Math.floor(timeLeft / 60);
            let seconds = timeLeft % 60;
            document.getElementById('time').innerText = 
                `${minutes}:${seconds < 10 ? '0' : ''}${seconds}`;
            
            if (timeLeft <= 0) {
                clearInterval(timer);
                alert("Session complete!");
            }
            timeLeft--;
        }

        // 3. Dynamic Greeting (Based on your location: Lahore)
        console.log("Welcome Alicia. Good luck with your finals on the 27th!");
    </script>
</body>
</html>
