<script>
    // The Annals - Big Thang Theory League History
    
    // Championship History Data
    const champions = [
        { year: 2024, team: "Aumsville Mudhens", record: "8-6-0" },
        { year: 2023, team: "Team 9", record: "10-4-0" },
        { year: 2022, team: "88Dancing bears", record: "10-4-0" },
        { year: 2021, team: "Pack of Wild Bonzo's", record: "8-6-0" },
        { year: 2020, team: "Aumsville Mudhens", record: "10-3-0" },
        { year: 2019, team: "Champagnemarinade", record: "8-5-0" },
        { year: 2018, team: "Pack of Wild Bonzo's", record: "11-2-0" },
        { year: 2017, team: "Champagnemarinade", record: "8-5-0" },
        { year: 2016, team: "Nwlove", record: "9-4-0" },
        { year: 2015, team: "Pack of Wild Bonzo's", record: "9-4-0" }
    ];

    // Season Scoring Leaders
    const seasonScorers = [
        { year: 2024, team: "Pack of Wild Bonzo's", points: 1533.64 },
        { year: 2023, team: "88Dancing bears", points: 1446.66 },
        { year: 2022, team: "Champagnemarinade", points: 1588.18 },
        { year: 2021, team: "Mama Bear", points: 1550.42 },
        { year: 2020, team: "Champagnemarinade", points: 1472.42 },
        { year: 2019, team: "Aumsville Mudhens", points: 1607.18 },
        { year: 2018, team: "Nwlove", points: 1561.04 },
        { year: 2017, team: "Champagnemarinade", points: 1353.88 },
        { year: 2016, team: "Pack of Wild Bonzo's", points: 1448.08 },
        { year: 2015, team: "Pack of Wild Bonzo's", points: 1406.24 }
    ];

    // Weekly High Scorers
    const weeklyScorers = [
        { year: 2024, player: "J. Allen", position: "QB", team: "Aumsville Mudhens", week: 14, points: 54.88 },
        { year: 2023, player: "D. Achane", position: "RB", team: "Pack of Wild Bonzo's", week: 3, points: 50.80 },
        { year: 2022, player: "J. Mixon", position: "RB", team: "Spotieotiedopealiciousangels", week: 9, points: 51.10 },
        { year: 2021, player: "J. Taylor", position: "RB", team: "Team 9", week: 11, points: 50.40 },
        { year: 2020, player: "A. Kamara", position: "RB", team: "88Dancing bears", week: 16, points: 53.70 },
        { year: 2019, player: "A. Rodgers", position: "QB", team: "Rabble Rousers", week: 7, points: 48.76 },
        { year: 2018, player: "D. Henry", position: "RB", team: "Nwlove", week: 14, points: 52.80 },
        { year: 2017, player: "T. Gurley", position: "RB", team: "Champagnemarinade", week: 15, points: 43.50 },
        { year: 2016, player: "L. Bell", position: "RB", team: "88Dancing bears", week: 14, points: 49.80 },
        { year: 2015, player: "D. Brees", position: "QB", team: "Shaboids the Real Dirty Birds", week: 8, points: 51.30 }
    ];

    // Championship Count by Team
    const championshipCounts = {};
    champions.forEach(champ => {
        championshipCounts[champ.team] = (championshipCounts[champ.team] || 0) + 1;
    });

    const sortedChampions = Object.entries(championshipCounts)
        .sort(([,a], [,b]) => b - a)
        .map(([team, count]) => ({ team, count }));
</script>

<style>
    .annals-container {
        max-width: 1200px;
        margin: 0 auto;
        padding: 20px;
        color: var(--g555);
    }

    .header {
        text-align: center;
        margin-bottom: 40px;
    }

    .header h1 {
        font-size: 2.5em;
        margin-bottom: 10px;
        color: var(--primaryColor);
    }

    .subtitle {
        font-size: 1.2em;
        color: var(--g777);
        font-style: italic;
    }

    .section {
        margin: 40px 0;
        background: var(--fff);
        border-radius: 8px;
        padding: 25px;
        box-shadow: 0px 3px 6px rgba(0,0,0,0.1);
    }

    .section-title {
        font-size: 1.8em;
        margin-bottom: 20px;
        color: var(--primaryColor);
        border-bottom: 2px solid var(--primaryColor);
        padding-bottom: 10px;
    }

    .champions-grid {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
        gap: 20px;
        margin-top: 20px;
    }

    .champion-card {
        background: linear-gradient(135deg, #ffd700, #ffed4e);
        border-radius: 8px;
        padding: 20px;
        text-align: center;
        border: 2px solid #daa520;
        position: relative;
        overflow: hidden;
    }

    .champion-card::before {
        content: "🏆";
        position: absolute;
        top: -10px;
        right: -10px;
        font-size: 3em;
        opacity: 0.3;
    }

    .champion-year {
        font-size: 1.5em;
        font-weight: bold;
        color: #8b4513;
        margin-bottom: 10px;
    }

    .champion-team {
        font-size: 1.2em;
        font-weight: bold;
        color: #2c2c2c;
        margin-bottom: 5px;
    }

    .champion-record {
        color: #555;
        font-style: italic;
    }

    .stats-table {
        width: 100%;
        border-collapse: collapse;
        margin-top: 15px;
    }

    .stats-table th,
    .stats-table td {
        padding: 12px;
        text-align: left;
        border-bottom: 1px solid var(--bbb);
    }

    .stats-table th {
        background-color: var(--primaryColor);
        color: white;
        font-weight: bold;
    }

    .stats-table tr:nth-child(even) {
        background-color: var(--f5f5f5);
    }

    .stats-table tr:hover {
        background-color: var(--e8f4f8);
    }

    .championship-summary {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
        gap: 15px;
        margin-top: 20px;
    }

    .summary-card {
        background: var(--f9f9f9);
        border-radius: 6px;
        padding: 15px;
        text-align: center;
        border-left: 4px solid var(--primaryColor);
    }

    .summary-count {
        font-size: 2em;
        font-weight: bold;
        color: var(--primaryColor);
    }

    .summary-team {
        font-size: 0.9em;
        color: var(--g777);
        margin-top: 5px;
    }

    .era-note {
        background: var(--f0f8ff);
        border-left: 4px solid var(--primaryColor);
        padding: 15px;
        margin: 20px 0;
        border-radius: 4px;
    }

    .era-note strong {
        color: var(--primaryColor);
    }

    @media (max-width: 768px) {
        .annals-container {
            padding: 15px;
        }
        
        .header h1 {
            font-size: 2em;
        }
        
        .section {
            padding: 15px;
        }
        
        .champions-grid {
            grid-template-columns: 1fr;
        }
        
        .stats-table {
            font-size: 0.9em;
        }
        
        .stats-table th,
        .stats-table td {
            padding: 8px;
        }
    }
</style>

<div class="annals-container">
    <div class="header">
        <h1>The Annals</h1>
        <p class="subtitle">A Complete History of The Big Thang Theory Fantasy Football League</p>
    </div>

    <div class="era-note">
        <strong>The NFL.com Era (2015-2024):</strong> Our league's foundational decade, chronicling the rise and fall of fantasy dynasties before our migration to the Sleeper platform in 2025.
    </div>

    <div class="section">
        <h2 class="section-title">Championship History</h2>
        <div class="champions-grid">
            {#each champions as champion}
                <div class="champion-card">
                    <div class="champion-year">{champion.year}</div>
                    <div class="champion-team">{champion.team}</div>
                    <div class="champion-record">{champion.record}</div>
                </div>
            {/each}
        </div>
    </div>

    <div class="section">
        <h2 class="section-title">Championship Summary</h2>
        <div class="championship-summary">
            {#each sortedChampions as champ}
                <div class="summary-card">
                    <div class="summary-count">{champ.count}</div>
                    <div class="summary-team">{champ.team}</div>
                </div>
            {/each}
        </div>
    </div>

    <div class="section">
        <h2 class="section-title">Season Scoring Leaders</h2>
        <table class="stats-table">
            <thead>
                <tr>
                    <th>Year</th>
                    <th>Team</th>
                    <th>Points</th>
                </tr>
            </thead>
            <tbody>
                {#each seasonScorers as scorer}
                    <tr>
                        <td><strong>{scorer.year}</strong></td>
                        <td>{scorer.team}</td>
                        <td>{scorer.points}</td>
                    </tr>
                {/each}
            </tbody>
        </table>
    </div>

    <div class="section">
        <h2 class="section-title">Weekly High Scorers</h2>
        <table class="stats-table">
            <thead>
                <tr>
                    <th>Year</th>
                    <th>Player</th>
                    <th>Position</th>
                    <th>Team</th>
                    <th>Week</th>
                    <th>Points</th>
                </tr>
            </thead>
            <tbody>
                {#each weeklyScorers as scorer}
                    <tr>
                        <td><strong>{scorer.year}</strong></td>
                        <td>{scorer.player}</td>
                        <td>{scorer.position}</td>
                        <td>{scorer.team}</td>
                        <td>{scorer.week}</td>
                        <td>{scorer.points}</td>
                    </tr>
                {/each}
            </tbody>
        </table>
    </div>

    <div class="section">
        <h2 class="section-title">League Legacy</h2>
        <p>From 2015 to 2024, The Big Thang Theory league witnessed incredible performances, fierce rivalries, and unforgettable moments. As we transition to the Sleeper platform in 2025, we carry forward this rich history while building toward new traditions.</p>
        
        <p><strong>Notable Achievements:</strong></p>
        <ul>
            <li>Highest Single Season: Champagnemarinade (2022) - 1,588.18 points</li>
            <li>Best Regular Season Record: Pack of Wild Bonzo's (2018) - 11-2-0</li>
            <li>Most Championships: Pack of Wild Bonzo's (3 titles)</li>
            <li>Highest Weekly Score: J. Allen (2024) - 54.88 points</li>
        </ul>
    </div>
</div>
