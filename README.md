<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Brain and Mind Academy - 1.2 Functions and Function Notation Worksheet</title>
    
    <!-- MathJax V3 Equation Engine -->
    <script>
        window.MathJax = {
            tex: {
                inlineMath: [['$', '$'], ['\\(', '\\)']],
                displayMath: [['$$', '$$'], ['\\[', '\\]']]
            },
            svg: {
                fontCache: 'global'
            }
        };
    </script>
    <script id="MathJax-script" async src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-svg.js"></script>

    <!-- Desmos API Script -->
    <script src="https://www.desmos.com/api/v1.8/calculator.js?apiKey=d2822b107a6c49f6a00a221957776319"></script>

    <style>
        :root {
            --primary-header: #1e3a8a;
            --header-gradient: linear-gradient(135deg, #0f172a 0%, #1e3a8a 100%);
            --accent-gold: #d97706;
            --accent-gold-light: #fcd34d;
            --correct-green: #059669;
            --correct-bg: #d1fae5;
            --incorrect-red: #dc2626;
            --incorrect-bg: #fee2e2;
            --skipped-orange: #f59e0b;
            --skipped-bg: #fef3c7;
            --bg-body: #f8fafc;
            --text-dark: #1e293b;
            --text-muted: #64748b;
            --border-color: #e2e8f0;
            --card-bg: #ffffff;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            background-color: var(--bg-body);
            color: var(--text-dark);
            min-height: 100vh;
            display: flex;
            flex-direction: column;
        }

        header {
            background: var(--header-gradient);
            color: white;
            padding: 1.25rem 2rem;
            display: flex;
            justify-content: space-between;
            align-items: center;
            box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1);
        }

        .brand-title {
            font-size: 1.5rem;
            font-weight: 700;
            letter-spacing: 0.5px;
            color: #ffffff;
        }

        .brand-subtitle {
            font-size: 0.9rem;
            color: var(--accent-gold-light);
            font-weight: 600;
            margin-top: 2px;
        }

        .user-info {
            display: flex;
            align-items: center;
            gap: 1rem;
        }

        .user-email {
            font-size: 0.85rem;
            background: rgba(255, 255, 255, 0.15);
            padding: 0.4rem 0.8rem;
            border-radius: 6px;
        }

        .btn {
            padding: 0.6rem 1.25rem;
            border: none;
            border-radius: 6px;
            font-weight: 600;
            font-size: 0.9rem;
            cursor: pointer;
            transition: all 0.2s ease;
            display: inline-flex;
            align-items: center;
            justify-content: center;
            gap: 0.5rem;
        }

        .btn-sm {
            padding: 0.4rem 0.85rem;
            font-size: 0.8rem;
            border-radius: 4px;
        }

        .btn-primary { background-color: var(--primary-header); color: white; }
        .btn-primary:hover { background-color: #172554; }
        .btn-gold { background-color: var(--accent-gold); color: white; }
        .btn-gold:hover { background-color: #b45309; }
        .btn-outline { background: transparent; border: 1.5px solid var(--border-color); color: var(--text-dark); }
        .btn-outline:hover { background-color: #f1f5f9; }
        .btn-danger { background-color: var(--incorrect-red); color: white; }
        .btn-danger:hover { background-color: #b91c1c; }
        .btn-success { background-color: var(--correct-green); color: white; }
        .btn-success:hover { background-color: #047857; }

        .screen {
            display: none;
            padding: 2rem;
            max-width: 1400px;
            margin: 0 auto;
            width: 100%;
            flex: 1;
        }

        .screen.active { display: block; }

        #auth-screen {
            max-width: 450px;
            margin: auto;
            padding-top: 4rem;
        }

        .auth-card {
            background: var(--card-bg);
            padding: 2.5rem;
            border-radius: 12px;
            box-shadow: 0 10px 25px -5px rgba(0,0,0,0.05);
            border: 1px solid var(--border-color);
            text-align: center;
        }

        .auth-card h2 { margin-bottom: 0.5rem; color: var(--primary-header); }
        .auth-card p { color: var(--text-muted); font-size: 0.9rem; margin-bottom: 1.5rem; }

        .form-group { margin-bottom: 1.25rem; text-align: left; }
        .form-group label { display: block; margin-bottom: 0.4rem; font-size: 0.85rem; font-weight: 600; }
        .form-group input {
            width: 100%; padding: 0.75rem; border: 1px solid var(--border-color);
            border-radius: 6px; font-size: 1rem; outline: none;
        }
        .form-group input:focus { border-color: var(--primary-header); box-shadow: 0 0 0 3px rgba(30, 58, 138, 0.1); }

        #video-screen { max-width: 850px; margin: auto; }
        .video-card {
            background: var(--card-bg); padding: 2rem; border-radius: 12px;
            border: 1px solid var(--border-color); box-shadow: 0 10px 25px -5px rgba(0,0,0,0.05); text-align: center;
        }
        .video-wrapper {
            position: relative; padding-bottom: 56.25%; height: 0; overflow: hidden;
            border-radius: 8px; margin: 1.5rem 0; background: #000;
        }
        .video-wrapper iframe { position: absolute; top: 0; left: 0; width: 100%; height: 100%; border: 0; }

        .quiz-container {
            display: grid;
            grid-template-columns: 1fr 380px;
            gap: 2rem;
            align-items: start;
        }

        .quiz-card {
            background: var(--card-bg);
            border-radius: 12px;
            padding: 2rem;
            border: 1px solid var(--border-color);
            box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.05);
        }

        .quiz-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            border-bottom: 2px solid var(--bg-body);
            padding-bottom: 1rem;
            margin-bottom: 1.5rem;
        }

        .q-badge {
            background: #eff6ff;
            color: var(--primary-header);
            font-weight: 700;
            padding: 0.3rem 0.8rem;
            border-radius: 20px;
            font-size: 0.85rem;
        }

        .q-title {
            font-size: 1.15rem;
            line-height: 1.6;
            margin-bottom: 1rem;
            font-weight: 700;
            color: var(--primary-header);
        }

        .problem-statement {
            background: #f1f5f9;
            border-left: 4px solid var(--primary-header);
            padding: 1rem 1.25rem;
            border-radius: 6px;
            font-size: 1rem;
            line-height: 1.6;
            margin-bottom: 1.5rem;
            font-weight: 600;
        }

        /* Micro Step Blocks */
        .step-block {
            background: #f8fafc;
            border: 1.5px solid var(--border-color);
            border-radius: 10px;
            padding: 1.25rem;
            margin-bottom: 1.5rem;
            transition: all 0.3s ease;
        }

        .step-block.locked {
            opacity: 0.4;
            pointer-events: none;
            filter: grayscale(0.8);
        }

        .step-block.active-step {
            border-color: var(--primary-header);
            box-shadow: 0 0 0 3px rgba(30, 58, 138, 0.1);
        }

        .step-block.completed-step {
            border-color: var(--correct-green);
            background-color: #f0fdf4;
        }

        .step-block.skipped-step {
            border-color: var(--skipped-orange);
            background-color: var(--skipped-bg);
        }

        .step-header {
            display: flex;
            align-items: center;
            justify-content: space-between;
            margin-bottom: 0.75rem;
        }

        .step-tag {
            font-weight: 700;
            font-size: 0.85rem;
            text-transform: uppercase;
            letter-spacing: 0.5px;
            color: var(--accent-gold);
        }

        .completed-step .step-tag { color: var(--correct-green); }
        .skipped-step .step-tag { color: var(--skipped-orange); }

        .step-prompt {
            font-size: 0.95rem;
            font-weight: 600;
            margin-bottom: 1rem;
            line-height: 1.5;
        }

        .step-actions {
            display: flex;
            gap: 0.5rem;
            margin-top: 1rem;
            padding-top: 0.75rem;
            border-top: 1px dashed var(--border-color);
        }

        .diagram-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 1rem;
            margin-bottom: 0.5rem;
        }

        .diagram-option {
            border: 2px solid var(--border-color);
            border-radius: 8px;
            padding: 0.75rem;
            background: white;
            cursor: pointer;
            text-align: center;
            transition: all 0.2s ease;
        }

        .diagram-option:hover:not(.disabled) {
            border-color: var(--primary-header);
            background-color: #eff6ff;
        }

        .diagram-option.selected {
            border-color: var(--primary-header);
            background-color: #eff6ff;
        }

        .diagram-option.correct {
            border-color: var(--correct-green);
            background-color: var(--correct-bg);
        }

        .diagram-option.incorrect {
            border-color: var(--incorrect-red);
            background-color: var(--incorrect-bg);
        }

        .diagram-option.disabled { cursor: default; }

        .step-options-list {
            display: flex;
            flex-direction: column;
            gap: 0.6rem;
            margin-bottom: 0.5rem;
        }

        .step-option-item {
            display: flex;
            align-items: center;
            padding: 0.75rem 1rem;
            border: 1.5px solid var(--border-color);
            border-radius: 6px;
            cursor: pointer;
            transition: all 0.2s ease;
            background: white;
            font-size: 0.9rem;
            font-weight: 600;
        }

        .step-option-item:hover:not(.disabled) {
            border-color: var(--primary-header);
            background-color: #eff6ff;
        }

        .step-option-item.selected {
            border-color: var(--primary-header);
            background-color: #eff6ff;
        }

        .step-option-item.correct {
            border-color: var(--correct-green);
            background-color: var(--correct-bg);
            color: #065f46;
        }

        .step-option-item.incorrect {
            border-color: var(--incorrect-red);
            background-color: var(--incorrect-bg);
            color: #991b1b;
        }

        .step-option-item.disabled { cursor: default; }

        .step-opt-prefix {
            width: 24px;
            height: 24px;
            border-radius: 50%;
            background: #e2e8f0;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: 700;
            font-size: 0.75rem;
            margin-right: 0.75rem;
            flex-shrink: 0;
        }

        .step-option-item.selected .step-opt-prefix { background: var(--primary-header); color: white; }
        .step-option-item.correct .step-opt-prefix { background: var(--correct-green); color: white; }
        .step-option-item.incorrect .step-opt-prefix { background: var(--incorrect-red); color: white; }

        .action-bar {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding-top: 1.5rem;
            border-top: 1px solid var(--border-color);
        }

        .rationale-box {
            margin-top: 1.5rem;
            padding: 1.25rem;
            border-radius: 8px;
            background: #f1f5f9;
            border-left: 4px solid var(--primary-header);
        }

        .rationale-title { font-weight: 700; color: var(--primary-header); margin-bottom: 0.5rem; }

        .quiz-sidebar {
            display: flex;
            flex-direction: column;
            gap: 1.5rem;
            position: sticky;
            top: 2rem;
        }

        .sidebar-card {
            background: var(--card-bg);
            border-radius: 12px;
            padding: 1.5rem;
            border: 1px solid var(--border-color);
        }

        .sidebar-title {
            font-size: 1.1rem;
            font-weight: 700;
            margin-bottom: 1rem;
            color: var(--primary-header);
        }

        .legend-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 0.5rem;
            margin-bottom: 1.5rem;
            font-size: 0.8rem;
        }

        .legend-item { display: flex; align-items: center; gap: 0.4rem; }
        .legend-dot { width: 12px; height: 12px; border-radius: 3px; }
        .dot-active { border: 2px solid var(--primary-header); background: transparent; }
        .dot-attempted { background: var(--correct-green); }
        .dot-skipped { background: var(--skipped-orange); }
        .dot-unvisited { background: #cbd5e1; }

        .question-grid {
            display: grid;
            grid-template-columns: repeat(5, 1fr);
            gap: 0.5rem;
            max-height: 220px;
            overflow-y: auto;
        }

        .grid-btn {
            aspect-ratio: 1; border: 1px solid var(--border-color); background: #f8fafc;
            color: var(--text-dark); border-radius: 6px; font-weight: 600; font-size: 0.85rem;
            cursor: pointer; transition: all 0.15s ease;
        }

        .grid-btn.active { border: 2px solid var(--primary-header); color: var(--primary-header); font-weight: 800; background: #eff6ff; }
        .grid-btn.attempted { background: var(--correct-green); color: white; border-color: var(--correct-green); }
        .grid-btn.skipped { background: var(--skipped-orange); color: white; border-color: var(--skipped-orange); }

        .calc-display {
            width: 100%;
            padding: 0.6rem;
            font-size: 1.2rem;
            text-align: right;
            border: 1px solid var(--border-color);
            border-radius: 6px;
            margin-bottom: 0.75rem;
            background: #f8fafc;
            font-family: monospace;
            font-weight: bold;
        }

        .calc-grid {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 0.35rem;
        }

        .calc-btn {
            padding: 0.55rem 0.2rem;
            font-size: 0.85rem;
            font-weight: 600;
            border: 1px solid var(--border-color);
            border-radius: 4px;
            background: #fff;
            cursor: pointer;
        }

        .calc-btn:hover { background: #e2e8f0; }
        .calc-btn.op { background: #eff6ff; color: var(--primary-header); }
        .calc-btn.special { background: var(--skipped-bg); color: var(--accent-gold); }

        #desmos-calculator {
            width: 100%;
            height: 280px;
            border-radius: 8px;
            border: 1px solid var(--border-color);
        }

        .results-summary {
            background: var(--card-bg); border-radius: 12px; padding: 2rem;
            border: 1px solid var(--border-color); margin-bottom: 2rem; text-align: center;
        }

        .score-circle {
            width: 130px; height: 130px; border-radius: 50%; background: var(--header-gradient);
            color: white; display: flex; flex-direction: column; align-items: center;
            justify-content: center; margin: 1rem auto;
        }

        .score-num { font-size: 2.2rem; font-weight: 800; color: var(--accent-gold-light); }
        .review-list { display: flex; flex-direction: column; gap: 1.5rem; }
        .review-card { background: var(--card-bg); border-radius: 12px; padding: 1.5rem; border: 1px solid var(--border-color); }

        .status-tag {
            padding: 0.25rem 0.6rem; border-radius: 4px; font-size: 0.75rem;
            font-weight: 700; text-transform: uppercase;
        }

        .tag-correct { background: var(--correct-bg); color: #065f46; }
        .tag-incorrect { background: var(--incorrect-bg); color: #991b1b; }
        .tag-skipped { background: var(--skipped-bg); color: #92400e; }

        @media (max-width: 992px) {
            .quiz-container { grid-template-columns: 1fr; }
            .quiz-sidebar { position: static; }
            .diagram-grid { grid-template-columns: 1fr; }
        }
    </style>
</head>
<body>

    <header>
        <div>
            <div class="brand-title">BRAIN AND MIND ACADEMY</div>
            <div class="brand-subtitle">1.2 Functions and Function Notation • Worksheet Master Practice Sheet</div>
        </div>
        <div class="user-info" id="user-header-info" style="display: none;">
            <span class="user-email" id="display-user-email"></span>
            <button class="btn btn-outline" style="color:white; border-color:rgba(255,255,255,0.3);" onclick="logout()">Switch User</button>
        </div>
    </header>

    <!-- Auth Screen -->
    <div id="auth-screen" class="screen active">
        <div class="auth-card">
            <h2>Student Portal</h2>
            <p>Enter your email address to access your interactive step-by-step learning card sheet.</p>
            <form onsubmit="handleLogin(event)">
                <div class="form-group">
                    <label for="email-input">Email ID</label>
                    <input type="email" id="email-input" required placeholder="student@school.com">
                </div>
                <button type="submit" class="btn btn-primary" style="width: 100%;">Start Practice Sheet</button>
            </form>
        </div>
    </div>

    <!-- Video Gate Screen -->
    <div id="video-screen" class="screen">
        <div class="video-card">
            <h2 style="color: var(--primary-header);">Concept Lesson: 1.2 Functions and Function Notation</h2>
            <p style="color: var(--text-muted); margin-top: 0.5rem;">Watch Jensen's concept lesson video before attempting the practice sheet.</p>
            
            <div class="video-wrapper">
                <iframe src="https://www.youtube.com/embed/qgRsd_7CWOc" title="1.2 Functions and Function Notation" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
            </div>

            <div style="margin-top: 1.5rem;">
                <p style="font-weight: 600; margin-bottom: 1rem; color: var(--text-dark);">Have you watched the concept lesson video?</p>
                <button class="btn btn-success" style="font-size: 1rem; padding: 0.75rem 2rem;" onclick="approveVideoAndStart()">Yes, I have watched the video & I'm ready! &rarr;</button>
            </div>
        </div>
    </div>

    <!-- Quiz Screen -->
    <div id="quiz-screen" class="screen">
        <div class="quiz-container">
            <div class="quiz-card">
                <div class="quiz-header">
                    <span class="q-badge" id="q-number-badge">Card 1 of 14</span>
                    <span style="font-size: 0.85rem; color: var(--text-muted);">Worksheet Card</span>
                </div>

                <div class="q-title" id="q-title-text"></div>
                <div class="problem-statement" id="q-problem-text"></div>

                <!-- STEP 1 BLOCK: Visual / Model Choice -->
                <div class="step-block active-step" id="step1-block">
                    <div class="step-header">
                        <span class="step-tag">Step 1: Function Model Choice</span>
                        <span id="step1-status-tag" style="font-weight:700; font-size:0.8rem; color:var(--accent-gold);">In Progress</span>
                    </div>
                    <div class="step-prompt" id="step1-prompt">Select the correct visual representation model:</div>
                    <div class="diagram-grid" id="step1-diagram-grid"></div>
                    <div class="step-actions" id="step1-actions">
                        <button class="btn btn-primary btn-sm" onclick="checkStep(1)">Check Step 1</button>
                        <button class="btn btn-gold btn-sm" onclick="skipStep(1)">Skip Step 1</button>
                    </div>
                </div>

                <!-- STEP 2 BLOCK: Expression / Substitution Setup -->
                <div class="step-block locked" id="step2-block">
                    <div class="step-header">
                        <span class="step-tag">Step 2: Substitution & Setup</span>
                        <span id="step2-status-tag" style="font-weight:700; font-size:0.8rem; color:var(--text-muted);">Locked</span>
                    </div>
                    <div class="step-prompt" id="step2-prompt">Formulate the algebraic substitution or condition:</div>
                    <div class="step-options-list" id="step2-options-container"></div>
                    <div class="step-actions" id="step2-actions" style="display:none;">
                        <button class="btn btn-primary btn-sm" onclick="checkStep(2)">Check Step 2</button>
                        <button class="btn btn-gold btn-sm" onclick="skipStep(2)">Skip Step 2</button>
                    </div>
                </div>

                <!-- STEP 3 BLOCK: Calculation & Final Answer -->
                <div class="step-block locked" id="step3-block">
                    <div class="step-header">
                        <span class="step-tag">Step 3: Final Calculation</span>
                        <span id="step3-status-tag" style="font-weight:700; font-size:0.8rem; color:var(--text-muted);">Locked</span>
                    </div>
                    <div class="step-prompt" id="step3-prompt">Calculate the final evaluated values:</div>
                    <div class="step-options-list" id="step3-options-container"></div>
                    <div class="step-actions" id="step3-actions" style="display:none;">
                        <button class="btn btn-primary btn-sm" onclick="checkStep(3)">Check Step 3</button>
                        <button class="btn btn-gold btn-sm" onclick="skipStep(3)">Skip Step 3</button>
                    </div>
                </div>

                <div class="action-bar">
                    <button class="btn btn-danger" id="skip-card-btn" onclick="skipEntireCard()">Skip Entire Card</button>
                    <button class="btn btn-outline" id="next-btn" style="display: none;" onclick="nextQuestion()">Next Card &rarr;</button>
                </div>

                <div class="rationale-box" id="rationale-container" style="display: none;">
                    <div class="rationale-title">Complete Step-by-Step Solution Summary</div>
                    <div id="rationale-text" style="font-size: 0.95rem; line-height: 1.6;"></div>
                </div>
            </div>

            <!-- Sidebar -->
            <div class="quiz-sidebar">
                <div class="sidebar-card">
                    <div class="sidebar-title">Card Palette (1–14)</div>
                    <div class="legend-grid">
                        <div class="legend-item"><div class="legend-dot dot-active"></div> Active</div>
                        <div class="legend-item"><div class="legend-dot dot-attempted"></div> Submitted</div>
                        <div class="legend-item"><div class="legend-dot dot-skipped"></div> Skipped</div>
                        <div class="legend-item"><div class="legend-dot dot-unvisited"></div> Unvisited</div>
                    </div>
                    <div class="question-grid" id="question-grid"></div>
                    <div style="margin-top: 1rem;">
                        <button class="btn btn-danger" style="width: 100%;" onclick="finishTest()">Finish & Submit Sheet</button>
                    </div>
                </div>

                <!-- Desmos Graphing Calculator Embed -->
                <div class="sidebar-card">
                    <div class="sidebar-title" style="margin-bottom:0.5rem;">Desmos Graph Plotter</div>
                    <div id="desmos-calculator"></div>
                </div>

                <!-- Scientific Calculator -->
                <div class="sidebar-card">
                    <div class="sidebar-title" style="margin-bottom:0.5rem;">Scientific Calculator</div>
                    <input type="text" class="calc-display" id="calc-disp" readonly value="0">
                    <div class="calc-grid">
                        <button class="calc-btn special" onclick="calcInput('**2')">x²</button>
                        <button class="calc-btn special" onclick="calcSqrt()">√x</button>
                        <button class="calc-btn special" onclick="calcVal(11)">11</button>
                        <button class="calc-btn op" onclick="calcClear()">C</button>

                        <button class="calc-btn" onclick="calcInput('7')">7</button>
                        <button class="calc-btn" onclick="calcInput('8')">8</button>
                        <button class="calc-btn" onclick="calcInput('9')">9</button>
                        <button class="calc-btn op" onclick="calcInput('/')">÷</button>
                        
                        <button class="calc-btn" onclick="calcInput('4')">4</button>
                        <button class="calc-btn" onclick="calcInput('5')">5</button>
                        <button class="calc-btn" onclick="calcInput('6')">6</button>
                        <button class="calc-btn op" onclick="calcInput('*')">×</button>
                        
                        <button class="calc-btn" onclick="calcInput('1')">1</button>
                        <button class="calc-btn" onclick="calcInput('2')">2</button>
                        <button class="calc-btn" onclick="calcInput('3')">3</button>
                        <button class="calc-btn op" onclick="calcInput('-')">-</button>
                        
                        <button class="calc-btn" onclick="calcInput('0')">0</button>
                        <button class="calc-btn" onclick="calcInput('.')">.</button>
                        <button class="calc-btn op" style="grid-column: span 2;" onclick="calcEval()">=</button>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <!-- Review Screen -->
    <div id="review-screen" class="screen">
        <div class="results-summary">
            <h2>Performance Summary</h2>
            <div class="score-circle">
                <span class="score-num" id="final-score">0 / 14</span>
                <span style="font-size: 0.8rem; opacity: 0.8;">Score</span>
            </div>
            <button class="btn btn-primary" onclick="restartQuiz()">Retake Sheet</button>
        </div>

        <h3 style="margin-bottom: 1rem; color: var(--primary-header);">Worksheet Answer Sheet Review</h3>
        <div class="review-list" id="review-list"></div>
    </div>

    <script>
        const AudioFX = {
            ctx: null,
            init() {
                if (!this.ctx) {
                    this.ctx = new (window.AudioContext || window.webkitAudioContext)();
                }
                if (this.ctx.state === 'suspended') {
                    this.ctx.resume();
                }
            },
            playCorrectBell() {
                this.init();
                const now = this.ctx.currentTime;
                const playSingleBell = (freq, time, duration) => {
                    const osc = this.ctx.createOscillator();
                    const gain = this.ctx.createGain();

                    osc.type = 'sine';
                    osc.frequency.setValueAtTime(freq, time);

                    gain.gain.setValueAtTime(0, time);
                    gain.gain.linearRampToValueAtTime(0.3, time + 0.01);
                    gain.gain.exponentialRampToValueAtTime(0.001, time + duration);

                    osc.connect(gain);
                    gain.connect(this.ctx.destination);

                    osc.start(time);
                    osc.stop(time + duration);
                };

                playSingleBell(880, now, 0.8);        
                playSingleBell(1318.51, now + 0.12, 1.2); 
            },
            playIncorrectBell() {
                this.init();
                const now = this.ctx.currentTime;

                const osc = this.ctx.createOscillator();
                const gain = this.ctx.createGain();

                osc.type = 'triangle';
                osc.frequency.setValueAtTime(220, now); 

                gain.gain.setValueAtTime(0, now);
                gain.gain.linearRampToValueAtTime(0.35, now + 0.01);
                gain.gain.exponentialRampToValueAtTime(0.001, now + 0.6);

                osc.connect(gain);
                gain.connect(this.ctx.destination);

                osc.start(now);
                osc.stop(now + 0.6);
            },
            playSkipChime() {
                this.init();
                const now = this.ctx.currentTime;

                const osc = this.ctx.createOscillator();
                const gain = this.ctx.createGain();

                osc.type = 'sine';
                osc.frequency.setValueAtTime(523.25, now); 
                osc.frequency.exponentialRampToValueAtTime(392, now + 0.15); 

                gain.gain.setValueAtTime(0.15, now);
                gain.gain.exponentialRampToValueAtTime(0.001, now + 0.15);

                osc.connect(gain);
                gain.connect(this.ctx.destination);

                osc.start(now);
                osc.stop(now + 0.15);
            }
        };

        const CHAPTER_KEY = "CHAPTER_MCR3U_1_2_WORKSHEET_MATHJAX";

        const makeSVG = (type) => {
            if (type === 'machine') {
                return `<svg width="200" height="110" viewBox="0 0 200 110">
                    <rect x="40" y="30" width="120" height="50" rx="6" fill="#eff6ff" stroke="#1e3a8a" stroke-width="2"/>
                    <path d="M 60 10 L 60 30 M 55 10 L 65 10" stroke="#1e3a8a" stroke-width="2"/>
                    <path d="M 140 80 L 140 100 M 135 100 L 145 100" stroke="#1e3a8a" stroke-width="2"/>
                    <text x="50" y="20" font-size="10" font-weight="bold" fill="#1e3a8a">INPUT x</text>
                    <text x="52" y="60" font-size="11" font-weight="bold" fill="#1e3a8a">FUNCTION f</text>
                    <text x="110" y="105" font-size="10" font-weight="bold" fill="#059669">OUTPUT f(x)</text>
                </svg>`;
            }
            if (type === 'mapping_a') {
                return `<svg width="220" height="120" viewBox="0 0 220 120">
                    <ellipse cx="50" cy="60" rx="35" ry="50" fill="#eff6ff" stroke="#1e3a8a" stroke-width="2"/>
                    <ellipse cx="170" cy="60" rx="35" ry="50" fill="#eff6ff" stroke="#1e3a8a" stroke-width="2"/>
                    <text x="40" y="35" font-size="9" font-weight="bold">1</text>
                    <text x="40" y="50" font-size="9" font-weight="bold">2</text>
                    <text x="40" y="65" font-size="9" font-weight="bold">3</text>
                    <text x="40" y="80" font-size="9" font-weight="bold">4</text>
                    <text x="170" y="35" font-size="9" font-weight="bold">1</text>
                    <text x="170" y="50" font-size="9" font-weight="bold">4</text>
                    <text x="170" y="65" font-size="9" font-weight="bold">9</text>
                    <text x="170" y="80" font-size="9" font-weight="bold">16</text>
                    <line x1="55" y1="32" x2="160" y2="32" stroke="#dc2626" stroke-width="1.5"/>
                    <line x1="55" y1="47" x2="160" y2="47" stroke="#dc2626" stroke-width="1.5"/>
                    <line x1="55" y1="62" x2="160" y2="62" stroke="#dc2626" stroke-width="1.5"/>
                    <line x1="55" y1="77" x2="160" y2="77" stroke="#dc2626" stroke-width="1.5"/>
                </svg>`;
            }
            if (type === 'mapping_d') {
                return `<svg width="220" height="120" viewBox="0 0 220 120">
                    <ellipse cx="50" cy="60" rx="35" ry="50" fill="#fee2e2" stroke="#dc2626" stroke-width="2"/>
                    <ellipse cx="170" cy="60" rx="35" ry="50" fill="#fee2e2" stroke="#dc2626" stroke-width="2"/>
                    <text x="40" y="35" font-size="9" font-weight="bold">-1</text>
                    <text x="40" y="55" font-size="9" font-weight="bold">1</text>
                    <text x="40" y="75" font-size="9" font-weight="bold">3</text>
                    <text x="40" y="95" font-size="9" font-weight="bold">5</text>
                    <text x="170" y="30" font-size="9" font-weight="bold">-3</text>
                    <text x="170" y="50" font-size="9" font-weight="bold">-1</text>
                    <text x="170" y="70" font-size="9" font-weight="bold">0</text>
                    <text x="170" y="90" font-size="9" font-weight="bold">2</text>
                    <line x1="55" y1="32" x2="160" y2="28" stroke="#dc2626" stroke-width="1.5"/>
                    <line x1="55" y1="52" x2="160" y2="28" stroke="#dc2626" stroke-width="1.5"/>
                    <line x1="55" y1="52" x2="160" y2="68" stroke="#dc2626" stroke-width="1.5"/>
                </svg>`;
            }
            return `<svg width="180" height="110" viewBox="0 0 200 120"><rect x="10" y="10" width="180" height="100" fill="#f1f5f9"/><text x="50" y="60" font-size="12">Diagram ${type}</text></svg>`;
        };

        // ALL Questions rendered in LaTeX Equation Editor Format
        const questionsData = [
            // Card 1: Q1a & Q1b
            {
                id: 1,
                title: "Card 1 (Worksheet Q1a & Q1b): Evaluate $f(4)$, $f(-5)$, and $f\\left(-\\frac{2}{3}\\right)$",
                problem: "For functions a) $f(x) = \\frac{2}{5}x + 11$ and b) $f(x) = 3x^2 + 2x + 1$, evaluate $f(4)$, $f(-5)$, and $f\\left(-\\frac{2}{3}\\right)$.",
                step1: {
                    prompt: "Select the Function Machine model representing algebraic substitution:",
                    diagrams: [
                        { svg: makeSVG('machine'), correct: true },
                        { svg: makeSVG('mapping_a'), correct: false },
                        { svg: makeSVG('mapping_d'), correct: false }
                    ]
                },
                step2: {
                    prompt: "For a) $f(x) = \\frac{2}{5}x + 11$, formulate substitutions and evaluate:",
                    options: [
                        "$f(4) = \\frac{63}{5}$, $f(-5) = 9$, $f\\left(-\\frac{2}{3}\\right) = \\frac{161}{15}$",
                        "$f(4) = \\frac{63}{5}$, $f(-5) = 11$, $f\\left(-\\frac{2}{3}\\right) = \\frac{165}{15}$",
                        "$f(4) = 12$, $f(-5) = 9$, $f\\left(-\\frac{2}{3}\\right) = 10$"
                    ],
                    correct: 0
                },
                step3: {
                    prompt: "For b) $f(x) = 3x^2 + 2x + 1$, evaluate $f(4) = 3(16)+8+1$, $f(-5) = 3(25)-10+1$, and $f\\left(-\\frac{2}{3}\\right) = 3\\left(\\frac{4}{9}\\right)-\\frac{4}{3}+1$:",
                    options: [
                        "$f(4) = 57$, $f(-5) = 66$, $f\\left(-\\frac{2}{3}\\right) = 1$",
                        "$f(4) = 57$, $f(-5) = 75$, $f\\left(-\\frac{2}{3}\\right) = 2$",
                        "$f(4) = 48$, $f(-5) = 66$, $f\\left(-\\frac{2}{3}\\right) = 0$"
                    ],
                    correct: 0
                },
                rationale: "<b>Full Solution Summary:</b><br>a) $f(4)=\\frac{63}{5}$, $f(-5)=9$, $f\\left(-\\frac{2}{3}\\right)=\\frac{161}{15}$.<br>b) $f(4)=57$, $f(-5)=66$, $f\\left(-\\frac{2}{3}\\right)=1$."
            },
            // Card 2: Q1c & Q1d
            {
                id: 2,
                title: "Card 2 (Worksheet Q1c & Q1d): Evaluate $f(4)$, $f(-5)$, and $f\\left(-\\frac{2}{3}\\right)$",
                problem: "For functions c) $f(x) = 2(x+4)^2$ and d) $f(x) = -6$, calculate $f(4)$, $f(-5)$, and $f\\left(-\\frac{2}{3}\\right)$.",
                step1: {
                    prompt: "Select the Function Machine diagram:",
                    diagrams: [
                        { svg: makeSVG('machine'), correct: true },
                        { svg: makeSVG('mapping_a'), correct: false }
                    ]
                },
                step2: {
                    prompt: "For c) $f(x) = 2(x+4)^2$, evaluate $f(4) = 2(8)^2$, $f(-5) = 2(-1)^2$, $f\\left(-\\frac{2}{3}\\right) = 2\\left(\\frac{10}{3}\\right)^2$:",
                    options: [
                        "$f(4) = 128$, $f(-5) = 2$, $f\\left(-\\frac{2}{3}\\right) = \\frac{200}{9}$",
                        "$f(4) = 64$, $f(-5) = 2$, $f\\left(-\\frac{2}{3}\\right) = \\frac{100}{9}$",
                        "$f(4) = 128$, $f(-5) = -2$, $f\\left(-\\frac{2}{3}\\right) = \\frac{200}{3}$"
                    ],
                    correct: 0
                },
                step3: {
                    prompt: "For constant function d) $f(x) = -6$, state outputs:",
                    options: [
                        "$f(4) = -6$, $f(-5) = -6$, $f\\left(-\\frac{2}{3}\\right) = -6$",
                        "$f(4) = -6$, $f(-5) = 6$, $f\\left(-\\frac{2}{3}\\right) = 4$",
                        "$f(4) = 0$, $f(-5) = 0$, $f\\left(-\\frac{2}{3}\\right) = 0$"
                    ],
                    correct: 0
                },
                rationale: "<b>Full Solution Summary:</b><br>c) $f(4)=128$, $f(-5)=2$, $f\\left(-\\frac{2}{3}\\right)=\\frac{200}{9}$.<br>d) Constant $f(x)=-6$ outputs $-6$ for all inputs."
            },
            // Card 3: Q1e & Q1f
            {
                id: 3,
                title: "Card 3 (Worksheet Q1e & Q1f): Evaluate $f(4)$, $f(-5)$, and $f\\left(-\\frac{2}{3}\\right)$",
                problem: "For functions e) $f(x) = \\frac{1}{x}$ and f) $f(x) = \\sqrt{x+5}$, calculate $f(4)$, $f(-5)$, and $f\\left(-\\frac{2}{3}\\right)$.",
                step1: {
                    prompt: "Select Function Machine diagram:",
                    diagrams: [
                        { svg: makeSVG('machine'), correct: true },
                        { svg: makeSVG('mapping_d'), correct: false }
                    ]
                },
                step2: {
                    prompt: "For e) $f(x) = \\frac{1}{x}$, evaluate $f(4)$, $f(-5)$, $f\\left(-\\frac{2}{3}\\right)$:",
                    options: [
                        "$f(4) = \\frac{1}{4}$, $f(-5) = -\\frac{1}{5}$, $f\\left(-\\frac{2}{3}\\right) = -\\frac{3}{2}$",
                        "$f(4) = \\frac{1}{4}$, $f(-5) = \\frac{1}{5}$, $f\\left(-\\frac{2}{3}\\right) = \\frac{2}{3}$",
                        "$f(4) = 4$, $f(-5) = -5$, $f\\left(-\\frac{2}{3}\\right) = -1.5$"
                    ],
                    correct: 0
                },
                step3: {
                    prompt: "For f) $f(x) = \\sqrt{x+5}$, evaluate $f(4) = \\sqrt{9}$, $f(-5) = \\sqrt{0}$, $f\\left(-\\frac{2}{3}\\right) = \\sqrt{\\frac{13}{3}}$:",
                    options: [
                        "$f(4) = 3$, $f(-5) = 0$, $f\\left(-\\frac{2}{3}\\right) = \\sqrt{\\frac{13}{3}}$",
                        "$f(4) = 9$, $f(-5) = 0$, $f\\left(-\\frac{2}{3}\\right) = \\sqrt{\\frac{13}{3}}$",
                        "$f(4) = 3$, $f(-5) = 0$, $f\\left(-\\frac{2}{3}\\right) = \\frac{13}{3}$"
                    ],
                    correct: 0
                },
                rationale: "<b>Full Solution Summary:</b><br>e) $f(4)=\\frac{1}{4}$, $f(-5)=-\\frac{1}{5}$, $f\\left(-\\frac{2}{3}\\right)=-\\frac{3}{2}$.<br>f) $f(4)=3$, $f(-5)=0$, $f\\left(-\\frac{2}{3}\\right)=\\sqrt{\\frac{13}{3}}$."
            },
            // Card 4: Q2
            {
                id: 4,
                title: "Card 4 (Worksheet Q2): Quadratic $f(x) = x^2 + 2$",
                problem: "If $f(x) = x^2 + 2$, state $f(1)$, $f(0)$, $f(2)$, $f(-2)$, $f(3)$, and $f\\left(\\frac{1}{2}\\right)$.",
                step1: {
                    prompt: "Select Function Machine visual:",
                    diagrams: [
                        { svg: makeSVG('machine'), correct: true },
                        { svg: makeSVG('mapping_a'), correct: false }
                    ]
                },
                step2: {
                    prompt: "Evaluate integer inputs: $f(1)$, $f(0)$, $f(2)$, $f(-2)$, $f(3)$:",
                    options: [
                        "$f(1)=3$, $f(0)=2$, $f(2)=6$, $f(-2)=6$, $f(3)=11$",
                        "$f(1)=3$, $f(0)=0$, $f(2)=6$, $f(-2)=-6$, $f(3)=11$",
                        "$f(1)=1$, $f(0)=2$, $f(2)=4$, $f(-2)=4$, $f(3)=9$"
                    ],
                    correct: 0
                },
                step3: {
                    prompt: "Evaluate fractional input $f\\left(\\frac{1}{2}\\right) = \\left(\\frac{1}{2}\\right)^2 + 2 = \\frac{1}{4} + \\frac{8}{4} = [ _____ ]$:",
                    options: ["$\\frac{9}{4}$", "$\\frac{5}{4}$", "2.5", "3"],
                    correct: 0
                },
                rationale: "<b>Full Solution Summary:</b><br>$f(1)=3, f(0)=2, f(2)=6, f(-2)=6, f(3)=11, f\\left(\\frac{1}{2}\\right)=\\frac{9}{4}$."
            },
            // Card 5: Q3a-e
            {
                id: 5,
                title: "Card 5 (Worksheet Q3a-e): State $f(4)$ Batch 1",
                problem: "State $f(4)$ for: a) $f(x)=4+5x$, b) $f(x)=x^2-6$, c) $f(t)=9-t$, d) $f(x)=10$, e) $f(z)=z^3$.",
                step1: {
                    prompt: "Select Function Machine diagram:",
                    diagrams: [
                        { svg: makeSVG('machine'), correct: true },
                        { svg: makeSVG('mapping_d'), correct: false }
                    ]
                },
                step2: {
                    prompt: "Evaluate a) $f(4) = 4+5(4) = 24$, b) $f(4) = 16-6 = 10$, c) $f(4) = 9-4 = 5$:",
                    options: [
                        "a) 24, b) 10, c) 5",
                        "a) 20, b) 10, c) 4",
                        "a) 24, b) 22, c) 5"
                    ],
                    correct: 0
                },
                step3: {
                    prompt: "Evaluate d) $f(4) = 10$, e) $f(4) = 4^3 = 64$:",
                    options: [
                        "d) 10, e) 64",
                        "d) 10, e) 12",
                        "d) 4, e) 64"
                    ],
                    correct: 0
                },
                rationale: "<b>Full Solution Summary:</b><br>a) 24, b) 10, c) 5, d) 10, e) 64."
            },
            // Card 6: Q3f-i
            {
                id: 6,
                title: "Card 6 (Worksheet Q3f-i): State $f(4)$ Batch 2",
                problem: "State $f(4)$ for: f) $f(x)=8(5-x)$, g) $f(x)=\\frac{1}{x}$, h) $f(x)=\\sqrt{13-x}$, i) $f(t)=\\frac{1}{t^2}$.",
                step1: {
                    prompt: "Select Function Machine diagram:",
                    diagrams: [
                        { svg: makeSVG('machine'), correct: true },
                        { svg: makeSVG('mapping_a'), correct: false }
                    ]
                },
                step2: {
                    prompt: "Evaluate f) $f(4) = 8(5-4) = 8$, g) $f(4) = \\frac{1}{4}$:",
                    options: [
                        "f) 8, g) $\\frac{1}{4}$",
                        "f) 40, g) 4",
                        "f) 8, g) 4"
                    ],
                    correct: 0
                },
                step3: {
                    prompt: "Evaluate h) $f(4) = \\sqrt{13-4} = 3$, i) $f(4) = \\frac{1}{4^2} = \\frac{1}{16}$:",
                    options: [
                        "h) 3, i) $\\frac{1}{16}$",
                        "h) 9, i) $\\frac{1}{8}$",
                        "h) 3, i) $\\frac{1}{8}$"
                    ],
                    correct: 0
                },
                rationale: "<b>Full Solution Summary:</b><br>f) 8, g) $\\frac{1}{4}$, h) 3, i) $\\frac{1}{16}$."
            },
            // Card 7: Q4a & Q4b
            {
                id: 7,
                title: "Card 7 (Worksheet Q4a & Q4b): Mapping Diagrams Analysis A & B",
                problem: "Write ordered pairs and state function status for mapping diagrams 4a $\{(1,1),(2,4),(3,9),(4,16)\}$ and 4b $\{(-5,11),(-4,6),(-2,-4),(0,-14),(2,-24)\}$.",
                step1: {
                    prompt: "Select Mapping Diagram 4a:",
                    diagrams: [
                        { svg: makeSVG('mapping_a'), correct: true },
                        { svg: makeSVG('mapping_d'), correct: false }
                    ]
                },
                step2: {
                    prompt: "State ordered pairs and function status for 4a:",
                    options: [
                        "$\\{(1,1), (2,4), (3,9), (4,16)\\}$; IS a function",
                        "$\\{(1,1), (2,4), (3,9), (4,16)\\}$; IS NOT a function",
                        "$\\{(1,4), (2,9), (3,16)\\}$; IS a function"
                    ],
                    correct: 0
                },
                step3: {
                    prompt: "State ordered pairs and function status for 4b:",
                    options: [
                        "$\\{(-5,11), (-4,6), (-2,-4), (0,-14), (2,-24)\\}$; IS a function",
                        "$\\{(-5,11), (-4,6), (-2,-4), (0,-14), (2,-24)\\}$; IS NOT a function",
                        "$\\{(11,-5), (6,-4), (-4,-2)\\}$; IS a function"
                    ],
                    correct: 0
                },
                rationale: "<b>Full Solution Summary:</b><br>4a and 4b are both Functions because each domain element maps to exactly one range element."
            },
            // Card 8: Q4c & Q4d
            {
                id: 8,
                title: "Card 8 (Worksheet Q4c & Q4d): Mapping Diagrams Analysis C & D",
                problem: "Write ordered pairs and state function status for mapping diagrams 4c $\{(-4,6),(3,6),(1,6),(5,6)\}$ and 4d $\{(-1,-3),(1,3),(1,0),(3,2),(5,2)\}$.",
                step1: {
                    prompt: "Select Mapping Diagram 4d:",
                    diagrams: [
                        { svg: makeSVG('mapping_d'), correct: true },
                        { svg: makeSVG('mapping_a'), correct: false }
                    ]
                },
                step2: {
                    prompt: "Is relation 4c $\{(-4,6), (3,6), (1,6), (5,6)\}$ a function?",
                    options: [
                        "YES, it is a function (constant output $y = 6$ for different $x$ is allowed).",
                        "NO, because $y = 6$ repeats four times.",
                        "NO, because domain contains negative numbers."
                    ],
                    correct: 0
                },
                step3: {
                    prompt: "Is relation 4d $\{(-1,-3), (1,3), (1,0), (3,2), (5,2)\}$ a function?",
                    options: [
                        "NOT a function, because input $x = 1$ maps to two different outputs (3 and 0).",
                        "IS a function, because all domain elements are distinct.",
                        "IS a function, because range contains 0."
                    ],
                    correct: 0
                },
                rationale: "<b>Full Solution Summary:</b><br>4c IS a function.<br>4d IS NOT a function because input $x = 1$ corresponds to two range values (3 and 0)."
            },
            // Card 9: Q5a
            {
                id: 9,
                title: "Card 9 (Worksheet Q5a): Data Set 5a Mapping Diagram",
                problem: "Show data set 5a $\{(1,4), (2,1), (3,-2), (4,-5), (5,-8), (6,-11), (7,-14), (8,-17)\}$ in a mapping diagram and state if it is a function.",
                step1: {
                    prompt: "Select Function Machine or Mapping representation model:",
                    diagrams: [
                        { svg: makeSVG('machine'), correct: true },
                        { svg: makeSVG('mapping_d'), correct: false }
                    ]
                },
                step2: {
                    prompt: "Identify domain and range elements for data set 5a:",
                    options: [
                        "Domain: $\\{1, 2, 3, 4, 5, 6, 7, 8\\}$, Range: $\\{-17, -14, -11, -8, -5, -2, 1, 4\\}$",
                        "Domain: $\\{-17, -14, -11, -8, -5, -2, 1, 4\\}$, Range: $\\{1, 2, 3, 4, 5, 6, 7, 8\\}$",
                        "Domain: $\\{1, 2, 3, 4\\}$, Range: $\\{4, 1, -2, -5\\}$"
                    ],
                    correct: 0
                },
                step3: {
                    prompt: "Is data set 5a a function?",
                    options: [
                        "YES, it is a function (each $x$-value from 1 to 8 maps to exactly one $y$-value).",
                        "NO, because the outputs decrease continuously.",
                        "NO, because range values are negative."
                    ],
                    correct: 0
                },
                rationale: "<b>Full Solution Summary:</b><br>1) Domain = $\\{1..8\\}$, Range = $\\{-17..4\\}$.<br>2) Function: YES, each input has one output."
            },
            // Card 10: Q5b
            {
                id: 10,
                title: "Card 10 (Worksheet Q5b): Data Set 5b Mapping Diagram",
                problem: "Show data set 5b $\{(-3,4), (-2,-1), (-1,-4), (0,-5), (1,4), (2,-1)\}$ in a mapping diagram and state if it is a function.",
                step1: {
                    prompt: "Select representation model:",
                    diagrams: [
                        { svg: makeSVG('machine'), correct: true },
                        { svg: makeSVG('mapping_a'), correct: false }
                    ]
                },
                step2: {
                    prompt: "Identify distinct domain and range sets for data set 5b:",
                    options: [
                        "Domain: $\\{-3, -2, -1, 0, 1, 2\\}$, Range: $\\{-5, -4, -1, 4\\}$",
                        "Domain: $\\{-5, -4, -1, 4\\}$, Range: $\\{-3, -2, -1, 0, 1, 2\\}$",
                        "Domain: $\\{-3, -2, -1, 0, 1, 2\\}$, Range: $\\{-3, -2, -1, 0, 1, 2\\}$"
                    ],
                    correct: 0
                },
                step3: {
                    prompt: "Is data set 5b a function?",
                    options: [
                        "YES, it is a function (each domain element maps to 1 output; repeating $y$-values 4 and -1 is allowed).",
                        "NO, because $y = 4$ and $y = -1$ repeat for different $x$-values.",
                        "NO, because minimum is -5."
                    ],
                    correct: 0
                },
                rationale: "<b>Full Solution Summary:</b><br>1) Domain = $\\{-3..2\\}$, Range = $\\{-5, -4, -1, 4\\}$.<br>2) Function: YES (parabolic relation values)."
            },
            // Card 11: Q5c
            {
                id: 11,
                title: "Card 11 (Worksheet Q5c): Data Set 5c Mapping Diagram",
                problem: "Show data set 5c $\{(-5,6), (-4,9), (-3,1), (-5,-6), (1,2), (3,8), (8,8)\}$ in a mapping diagram and state if it is a function.",
                step1: {
                    prompt: "Select Mapping Diagram with non-function split arrows:",
                    diagrams: [
                        { svg: makeSVG('mapping_d'), correct: true },
                        { svg: makeSVG('mapping_a'), correct: false }
                    ]
                },
                step2: {
                    prompt: "Identify the domain element that violates the function definition:",
                    options: [
                        "Input $x = -5$ maps to two different outputs (6 and -6).",
                        "Input $x = 8$ maps to 8.",
                        "Range value 8 receives two arrows from $x = 3$ and $x = 8$.",
                        "Input $x = -4$ maps to 9."
                    ],
                    correct: 0
                },
                step3: {
                    prompt: "Is data set 5c a function?",
                    options: [
                        "NOT a function, because $x = -5$ maps to both 6 and -6.",
                        "IS a function, because all other points are valid.",
                        "IS a function, because domain and range are finite."
                    ],
                    correct: 0
                },
                rationale: "<b>Full Solution Summary:</b><br>1) Input $x = -5$ has two outputs (6 and -6).<br>2) Function: NO."
            },
            // Card 12: Q5d
            {
                id: 12,
                title: "Card 12 (Worksheet Q5d): Data Set 5d Mapping Diagram",
                problem: "Show data set 5d $\{(9,9), (7,9), (5,9), (3,9)\}$ in a mapping diagram and state if it is a function.",
                step1: {
                    prompt: "Select Function Machine model:",
                    diagrams: [
                        { svg: makeSVG('machine'), correct: true },
                        { svg: makeSVG('mapping_a'), correct: false }
                    ]
                },
                step2: {
                    prompt: "Identify domain and range sets for data set 5d:",
                    options: [
                        "Domain: $\\{3, 5, 7, 9\\}$, Range: $\\{9\\}$",
                        "Domain: $\\{9\\}$, Range: $\\{3, 5, 7, 9\\}$",
                        "Domain: $\\{3, 5, 7, 9\\}$, Range: $\\{3, 5, 7, 9\\}$"
                    ],
                    correct: 0
                },
                step3: {
                    prompt: "Is data set 5d a function?",
                    options: [
                        "YES, it is a function (each $x$-value $\\{3,5,7,9\\}$ maps to exactly one output, 9).",
                        "NO, because all outputs are equal to 9.",
                        "NO, because $x$-values are odd numbers."
                    ],
                    correct: 0
                },
                rationale: "<b>Full Solution Summary:</b><br>1) Domain = $\\{3,5,7,9\\}$, Range = $\\{9\\}$.<br>2) Function: YES (constant function)."
            },
            // Card 13: Q6a
            {
                id: 13,
                title: "Card 13 (Worksheet Q6a): Domain of $f(x) = \\sqrt{8-x}$",
                problem: "State the domain of the radical function $f(x) = \\sqrt{8-x}$.",
                step1: {
                    prompt: "Select Function Machine model:",
                    diagrams: [
                        { svg: makeSVG('machine'), correct: true },
                        { svg: makeSVG('mapping_a'), correct: false }
                    ]
                },
                step2: {
                    prompt: "Set the radicand non-negative to find domain restriction: $8 - x \\ge 0$:",
                    options: [
                        "$8 \\ge x \\implies x \\le 8$",
                        "$x \\ge 8$",
                        "$x \\neq 8$",
                        "$8 - x > 0 \\implies x < 8$"
                    ],
                    correct: 0
                },
                step3: {
                    prompt: "State the domain in set notation:",
                    options: [
                        "$\\{x \\in \\mathbb{R} \\mid x \\le 8\\}$",
                        "$\\{x \\in \\mathbb{R} \\mid x \\ge 8\\}$",
                        "$\\{x \\in \\mathbb{R} \\mid x \\neq 8\\}$",
                        "$\\{x \\in \\mathbb{R}\\}$"
                    ],
                    correct: 0
                },
                rationale: "<b>Full Solution Summary:</b><br>1) Radicand $8 - x \\ge 0 \\implies x \\le 8$.<br>2) Domain = $\\{x \\in \\mathbb{R} \\mid x \\le 8\\}$."
            },
            // Card 14: Q6b
            {
                id: 14,
                title: "Card 14 (Worksheet Q6b): Domain of $f(x) = \\frac{x^2+3}{(x-1)(x+3)}$",
                problem: "State the domain of the rational function $f(x) = \\frac{x^2+3}{(x-1)(x+3)}$.",
                step1: {
                    prompt: "Select Function Machine model:",
                    diagrams: [
                        { svg: makeSVG('machine'), correct: true },
                        { svg: makeSVG('mapping_d'), correct: false }
                    ]
                },
                step2: {
                    prompt: "Set denominator non-zero to find excluded values: $(x-1)(x+3) \\neq 0$:",
                    options: [
                        "$x - 1 \\neq 0$ and $x + 3 \\neq 0 \\implies x \\neq 1$ and $x \\neq -3$",
                        "$x \\neq -1$ and $x \\neq 3$",
                        "$x^2 + 3 \\neq 0 \\implies x \\neq \\sqrt{-3}$",
                        "$x \\neq 0$"
                    ],
                    correct: 0
                },
                step3: {
                    prompt: "State the domain in set notation:",
                    options: [
                        "$\\{x \\in \\mathbb{R} \\mid x \\neq 1, x \\neq -3\\}$",
                        "$\\{x \\in \\mathbb{R} \\mid x \\neq -1, x \\neq 3\\}$",
                        "$\\{x \\in \\mathbb{R} \\mid x \\le 1\\}$",
                        "$\\{x \\in \\mathbb{R}\\}$"
                    ],
                    correct: 0
                },
                rationale: "<b>Full Solution Summary:</b><br>1) Denominator $(x-1)(x+3) \\neq 0 \\implies x \\neq 1, -3$.<br>2) Domain = $\\{x \\in \\mathbb{R} \\mid x \\neq 1, x \\neq -3\\}$."
            }
        ];

        let currentUser = null;
        let currentQIndex = 0;
        let userState = { answers: {}, status: {}, videoApproved: false, cardSteps: {} };
        let desmosCalc = null;

        function triggerMathJax() {
            if (window.MathJax && MathJax.typesetPromise) {
                MathJax.typesetPromise().catch((err) => console.log(err));
            }
        }

        function initDesmos() {
            const elt = document.getElementById('desmos-calculator');
            if (elt && !desmosCalc && window.Desmos) {
                desmosCalc = Desmos.GraphingCalculator(elt, {
                    expressions: true,
                    keypad: false,
                    settingsMenu: false
                });
                desmosCalc.setExpression({ id: 'g1', latex: 'f(x)=\\frac{2}{5}x+11' });
            }
        }

        function calcInput(val) {
            const d = document.getElementById('calc-disp');
            if (d.value === '0' || d.value === 'Error') d.value = val;
            else d.value += val;
        }

        function calcVal(num) {
            const d = document.getElementById('calc-disp');
            if (d.value === '0' || d.value === 'Error') d.value = num;
            else d.value += num;
        }

        function calcClear() {
            document.getElementById('calc-disp').value = '0';
        }

        function calcEval() {
            const d = document.getElementById('calc-disp');
            try {
                d.value = eval(d.value);
            } catch(e) {
                d.value = 'Error';
            }
        }

        function calcSqrt() {
            const d = document.getElementById('calc-disp');
            try {
                const val = parseFloat(d.value) || 0;
                d.value = Number(Math.sqrt(val).toFixed(4));
            } catch(e) {
                d.value = 'Error';
            }
        }

        function handleLogin(e) {
            e.preventDefault();
            const email = document.getElementById('email-input').value.trim();
            if (email) {
                currentUser = email;
                localStorage.setItem('bm_user_email', email);
                initSession();
            }
        }

        function initSession() {
            document.getElementById('display-user-email').innerText = currentUser;
            document.getElementById('user-header-info').style.display = 'flex';

            const savedData = localStorage.getItem(`${currentUser}_${CHAPTER_KEY}`);
            if (savedData) {
                userState = JSON.parse(savedData);
            } else {
                userState = { answers: {}, status: {}, videoApproved: false, cardSteps: {} };
            }

            if (!userState.videoApproved) {
                switchScreen('video-screen');
            } else {
                startQuizScreen();
            }
        }

        function approveVideoAndStart() {
            userState.videoApproved = true;
            saveState();
            startQuizScreen();
        }

        function startQuizScreen() {
            switchScreen('quiz-screen');
            renderGrid();
            loadQuestion(0);
            setTimeout(initDesmos, 300);
        }

        function logout() {
            localStorage.removeItem('bm_user_email');
            currentUser = null;
            document.getElementById('user-header-info').style.display = 'none';
            switchScreen('auth-screen');
        }

        function saveState() {
            if (currentUser) {
                localStorage.setItem(`${currentUser}_${CHAPTER_KEY}`, JSON.stringify(userState));
            }
        }

        function switchScreen(id) {
            document.querySelectorAll('.screen').forEach(s => s.classList.remove('active'));
            document.getElementById(id).classList.add('active');
        }

        function renderGrid() {
            const grid = document.getElementById('question-grid');
            grid.innerHTML = '';
            questionsData.forEach((q, idx) => {
                const btn = document.createElement('button');
                btn.className = 'grid-btn';
                btn.innerText = idx + 1;

                if (idx === currentQIndex) btn.classList.add('active');
                if (userState.status[idx] === 'submitted') btn.classList.add('attempted');
                if (userState.status[idx] === 'skipped') btn.classList.add('skipped');

                btn.onclick = () => jumpToQuestion(idx);
                grid.appendChild(btn);
            });
        }

        function loadQuestion(index) {
            currentQIndex = index;
            const q = questionsData[index];

            document.getElementById('q-number-badge').innerText = `Card ${index + 1} of ${questionsData.length}`;
            document.getElementById('q-title-text').innerHTML = q.title;
            document.getElementById('q-problem-text').innerHTML = q.problem;

            if (!userState.cardSteps[index]) {
                userState.cardSteps[index] = {
                    s1Selection: null, s1Status: 'unattempted',
                    s2Selection: null, s2Status: 'unattempted',
                    s3Selection: null, s3Status: 'unattempted'
                };
            }

            const cState = userState.cardSteps[index];

            renderStep1UI(q, cState);
            renderStep2UI(q, cState);
            renderStep3UI(q, cState);

            const isCardFinished = userState.status[index] === 'submitted' || userState.status[index] === 'skipped';
            const ratBox = document.getElementById('rationale-container');

            if (isCardFinished) {
                ratBox.style.display = 'block';
                document.getElementById('rationale-text').innerHTML = q.rationale;
                document.getElementById('skip-card-btn').style.display = 'none';
                document.getElementById('next-btn').style.display = 'inline-flex';
            } else {
                ratBox.style.display = 'none';
                document.getElementById('skip-card-btn').style.display = 'inline-flex';
                document.getElementById('next-btn').style.display = 'none';
            }

            renderGrid();
            triggerMathJax();
        }

        function renderStep1UI(q, cState) {
            const s1Block = document.getElementById('step1-block');
            const grid = document.getElementById('step1-diagram-grid');
            const tag = document.getElementById('step1-status-tag');
            const actions = document.getElementById('step1-actions');
            grid.innerHTML = '';

            if (cState.s1Status === 'correct') {
                s1Block.className = 'step-block completed-step';
                tag.innerText = '✓ Correct';
                tag.style.color = 'var(--correct-green)';
                actions.style.display = 'none';
            } else if (cState.s1Status === 'skipped') {
                s1Block.className = 'step-block skipped-step';
                tag.innerText = 'Skipped';
                tag.style.color = 'var(--skipped-orange)';
                actions.style.display = 'none';
            } else {
                s1Block.className = 'step-block active-step';
                tag.innerText = 'In Progress';
                tag.style.color = 'var(--accent-gold)';
                actions.style.display = 'flex';
            }

            q.step1.diagrams.forEach((d, idx) => {
                const item = document.createElement('div');
                item.className = 'diagram-option';

                if (cState.s1Selection === idx) item.classList.add('selected');

                if (cState.s1Status !== 'unattempted' && cState.s1Status !== 'incorrect') {
                    item.classList.add('disabled');
                    if (d.correct) item.classList.add('correct');
                    else if (cState.s1Selection === idx) item.classList.add('incorrect');
                } else if (cState.s1Status === 'incorrect' && cState.s1Selection === idx) {
                    item.classList.add('incorrect');
                    item.onclick = () => selectStep1Selection(idx);
                } else {
                    item.onclick = () => selectStep1Selection(idx);
                }

                item.innerHTML = `<div style="font-size:0.8rem; font-weight:700; margin-bottom:0.25rem;">Option ${String.fromCharCode(65 + idx)}</div>${d.svg}`;
                grid.appendChild(item);
            });
        }

        function selectStep1Selection(idx) {
            const cState = userState.cardSteps[currentQIndex];
            if (cState.s1Status === 'correct' || cState.s1Status === 'skipped') return;
            cState.s1Selection = idx;
            cState.s1Status = 'unattempted';
            saveState();
            loadQuestion(currentQIndex);
        }

        function renderStep2UI(q, cState) {
            const s2Block = document.getElementById('step2-block');
            const container = document.getElementById('step2-options-container');
            const tag = document.getElementById('step2-status-tag');
            const actions = document.getElementById('step2-actions');
            container.innerHTML = '';

            const isStep1Passed = cState.s1Status === 'correct' || cState.s1Status === 'skipped';

            if (!isStep1Passed) {
                s2Block.className = 'step-block locked';
                tag.innerText = 'Locked';
                tag.style.color = 'var(--text-muted)';
                actions.style.display = 'none';
                return;
            }

            if (cState.s2Status === 'correct') {
                s2Block.className = 'step-block completed-step';
                tag.innerText = '✓ Correct';
                tag.style.color = 'var(--correct-green)';
                actions.style.display = 'none';
            } else if (cState.s2Status === 'skipped') {
                s2Block.className = 'step-block skipped-step';
                tag.innerText = 'Skipped';
                tag.style.color = 'var(--skipped-orange)';
                actions.style.display = 'none';
            } else {
                s2Block.className = 'step-block active-step';
                tag.innerText = 'In Progress';
                tag.style.color = 'var(--accent-gold)';
                actions.style.display = 'flex';
            }

            q.step2.options.forEach((optText, idx) => {
                const item = document.createElement('div');
                item.className = 'step-option-item';

                if (cState.s2Selection === idx) item.classList.add('selected');

                if (cState.s2Status !== 'unattempted' && cState.s2Status !== 'incorrect') {
                    item.classList.add('disabled');
                    if (idx === q.step2.correct) item.classList.add('correct');
                    else if (cState.s2Selection === idx) item.classList.add('incorrect');
                } else if (cState.s2Status === 'incorrect' && cState.s2Selection === idx) {
                    item.classList.add('incorrect');
                    item.onclick = () => selectStep2Selection(idx);
                } else {
                    item.onclick = () => selectStep2Selection(idx);
                }

                item.innerHTML = `<div class="step-opt-prefix">${String.fromCharCode(65 + idx)}</div><div>${optText}</div>`;
                container.appendChild(item);
            });
        }

        function selectStep2Selection(idx) {
            const cState = userState.cardSteps[currentQIndex];
            if (cState.s2Status === 'correct' || cState.s2Status === 'skipped') return;
            cState.s2Selection = idx;
            cState.s2Status = 'unattempted';
            saveState();
            loadQuestion(currentQIndex);
        }

        function renderStep3UI(q, cState) {
            const s3Block = document.getElementById('step3-block');
            const container = document.getElementById('step3-options-container');
            const tag = document.getElementById('step3-status-tag');
            const actions = document.getElementById('step3-actions');
            container.innerHTML = '';

            const isStep2Passed = cState.s2Status === 'correct' || cState.s2Status === 'skipped';

            if (!isStep2Passed) {
                s3Block.className = 'step-block locked';
                tag.innerText = 'Locked';
                tag.style.color = 'var(--text-muted)';
                actions.style.display = 'none';
                return;
            }

            if (cState.s3Status === 'correct') {
                s3Block.className = 'step-block completed-step';
                tag.innerText = '✓ Correct';
                tag.style.color = 'var(--correct-green)';
                actions.style.display = 'none';
            } else if (cState.s3Status === 'skipped') {
                s3Block.className = 'step-block skipped-step';
                tag.innerText = 'Skipped';
                tag.style.color = 'var(--skipped-orange)';
                actions.style.display = 'none';
            } else {
                s3Block.className = 'step-block active-step';
                tag.innerText = 'In Progress';
                tag.style.color = 'var(--accent-gold)';
                actions.style.display = 'flex';
            }

            q.step3.options.forEach((optText, idx) => {
                const item = document.createElement('div');
                item.className = 'step-option-item';

                if (cState.s3Selection === idx) item.classList.add('selected');

                if (cState.s3Status !== 'unattempted' && cState.s3Status !== 'incorrect') {
                    item.classList.add('disabled');
                    if (idx === q.step3.correct) item.classList.add('correct');
                    else if (cState.s3Selection === idx) item.classList.add('incorrect');
                } else if (cState.s3Status === 'incorrect' && cState.s3Selection === idx) {
                    item.classList.add('incorrect');
                    item.onclick = () => selectStep3Selection(idx);
                } else {
                    item.onclick = () => selectStep3Selection(idx);
                }

                item.innerHTML = `<div class="step-opt-prefix">${String.fromCharCode(65 + idx)}</div><div>${optText}</div>`;
                container.appendChild(item);
            });
        }

        function selectStep3Selection(idx) {
            const cState = userState.cardSteps[currentQIndex];
            if (cState.s3Status === 'correct' || cState.s3Status === 'skipped') return;
            cState.s3Selection = idx;
            cState.s3Status = 'unattempted';
            saveState();
            loadQuestion(currentQIndex);
        }

        function checkStep(stepNum) {
            const q = questionsData[currentQIndex];
            const cState = userState.cardSteps[currentQIndex];

            if (stepNum === 1) {
                if (cState.s1Selection === null) {
                    alert("Please select an option for Step 1 first!");
                    return;
                }
                if (q.step1.diagrams[cState.s1Selection].correct) {
                    cState.s1Status = 'correct';
                    AudioFX.playCorrectBell();
                } else {
                    cState.s1Status = 'incorrect';
                    AudioFX.playIncorrectBell();
                }
            } else if (stepNum === 2) {
                if (cState.s2Selection === null) {
                    alert("Please select an option for Step 2 first!");
                    return;
                }
                if (cState.s2Selection === q.step2.correct) {
                    cState.s2Status = 'correct';
                    AudioFX.playCorrectBell();
                } else {
                    cState.s2Status = 'incorrect';
                    AudioFX.playIncorrectBell();
                }
            } else if (stepNum === 3) {
                if (cState.s3Selection === null) {
                    alert("Please select an option for Step 3 first!");
                    return;
                }
                if (cState.s3Selection === q.step3.correct) {
                    cState.s3Status = 'correct';
                    userState.status[currentQIndex] = 'submitted';
                    userState.answers[currentQIndex] = cState.s3Selection;
                    AudioFX.playCorrectBell();
                } else {
                    cState.s3Status = 'incorrect';
                    AudioFX.playIncorrectBell();
                }
            }
            saveState();
            loadQuestion(currentQIndex);
        }

        function skipStep(stepNum) {
            const cState = userState.cardSteps[currentQIndex];

            if (stepNum === 1) {
                cState.s1Status = 'skipped';
                AudioFX.playSkipChime();
            } else if (stepNum === 2) {
                cState.s2Status = 'skipped';
                AudioFX.playSkipChime();
            } else if (stepNum === 3) {
                cState.s3Status = 'skipped';
                userState.status[currentQIndex] = 'submitted';
                AudioFX.playSkipChime();
            }
            saveState();
            loadQuestion(currentQIndex);
        }

        function skipEntireCard() {
            const cState = userState.cardSteps[currentQIndex];
            cState.s1Status = 'skipped';
            cState.s2Status = 'skipped';
            cState.s3Status = 'skipped';
            userState.status[currentQIndex] = 'skipped';
            saveState();
            AudioFX.playSkipChime();
            nextQuestion();
        }

        function nextQuestion() {
            if (currentQIndex < questionsData.length - 1) {
                loadQuestion(currentQIndex + 1);
            } else {
                finishTest();
            }
        }

        function jumpToQuestion(idx) {
            loadQuestion(idx);
        }

        function finishTest() {
            switchScreen('review-screen');
            let score = 0;
            const reviewList = document.getElementById('review-list');
            reviewList.innerHTML = '';

            questionsData.forEach((q, idx) => {
                const status = userState.status[idx];
                const cState = userState.cardSteps[idx] || {};
                const isFullyCorrect = cState.s1Status === 'correct' && cState.s2Status === 'correct' && cState.s3Status === 'correct';

                if (isFullyCorrect) score++;

                const card = document.createElement('div');
                card.className = 'review-card';

                let tagHtml = '<span class="status-tag tag-skipped">Skipped</span>';
                if (status === 'submitted') {
                    tagHtml = isFullyCorrect 
                        ? '<span class="status-tag tag-correct">Fully Correct</span>' 
                        : '<span class="status-tag tag-incorrect">Completed with Help</span>';
                }

                const s3Answer = cState.s3Selection !== null ? q.step3.options[cState.s3Selection] : 'None';
                const s3Correct = q.step3.options[q.step3.correct];

                card.innerHTML = `
                    <div style="display:flex; justify-content:space-between; margin-bottom:0.5rem;">
                        <strong>${q.title}</strong>
                        ${tagHtml}
                    </div>
                    <p style="font-size:0.9rem; margin-bottom:0.5rem;">${q.problem}</p>
                    <p style="font-size:0.9rem; color:var(--text-muted);">
                        <strong>Your Step 3 Answer:</strong> ${s3Answer} | 
                        <strong>Correct Step 3 Answer:</strong> ${s3Correct}
                    </p>
                    <div style="margin-top:0.5rem; font-size:0.85rem; background:#f8fafc; padding:0.5rem; border-radius:4px;">
                        <strong>Solution Rationale:</strong> ${q.rationale}
                    </div>
                `;
                reviewList.appendChild(card);
            });

            document.getElementById('final-score').innerText = `${score} / ${questionsData.length}`;
            triggerMathJax();
        }

        function restartQuiz() {
            userState = { answers: {}, status: {}, videoApproved: true, cardSteps: {} };
            saveState();
            startQuizScreen();
        }

        window.onload = function() {
            const savedUser = localStorage.getItem('bm_user_email');
            if (savedUser) {
                currentUser = savedUser;
                initSession();
            }
        };
    </script>
</body>
</html>
