<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>나만의 웹사이트</title>
    <style>
        #map {
            position: relative;
            width: 50%;
            height: auto;
        }
        .popup {
            position: absolute;
            background-color: white;
            border: 1px solid black;
            padding: 10px;
            display: none;
        }
    </style>
</head>
<body>
    <h1>안녕하세요! 나만의 웹사이트에 오신 것을 환영합니다.</h1>
    <div id="map-container">
        <img id="map" src="map_1.png" alt="Mall Map">
        <div id="popup" class="popup">이 위치로 AGV 호출</div>
    </div>
    <p>이곳에서 저의 프로젝트와 블로그를 확인할 수 있습니다.</p>

    <script>
        const map = document.getElementById('map');
        const popup = document.getElementById('popup');

        map.addEventListener('click', function(event) {
            const rect = map.getBoundingClientRect();
            const x = event.clientX - rect.left;
            const y = event.clientY - rect.top;

            popup.style.left = `${x}px`;
            popup.style.top = `${y}px`;
            popup.style.display = 'block';
        });

        map.addEventListener('mouseleave', function() {
            popup.style.display = 'none';
        });
    </script>
</body>
</html>
