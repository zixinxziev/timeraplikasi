<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Timer App</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            height: 100vh;
            margin: 0;
            background-color: #f5f5f5;
        }
        
        .timer-container {
            background-color: white;
            border-radius: 10px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
            padding: 30px;
            text-align: center;
            width: 300px;
        }
        
        .timer-display {
            font-size: 48px;
            margin: 20px 0;
            color: #333;
        }
        
        .timer-controls {
            display: flex;
            justify-content: center;
            gap: 10px;
        }
        
        button {
            padding: 10px 20px;
            font-size: 16px;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            transition: background-color 0.3s;
        }
        
        #startBtn {
            background-color: #4CAF50;
            color: white;
        }
        
        #startBtn:hover {
            background-color: #45a049;
        }
        
        #pauseBtn {
            background-color: #f39c12;
            color: white;
        }
        
        #pauseBtn:hover {
            background-color: #e67e22;
        }
        
        #resetBtn {
            background-color: #e74c3c;
            color: white;
        }
        
        #resetBtn:hover {
            background-color: #c0392b;
        }
        
        input {
            padding: 10px;
            font-size: 16px;
            width: 60px;
            text-align: center;
            border: 1px solid #ddd;
            border-radius: 5px;
        }
        
        .time-input {
            display: flex;
            gap: 10px;
            justify-content: center;
            margin-bottom: 20px;
        }
        
        .time-input div {
            display: flex;
            flex-direction: column;
            align-items: center;
        }
        
        .time-input span {
            font-size: 12px;
            color: #777;
            margin-top: 5px;
        }
    </style>
</head>
<body>
    <div class="timer-container">
        <h1>Timer App</h1>
        
        <div class="time-input">
            <div>
                <input type="number" id="hours" min="0" max="23" value="0">
                <span>Jam</span>
            </div>
            <div>
                <input type="number" id="minutes" min="0" max="59" value="0">
                <span>Menit</span>
            </div>
            <div>
                <input type="number" id="seconds" min="0" max="59" value="10">
                <span>Detik</span>
            </div>
        </div>
        
        <div class="timer-display" id="display">00:00:10</div>
        
        <div class="timer-controls">
            <button id="startBtn">Mulai</button>
            <button id="pauseBtn">Jeda</button>
            <button id="resetBtn">Reset</button>
        </div>
    </div>

    <script>
        let timer;
        let totalSeconds = 10;
        let isRunning = false;
        
        const hoursInput = document.getElementById('hours');
        const minutesInput = document.getElementById('minutes');
        const secondsInput = document.getElementById('seconds');
        const display = document.getElementById('display');
        const startBtn = document.getElementById('startBtn');
        const pauseBtn = document.getElementById('pauseBtn');
        const resetBtn = document.getElementById('resetBtn');
        
        // Update timer display
        function updateDisplay() {
            const hours = Math.floor(totalSeconds / 3600);
            const minutes = Math.floor((totalSeconds % 3600) / 60);
            const seconds = totalSeconds % 60;
            
            display.textContent = 
                `${hours.toString().padStart(2, '0')}:${minutes.toString().padStart(2, '0')}:${seconds.toString().padStart(2, '0')}`;
        }
        
        // Start timer
        function startTimer() {
            if (isRunning) return;
            
            isRunning = true;
            timer = setInterval(() => {
                if (totalSeconds > 0) {
                    totalSeconds--;
                    updateDisplay();
                } else {
                    clearInterval(timer);
                    isRunning = false;
                    alert('Waktu habis!');
                }
            }, 1000);
        }
        
        // Pause timer
        function pauseTimer() {
            clearInterval(timer);
            isRunning = false;
        }
        
        // Reset timer
        function resetTimer() {
            pauseTimer();
            totalSeconds = parseInt(hoursInput.value) * 3600 + 
                          parseInt(minutesInput.value) * 60 + 
                          parseInt(secondsInput.value);
            updateDisplay();
        }
        
        // Event listeners
        startBtn.addEventListener('click', startTimer);
        pauseBtn.addEventListener('click', pauseTimer);
        resetBtn.addEventListener('click', resetTimer);
        
        // Input validation
        [hoursInput, minutesInput, secondsInput].forEach(input => {
            input.addEventListener('change', function() {
                let value = parseInt(this.value) || 0;
                
                if (this.id === 'hours') {
                    this.value = Math.max(0, Math.min(23, value));
                } else {
                    this.value = Math.max(0, Math.min(59, value));
                }
                
                if (!isRunning) {
                    resetTimer();
                }
            });
        });
        
        // Initialize
        updateDisplay();
    </script>
</body>
</html>
