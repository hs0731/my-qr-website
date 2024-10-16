<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>인터랙티브 지도</title>
    <style>
        .map-container {
            position: relative;
            width: 100%;
            max-width: 800px;
            margin: auto;
        }
        .popup {
            position: absolute;
            background-color: white;
            border: 1px solid black;
            padding: 10px;
            display: none;
        }
        .info {
            margin-top: 20px;
            font-size: 18px;
        }
    </style>
</head>
<body>
    <h1>인터랙티브 지도</h1>
    <div class="map-container">
        <svg id="map" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 800 600">
            <!-- SVG 내용 -->
            <rect x="100" y="100" width="200" height="100" fill="lightblue" id="C402"/>
            <text x="150" y="150" font-size="20">C402</text>
            <!-- 다른 구역들도 추가 -->
        </svg>
    </div>
    <div id="info" class="info">여기에 장소 설명이 나타납니다.</div>

    <script>
        const map = document.getElementById('map');
        const info = document.getElementById('info');

        map.addEventListener('click', function(event) {
            const target = event.target;
            if (target.tagName === 'rect') {
                const id = target.id;
                info.textContent = `${id}에 대한 설명입니다.`;
            }
        });
    </script>
</body>
</html>
