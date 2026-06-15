<!DOCTYPE html>
<html lang="ja">
<head>
    <meta charset="UTF-8">
    <title>北海道旅行カウントダウン</title>
    <style>
        body { font-family: sans-serif; text-align: center; background: #e0f7fa; }
        .grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(80px, 1fr)); gap: 10px; max-width: 600px; margin: 20px auto; }
        .day { padding: 20px; background: #00796b; color: white; border-radius: 8px; cursor: pointer; transition: 0.3s; }
        .day.locked { background: #b0bec5; cursor: not-allowed; }
        .day.open { background: #ff9800; }
    </style>
</head>
<body>
    <h1>✈️ 北海道旅行まであと何日？</h1>
    <div class="grid" id="calendar"></div>

    <script>
        const startDate = new Date('2026/06/15'); // 今日
        const targetDate = new Date('2026/07/08'); // 旅行日
        const calendar = document.getElementById('calendar');
        
        // 日数を計算
        const diffDays = Math.ceil((targetDate - startDate) / (1000 * 60 * 60 * 24));

        for (let i = 1; i <= diffDays; i++) {
            const div = document.createElement('div');
            div.className = 'day locked';
            div.innerText = `${i}日目`;
            
            // i日目が過ぎていれば開ける（簡易判定）
            div.onclick = () => {
                div.classList.remove('locked');
                div.classList.add('open');
                div.innerText = `準備中！`;
            };
            calendar.appendChild(div);
        }
    </script>
</body>
</html>
