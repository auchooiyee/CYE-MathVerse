# 🚀 CYE-MathVerse Starter Kit v1

Welcome to **CYE-MathVerse** — an educational math gaming ecosystem built for secondary school students (Malaysian KSSM Form 1–5, SPM, and IGCSE).

This Starter Kit provides a standardized, modular, zero-dependency framework to build, test, and deploy interactive HTML5 math games seamlessly into the CYE-MathVerse portal.

---

## 📁 1. Project Directory Structure

The project maintains a flat, route-friendly directory structure so that every game folder is directly accessible as a clean URL on Netlify (e.g. `https://cye-mathverse.netlify.app/financial-hero/`):

```
CYE-MathVerse/
│
├── index.html                 # 🏠 Main CYE-MathVerse Game Library (Portal)
├── README.md                  # 📖 Comprehensive Starter Kit & Developer Guide
│
├── assets/                    # 🎨 Shared Branding & Assets
│   └── cye-logo.svg           # CYE Vector Logo & Crest
│
├── game-template/             # ⚡ Standard Reusable Game Template (Starter Boilerplate)
│   └── index.html             # Self-contained single-file game engine
│
├── financial-hero/            # 💰 Form 4: Financial Management 2D Adventure
│   └── index.html
│
├── math-csi-cyber-heist/      # 🔐 Form 4 & 5: Cyber Detective Math Mystery
│   └── index.html
│
├── salary-tax-tycoon/         # 💼 Form 5: Taxation & Career Simulation 2.0
│   └── index.html
│
└── galactic-defense/          # 🚀 Form 4: Space Defense & Coordinate Algebra
    └── index.html
```

---

## 🛠️ 2. The 3-Step Game Creation Workflow

Creating a brand-new educational game takes under **5 minutes** using the starter kit:

```
Step 1: DUPLICATE          Step 2: CUSTOMIZE          Step 3: REGISTER
┌────────────────────┐    ┌────────────────────┐    ┌────────────────────┐
│ Duplicate folder:  │ ➔  │ Edit GAME_CONFIG   │ ➔  │ Add Game Card to   │
│ `game-template/`   │    │ in new index.html  │    │ root `index.html`  │
│ to `my-new-game/`  │    │ (Questions & Theme)│    │                    │
└────────────────────┘    └────────────────────┘    └────────────────────┘
```

### Step 1: Duplicate the Game Template
Copy `game-template/` and rename the folder to your new game slug (kebab-case):
```bash
# Example: Creating a new Probability game
cp -r game-template probability-quest
```

### Step 2: Customize `GAME_CONFIG` in `probability-quest/index.html`
Open `probability-quest/index.html` and update the configuration block at the top of the `<script>` tag:

```javascript
const GAME_CONFIG = {
    title: "PROBABILITY QUEST",
    subtitle: "Form 4 Chapter 9: Probability of Combined Events",
    icon: "🎲",
    form: "FORM 4",
    chapter: "Chapter 9 • Probability",
    difficulty: "⭐ Medium",
    timeEst: "⏱️ 10–15 min",
    missionBrief: "Calculate sample spaces, dependent and independent events, and union/intersection probabilities to navigate the cosmic maze!",
    totalLives: 3,
    pointsPerCorrect: 100,
    streakMultiplierBonus: 25,

    // Reference formulas displayed in Cheat-Sheet Modal
    formulas: [
        { title: "Probability of Event A", code: "P(A) = n(A) / n(S)" },
        { title: "Complement of Event A", code: "P(A') = 1 - P(A)" },
        { title: "Addition Rule (Non-Mutually Exclusive)", code: "P(A ∪ B) = P(A) + P(B) - P(A ∩ B)" },
        { title: "Independent Events Multiplication", code: "P(A ∩ B) = P(A) × P(B)" }
    ],

    // Questions Database
    questions: [
        {
            category: "Independent Events",
            prompt: "A fair die is rolled and a fair coin is tossed. What is the probability of getting a prime number on the die AND 'Heads' on the coin?",
            visual: "Die Primes = {2, 3, 5} | Coin = {H, T}",
            hint: "Find P(Prime) = 3/6 = 1/2, and P(Heads) = 1/2. Multiply them together.",
            options: [
                { label: "1/4 (25%)", isCorrect: true },
                { label: "1/2 (50%)", isCorrect: false },
                { label: "3/8 (37.5%)", isCorrect: false },
                { label: "1/6 (16.7%)", isCorrect: false }
            ],
            explanation: "P(Prime) = 3/6 = 1/2. P(Heads) = 1/2. Because the events are independent: P(Prime ∩ Heads) = (1/2) × (1/2) = 1/4."
        }
        // Add more questions here...
    ]
};
```

### Step 3: Add Game Card to `index.html` (Main Library)
Add the following card markup to the `#games-grid` container inside root `index.html`:

```html
<!-- GAME: Probability Quest -->
<div class="game-card bg-white rounded-2xl overflow-hidden shadow-sm border border-slate-200/80 flex flex-col group" data-category="form-4 mystery">
    <div class="h-44 bg-gradient-to-br from-purple-500 via-indigo-600 to-blue-700 relative overflow-hidden flex items-center justify-center">
        <span class="text-6xl group-hover:scale-110 transition-transform duration-500">🎲</span>
        <div class="absolute top-3 right-3 bg-white/95 backdrop-blur-sm text-purple-800 text-[10px] font-black px-2.5 py-1 rounded-full shadow-sm">
            ⭐⭐ MEDIUM
        </div>
    </div>
    <div class="p-5 flex flex-col flex-grow">
        <div class="flex items-center justify-between gap-1 mb-2">
            <span class="text-[11px] font-black text-purple-600 uppercase tracking-wide">FORM 4</span>
            <span class="text-[11px] text-slate-500 font-bold">⏱️ 10–15 min</span>
        </div>
        <div class="text-xs font-bold text-slate-500 mb-1">
            Chapter 9 • Probability of Combined Events
        </div>
        <h3 class="text-lg font-black text-slate-900 mb-2 group-hover:text-primary-600 transition">
            Probability Quest
        </h3>
        <p class="text-slate-600 text-xs sm:text-sm mb-5 flex-grow font-medium leading-relaxed">
            Calculate compound event probabilities, sample spaces, and union rules to unlock cosmic gates.
        </p>
        <a href="probability-quest/" class="block w-full text-center bg-primary-600 hover:bg-primary-700 text-white font-bold py-2.5 px-4 rounded-xl transition shadow-sm text-sm">
            PLAY NOW ➔
        </a>
    </div>
</div>
```

---

## 🧩 3. Standard Game Architecture

Every game in the CYE-MathVerse ecosystem adheres to the **4-Phase Educational Game Flow**:

```
 ┌────────────────────────────────────────────────────────┐
 │ 1. MISSION BRIEFING                                    │
 │    • Title, Subtitle, Form & Topic tags                │
 │    • Storyline Briefing, Learning Goals & Rules        │
 │    • [ ENTER MISSION ]                                 │
 └──────────────────────────┬─────────────────────────────┘
                            │
 ┌──────────────────────────▼─────────────────────────────┐
 │ 2. PLAYER IDENTIFICATION                               │
 │    • Student / Cadet Name Input                        │
 │    • Character Avatar Picker (🚀, 🤖, 🦊, 🦉, 🦁, ⚡)  │
 │    • [ LAUNCH MISSION ]                                │
 └──────────────────────────┬─────────────────────────────┘
                            │
 ┌──────────────────────────▼─────────────────────────────┐
 │ 3. INTERACTIVE GAMEPLAY LOOP                           │
 │    • Unified HUD: Avatar, Lives ❤️, Score, Streak 🔥,  │
 │      Progress Bar, Timer ⏱️, Sound Toggle & Pause     │
 │    • Challenge Prompts with Math Formulas              │
 │    • Immediate Audio/Visual Feedback + Full Solution   │
 │    • Built-in Formula Cheat Sheet & Interactive Canvas │
 └──────────────────────────┬─────────────────────────────┘
                            │
 ┌──────────────────────────▼─────────────────────────────┐
 │ 4. MISSION EVALUATION & SUMMARY                        │
 │    • Star Rating: ⭐ / ⭐⭐ / ⭐⭐⭐                   │
 │    • Stats: Player, Score, Accuracy %, Time, Streak    │
 │    • LocalStorage High-Score Persistence               │
 │    • [ PLAY AGAIN ]  |  [ GAME LIBRARY ]               │
 └────────────────────────────────────────────────────────┘
```

---

## 🤖 4. AI Prompting Formula

When using AI coding assistants (e.g. Antigravity, Gemini, ChatGPT) to generate new games for CYE-MathVerse, use this standard prompt formula:

> **Prompt Template**:
>
> "Create a new CYE-MathVerse game following `game-template/index.html` standards:
> - **Game Name**: [Game Title, e.g., Trigonometry Sky Tracker]
> - **Curriculum**: [Form & Chapter, e.g., Form 5 Chapter 5: Trigonometric Functions]
> - **Game Genre**: [e.g., Simulation / Mystery / Challenge / Arcade]
> - **Difficulty**: [Easy / Medium / Hard]
> - **Requirements**:
>   1. Provide 6 to 10 progressive math questions with visual formulas, strategic hints, and step-by-step mathematical solutions.
>   2. Include formula sheet entries for sine, cosine, tangent rules and area of triangles.
>   3. Use the procedural Web Audio synthesizer, HUD with lives/score/streaks, scratchpad, and victory screen.
>   4. Keep the output as a standalone single-file `index.html` ready to place in `/trigonometry-sky-tracker/`."

---

## 📚 5. KSSM Curriculum & Game Genre Taxonomy

Use this topic and genre matrix when planning future MathVerse titles:

| Level | Chapter & Topic | Recommended Game Genre | Example Game Mechanics |
|---|---|---|---|
| **Form 4** | Ch 1: Quadratic Functions & Equations | 🚀 Arcade / Projectile | Trajectory calculation & parabolas |
| **Form 4** | Ch 2: Number Bases (Base 2, 8, 10, etc.) | 🔐 Mystery / Cipher | Base conversions to hack cyber locks |
| **Form 4** | Ch 3: Logical Reasoning | 🧩 Logic Puzzle | Truth tables, implications & deductions |
| **Form 4** | Ch 4: Operations on Sets | 🗺️ Strategy / Grid | Venn diagram territory conquest |
| **Form 4** | Ch 5: Network in Graph Theory | 🕸️ Network Pathfinding | Minimum spanning trees & Eulerian paths |
| **Form 4** | Ch 6: Linear Inequalities in Two Variables | 🛡️ Defense / Territory | Shading feasible coordinate regions |
| **Form 4** | Ch 7: Graphs of Motion | 🏎️ Speed & Time Challenge | Distance-time & speed-time physics |
| **Form 4** | Ch 8: Measures of Dispersion | 📊 Detective Mystery | Standard deviation & outlier analysis |
| **Form 4** | Ch 9: Probability of Combined Events | 🎲 Casino / Quest | Tree diagrams & compound probability |
| **Form 4** | Ch 10: Consumer Mathematics (Financial) | 💰 2D Side-Scroller | Cash flow, SMART goals & budgeting |
| **Form 5** | Ch 1: Variation (Direct, Inverse, Joint) | ⚙️ Factory Simulation | Ratio machines & proportionality gears |
| **Form 5** | Ch 2: Matrices | 🤖 Cyber Battle | Matrix multiplication & inverse cipher |
| **Form 5** | Ch 3: Consumer Mathematics (Insurance) | 🏥 Life Simulation | Deductibles, copayments & policy limits |
| **Form 5** | Ch 4: Consumer Mathematics (Taxation) | 💼 Tycoon Simulation | Income tax, reliefs, rebates & road tax |
| **Form 5** | Ch 5: Congruency, Enlargement & Tessellation | 🎨 Spatial Puzzle | Scale factor & isometric transformations |
| **Form 5** | Ch 6: Trigonometric Ratios & Graphs | 📡 Radar / Tracking | Angle of elevation, sine & cosine waves |
| **Form 5** | Ch 7: Linear Law | 📈 Lab Experiment | Reducing non-linear curves to $Y = mX + c$ |
| **Form 5** | Ch 8: Kinematics & Calculus | 🚀 Space Launch | Rates of change, derivatives & integrals |

---

## 🌐 6. Netlify Deployment Architecture

All games share a single Netlify site with instant static folder mapping:

```
https://cye-mathverse.netlify.app/
│
├── /                         ➔ index.html (Game Library)
├── /financial-hero/          ➔ financial-hero/index.html
├── /math-csi-cyber-heist/    ➔ math-csi-cyber-heist/index.html
├── /salary-tax-tycoon/       ➔ salary-tax-tycoon/index.html
├── /galactic-defense/        ➔ galactic-defense/index.html
├── /game-template/           ➔ game-template/index.html
└── /[your-new-game]/         ➔ [your-new-game]/index.html
```

- **Zero Build Steps**: No npm install or build scripts required.
- **Instant Preview**: Works immediately via local preview or pushing directly to your GitHub repository connected to Netlify.

---

## 🤖 7. AI Agent + Educator Review (Human-in-the-Loop) Workflow

CYE-MathVerse is designed to work seamlessly with **Google Antigravity** as an autonomous agentic pair-programmer, while keeping the educator firmly in control of quality and syllabus correctness:

```
                    💡 YOUR IDEA
                         │
                         ▼
              ┌─────────────────────┐
              │  Google Antigravity │
              │      🤖 AI Agent    │
              └──────────┬──────────┘
                         │
              Plan → Code → Test → Fix
                         │
                         ▼
              ┌─────────────────────┐
              │      GitHub         │
              │   📦 Source Code    │
              └──────────┬──────────┘
                         │
                    git push
                         │
                         ▼
              ┌─────────────────────┐
              │   👨‍🏫 YOU REVIEW     │
              │  (Human-in-the-Loop)│
              └──────────┬──────────┘
                         │
                     Approved
                         │
                         ▼
              ┌─────────────────────┐
              │      Netlify        │
              │    🌐 Production    │
              └──────────┬──────────┘
                         │
                         ▼
                  🎮 Students
```

### 🛡️ Safety & Quality Review Protocol
1. **AI Autonomous Phase**:
   - Agent creates `[game-name]/index.html` from `game-template/`.
   - Agent generates KSSM-aligned questions, equations, hints, and step-by-step mathematical solutions.
   - Agent tests layout, audio synthesizer, HUD mechanics, and registers the game card in `index.html`.
2. **Educator Review Gate (You)**:
   - Verify math accuracy and syllabus alignment (e.g. correct SPM marking criteria).
   - Test in browser (open `index.html` locally).
   - Review file diffs before pushing.
3. **Automated Production Deployment**:
   - `git add .` ➔ `git commit -m "Add [game-name]"` ➔ `git push origin main`
   - Netlify automatically detects changes and publishes the live game in ~15 seconds with zero server configuration.

---

© 2026 CYE MathVerse. Built with ❤️ for engaging mathematics education.

