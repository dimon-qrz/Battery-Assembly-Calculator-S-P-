<!DOCTYPE html>
<html lang="uk">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Калькулятор збірки акумуляторів</title>
    <style>
        :root {
            --bg-color: #0d1117;
            --card-bg: #161b22;
            --border-color: #30363d;
            --text-color: #c9d1d9;
            --accent-color: #58a6ff;
            --accent-hover: #1f6feb;
        }

        body {
            font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
            background-color: var(--bg-color);
            color: var(--text-color);
            margin: 0;
            padding: 20px;
            display: flex;
            justify-content: center;
        }

        .container {
            width: 100%;
            max-width: 800px;
            background-color: var(--card-bg);
            border: 1px solid var(--border-color);
            border-radius: 8px;
            padding: 24px;
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.3);
        }

        h1 { font-size: 20px; margin-top: 0; margin-bottom: 20px; border-bottom: 1px solid var(--border-color); padding-bottom: 10px; color: #f0f6fc; }
        .section { margin-bottom: 20px; }
        label { display: block; margin-bottom: 8px; font-weight: 600; font-size: 14px; }
        .radio-group, .grid-inputs { display: flex; gap: 15px; flex-wrap: wrap; }
        
        .radio-card { flex: 1; min-width: 130px; background-color: var(--bg-color); border: 1px solid var(--border-color); border-radius: 6px; padding: 10px; text-align: center; cursor: pointer; }
        .radio-card input { display: none; }
        .radio-card:has(input:checked) { border-color: var(--accent-color); background-color: rgba(88, 166, 255, 0.1); }
        
        .input-group { flex: 1; min-width: 200px; background-color: var(--bg-color); border: 1px solid var(--border-color); border-radius: 6px; padding: 12px; }
        input[type="number"] { width: 100%; background-color: #010409; border: 1px solid var(--border-color); color: var(--text-color); padding: 8px; border-radius: 4px; font-size: 16px; margin-top: 5px; }

        .results-box { background-color: var(--bg-color); border: 1px solid var(--border-color); border-radius: 6px; padding: 15px; margin-bottom: 20px; }
        .results-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(180px, 1fr)); gap: 10px; }
        .result-value { font-size: 18px; font-weight: bold; color: var(--accent-color); }

        .visual-container { background-color: var(--bg-color); border: 1px solid var(--border-color); border-radius: 6px; padding: 15px; text-align: center; display: flex; flex-direction: column; align-items: center; }
        .battery-matrix { display: inline-flex; flex-direction: column; gap: 6px; padding: 10px; }
        .battery-row { display: flex; gap: 6px; align-items: center; }
        .cell { width: 28px; height: 44px; background-color: #21262d; border: 2px solid var(--accent-color); border-radius: 4px; display: flex; align-items: center; justify-content: center; font-size: 10px; }
        
        .footer { margin-top: 30px; border-top: 1px solid var(--border-color); padding-top: 20px; font-size: 13px; text-align: center; color: #8b949e; }
        .footer a { color: var(--accent-color); text-decoration: none; margin: 0 10px; }
        .footer a:hover { text-decoration: underline; }
    </style>
</head>
<body>

<div class="container">
    <h1>Калькулятор збірки акумуляторів (S/P)</h1>

    <div class="section">
        <label>Хімічний тип:</label>
        <div class="radio-group">
            <label class="radio-card"><input type="radio" name="chemistry" value="liion" checked onchange="updateChemistry()"><div><strong>Li-ion</strong></div></label>
            <label class="radio-card"><input type="radio" name="chemistry" value="lifepo4" onchange="updateChemistry()"><div><strong>LiFePO4</strong></div></label>
            <label class="radio-card"><input type="radio" name="chemistry" value="lead" onchange="updateChemistry()"><div><strong>Свинець</strong></div></label>
        </div>
    </div>

    <div class="section">
        <div class="grid-inputs">
            <div class="input-group">
                <label>Послідовно (S):</label>
                <input type="number" id="seriesCount" value="4" min="1" oninput="calculateFromConfig()">
            </div>
            <div class="input-group">
                <label>Паралельно (P):</label>
                <input type="number" id="parallelCount" value="1" min="1" oninput="calculateFromConfig()">
            </div>
            <div class="input-group">
                <label>Напруга (V):</label>
                <input type="number" id="targetVoltage" value="12.8" step="0.1" oninput="calculateFromVoltage()">
            </div>
        </div>
    </div>

    <div class="results-box">
        <div class="results-grid">
            <div class="result-item">Номінальна напруга:<div class="result-value" id="resNomVoltage">12.8 V</div></div>
            <div class="result-item">Конфігурація:<div class="result-value" id="resConfig">4S 1P</div></div>
            <div class="result-item">Всього елементів:<div class="result-value" id="resTotalCells">4 шт.</div></div>
        </div>
    </div>

    <div class="visual-container">
        <div id="batteryMatrix" class="battery-matrix"></div>
    </div>

    <div class="footer">
        <p>Автор: <b>Dima Lasun</b></p>
        <a href="https://github.com/dimon-qrz" target="_blank">GitHub Profile</a> | 
        <a href="https://www.facebook.com/groups/3145673675685047" target="_blank">Група: Ремонт електрообладнання</a>
    </div>
</div>

<script>
    const chemistries = { liion: { nom: 3.6 }, lifepo4: { nom: 3.2 }, lead: { nom: 2.0 } };

    function getSelectedChemistry() {
        return chemistries[document.querySelector('input[name="chemistry"]:checked').value];
    }

    function calculateFromConfig() {
        let s = parseInt(document.getElementById('seriesCount').value) || 1;
        let p = parseInt(document.getElementById('parallelCount').value) || 1;
        const chem = getSelectedChemistry();
        const nomV = (s * chem.nom).toFixed(1);
        
        document.getElementById('targetVoltage').value = nomV;
        document.getElementById('resNomVoltage').innerText = nomV + ' V';
        document.getElementById('resConfig').innerText = s + 'S ' + p + 'P';
        document.getElementById('resTotalCells').innerText = (s * p) + ' шт.';
        renderVisual(s, p);
    }

    function calculateFromVoltage() {
        const targetV = parseFloat(document.getElementById('targetVoltage').value) || 0;
        const chem = getSelectedChemistry();
        document.getElementById('seriesCount').value = Math.max(1, Math.round(targetV / chem.nom));
        calculateFromConfig();
    }

    function updateChemistry() { calculateFromConfig(); }

    function renderVisual(s, p) {
        const container = document.getElementById('batteryMatrix');
        container.innerHTML = '';
        const limit = 10;
        for (let i = 0; i < Math.min(s, limit); i++) {
            const row = document.createElement('div');
            row.className = 'battery-row';
            for (let j = 0; j < Math.min(p, limit); j++) {
                const cell = document.createElement('div');
                cell.className = 'cell';
                row.appendChild(cell);
            }
            container.appendChild(row);
        }
    }

    calculateFromConfig();
</script>

</body>
</html>
