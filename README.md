  <!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Alisha Studio | Academic Planner</title>
    <style>
        :root {
            --primary: #f472b6;
            --bg: #fdf2f8;
            --glass: rgba(255, 255, 255, 0.7);
            --border: rgba(244, 114, 182, 0.2);
            --text: #500724;
        }
        body.dark-mode {
            --primary: #818cf8;
            --bg: #020617;
            --glass: rgba(30, 41, 59, 0.7);
            --text: #f8fafc;
        }
        * { box-sizing: border-box; margin: 0; padding: 0; }
        body { background: var(--bg); color: var(--text); font-family: 'Inter', sans-serif; padding: 20px; transition: 0.5s; }

        /* --- Full Bento Layout --- */
        .dashboard-container {
            max-width: 1400px;
            margin: 0 auto;
            display: grid;
            grid-template-columns: 260px 1fr 300px;
            gap: 20px;
        }

        .glass {
            background: var(--glass);
            backdrop-filter: blur(15px);
            border: 1px solid var(--border);
            border-radius: 25px;
            padding: 20px;
            margin-bottom: 20px;
        }

        /* --- Sidebar Features --- */
        .brand-name { font-size: 1.5rem; font-weight: 800; color: var(--primary); margin-bottom: 30px; }
        .nav-link { padding: 12px; display: block; text-decoration: none; color: inherit; font-size: 0.9rem; border-radius: 12px; }
        .nav-link:hover { background: rgba(255,255,255,0.4); color: var(--primary); }

        /* --- Schedule Table (Reference Style) --- */
        .schedule-table { width: 100%; border-collapse: collapse; font-size: 0.85rem; margin-top: 15px; }
        .schedule-table td { padding: 8px 5px; border-bottom: 1px solid rgba(0,0,0,0.05); }
        .time-tag { color: var(--primary); font-weight: bold; width: 80px; }

        /* --- Course Cards with Images --- */
        .course-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(180px, 1fr)); gap: 15px; }
        .course-card { background: white; border-radius: 20px; overflow: hidden; border: 1px solid var(--border); transition: 0.3s; }
        .course-card:hover { transform: translateY(-5px); border-color: var(--primary); }
        .course-card img { width: 100%; height: 110px; object-fit: cover; }
        .course-info { padding: 12px; text-align: center; }

        /* --- Interactive Goals --- */
        .goal-input { width: 100%; padding: 10px; border-radius: 10px; border: 1px solid var(--border); margin-bottom: 10px; outline: none; }
        .btn-add { background: var(--primary); color: white; border: none; padding: 10px; border-radius: 10px; width: 100%; cursor: pointer; font-weight: bold; }
        .goal-item { display: flex; align-items: center; gap: 10px; margin-top: 10px; font-size: 0.9rem; }

        /* --- Focus Timer --- */
        .timer-val { font-size: 3.5rem; font-weight: 800; color: var(--primary); margin: 10px 0; }

        @media (max-width: 1024px) { .dashboard-container { grid-template-columns: 1fr; } }
    </style>
</head>
<body>

<div class="dashboard-container">
    <aside>
        <div class="glass">
            <h1 class="brand-name">Lumina Studio.</h1>
            <a href="#" class="nav-link">🌸 Dashboard</a>
            <a href="#" class="nav-link">📝 Assignments</a>
            <a href="#" class="nav-link">📅 Exams</a>
            <a href="#" class="nav-link">☁️ Files</a>
        </div>
        <div class="glass">
            <img src="https://i.pinimg.com/564x/57/9d/28/579d280d96570c6533d3d828a2a78f2e.jpg" style="width:100%; border-radius:15px; opacity:0.8;" alt="Vibe">
            <p style="font-size: 0.75rem; margin-top: 10px; font-style: italic;">"Focus on your growth, Alicia."</p>
        </div>
    </aside>

    <main>
        <section class="glass">
            <h2>Daily Schedule</h2>
            <table class="schedule-table">
                <tr><td class="time-tag">08:00 AM</td><td>Routine & Prep</td></tr>
                <tr><td class="time-tag">09:00 AM</td><td>Logic Design (CS101)</td></tr>
                <tr><td class="time-tag">12:00 PM</td><td>Lunch & Rest</td></tr>
                <tr><td class="time-tag">02:00 PM</td><td>Finals Study Session</td></tr>
            </table>
        </section>

        <section class="glass">
            <h2>Current Courses</h2>
            <div class="course-grid">
                <div class="course-card">
                    <img src="https://static.vecteezy.com/system/resources/previews/007/920/582/non_2x/a-goal-without-a-plan-is-just-a-wish-quote-inspirational-motivating-quotes-free-vector.jpg" alt="Course">
                    <div class="course-info"><h4>Subject 01</h4><p style="font-size:0.7rem;">Active: 2</p></div>
                </div>
                <div class="course-card">
                    <img src="https://img.freepik.com/premium-vector/if-your-goals-scare-you-they-big-enough-inspirational-quotes-motivation-poster-typography_1162612-1720.jpg" alt="Course">
                    <div class="course-info"><h4>Subject 02</h4><p style="font-size:0.7rem;">Exam in 10d</p></div>
                </div>
            </div>
        </section>
    </main>

    <aside>
        <div class="glass" style="text-align: center;">
            <h2>Focus</h2>
            <div class="timer-val" id="timer">25:00</div>
            <button class="btn-add" onclick="toggleTimer()" id="timerBtn">Start</button>
        </div>

        <div class="glass">
            <h2>Custom Goals</h2>
            <input type="text" id="gInput" class="goal-input" placeholder="New goal...">
            <button class="btn-add" onclick="addGoal()">Add Goal</button>
            <div id="gList"></div>
            
            <div id="studyGuide" style="margin-top: 20px; font-size: 0.8rem; border-left: 3px solid var(--primary); padding-left: 10px;">
                <strong>Study Tip:</strong> Add a goal to see advice!
            </div>
        </div>
    </aside>
</div>

<script>
    // GOALS LOGIC (Saves to browser)
    let goals = JSON.parse(localStorage.getItem('alicia_goals')) || [];
    function addGoal() {
        const input = document.getElementById('gInput');
        if (!input.value) return;
        goals.push(input.value);
        localStorage.setItem('alicia_goals', JSON.stringify(goals));
        input.value = '';
        renderGoals();
    }
    function renderGoals() {
        const list = document.getElementById('gList');
        const guide = document.getElementById('studyGuide');
        list.innerHTML = goals.map(g => `<div class="goal-item"><input type="checkbox"> ${g}</div>`).join('');
        
        if(goals.length > 0) {
            const last = goals[goals.length-1].toLowerCase();
            if(last.includes("math") || last.includes("mth")) guide.innerHTML = "<strong>Tip:</strong> Solve 5 problems using the 25:00 timer.";
            else if(last.includes("code") || last.includes("cs")) guide.innerHTML = "<strong>Tip:</strong> Check your logic loops twice before running.";
            else guide.innerHTML = "<strong>Tip:</strong> Break this into 3 tiny steps.";
        }
    }

    // TIMER LOGIC
    let time = 25 * 60; let run = false; let int;
    function toggleTimer() {
        if(!run) { 
            int = setInterval(() => {
                time--; 
                let m = Math.floor(time/60); let s = time%60;
                document.getElementById('timer').innerText = `${m}:${s < 10 ? '0' : ''}${s}`;
                if(time <= 0) clearInterval(int);
            }, 1000);
            document.getElementById('timerBtn').innerText = "Pause";
        } else { clearInterval(int); document.getElementById('timerBtn').innerText = "Resume"; }
        run = !run;
    }
    renderGoals();
</script>
<section class="glass">
    <h2>Current Courses</h2>
    <div class="course-grid">
        <div class="course-card">
            <img src="<img width="620" height="800" alt="image" src="https://img.picturequotes.com/2/333/332824/when-you-have-set-yourself-a-task-finish-it-quote-1.jpg" />" alt="Books">
            <div class="course-info">
                <h4>Course A</h4>
                <p style="font-size:0.7rem;">2 Tasks Remaining</p>
            </div>
        </div>
        <div class="course-card">
            <img src="https:" alt="Tech">
            <div class="course-info">
                <h4>Course B</h4>
                <p style="font-size:0.7rem;">Exams</p>
            </div>
        </div>
    </div>
</section>

<section class="glass" style="margin-top:20px; text-align:center;">
    <h3>Daily Vibe</h3>
    <div style="font-size: 2rem; display: flex; justify-content: center; gap: 20px; margin-top: 10px;">
        <span style="cursor:pointer;" onclick="setMood('✨')">✨</span>
        <span style="cursor:pointer;" onclick="setMood('☁️')">☁️</span>
        <span style="cursor:pointer;" onclick="setMood('🎧')">🎧</span>
        <span style="cursor:pointer;" onclick="setMood('📚')">📚</span>
    </div>
    <p id="moodStatus" style="font-size: 0.8rem; margin-top: 10px; color: var(--primary);">How are you feeling today?</p>
</section>

<script>
    function setMood(emoji) {
        document.getElementById('moodStatus').innerText = "Current Vibe: " + emoji;
        // Software Engineering tip: You could save this to LocalStorage too!
    }
</script>
</body>
</html>
