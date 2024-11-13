<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Data Diri Not Manuality</title>
    <style>
        /* Styling untuk background dan switch day-night */
        body {
            display: flex;
            flex-direction: column;
            align-items: center;
            height: 100vh;
            margin: 0;
            transition: background-color 0.5s;
            background-color: #87CEEB; /* Warna siang */
            color: #333;
            font-family: Arial, sans-serif;
        }

        .switch-container {
            position: fixed;
            top: 10px;
            left: 10px;
            padding: 10px;
            background-color: #e0e0e0;
            border-radius: 25px;
            box-shadow: 0px 4px 10px rgba(0, 0, 0, 0.2);
            z-index: 1000;
        }

        .switch {
            position: relative;
            width: 80px;
            height: 40px;
            border-radius: 20px;
            background-color: #87CEEB;
            cursor: pointer;
            display: flex;
            align-items: center;
            transition: background-color 0.5s;
            padding: 5px;
            overflow: hidden;
        }

        .toggle {
            width: 30px;
            height: 30px;
            border-radius: 50%;
            background-color: yellow;
            box-shadow: 0 0 10px rgba(255, 223, 0, 0.7);
            transition: transform 0.5s, background-color 0.5s, box-shadow 0.5s, clip-path 0.5s;
        }

        .clouds, .stars {
            position: absolute;
            width:

100%;
            height: 100%;
            display: flex;
            justify-content: space-around;
            align-items: center;
            transition: opacity 0.5s;
        }

        .clouds { opacity: 1; }
        .stars { opacity: 0; }

        .switch.night .clouds { opacity: 0; }
        .switch.night .stars { opacity: 1; }

        .cloud {
            width: 18px;
            height: 10px;
            background-color: #FFF;
            border-radius: 50%;
            box-shadow: 8px 0px 0px #FFF, 15px 0px 0px #FFF;
        }

        .star {
            width: 5px;
            height: 5px;
            background-color: #FFF;
            border-radius: 50%;
        }

        .switch.night { background-color: #2C2C54; }

        .switch.night .toggle {
            transform: translateX(40px);
            background-color: #F5F3CE;
            box-shadow: 0 0 10px rgba(255, 255, 255, 0.5);
            clip-path: circle(50% at 70% 50%);
        }

        /* Styling untuk menu navigasi */
        .menu {
            display: flex;
            justify-content: center;
            gap: 20px;
            padding: 10px;
            background-color: #333;
            color: #FFF;
            width: 100%;
        }

        .menu-item {
            cursor: pointer;
            padding: 10px 20px;
            border-radius: 5px;
            transition: background-color 0.3s;
        }

        .menu-item:hover {
            background-color: #555;
        }

        /* Styling untuk konten kalkulator */
        .content {
            display: none;
            margin-top: 20px;
            text-align: center;
        }

        .calculator {
            display: inline-block;
            width: 240px;
            background-color: #333;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0px 4px 10px rgba(0, 0, 0, 0.2);
            color: #FFF;
        }

        .display {
            width: 100%;
            height: 60px;
            background-color: #222;
            color: #FFF;
            font-size: 24px;
            border: none;
            border-radius: 5px;
            padding: 10px;
            text-align: right;
            margin-bottom: 10px;
        }

        .buttons {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 10px;
        }

        .button {
            width: 100%;
            height: 60px;
            background-color: #444;
            color: #FFF;
            font-size: 18px;
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }

        .button.operator {
            background-color: #FF9500;
        }
    </style>
</head>
<body>
    <!-- Switch Day and Night -->
    <div class="switch-container">
        <div class="switch" onclick="toggleTheme()">
            <div class="clouds">
                <div class="cloud"></div>
                <div class="cloud"></div>
            </div>
            <div class="stars">
                <div class="star"></div>
                <div class="star"></div>
                <div class="star"></div>
            </div>
            <div class="toggle"></div>
        </div>
    </div>

    <!-- Menu Navigasi -->
    <div class="menu">
        <div class="menu-item" onclick="showContent('home')">Beranda</div>
        <div class="menu-item" onclick="showContent('other')">Pilihan Lainnya</div>
        <div class="menu-item" onclick="exitApp()">Keluar</div>
    </div>

    <!-- Konten Beranda -->
    <div id="home" class="content" style="display: block;">
        <h1>Selamat Datang di Beranda</h1>
        <h5>Dibawah ini Adalah sebuah Data diri saya.</h5>
        <h2>Nama : Bisa Dilihat Di Nama Media Sosial saya</h2>
        <h2>TTL :Hanya sebuah Tempat San lahir</h2>
        <h3>Ga Penting</h3>
        <h2>alamat : Jangan Tanya </h2>
        <h3>Note:Kecuali Kurir Paket & Stallker</h3>
        <h1>TERIMA KASIH 🙏</h1>
        <h2>semoga harimu senin terus</h2>
        
    </div>

    <!-- Konten Pilihan Lainnya -->
    <div id="other" class="content">
        <h1>Pilihan Lainnya</h2>
        <h4>TIDAK ADA TOMBOL KEMBALI 😁</h4>
        <button onclick="showContent('calculator')"> Kalkulator</button>
    </div>

    <!-- Konten Kalkulator -->
    <div id="calculator" class="content">
        <div class="calculator">
            <input type="text" class="display" id="display" disabled>
            <div class="buttons">
                <button class="button" onclick="clearDisplay()">C</button>
                <button class="button" onclick="appendDisplay('/')">/</button>
                <button class="button" onclick="appendDisplay('*')">*</button>
                <button class="button operator" onclick="appendDisplay('-')">-</button>
                <button class="button" onclick="appendDisplay('7')">7</button>
                <button class="button" onclick="appendDisplay('8')">8</button>
                <button class="button" onclick="appendDisplay('9')">9</button>
                <button class="button operator" onclick="appendDisplay('+')">+</button>
                <button class="button" onclick="appendDisplay('4')">4</button>
                <button class="button" onclick="appendDisplay('5')">5</button>
                <button class="button" onclick="appendDisplay('6')">6</button>
                <button class="button" onclick="calculate()">=</button>
                <button class="button" onclick="appendDisplay('1')">1</button>
                <button class="button" onclick="appendDisplay('2')">2</button>
                <button class="button" onclick="appendDisplay('3')">3</button>
                <button class="button" onclick="appendDisplay('0')">0</button>
            </div>
            <button onclick="showContent('home')">Kembali ke Beranda</button>
        </div>
    </div>

    <script>
        function toggleTheme() {
            const switchElement = document.querySelector('.switch');
            switchElement.classList.toggle('night');
            
            if (switchElement.classList.contains('night')) {
                document.body.style.backgroundColor = '#2C2C54';
            } else {
                document.body.style.backgroundColor = '#87CEEB';
            }
        }

        function clearDisplay() {
            document.getElementById('display').value = '';
        }

        function appendDisplay(value) {
            document.getElementById('display').value += value;
        }

        function calculate() {
            const display = document.getElementById('display');
            try {
                display.value = eval(display.value);
            } catch {
                display.value = 'Error';
            }
        }

        function showContent(id) {
            document.querySelectorAll('.content').forEach(content => content.style.display = 'none');
            document.getElementById(id).style.display = 'block';
        }

        function exitApp() {
            alert("Keluar dari aplikasi.");
            window.close(); // Untuk web mungkin tidak berfungsi di beberapa browser
        }
    </script>
</body>
</html>
