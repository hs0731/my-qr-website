<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>AGV 호출 시스템</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background-color: #f4f4f4;
            text-align: center;
        }
        h1 {
            color: #333;
        }
        .map-container {
            position: relative;
            width: 100%;
            max-width: 600px;
            margin: 0 auto;
            border: 2px solid #ccc;
        }
        .map {
            width: 100%;
            height: auto;
        }
        .popup {
            position: absolute;
            background-color: white;
            border: 2px solid #007bff;
            border-radius: 8px;
            padding: 10px;
            width: 200px;
            box-shadow: 0px 4px 8px rgba(0,0,0,0.1);
            display: none;
            z-index: 10;
        }
        .popup h3 {
            margin: 0;
            font-size: 1.1rem;
            color: #007bff;
        }
        .popup button {
            margin-top: 10px;
            padding: 10px;
            background-color: #007bff;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }
        .popup button:hover {
            background-color: #0056b3;
        }
        /* 지도에 파란 핀을 표시 */
        .pin {
            position: absolute;
            width: 30px;
            height: 30px;
            background-image: url('pin.png'); /* 파란 핀 이미지 */
            background-size: cover;
            transform: translate(-50%, -100%);
        }
    </style>
</head>
<body>
    <h1>AGV 호출 시스템</h1>

    <!-- 지도 이미지 -->
    <div class="map-container">
        <img src="map.png" alt="지도" class="map" id="map" onclick="showPopup(event)">
        
        <!-- 클릭 시 나오는 팝업 -->
        <div class="popup" id="popup">
            <h3>이 위치로 AGV 호출</h3>
            <p>선택한 위치로 AGV를 호출합니다.</p>
            <button onclick="callAGV()">AGV 호출</button>
        </div>
        
        <!-- 파란 핀 -->
        <div class="pin" id="pin"></div>
    </div>

    <script>
        const popup = document.getElementById('popup');
        const pin = document.getElementById('pin');

        function showPopup(event) {
            // 지도 클릭 위치 계산
            const map = document.getElementById('map');
            const rect = map.getBoundingClientRect();
            const x = event.clientX - rect.left;
            const y = event.clientY - rect.top;

            // 팝업 위치 설정
            popup.style.left = `${x}px`;
            popup.style.top = `${y}px`;
            popup.style.display = 'block';

            // 파란 핀 위치 설정
            pin.style.left = `${x}px`;
            pin.style.top = `${y}px`;
            pin.style.display = 'block';
        }

        function callAGV() {
            alert("AGV가 호출되었습니다!");
            popup.style.display = 'none';
            pin.style.display = 'none';
        }
    </script>
</body>
</html>
