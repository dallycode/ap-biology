# <!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <title>AP Bio Hub</title>

    <!-- Modern font -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700;800&family=Space+Grotesk:wght@500;600;700&display=swap" rel="stylesheet">

    <link rel="stylesheet" href="style.css">
</head>

<body>

<!-- SIDEBAR -->
<aside class="sidebar">

    <div class="logo">
        <div class="logo-icon">🧬</div>
        <div>
            <h2>AP Bio</h2>
            <span>HUB</span>
        </div>
    </div>

    <nav>

        <button class="nav-item active" onclick="showPage('dashboard')">
            <span>⌂</span>
            Dashboard
        </button>

        <button class="nav-item" onclick="showPage('units')">
            <span>▦</span>
            Units
        </button>

        <button class="nav-item" onclick="showPage('questions')">
            <span>?</span>
            Question Bank
        </button>

        <button class="nav-item" onclick="showPage('flashcards')">
            <span>◇</span>
            Flashcards
        </button>

        <button class="nav-item" onclick="showPage('timer')">
            <span>◷</span>
            Study Timer
        </button>

    </nav>

    <div class="sidebar-bottom">
        <button onclick="toggleDarkMode()" class="dark-button">
            ◐ Toggle Theme
        </button>
    </div>

</aside>


<!-- MAIN CONTENT -->
<main class="main">

    <!-- TOP BAR -->
    <header class="topbar">

        <div>
            <p class="small-label">AP BIOLOGY</p>
            <h1 id="pageTitle">Dashboard</h1>
        </div>

        <div class="streak">
            🔥 <strong id="streakNumber">7</strong> day streak
        </div>

    </header>


    <!-- DASHBOARD -->
    <section id="dashboard" class="page active-page">

        <div class="hero">

            <div>
                <p class="eyebrow">YOUR AP BIOLOGY STUDY SPACE</p>

                <h2>
                    Master biology.<br>
                    One concept at a time.
                </h2>

                <p>
                    Review AP Biology content, test yourself,
                    and build your confidence before exam day.
                </p>

                <button class="primary-btn" onclick="showPage('questions')">
                    Start Practicing →
                </button>
            </div>

            <div class="dna-decoration">
                🧬
            </div>

        </div>


        <!-- STATS -->

        <div class="stats-grid">

            <div class="stat-card">
                <span class="stat-icon">📚</span>
                <p>Units Completed</p>
                <h3 id="unitsCompleted">2 / 8</h3>
            </div>

            <div class="stat-card">
                <span class="stat-icon">✓</span>
                <p>Questions Answered</p>
                <h3 id="questionsAnswered">0</h3>
            </div>

            <div class="stat-card">
                <span class="stat-icon">⚡</span>
                <p>Accuracy</p>
                <h3 id="accuracy">—</h3>
            </div>

            <div class="stat-card">
                <span class="stat-icon">⏱</span>
                <p>Study Time</p>
                <h3 id="studyTime">0 min</h3>
            </div>

        </div>


        <!-- PROGRESS -->

        <div class="section-heading">
            <div>
                <p class="small-label">AP BIOLOGY</p>
                <h2>Your Progress</h2>
            </div>
        </div>


        <div class="progress-card">

            <div class="progress-info">
                <div>
                    <strong>Overall Course Progress</strong>
                    <p>Keep going — consistency matters.</p>
                </div>

                <strong id="overallProgress">25%</strong>
            </div>

            <div class="progress-bar">
                <div class="progress-fill" id="progressFill"></div>
            </div>

        </div>


        <!-- TODAY -->

        <div class="today-card">

            <div>
                <p class="small-label">TODAY'S RECOMMENDATION</p>

                <h2>Review Cell Structure</h2>

                <p>
                    Review Unit 2 concepts before practicing
                    cell communication questions.
                </p>
            </div>

            <button class="secondary-btn" onclick="openUnit(2)">
                Review Unit 2
            </button>

        </div>

    </section>


    <!-- UNITS -->

    <section id="units" class="page">

        <div class="section-heading">
            <div>
                <p class="small-label">COURSE CONTENT</p>
                <h2>AP Biology Units</h2>
            </div>
        </div>

        <div class="units-grid" id="unitsContainer"></div>

    </section>


    <!-- QUESTIONS -->

    <section id="questions" class="page">

        <div class="section-heading">
            <div>
                <p class="small-label">PRACTICE</p>
                <h2>Question Bank</h2>
            </div>

            <select id="questionFilter" onchange="filterQuestions()">
                <option value="all">All Units</option>
                <option value="1">Unit 1</option>
                <option value="2">Unit 2</option>
                <option value="3">Unit 3</option>
                <option value="4">Unit 4</option>
                <option value="5">Unit 5</option>
                <option value="6">Unit 6</option>
                <option value="7">Unit 7</option>
                <option value="8">Unit 8</option>
            </select>
        </div>

        <div class="question-card">

            <div class="question-top">
                <span id="questionUnit" class="unit-tag">UNIT 1</span>
                <span id="questionNumber">Question 1</span>
            </div>

            <h2 id="questionText">
                Loading question...
            </h2>

            <div id="answers"></div>

            <div id="explanation" class="explanation hidden"></div>

            <div class="question-controls">

                <button class="secondary-btn" onclick="nextQuestion()">
                    Next Question →
                </button>

            </div>

        </div>

    </section>


    <!-- FLASHCARDS -->

    <section id="flashcards" class="page">

        <div class="section-heading">
            <div>
                <p class="small-label">ACTIVE RECALL</p>
                <h2>Flashcards</h2>
                <p>Click a card to reveal the answer.</p>
            </div>
        </div>

        <div class="flashcard-container">

            <div class="flashcard" id="flashcard" onclick="flipCard()">

                <div class="flashcard-inner">

                    <div class="flashcard-front">
                        <span>QUESTION</span>
                        <h2 id="flashQuestion">
                            What is the function of ATP?
                        </h2>
                        <small>Click to flip</small>
                    </div>

                    <div class="flashcard-back">
                        <span>ANSWER</span>
                        <h2 id="flashAnswer">
                            ATP provides usable energy for cellular processes.
                        </h2>
                    </div>

                </div>

            </div>

        </div>

        <div class="flash-controls">

            <button class="secondary-btn" onclick="previousCard()">
                ← Previous
            </button>

            <span id="cardCounter">1 / 10</span>

            <button class="primary-btn" onclick="nextCard()">
                Next →
            </button>

        </div>

    </section>


    <!-- TIMER -->

    <section id="timer" class="page">

        <div class="timer-container">

            <p class="small-label">FOCUS SESSION</p>

            <h2>Study Timer</h2>

            <div id="timerDisplay">
                25:00
            </div>

            <div class="timer-controls">

                <button class="primary-btn" onclick="startTimer()">
                    Start
                </button>

                <button class="secondary-btn" onclick="pauseTimer()">
                    Pause
                </button>

                <button class="secondary-btn" onclick="resetTimer()">
                    Reset
                </button>

            </div>

        </div>

    </section>

</main>

<script src="script.js"></script>

</body>
</html>