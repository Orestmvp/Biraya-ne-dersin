<!DOCTYPE html>
<html lang="tr">
<head>
  <meta charset="UTF-8">
  <title>Birlikte Bira?</title>
  <style>
    body {
      font-family: 'Segoe UI', sans-serif;
      background: #f0f8ff;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      height: 100vh;
      margin: 0;
      text-align: center;
      overflow: hidden;
      position: relative;
    }

    h1 {
      font-size: 2em;
      margin-bottom: 40px;
      z-index: 1;
    }

    .button {
      padding: 15px 25px;
      font-size: 16px;
      border: none;
      border-radius: 10px;
      cursor: pointer;
      margin: 10px;
      transition: 0.3s ease;
      position: absolute;
      z-index: 1;
    }

    .yes {
      background-color: #007bff;
      color: white;
      left: 40%;
      top: 60%;
    }

    .no {
      background-color: #dc3545;
      color: white;
      left: 55%;
      top: 60%;
    }

    .beer {
      position: absolute;
      font-size: 30px;
      animation: float 2s ease-out forwards;
      pointer-events: none;
    }

    @keyframes float {
      0% {
        opacity: 1;
        transform: translateY(0) scale(1);
      }
      100% {
        opacity: 0;
        transform: translateY(-150px) scale(1.5);
      }
    }
  </style>
</head>
<body onclick="createBeer(event)">
  <h1>Beraber buz gibi bira içmeye ne dersin?</h1>

  <button class="button yes" onclick="event.stopPropagation(); alert('Harika! 🍻 Ne zaman gidiyoruz?')">Evet neden olmasın</button>
  <button class="button no" id="noBtn">Hayır</button>

  <script>
    const noBtn = document.getElementById('noBtn');

    noBtn.addEventListener('mouseover', () => {
      const x = Math.floor(Math.random() * (window.innerWidth - 100));
      const y = Math.floor(Math.random() * (window.innerHeight - 50));
      noBtn.style.left = `${x}px`;
      noBtn.style.top = `${y}px`;
    });

    function createBeer(e) {
      const beer = document.createElement("div");
      beer.className = "beer";
      beer.innerText = "🍺";
      beer.style.left = `${e.clientX}px`;
      beer.style.top = `${e.clientY}px`;
      document.body.appendChild(beer);

      setTimeout(() => {
        beer.remove();
      }, 2000);
    }
  </script>
</body>
</html>

