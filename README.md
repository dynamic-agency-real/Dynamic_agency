<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Dynamics - Premium Social Services</title>
    <style>
        :root {
            --primary-red: #ff0000;
            --success-green: #28a745;
            --dark-bg: #0a0a0a;
            --card-bg: #161616;
        }

        body {
            margin: 0;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: var(--dark-bg);
            color: white;
            text-align: center;
        }

        /* 1. Intro Animation */
        #intro-overlay {
            position: fixed;
            top: 0; left: 0;
            width: 100%; height: 100%;
            background: black;
            display: flex;
            justify-content: center;
            align-items: center;
            z-index: 9999;
            animation: fadeOut 0.8s forwards 4s;
        }

        .dynamics-text {
            color: var(--primary-red);
            font-size: clamp(3rem, 10vw, 5rem);
            font-weight: 900;
            text-transform: uppercase;
            letter-spacing: 8px;
            text-shadow: 0 0 20px rgba(255, 0, 0, 0.5);
        }

        @keyframes fadeOut {
            to { opacity: 0; visibility: hidden; }
        }

        /* 2. Main Content */
        .container {
            padding: 20px;
            max-width: 500px;
            margin: auto;
        }

        h1 { color: var(--primary-red); margin-top: 40px; font-weight: 800; }
        .sub-text { color: #888; margin-bottom: 30px; }

        .service-card {
            background: var(--card-bg);
            border-radius: 12px;
            padding: 18px;
            margin: 12px 0;
            display: flex;
            justify-content: space-between;
            align-items: center;
            border: 1px solid #222;
            transition: 0.3s;
        }

        .service-card:hover { border-color: var(--primary-red); }

        .price-info { text-align: left; }
        .price-info strong { display: block; font-size: 1.1rem; }
        .price-info span { color: var(--success-green); font-weight: bold; }
        .badge { font-size: 0.7rem; background: gold; color: black; padding: 2px 6px; border-radius: 4px; margin-left: 5px; }

        .select-btn {
            background-color: var(--success-green);
            color: white;
            border: none;
            padding: 10px 18px;
            border-radius: 6px;
            font-weight: bold;
            cursor: pointer;
        }

        /* 3. Payment & Order Section */
        #order-section {
            display: none;
            background: #111;
            padding: 25px;
            border-radius: 20px;
            margin-top: 30px;
            border: 1px solid var(--success-green);
        }

        input[type="text"] {
            width: 90%;
            padding: 12px;
            margin: 10px 0;
            background: #222;
            border: 1px solid #444;
            color: white;
            border-radius: 8px;
            font-size: 1rem;
        }

        .qr-container {
            background: white;
            padding: 15px;
            border-radius: 10px;
            width: fit-content;
            margin: 20px auto;
        }

        .qr-container img { width: 220px; display: block; }

        .submit-btn {
            background: var(--primary-red);
            width: 100%;
            padding: 15px;
            border: none;
            color: white;
            font-weight: bold;
            font-size: 1.1rem;
            border-radius: 10px;
            cursor: pointer;
            margin-top: 15px;
        }
    </style>
</head>
<body>

    <div id="intro-overlay">
        <div class="dynamics-text">DYNAMICS</div>
    </div>

    <div class="container">
        <h1>DYNAMICS SMM</h1>
        <p class="sub-text">High Quality Instagram Growth Services</p>

        <div id="services">
            <div class="service-card">
                <div class="price-info"><strong>1,000 (1K) Followers</strong><span>$2.30</span></div>
                <button class="select-btn" onclick="openOrder('1K Followers', '$2.30')">Select</button>
            </div>
            <div class="service-card">
                <div class="price-info"><strong>3,000 (3K) Followers</strong><span>$6.90</span></div>
                <button class="select-btn" onclick="openOrder('3K Followers', '$6.90')">Select</button>
            </div>
            <div class="service-card" style="border-color: gold;">
                <div class="price-info"><strong>10,000 (10K) Followers <span class="badge">BEST VALUE</span></strong><span>$22.00</span></div>
                <button class="select-btn" onclick="openOrder('10K Followers', '$22.00')">Select</button>
            </div>
            <div class="service-card" style="border-color: gold;">
                <div class="price-info"><strong>20,000 (20K) Followers <span class="badge">PREMIUM</span></strong><span>$42.00</span></div>
                <button class="select-btn" onclick="openOrder('20K Followers', '$42.00')">Select</button>
            </div>
        </div>

        <div id="order-section">
            <h3 id="selected-title" style="color: var(--success-green);"></h3>
            
            <input type="text" id="insta-username" placeholder="Enter Instagram Username or Link" required>
            
            <p style="font-size: 0.9rem; color: #ccc;">Scan QR with Binance App to Pay:</p>
            <div class="qr-container">
                <img src="https://i.ibb.co/XRs6X9N/binance-qr.png" alt="Binance QR Code">
            </div>
            
            <p style="font-size: 0.8rem;">After payment, click below to send screenshot & details to Admin.</p>
            <button class="submit-btn" onclick="sendOrder()">SUBMIT TO WHATSAPP</button>
        </div>
    </div>

    <script>
        let selectedPkg = "";
        let selectedPrice = "";

        function openOrder(pkg, price) {
            selectedPkg = pkg;
            selectedPrice = price;
            document.getElementById('selected-title').innerText = "Order: " + pkg + " (" + price + ")";
            document.getElementById('order-section').style.display = 'block';
            window.scrollTo({ top: document.body.scrollHeight, behavior: 'smooth' });
        }

        function sendOrder() {
            const username = document.getElementById('insta-username').value;
            const whatsappNumber = "919540775314"; 

            if(!username) {
                alert("Please enter Instagram Username!");
                return;
            }

            const message = `*NEW ORDER - DYNAMICS*\n\n` +
                            `📦 *Package:* ${selectedPkg}\n` +
                            `💰 *Price:* ${selectedPrice}\n` +
                            `👤 *Instagram:* ${username}\n\n` +
                            `I have paid via Binance. Sending screenshot...`;

            const waLink = `https://wa.me/${whatsappNumber}?text=${encodeURIComponent(message)}`;
            window.open(waLink, '_blank');
        }
    </script>
</body>
</html>
# Dynamic_agency
