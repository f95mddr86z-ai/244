<!DOCTYPE html>
<html lang="zh-TW">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>Vibe Counter</title>

    <meta name="apple-mobile-web-app-capable" content="yes">
    <meta name="apple-mobile-web-app-status-bar-style" content="black-translucent">
    <meta name="apple-mobile-web-app-title" content="VibeApp">
    
    <link rel="manifest" href="manifest.json">

    <style>
        :root {
            --primary: #6366f1;
            --bg: #0f172a;
        }
        body {
            margin: 0;
            padding: 0;
            font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
            background-color: var(--bg);
            color: white;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            height: 100vh;
            overflow: hidden;
            /* 防止手機上長按選取文字 */
            user-select: none; 
            -webkit-user-select: none;
        }
        .card {
            background: rgba(255, 255, 255, 0.05);
            padding: 2rem;
            border-radius: 24px;
            text-align: center;
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.1);
            width: 80%;
        }
        h1 { font-weight: 300; margin-bottom: 0.5rem; }
        #count { font-size: 5rem; font-weight: 800; margin: 1rem 0; color: var(--primary); }
        button {
            background: var(--primary);
            border: none;
            color: white;
            padding: 1rem 2rem;
            font-size: 1.2rem;
            border-radius: 16px;
            cursor: pointer;
            transition: transform 0.1s;
            width: 100%;
        }
        button:active { transform: scale(0.95); background: #4f46e5; }
    </style>
</head>
<body>

    <div class="card">
        <h1>Current Vibe</h1>
        <div id="count">0</div>
        <button onclick="addVibe()">增加 Vibe 能量</button>
    </div>

    <script>
        let vibes = 0;
        function addVibe() {
            vibes++;
            document.getElementById('count').innerText = vibes;
            // 加上震動回饋（安卓支援較好，iOS 需原生 App 權限）
            if (navigator.vibrate) navigator.vibrate(50);
        }
    </script>
</body>
</html>

