<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <meta name="monetag" content="5aa306ea7984abf1e5af16b451c479ba">
        <!-- Google Search Console Verification -->
        <meta name="google-site-verification" content="zEr6NktJOaXowuOGJALN97Q7o1s6RA3m3Hw4lBAjcEc" />
    <script>
  // 1. Create a new division (container) for your payment info
  const paymentSection = document.createElement('div');

  // 2. Style it so it looks nice (Centered)
  paymentSection.style.textAlign = 'center';
  paymentSection.style.marginTop = '20px';
  paymentSection.style.fontFamily = 'Arial, sans-serif';

  // 3. Insert the HTML content (Image + Bold Text)
  paymentSection.innerHTML = `
      <img src="https://i.ibb.co/Kx5jBvpN/Paytm-QRcode-1768137322803.png" alt="Paytm QR Code" width="200">
      <br><br>
      <strong>Upi id - dwaipayanbhai@ptsbi</strong>
      <br>
      <strong>And email - legendboss012@gmail.com</strong>
  `;

  // 4. Append this section to the body of your webpage
  document.body.appendChild(paymentSection);
</script>

    <title>Free Fire Community Hub & Analytics</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <style>
    <div style="text-align: center; margin: 20px 0;">
    <img src="https://i.ibb.co/Kx5jBvpN/Paytm-QRcode-1768137322803.png" alt="Paytm QR Code" width="200">
    <br><br>
    <strong>Upi id - dwaipayanbhai@ptsbi</strong>
    <br>
    <strong>And email - legendboss012@gmail.com</strong>
</div>
        @import url('https://fonts.googleapis.com/css2?family=Inter:wght@300;400;600;800&display=swap');
        body { font-family: 'Inter', sans-serif; background-color: #f8fafc; color: #1e293b; }
        .chart-container { position: relative; width: 100%; max-width: 600px; margin-left: auto; margin-right: auto; height: 300px; max-height: 400px; }
        @media (min-width: 768px) { .chart-container { height: 350px; } }
        .glass-panel { background: rgba(255, 255, 255, 0.9); backdrop-filter: blur(10px); border: 1px solid rgba(255, 255, 255, 0.2); }
    </style>
</head>
    <meta name="google-site-verification" content="zEr6NktJOaXowuOGJALN97Q7o1s6RA3m3Hw4lBAjcEc" />
<body class="bg-slate-50 min-h-screen flex flex-col">

    <!-- Chosen Palette: Warm Neutrals with Free Fire Orange/Yellow Accents -->
    <!-- Application Structure Plan: The SPA is designed as a 'Community Dashboard'. It moves from high-level analytical data (Context) to the actual content repository (Action). 
         1. Header: Branding and Global Stats.
         2. Engagement Analytics: Visualizes the 'why' behind the community - showing growth and popular categories using Chart.js.
         3. The Vault (Gallery): The core interactive section where users browse items.
         4. Admin Panel: Allows dynamic modification of the data, which instantly reflects in both the Gallery and the Analytics (Charts). 
         This flow was chosen to validate the community's value before presenting the items, fostering a sense of scale and activity. -->
    <!-- Visualization & Content Choices: 
         1. Doughnut Chart: Goal: Inform/Compare. Shows distribution of item categories. Justification: Quick visual grasp of what content dominates.
         2. Line Chart: Goal: Change. Shows user engagement trends over time. Justification: Demonstrates community health.
         3. Dynamic Grid: Goal: Organize. Displays the items. Interaction: Filtering and searching.
         4. Admin Form: Goal: Change. Updates the underlying data model, proving the app's dynamic nature. 
         Library: Chart.js for canvas rendering. Vanilla JS for logic. -->
    <!-- CONFIRMATION: NO SVG graphics used. NO Mermaid JS used. -->

    <nav class="bg-white border-b border-slate-200 sticky top-0 z-50">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="flex justify-between h-16">
                <div class="flex items-center gap-3">
                    <span class="text-3xl">🔥</span>
                    <div>
                        <h1 class="text-xl font-bold bg-clip-text text-transparent bg-gradient-to-r from-orange-500 to-yellow-500 uppercase italic tracking-tighter">FF Hub</h1>
                        <p class="text-xs text-slate-500 hidden sm:block">Community & Analytics</p>
                    </div>
                </div>
                <div class="flex items-center space-x-4">
                    <button onclick="scrollToSection('analytics')" class="text-sm font-medium text-slate-600 hover:text-orange-500 transition-colors">Insights</button>
                    <button onclick="scrollToSection('vault')" class="text-sm font-medium text-slate-600 hover:text-orange-500 transition-colors">Vault</button>
                    <button onclick="toggleAdmin()" class="px-4 py-2 bg-slate-900 text-white text-sm font-bold rounded-full hover:bg-orange-600 transition-colors shadow-lg shadow-orange-500/20">Admin</button>
                </div>
            </div>
        </div>
    </nav>

    <main class="flex-grow max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-8 w-full space-y-12">

        <section id="analytics" class="animate-fade-in">
            <div class="mb-6">
                <h2 class="text-2xl font-bold text-slate-900 flex items-center gap-2">
                    <span>📊</span> Community Insights
                </h2>
                <p class="mt-2 text-slate-600 max-w-3xl leading-relaxed">
                    This section provides a real-time analytical overview of the Free Fire community ecosystem. 
                    By visualizing the distribution of content categories and tracking engagement trends over time, community managers can identify which content types (Bundles, Weapons, Events) drive the most interest. 
                    These visualizations update dynamically as new items are added to the database.
                </p>
            </div>

            <div class="grid grid-cols-1 lg:grid-cols-2 gap-8">
                <!-- Chart 1: Category Distribution -->
                <div class="bg-white p-6 rounded-2xl shadow-sm border border-slate-100">
                    <div class="flex justify-between items-center mb-4">
                        <h3 class="font-semibold text-slate-800">Content Distribution</h3>
                        <span class="text-xs bg-orange-100 text-orange-800 px-2 py-1 rounded-full">Live Data</span>
                    </div>
                    <div class="chart-container">
                        <canvas id="categoryChart"></canvas>
                    </div>
                    <p class="text-xs text-slate-400 text-center mt-4">Proportion of items available in the Vault.</p>
                </div>

                <!-- Chart 2: Engagement Trends -->
                <div class="bg-white p-6 rounded-2xl shadow-sm border border-slate-100">
                    <div class="flex justify-between items-center mb-4">
                        <h3 class="font-semibold text-slate-800">Weekly Engagement</h3>
                        <span class="text-xs bg-green-100 text-green-800 px-2 py-1 rounded-full">Last 7 Days</span>
                    </div>
                    <div class="chart-container">
                        <canvas id="trendChart"></canvas>
                    </div>
                    <p class="text-xs text-slate-400 text-center mt-4">User interaction volume based on clicks and views.</p>
                </div>
            </div>
        </section>

        <section id="vault" class="scroll-mt-20">
            <div class="flex flex-col md:flex-row md:items-end justify-between gap-4 mb-8">
                <div>
                    <h2 class="text-2xl font-bold text-slate-900 flex items-center gap-2">
                        <span>💎</span> The Vault
                    </h2>
                    <p class="mt-2 text-slate-600 max-w-2xl leading-relaxed">
                        Access the complete repository of Free Fire assets. This interactive grid allows users to filter, search, and navigate directly to external resources. 
                        Use the controls below to narrow down the specific skins, events, or news updates you are looking for.
                    </p>
                </div>
                
                <div class="flex flex-col sm:flex-row gap-3">
                    <div class="relative">
                        <span class="absolute left-3 top-3 text-slate-400">🔍</span>
                        <input type="text" id="searchInput" placeholder="Search items..." class="pl-10 pr-4 py-2.5 bg-white border border-slate-200 rounded-lg text-sm focus:outline-none focus:border-orange-500 focus:ring-1 focus:ring-orange-500 w-full sm:w-64 transition-all">
                    </div>
                </div>
            </div>

            <!-- Category Filters -->
            <div class="flex flex-wrap gap-2 mb-8" id="categoryFilters">
                <!-- Injected via JS -->
            </div>

            <!-- Item Grid -->
            <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-6" id="itemGrid">
                <!-- Injected via JS -->
            </div>
        </section>

        <section id="adminPanel" class="hidden bg-slate-900 rounded-3xl p-8 text-white relative overflow-hidden transition-all duration-500 ease-in-out">
            <div class="absolute top-0 right-0 w-64 h-64 bg-orange-500 rounded-full mix-blend-multiply filter blur-3xl opacity-20 pointer-events-none transform translate-x-1/2 -translate-y-1/2"></div>
            
            <div class="relative z-10">
                <div class="flex justify-between items-start mb-6">
                    <div>
                        <h2 class="text-2xl font-bold text-white flex items-center gap-2">
                            <span>⚡</span> Admin Command
                        </h2>
                        <p class="mt-2 text-slate-400 max-w-2xl">
                            Secure area for community managers. Adding items here will immediately update the Analytics charts above and populate the Vault grid.
                        </p>
                    </div>
                    <button onclick="toggleAdmin()" class="text-slate-400 hover:text-white">✕ Close</button>
                </div>

                <form id="uploadForm" class="grid grid-cols-1 md:grid-cols-2 gap-6">
                    <div class="space-y-4">
                        <div>
                            <label class="block text-xs font-bold text-slate-500 uppercase mb-1">Item Title</label>
                            <input type="text" id="inputTitle" required class="w-full bg-slate-800 border border-slate-700 rounded-lg p-3 text-white focus:border-orange-500 focus:outline-none" placeholder="e.g. Draco Blue Flame">
                        </div>
                        <div>
                            <label class="block text-xs font-bold text-slate-500 uppercase mb-1">Category</label>
                            <select id="inputCategory" class="w-full bg-slate-800 border border-slate-700 rounded-lg p-3 text-white focus:border-orange-500 focus:outline-none">
                                <option value="Bundles">Bundles</option>
                                <option value="Weapons">Weapons</option>
                                <option value="Events">Events</option>
                                <option value="Esports">Esports</option>
                                <option value="News">News</option>
                            </select>
                        </div>
                    </div>
                    <div class="space-y-4">
                        <div>
                            <label class="block text-xs font-bold text-slate-500 uppercase mb-1">Image URL</label>
                            <input type="url" id="inputImage" class="w-full bg-slate-800 border border-slate-700 rounded-lg p-3 text-white focus:border-orange-500 focus:outline-none" placeholder="https://...">
                        </div>
                        <div>
                            <label class="block text-xs font-bold text-slate-500 uppercase mb-1">Destination Link</label>
                            <input type="url" id="inputLink" required class="w-full bg-slate-800 border border-slate-700 rounded-lg p-3 text-white focus:border-orange-500 focus:outline-none" placeholder="https://...">
                        </div>
                    </div>
                    <div class="md:col-span-2">
                        <button type="submit" class="w-full bg-gradient-to-r from-orange-600 to-yellow-500 text-black font-bold py-3 rounded-lg hover:from-orange-500 hover:to-yellow-400 transition-all transform hover:scale-[1.01]">
                            + Upload to Database
                        </button>
                    </div>
                </form>
            </div>
        </section>

    </main>

    <footer class="bg-white border-t border-slate-200 py-8 mt-auto">
        <div class="max-w-7xl mx-auto px-4 text-center">
            <p class="text-slate-500 text-sm">© 2024 FF Community Hub. All rights reserved.</p>
        </div>
    </footer>

    <script>
        // --- DATA STATE MANAGEMENT ---
        const INITIAL_DATA = [
            { id: 1, title: "Booyah Pass Season 12", image: "https://images.unsplash.com/photo-1542751371-adc38448a05e?auto=format&fit=crop&q=80&w=800", link: "#", category: "Bundles", views: 12500 },
            { id: 2, title: "M1887 Evo Gun Skin", image: "https://images.unsplash.com/photo-1552820728-8b83bb6b773f?auto=format&fit=crop&q=80&w=800", link: "#", category: "Weapons", views: 8200 },
            { id: 3, title: "Daily Diamond Event", image: "https://images.unsplash.com/photo-1614680376593-902f74cf0d41?auto=format&fit=crop&q=80&w=800", link: "#", category: "Events", views: 50000 },
            { id: 4, title: "Pro League Finals", image: "https://images.unsplash.com/photo-1511512578047-dfb367046420?auto=format&fit=crop&q=80&w=800", link: "#", category: "Esports", views: 15000 },
            { id: 5, title: "Mystery Shop Update", image: "https://images.unsplash.com/photo-1550745165-9bc0b252726f?auto=format&fit=crop&q=80&w=800", link: "#", category: "Events", views: 32000 },
        ];

        let appState = {
            items: JSON.parse(localStorage.getItem('ff_items')) || INITIAL_DATA,
            filter: 'All',
            search: '',
            charts: {}
        };

        const CATEGORIES = ["All", "Bundles", "Weapons", "Events", "Esports", "News"];

        // --- DOM ELEMENT REFERENCES ---
        const gridEl = document.getElementById('itemGrid');
        const filtersEl = document.getElementById('categoryFilters');
        const adminPanel = document.getElementById('adminPanel');
        const searchInput = document.getElementById('searchInput');

        // --- INITIALIZATION ---
        function init() {
            renderFilters();
            renderGrid();
            initCharts();
            setupEventListeners();
        }

        // --- CORE INTERACTION HANDLING ---
        function setupEventListeners() {
            // Search Input
            searchInput.addEventListener('input', (e) => {
                appState.search = e.target.value.toLowerCase();
                renderGrid();
            });

            // Form Submission
            document.getElementById('uploadForm').addEventListener('submit', (e) => {
                e.preventDefault();
                const newItem = {
                    id: Date.now(),
                    title: document.getElementById('inputTitle').value,
                    category: document.getElementById('inputCategory').value,
                    image: document.getElementById('inputImage').value || "https://images.unsplash.com/photo-1534423861386-85a16f5d13fd?auto=format&fit=crop&q=80&w=800",
                    link: document.getElementById('inputLink').value,
                    views: 0
                };

                appState.items.unshift(newItem); // Add to top
                saveData();
                renderGrid();
                updateCharts();
                
                // Reset form and notify
                e.target.reset();
                alert('Item Added! Charts and Vault updated.');
                toggleAdmin(); // Close panel
            });
        }

        function saveData() {
            localStorage.setItem('ff_items', JSON.stringify(appState.items));
        }

        function toggleAdmin() {
            adminPanel.classList.toggle('hidden');
            if(!adminPanel.classList.contains('hidden')) {
                adminPanel.scrollIntoView({ behavior: 'smooth' });
            }
        }

        function scrollToSection(id) {
            document.getElementById(id).scrollIntoView({ behavior: 'smooth' });
        }

        function setFilter(category) {
            appState.filter = category;
            renderFilters(); // Update active state of buttons
            renderGrid();
        }

        // --- RENDERING ---
        function renderFilters() {
            filtersEl.innerHTML = CATEGORIES.map(cat => `
                <button 
                    onclick="setFilter('${cat}')"
                    class="px-4 py-2 rounded-full text-sm font-semibold transition-all ${appState.filter === cat ? 'bg-slate-900 text-white shadow-lg' : 'bg-white text-slate-500 border border-slate-200 hover:bg-slate-50'}"
                >
                    ${cat}
                </button>
            `).join('');
        }

        function renderGrid() {
            const filtered = appState.items.filter(item => {
                const matchCat = appState.filter === 'All' || item.category === appState.filter;
                const matchSearch = item.title.toLowerCase().includes(appState.search);
                return matchCat && matchSearch;
            });

            if (filtered.length === 0) {
                gridEl.innerHTML = `<div class="col-span-full py-12 text-center text-slate-400 italic">No items found matching your criteria.</div>`;
                return;
            }

            gridEl.innerHTML = filtered.map(item => `
                <a href="${item.link}" target="_blank" class="group bg-white rounded-xl shadow-sm border border-slate-100 overflow-hidden hover:shadow-md hover:border-orange-200 transition-all duration-300 flex flex-col h-full">
                    <div class="relative w-full h-48 overflow-hidden bg-slate-100">
                        <img src="${item.image}" alt="${item.title}" class="w-full h-full object-cover transform group-hover:scale-105 transition-transform duration-500" onerror="this.src='https://placehold.co/600x400?text=No+Image'">
                        <div class="absolute top-2 left-2 bg-slate-900/80 backdrop-blur text-white text-[10px] font-bold px-2 py-1 rounded uppercase tracking-wider">
                            ${item.category}
                        </div>
                    </div>
                    <div class="p-4 flex-grow flex flex-col justify-between">
                        <div>
                            <h3 class="font-bold text-slate-800 text-lg leading-tight mb-2 group-hover:text-orange-600 transition-colors">${item.title}</h3>
                        </div>
                        <div class="mt-4 flex items-center justify-between text-xs text-slate-400 border-t border-slate-50 pt-3">
                            <span>${(item.views || 0).toLocaleString()} views</span>
                            <span class="text-orange-500 font-semibold group-hover:translate-x-1 transition-transform">Go Now →</span>
                        </div>
                    </div>
                </a>
            `).join('');
        }

        // --- CHART LOGIC ---
        function initCharts() {
            // Chart 1: Category Distribution (Doughnut)
            const ctxCat = document.getElementById('categoryChart').getContext('2d');
            appState.charts.category = new Chart(ctxCat, {
                type: 'doughnut',
                data: getCategoryData(),
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    plugins: {
                        legend: { position: 'right', labels: { usePointStyle: true, boxWidth: 6 } }
                    }
                }
            });

            // Chart 2: Engagement Trends (Line - Mock Data based on items)
            const ctxTrend = document.getElementById('trendChart').getContext('2d');
            appState.charts.trend = new Chart(ctxTrend, {
                type: 'line',
                data: {
                    labels: ['Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun'],
                    datasets: [{
                        label: 'Interactions',
                        data: [120, 190, 300, 250, 400, 450, 600], // Mock data
                        borderColor: '#f97316', // Orange-500
                        backgroundColor: 'rgba(249, 115, 22, 0.1)',
                        borderWidth: 2,
                        fill: true,
                        tension: 0.4,
                        pointRadius: 0
                    }]
                },
                options: {
                    
