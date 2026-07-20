<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Nextora - Career & Education Platform</title>
    <!-- Font Awesome Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        :root {
            --primary: #4f46e5;
            --primary-hover: #4338ca;
            --secondary: #0f172a;
            --bg-light: #f8fafc;
            --surface: #ffffff;
            --text-dark: #0f172a;
            --text-light: #64748b;
            --border: #e2e8f0;
            --radius: 12px;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            background-color: var(--bg-light);
            color: var(--text-dark);
            display: flex;
            min-height: 100vh;
        }

        /* --- SIDEBAR LAYOUT --- */
        .sidebar {
            width: 260px;
            background-color: var(--secondary);
            color: white;
            padding: 1.5rem;
            display: flex;
            flex-direction: column;
            gap: 2rem;
            position: fixed;
            height: 100vh;
        }

        .brand {
            font-size: 1.5rem;
            font-weight: 700;
            display: flex;
            align-items: center;
            gap: 0.75rem;
            color: #818cf8;
        }

        .nav-menu {
            list-style: none;
            display: flex;
            flex-direction: column;
            gap: 0.5rem;
        }

        .nav-item button {
            width: 100%;
            background: none;
            border: none;
            color: #94a3b8;
            padding: 0.75rem 1rem;
            border-radius: var(--radius);
            display: flex;
            align-items: center;
            gap: 0.75rem;
            font-size: 0.95rem;
            cursor: pointer;
            transition: all 0.2s ease;
        }

        .nav-item button:hover, .nav-item button.active {
            background-color: rgba(255, 255, 255, 0.1);
            color: white;
        }

        /* --- MAIN CONTENT AREA --- */
        .main-content {
            margin-left: 260px;
            flex: 1;
            padding: 2rem;
        }

        .tab-content {
            display: none;
        }

        .tab-content.active {
            display: block;
        }

        /* --- HERO HIGHLIGHT BAR --- */
        .hero-highlight-bar {
            background: linear-gradient(135deg, #0f172a 0%, #1e1b4b 50%, #312e81 100%);
            border-radius: 16px;
            padding: 2.5rem 2rem;
            color: #ffffff;
            box-shadow: 0 20px 25px -5px rgba(15, 23, 42, 0.25), 0 8px 10px -6px rgba(15, 23, 42, 0.1);
            position: relative;
            overflow: hidden;
            margin-bottom: 2rem;
            border: 1px solid rgba(255, 255, 255, 0.1);
        }

        .hero-highlight-bar::before {
            content: '';
            position: absolute;
            top: -50%;
            right: -10%;
            width: 300px;
            height: 300px;
            background: radial-gradient(circle, rgba(99, 102, 241, 0.35) 0%, rgba(0, 0, 0, 0) 70%);
            border-radius: 50%;
            pointer-events: none;
        }

        .hero-content {
            position: relative;
            z-index: 2;
            max-width: 850px;
        }

        .hero-badge-group {
            display: flex;
            align-items: center;
            gap: 0.75rem;
            flex-wrap: wrap;
            margin-bottom: 1rem;
        }

        .hero-pill {
            background: rgba(99, 102, 241, 0.25);
            border: 1px solid rgba(129, 140, 248, 0.4);
            color: #a5b4fc;
            font-size: 0.8rem;
            font-weight: 600;
            padding: 0.35rem 0.85rem;
            border-radius: 9999px;
            display: inline-flex;
            align-items: center;
            gap: 0.4rem;
            letter-spacing: 0.025em;
            text-transform: uppercase;
        }

        .hero-pill-active {
            background: linear-gradient(135deg, #6366f1 0%, #4f46e5 100%);
            color: #ffffff;
            border: none;
            box-shadow: 0 4px 12px rgba(79, 70, 229, 0.35);
        }

        .hero-title {
            font-size: 2.25rem;
            font-weight: 800;
            line-height: 1.25;
            margin-bottom: 0.85rem;
            letter-spacing: -0.02em;
            background: linear-gradient(to right, #ffffff, #c7d2fe);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        .hero-description {
            font-size: 1.05rem;
            line-height: 1.6;
            color: #cbd5e1;
            margin-bottom: 1.75rem;
            font-weight: 400;
        }

        .hero-stats-row {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(180px, 1fr));
            gap: 1rem;
            padding-top: 1.25rem;
            border-top: 1px solid rgba(255, 255, 255, 0.12);
        }

        .hero-stat-card {
            background: rgba(255, 255, 255, 0.05);
            backdrop-filter: blur(8px);
            border: 1px solid rgba(255, 255, 255, 0.08);
            border-radius: 10px;
            padding: 0.85rem 1rem;
        }

        .hero-stat-number {
            font-size: 1.35rem;
            font-weight: 700;
            color: #38bdf8;
            display: block;
        }

        .hero-stat-label {
            font-size: 0.8rem;
            color: #94a3b8;
            text-transform: uppercase;
            letter-spacing: 0.05em;
        }

        /* --- CARDS & UI COMPONENTS --- */
        .calculator-card {
            background: var(--surface);
            padding: 1.5rem;
            border-radius: var(--radius);
            border: 1px solid var(--border);
            margin-bottom: 2rem;
            display: flex;
            gap: 1rem;
            align-items: flex-end;
            flex-wrap: wrap;
        }

        .form-group {
            display: flex;
            flex-direction: column;
            gap: 0.5rem;
            flex: 1;
            min-width: 200px;
        }

        .form-group label {
            font-size: 0.875rem;
            font-weight: 600;
            color: var(--text-light);
        }

        .form-group input, .form-group select {
            padding: 0.75rem;
            border: 1px solid var(--border);
            border-radius: 8px;
            outline: none;
        }

        .btn {
            padding: 0.75rem 1.5rem;
            border: none;
            border-radius: 8px;
            background-color: var(--primary);
            color: white;
            font-weight: 600;
            cursor: pointer;
            transition: background 0.2s ease;
        }

        .btn:hover {
            background-color: var(--primary-hover);
        }

        .btn-secondary {
            background-color: #e2e8f0;
            color: var(--text-dark);
        }

        .grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
            gap: 1.5rem;
        }

        .card {
            background: var(--surface);
            border: 1px solid var(--border);
            border-radius: var(--radius);
            padding: 1.5rem;
            display: flex;
            flex-direction: column;
            justify-content: space-between;
        }

        .card-header {
            margin-bottom: 1rem;
        }

        .badge {
            display: inline-block;
            padding: 0.25rem 0.5rem;
            border-radius: 6px;
            font-size: 0.75rem;
            font-weight: 600;
        }

        .badge-free { background-color: #dcfce7; color: #166534; }
        .badge-paid { background-color: #fee2e2; color: #991b1b; }

        /* --- CHATBOT WIDGET --- */
        .chat-widget {
            position: fixed;
            bottom: 2rem;
            right: 2rem;
            z-index: 1000;
        }

        .chat-btn {
            width: 60px;
            height: 60px;
            border-radius: 50%;
            background-color: var(--primary);
            color: white;
            border: none;
            font-size: 1.5rem;
            cursor: pointer;
            box-shadow: 0 4px 12px rgba(0,0,0,0.15);
        }

        .chat-window {
            position: absolute;
            bottom: 75px;
            right: 0;
            width: 350px;
            height: 450px;
            background: var(--surface);
            border: 1px solid var(--border);
            border-radius: var(--radius);
            box-shadow: 0 10px 25px rgba(0,0,0,0.1);
            display: flex;
            flex-direction: column;
            overflow: hidden;
        }

        .chat-window.hidden {
            display: none;
        }

        .chat-header {
            background: linear-gradient(135deg, #0f172a 0%, #1e1b4b 100%);
            color: white;
            padding: 1rem;
            display: flex;
            justify-content: space-between;
            align-items: center;
            font-weight: 700;
            letter-spacing: 0.03em;
        }

        .chat-messages {
            flex: 1;
            padding: 1rem;
            overflow-y: auto;
            display: flex;
            flex-direction: column;
            gap: 0.75rem;
        }

        .message {
            padding: 0.75rem;
            border-radius: 8px;
            max-width: 80%;
            font-size: 0.9rem;
        }

        .message.bot { background-color: #f1f5f9; align-self: flex-start; }
        .message.user { background-color: var(--primary); color: white; align-self: flex-end; }

        .chat-input-area {
            padding: 0.75rem;
            border-top: 1px solid var(--border);
            display: flex;
            gap: 0.5rem;
        }

        .chat-input-area input {
            flex: 1;
            padding: 0.5rem;
            border: 1px solid var(--border);
            border-radius: 6px;
            outline: none;
        }

        /* --- TOAST NOTIFICATION --- */
        .toast {
            position: fixed;
            bottom: 2rem;
            left: 50%;
            transform: translateX(-50%);
            background-color: var(--secondary);
            color: white;
            padding: 0.75rem 1.5rem;
            border-radius: 8px;
            font-size: 0.9rem;
            box-shadow: 0 4px 12px rgba(0,0,0,0.15);
            transition: opacity 0.3s ease;
            z-index: 2000;
        }
    </style>
</head>
<body>

    <!-- SIDEBAR NAVIGATION -->
    <aside class="sidebar">
        <div class="brand">
            <i class="fa-solid fa-compass"></i> Nextora
        </div>
        <ul class="nav-menu">
            <li class="nav-item">
                <button class="active" onclick="switchTab('colleges', this)">
                    <i class="fa-solid fa-building-columns"></i> Colleges & Degrees
                </button>
            </li>
            <li class="nav-item">
                <button onclick="switchTab('courses', this)">
                    <i class="fa-solid fa-book-open"></i> Skill Courses
                </button>
            </li>
            <li class="nav-item">
                <button onclick="switchTab('scholarships', this)">
                    <i class="fa-solid fa-hand-holding-dollar"></i> Grants & Scholarships
                </button>
            </li>
            <li class="nav-item">
                <button onclick="switchTab('profile', this)">
                    <i class="fa-solid fa-user"></i> My Profile
                </button>
            </li>
        </ul>
    </aside>

    <!-- MAIN CONTENT AREA -->
    <main class="main-content">

        <!-- TAB 1: COLLEGES & DEGREES -->
        <section id="colleges" class="tab-content active">

            <!-- MODERN HIGHLIGHTED HERO BANNER -->
            <div class="hero-highlight-bar">
                <div class="hero-content">
                    <div class="hero-badge-group">
                        <span class="hero-pill hero-pill-active">
                            <i class="fa-solid fa-wand-magic-sparkles"></i> Smart Recommendation Engine
                        </span>
                        <span class="hero-pill">
                            <i class="fa-solid fa-graduation-cap"></i> Degrees & Colleges
                        </span>
                    </div>

                    <h1 class="hero-title">
                        Discover Your Ideal Academic Path & Dream College
                    </h1>

                    <p class="hero-description">
                        Explore top-ranked universities, degree programs, and career roadmaps tailored to your profile. Enter your academic scores to filter eligible colleges and find the best match for your future goals.
                    </p>

                    <div class="hero-stats-row">
                        <div class="hero-stat-card">
                            <span class="hero-stat-number">500+</span>
                            <span class="hero-stat-label">Accredited Colleges</span>
                        </div>
                        <div class="hero-stat-card">
                            <span class="hero-stat-number">98%</span>
                            <span class="hero-stat-label">Recommendation Accuracy</span>
                        </div>
                        <div class="hero-stat-card">
                            <span class="hero-stat-number">50+</span>
                            <span class="hero-stat-label">Career Streams</span>
                        </div>
                    </div>
                </div>
            </div>

            <!-- CALCULATOR / FILTERS -->
            <div class="calculator-card">
                <div class="form-group">
                    <label for="calcScore">12th Marks Percentage (%)</label>
                    <input type="number" id="calcScore" placeholder="e.g. 85" min="0" max="100">
                </div>
                <div class="form-group">
                    <label for="calcStream">Preferred Stream</label>
                    <select id="calcStream">
                        <option value="all">All Streams</option>
                        <option value="Engineering">Engineering</option>
                        <option value="Management">Management</option>
                        <option value="Arts">Arts & Humanities</option>
                        <option value="Science">Pure Sciences</option>
                    </select>
                </div>
                <button class="btn" onclick="filterColleges()">Filter Colleges</button>
            </div>

            <!-- COLLEGES GRID -->
            <div id="collegesGrid" class="grid"></div>
        </section>

        <!-- TAB 2: COURSES -->
        <section id="courses" class="tab-content">
            <h2 style="margin-bottom: 1.5rem;">Skill Upgrading Courses</h2>
            <div id="coursesGrid" class="grid"></div>
        </section>

        <!-- TAB 3: SCHOLARSHIPS -->
        <section id="scholarships" class="tab-content">
            <h2 style="margin-bottom: 1.5rem;">Scholarships & Grants</h2>
            <div id="scholarshipsGrid" class="grid"></div>
        </section>

        <!-- TAB 4: PROFILE -->
        <section id="profile" class="tab-content">
            <h2 style="margin-bottom: 1.5rem;">Student Profile</h2>
            <div class="calculator-card" style="flex-direction: column; align-items: stretch;">
                <form id="profileForm" onsubmit="saveProfile(event)">
                    <div class="form-group" style="margin-bottom: 1rem;">
                        <label>10th Percentage (%)</label>
                        <input type="number" id="p10th" required>
                    </div>
                    <div class="form-group" style="margin-bottom: 1rem;">
                        <label>12th Percentage (%)</label>
                        <input type="number" id="p12th" required>
                    </div>
                    <div class="form-group" style="margin-bottom: 1rem;">
                        <label>Academic Stream</label>
                        <select id="pStream">
                            <option value="Engineering">Engineering</option>
                            <option value="Management">Management</option>
                            <option value="Arts">Arts</option>
                            <option value="Science">Science</option>
                        </select>
                    </div>
                    <div class="form-group" style="margin-bottom: 1.5rem;">
                        <label>Current Status</label>
                        <input type="text" id="pStatus" placeholder="e.g. High School Senior">
                    </div>
                    <button type="submit" class="btn">Save Profile Data</button>
                </form>
            </div>
        </section>

    </main>

    <!-- CHATBOT WIDGET -->
    <div class="chat-widget">
        <button class="chat-btn" onclick="toggleChat()">
            <i class="fa-solid fa-robot"></i>
        </button>
        <div class="chat-window hidden" id="chatWindow">
            <div class="chat-header">
                <span>Ask Explore Discover</span>
                <i class="fa-solid fa-xmark" style="cursor: pointer;" onclick="toggleChat()"></i>
            </div>
            <div class="chat-messages" id="chatMessages">
                <div class="message bot">Hello! Ask me anything about career paths, recommended degrees, or skill courses.</div>
            </div>
            <div class="chat-input-area">
                <input type="text" id="chatInput" placeholder="Type a message..." onkeypress="handleChatKeyPress(event)">
                <button class="btn" onclick="sendChatMessage()"><i class="fa-solid fa-paper-plane"></i></button>
            </div>
        </div>
    </div>

    <!-- SCRIPT LOGIC -->
    <script>
        // Set your Gemini API key here if available
        const GEMINI_API_KEY = "";

        // --- MOCK DATA ---
        const COLLEGES_DB = [
            { name: "Tech Institute of Excellence", cutoff: 80, stream: "Engineering", location: "California", degree: "B.Tech Computer Science" },
            { name: "Global Management Academy", cutoff: 75, stream: "Management", location: "New York", degree: "BBA Business Analytics" },
            { name: "National Arts University", cutoff: 65, stream: "Arts", location: "Chicago", degree: "BA Digital Media" },
            { name: "Apex Science Campus", cutoff: 85, stream: "Science", location: "Boston", degree: "B.Sc Data Science" }
        ];

        const COURSES_DB = [
            { title: "Full-Stack Web Architecture", provider: "Coursera", price: "Free", difficulty: "Intermediate", desc: "Master modern web development with Hands-on projects." },
            { title: "AI Integration & Machine Learning", provider: "Udemy", price: "$19.99", difficulty: "Advanced", desc: "Build smart apps using generative AI tools." },
            { title: "UI/UX Product Design Core", provider: "edX", price: "Free", difficulty: "Beginner", desc: "Learn human-centric interface design strategies." }
        ];

        const SCHOLARSHIPS_DB = [
            { name: "Future Innovators STEM Grant", amount: "$5,000", eligibility: "12th Marks > 85%", deadline: "Aug 30, 2026" },
            { name: "Global Merit Opportunity Fund", amount: "$10,000", eligibility: "Overall Academic Distinction", deadline: "Sep 15, 2026" }
        ];
        let currentUser = {
            id: 1,
            profile: { p10th: 88, p12th: 82, stream: "Engineering", status: "High School Senior" }
        };

        // --- NAVIGATION ---
        function switchTab(tabId, el) {
            document.querySelectorAll('.tab-content').forEach(t => t.classList.remove('active'));
            document.querySelectorAll('.nav-item button').forEach(b => b.classList.remove('active'));

            document.getElementById(tabId).classList.add('active');
            el.classList.add('active');
        }

        // --- COLLEGES FILTER ENGINE ---
        function renderColleges(data) {
            const grid = document.getElementById('collegesGrid');
            grid.innerHTML = '';
            if (data.length === 0) {
                grid.innerHTML = '<p style="grid-column: 1/-1; color: var(--text-light);">No colleges match your cut-off score.</p>';
                return;
            }
            data.forEach(c => {
                grid.innerHTML += `
                    <div class="card">
                        <div class="card-header">
                            <span class="badge badge-free">${c.stream}</span>
                            <h3 style="margin-top:0.5rem; font-size: 1.1rem;">${c.name}</h3>
                            <p style="color: var(--text-light); font-size: 0.85rem;">${c.location}</p>
                        </div>
                        <div>
                            <p><strong>Degree:</strong> ${c.degree}</p>
                            <p style="color: var(--text-light); font-size: 0.9rem;">Min. Cutoff: <strong>${c.cutoff}%</strong></p>
                        </div>
                        <button class="btn btn-secondary" style="margin-top: 1rem;" onclick="showToast('Application link generated!')">View Details</button>
                    </div>
                `;
            });
        }

        function filterColleges() {
            const score = parseFloat(document.getElementById('calcScore').value) || 0;
            const stream = document.getElementById('calcStream').value;

            const filtered = COLLEGES_DB.filter(c => {
                const matchScore = score >= c.cutoff;
                const matchStream = stream === 'all' || c.stream === stream;
                return matchScore && matchStream;
            });

            renderColleges(filtered);
        }

        // --- COURSES MARKETPLACE ---
        function renderCourses() {
            const grid = document.getElementById('coursesGrid');
            grid.innerHTML = '';
            COURSES_DB.forEach(c => {
                const isFree = c.price.toLowerCase() === 'free';
                grid.innerHTML += `
                    <div class="card">
                        <div class="card-header">
                            <span class="badge ${isFree ? 'badge-free' : 'badge-paid'}">${c.price}</span>
                            <h3 style="margin-top: 0.5rem; font-size: 1.1rem;">${c.title}</h3>
                            <p style="color: var(--text-light); font-size: 0.85rem;">Provider: ${c.provider}</p>
                        </div>
                        <div>
                            <p style="margin-bottom: 0.75rem; font-size: 0.9rem;">${c.desc}</p>
                            <p style="font-size: 0.85rem;"><strong>Level:</strong> ${c.difficulty}</p>
                        </div>
                        <button class="btn btn-secondary" style="margin-top: 1rem;" onclick="showToast('Enrolled in course successfully!')"><i class="fa-solid fa-graduation-cap"></i> Enroll Now</button>
                    </div>
                `;
            });
        }

        // --- SCHOLARSHIPS DIRECTORY ---
        function renderScholarships() {
            const grid = document.getElementById('scholarshipsGrid');
            grid.innerHTML = '';
            SCHOLARSHIPS_DB.forEach(s => {
                grid.innerHTML += `
                    <div class="card">
                        <div class="card-header">
                            <span class="badge badge-free">Grant</span>
                            <h3 style="margin-top: 0.5rem; font-size: 1.1rem;">${s.name}</h3>
                            <p style="color: var(--text-light); font-size: 0.85rem;">Deadline: ${s.deadline}</p>
                        </div>
                        <div>
                            <p style="color: #166534; font-weight: 700; font-size: 1.2rem;">${s.amount}</p>
                            <p style="color: var(--text-light); font-size: 0.85rem; margin-top: 0.5rem;"><strong>Eligibility:</strong> ${s.eligibility}</p>
                        </div>
                        <button class="btn btn-secondary" style="margin-top: 1rem;" onclick="showToast('Scholarship application window opened.')"><i class="fa-solid fa-paper-plane"></i> Apply Grant</button>
                    </div>
                `;
            });
        }

        // --- PROFILE MANAGEMENT ---
        function loadProfileData() {
            if (!currentUser || !currentUser.profile) return;
            const p = currentUser.profile;
            if (p.p10th) document.getElementById('p10th').value = p.p10th;
            if (p.p12th) document.getElementById('p12th').value = p.p12th;
            if (p.stream) document.getElementById('pStream').value = p.stream;
            if (p.status) document.getElementById('pStatus').value = p.status;

            if (p.p12th) document.getElementById('calcScore').value = p.p12th;
            if (p.stream) document.getElementById('calcStream').value = p.stream;
        }

        function saveProfile(e) {
            e.preventDefault();
            if (!currentUser) return;

            currentUser.profile = {
                p10th: document.getElementById('p10th').value,
                p12th: document.getElementById('p12th').value,
                stream: document.getElementById('pStream').value,
                status: document.getElementById('pStatus').value
            };

            showToast('Profile saved successfully!');
            loadProfileData();
        }

        // --- CHATBOT SYSTEM ---
        function toggleChat() {
            const chatWin = document.getElementById('chatWindow');
            chatWin.classList.toggle('hidden');
        }

        function handleChatKeyPress(e) {
            if (e.key === 'Enter') sendChatMessage();
        }

        function sendChatMessage() {
            const input = document.getElementById('chatInput');
            const text = input.value.trim();
            if (!text) return;

            appendMessage('user', text);
            input.value = '';
            processBotResponse(text);
        }

        function appendMessage(sender, text) {
            const container = document.getElementById('chatMessages');
            const msgDiv = document.createElement('div');
            msgDiv.className = `message ${sender}`;
            msgDiv.innerText = text;
            container.appendChild(msgDiv);
            container.scrollTop = container.scrollHeight;
        }

        async function processBotResponse(query) {
            if (GEMINI_API_KEY) {
                try {
                    const response = await fetch(`https://generativelanguage.googleapis.com/v1beta/models/gemini-pro:generateContent?key=${GEMINI_API_KEY}`, {
                        method: 'POST',
                        headers: { 'Content-Type': 'application/json' },
                        body: JSON.stringify({
                            contents: [{ parts: [{ text: `You are Nextora AI, an expert career counselor. Answer briefly: ${query}` }] }]
                        })
                    });
                    const data = await response.json();
                    const reply = data.candidates?.[0]?.content?.parts?.[0]?.text || "I'm having trouble connecting right now.";
                    appendMessage('bot', reply);
                    return;
                } catch (e) {
                    console.error('Gemini API Error:', e);
                }
            }

            // Fallback smart response
            setTimeout(() => {
                let response = "I'm here to help you navigate your educational journey! Try exploring colleges based on your scores in the 'Colleges & Degrees' tab.";
                const q = query.toLowerCase();

                if (q.includes('career') || q.includes('profile')) {
                    response = "Based on market trends, fields in Software Engineering, Data Science, and Digital Product Design currently offer the strongest growth prospects.";
                } else if (q.includes('skill') || q.includes('tech')) {
                    response = "In-demand skills for 2026 include AI Integration, Full-Stack Web Development, Data Analytics, and UI/UX Architecture.";
                } else if (q.includes('scholarship') || q.includes('grant')) {
                    response = "You can filter available grants under the Scholarships tab. Keep an eye out for application deadlines!";
                }

                appendMessage('bot', response);
            }, 600);
        }

        // --- TOAST NOTIFICATION UTILITY ---
        function showToast(message) {
            const existing = document.querySelector('.toast');
            if (existing) existing.remove();

            const toast = document.createElement('div');
            toast.className = 'toast';
            toast.innerText = message;
            document.body.appendChild(toast);

            setTimeout(() => {
                toast.style.opacity = '0';
                setTimeout(() => toast.remove(), 300);
            }, 3000);
        }

        // --- INITIALIZATION ---
        window.onload = () => {
            renderColleges(COLLEGES_DB);
            renderCourses();
            renderScholarships();
            loadProfileData();
        };
    </script>
</body>
</html>
