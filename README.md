# Nextora
the career path website for student
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Nextora — Inclusive Student College & Career Roadmap Portal</title>
    <!-- Tailwind CSS for high-fidelity interactive styling -->
    <script src="https://cdn.jsdelivr.net/npm/@tailwindcss/browser@4"></script>
    <!-- Lucide Icons for scannable UI layout components -->
    <script src="https://unpkg.com/lucide@latest"></script>
    <style>
        .chat-scroll::-webkit-scrollbar { width: 4px; }
        .chat-scroll::-webkit-scrollbar-thumb { background-color: #cbd5e1; border-radius: 4px; }
    </style>
</head>
<body class="bg-slate-50 font-sans text-slate-800 antialiased">

    <!-- Header Block -->
    <header class="sticky top-0 z-40 bg-white/80 border-b border-slate-200 backdrop-blur-md">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 h-16 flex items-center justify-between">
            <div class="flex items-center gap-2">
                <div class="p-2 bg-indigo-600 rounded-lg text-white">
                    <i data-lucide="compass" class="w-6 h-6"></i>
                </div>
                <span class="text-xl font-bold tracking-tight bg-gradient-to-r from-indigo-600 to-violet-600 bg-clip-text text-transparent">Nextora</span>
            </div>
            <nav class="hidden md:flex items-center gap-6 text-sm font-medium text-slate-600">
                <a href="#finder" class="hover:text-indigo-600 transition-colors">Unified College Finder</a>
                <a href="#streams" class="hover:text-indigo-600 transition-colors">Market Demands</a>
            </nav>
            <button onclick="toggleChat()" class="flex items-center gap-2 px-4 py-2 bg-indigo-600 text-white rounded-lg text-sm font-semibold hover:bg-indigo-700 shadow-sm transition-all">
                <i data-lucide="bot" class="w-4 h-4"></i>  Talk with Nexto
            </button>
        </div>
    </header>

    <!-- Content Workspace -->
    <main class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-8 grid grid-cols-1 lg:grid-cols-3 gap-8">
        
        <!-- Left Side: Interactive Portal Elements -->
        <div class="lg:col-span-2 space-y-8">
            
            <!-- Hero Dashboard Introduction -->
            <section class="bg-gradient-to-br from-slate-900 to-slate-800 text-white p-6 sm:p-8 rounded-2xl shadow-xl relative overflow-hidden">
                <div class="relative z-10 max-w-xl">
                    <span class="text-xs font-bold uppercase tracking-widest text-indigo-400 bg-indigo-500/10 px-2.5 py-1 rounded-full">Academic Year 2026-2027</span>
                    <h1 class="text-3xl font-extrabold tracking-tight mt-3 mb-2">No Grade Left Behind: Map Your Path.</h1>
                    <p class="text-slate-300 text-sm leading-relaxed">Whether you passed with 40% or topped with 99%, Nextora dynamically matches your profile against accessible government platforms, practical skill milestones, and target structural packages.</p>
                </div>
                <div class="absolute right-0 bottom-0 opacity-10 transform translate-x-1/4 translate-y-1/4">
                    <i data-lucide="graduation-cap" class="w-64 h-64"></i>
                </div>
            </section>

            <!-- Dynamic Interactive Filter Widget -->
            <section id="finder" class="bg-white border border-slate-200 rounded-2xl p-6 shadow-sm">
                <h2 class="text-lg font-bold text-slate-900 mb-4 flex items-center gap-2">
                    <i data-lucide="sliders" class="w-5 h-5 text-indigo-600"></i> Academic Matching System
                </h2>
                
                <div class="grid grid-cols-1 sm:grid-cols-3 gap-4 mb-6">
                    <div>
                        <label class="block text-xs font-bold uppercase tracking-wider text-slate-500 mb-2">Current Stream</label>
                        <select id="streamFilter" onchange="filterColleges()" class="w-full bg-slate-50 border border-slate-200 rounded-lg p-2.5 text-sm focus:outline-none focus:ring-2 focus:ring-indigo-500">
                            <option value="all">All Academic Streams</option>
                            <option value="Science (PCM)">Science (PCM)</option>
                            <option value="Science (PCB)">Science (PCB)</option>
                            <option value="Commerce">Commerce</option>
                            <option value="Arts">Arts / Humanities</option>
                        </select>
                    </div>
                    <div>
                        <label class="block text-xs font-bold uppercase tracking-wider text-slate-500 mb-2">Your Score Range</label>
                        <div class="flex items-center gap-3 bg-slate-50 border border-slate-200 rounded-lg p-2">
                            <input type="range" id="gradeRange" min="40" max="100" value="65" oninput="updateGradeLabel(this.value)" class="w-full h-2 bg-slate-200 rounded-lg appearance-none cursor-pointer accent-indigo-600">
                            <span id="gradeLabel" class="text-sm font-bold text-indigo-600 min-w-[2.5rem] text-right">65%</span>
                        </div>
                    </div>
                    <div>
                        <label class="block text-xs font-bold uppercase tracking-wider text-slate-500 mb-2">Admission Process Type</label>
                        <select id="typeFilter" onchange="filterColleges()" class="w-full bg-slate-50 border border-slate-200 rounded-lg p-2.5 text-sm focus:outline-none focus:ring-2 focus:ring-indigo-500">
                            <option value="all">All Entry Channels</option>
                            <option value="Government Regular">Government Regular</option>
                            <option value="Direct / Open Enrollment">Direct / Open Enrollment</option>
                            <option value="National Entrance / Elite">National Entrance / Elite</option>
                        </select>
                    </div>
                </div>

                <!-- Live Results Placement Node -->
                <div id="collegeContainer" class="space-y-4">
                    <!-- Dynamic JavaScript Rendering Happens Here -->
                </div>
            </section>

            <!-- 2026 Skills Mapping Node -->
            <section id="streams" class="bg-white border border-slate-200 rounded-2xl p-6 shadow-sm">
                <h2 class="text-lg font-bold text-slate-900 mb-2 flex items-center gap-2">
                    <i data-lucide="trending-up" class="w-5 h-5 text-indigo-600"></i> High-Demand Skills Paradigm
                </h2>
                <p class="text-slate-500 text-xs mb-4">Degrees act as access pipelines, but corporate hiring engines strictly compensate actionable domain knowledge:</p>
                <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
                    <div class="p-4 bg-emerald-50/60 rounded-xl border border-emerald-100">
                        <div class="flex items-center gap-2 text-emerald-800 font-bold text-sm mb-1">
                            <i data-lucide="cpu" class="w-4 h-4"></i> Technical Specialization Tracks
                        </div>
                        <p class="text-xs text-emerald-700 leading-relaxed">Prompt Engineering API structures, localized hardware systems troubleshooting, linux architecture layers, and structured data handling framework execution.</p>
                    </div>
                    <div class="p-4 bg-blue-50/60 rounded-xl border border-blue-100">
                        <div class="flex items-center gap-2 text-blue-800 font-bold text-sm mb-1">
                            <i data-lucide="pie-chart" class="w-4 h-4"></i> Commerce, Logistics & Arts
                        </div>
                        <p class="text-xs text-blue-700 leading-relaxed">GST submission filing, Power BI tracking automation, UX design documentation research protocols, and product sales pipeline strategy.</p>
                    </div>
                </div>
            </section>
        </div>

        <!-- Right Side: Tom Chatbot Assistant Interface Container -->
        <div class="lg:col-span-1">
            <div id="chatWidget" class="bg-white border border-slate-200 rounded-2xl shadow-md h-[calc(100vh-8rem)] sticky top-24 flex flex-col overflow-hidden transition-all duration-300">
                <!-- Chat UI Banner -->
                <div class="p-4 bg-gradient-to-r from-indigo-600 to-violet-600 text-white flex items-center justify-between">
                    <div class="flex items-center gap-2">
                        <div class="relative">
                            <div class="w-9 h-9 bg-white/20 rounded-full flex items-center justify-center font-bold text-sm"><i data-lucide="bot" class="w-5 h-5 mx-auto"></i></div>
                            <span class="absolute bottom-0 right-0 w-2.5 h-2.5 bg-emerald-400 border-2 border-white rounded-full"></span>
                        </div>
                        <div>
                            <h3 class="font-bold text-sm leading-none">Nexto</h3>
                            <span class="text-[10px] text-indigo-200">Ask Discover Achieve</span>
                        </div>
                    </div>
                    <button onclick="clearChat()" class="p-1.5 hover:bg-white/10 rounded-lg text-indigo-100 transition-colors" title="Reset Session">
                        <i data-lucide="rotate-ccw" class="w-4 h-4"></i>
                    </button>
                </div>

                <!-- Chat Display Hub -->
                <div id="chatMessages" class="flex-1 p-4 overflow-y-auto chat-scroll space-y-3 bg-slate-50 text-xs">
                    <div class="flex items-start gap-2 max-w-[85%]">
                        <div class="p-1.5 bg-indigo-100 text-indigo-700 rounded-lg shrink-0"><i data-lucide="bot" class="w-3.5 h-3.5"></i></div>
                        <div class="bg-white border border-slate-200 p-3 rounded-xl rounded-tl-none text-slate-700 shadow-xs">
                            Hello! I am **Nexto**. Tell me your board score percentage directly (e.g., *45%, 65%, or 95%*). I am here to detail entry processes, pricing structures, and real-world skills to launch your career path!
                        </div>
                    </div>
                </div>

                <!-- Quick Query Injectors -->
                <div class="p-2 bg-white border-t border-slate-100 flex flex-wrap gap-1.5">
                    <button onclick="sendQuickPrompt('I scored 45% in boards. What open options or diplomas can I get?')" class="text-[10px] bg-slate-100 hover:bg-indigo-50 hover:text-indigo-600 text-slate-600 px-2 py-1 rounded-md transition-colors border border-slate-200/60">Options for 45%?</button>
                    <button onclick="sendQuickPrompt('What is the direct admission process for 60% score bracket?')" class="text-[10px] bg-slate-100 hover:bg-indigo-50 hover:text-indigo-600 text-slate-600 px-2 py-1 rounded-md transition-colors border border-slate-200/60">60% Entry Methods</button>
                    <button onclick="sendQuickPrompt('I passed with 95% PCM, detail premium government options.')" class="text-[10px] bg-slate-100 hover:bg-indigo-50 hover:text-indigo-600 text-slate-600 px-2 py-1 rounded-md transition-colors border border-slate-200/60">95% Elite Tier</button>
                </div>

                <!-- Interaction Box -->
                <div class="p-3 bg-white border-t border-slate-200 flex items-center gap-2">
                    <input type="text" id="userInput" onkeydown="if(event.key==='Enter') sendMessage()" placeholder="Drop your score % or ask Tom anything..." class="flex-1 bg-slate-50 border border-slate-200 rounded-lg px-3 py-2 text-xs focus:outline-none focus:ring-2 focus:ring-indigo-500">
                    <button onclick="sendMessage()" class="p-2 bg-indigo-600 text-white rounded-lg hover:bg-indigo-700 transition-colors shadow-xs shrink-0">
                        <i data-lucide="send" class="w-4 h-4"></i>
                    </button>
                </div>
            </div>
        </div>
    </main>

    <!-- Operational JavaScript Logic -->
    <script>
        // Highly granular mock relational database covering the entire 40% - 100% spectrum
        const collegeDatabase = [
            // --- 90% TO 100% RANGE ---
            { name: "IIT Bombay", location: "Mumbai", stream: "Science (PCM)", degree: "B.Tech (Computer Science / AI)", type: "National Entrance / Elite", cutoff: 95, fees: "₹2.2L / year", package: "₹24.0 LPA", admission: "Clear the JEE Main + Advanced National Entrance pipeline followed by JoSAA centralized counseling parameters.", skills: "AI/ML Compute Frameworks, GPU Operation Management", masterTrack: "M.Tech Neural Systems / MS Data Pipelines" },
            { name: "SRCC (Shri Ram College of Commerce)", location: "Delhi", stream: "Commerce", degree: "B.Com (Honours)", type: "National Entrance / Elite", cutoff: 96, fees: "₹30K / year", package: "₹11.2 LPA", admission: "Mandatory compliance registration through the central NTA portal and achieving elite scores via the standard CUET-UG exam.", skills: "Advanced Financial Modeling, Corporate Valuation Matrix Design", masterTrack: "MBA Finance Architecture / Chartered Accountancy Track" },
            
            // --- 80% TO 89% RANGE ---
            { name: "Delhi Technological University (DTU)", location: "Delhi", stream: "Science (PCM)", degree: "B.Tech (Software Engineering)", type: "Government Regular", cutoff: 87, fees: "₹2.1L / year", package: "₹15.0 LPA", admission: "Apply through JAC Delhi Counselling based squarely on national percentile matrices.", skills: "Full Stack Deployment Architecture, DevOps Enterprise Logic", masterTrack: "M.Tech Distributed Computing ecosystems" },
            { name: "NLSIU Bengaluru", location: "Arts", degree: "BA LLB (Integrated Corporate Law)", type: "National Entrance / Elite", cutoff: 88, fees: "₹2.5L / year", package: "₹14.0 LPA", admission: "Secure high validation merit ranking through the all-India CLAT examination channel.", skills: "Venture Capital compliance structuring, Corporate Governance Law", masterTrack: "LLM International Commercial Frameworks" },

            // --- 70% TO 79% RANGE ---
            { name: "Guru Gobind Singh Indraprastha University", location: "Delhi", stream: "Commerce", degree: "BBA (Banking & Corporate Finance)", type: "Government Regular", cutoff: 76, fees: "₹1.1L / year", package: "₹6.5 LPA", admission: "Participate in the GGSIPU Centralized CET clearing portal or submit normalized secondary CUET marks parameters.", skills: "SQL Data Auditing, Multi-ledger bookkeeping automation inside Excel", masterTrack: "MBA Management Accounting Operations" },
            { name: "St. Xavier's College (Autonomous)", location: "Mumbai", stream: "Arts", degree: "BA (English Media Analytics)", type: "Government Regular", cutoff: 78, fees: "₹12K / year", package: "₹5.5 LPA", admission: "Submit application to the institutional web portal; filtered via normalized combined state board performance indices.", skills: "Media Analytics, Content Architecture Planning, Strategic Copywriting", masterTrack: "MA Mass Communication & Public Relations Strategy" },

            // --- 60% TO 69% RANGE ---
            { name: "Mumbai University Local Hub Centers", location: "Maharashtra", stream: "Science (PCM)", degree: "B.Sc (Information Technology)", type: "Government Regular", cutoff: 64, fees: "₹35K / year", package: "₹4.5 LPA", admission: "Direct university digital enrollment registry system followed by merit desk assignment distributions.", skills: "Linux System Administration, JavaScript Core Ecosystem Troubleshooting", masterTrack: "MCA (Master of Computer Applications)" },
            { name: "Savitribai Phule Pune University Center", location: "Pune", stream: "Commerce", degree: "B.Com (Regular Accountancy)", type: "Government Regular", cutoff: 61, fees: "₹18K / year", package: "₹4.0 LPA", skills: "GST Compliance Pipeline Execution, Commercial Balance Sheet Adjustments", masterTrack: "M.Com Advanced Financial Accounting metrics" },

            // --- 50% TO 59% RANGE ---
            { name: "State Vocational Technical Academies", location: "Pan-India Centers", stream: "Science (PCB)", degree: "Diploma in Medical Lab Technology (DMLT)", type: "Direct / Open Enrollment", cutoff: 52, fees: "₹25K / year", package: "₹3.8 LPA", admission: "Direct walk-in admissions process subject to basic physical high school verification clearance parameters.", skills: "Pathology Diagnostic Automation, Sample Compliance Data Management", masterTrack: "B.Sc Advanced Medical Imaging Systems" },
            { name: "National Institute of Hospitality & Hotel Management", location: "Regional Hubs", stream: "Arts", degree: "B.Sc (Applied Hospitality Operations)", type: "Government Regular", cutoff: 55, fees: "₹95K / year", package: "₹4.2 LPA", admission: "Clear the open institutional application registry and face-to-face communication screening rounds.", skills: "Supply Chain Coordination Systems, Premium Customer Experience Frameworks", masterTrack: "MBA Logistics & Hospitality Systems" },

            // --- 40% TO 49% RANGE (Passed Status) ---
            { name: "IGNOU National Open University", location: "Distance Learning Hub", stream: "Arts", degree: "BA (Tourism Management & Public Admin)", type: "Direct / Open Enrollment", cutoff: 40, fees: "₹7K / year", package: "₹3.2 LPA", skills: "Public Relations Logistics, Local E-Commerce Operations Setup, Excel Basics", masterTrack: "MA Public Administration or Regional Enterprise Execution" },
            { name: "Government Industrial Training Institutes (ITI)", location: "All District Centers", stream: "Science (PCM)", degree: "Advanced Diploma in Electronics System Repair", type: "Direct / Open Enrollment", cutoff: 42, fees: "₹6K / year", package: "₹3.5 LPA", skills: "Hardware Circuit Analysis, Micro-Automation System Assembly Execution", masterTrack: "Lateral Entry structural upgrades to B.Sc Applied Tech" }
        ];

        function updateGradeLabel(val) {
            document.getElementById('gradeLabel').innerText = val + '%';
            filterColleges();
        }

        // Functional filter calculation engine processing score boundaries
        function filterColleges() {
            const stream = document.getElementById('streamFilter').value;
            const targetGrade = parseInt(document.getElementById('gradeRange').value);
            const type = document.getElementById('typeFilter').value;
            const container = document.getElementById('collegeContainer');
            
            container.innerHTML = '';
            
            // Check mapping compatibility across arrays
            const filtered = collegeDatabase.filter(item => {
                const streamMatch = (stream === 'all' || item.stream === stream);
                const gradeMatch = (targetGrade >= item.cutoff);
                const typeMatch = (type === 'all' || item.type === type);
                return streamMatch && gradeMatch && typeMatch;
            });

            if(filtered.length === 0) {
                container.innerHTML = `
                    <div class="text-center p-8 bg-slate-50 border border-dashed border-slate-300 rounded-xl">
                        <i data-lucide="frown" class="w-8 h-8 text-slate-400 mx-auto mb-2"></i>
                        <p class="text-sm font-medium text-slate-600">No matching institutions found at this exact percentage filter point.</p>
                        <p class="text-xs text-slate-400 mt-1">Slide your 'Score Range' slider down to lower percentage tiers to inspect direct open enrollment frameworks!</p>
                    </div>
                `;
                lucide.createIcons();
                return;
            }

            filtered.forEach(col => {
                const card = document.createElement('div');
                card.className = "bg-white border border-slate-200 hover:border-indigo-300 p-5 rounded-xl shadow-xs transition-all duration-200 text-xs";
                card.innerHTML = `
                    <div class="flex flex-col sm:flex-row sm:items-center justify-between gap-2 mb-3">
                        <div>
                            <span class="text-[10px] font-bold uppercase tracking-wider bg-indigo-50 text-indigo-700 px-2 py-0.5 rounded-md">${col.stream || 'All Streams'}</span>
                            <span class="text-[10px] font-bold uppercase tracking-wider bg-slate-100 text-slate-600 px-2 py-0.5 rounded-md ml-1">${col.type}</span>
                            <h3 class="text-base font-bold text-slate-900 mt-1">${col.name} <span class="text-xs font-normal text-slate-500">(${col.location})</span></h3>
                        </div>
                        <div class="text-left sm:text-right shrink-0">
                            <span class="text-[10px] text-slate-400 block uppercase font-semibold">Min Entry Cutoff</span>
                            <span class="text-sm font-extrabold text-indigo-600">≥ ${col.cutoff}%</span>
                        </div>
                    </div>
                    <div class="grid grid-cols-1 sm:grid-cols-3 gap-3 bg-slate-50/80 p-3 rounded-lg border border-slate-100 mb-3">
                        <div><strong class="text-slate-400 block font-normal">Course Degree</strong><span class="text-slate-700 font-bold">${col.degree}</span></div>
                        <div><strong class="text-slate-400 block font-normal">Approximate Fees</strong><span class="text-slate-700 font-bold text-slate-800">${col.fees}</span></div>
                        <div><strong class="text-slate-400 block font-normal">Avg. Placement Package</strong><span class="text-emerald-700 font-bold">${col.package}</span></div>
                    </div>
                    <div class="space-y-2 pt-1 border-t border-slate-100">
                        <p class="text-slate-600 leading-relaxed"><i data-lucide="key-round" class="w-3.5 h-3.5 inline text-amber-500 mr-1 shrink-0"></i><strong>Admission Process:</strong> ${col.admission}</p>
                        <p class="text-slate-600 leading-relaxed"><i data-lucide="shield-check" class="w-3.5 h-3.5 inline text-indigo-500 mr-1 shrink-0"></i><strong>Market Skills:</strong> ${col.skills}</p>
                        <p class="text-slate-600 leading-relaxed"><i data-lucide="git-merge" class="w-3.5 h-3.5 inline text-violet-500 mr-1 shrink-0"></i><strong>Logical Post-Grad Route:</strong> ${col.masterTrack}</p>
                    </div>
                `;
                container.appendChild(card);
            });
            lucide.createIcons();
        }

        // --- Tom Assistant Conversational AI Simulation Script Block ---
        function appendMessage(sender, text) {
            const container = document.getElementById('chatMessages');
            const msgObj = document.createElement('div');
            msgObj.className = sender === 'user' ? "flex items-start gap-2 max-w-[85%] ml-auto flex-row-reverse" : "flex items-start gap-2 max-w-[85%]";
            
            const icon = sender === 'user' ? 'user' : 'bot';
            const bgClass = sender === 'user' ? "bg-indigo-600 text-white rounded-br-none" : "bg-white border border-slate-200 text-slate-700 rounded-tl-none";
            const iconBg = sender === 'user' ? "bg-indigo-700 text-indigo-100" : "bg-indigo-100 text-indigo-700";

            msgObj.innerHTML = `
                <div class="p-1.5 ${iconBg} rounded-lg shrink-0"><i data-lucide="${icon}" class="w-3.5 h-3.5"></i></div>
                <div class="${bgClass} p-3 rounded-xl shadow-xs leading-relaxed">${text}</div>
            `;
            container.appendChild(msgObj);
            container.scrollTop = container.scrollHeight;
            lucide.createIcons();
        }

        function generateNextoResponse(input) {
            const cleanedInput = input.toLowerCase();
            const gradeMatch = cleanedInput.match(/\d+/);
            
            if(gradeMatch) {
                const score = parseInt(gradeMatch[0]);
                if (score >= 90) {
                    return `Scoring **${score}%** places you in the elite bracket! You should target premium channels like **IITs/SRCC via CUET/JEE routes**. Admission depends on national entrance normalization. Your skill target: **AI infrastructure frameworks or premium valuation modeling**.`;
                } else if (score >= 70) {
                    return `With **${score}%**, you have strong options at structured public varsities like **Indraprastha University or St. Xavier's**. Entry is managed via normalized counseling lists. Pair your college track with **SQL databases or advanced media workflows** to maximize placements!`;
                } else if (score >= 60) {
                    return `Your score of **${score}%** matches well with massive state hubs like **Mumbai or Pune University regular wings**. Admission processes are straightforward, relying on standard board cutoffs. Secure your path by building **Linux deployment or core accounting automation skills**!`;
                } else {
                    return `A grade of **${score}%** is a practical starting point! Nextora lists excellent direct-entry tracks like **IGNOU Open University systems** or regional **Government ITI centers**. There are zero entrance test hurdles, fees are exceptionally low (< ₹15k), and learning **applied hardware diagnostics or digital vendor management** will get you hired faster than a generic degree!`;
                }
            }

            if(cleanedInput.includes('skill') || cleanedInput.includes('demand') || cleanedInput.includes('company')) {
                return `Hiring markets prioritize practical skills over theoretical degrees. Tech fields seek **Cloud Architecture and Data Pipeline management**, while Commerce and Arts look for **Power BI parsing, automated GST filing, or corporate compliance legal writing**.`;
            }

            if(cleanedInput.includes('process') || cleanedInput.includes('admission') || cleanedInput.includes('get in')) {
                return `Admission processes fall into three categories: **1. Entrance Exams** (for the 90%+ elite tier like JEE/CUET), **2. Normalized Merit Portals** (for the 60%-80% band), and **3. Direct Open Registration** (for the 40%-50% band, including IGNOU and vocational ITI centers). Adjust the slider to see how they map out!`;
            }

            return `I can help map things out for you! Share your exact score percentage (*e.g., 45% or 78%*) or ask about specific fee frameworks and courses.`;
        }

        function sendMessage() {
            const inputField = document.getElementById('userInput');
            const query = inputField.value.trim();
            if(!query) return;

            appendMessage('user', query);
            inputField.value = '';

            setTimeout(() => {
                const response = generateNextoResponse(query);
                appendMessage('nexto', response);
            }, 400);
        }

        function sendQuickPrompt(text) {
            appendMessage('user', text);
            setTimeout(() => {
                const response = generateTomResponse(text);
                appendMessage('tom', response);
            }, 400);
        }

        function clearChat() {
            const container = document.getElementById('chatMessages');
            container.innerHTML = `
                <div class="flex items-start gap-2 max-w-[85%]">
                    <div class="p-1.5 bg-indigo-100 text-indigo-700 rounded-lg shrink-0"><i data-lucide="bot" class="w-3.5 h-3.5"></i></div>
                    <div class="bg-white border border-slate-200 p-3 rounded-xl rounded-tl-none text-slate-700 shadow-xs">
                        Nextora chatbot session reset! Let me know your target score bands.
                    </div>
                </div>
            `;
            lucide.createIcons();
        }

        function toggleChat() {
            const widget = document.getElementById('chatWidget');
            widget.classList.add('ring-4', 'ring-indigo-500/20');
            setTimeout(() => widget.classList.remove('ring-4', 'ring-indigo-500/20'), 1000);
            widget.scrollIntoView({ behavior: 'smooth', block: 'center' });
        }

        window.onload = () => {
            lucide.createIcons();
            filterColleges();
        };
    </script>
</body>
</html>
