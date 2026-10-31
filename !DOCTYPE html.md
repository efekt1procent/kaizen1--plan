  
<!DOCTYPE html>  
<html lang="pl">  
<head>  
    <meta charset="UTF-8">  
    <meta name="viewport" content="width=device-width, initial-scale=1.0">  
    <title>Kaizen 28 - Minimalistyczny Plan Kalisteniczny</title>  
    <style>  
        :root {  
            --bg-color: #121214;  
            --card-bg: #1e1e24;  
            --accent: #10b981;  
            --accent-hover: #059669;  
            --text-main: #f3f4f6;  
            --text-muted: #9ca3af;  
            --border: #2d2d38;  
            --done-bg: #064e3b;  
        }  
  
        * {  
            box-sizing: border-box;  
            margin: 0;  
            padding: 0;  
            font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;  
        }  
  
        body {  
            background-color: var(--bg-color);  
            color: var(--text-main);  
            padding: 16px;  
            line-height: 1.5;  
            max-width: 600px;  
            margin: 0 auto;  
        }  
  
        header {  
            text-align: center;  
            margin-bottom: 24px;  
            padding-top: 12px;  
        }  
  
        h1 {  
            font-size: 1.5rem;  
            color: var(--accent);  
            margin-bottom: 4px;  
        }  
  
        p.subtitle {  
            font-size: 0.9rem;  
            color: var(--text-muted);  
        }  
  
        /* Sekcja Kotwic / Nawyku */  
        .habit-card {  
            background-color: var(--card-bg);  
            border: 1px solid var(--border);  
            border-radius: 12px;  
            padding: 16px;  
            margin-bottom: 20px;  
            font-size: 0.9rem;  
        }  
  
        .habit-card h3 {  
            color: var(--accent);  
            font-size: 1rem;  
            margin-bottom: 6px;  
        }  
  
        /* Pasek postępu */  
        .progress-container {  
            background-color: var(--card-bg);  
            border: 1px solid var(--border);  
            border-radius: 12px;  
            padding: 16px;  
            margin-bottom: 24px;  
            text-align: center;  
        }  
  
        .progress-bar-bg {  
            background-color: var(--border);  
            border-radius: 8px;  
            height: 10px;  
            width: 100%;  
            margin-top: 10px;  
            overflow: hidden;  
        }  
  
        .progress-bar-fill {  
            background-color: var(--accent);  
            height: 100%;  
            width: 0%;  
            transition: width 0.3s ease;  
        }  
  
        .stats-text {  
            font-size: 0.85rem;  
            color: var(--text-muted);  
            margin-top: 6px;  
        }  
  
        /* Sekcja tygodni i dni */  
        .week-section {  
            margin-bottom: 24px;  
        }  
  
        .week-title {  
            font-size: 1.1rem;  
            font-weight: bold;  
            color: var(--text-main);  
            margin-bottom: 12px;  
            border-left: 4px solid var(--accent);  
            padding-left: 8px;  
        }  
  
        .day-card {  
            background-color: var(--card-bg);  
            border: 1px solid var(--border);  
            border-radius: 12px;  
            padding: 16px;  
            margin-bottom: 12px;  
            transition: background-color 0.2s;  
        }  
  
        .day-card.completed {  
            background-color: #062e22;  
            border-color: #047857;  
        }  
  
        .day-header {  
            display: flex;  
            justify-content: space-between;  
            align-items: center;  
            cursor: pointer;  
        }  
  
        .day-title {  
            font-weight: bold;  
            font-size: 1.05rem;  
        }  
  
        .day-type {  
            font-size: 0.8rem;  
            color: var(--text-muted);  
            background: rgba(255,255,255,0.05);  
            padding: 2px 8px;  
            border-radius: 6px;  
        }  
  
        .day-content {  
            margin-top: 12px;  
            padding-top: 12px;  
            border-top: 1px solid var(--border);  
            display: none;  
        }  
  
        .day-card.open .day-content {  
            display: block;  
        }  
  
        .exercise-item {  
            margin-bottom: 10px;  
            font-size: 0.9rem;  
        }  
  
        .exercise-label {  
            font-weight: bold;  
            color: var(--accent);  
        }  
  
        /* Instrukcje rozwijane */  
        .instruction-toggle {  
            background: none;  
            border: 1px solid var(--border);  
            color: var(--text-muted);  
            font-size: 0.8rem;  
            padding: 4px 8px;  
            border-radius: 6px;  
            cursor: pointer;  
            margin-top: 4px;  
            display: inline-block;  
        }  
  
        .instruction-toggle:hover {  
            color: var(--text-main);  
            border-color: var(--accent);  
        }  
  
        .instruction-box {  
            background: rgba(0,0,0,0.2);  
            padding: 8px 12px;  
            border-radius: 6px;  
            margin-top: 6px;  
            font-size: 0.85rem;  
            color: var(--text-muted);  
            display: none;  
        }  
  
        .instruction-box.open {  
            display: block;  
        }  
  
        /* Przycisk ukończenia */  
        .complete-btn {  
            background-color: transparent;  
            border: 2px solid var(--accent);  
            color: var(--accent);  
            padding: 8px 16px;  
            border-radius: 8px;  
            font-weight: bold;  
            width: 100%;  
            margin-top: 14px;  
            cursor: pointer;  
            transition: all 0.2s;  
        }  
  
        .day-card.completed .complete-btn {  
            background-color: var(--accent);  
            color: #000;  
        }  
  
        .footer-note {  
            text-align: center;  
            font-size: 0.8rem;  
            color: var(--text-muted);  
            margin-top: 40px;  
            margin-bottom: 20px;  
        }  
    </style>  
</head>  
<body>  
  
    <header>  
        <h1>Kaizen 28</h1>  
        <p class="subtitle">Mikro-rytuały siły, mobilności i zdrowych pleców (3-5 min dziennie)</p>  
    </header>  
  
    <!-- Zasada nawyku -->  
    <div class="habit-card">  
        <h3>💡 Sekret bezwzględnego nawyku (Kotwica)</h3>  
        <p>Nie planuj konkretnej godziny. Przepnij trening do istniejącego nawyku: <strong>„Zaraz po wypiciu porannej kawy / po zdjęciu butów po powrocie – otwieram aplikację i robię 1 ruch”</strong>.</p>  
    </div>  
  
    <!-- Pasek postępu -->  
    <div class="progress-container">  
        <h3 id="progress-title">Twój postęp w wyzwaniu</h3>  
        <div class="progress-bar-bg">  
            <div class="progress-bar-fill" id="progressBar"></div>  
        </div>  
        <div class="stats-text" id="statsText">Ukończono 0 z 28 dni (0%)</div>  
    </div>  
  
    <div id="appContainer"></div>  
  
    <div class="footer-note">  
        Stworzone w duchu Kaizen. Zapisuje postępy automatycznie w telefonie.  
    </div>  
  
    <script>  
        // Dane planu 28-dniowego  
        const planData = [  
            // TYDZIEŃ 1 (3 dni)  
            { week: 1, day: 1, type: "Dzień A: Drążek & Plecy",   
              mobilization: { name: "Zwis swobodny na drążku", desc: "Złap drążek nachwytem, rozluźnij nogi i pozwól grawitacji rozciągnąć kręgosłup i barki przez 30 sekund. Poczuj ulgę w lędźwiach." },  
              strength: { name: "Aktywny zwis lub 1 seria podciągania", desc: "Ściągnij łopatki w dół i do tyłu (aktywny zwis) lub wykonaj 1 spokojną serię podciągania (lub opuszczania się z drążka z zapasem)." },  
              stretch: { name: "Rozciąganie pleców na drążku", desc: "Po zejściu z drążka złap go wyżej i odciągnij biodra w tył, rozciągając boki i najszerszy grzbiet (30 sekund)." }  
            },  
            { week: 1, day: 2, type: "Dzień B: Pompka & Klatka",   
              mobilization: { name: "Kot-Krowa (Cat-Cow)", desc: "W klęku podpartym naprzemiennie wyginaj kręgosłup w łuk do góry (koci grzbiet) i opuszczaj w dół (krowa). 8-10 płynnych powtórzeń dla uwolnienia lędźwi." },  
              strength: { name: "Klasyczna pompka na podłodze", desc: "1 czysta, kontrolowana seria pompek. Brzuch i pośladki napięte, ciało w linii prostej. Zrób z zapasem!" },  
              stretch: { name: "Pozycja Dziecka (Child's Pose)", desc: "Usiądź na piętach, wyciągnij ręce przed siebie i opuść klatkę do ziemi. Głębokie oddychanie przez 30 sekund dla pełnego rozluźnienia lędźwi." }  
            },  
            { week: 1, day: 3, type: "Dzień C: Nogi & Core",   
              mobilization: { name: "Krążenia bioder i miednicy", desc: "Stojąc, wykonaj powolne krążenia biodrami w obie strony (po 8 kółek), odblokowując spięte stawy miednicowe." },  
              strength: { name: "Standardowy przysiad z masą ciała", desc: "1 seria spokojnych, głębokich przysiadów. Kolana zbieżne ze stopami, plecy proste." },  
              stretch: { name: "Mostek barkowy (Glute Bridge) + Rozciąganie ud", desc: "Leżąc na plecach, unieś biodra napinając pośladki (wzmacnia core/lędźwie), a na koniec delikatnie rozciągnij tył ud." }  
            },  
  
            // TYDZIEŃ 2 (4 dni)  
            { week: 2, day: 4, type: "Dzień A: Drążek & Plecy",   
              mobilization: { name: "Zwis swobodny na drążku", desc: "Zwis luźny przez 30-45 sekund. Skup się na całkowitym rozluźnieniu oddechu." },  
              strength: { name: "Drążek: Zwis aktywny / Podciąganie", desc: "1 kontrolowana seria. Pamiętaj o jakości ruchu, a nie ilości." },  
              stretch: { name: "Rozciąganie pleców na drążku", desc: "Głębokie odciągnięcie tułowia w tył (30 sekund)." }  
            },  
            { week: 2, day: 5, type: "Dzień B: Pompka & Klatka",   
              mobilization: { name: "Kot-Krowa (Cat-Cow)", desc: "10 powolnych ruchów mobilizujących kręgosłup." },  
              strength: { name: "Klasyczna pompka", desc: "1 seria o 1 powtórzenie lub 1 sekundę wolniejsza niż tydzień temu." },  
              stretch: { name: "Pozycja Dziecka (Child's Pose)", desc: "30 sekund głębokiego oddechu w lędźwie." }  
            },  
            { week: 2, day: 6, type: "Dzień C: Nogi & Core",   
              mobilization: { name: "Krążenia bioder", desc: "Rozruszanie stawów przed ruchem." },  
              strength: { name: "Przysiady + Wznosy kolan", desc: "1 seria przysiadów z dodatkowym spięciem brzucha na górze." },  
              stretch: { name: "Mostek barkowy + Tył ud", desc: "Aktywacja pośladków chroniąca lędźwie." }  
            },  
            { week: 2, day: 7, type: "Dzień A: Drążek & Stabilizacja",   
              mobilization: { name: "Zwis krótki + mobilność barków", desc: "Zwis swobodny (30s) dla dekompresji kręgosłupa." },  
              strength: { name: "Zwis aktywny z dopięciem łopatek", desc: "1 solidna seria budująca plecy bez przemęczenia." },  
              stretch: { name: "Rozciąganie najszerszego grzbietu", desc: "Rozluźnienie boku tułowia." }  
            },  
  
            // TYDZIEŃ 3 (5 dni)  
            { week: 3, day: 8, type: "Dzień A: Drążek & Plecy", mobilization: { name: "Zwis swobodny", desc: "30 sekund dekompresji." }, strength: { name: "Podciąganie / Zwis aktywny", desc: "1 seria jakościowa." }, stretch: { name: "Rozciąganie pleców", desc: "30 sekund." } },  
            { week: 3, day: 9, type: "Dzień B: Pompka & Brzuch", mobilization: { name: "Kot-Krowa", desc: "10 powtórzeń mobilności." }, strength: { name: "Pompka klasyczna + Deska (Plank 20s)", desc: "Dodajemy 20 sekund deski dla wzmocnienia core." }, stretch: { name: "Pozycja Dziecka", desc: "Relaks lędźwi." } },  
            { week: 3, day: 10, type: "Dzień C: Nogi & Core", mobilization: { name: "Krążenia bioder", desc: "Mobilność." }, strength: { name: "Przysiady", desc: "1 seria." }, stretch: { name: "Mostek barkowy", desc: "Ochrona kręgosłupa." } },  
            { week: 3, day: 11, type: "Dzień A: Drążek & Pociąganie", mobilization: { name: "Zwis swobodny", desc: "Rozciąganie." }, strength: { name: "Zwis aktywny / Podciąganie", desc: "1 seria." }, stretch: { name: "Rozciąganie grzbietu", desc: "30s." } },  
            { week: 3, day: 12, type: "Dzień B: Pompka & Klatka", mobilization: { name: "Kot-Krowa", desc: "Mobilność." }, strength: { name: "Klasyczna pompka", desc: "1 seria z pełną kontrolą." }, stretch: { name: "Pozycja Dziecka", desc: "Ulgowy rozciąg." } },  
  
            // TYDZIEŃ 4 (6 dni - szczyt nawyku)  
            { week: 4, day: 13, type: "Dzień A: Drążek & Plecy", mobilization: { name: "Zwis swobodny", desc: "Dekompresja." }, strength: { name: "Podciąganie / Zwis", desc: "1 seria." }, stretch: { name: "Rozciąganie", desc: "30s." } },  
            { week: 4, day: 14, type: "Dzień B: Pompka & Brzuch", mobilization: { name: "Kot-Krowa", desc: "Mobilność." }, strength: { name: "Pompka + Plank 30s", desc: "Stabilizacja." }, stretch: { name: "Pozycja Dziecka", desc: "Ulga." } },  
            { week: 4, day: 15, type: "Dzień C: Nogi & Core", mobilization: { name: "Krążenia bioder", desc: "Stawy." }, strength: { name: "Przysiady", desc: "1 seria." }, stretch: { name: "Mostek barkowy", desc: "Pośladki." } },  
            { week: 4, day: 16, type: "Dzień A: Drążek & Plecy", mobilization: { name: "Zwis swobodny", desc: "Dekompresja." }, strength: { name: "Drążek", desc: "1 seria." }, stretch: { name: "Rozciąganie", desc: "30s." } },  
            { week: 4, day: 17, type: "Dzień B: Pompka", mobilization: { name: "Kot-Krowa", desc: "Mobilność." }, strength: { name: "Pompka", desc: "1 seria." }, stretch: { name: "Pozycja Dziecka", desc: "Relaks." } },  
            { week: 4, day: 18, type: "Dzień C: Nogi & Core", mobilization: { name: "Krążenia", desc: "Biodra." }, strength: { name: "Przysiady", desc: "1 seria." }, stretch: { name: "Mostek", desc: "Tył." } },  
        ];  
  
        // Automatyczne dopełnienie do 28 dni  
        for(let i = 19; i <= 28; i++) {  
            let mod = i % 3;  
            let typeName = mod === 1 ? "Dzień A: Drążek & Plecy" : (mod === 2 ? "Dzień B: Pompka & Brzuch" : "Dzień C: Nogi & Core");  
            let mob = mod === 1 ? "Zwis swobodny na drążku" : (mod === 2 ? "Kot-Krowa (Cat-Cow)" : "Krążenia bioder i miednicy");  
            let str = mod === 1 ? "Zwis aktywny / Podciąganie" : (mod === 2 ? "Klasyczna pompka" : "Standardowy przysiad");  
            let strt = mod === 1 ? "Rozciąganie pleców na drążku" : (mod === 2 ? "Pozycja Dziecka (Child's Pose)" : "Mostek barkowy");  
              
            planData.push({  
                week: Math.ceil(i / 7),  
                day: i,  
                type: typeName,  
                mobilization: { name: mob, desc: "Wykonaj spokojnie i bez pośpiechu." },  
                strength: { name: str, desc: "Tylko 1 solidna, czysta seria z dużym zapasem." },  
                stretch: { name: strt, desc: "Rozluźnienie po wysiłku (30 sekund)." }  
            });  
        }  
  
        // Ładowanie stanu z pamięci przeglądarki  
        let completedDays = JSON.parse(localStorage.getItem('kaizen_completed_days')) || [];  
  
        function renderApp() {  
            const container = document.getElementById('appContainer');  
            container.innerHTML = '';  
  
            for (let w = 1; w <= 4; w++) {  
                const weekDays = planData.filter(d => d.week === w);  
                  
                const weekDiv = document.createElement('div');  
                weekDiv.className = 'week-section';  
                  
                let weekTitleText = `Tydzień ${w} `;  
                if(w === 1) weekTitleText += "(3 dni - Płynny start)";  
                else if(w === 2) weekTitleText += "(4 dni - Budowanie rytmu)";  
                else if(w === 3) weekTitleText += "(5 dni - Wyższa częstotliwość)";  
                else if(w === 4) weekTitleText += "(6 dni - Pełny mikrorytuał)";  
  
                weekDiv.innerHTML = `<div class="week-title">${weekTitleText}</div>`;  
  
                weekDays.forEach(dayObj => {  
                    const isDone = completedDays.includes(dayObj.day);  
                      
                    const card = document.createElement('div');  
                    card.className = `day-card ${isDone ? 'completed' : ''}`;  
                    card.id = `day-card-${dayObj.day}`;  
  
                    card.innerHTML = `  
                        <div class="day-header" onclick="toggleDay(${dayObj.day})">  
                            <div>  
                                <span class="day-title">Dzień ${dayObj.day}</span>  
                                <div class="day-type">${dayObj.type}</div>  
                            </div>  
                            <span style="font-size: 1.2rem;">${isDone ? '✅' : '▼'}</span>  
                        </div>  
                        <div class="day-content" id="day-content-${dayObj.day}">  
                            <div class="exercise-item">  
                                <span class="exercise-label">1. Mobilizacja (Plecy/Stawy):</span> ${dayObj.mobilization.name}  
                                <br><button class="instruction-toggle" onclick="toggleInst(${dayObj.day}, 1)">ℹ️ Instrukcja</button>  
                                <div class="instruction-box" id="inst-${dayObj.day}-1">${dayObj.mobilization.desc}</div>  
                            </div>  
                            <div class="exercise-item" style="margin-top: 10px;">  
                                <span class="exercise-label">2. Siła Kaizen (1 Seria):</span> ${dayObj.strength.name}  
                                <br><button class="instruction-toggle" onclick="toggleInst(${dayObj.day}, 2)">ℹ️ Instrukcja</button>  
                                <div class="instruction-box" id="inst-${dayObj.day}-2">${dayObj.strength.desc}</div>  
                            </div>  
                            <div class="exercise-item" style="margin-top: 10px;">  
                                <span class="exercise-label">3. Rozciąganie (Ulgowe):</span> ${dayObj.stretch.name}  
                                <br><button class="instruction-toggle" onclick="toggleInst(${dayObj.day}, 3)">ℹ️ Instrukcja</button>  
                                <div class="instruction-box" id="inst-${dayObj.day}-3">${dayObj.stretch.desc}</div>  
                            </div>  
                            <button class="complete-btn" onclick="toggleComplete(${dayObj.day})">  
                                ${isDone ? 'Ukończono! (Kliknij, aby cofnąć)' : 'Oznacz jako zrobione ✓'}  
                            </button>  
                        </div>  
                    `;  
                    weekDiv.appendChild(card);  
                });  
  
                container.appendChild(weekDiv);  
            }  
  
            updateProgress();  
        }  
  
        function toggleDay(dayNum) {  
            const card = document.getElementById(`day-card-${dayNum}`);  
            card.classList.toggle('open');  
        }  
  
        function toggleInst(dayNum, index) {  
            event.stopPropagation();  
            const box = document.getElementById(`inst-${dayNum}-${index}`);  
            box.classList.toggle('open');  
        }  
  
        function toggleComplete(dayNum) {  
            event.stopPropagation();  
            if (completedDays.includes(dayNum)) {  
                completedDays = completedDays.filter(d => d !== dayNum);  
            } else {  
                completedDays.push(dayNum);  
            }  
            localStorage.setItem('kaizen_completed_days', JSON.stringify(completedDays));  
            renderApp();  
            setTimeout(() => {  
                const card = document.getElementById(`day-card-${dayNum}`);  
                if(card) card.classList.add('open');  
            }, 50);  
        }  
  
        function updateProgress() {  
            const total = 28;  
            const count = completedDays.length;  
            const percent = Math.round((count / total) * 100);  
              
            document.getElementById('progressBar').style.width = percent + '%';  
            document.getElementById('statsText').innerText = `Ukończono ${count} z ${total} dni (${percent}%)`;  
        }  
  
        renderApp();  
    </script>  
</body>  
</html>  
