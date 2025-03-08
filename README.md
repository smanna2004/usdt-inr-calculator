<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>USDT & INR Converter</title>
    <script src="https://cdn.tailwindcss.com"></script>
</head>
<body class="bg-gradient-to-r from-blue-400 to-purple-600 flex items-center justify-center min-h-screen">
    <div class="bg-gradient-to-br from-white to-gray-200 p-8 rounded-xl shadow-2xl w-full max-w-md">
        <h2 class="text-2xl font-bold text-center mb-6 text-gray-800">USDT & INR Converter</h2>
        
        <div class="mb-5">
            <h3 class="text-lg font-semibold text-center text-gray-700">Enter USDT Amount</h3>
            <input type="number" id="usdtAmount" class="w-full p-3 border rounded-lg text-center text-2xl font-bold mt-2 bg-gray-100" placeholder="Enter USDT">
        </div>
        
        <div class="mb-5">
            <h3 class="text-lg font-semibold text-center text-gray-700">Enter INR Amount</h3>
            <input type="number" id="inrAmount" class="w-full p-3 border rounded-lg text-center text-2xl font-bold mt-2 bg-gray-100" placeholder="Enter INR">
        </div>
        
        <button onclick="calculateExchangeRate()" class="w-full bg-blue-600 hover:bg-blue-700 text-white p-3 rounded-lg mt-5 transition">Calculate Exchange Rate</button>
        
        <div class="mt-5">
            <h3 class="text-lg font-semibold text-center text-gray-700">Exchange Rate (Editable)</h3>
            <input type="number" id="exchangeRate" class="w-full p-3 border rounded-lg text-center text-2xl font-bold mt-2 bg-gray-100" value="0.00">
        </div>
        
        <div class="mb-5 mt-6">
            <h3 class="text-lg font-semibold text-center text-gray-700">Select Conversion</h3>
            <select id="conversionType" class="w-full p-3 border rounded-lg text-center text-xl font-bold mt-2 bg-gray-100">
                <option value="usdtToInr">USDT to INR</option>
                <option value="inrToUsdt">INR to USDT</option>
            </select>
        </div>
        
        <button onclick="convert()" class="w-full bg-green-500 hover:bg-green-600 text-white p-3 rounded-lg mt-5 transition">Convert</button>
        
        <div class="mt-5">
            <h3 class="text-lg font-semibold text-center text-gray-700">Converted Amount</h3>
            <input type="text" id="convertedAmount" class="w-full p-3 border rounded-lg text-center text-2xl font-bold mt-2 bg-gray-100" readonly value="0.00">
        </div>
    </div>
    
    <script>
        function calculateExchangeRate() {
            let usdt = parseFloat(document.getElementById('usdtAmount').value);
            let inr = parseFloat(document.getElementById('inrAmount').value);
            
            if (isNaN(usdt) || isNaN(inr) || usdt <= 0 || inr <= 0) {
                alert('Please enter valid numbers!');
                return;
            }
            
            let rate = (inr / usdt).toFixed(2);
            document.getElementById('exchangeRate').value = rate;
        }
        
        function convert() {
            let amount = parseFloat(document.getElementById('usdtAmount').value) || parseFloat(document.getElementById('inrAmount').value);
            let rate = parseFloat(document.getElementById('exchangeRate').value);
            let conversionType = document.getElementById('conversionType').value;
            
            if (isNaN(amount) || isNaN(rate) || rate <= 0) {
                alert('Please enter valid numbers!');
                return;
            }
            
            let convertedAmount;
            if (conversionType === "usdtToInr") {
                convertedAmount = (amount * rate).toFixed(2);
                document.getElementById('convertedAmount').value = `₹${convertedAmount}`;
            } else {
                convertedAmount = (amount / rate).toFixed(6);
                document.getElementById('convertedAmount').value = `${convertedAmount} USDT`;
            }
        }
    </script>
</body>
</html>
