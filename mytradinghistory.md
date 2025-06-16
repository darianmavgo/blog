<!DOCTYPE html>
<html lang="en" class="scroll-smooth">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My Trading Journey: A Decade of Code & Hard Lessons</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;700&display=swap" rel="stylesheet">
    <!-- Chosen Palette: Warm Neutral & Muted Blue -->
    <!-- Application Structure Plan: The application is structured as a single-page, vertical-scrolling narrative to mirror the storytelling format of the source essay. A sticky navigation bar allows users to jump to thematic sections: The Timeline, The Strategies, The Tech Stack, Hard Lessons, and The Conclusion. This structure was chosen over a dashboard because the source material is a personal journey, not a data-heavy report. The goal is to guide the user through the story chronologically and thematically, allowing them to explore key aspects like strategy performance and technological evolution in a digestible, interactive format. Key interactions include a clickable timeline and an interactive chart to visualize backtest performance. -->
    <!-- Visualization & Content Choices: 
        - Timeline (HTML/CSS): Goal: Show the long duration of the journey. Method: A responsive, horizontal timeline. Interaction: Clicking a year reveals contextual text. Justification: More engaging and visually structured than a simple text list.
        - Backtest Performance (Chart.js Line Chart): Goal: Compare and visualize the volatile performance of the "Whitings Creek" strategy, highlighting the 2020 crash. Method: A cumulative P&L line chart. Interaction: Tooltips on hover provide specific monthly data. Justification: A cumulative chart powerfully tells the story of the strategy's rise and fall, which is more impactful than raw monthly bars.
        - Tech Stack Evolution (HTML/CSS Diagram): Goal: Organize and clarify the technological progression. Method: A flexbox-based visual flowchart. Interaction: None needed. Justification: Simplifies a complex technical narrative into an easy-to-understand graphic.
        - Key Setbacks (HTML/CSS Callout Cards): Goal: Inform and emphasize critical learning moments. Method: Distinctly styled cards with icons. Interaction: None. Justification: Visually isolates and gives weight to the most impactful "hard lessons" of the journey. -->
    <!-- CONFIRMATION: NO SVG graphics used. NO Mermaid JS used. -->
    <style>
        body {
            font-family: 'Inter', sans-serif;
            background-color: #F5F5F4; /* stone-100 */
            color: #374151; /* gray-700 */
        }
        .nav-link {
            transition: color 0.3s ease;
        }
        .nav-link:hover {
            color: #3B82F6; /* blue-500 */
        }
        .timeline-item-content {
            transition: all 0.3s ease-in-out;
        }
        .chart-container {
            position: relative;
            width: 100%;
            max-width: 800px;
            margin-left: auto;
            margin-right: auto;
            height: 300px;
            max-height: 400px;
        }
        @media (min-width: 768px) {
            .chart-container {
                height: 400px;
            }
        }
    </style>
</head>
<body class="antialiased">

    <!-- Header & Navigation -->
    <header class="bg-stone-100/80 backdrop-blur-md sticky top-0 z-50 border-b border-stone-200">
        <nav class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="flex items-center justify-between h-16">
                <div class="flex items-center">
                    <span class="font-bold text-lg text-gray-800">The Trading Journey</span>
                </div>
                <div class="hidden md:block">
                    <div class="ml-10 flex items-baseline space-x-4">
                        <a href="#timeline" class="nav-link px-3 py-2 rounded-md text-sm font-medium text-gray-600">Timeline</a>
                        <a href="#strategies" class="nav-link px-3 py-2 rounded-md text-sm font-medium text-gray-600">Strategies</a>
                        <a href="#tech" class="nav-link px-3 py-2 rounded-md text-sm font-medium text-gray-600">Tech Stack</a>
                        <a href="#lessons" class="nav-link px-3 py-2 rounded-md text-sm font-medium text-gray-600">Hard Lessons</a>
                        <a href="#conclusion" class="nav-link px-3 py-2 rounded-md text-sm font-medium text-gray-600">Conclusion</a>
                    </div>
                </div>
            </div>
        </nav>
    </header>

    <main class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-12">

        <!-- Hero Section -->
        <section class="text-center py-16">
            <h1 class="text-4xl md:text-5xl font-bold text-gray-800 tracking-tight">My Trading Journey</h1>
            <p class="mt-6 max-w-3xl mx-auto text-lg md:text-xl text-gray-500">A decade-long roller coaster with markets, code, and the painful search for a winning edge.</p>
        </section>

        <!-- The Timeline Section -->
        <section id="timeline" class="py-16">
             <div class="text-center mb-12">
                <h2 class="text-3xl font-bold text-gray-800">A Winding Road</h2>
                <p class="mt-4 max-w-2xl mx-auto text-lg text-gray-500">This wasn't a sprint; it was a marathon of trial and error spanning over a decade. Each year brought new ideas, new technologies, and new challenges. Click on a year to see the highlights of that period.</p>
            </div>
            <div id="timeline-container" class="relative">
                <!-- Timeline line -->
                <div class="hidden sm:block absolute left-1/2 h-full w-0.5 bg-stone-300 -translate-x-1/2"></div>
                
                <!-- Timeline items will be injected here by JS -->
            </div>
        </section>

        <!-- The Strategies Section -->
        <section id="strategies" class="py-16">
            <div class="text-center mb-12">
                <h2 class="text-3xl font-bold text-gray-800">The Search for a Strategy</h2>
                <p class="mt-4 max-w-2xl mx-auto text-lg text-gray-500">At the core of this journey was the hunt for a repeatable, profitable strategy. From simple observations to complex rules, the approach evolved, but the results were often humbling.</p>
            </div>
            <div class="grid md:grid-cols-2 gap-8 items-start">
                <div class="space-y-6">
                    <div class="bg-white p-6 rounded-lg shadow-sm border border-stone-200">
                        <h3 class="text-xl font-bold text-gray-800">Strategy: Whitings Creek</h3>
                        <p class="text-gray-500 mt-2">The primary strategy, based on a mean-reversion concept.</p>
                        <ul class="mt-4 space-y-2 text-gray-600 list-inside list-disc">
                            <li><strong>Trigger:</strong> Stock drops 10% from a 10-day low.</li>
                            <li><strong>Entry:</strong> Buy at 3% below the previous day's close.</li>
                            <li><strong>Profit Target:</strong> Sell for a 5% gain.</li>
                            <li><strong>Exit Rule:</strong> Sell at market open on Day 3 if profit target isn't met.</li>
                            <li><strong>Filters:</strong> Stocks > $3, Volume > 100k, No Leveraged ETFs.</li>
                        </ul>
                    </div>
                    <div class="bg-white p-6 rounded-lg shadow-sm border border-stone-200">
                        <h3 class="text-xl font-bold text-gray-800">Strategy: Dover</h3>
                        <p class="text-gray-500 mt-2">An extreme version of Whitings Creek, looking for deeper drops.</p>
                         <ul class="mt-4 space-y-2 text-gray-600 list-inside list-disc">
                            <li><strong>Trigger:</strong> Stock drops 20% from a 10-day low.</li>
                            <li class="text-gray-400">Result: Primarily led to fewer trades, with no significant advantage over the original strategy.</li>
                        </ul>
                    </div>
                </div>
                <div class="bg-white p-6 rounded-lg shadow-sm border border-stone-200">
                     <h3 class="text-xl font-bold text-gray-800 mb-4 text-center">Backtest Performance (Aug 2019 - Aug 2020)</h3>
                     <p class="text-center text-gray-500 mb-4 text-sm">This chart visualizes the cumulative profit and loss of the "Whitings Creek" backtest. It highlights the extreme volatility and the devastating impact of the March 2020 market crash, a recurring theme in the testing results.</p>
                    <div class="chart-container">
                        <canvas id="performanceChart"></canvas>
                    </div>
                </div>
            </div>
        </section>

        <!-- Tech Stack Evolution Section -->
        <section id="tech" class="py-16">
            <div class="text-center mb-12">
                <h2 class="text-3xl font-bold text-gray-800">The Technology Evolution</h2>
                <p class="mt-4 max-w-2xl mx-auto text-lg text-gray-500">The tools and technologies changed as much as the strategies. The goal was always to build a faster, more reliable, and more powerful backtesting engine from the ground up.</p>
            </div>
            <div class="max-w-4xl mx-auto bg-white p-8 rounded-lg shadow-sm border border-stone-200">
                <div class="flex flex-col md:flex-row justify-between items-center space-y-8 md:space-y-0 md:space-x-8">
                    <div class="text-center p-4 rounded-lg bg-stone-50 border">
                        <h4 class="font-bold text-lg">Phase 1: Python</h4>
                        <p class="text-gray-500">Pandas & Google Sheets</p>
                        <p class="text-sm mt-2 text-red-500">Flaw: Brittle, slow, led to costly manual errors.</p>
                    </div>
                    <div class="text-3xl text-stone-400 font-thin">→</div>
                    <div class="text-center p-4 rounded-lg bg-stone-50 border">
                        <h4 class="font-bold text-lg">Phase 2: SQLite</h4>
                        <p class="text-gray-500">Standalone Database</p>
                        <p class="text-sm mt-2 text-blue-500">Advantage: Fast, reliable, eliminated data integrity issues.</p>
                    </div>
                    <div class="text-3xl text-stone-400 font-thin">→</div>
                     <div class="text-center p-4 rounded-lg bg-stone-50 border">
                        <h4 class="font-bold text-lg">Phase 3: Go & SQL</h4>
                        <p class="text-gray-500">Go App Engine + SQL Scripts</p>
                        <p class="text-sm mt-2 text-green-500">Result: Powerful, efficient, chainable logic for complex backtests.</p>
                    </div>
                </div>
            </div>
        </section>

        <!-- Hard Lessons Section -->
        <section id="lessons" class="py-16">
             <div class="text-center mb-12">
                <h2 class="text-3xl font-bold text-gray-800">Hard-Won Lessons</h2>
                <p class="mt-4 max-w-2xl mx-auto text-lg text-gray-500">Some lessons are only learned through failure. These were the moments that were financially and emotionally costly, but ultimately shaped the final perspective.</p>
            </div>
            <div class="grid md:grid-cols-2 gap-8 max-w-4xl mx-auto">
                <div class="bg-white p-6 rounded-lg shadow-sm border border-red-200">
                    <h3 class="font-bold text-lg text-red-800">The $10,000 Error</h3>
                    <p class="mt-2 text-gray-600">A simple Python script reading the wrong column from a Google Sheet caused a $10,000 loss in a single day, forcing a complete migration to the more robust SQLite.</p>
                </div>
                <div class="bg-white p-6 rounded-lg shadow-sm border border-red-200">
                    <h3 class="font-bold text-lg text-red-800">The OILU Catastrophe</h3>
                    <p class="mt-2 text-gray-600">A $65,000 loss concentrated in leveraged oil ETFs. A bet on a quick recovery turned into a complete wipeout when the ETF was liquidated, making the position worthless.</p>
                </div>
            </div>
        </section>

        <!-- Conclusion Section -->
        <section id="conclusion" class="py-16 text-center bg-white rounded-lg shadow-sm border border-stone-200">
            <h2 class="text-3xl font-bold text-gray-800">The Final Takeaway</h2>
            <div class="mt-6 max-w-3xl mx-auto space-y-4 text-lg text-gray-600">
                <p>After all these years, all the code, the late nights, the thousands of backtests, and the very real financial losses, the conclusion is painfully clear. The most financially successful things I've ever done were selling my house and an undeveloped lot of land.</p>
                <p class="italic">I'm afraid to actually add up all the money I’ve lost actively trading since 2008. It's certainly more than my passive investments have gained. It feels like a colossal waste of my youth, all this effort spent trying to accumulate wealth through a shortcut that, for me, never existed.</p>
                <p>Now I know about index funds like VTSAX. The smart thing to do is to just park my money there, even with the uncomfortable reality of having to sell some of it to live on. It’s a hard pill to swallow, but my long, painful journey has taught me that the most complex path is rarely the most profitable one.</p>
            </div>
        </section>

    </main>
    
    <footer class="text-center py-8 border-t border-stone-200">
        <p class="text-sm text-gray-500">An interactive narrative based on a personal journey. Created 2024.</p>
    </footer>

    <script>
        document.addEventListener('DOMContentLoaded', function() {
            // --- Timeline Data & Logic ---
            const timelineData = [
                {
                    year: '2008',
                    side: 'left',
                    title: 'The Spark',
                    text: 'The journey begins with a simple observation: stocks that fall hard often recover a little. Early success with this idea is wiped out by the financial crisis, resulting in major losses.'
                },
                {
                    year: '2015',
                    side: 'right',
                    title: 'Early Coding Attempts',
                    text: 'Sporadic efforts to code a trading system in Python for Interactive Brokers. The focus isn\'t yet fully dedicated.'
                },
                {
                    year: '2019',
                    side: 'left',
                    title: 'Getting Serious with Backtesting',
                    text: 'A deep dive into the `backtrader` Python library. Frustration with its limitations leads to the decision to build a custom backtesting engine using SQLite.'
                },
                {
                    year: '2020',
                    side: 'right',
                    title: 'Trial by Fire',
                    text: 'A year of intense development, live trading, and painful lessons. The March COVID crash invalidates every strategy, and major losses in oil ETFs force a reckoning. The tech stack evolves to Go and SQL for speed and reliability.'
                },
                 {
                    year: 'Present',
                    side: 'left',
                    title: 'A New Perspective',
                    text: 'After years of struggle, the conclusion is reached: passive investing in index funds like VTSAX is a more reliable path to wealth accumulation than the fruitless search for a trading edge.'
                },
            ];

            const timelineContainer = document.getElementById('timeline-container');
            timelineData.forEach(item => {
                const isLeft = item.side === 'left';
                const timelineElement = document.createElement('div');
                timelineElement.classList.add('timeline-item', 'mb-8', 'flex', 'justify-between', 'items-center', 'w-full');
                if (!isLeft) {
                    timelineElement.classList.add('flex-row-reverse', 'sm:flex-row');
                }

                timelineElement.innerHTML = `
                    <div class="order-1 w-5/12 sm:w-5/12"></div>
                    <div class="z-20 flex items-center order-1 bg-stone-800 shadow-xl w-8 h-8 rounded-full">
                        <h1 class="mx-auto font-semibold text-sm text-white">${item.year}</h1>
                    </div>
                    <div class="order-1 bg-white rounded-lg shadow-sm border border-stone-200 w-full sm:w-5/12 px-6 py-4 cursor-pointer timeline-item-content">
                        <h3 class="font-bold text-gray-800 text-lg">${item.title}</h3>
                        <p class="text-sm leading-snug tracking-wide text-gray-500 text-opacity-100 h-0 opacity-0">${item.text}</p>
                    </div>
                `;
                timelineContainer.appendChild(timelineElement);

                const content = timelineElement.querySelector('.timeline-item-content');
                content.addEventListener('click', () => {
                    const textP = content.querySelector('p');
                    textP.classList.toggle('h-0');
                    textP.classList.toggle('opacity-0');
                    textP.classList.toggle('mt-2');
                });
            });


            // --- Chart.js Performance Chart ---
            const ctx = document.getElementById('performanceChart').getContext('2d');
            
            const backtestData = [
                { ym: "2019-08", gain: -4895.17 }, { ym: "2019-09", gain: -5328.47 },
                { ym: "2019-10", gain: -806.89 }, { ym: "2019-11", gain: 8574.63 },
                { ym: "2019-12", gain: 749.60 }, { ym: "2020-01", gain: -10552.04 },
                { ym: "2020-02", gain: -19104.10 }, { ym: "2020-03", gain: -42841.04 },
                { ym: "2020-04", gain: 14577.89 }, { ym: "2020-05", gain: 1631.33 },
                { ym: "2020-06", gain: 4732.97 }, { ym: "2020-07", gain: 1801.99 },
                { ym: "2020-08", gain: -5154.77 }
            ];

            let cumulativeGain = 0;
            const cumulativeData = backtestData.map(d => {
                cumulativeGain += d.gain;
                return cumulativeGain;
            });

            const labels = backtestData.map(d => d.ym);

            const performanceChart = new Chart(ctx, {
                type: 'line',
                data: {
                    labels: labels,
                    datasets: [{
                        label: 'Cumulative P&L ($)',
                        data: cumulativeData,
                        borderColor: '#3B82F6', // blue-500
                        backgroundColor: 'rgba(59, 130, 246, 0.1)',
                        borderWidth: 2,
                        pointBackgroundColor: '#3B82F6',
                        tension: 0.1,
                        fill: true,
                    }]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    scales: {
                        y: {
                            beginAtZero: false,
                             ticks: {
                                callback: function(value, index, values) {
                                    return '$' + value.toLocaleString();
                                }
                            }
                        },
                        x: {
                           ticks: {
                                maxRotation: 45,
                                minRotation: 45
                           }
                        }
                    },
                    plugins: {
                        tooltip: {
                            callbacks: {
                                label: function(context) {
                                    let label = context.dataset.label || '';
                                    if (label) {
                                        label += ': ';
                                    }
                                    if (context.parsed.y !== null) {
                                        label += new Intl.NumberFormat('en-US', { style: 'currency', currency: 'USD' }).format(context.parsed.y);
                                    }
                                    return label;
                                }
                            }
                        },
                        legend: {
                            display: false
                        }
                    }
                }
            });
             // --- Smooth scrolling for nav links ---
            document.querySelectorAll('a[href^="#"]').forEach(anchor => {
                anchor.addEventListener('click', function (e) {
                    e.preventDefault();
                    document.querySelector(this.getAttribute('href')).scrollIntoView({
                        behavior: 'smooth'
                    });
                });
            });
        });
    </script>
</body>
</html>
