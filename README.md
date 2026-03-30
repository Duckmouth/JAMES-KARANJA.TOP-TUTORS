<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=yes">
  <title>James Karanja | PhD-Level Assignment Help — Real-time Order Hub</title>
  <!-- Google Fonts + Font Awesome Icons -->
  <link href="https://fonts.googleapis.com/css2?family=Inter:opsz,wght@14..32,300;14..32,400;14..32,600;14..32,700;14..32,800&display=swap" rel="stylesheet">
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
  <!-- Chart.js for live analytics feel -->
  <script src="https://cdn.jsdelivr.net/npm/chart.js@4.4.0/dist/chart.umd.min.js"></script>
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      font-family: 'Inter', sans-serif;
      background: #f6f9fc;
      color: #0a1e2f;
      line-height: 1.5;
      scroll-behavior: smooth;
    }

    /* premium glassmorphism + subtle grid */
    .bg-noise {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background-image: radial-gradient(#e0e7ff 0.8px, transparent 0.8px);
      background-size: 28px 28px;
      opacity: 0.3;
      pointer-events: none;
      z-index: -2;
    }

    .container {
      max-width: 1440px;
      margin: 0 auto;
      padding: 0 32px;
    }

    /* header */
    .hero {
      background: linear-gradient(135deg, #0b2b3f 0%, #0a1c2a 100%);
      color: white;
      border-radius: 0 0 48px 48px;
      padding: 2rem 0 3rem 0;
      box-shadow: 0 20px 35px -12px rgba(0,0,0,0.2);
      position: relative;
      z-index: 2;
    }

    .hero-content {
      display: flex;
      flex-wrap: wrap;
      justify-content: space-between;
      align-items: center;
      gap: 2rem;
    }

    .brand h1 {
      font-size: 2.8rem;
      font-weight: 800;
      letter-spacing: -0.02em;
      background: linear-gradient(120deg, #FFF, #b9e6ff);
      -webkit-background-clip: text;
      background-clip: text;
      color: transparent;
    }
    .brand p {
      font-size: 1rem;
      opacity: 0.85;
      margin-top: 8px;
    }

    .expert-badge {
      background: rgba(255,255,240,0.12);
      backdrop-filter: blur(8px);
      border-radius: 60px;
      padding: 10px 24px;
      font-weight: 500;
      border: 1px solid rgba(255,255,255,0.2);
    }

    /* guarantee cards */
    .guarantee-grid {
      display: flex;
      flex-wrap: wrap;
      gap: 1rem;
      margin: 2rem 0 0;
      justify-content: center;
    }
    .guarantee-item {
      background: rgba(255,255,245,0.08);
      border-radius: 100px;
      padding: 8px 22px;
      font-size: 0.9rem;
      font-weight: 500;
      backdrop-filter: blur(4px);
    }
    .guarantee-item i {
      margin-right: 8px;
      color: #ffd966;
    }

    /* specialization pills */
    .spec-section {
      margin: 2.5rem 0 1rem;
    }
    .spec-pills {
      display: flex;
      flex-wrap: wrap;
      gap: 10px;
      margin-top: 16px;
    }
    .pill {
      background: white;
      border-radius: 40px;
      padding: 6px 18px;
      font-size: 0.8rem;
      font-weight: 600;
      color: #0a2b3c;
      box-shadow: 0 2px 6px rgba(0,0,0,0.03);
      transition: all 0.2s;
      border: 1px solid #e2edf2;
    }
    .pill i {
      margin-right: 6px;
      font-size: 0.75rem;
      color: #1e6f5c;
    }

    /* live order board (real-time simulation) */
    .dashboard {
      margin-top: 2.5rem;
      margin-bottom: 3rem;
    }
    .card {
      background: white;
      border-radius: 32px;
      box-shadow: 0 20px 35px -12px rgba(0, 0, 0, 0.08);
      padding: 1.8rem;
      transition: all 0.2s ease;
      border: 1px solid rgba(0,0,0,0.03);
    }
    .order-header {
      display: flex;
      justify-content: space-between;
      align-items: baseline;
      flex-wrap: wrap;
      margin-bottom: 1.5rem;
    }
    .live-badge {
      background: #e53e3e10;
      color: #c53030;
      font-weight: 700;
      border-radius: 100px;
      padding: 6px 14px;
      font-size: 0.8rem;
      letter-spacing: 0.3px;
    }
    .live-badge i {
      color: #e53e3e;
      animation: pulse 1.2s infinite;
    }
    @keyframes pulse {
      0% { opacity: 0.4; }
      100% { opacity: 1; }
    }
    .order-table-wrapper {
      overflow-x: auto;
    }
    .order-table {
      width: 100%;
      border-collapse: collapse;
      font-size: 0.9rem;
    }
    .order-table th {
      text-align: left;
      padding: 16px 8px 12px 0;
      font-weight: 700;
      color: #2c5282;
      border-bottom: 2px solid #e9ecef;
    }
    .order-table td {
      padding: 14px 8px 14px 0;
      border-bottom: 1px solid #edf2f7;
      font-weight: 500;
    }
    .status-badge {
      background: #c6f6d5;
      color: #276749;
      padding: 4px 12px;
      border-radius: 40px;
      font-size: 0.7rem;
      font-weight: 700;
      display: inline-block;
    }
    .status-progress {
      background: #feebc8;
      color: #9c4221;
    }
    .urgency {
      font-weight: 800;
      color: #dd6b20;
    }

    .stats-row {
      display: flex;
      flex-wrap: wrap;
      gap: 1.8rem;
      margin: 2rem 0;
      justify-content: space-between;
    }
    .stat-card {
      flex: 1;
      background: linear-gradient(145deg, #ffffff, #f8fafc);
      border-radius: 28px;
      padding: 1.2rem;
      text-align: center;
      box-shadow: 0 5px 12px rgba(0,0,0,0.02);
      border: 1px solid #eef2f6;
    }
    .stat-number {
      font-size: 2.4rem;
      font-weight: 800;
      color: #1a4c6e;
    }

    .cta-whatsapp {
      background: linear-gradient(105deg, #075e54 0%, #128c7e 100%);
      border-radius: 28px;
      padding: 2rem;
      color: white;
      display: flex;
      flex-wrap: wrap;
      justify-content: space-between;
      align-items: center;
      margin: 2rem 0;
    }
    .btn-wa {
      background: white;
      color: #075e54;
      padding: 14px 32px;
      border-radius: 50px;
      font-weight: 800;
      text-decoration: none;
      display: inline-flex;
      align-items: center;
      gap: 12px;
      transition: 0.2s;
      font-size: 1.1rem;
    }
    .btn-wa:hover {
      transform: scale(1.02);
      box-shadow: 0 12px 18px -8px rgba(0,0,0,0.2);
    }

    footer {
      text-align: center;
      padding: 2rem 0;
      font-size: 0.8rem;
      color: #4a627a;
      border-top: 1px solid #e2edf2;
      margin-top: 2rem;
    }

    @media (max-width: 780px) {
      .container { padding: 0 20px; }
      .brand h1 { font-size: 2rem; }
      .hero-content { flex-direction: column; align-items: start; }
    }
    .chart-container {
      max-width: 320px;
      margin: 0 auto;
    }
    canvas { max-height: 140px; width: auto; }
  </style>
</head>
<body>
<div class="bg-noise"></div>

<main>
  <div class="hero">
    <div class="container">
      <div class="hero-content">
        <div class="brand">
          <h1><i class="fas fa-graduation-cap" style="color: #ffd966;"></i> James Karanja</h1>
          <p>PhD-level consortium — elite academic architects</p>
          <div class="expert-badge" style="margin-top: 12px;">
            <i class="fas fa-user-graduate"></i> A group of qualified experts specialised in various fields
          </div>
        </div>
        <div class="expert-badge">
          <i class="fas fa-globe"></i> 24/7 Global Elite Support
        </div>
      </div>
      <div class="guarantee-grid">
        <div class="guarantee-item"><i class="fas fa-star"></i> Excellent Grades</div>
        <div class="guarantee-item"><i class="fas fa-clock"></i> Timely Delivery</div>
        <div class="guarantee-item"><i class="fas fa-wallet"></i> Affordable</div>
        <div class="guarantee-item"><i class="fas fa-file-alt"></i> 0% Plagiarism</div>
        <div class="guarantee-item"><i class="fas fa-headset"></i> 24/7 Availability</div>
      </div>
    </div>
  </div>

  <div class="container">
    <!-- specialization row -->
    <div class="spec-section">
      <h3 style="font-weight: 700; font-size: 1.6rem;"><i class="fas fa-microscope"></i> Our Specialization &nbsp;🔥</h3>
      <div class="spec-pills">
        <span class="pill"><i class="fas fa-laptop"></i> Online exams</span>
        <span class="pill"><i class="fas fa-book-open"></i> Coursework</span>
        <span class="pill"><i class="fas fa-pen-fancy"></i> Essays</span>
        <span class="pill"><i class="fas fa-scroll"></i> Thesis</span>
        <span class="pill"><i class="fas fa-comments"></i> Discussions</span>
        <span class="pill"><i class="fas fa-chart-line"></i> Research summary</span>
        <span class="pill"><i class="fas fa-project-diagram"></i> Projects</span>
        <span class="pill"><i class="fas fa-file-powerpoint"></i> Dissertation</span>
        <span class="pill"><i class="fas fa-chart-bar"></i> Data analysis</span>
        <span class="pill"><i class="fas fa-chart-pie"></i> Accounting,Finance</span>
        <span class="pill"><i class="fas fa-chart-line"></i> Economics</span>
        <span class="pill"><i class="fas fa-users"></i> Management</span>
        <span class="pill"><i class="fas fa-brain"></i> Psychology</span>
        <span class="pill"><i class="fas fa-dna"></i> Biology, Chemistry</span>
        <span class="pill"><i class="fab fa-python"></i> R, Java, Python, C++, SPSS, Matlab</span>
        <span class="pill"><i class="fas fa-microchip"></i> Computer Science</span>
        <span class="pill"><i class="fas fa-cogs"></i> Engineering</span>
        <span class="pill"><i class="fas fa-chart-simple"></i> Statistics</span>
        <span class="pill"><i class="fas fa-infinity"></i> AND ALL OTHER ASSIGNMENTS ✍️</span>
      </div>
    </div>

    <!-- LIVE ORDERS DASHBOARD (real-time simulation) -->
    <div class="dashboard">
      <div class="card">
        <div class="order-header">
          <h2><i class="fas fa-charging-station" style="color:#2b6a9f;"></i> Real‑Time Order Stream</h2>
          <div class="live-badge"><i class="fas fa-circle"></i> LIVE FEED · UPDATES EVERY 12 SEC</div>
        </div>
        <div class="order-table-wrapper">
          <table class="order-table" id="orderTable">
            <thead>
              <tr><th>Order ID</th><th>Subject / Field</th><th>Task Type</th><th>Deadline</th><th>Status</th></tr>
            </thead>
            <tbody id="orderTableBody">
              <!-- dynamic rows injected via JS -->
            </tbody>
          </table>
        </div>
        <div style="margin-top: 20px; font-size: 0.75rem; text-align: right; color: #5a6e85;">
          <i class="fas fa-sync-alt"></i> Refreshing in real-time — PhD experts assigned instantly
        </div>
      </div>
    </div>

    <!-- statistics + live metrics -->
    <div class="stats-row">
      <div class="stat-card">
        <i class="fas fa-tasks fa-2x" style="color:#2c7a4a;"></i>
        <div class="stat-number" id="activeOrdersCount">0</div>
        <div>Active Orders (now)</div>
      </div>
      <div class="stat-card">
        <i class="fas fa-check-circle fa-2x" style="color:#2b6a9f;"></i>
        <div class="stat-number" id="completedTodayCount">0</div>
        <div>Completed Today</div>
      </div>
      <div class="stat-card">
        <i class="fas fa-chalkboard-user fa-2x"></i>
        <div class="stat-number">47</div>
        <div>PhD Experts Online</div>
      </div>
      <div class="stat-card">
        <div class="chart-container"><canvas id="specializationChart" width="200" height="120"></canvas></div>
        <div>Field distribution (live)</div>
      </div>
    </div>

    <!-- CTA with WhatsApp integration -->
    <div class="cta-whatsapp">
      <div>
        <h3 style="font-size: 1.6rem;"><i class="fab fa-whatsapp"></i> Secure Your Top Grade Now</h3>
        <p style="opacity: 0.9;">Direct consultation with Dr. Karanja's team — instant response, premium support.</p>
        <div style="margin-top: 10px;"><i class="fas fa-trophy"></i> 100% confidentiality & money-back guarantee</div>
      </div>
      <div>
        <a href="https://wa.me/qr/4PKBWS2XMM4VF1" target="_blank" class="btn-wa"><i class="fab fa-whatsapp fa-lg"></i> WhatsApp Individual</a>
        <a href="https://chat.whatsapp.com/K4pGzREL0Io5XN9v5McvbQ" target="_blank" class="btn-wa" style="background:#25D366; color:white; margin-left: 12px;"><i class="fab fa-whatsapp"></i> Join Group</a>
      </div>
    </div>

    <!-- Additional context: mission and value -->
    <div style="background:#ffffff; border-radius: 32px; padding: 1.8rem; margin: 2rem 0; border:1px solid #eef2f8;">
      <div style="display: flex; flex-wrap: wrap; gap: 2rem; justify-content: space-between;">
        <div style="flex:1">
          <i class="fas fa-quote-left fa-2x" style="color:#2c7a4a;"></i>
          <h3>James Karanja Assignment Help</h3>
          <p style="margin-top: 12px;">A convergence of world-class scholars, data scientists, and academic editors. We deliver bespoke solutions for undergraduate, master's, and doctoral projects. Our real-time order tracking ensures transparency and unmatched precision — every dissertation, coding project, or statistical analysis is cross-validated by domain specialists.</p>
          <p><strong>🔥 Excellence is not an option, it's our baseline.</strong></p>
        </div>
        <div style="flex:1">
          <i class="fas fa-chart-line fa-2x"></i>
          <h4>Why top 1% choose us</h4>
          <ul style="margin-top: 10px; list-style: none;">
            <li><i class="fas fa-check-circle text-green"></i> PhD native-level writers (STEM, Humanities, Business)</li>
            <li><i class="fas fa-code"></i> R, Python, Java, C++ & SPSS experts — real-time debugging</li>
            <li><i class="fas fa-chart-simple"></i> Turnitin reports & AI-free guarantee</li>
            <li><i class="fas fa-clock"></i> 6-hour emergency delivery option</li>
          </ul>
        </div>
      </div>
    </div>
    <footer>
      <p>© 2025 James Karanja Academic Elite — PhD-led consortium. All assignments handled with integrity. 📚 24/7 support | GDPR Compliant</p>
      <p><i class="fas fa-envelope"></i> support@jameskaranja-expert.com | <i class="fas fa-phone-alt"></i> +1 (877) 900-EDU</p>
    </footer>
  </div>
</main>

<script>
  // ----------------------------------------------
  // REAL-TIME ORDER SIMULATION - PHD-LEVEL DYNAMICS
  // ----------------------------------------------
  const subjects = [
    "Machine Learning", "Corporate Finance", "Cognitive Psych", "Organic Chem", "Macroeconomics", 
    "Java Algorithms", "Structural Eng", "Data Science", "Dissertation Lit Review", "Accounting Audit",
    "SPSS Analysis", "Python AI", "C++ OOP", "Biostatistics", "Thesis Proposal", "Nursing Ethics",
    "Business Strategy", "International Law", "R Programming", "Matlab Simulation"
  ];
  const taskTypes = ["Essay", "Coursework", "Online Exam", "Thesis", "Project", "Dissertation", "Data Analysis", "Coding Project", "Research Summary"];
  const statuses = ["In Progress", "Under Review", "Drafting", "Expert Assigned"];
  const deadlines = ["2 hours", "6 hours", "12 hours", "24 hours", "3 days", "1 week"];

  let activeOrders = [];
  let completedCounter = 0;
  let intervalId = null;
  let chart = null;
  let fieldDistribution = {};

  // Helper to generate random order
  function generateRandomOrder(id) {
    const subject = subjects[Math.floor(Math.random() * subjects.length)];
    const task = taskTypes[Math.floor(Math.random() * taskTypes.length)];
    const deadline = deadlines[Math.floor(Math.random() * deadlines.length)];
    const status = statuses[Math.floor(Math.random() * statuses.length)];
    const urgencyFlag = (deadline === "2 hours" || deadline === "6 hours") ? " 🔥" : "";
    return {
      id: id,
      subject: subject,
      taskType: task,
      deadline: deadline + urgencyFlag,
      status: status,
      rawStatus: status,
      rawDeadline: deadline
    };
  }

  // update UI table + stats
  function renderOrders() {
    const tbody = document.getElementById('orderTableBody');
    if (!tbody) return;
    tbody.innerHTML = '';
    for (let i = 0; i < activeOrders.length; i++) {
      const o = activeOrders[i];
      const row = tbody.insertRow();
      row.insertCell(0).innerHTML = `<strong>#JK-${o.id}</strong>`;
      row.insertCell(1).innerHTML = `<i class="fas fa-flask"></i> ${o.subject}`;
      row.insertCell(2).innerHTML = o.taskType;
      row.insertCell(3).innerHTML = `<span class="urgency">${o.deadline}</span>`;
      let statusClass = "status-badge";
      if (o.rawStatus === "Expert Assigned") statusClass = "status-badge";
      else if (o.rawStatus === "In Progress") statusClass = "status-badge";
      else statusClass = "status-badge status-progress";
      row.insertCell(4).innerHTML = `<span class="${statusClass}">${o.status}</span>`;
    }
    document.getElementById('activeOrdersCount').innerText = activeOrders.length;
    document.getElementById('completedTodayCount').innerText = completedCounter;
    updateChartData();
  }

  // complete random old orders (simulate finishing)
  function completeRandomOrders() {
    if (activeOrders.length === 0) return;
    const completeIndex = Math.floor(Math.random() * activeOrders.length);
    const completedOrder = activeOrders[completeIndex];
    activeOrders.splice(completeIndex, 1);
    completedCounter++;
    // also update field distribution for removed order
    let fieldKey = extractFieldCategory(completedOrder.subject);
    if (fieldDistribution[fieldKey] && fieldDistribution[fieldKey] > 0) fieldDistribution[fieldKey]--;
    renderOrders();
  }

  function extractFieldCategory(subject) {
    if (subject.includes("Machine Learning") || subject.includes("Python") || subject.includes("Java") || subject.includes("C++") || subject.includes("Algorithms") || subject.includes("Data Science") || subject.includes("R Programming") || subject.includes("Matlab")) return "Programming & CS";
    if (subject.includes("Finance") || subject.includes("Accounting") || subject.includes("Economics")) return "Finance/Economics";
    if (subject.includes("Psych") || subject.includes("Nursing") || subject.includes("Ethics")) return "Social Sciences";
    if (subject.includes("Chem") || subject.includes("Biology") || subject.includes("Biostatistics")) return "Natural Sciences";
    if (subject.includes("Engineering") || subject.includes("Structural")) return "Engineering";
    if (subject.includes("Thesis") || subject.includes("Dissertation") || subject.includes("Proposal")) return "Advanced Research";
    return "Business & Management";
  }

  function addNewOrder() {
    const newId = Date.now() % 100000;
    const newOrder = generateRandomOrder(newId);
    activeOrders.unshift(newOrder);
    if (activeOrders.length > 14) activeOrders.pop(); // keep board fresh and not overflow
    let fieldCat = extractFieldCategory(newOrder.subject);
    if (!fieldDistribution[fieldCat]) fieldDistribution[fieldCat] = 0;
    fieldDistribution[fieldCat]++;
    renderOrders();
  }

  // periodic update: add order every 8-12 seconds, complete random order every 9-14 sec
  function startLiveSimulation() {
    addNewOrder(); // initial
    setInterval(() => {
      addNewOrder();
    }, 9500);
    setInterval(() => {
      if (activeOrders.length > 0) completeRandomOrders();
      else {
        // if no orders, add one to keep alive
        addNewOrder();
      }
    }, 11000);
    // also update statuses occasionally (enhance realism)
    setInterval(() => {
      if (activeOrders.length) {
        let rand = Math.floor(Math.random() * activeOrders.length);
        let possibleStatus = statuses;
        let newStatus = possibleStatus[Math.floor(Math.random() * possibleStatus.length)];
        activeOrders[rand].status = newStatus;
        activeOrders[rand].rawStatus = newStatus;
        renderOrders();
      }
    }, 18000);
  }

  // initialize chart.js showing realtime field distribution
  function initChart() {
    const ctx = document.getElementById('specializationChart').getContext('2d');
    chart = new Chart(ctx, {
      type: 'doughnut',
      data: {
        labels: ['Programming & CS', 'Finance/Economics', 'Social Sciences', 'Natural Sciences', 'Engineering', 'Advanced Research', 'Business & Mgmt'],
        datasets: [{
          data: [4, 3, 2, 2, 1, 3, 2],
          backgroundColor: ['#2c7a4a', '#2b6a9f', '#9c4221', '#dd6b20', '#6b46c1', '#b7791f', '#319795'],
          borderWidth: 0,
        }]
      },
      options: { responsive: true, maintainAspectRatio: true, plugins: { legend: { position: 'bottom', labels: { boxWidth: 10, font: { size: 9 } } } } }
    });
  }
  
  function updateChartData() {
    if (!chart) return;
    const labelsOrder = ['Programming & CS', 'Finance/Economics', 'Social Sciences', 'Natural Sciences', 'Engineering', 'Advanced Research', 'Business & Mgmt'];
    let newData = labelsOrder.map(lbl => fieldDistribution[lbl] || 0);
    // if all zero show dummy realistic distribution
    if (newData.every(v => v === 0)) {
      newData = [4, 3, 2, 1, 2, 3, 2];
    }
    chart.data.datasets[0].data = newData;
    chart.update();
  }

  // seed initial orders with PhD-level realistic context
  function seedInitialOrders() {
    const initialOrdersData = [
      { id: 4401, subject: "Deep Learning Thesis", taskType: "Dissertation", deadline: "48 hours", status: "Expert Assigned" },
      { id: 4402, subject: "Corporate Tax Accounting", taskType: "Coursework", deadline: "12 hours", status: "In Progress" },
      { id: 4403, subject: "R Programming for Epidemiology", taskType: "Data Analysis", deadline: "6 hours 🔥", status: "Drafting" },
      { id: 4404, subject: "Java Microservices Project", taskType: "Coding Project", deadline: "24 hours", status: "Under Review" },
      { id: 4405, subject: "Macroeconomic Policy", taskType: "Essay", deadline: "3 days", status: "Expert Assigned" },
      { id: 4406, subject: "Structural Steel Design", taskType: "Engineering", deadline: "2 hours 🔥", status: "In Progress" },
      { id: 4407, subject: "Dissertation Chapter 3", taskType: "Dissertation", deadline: "1 week", status: "Drafting" },
    ];
    for (let ord of initialOrdersData) {
      activeOrders.push({
        id: ord.id, subject: ord.subject, taskType: ord.taskType, deadline: ord.deadline, status: ord.status, rawStatus: ord.status, rawDeadline: ord.deadline
      });
      let cat = extractFieldCategory(ord.subject);
      fieldDistribution[cat] = (fieldDistribution[cat] || 0) + 1;
    }
    completedCounter = 12; // today completed (simulation realistic)
    renderOrders();
  }

  // initial load
  seedInitialOrders();
  initChart();
  startLiveSimulation();

  // additional live clock for extra professionalism
  function updateLiveTimestamp() {
    let timeDiv = document.createElement('div');
    // subtle effect: add dynamic timestamp inside order-header (optional)
    const headerDiv = document.querySelector('.order-header');
    if (headerDiv && !document.getElementById('liveClock')) {
      let span = document.createElement('span');
      span.id = 'liveClock';
      span.style.fontSize = '0.7rem';
      span.style.fontWeight = '400';
      span.style.background = '#eef2fa';
      span.style.padding = '4px 10px';
      span.style.borderRadius = '40px';
      headerDiv.appendChild(span);
    }
    if (document.getElementById('liveClock')) {
      const now = new Date();
      document.getElementById('liveClock').innerHTML = `<i class="far fa-clock"></i> ${now.toLocaleTimeString()} UTC`;
    }
  }
  setInterval(updateLiveTimestamp, 1000);
  updateLiveTimestamp();

  // ensure that statistics and chart are interactive
  window.addEventListener('resize', () => { if(chart) chart.resize(); });
</script>
</body>
</html>
