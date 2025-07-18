<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Josh (Lithap) - Advanced GitHub Profile Animations</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Fira+Code:wght@300;400;500;600;700&display=swap');
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            background: linear-gradient(135deg, #0c0c0c 0%, #1a1a1a 50%, #0c0c0c 100%);
            font-family: 'Fira Code', monospace;
            color: #00ff41;
            overflow-x: hidden;
        }
        
        /* Matrix Rain Effect */
        .matrix-bg {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -1;
            opacity: 0.1;
        }
        
        .matrix-char {
            position: absolute;
            color: #00ff41;
            font-family: 'Fira Code', monospace;
            font-size: 14px;
            animation: matrix-fall linear infinite;
        }
        
        @keyframes matrix-fall {
            0% { transform: translateY(-100vh); opacity: 1; }
            100% { transform: translateY(100vh); opacity: 0; }
        }
        
        /* Terminal Header */
        .terminal-header {
            background: linear-gradient(45deg, #ff6b6b, #4ecdc4, #45b7d1);
            background-size: 400% 400%;
            animation: gradient-shift 3s ease infinite;
            padding: 2rem;
            text-align: center;
            position: relative;
            overflow: hidden;
        }
        
        @keyframes gradient-shift {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }
        
        .terminal-window {
            background: rgba(0, 0, 0, 0.9);
            border-radius: 10px;
            padding: 1rem;
            margin: 2rem auto;
            max-width: 800px;
            border: 2px solid #00ff41;
            box-shadow: 0 0 30px rgba(0, 255, 65, 0.3);
        }
        
        .terminal-bar {
            display: flex;
            align-items: center;
            margin-bottom: 1rem;
            padding-bottom: 0.5rem;
            border-bottom: 1px solid #333;
        }
        
        .terminal-buttons {
            display: flex;
            gap: 0.5rem;
        }
        
        .terminal-button {
            width: 12px;
            height: 12px;
            border-radius: 50%;
        }
        
        .close { background: #ff5f56; }
        .minimize { background: #ffbd2e; }
        .maximize { background: #27ca3f; }
        
        .terminal-title {
            margin-left: 1rem;
            color: #888;
            font-size: 0.9rem;
        }
        
        /* Typing Animation */
        .typing-text {
            font-size: 1.2rem;
            color: #00ff41;
            white-space: nowrap;
            overflow: hidden;
            border-right: 2px solid #00ff41;
            animation: typing 4s steps(40, end), blink-caret 0.75s step-end infinite;
        }
        
        @keyframes typing {
            from { width: 0; }
            to { width: 100%; }
        }
        
        @keyframes blink-caret {
            from, to { border-color: transparent; }
            50% { border-color: #00ff41; }
        }
        
        /* Glitch Effect */
        .glitch {
            position: relative;
            color: #00ff41;
            font-size: 2rem;
            font-weight: bold;
            text-transform: uppercase;
            animation: glitch 2s infinite;
        }
        
        .glitch::before,
        .glitch::after {
            content: attr(data-text);
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
        }
        
        .glitch::before {
            animation: glitch-1 0.5s infinite;
            color: #ff6b6b;
            z-index: -1;
        }
        
        .glitch::after {
            animation: glitch-2 0.5s infinite;
            color: #4ecdc4;
            z-index: -2;
        }
        
        @keyframes glitch {
            0%, 100% { transform: translate(0); }
            20% { transform: translate(-2px, 2px); }
            40% { transform: translate(-2px, -2px); }
            60% { transform: translate(2px, 2px); }
            80% { transform: translate(2px, -2px); }
        }
        
        @keyframes glitch-1 {
            0%, 100% { transform: translate(0); }
            10% { transform: translate(-2px, -2px); }
            20% { transform: translate(2px, 2px); }
            30% { transform: translate(-2px, 2px); }
            40% { transform: translate(2px, -2px); }
        }
        
        @keyframes glitch-2 {
            0%, 100% { transform: translate(0); }
            10% { transform: translate(2px, 2px); }
            20% { transform: translate(-2px, -2px); }
            30% { transform: translate(2px, -2px); }
            40% { transform: translate(-2px, 2px); }
        }
        
        /* Skill Bars */
        .skill-bar {
            background: #333;
            height: 20px;
            border-radius: 10px;
            margin: 0.5rem 0;
            overflow: hidden;
            position: relative;
        }
        
        .skill-progress {
            height: 100%;
            background: linear-gradient(90deg, #ff6b6b, #4ecdc4, #45b7d1);
            border-radius: 10px;
            animation: skill-load 2s ease-in-out;
            position: relative;
        }
        
        .skill-progress::after {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.4), transparent);
            animation: skill-shine 2s infinite;
        }
        
        @keyframes skill-load {
            from { width: 0%; }
        }
        
        @keyframes skill-shine {
            0% { left: -100%; }
            100% { left: 100%; }
        }
        
        /* Floating Elements */
        .floating-element {
            position: absolute;
            animation: float 6s ease-in-out infinite;
        }
        
        @keyframes float {
            0%, 100% { transform: translateY(0px); }
            50% { transform: translateY(-20px); }
        }
        
        /* Neon Glow */
        .neon-text {
            color: #00ff41;
            text-shadow: 
                0 0 5px #00ff41,
                0 0 10px #00ff41,
                0 0 15px #00ff41,
                0 0 20px #00ff41;
            animation: neon-flicker 2s infinite alternate;
        }
        
        @keyframes neon-flicker {
            0%, 100% { opacity: 1; }
            50% { opacity: 0.8; }
        }

        /* Pulse Animation for YouTube Alert */
        @keyframes pulse {
            0% { transform: scale(1); }
            50% { transform: scale(1.05); }
            100% { transform: scale(1); }
        }

        /* Responsive */
        @media (max-width: 768px) {
            .terminal-window {
                margin: 1rem;
                padding: 0.5rem;
            }

            .glitch {
                font-size: 1.5rem;
            }
        }
    </style>
</head>
<body>
    <!-- Matrix Background -->
    <div class="matrix-bg" id="matrix"></div>
    
    <!-- YouTube Alert -->
    <div style="background: #ff0000; padding: 1rem; text-align: center; animation: pulse 2s infinite;">
        <h2 style="color: white; margin: 0; font-size: 1.5rem;">🎬 WATCH THIS! 🎬</h2>
        <a href="https://www.youtube.com/watch?v=pcSlowAhvUk&t=133s" target="_blank" style="color: #ffff00; text-decoration: none; font-weight: bold;">
            ▶️ CLICK HERE FOR EPIC CONTENT! ▶️
        </a>
    </div>

    <!-- Terminal Header -->
    <div class="terminal-header">
        <h1 class="glitch neon-text" data-text="JOSH (LITHAP)">JOSH (LITHAP)</h1>
        <p class="typing-text">T5 Cyber Engineer & L-III Architect</p>
    </div>
    
    <!-- Main Terminal Window -->
    <div class="terminal-window">
        <div class="terminal-bar">
            <div class="terminal-buttons">
                <div class="terminal-button close"></div>
                <div class="terminal-button minimize"></div>
                <div class="terminal-button maximize"></div>
            </div>
            <div class="terminal-title">josh@lithap:~/profile</div>
        </div>
        
        <div class="terminal-content">
            <p>$ whoami</p>
            <p class="neon-text">Josh (Lithap) - T5 Cyber Engineer & L-III Architect</p>
            <br>
            <p>$ cat specializations.txt</p>
            <p>🔧 Kernel Development</p>
            <p>🖥️ UEFI/Firmware Engineering</p>
            <p>🌐 Hypervisor Architecture</p>
            <p>🔒 Quantum-Resistant Cryptography</p>
            <p>🎮 Advanced Game Hacking</p>
            <br>
            <p>$ ./show_skills.sh</p>
            <div style="margin: 1rem 0;">
                <p>Kernel Development</p>
                <div class="skill-bar">
                    <div class="skill-progress" style="width: 95%;"></div>
                </div>
                
                <p>Game Hacking</p>
                <div class="skill-bar">
                    <div class="skill-progress" style="width: 92%;"></div>
                </div>
                
                <p>Security Research</p>
                <div class="skill-bar">
                    <div class="skill-progress" style="width: 98%;"></div>
                </div>
                
                <p>GUI Design</p>
                <div class="skill-bar">
                    <div class="skill-progress" style="width: 96%;"></div>
                </div>
            </div>
            <br>
            <p class="neon-text">$ echo "Building the future of cybersecurity, one exploit at a time"</p>
            <p>Building the future of cybersecurity, one exploit at a time</p>
            <br>
            <p>$ █</p>
        </div>
    </div>
    
    <script>
        // Matrix Rain Effect
        function createMatrixRain() {
            const matrix = document.getElementById('matrix');
            const chars = '01アイウエオカキクケコサシスセソタチツテトナニヌネノハヒフヘホマミムメモヤユヨラリルレロワヲン';
            
            for (let i = 0; i < 50; i++) {
                const char = document.createElement('div');
                char.className = 'matrix-char';
                char.textContent = chars[Math.floor(Math.random() * chars.length)];
                char.style.left = Math.random() * 100 + '%';
                char.style.animationDuration = (Math.random() * 3 + 2) + 's';
                char.style.animationDelay = Math.random() * 2 + 's';
                matrix.appendChild(char);
            }
        }
        
        // Initialize matrix rain
        createMatrixRain();
        
        // Refresh matrix characters periodically
        setInterval(() => {
            const chars = document.querySelectorAll('.matrix-char');
            chars.forEach(char => {
                if (Math.random() < 0.1) {
                    const newChars = '01アイウエオカキクケコサシスセソタチツテトナニヌネノハヒフヘホマミムメモヤユヨラリルレロワヲン';
                    char.textContent = newChars[Math.floor(Math.random() * newChars.length)];
                }
            });
        }, 100);
    </script>
</body>
</html>
