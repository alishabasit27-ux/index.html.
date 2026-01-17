<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Alicia | Coquette Planner</title>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600;800&family=Playfair+Display:ital,wght@1,600&display=swap" rel="stylesheet">
    <style>
        :root {
            --primary: #e11d48;       /* Deep Rose */
            --soft-pink: #fce7f3;     /* Light Pink Background */
            --card-bg: #fff1f2;       /* Very Pale Pink Card */
            --glass: rgba(255, 255, 255, 0.6);
            --border: #fbcfe8;        /* Pink Border */
            --text: #881337;          /* Dark Rose Text */
            --shadow: rgba(244, 63, 94, 0.1);
        }

        body.dark-mode {
            --primary: #f472b6;
            --soft-pink: #0f172a;     /* Dark Navy */
            --card-bg: #1e293b;       /* Dark Blue Grey */
            --glass: rgba(30, 41, 59, 0.7);
            --border: #334155;
            --text: #e2e8f0;          /* Light Grey Text */
            --shadow: rgba(0, 0, 0, 0.3);
        }

        * { box-sizing: border-box; margin: 0; padding: 0; }
        body { 
            background-color: var(--soft-pink); 
            color: var(--text); 
            font-family: 'Inter', sans-serif; 
            padding: 20px; 
            transition: 0.5s;
        }

        /* --- THEME SWITCHER (Fixed Position) --- */
        .theme-toggle {
            position: fixed; bottom: 20px; right: 20px;
            background: var(--primary); color: white;
            border: none; padding: 12px 24px; border-radius: 30px;
            font-weight: bold; cursor: pointer;
            box-shadow: 0 5px 15px var(--shadow);
            z-index: 1000; transition: 0.3s;
        }
        .theme-toggle:hover { transform: scale(1.05); }

        /* --- LAYOUT GRID --- */
        .dashboard {
            max-width: 1400px;
            margin: 0 auto;
            display: grid;
            grid-template-columns: 280px 1fr 300px; /* Sidebar | Main | Right Panel */
            gap: 25px;
        }

        /* --- CARDS & GLASS EFFECT --- */
        .card {
            background: var(--card-bg);
            border: 1px solid var(--border);
            border-radius: 20px;
            padding: 20px;
            margin-bottom: 20px;
            box-shadow: 0 4px 20px var(--shadow);
            backdrop-filter: blur(10px);
        }

        h1, h2, h3 { font-family: 'Playfair Display', serif; margin-bottom: 15px; color: var(--primary); }
        
        /* --- LEFT COLUMN: Clock & Quick Actions --- */
        .digital-clock {
            display: flex; gap: 10px; font-weight: 900; font-size: 3rem; color: white;
            margin-bottom: 20px;
        }
        .clock-box {
            background: #f43f5e; /* Hot Pink */
            padding: 15px; border-radius: 15px; flex: 1; text-align: center;
            box-shadow: 0 5px 15px rgba(244, 63, 94, 0.3);
        }

        .quick-btn {
            display: block; width: 100%; padding: 10px; margin-bottom: 8px;
            background: white; border: 1px solid var(--border); border-radius: 10px;
            text-align: left; cursor: pointer; color: var(--text); font-size: 0.9rem;
            transition: 0.2s;
        }
        .quick-btn:hover { background: var(--primary); color: white; }

        /* --- CENTER COLUMN: Schedule & Tasks --- */
        .schedule-table { width: 100%; border-collapse: collapse; font-size: 0.9rem; }
        .schedule-table td { padding: 12px 5px; border-bottom: 1px solid var(--border); }
        .tag { 
            background: #fce7f3; color: #be185d; 
            padding: 4px 8px; border-radius: 5px; font-size: 0.75rem; font-weight: bold; 
        }

        /* --- RIGHT COLUMN: Notifications & Focus --- */
        .notification-card { background: white; border-radius: 15px; padding: 15px; margin-bottom: 10px; font-size: 0.85rem; border-left: 4px solid var(--primary); }
        
        .music-widget {
            background: #1e1b4b; /* Deep Indigo for contrast like Spotify */
            color: white; padding: 20px; border-radius: 20px;
            display: flex; align-items: center; gap: 15px;
        }
        .music-img { width: 60px; height: 60px; border-radius: 10px; object-fit: cover; }

        .timer-display { font-size: 4rem; font-weight: 800; color: var(--primary); text-align: center; margin: 10px 0; }

        /* --- BOTTOM: Courses Grid --- */
        .course-grid {
            grid-column: 1 / -1; /* Span full width */
            display: grid; grid-template-columns: repeat(auto-fill, minmax(200px, 1fr)); gap: 20px;
        }
        .course-card {
            background: white; border-radius: 15px; overflow: hidden; border: 1px solid var(--border);
            transition: 0.3s; text-align: center;
        }
        .course-card:hover { transform: translateY(-5px); border-color: var(--primary); }
        .course-card img { width: 100%; height: 120px; object-fit: cover; }

        /* --- FOOTER --- */
        footer {
            grid-column: 1 / -1; text-align: center; padding: 40px;
            font-family: 'Playfair Display', serif; font-style: italic; opacity: 0.7;
        }

        /* Mobile */
        @media (max-width: 1024px) { .dashboard { grid-template-columns: 1fr; } }
    </style>
</head>
<body>

    <button class="theme-toggle" onclick="toggleTheme()">✨ Switch Theme</button>

    <div class="dashboard">
        
        <aside>
            <div class="digital-clock">
                <div class="clock-box" id="hour">14</div>
                <div class="clock-box" id="min">36</div>
            </div>

            <div class="card">
                <h2>Quick Action</h2>
                <button class="quick-btn">📒New Assignment</button>
                <button class="quick-btn">📚 New Course</button>
                <button class="quick-btn">📖New Exam</button>
                <button class="quick-btn">📝 New Note</button>
            </div>

            <div class="card">
                <h3>Navigation</h3>
                <ul style="list-style: none; padding-left: 5px;">
                    <li style="margin-bottom: 10px;">📂 Files</li>
                    <li style="margin-bottom: 10px;">📊 Grades</li>
                    <li style="margin-bottom: 10px;">🌸 Dashboard</li>
                </ul>
            </div>
            
            <img src="https://i.pinimg.com/736x/ef/d6/3c/efd63cda211c095a53f2ac004ff232f1.jpg" alt="Vibe">
        </aside>

        <main>
            <div style="margin-bottom: 20px;">
                <h1 style="font-size: 2.5rem;">Alicia's Planner</h1>
                <p style="opacity: 0.7;">Let's be productive today!</p>
            </div>

            <div class="card">
                <h2>Today's Schedule</h2>
                <table class="schedule-table">
                    <tr><td>08:00 AM</td><td><strong>Prepare for School</strong></td><td><span class="tag">Routine</span></td></tr>
                    <tr><td>09:00 AM</td><td><strong>Go to University</strong></td><td><span class="tag">School</span></td></tr>
                    <tr><td>12:00 PM</td><td><strong>Lunch Break</strong></td><td><span class="tag">Rest</span></td></tr>
                    <tr><td>02:00 PM</td><td><strong>CS201 Study</strong></td><td><span class="tag">Focus</span></td></tr>
                    <tr><td>04:00 PM</td><td><strong>Go Home</strong></td><td><span class="tag">Travel</span></td></tr>
                </table>
            </div>

            <div class="card">
                <h2>Weekly Tasks</h2>
                <div style="display: flex; justify-content: space-between; margin-bottom: 10px; border-bottom: 1px dashed var(--border); padding-bottom: 10px;">
                    <span>Finals Preparation</span>
                    <span style="color: var(--primary);">Due Jan 27</span>
                </div>
                <div style="display: flex; justify-content: space-between; margin-bottom: 10px;">
                    <span>Lab Assignment 03</span>
                    <span style="color: var(--primary);">Due Tomorrow</span>
                </div>
            </div>
        </main>

        <aside>
            <div class="card">
                <h3>🔔 Notifications</h3>
                <div class="notification-card">
                    <strong>Welcome back, Alicia!</strong><br>
                    You have 2 upcoming exams.
                </div>
                <div class="notification-card">
                    <strong>Tasks Update</strong><br>
                    You have 0 assignments overdue.
                </div>
            </div>

            <div class="music-widget" style="margin-bottom: 20px;">
                <img src="https://i.pinimg.com/736x/05/c3/44/05c344e5df9b0edcdfa0777283601ebb.jpg" class="music-img" alt="Album">
                <div>
                    <div style="font-size: 0.8rem; opacity: 0.7;">currently: studying</div>
                    <div style="font-weight: bold;">Lofi Beats</div>
                    <div style="font-size: 0.8rem;">Alicia's Mix</div>
                </div>
            </div>

            <div class="card" style="text-align: center;">
                <h3>Focus Timer</h3>
                <div class="timer-display" id="timer">25:00</div>
                <button class="quick-btn" style="text-align: center; background: var(--primary); color: white;" onclick="toggleTimer()" id="timerBtn">Start</button>
            </div>
        </aside>

        <div class="course-grid">
            <div class="course-card">
                <img src=https://i.pinimg.com/736x/44/0c/0a/440c0ab4244c3bf91e796cd4d5c65fd5.jpg"" alt="C1">
                <div style="padding: 10px;"><h4>Subject 1</h4></div>
            </div>
            <div class="course-card">
                <img src="https://i.pinimg.com/736x/73/4a/63/734a6335a74c2b87af297fec97aaa6ca.jpg" alt="C2">
                <div style="padding: 10px;"><h4>Subject 2</h4></div>
            </div>
            <div class="course-card">
                <img src="https://i.pinimg.com/736x/d7/57/52/d75752a044f4ce0ceaeff5f50709937e.jpg" alt="C3">
                <div style="padding: 10px;"><h4>Subject 3</h4></div>
            </div>
            <div class="course-card">
                <img src="https://i.pinimg.com/736x/28/24/c1/2824c1ea83a6d77169f59635915d535d.jpg" alt="C4">
                <div style="padding: 10px;"><h4>Subject 3</h4></div>
            </div>
        </div>

        <footer>
            Created with love by Alisha 🎀 2026
        </footer>
    </div>

    <script>
        // 1. THEME SWITCHER LOGIC
        // Check if user already has a saved theme
        if (localStorage.getItem('theme') === 'dark') {
            document.body.classList.add('dark-mode');
        }

        function toggleTheme() {
            document.body.classList.toggle('dark-mode');
            // Save preference
            if (document.body.classList.contains('dark-mode')) {
                localStorage.setItem('theme', 'dark');
            } else {
                localStorage.setItem('theme', 'light');
            }
        }

        // 2. LIVE CLOCK LOGIC
        function updateClock() {
            const now = new Date();
            const hours = String(now.getHours()).padStart(2, '0');
            const minutes = String(now.getMinutes()).padStart(2, '0');
            document.getElementById('hour').innerText = hours;
            document.getElementById('min').innerText = minutes;
        }
        setInterval(updateClock, 1000);
        updateClock(); // Run immediately

        // 3. TIMER LOGIC
        let time = 25 * 60; 
        let run = false; 
        let int;
        function toggleTimer() {
            const btn = document.getElementById('timerBtn');
            if (!run) {
                int = setInterval(() => {
                    time--;
                    let m = Math.floor(time / 60);
                    let s = time % 60;
                    document.getElementById('timer').innerText = `${m}:${s < 10 ? '0' : ''}${s}`;
                    if (time <= 0) clearInterval(int);
                }, 1000);
                btn.innerText = "Pause";
            } else {
                clearInterval(int);
                btn.innerText = "Resume";
            }
            run = !run;
        }
    </script>
</body>
</html>
