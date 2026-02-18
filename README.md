<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Currency Converter</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
        }
        
        body {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            padding: 20px;
        }
        
        .container {
            width: 100%;
            max-width: 500px;
            background: rgba(255, 255, 255, 0.95);
            border-radius: 24px;
            box-shadow: 0 20px 60px rgba(0, 0, 0, 0.3);
            overflow: hidden;
            animation: fadeIn 0.6s ease-out;
        }
        
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        header {
            background: linear-gradient(to right, #4f46e5, #7c3aed);
            color: white;
            padding: 30px 20px;
            text-align: center;
            position: relative;
        }
        
        h1 {
            font-size: 2.5rem;
            margin-bottom: 10px;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 15px;
        }
        
        h1 span {
            font-size: 3rem;
        }
        
        .subtitle {
            font-size: 1rem;
            opacity: 0.9;
            font-weight: 300;
        }
        
        main {
            padding: 30px;
        }
        
        .converter-box {
            background: white;
            border-radius: 16px;
            padding: 25px;
            box-shadow: 0 8px 30px rgba(0, 0, 0, 0.08);
            margin-bottom: 25px;
        }
        
        .amount-input {
            margin-bottom: 25px;
        }
        
        label {
            display: block;
            margin-bottom: 8px;
            color: #4f46e5;
            font-weight: 600;
            font-size: 0.95rem;
        }
        
        .input-group {
            position: relative;
            display: flex;
        }
        
        .currency-symbol {
            background: #f3f4f6;
            padding: 15px 20px;
            border: 2px solid #e5e7eb;
            border-right: none;
            border-radius: 12px 0 0 12px;
            font-size: 1.2rem;
            font-weight: bold;
            color: #374151;
        }
        
        input {
            flex: 1;
            padding: 15px;
            border: 2px solid #e5e7eb;
            border-radius: 0 12px 12px 0;
            font-size: 1.5rem;
            font-weight: 600;
            color: #1f2937;
            outline: none;
            transition: border-color 0.3s;
        }
        
        input:focus {
            border-color: #4f46e5;
        }
        
        .currencies {
            display: grid;
            grid-template-columns: 1fr auto 1fr;
            gap: 20px;
            align-items: center;
            margin-bottom: 25px;
        }
        
        select {
            width: 100%;
            padding: 15px;
            border: 2px solid #e5e7eb;
            border-radius: 12px;
            font-size: 1.1rem;
            font-weight: 500;
            color: #1f2937;
            background: white;
            cursor: pointer;
            outline: none;
            transition: border-color 0.3s;
            appearance: none;
            background-image: url("data:image/svg+xml;charset=UTF-8,%3csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 24 24' fill='none' stroke='currentColor' stroke-width='2' stroke-linecap='round' stroke-linejoin='round'%3e%3cpolyline points='6 9 12 15 18 9'%3e%3c/polyline%3e%3c/svg%3e");
            background-repeat: no-repeat;
            background-position: right 15px center;
            background-size: 16px;
            padding-right: 45px;
        }
        
        select:focus {
            border-color: #4f46e5;
        }
        
        .swap-btn {
            background: #f3f4f6;
            border: 2px solid #e5e7eb;
            width: 50px;
            height: 50px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            transition: all 0.3s;
            margin-top: 10px;
        }
        
        .swap-btn:hover {
            background: #4f46e5;
            border-color: #4f46e5;
            color: white;
            transform: rotate(180deg);
        }
        
        .convert-btn {
            width: 100%;
            padding: 18px;
            background: linear-gradient(to right, #4f46e5, #7c3aed);
            color: white;
            border: none;
            border-radius: 12px;
            font-size: 1.2rem;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 10px;
        }
        
        .convert-btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 10px 20px rgba(79, 70, 229, 0.3);
        }
        
        .convert-btn:active {
            transform: translateY(0);
        }
        
        .result-box {
            background: linear-gradient(to right, #10b981, #059669);
            color: white;
            padding: 25px;
            border-radius: 16px;
            text-align: center;
            animation: slideUp 0.5s ease-out;
        }
        
        @keyframes slideUp {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        .result-label {
            font-size: 1rem;
            opacity: 0.9;
            margin-bottom: 10px;
        }
        
        .result-amount {
            font-size: 3rem;
            font-weight: 700;
            margin-bottom: 10px;
        }
        
        .result-details {
            font-size: 1rem;
            opacity: 0.9;
        }
        
        .exchange-rate {
            display: flex;
            justify-content: center;
            align-items: center;
            gap: 10px;
            margin-top: 15px;
            font-size: 1.1rem;
        }
        
        footer {
            text-align: center;
            padding: 20px;
            color: rgba(255, 255, 255, 0.8);
            font-size: 0.9rem;
        }
        
        @media (max-width: 600px) {
            .container {
                border-radius: 20px;
            }
            
            h1 {
                font-size: 2rem;
            }
            
            h1 span {
                font-size: 2.5rem;
            }
            
            .currencies {
                grid-template-columns: 1fr;
                grid-template-rows: 1fr auto 1fr;
            }
            
            .swap-btn {
                margin: 0 auto;
                transform: rotate(90deg);
            }
            
            .swap-btn:hover {
                transform: rotate(270deg);
            }
            
            .result-amount {
                font-size: 2.5rem;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <h1><span>💰</span> Currency Converter</h1>
            <p class="subtitle">Real-time currency conversion with accurate rates</p>
        </header>
        
        <main>
            <div class="converter-box">
                <div class="amount-input">
                    <label>Amount to Convert</label>
                    <div class="input-group">
                        <div class="currency-symbol" id="fromSymbol">$</div>
                        <input type="number" id="amountInput" value="100" min="0" step="0.01" placeholder="Enter amount">
                    </div>
                </div>
                
                <div class="currencies">
                    <div class="from-currency">
                        <label>From Currency</label>
                        <select id="fromCurrency">
                            <!-- Currencies will be populated by JavaScript -->
                        </select>
                    </div>
                    
                    <div class="swap-container">
                        <div class="swap-btn" id="swapBtn">
                            <span>⇄</span>
                        </div>
                    </div>
                    
                    <div class="to-currency">
                        <label>To Currency</label>
                        <select id="toCurrency">
                            <!-- Currencies will be populated by JavaScript -->
                        </select>
                    </div>
                </div>
                
                <button class="convert-btn" id="convertBtn">
                    <span>🔄</span> Convert Currency
                </button>
            </div>
            
            <div class="result-box" id="resultBox" style="display: none;">
                <div class="result-label">Converted Amount</div>
                <div class="result-amount" id="resultAmount">0.00</div>
                <div class="result-details" id="resultDetails"></div>
                <div class="exchange-rate" id="exchangeRate"></div>
            </div>
        </main>
        
        <footer>
            <p>Currency rates are updated regularly | 💱 Offline Demo Version</p>
        </footer>
    </div>

    <script>
        // Currency data with exchange rates (base: USD)
        const currencies = [
            { code: "USD", name: "US Dollar", symbol: "$", rate: 1.00, emoji: "🇺🇸" },
            { code: "EUR", name: "Euro", symbol: "€", rate: 0.92, emoji: "🇪🇺" },
            { code: "GBP", name: "British Pound", symbol: "£", rate: 0.79, emoji: "🇬🇧" },
            { code: "JPY", name: "Japanese Yen", symbol: "¥", rate: 149.50, emoji: "🇯🇵" },
            { code: "CAD", name: "Canadian Dollar", symbol: "CA$", rate: 1.37, emoji: "🇨🇦" },
            { code: "AUD", name: "Australian Dollar", symbol: "A$", rate: 1.53, emoji: "🇦🇺" },
            { code: "CHF", name: "Swiss Franc", symbol: "CHF", rate: 0.88, emoji: "🇨🇭" },
            { code: "CNY", name: "Chinese Yuan", symbol: "¥", rate: 7.19, emoji: "🇨🇳" },
            { code: "INR", name: "Indian Rupee", symbol: "₹", rate: 83.15, emoji: "🇮🇳" },
            { code: "BRL", name: "Brazilian Real", symbol: "R$", rate: 5.05, emoji: "🇧🇷" },
            { code: "MXN", name: "Mexican Peso", symbol: "MX$", rate: 17.25, emoji: "🇲🇽" },
            { code: "KRW", name: "South Korean Won", symbol: "₩", rate: 1342.00, emoji: "🇰🇷" }
        ];

        // DOM Elements
        const fromCurrencySelect = document.getElementById('fromCurrency');
        const toCurrencySelect = document.getElementById('toCurrency');
        const amountInput = document.getElementById('amountInput');
        const convertBtn = document.getElementById('convertBtn');
        const swapBtn = document.getElementById('swapBtn');
        const resultBox = document.getElementById('resultBox');
        const resultAmount = document.getElementById('resultAmount');
        const resultDetails = document.getElementById('resultDetails');
        const exchangeRate = document.getElementById('exchangeRate');
        const fromSymbol = document.getElementById('fromSymbol');

        // Populate currency dropdowns
        function populateCurrencies() {
            currencies.forEach(currency => {
                const option1 = document.createElement('option');
                option1.value = currency.code;
                option1.textContent = `${currency.emoji} ${currency.code} - ${currency.name}`;
                
                const option2 = option1.cloneNode(true);
                
                fromCurrencySelect.appendChild(option1);
                toCurrencySelect.appendChild(option2);
            });
            
            // Set default values
            fromCurrencySelect.value = "USD";
            toCurrencySelect.value = "EUR";
            updateCurrencySymbol();
        }

        // Update currency symbol in the input field
        function updateCurrencySymbol() {
            const fromCurrency = fromCurrencySelect.value;
            const currency = currencies.find(c => c.code === fromCurrency);
            fromSymbol.textContent = currency.symbol;
        }

        // Convert currency
        function convertCurrency() {
            const amount = parseFloat(amountInput.value);
            if (isNaN(amount) || amount < 0) {
                alert("Please enter a valid amount");
                return;
            }
            
            const fromCurrency = fromCurrencySelect.value;
            const toCurrency = toCurrencySelect.value;
            
            const fromCurrencyData = currencies.find(c => c.code === fromCurrency);
            const toCurrencyData = currencies.find(c => c.code === toCurrency);
            
            // Convert via USD as base
            const amountInUSD = amount / fromCurrencyData.rate;
            const convertedAmount = amountInUSD * toCurrencyData.rate;
            
            // Format the result
            const formattedResult = convertedAmount.toLocaleString('en-US', {
                minimumFractionDigits: 2,
                maximumFractionDigits: 2
            });
            
            const formattedOriginal = amount.toLocaleString('en-US', {
                minimumFractionDigits: 2,
                maximumFractionDigits: 2
            });
            
            // Calculate exchange rate
            const rate = toCurrencyData.rate / fromCurrencyData.rate;
            
            // Update UI
            resultAmount.textContent = `${toCurrencyData.symbol} ${formattedResult}`;
            resultDetails.textContent = `${fromCurrencyData.symbol} ${formattedOriginal} ${fromCurrency} = ${toCurrencyData.symbol} ${formattedResult} ${toCurrency}`;
            exchangeRate.innerHTML = `<span>💱</span> 1 ${fromCurrency} = ${rate.toFixed(4)} ${toCurrency}`;
            
            // Show result with animation
            resultBox.style.display = 'block';
        }

        // Swap currencies
        function swapCurrencies() {
            const fromValue = fromCurrencySelect.value;
            const toValue = toCurrencySelect.value;
            
            fromCurrencySelect.value = toValue;
            toCurrencySelect.value = fromValue;
            
            updateCurrencySymbol();
            convertCurrency();
        }

        // Initialize the app
        function init() {
            populateCurrencies();
            convertCurrency(); // Show initial conversion
            
            // Event listeners
            convertBtn.addEventListener('click', convertCurrency);
            swapBtn.addEventListener('click', swapCurrencies);
            fromCurrencySelect.addEventListener('change', () => {
                updateCurrencySymbol();
                convertCurrency();
            });
            toCurrencySelect.addEventListener('change', convertCurrency);
            amountInput.addEventListener('input', convertCurrency);
            
            // Add some animation to the convert button on page load
            setTimeout(() => {
                convertBtn.style.transform = 'scale(1.05)';
                setTimeout(() => {
                    convertBtn.style.transform = 'scale(1)';
                }, 200);
            }, 500);
        }

        // Start the app when DOM is loaded
        document.addEventListener('DOMContentLoaded', init);
    </script>
</body>

</html>
