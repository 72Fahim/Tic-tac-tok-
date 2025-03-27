# Tic-tac-tok-<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Pepe Coin Mining</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
    <style>
        body {
            background-color: #121212;
            color: #ffffff;
            font-family: 'Arial', sans-serif;
            margin: 0;
            padding: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            flex-direction: column;
        }

        .container {
            text-align: center;
            background-color: #1e1e1e;
            padding: 20px;
            border-radius: 15px;
            box-shadow: 0 0 20px rgba(0, 0, 0, 0.5);
            max-width: 400px;
            width: 100%;
            margin-bottom: 60px;
        }

        .hidden {
            display: none;
        }

        header {
            position: relative;
        }

        header h1 {
            color: #4caf50;
            font-size: 2rem;
            margin-bottom: 10px;
        }

        header p {
            color: #ccc;
            font-size: 0.9rem;
            margin: 5px 0;
        }

        .header-telegram-link {
            margin-top: 10px;
            padding: 8px;
            background-color: #2c2c2c;
            border-radius: 5px;
            text-align: center;
        }

        .header-telegram-link a {
            color: #4caf50;
            text-decoration: none;
            font-weight: bold;
        }

        .header-telegram-link a:hover {
            text-decoration: underline;
        }

        .wallet {
            background-color: #2c2c2c;
            padding: 15px;
            border-radius: 10px;
            margin-bottom: 20px;
        }

        .wallet h2 {
            font-size: 1.2rem;
            margin-bottom: 10px;
        }

        .wallet p {
            font-size: 1.5rem;
            font-weight: bold;
            margin-bottom: 15px;
        }

        .wallet button {
            background-color: #4caf50;
            color: white;
            border: none;
            padding: 10px 20px;
            border-radius: 5px;
            cursor: pointer;
            font-size: 1rem;
        }

        .wallet button:hover {
            background-color: #45a049;
        }

        .mining-area {
            position: relative;
            height: 200px;
            border: 2px dashed #4caf50;
            border-radius: 10px;
            overflow: hidden;
        }

        .frogs-container {
            position: relative;
            width: 100%;
            height: 100%;
        }

        .frog {
            position: absolute;
            font-size: 2rem;
            animation: swim 5s infinite;
            cursor: pointer;
            user-select: none;
        }

        @keyframes swim {
            0% { transform: translate(0, 0); }
            25% { transform: translate(20px, 20px); }
            50% { transform: translate(-20px, 40px); }
            75% { transform: translate(20px, 60px); }
            100% { transform: translate(0, 0); }
        }

        #withdrawForm input {
            padding: 10px;
            margin: 5px 0;
            border: 1px solid #ccc;
            border-radius: 5px;
            width: 100%;
            background-color: #2c2c2c;
            color: #ffffff;
        }

        #withdrawForm button {
            width: 100%;
            margin-top: 10px;
            background-color: #4caf50;
            color: white;
            border: none;
            padding: 10px 20px;
            border-radius: 5px;
            cursor: pointer;
            font-size: 1rem;
        }

        .highlighted-line {
            background-color: #ffebee;
            padding: 10px;
            border-radius: 5px;
            margin: 10px 0;
            text-align: center;
        }

        .danger-text {
            color: #d32f2f;
            font-weight: bold;
        }

        .withdraw-animation {
            position: relative;
            margin-top: 20px;
        }

        .frog-eating .frog {
            font-size: 3rem;
            animation: grow 2s infinite ease-in-out;
        }

        @keyframes grow {
            0% { transform: scale(1); }
            50% { transform: scale(1.2); }
            100% { transform: scale(1); }
        }

        .binary-counter {
            margin-top: 15px;
            padding: 8px;
            background-color: #2c2c2c;
            border-radius: 5px;
            font-family: monospace;
            color: #4caf50;
            font-size: 0.9rem;
            text-align: center;
        }

        .withdraw-history {
            margin-top: 20px;
            background-color: #2c2c2c;
            padding: 15px;
            border-radius: 10px;
        }

        .withdraw-history h3 {
            margin-bottom: 10px;
        }

        .scrollable-history {
            max-height: 150px;
            overflow-y: auto;
            border: 1px solid #ccc;
            border-radius: 5px;
            padding: 10px;
        }

        .withdraw-history ul {
            list-style-type: none;
            padding: 0;
        }

        .withdraw-history li {
            margin: 5px 0;
            font-size: 0.9rem;
            color: #ccc;
        }

        #tasksSection {
            margin-top: 20px;
        }

        .task-container {
            display: flex;
            justify-content: center;
            align-items: center;
            flex-direction: column;
        }

        #taskButton {
            background-color: #4caf50;
            color: white;
            border: none;
            padding: 15px 30px;
            border-radius: 10px;
            cursor: pointer;
            font-size: 1rem;
            display: flex;
            align-items: center;
            gap: 10px;
            animation: pulse 1.5s infinite;
        }

        #taskButton:disabled {
            background-color: #cccccc;
            cursor: not-allowed;
            animation: none;
        }

        .task-icon {
            font-size: 1.5rem;
            animation: spin 2s infinite linear;
        }

        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }

        @keyframes pulse {
            0% { transform: scale(1); }
            50% { transform: scale(1.1); }
            100% { transform: scale(1); }
        }

        .auto-task-toggle {
            margin-top: 20px;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .switch {
            position: relative;
            display: inline-block;
            width: 60px;
            height: 34px;
        }

        .switch input {
            opacity: 0;
            width: 0;
            height: 0;
        }

        .slider {
            position: absolute;
            cursor: pointer;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background-color: #ccc;
            transition: 0.4s;
            border-radius: 34px;
        }

        .slider:before {
            position: absolute;
            content: "";
            height: 26px;
            width: 26px;
            left: 4px;
            bottom: 4px;
            background-color: white;
            transition: 0.4s;
            border-radius: 50%;
        }

        input:checked + .slider {
            background-color: #4caf50;
        }

        input:checked + .slider:before {
            transform: translateX(26px);
        }

        .mini-window {
            margin-top: 20px;
            width: 100%;
            height: 300px;
            border: 2px solid #4caf50;
            border-radius: 10px;
            overflow: hidden;
            position: relative;
        }

        #adFrame {
            width: 100%;
            height: 100%;
            border: none;
        }

        #countdown {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            font-size: 3rem;
            color: #4caf50;
            z-index: 10;
            display: none;
        }

        .footer {
            position: fixed;
            bottom: 0;
            width: 100%;
            background-color: #1e1e1e;
            padding: 10px 0;
            text-align: center;
        }

        .footer-navigation {
            display: flex;
            justify-content: space-around;
        }

        .footer-nav-button {
            background-color: transparent;
            color: white;
            border: none;
            padding: 10px 15px;
            border-radius: 5px;
            cursor: pointer;
            font-size: 0.9rem;
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 5px;
        }

        .footer-nav-button.active {
            background-color: #4caf50;
        }

        .footer-nav-button:hover {
            background-color: #4caf50;
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <h1>Pepe Coin Mining 🐸</h1>
            <p>Mine Pepe Coins and earn rewards!</p>
            <p>Your Unique ID: <span id="userId"></span></p>
            <div class="header-telegram-link hidden" id="telegramLinkContainer">
                <p>Complete withdrawal on Telegram: <a href="#" id="telegramLink" target="_blank">Click Here</a></p>
            </div>
        </header>

        <section id="miningSection" class="content-section">
            <div class="wallet">
                <h2>Your Balance</h2>
                <p id="pepeBalance">0.00 PEPE</p>
                <button id="claimButton">Claim</button>
            </div>
            <div class="mining-area">
                <div class="frogs-container" id="frogsContainer"></div>
            </div>
        </section>

        <section id="withdrawSection" class="content-section hidden">
            <h2>Withdraw PEPE</h2>
            <p>Withdraw your mined Pepe Coins to your wallet.</p>
            <div class="highlighted-line">
                <p>⚠️ A <span class="danger-text">4% transaction fee</span> will be deducted from your balance.</p>
            </div>
            <form id="withdrawForm">
                <input type="text" id="walletAddress" placeholder="Enter your wallet address" required>
                <input type="number" id="withdrawAmount" placeholder="Enter amount (Min: 10000)" required>
                <button type="submit" id="withdrawButton">Withdraw</button>
            </form>
            <div class="withdraw-animation">
                <div class="frog-eating" id="frogEating">
                    <div class="frog">🐸</div>
                </div>
            </div>
            <div class="rules">
                <h3>Withdrawal Rules:</h3>
                <ul>
                    <li>Minimum withdrawal: 10000 PEPE</li>
                    <li>Maximum withdrawal: Unlimited ∞</li>
                    <li>Withdrawals are processed within 24 hours.</li>
                </ul>
                <div id="binaryCounter" class="binary-counter">0</div>
            </div>
            <div class="withdraw-history">
                <h3>Withdrawal History</h3>
                <div class="scrollable-history">
                    <ul id="withdrawHistory"></ul>
                </div>
            </div>
        </section>

        <section id="tasksSection" class="content-section hidden">
            <h2>Tasks</h2>
            <p>Complete tasks to earn more PEPE.</p>
            <div class="task-container">
                <button id="taskButton">
                    <span class="task-icon">🐸</span>
                    <span class="task-text">Start Task</span>
                </button>
                <div class="auto-task-toggle">
                    <label class="switch">
                        <input type="checkbox" id="autoTaskToggle">
                        <span class="slider round"></span>
                    </label>
                    <p>Auto Task: <span id="autoTaskStatus">Off</span></p>
                </div>
                <div class="note">
                    <p style="color: red;">Click on the "Re-human Verification" button if required.</p>
                </div>
            </div>
            <div class="mini-window">
                <iframe id="adFrame" src="about:blank"></iframe>
                <div id="countdown">14</div>
            </div>
        </section>

        <section id="helpSection" class="content-section hidden">
            <h2>Help & Support</h2>
            <p>If you have any questions or need assistance, please check the following information:</p>
            <div class="help-content">
                <h3>Frequently Asked Questions (FAQ)</h3>
                <ul>
                    <li><strong>How do I start mining?</strong> - Click on the frogs in the mining section to earn PEPE coins.</li>
                    <li><strong>How do I withdraw my coins?</strong> - Go to the withdraw section and enter your wallet address and amount.</li>
                    <li><strong>What is the minimum withdrawal amount?</strong> - The minimum withdrawal amount is 10000 PEPE.</li>
                </ul>
                <h3>Contact Support</h3>
                <p>If you need further assistance, please contact us at <a href="mailto:Pepemining@gmail.com">Pepemining@gmail.com</a>.</p>
            </div>
        </section>
    </div>

    <footer class="footer">
        <nav class="footer-navigation">
            <button class="footer-nav-button active" data-section="mining">
                <i class="fas fa-frog"></i>
                <span>Mining</span>
            </button>
            <button class="footer-nav-button" data-section="withdraw">
                <i class="fas fa-wallet"></i>
                <span>Withdraw</span>
            </button>
            <button class="footer-nav-button" data-section="tasks">
                <i class="fas fa-tasks"></i>
                <span>Tasks</span>
            </button>
            <button class="footer-nav-button" data-section="help">
                <i class="fas fa-question-circle"></i>
                <span>Help</span>
            </button>
        </nav>
    </footer>

    <script>
        // Initialize all variables from local storage
        let pepeBalance = parseFloat(localStorage.getItem('pepeBalance')) || 0;
        let miningSpeed = parseFloat(localStorage.getItem('miningSpeed')) || 1.00;
        let totalWithdrawn = parseFloat(localStorage.getItem('totalWithdrawn')) || 0;
        let withdrawHistory = JSON.parse(localStorage.getItem('withdrawHistory')) || [];
        let taskClickCount = parseInt(localStorage.getItem('taskClickCount')) || 0;
        let lastMiningTime = parseInt(localStorage.getItem('lastMiningTime')) || Date.now();
        let isTaskRunning = false;
        let autoTaskInterval = null;

        // Generate or retrieve user ID
        let userId = localStorage.getItem('userId');
        if (!userId) {
            userId = Math.floor(100000 + Math.random() * 900000);
            localStorage.setItem('userId', userId);
        }
        document.getElementById('userId').innerText = userId;

        // Calculate offline mining
        const calculateOfflineMining = () => {
            const now = Date.now();
            const timeDiff = now - lastMiningTime;
            const minutesPassed = Math.floor(timeDiff / (1000 * 60));
            const minedAmount = minutesPassed * (miningSpeed / 60);
            
            if (minutesPassed > 0) {
                pepeBalance += minedAmount;
                lastMiningTime = now;
                saveToLocalStorage();
            }
        };

        // Initialize the app
        const initApp = () => {
            calculateOfflineMining();
            updateUI();
            startBackgroundMining();
        };

        // Update UI with current values
        const updateUI = () => {
            document.getElementById('pepeBalance').innerText = pepeBalance.toFixed(2) + ' PEPE';
            document.getElementById('binaryCounter').textContent = taskClickCount.toString(2);
            updateWithdrawHistory();
        };

        // Save all data to local storage
        const saveToLocalStorage = () => {
            localStorage.setItem('pepeBalance', pepeBalance);
            localStorage.setItem('miningSpeed', miningSpeed);
            localStorage.setItem('totalWithdrawn', totalWithdrawn);
            localStorage.setItem('withdrawHistory', JSON.stringify(withdrawHistory));
            localStorage.setItem('taskClickCount', taskClickCount);
            localStorage.setItem('lastMiningTime', lastMiningTime);
        };

        // Background mining service
        const startBackgroundMining = () => {
            setInterval(() => {
                pepeBalance += miningSpeed / 60;
                lastMiningTime = Date.now();
                saveToLocalStorage();
                updateUI();
            }, 1000);
        };

        // Update withdrawal history display
        const updateWithdrawHistory = () => {
            const historyList = document.getElementById('withdrawHistory');
            historyList.innerHTML = '';
            withdrawHistory.forEach(item => {
                const li = document.createElement('li');
                li.innerText = `${item.amount} PEPE to ${item.address} at ${item.timestamp}`;
                historyList.appendChild(li);
            });
        };

        // Navigation Buttons
        const navButtons = document.querySelectorAll('.footer-nav-button');
        const sections = {
            mining: document.getElementById('miningSection'),
            withdraw: document.getElementById('withdrawSection'),
            tasks: document.getElementById('tasksSection'),
            help: document.getElementById('helpSection')
        };

        navButtons.forEach(button => {
            button.addEventListener('click', () => {
                // Turn off auto task if enabled when navigating
                if (document.getElementById('autoTaskToggle').checked) {
                    document.getElementById('autoTaskToggle').checked = false;
                    document.getElementById('autoTaskStatus').innerText = 'Off';
                    clearInterval(autoTaskInterval);
                }

                navButtons.forEach(btn => btn.classList.remove('active'));
                button.classList.add('active');
                Object.values(sections).forEach(section => section.classList.add('hidden'));
                sections[button.dataset.section].classList.remove('hidden');
            });
        });

        // Claim Button
        document.getElementById('claimButton').addEventListener('click', () => {
            navButtons.forEach(btn => btn.classList.remove('active'));
            document.querySelector('[data-section="withdraw"]').classList.add('active');
            Object.values(sections).forEach(section => section.classList.add('hidden'));
            document.getElementById('withdrawSection').classList.remove('hidden');
        });

        // Withdraw Form
        document.getElementById('withdrawForm').addEventListener('submit', (e) => {
            e.preventDefault();
            const walletAddress = document.getElementById('walletAddress').value;
            const amount = parseFloat(document.getElementById('withdrawAmount').value);

            if (amount < 10000) {
                alert('Minimum withdrawal amount is 10000 PEPE!');
            } else if (amount > pepeBalance) {
                alert('Insufficient balance!');
            } else {
                const transactionFee = amount * 0.04;
                const finalAmount = amount - transactionFee;
                pepeBalance -= amount;
                totalWithdrawn += finalAmount;
                
                // Add to withdrawal history
                const historyItem = {
                    amount: finalAmount.toFixed(2),
                    address: walletAddress,
                    timestamp: new Date().toLocaleString()
                };
                withdrawHistory.push(historyItem);
                
                saveToLocalStorage();
                updateUI();
                
                alert(`Withdrawn ${finalAmount.toFixed(2)} PEPE to ${walletAddress} (4% fee deducted)`);

                // Prepare Telegram message
                const binaryCount = taskClickCount.toString(2);
                const telegramMessage = `Pepe Coin Withdrawal:\n\n1. Wallet: ${walletAddress}\n2. Amount: ${finalAmount.toFixed(2)} PEPE\n3. ${binaryCount}`;
                
                // Update Telegram link in header
                const telegramLink = document.getElementById('telegramLink');
                telegramLink.href = `https://t.me/Pepewithdrawa?text=${encodeURIComponent(telegramMessage)}`;
                document.getElementById('telegramLinkContainer').classList.remove('hidden');

                // Animation
                const frog = document.querySelector('.frog-eating .frog');
                frog.style.animation = 'grow 2s infinite ease-in-out';
                setTimeout(() => frog.style.animation = 'none', 5000);
            }
        });

        // Task Button
        document.getElementById('taskButton').addEventListener('click', () => {
            if (!isTaskRunning) {
                taskClickCount++;
                saveToLocalStorage();
                updateUI();
                startTask();
            }
        });

        // Auto Task
        document.getElementById('autoTaskToggle').addEventListener('change', (e) => {
            const autoTaskStatus = document.getElementById('autoTaskStatus');
            if (e.target.checked) {
                autoTaskStatus.innerText = 'On';
                if (!isTaskRunning) {
                    taskClickCount++;
                    saveToLocalStorage();
                    updateUI();
                    startTask();
                }
                autoTaskInterval = setInterval(() => {
                    if (!isTaskRunning) {
                        taskClickCount++;
                        saveToLocalStorage();
                        updateUI();
                        startTask();
                    }
                }, 15000);
            } else {
                autoTaskStatus.innerText = 'Off';
                clearInterval(autoTaskInterval);
            }
        });

        // Start Task
        function startTask() {
            isTaskRunning = true;
            const taskButton = document.getElementById('taskButton');
            taskButton.disabled = true;
            
            const adFrame = document.getElementById('adFrame');
            const countdownElement = document.getElementById('countdown');

            adFrame.src = "https://www.effectiveratecpm.com/q6jk1v8am7?key=fbdd76c7a8eadf9c6877d1f24a52e0e1";
            let timeLeft = 14;
            countdownElement.style.display = 'block';
            countdownElement.innerText = timeLeft;

            const countdownInterval = setInterval(() => {
                timeLeft--;
                countdownElement.innerText = timeLeft;

                if (timeLeft <= 0) {
                    clearInterval(countdownInterval);
                    isTaskRunning = false;
                    pepeBalance += 100;
                    lastMiningTime = Date.now();
                    saveToLocalStorage();
                    updateUI();
                    countdownElement.style.display = 'none';
                    taskButton.disabled = false;
                    
                    if (document.getElementById('autoTaskToggle').checked) {
                        setTimeout(() => {
                            taskClickCount++;
                            saveToLocalStorage();
                            updateUI();
                            startTask();
                        }, 1000);
                    }
                }
            }, 1000);
        }

        // Generate frogs
        function generateFrogs() {
            const frogsContainer = document.getElementById('frogsContainer');
            for (let i = 0; i < 25; i++) {
                const frog = document.createElement('div');
                frog.classList.add('frog');
                frog.innerText = '🐸';
                frog.style.left = `${Math.random() * 90}%`;
                frog.style.top = `${Math.random() * 90}%`;
                frog.style.animationDuration = `${Math.random() * 3 + 2}s`;
                frog.addEventListener('click', () => {
                    moveFrog(frog);
                    pepeBalance += 0.1;
                    lastMiningTime = Date.now();
                    saveToLocalStorage();
                    updateUI();
                });
                frogsContainer.appendChild(frog);
            }
        }

        function moveFrog(frog) {
            frog.style.animation = 'none';
            frog.offsetHeight;
            frog.style.left = `${Math.random() * 90}%`;
            frog.style.top = `${Math.random() * 90}%`;
            frog.style.animation = 'swim 2s infinite';
        }

        // Initialize the application
        window.addEventListener('load', () => {
            generateFrogs();
            initApp();
        });

        // Save data before window closes
        window.addEventListener('beforeunload', () => {
            saveToLocalStorage();
        });
    </script>
</body>
</html>
