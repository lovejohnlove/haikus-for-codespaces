<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Dr. Omnimanity - Stsphere Theory</title>
  <style>
    body {
      margin: 0;
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      background: radial-gradient(circle, #00f, #0ff, #0f0, #ff0, #f90, #f00);
      background-size: 400% 400%;
      animation: backgroundShift 30s linear infinite;
      color: #ffffff;
      text-align: center;
      padding: 50px;
      overflow: hidden;
      position: relative;
    }

    @keyframes backgroundShift {
      0% { background-position: 0% 50%; }
      50% { background-position: 100% 50%; }
      100% { background-position: 0% 50%; }
    }

    .particles {
      position: absolute;
      width: 100%;
      height: 100%;
      top: 0;
      left: 0;
      background: transparent;
      pointer-events: none;
      z-index: 0;
      overflow: hidden;
    }

    .particle {
      position: absolute;
      width: 2px;
      height: 2px;
      background: white;
      border-radius: 50%;
      opacity: 0.6;
      animation: float 20s linear infinite;
    }

    @keyframes float {
      0% { transform: translateY(0) translateX(0); opacity: 0.6; }
      100% { transform: translateY(-100vh) translateX(20vw); opacity: 0; }
    }

    .spiral {
      position: absolute;
      top: 50%;
      left: 50%;
      width: 800px;
      height: 800px;
      background: repeating-radial-gradient(
        circle at center,
        hsla(200, 100%, 70%, 0.2) 0px,
        hsla(220, 100%, 70%, 0.2) 5px,
        transparent 5px,
        transparent 10px
      );
      border-radius: 50%;
      transform: translate(-50%, -50%) scale(1) rotate(0deg);
      animation: spin 60s linear infinite, breathe 6s ease-in-out infinite, hueShift 20s linear infinite;
      z-index: 1;
    }

    @keyframes spin {
      0% { transform: translate(-50%, -50%) scale(1) rotate(0deg); }
      100% { transform: translate(-50%, -50%) scale(1) rotate(360deg); }
    }

    @keyframes breathe {
      0%, 100% { transform: translate(-50%, -50%) scale(1); }
      50% { transform: translate(-50%, -50%) scale(1.2); }
    }

    @keyframes hueShift {
      0% {
        background: repeating-radial-gradient(
          circle at center,
          hsla(200, 100%, 70%, 0.2) 0px,
          hsla(220, 100%, 70%, 0.2) 5px,
          transparent 5px,
          transparent 10px
        );
      }
      50% {
        background: repeating-radial-gradient(
          circle at center,
          hsla(300, 100%, 70%, 0.2) 0px,
          hsla(320, 100%, 70%, 0.2) 5px,
          transparent 5px,
          transparent 10px
        );
      }
      100% {
        background: repeating-radial-gradient(
          circle at center,
          hsla(200, 100%, 70%, 0.2) 0px,
          hsla(220, 100%, 70%, 0.2) 5px,
          transparent 5px,
          transparent 10px
        );
      }
    }

    .content {
      position: relative;
      z-index: 2;
    }

    h1 {
      font-size: 3em;
      margin-bottom: 0.5em;
      text-shadow: 2px 2px 8px #000;
    }

    h2 {
      font-size: 2em;
      margin-bottom: 1em;
      text-shadow: 1px 1px 5px #000;
    }

    p {
      font-size: 1.2em;
      max-width: 800px;
      margin: auto;
      text-shadow: 1px 1px 3px #000;
    }

    .controls {
      margin-top: 30px;
    }

    button {
      background: rgba(0, 0, 50, 0.8);
      color: white;
      border: 1px solid #0ff;
      padding: 10px 20px;
      margin: 5px;
      border-radius: 5px;
      cursor: pointer;
      transition: background 0.3s;
    }

    button:hover {
      background: rgba(0, 50, 100, 0.8);
    }

    footer {
      margin-top: 50px;
      font-size: 0.9em;
      opacity: 0.7;
    }

    .portal {
      display: none;
      position: absolute;
      top: 50%;
      left: 50%;
      width: 200px;
      height: 200px;
      background: transparent;
      border: 2px solid rgba(0, 255, 255, 0.8);
      border-radius: 50%;
      transform: translate(-50%, -50%);
      animation: portalOpen 1.5s ease-in-out forwards;
    }

    @keyframes portalOpen {
      0% { width: 200px; height: 200px; opacity: 1; }
      100% { width: 1000px; height: 1000px; opacity: 0; }
    }

  </style>
</head>
<body>

  <div class="particles" id="particles"></div>

  <div class="spiral" id="spiral"></div>
  <div class="portal" id="portal"></div>

  <div class="content">
    <h1>Dr. Omnimanity</h1>
    <h2>World of One - Stsphere Theory of Time</h2>
    <p>
      Welcome to the exploration of time as a tangible matter — woven from the finest grains of space itself. 
      In the Stsphere Theory, time is not a flow, but a structure: a lattice of space grains shaping reality 
      moment by moment, folding existence into endless spirals of perception.
    </p>

    <div class="controls">
      <button onclick="setSpeed('slow')">Spiral Slow</button>
      <button onclick="setSpeed('medium')">Spiral Medium</button>
      <button onclick="setSpeed('fast')">Spiral Fast</button>
      <button onclick="toggleBreathe()">Toggle Breathing</button>
      <button onclick="toggleHue()">Toggle Color Shift</button>
      <button onclick="enterStsphere()">Enter the Stsphere</button>
    </div>

    <footer>
      © 2025 Dr. Omnimanity
    </footer>
  </div>

  <script>
    // Particle creation
    const particleContainer = document.getElementById('particles');
    for (let i = 0; i < 100; i++) {
      const p = document.createElement('div');
      p.classList.add('particle');
      p.style.top = Math.random() * 100 + 'vh';
      p.style.left = Math.random() * 100 + 'vw';
      p.style.animationDuration = (10 + Math.random() * 20) + 's';
      p.style.opacity = Math.random();
      particleContainer.appendChild(p);
    }

    const spiral = document.getElementById('spiral');
    const portal = document.getElementById('portal');
    let hueOn = true;
    let breatheOn = true;

    function setSpeed(speed) {
      if (speed === 'slow') {
        spiral.style.animationDuration = 'spin 90s linear infinite, ' + (breatheOn ? 'breathe 6s ease-in-out infinite,' : '') + (hueOn ? 'hueShift 20s linear infinite' : '');
      } else if (speed === 'medium') {
        spiral.style.animationDuration = 'spin 60s linear infinite, ' + (breatheOn ? 'breathe 6s ease-in-out infinite,' : '') + (hueOn ? 'hueShift 20s linear infinite' : '');
      } else if (speed === 'fast') {
        spiral.style.animationDuration = 'spin 30s linear infinite, ' + (breatheOn ? 'breathe 6s ease-in-out infinite,' : '') + (hueOn ? 'hueShift 20s linear infinite' : '');
      }
    }

    function toggleBreathe() {
      breatheOn = !breatheOn;
      spiral.style.animation = `spin 60s linear infinite${breatheOn ? ', breathe 6s ease-in-out infinite' : ''}${hueOn ? ', hueShift 20s linear infinite' : ''}`;
    }

    function toggleHue() {
      hueOn = !hueOn;
      spiral.style.animation = `spin 60s linear infinite${breatheOn ? ', breathe 6s ease-in-out infinite' : ''}${hueOn ? ', hueShift 20s linear infinite' : ''}`;
    }

    function enterStsphere() {
      portal.style.display = 'block';
      setTimeout(() => {
        alert("Entering the deeper levels of the Stsphere... (more coming soon!)");
      }, 1500);
    }
  </script>

</body>
</html>
# Haikus for Codespaces

This is a quick node project template for demoing Codespaces. It is based on the [Azure node sample](https://github.com/Azure-Samples/nodejs-docs-hello-world). It's great!!!

Point your browser to [Quickstart for GitHub Codespaces](https://docs.github.com/en/codespaces/getting-started/quickstart) for a tour of using Codespaces with this repo.
