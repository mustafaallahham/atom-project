# atom-projecthtml
<!DOCTYPE html>
<html lang="ar">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>نموذج الذرة التفاعلي</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>

  <header>
    <h1>مرحباً في مشروع الذرة التفاعلي</h1>
    <nav>
      <a href="index.html">الرئيسية</a> |
      <a href="quiz.html">الاختبار</a>
    </nav>
  </header>

  <main>
    <h2>ماذا ستتعلم هنا؟</h2>
    <p>في هذا المشروع، ستتعرف على مكونات الذرة (البروتونات، النيوترونات، الإلكترونات) وكيفية توزيعها في المدارات.</p>

    <iframe src="atom-model-full.html" width="100%" height="500" frameborder="0"></iframe>

    <p>يمكنك تجربة النموذج أعلاه وسحب الجسيمات كما تشاء!</p>
  </main>

  <footer>
    <p>مشروع تعليمي - جميع الحقوق محفوظة &copy;</p>
  </footer>

</body>
</html>

html
<!DOCTYPE html>
<html lang="ar">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>اختبار الذرة</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>

  <header>
    <h1>اختبار الذرة</h1>
    <nav>
      <a href="index.html">الرئيسية</a> |
      <a href="quiz.html">الاختبار</a>
    </nav>
  </header>

  <main>
    <h2>هل أنت جاهز لاختبار بسيط؟</h2>
    <form id="quizForm">
      <p><strong>1. ما الشحنة التي يحملها البروتون؟</strong></p>
      <label><input type="radio" name="q1" value="a"> سالبة</label><br>
      <label><input type="radio" name="q1" value="b"> موجبة</label><br>
      <label><input type="radio" name="q1" value="c"> لا شحنة</label><br>

      <p><strong>2. أي جسيم يدور حول النواة؟</strong></p>
      <label><input type="radio" name="q2" value="a"> البروتون</label><br>
      <label><input type="radio" name="q2" value="b"> النيوترون</label><br>
      <label><input type="radio" name="q2" value="c"> الإلكترون</label><br>

      <button type="button" onclick="submitQuiz()">إرسال الإجابات</button>
    </form>

    <div id="result"></div>
  </main>

  <footer>
    <p>مشروع تعليمي - جميع الحقوق محفوظة &copy;</p>
  </footer>

  <script>
    function submitQuiz() {
      const q1 = document.querySelector('input[name="q1"]:checked');
      const q2 = document.querySelector('input[name="q2"]:checked');

      let score = 0;
      if (q1 && q1.value === 'b') score++;
      if (q2 && q2.value === 'c') score++;

      document.getElementById('result').innerHTML = `<p>لقد حصلت على ${score} من 2</p>`;
    }
  </script>

</body>
</html>


css
body {
  font-family: Arial, sans-serif;
  margin: 0;
  padding: 0;
  background: #f0f2f5;
  color: #333;
}

header {
  background: #2c3e50;
  color: white;
  padding: 20px;
  text-align: center;
}

nav a {
  color: white;
  margin: 0 10px;
  text-decoration: none;
}

main {
  padding: 20px;
}

footer {
  background: #2c3e50;
  color: white;
  text-align: center;
  padding: 10px;
}


html
<!DOCTYPE html>
<html lang="ar">
<head>
  <meta charset="UTF-8">
  <title>نموذج تفاعلي متكامل للذرة</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <style>
    body {
      font-family: 'Segoe UI', sans-serif;
      text-align: center;
      background: #f5f6fa;
      margin: 0;
      padding: 20px;
    }
    h1 {
      color: #2f3640;
    }
    select, button {
      padding: 10px;
      margin: 10px;
      font-size: 16px;
    }
    #atom {
      position: relative;
      width: 400px;
      height: 400px;
      margin: 50px auto;
      border-radius: 50%;
      background: radial-gradient(circle, #ffffff 60%, #dcdde1 100%);
      box-shadow: 0 0 15px rgba(0,0,0,0.2);
    }
    .orbit {
      position: absolute;
      border: 1px dashed #555;
      border-radius: 50%;
      pointer-events: none;
    }
    .electron, .proton, .neutron {
      position: absolute;
      width: 15px;
      height: 15px;
      border-radius: 50%;
      cursor: grab;
      transition: transform 0.2s;
    }
    .electron:hover, .proton:hover, .neutron:hover {
      transform: scale(1.2);
    }
    .electron { background: #3498db; }
    .proton { background: #e74c3c; }
    .neutron { background: #7f8c8d; }

    .tooltip {
      position: absolute;
      background: #2c3e50;
      color: white;
      padding: 5px 10px;
      border-radius: 5px;
      font-size: 12px;
      white-space: nowrap;
      pointer-events: none;
      opacity: 0;
      transition: opacity 0.3s;
      z-index: 10;
    }

    #infoBox {
      margin-top: 20px;
      font-size: 16px;
    }

    @media (max-width: 500px) {
      #atom {
        width: 280px;
        height: 280px;
      }
    }
  </style>
</head>
<body>

<h1>نموذج تفاعلي متكامل للذرة</h1>

<select id="elementSelector">
  <option value="hydrogen">هيدروجين (H)</option>
  <option value="helium" selected>هيليوم (He)</option>
  <option value="carbon">كربون (C)</option>
  <option value="oxygen">أكسجين (O)</option>
  <option value="sodium">صوديوم (Na)</option>
  <option value="chlorine">كلور (Cl)</option>
  <option value="argon">أرجون (Ar)</option>
  <option value="calcium">كالسيوم (Ca)</option>
</select>

<button onclick="downloadImage()">💾 حفظ كصورة</button>
<button onclick="toggleLang()">🔄 تبديل اللغة</button>

<div id="atom">
  <div id="nucleus" style="position: absolute; left: 190px; top: 190px; width: 20px; height: 20px; background: black; border-radius: 50%;"></div>
</div>

<div id="infoBox"></div>
<div class="tooltip" id="tooltip"></div>

<script>
  const elements = {
    hydrogen: { protons: 1, neutrons: 0, electrons: 1 },
    helium: { protons: 2, neutrons: 2, electrons: 2 },
    carbon: { protons: 6, neutrons: 6, electrons: 6 },
    oxygen: { protons: 8, neutrons: 8, electrons: 8 },
    sodium: { protons: 11, neutrons: 12, electrons: 11 },
    chlorine: { protons: 17, neutrons: 18, electrons: 17 },
    argon: { protons: 18, neutrons: 22, electrons: 18 },
    calcium: { protons: 20, neutrons: 20, electrons: 20 }
  };

  const orbits = [
    { radiusX: 50, radiusY: 50, top: 175, left: 175 },  // K
    { radiusX: 100, radiusY: 100, top: 150, left: 150 }, // L
    { radiusX: 150, radiusY: 150, top: 125, left: 125 }, // M
    { radiusX: 200, radiusY: 200, top: 100, left: 100 }  // N
  ];

  let currentLang = 'ar';

  function distributeElectrons(total) {
    const maxInOrbit = [2, 8, 8, 18, 32];
    let electrons = [];
    let remaining = total;
    for (let i = 0; i < maxInOrbit.length && remaining > 0; i++) {
      let count = Math.min(maxInOrbit[i], remaining);
      for (let j = 0; j < count; j++) {
        electrons.push(i);
      }
      remaining -= count;
    }
    return electrons;
  }

  function drawAtom() {
    const selected = document.getElementById('elementSelector').value;
    const data = elements[selected];
    const electronLevels = distributeElectrons(data.electrons);

    // مسح القديم
    document.querySelectorAll('.electron, .proton, .neutron, .orbit').forEach(e => e.remove());

    const atom = document.getElementById('atom');

    // رسم المدارات
    electronLevels.forEach((level, index) => {
      if (electronLevels.includes(level)) {
        const orbit = document.createElement('div');
        orbit.className = 'orbit';
        orbit.style.width = orbits[level].radiusX * 2 + 'px';
        orbit.style.height = orbits[level].radiusY * 2 + 'px';
        orbit.style.top = orbits[level].top + 'px';
        orbit.style.left = orbits[level].left + 'px';
        atom.appendChild(orbit);
      }
    });

    // رسم الإلكترونات
    electronLevels.forEach((level, index) => {
      const angle = (index / electronLevels.filter(e => e === level).length) * 2 * Math.PI;
      const x = orbits[level].radiusX * Math.cos(angle);
      const y = orbits[level].radiusY * Math.sin(angle);
      const electron = document.createElement('div');
      electron.className = 'electron';
      electron.style.left = (orbits[level].left + orbits[level].radiusX + x - 7) + 'px';
      electron.style.top = (orbits[level].top + orbits[level].radiusY + y - 7) + 'px';
      electron.dataset.info = currentLang === 'ar' ? "إلكترون | -1 شحنة" : "Electron | -1 charge";
      atom.appendChild(electron);
      setupDragging(electron);
      setupTooltip(electron);
    });

    // رسم البروتونات والنيوترونات
    for (let i = 0; i < data.protons; i++) {
      const p = document.createElement('div');
      p.className = 'proton';
      p.style.left = (190 + Math.random() * 10) + 'px';
      p.style.top = (190 + Math.random() * 10) + 'px';
      p.dataset.info = currentLang === 'ar' ? "بروتون | +1 شحنة" : "Proton | +1 charge";
      atom.appendChild(p);
      setupDragging(p);
      setupTooltip(p);
    }

    for (let i = 0; i < data.neutrons; i++) {
      const n = document.createElement('div');
      n.className = 'neutron';
      n.style.left = (190 + Math.random() * 10) + 'px';
      n.style.top = (190 + Math.random() * 10) + 'px';
      n.dataset.info = currentLang === 'ar' ? "نيوترون | لا شحنة" : "Neutron | No charge";
      atom.appendChild(n);
      setupDragging(n);
      setupTooltip(n);
    }

    // عرض المعلومات
    document.getElementById('infoBox').innerHTML = `
      <strong>${currentLang === 'ar' ? 'عدد البروتونات' : 'Protons'}:</strong> ${data.protons} |
      <strong>${currentLang === 'ar' ? 'عدد النيوترونات' : 'Neutrons'}:</strong> ${data.neutrons} |
      <strong>${currentLang === 'ar' ? 'عدد الإلكترونات' : 'Electrons'}:</strong> ${data.electrons} |
      <strong>${currentLang === 'ar' ? 'الكتلة الذرية' : 'Atomic Mass'}:</strong> ${data.protons + data.neutrons}
    `;
  }

  function toggleLang() {
    currentLang = currentLang === 'ar' ? 'en' : 'ar';
    drawAtom();
  }

  function setupDragging(p) {
    let isDragging = false;
    p.addEventListener('mousedown', () => isDragging = true);
    document.addEventListener('mouseup', () => isDragging = false);
    document.addEventListener('mousemove', e => {
      if (isDragging) {
        p.style.left = e.pageX - 7 + 'px';
        p.style.top = e.pageY - 7 + 'px';
      }
    });
  }

  function setupTooltip(p) {
    const tooltip = document.getElementById('tooltip');
    p.addEventListener('mouseover', () => {
      tooltip.textContent = p.dataset.info;
      tooltip.style.opacity = 1;
    });
    p.addEventListener('mousemove', e => {
      tooltip.style.left = e.pageX + 10 + 'px';
      tooltip.style.top = e.pageY + 10 + 'px';
    });
    p.addEventListener('mouseleave', () => {
      tooltip.style.opacity = 0;
    });
  }

  function downloadImage() {
    html2canvas(document.getElementById('atom')).then(canvas => {
      const link = document.createElement('a');
      link.download = 'atom-model.png';
      link.href = canvas.toDataURL();
      link.click();
    });
  }

  // تهيئ عند التحميل
  drawAtom();
  document.getElementById('elementSelector').addEventListener('change', drawAtom);
</script>

<!-- مكتبة html2canvas لحفظ الصورة -->
<script src="https://cdnjs.cloudflare.com/ajax/libs/html2canvas/1.4.1/html2canvas.min.js"></script>

</body>
</html>





كل ما يخص الذرات من معلومات
