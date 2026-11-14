<!doctype html>
<html lang="zh-Hant">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>向植物學習｜直接類推配對</title>

  <style>
    * {
      box-sizing: border-box;
    }

    body {
      margin: 0;
      background: #f4f7ef;
      color: #193e32;
      font-family: system-ui, "Noto Sans TC", sans-serif;
      font-size: 19px;
    }

    main {
      max-width: 1120px;
      margin: auto;
      padding: 32px;
    }

    header {
      display: flex;
      justify-content: space-between;
      gap: 20px;
      align-items: center;
    }

    h1 {
      font-size: 34px;
      margin: 8px 0;
    }

    h2 {
      font-size: 22px;
    }

    p {
      line-height: 1.6;
    }

    button,
    select {
      font: inherit;
      border: 2px solid #9cb3a2;
      border-radius: 14px;
      padding: 16px;
      background: white;
      color: #193e32;
      cursor: pointer;
    }

    button:hover {
      border-color: #225e49;
    }

    button:focus-visible,
    select:focus-visible {
      outline: 4px solid #d99232;
      outline-offset: 3px;
    }

    .cols {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 28px;
    }

    .cards {
      display: grid;
      gap: 13px;
    }

    .card {
      text-align: left;
      min-height: 120px;
      display: flex;
      gap: 18px;
      align-items: center;
    }

    .card strong {
      display: block;
      font-size: 23px;
    }

    .card small {
      font-size: 17px;
      display: block;
      margin-top: 8px;
      color: #476454;
    }

    .icon {
      font-size: 40px;
    }

    .selected {
      background: #e0efdb;
      border: 3px solid #256345;
    }

    .done {
      background: #e5e8e2;
      opacity: 0.65;
    }

    .panel {
      background: #fff;
      padding: 22px;
      margin-top: 24px;
      border-radius: 18px;
    }

    select {
      width: 100%;
      margin: 12px 0;
    }

    #check {
      background: #225e49;
      color: white;
    }

    #feedback {
      min-height: 80px;
      margin-bottom: 0;
    }

    #status {
      white-space: nowrap;
      font-weight: bold;
    }

    footer {
      font-size: 16px;
      margin-top: 24px;
      color: #476454;
    }

    @media (max-width: 650px) {
      main {
        padding: 16px;
      }

      .cols {
        gap: 10px;
      }

      .card {
        padding: 12px;
        display: block;
      }

      h1 {
        font-size: 26px;
      }

      .icon {
        font-size: 28px;
      }

      header {
        display: block;
      }
    }
  </style>
</head>

<body>
  <main>
    <header>
      <div>
        <div>五年級自然 · 直接類推</div>
        <h1>向植物學習的仿生學</h1>
      </div>

      <div id="status" role="status">已完成 0／3 組</div>
    </header>

    <p>
      ① 選一張植物卡和一張用品卡　② 選共同特性<br>
      ③ 先口頭說理由，再檢查。重點是解釋原理，沒有計時競賽。
    </p>

    <div class="cols">
      <section>
        <h2>植物的構造或特性</h2>
        <div id="plants" class="cards"></div>
      </section>

      <section>
        <h2>用品與設計</h2>
        <div id="items" class="cards"></div>
      </section>
    </div>

    <section class="panel">
      <label for="reason">
        <strong>兩者共同的特性或作用是什麼？</strong>
      </label>

      <select id="reason">
        <option value="">請先選卡牌，再選共同原理</option>
        <option value="hook">
          用小鉤鉤住纖維，產生附著效果
        </option>
        <option value="water">
          表面使水不易鋪開，滾動水珠可帶走部分灰塵
        </option>
        <option value="air">
          增加空氣阻力，使下降速度減慢
        </option>
        <option value="color">
          只要顏色相同，就能有相同功能
        </option>
      </select>

      <p>請說：「＿＿像＿＿，因為兩者都＿＿，所以能＿＿。」</p>

      <button id="check">檢查配對</button>
      <button id="reset">重新開始</button>

      <p id="feedback" aria-live="polite">
        各組先討論20秒，再輪流派代表操作。選錯可重選。
      </p>
    </section>

    <footer>
      課本核心：大花咸豐草果實與魔鬼氈。蓮葉為課本延伸；
      蒲公英與降落傘為功能類比，並非發明起源的判定。<br>
      配對後再想：如何將這個原理用在生活用品？可能有什麼限制？
    </footer>
  </main>

  <script>
    const plants = [
      {
        id: "hook",
        icon: "🌿",
        title: "大花咸豐草果實",
        text: "觀察果實的倒鉤與附著方式。"
      },
      {
        id: "water",
        icon: "🪷",
        title: "蓮葉",
        text: "觀察表面水珠與滾動現象。"
      },
      {
        id: "air",
        icon: "🌼",
        title: "蒲公英果實的冠毛",
        text: "觀察果實在空氣中下降的情形。"
      }
    ];

    const items = [
      {
        id: "water",
        icon: "💧",
        title: "仿蓮葉自潔塗層",
        text: "水珠滾動，帶走部分表面灰塵。"
      },
      {
        id: "air",
        icon: "🪂",
        title: "降落傘",
        text: "展開傘面，讓下降速度減慢。"
      },
      {
        id: "hook",
        icon: "🎒",
        title: "魔鬼氈",
        text: "勾面與毛圈面可反覆貼合、分開。"
      }
    ];

    const explanations = {
      hook:
        "大花咸豐草果實倒鉤與魔鬼氈勾面，都能鉤住纖維而附著。" +
        "果實用來傳播，魔鬼氈用來固定；用途並不完全相同。",

      water:
        "蓮葉表面的微細構造與表面性質讓水不易鋪開。" +
        "仿蓮葉塗層借用這個原理，讓水珠滾落時帶走部分灰塵；" +
        "不保證能去除油汙。",

      air:
        "蒲公英果實的冠毛與降落傘都能增加空氣阻力、減慢下降。" +
        "這是功能相似的直接類推，不代表降落傘發明一定來自蒲公英。"
    };

    let selected = {
      plants: null,
      items: null
    };

    const completed = new Set();
    const feedback = document.querySelector("#feedback");

    function render() {
      for (const [type, data] of [
        ["plants", plants],
        ["items", items]
      ]) {
        const box = document.getElementById(type);
        box.replaceChildren();

        for (const card of data) {
          const button = document.createElement("button");

          button.className =
            "card" +
            (selected[type] === card.id ? " selected" : "") +
            (completed.has(card.id) ? " done" : "");

          button.disabled = completed.has(card.id);

          button.setAttribute(
            "aria-pressed",
            String(selected[type] === card.id)
          );

          button.innerHTML = `
            <span class="icon" aria-hidden="true">
              ${card.icon}
            </span>
            <span>
              <strong>
                ${card.title}${completed.has(card.id) ? " ✓" : ""}
              </strong>
              <small>${card.text}</small>
            </span>
          `;

          button.onclick = () => {
            selected[type] =
              selected[type] === card.id ? null : card.id;

            render();
          };

          box.append(button);
        }
      }

      document.querySelector("#status").textContent =
        `已完成 ${completed.size}／3 組`;
    }

    document.querySelector("#check").onclick = () => {
      const reason = document.querySelector("#reason").value;

      if (!selected.plants || !selected.items || !reason) {
        feedback.textContent =
          "請選一張植物卡、一張用品卡和共同原理，再向同學說明理由。";
        return;
      }

      if (selected.plants !== selected.items) {
        feedback.textContent =
          "再比較一次：它們靠哪個構造或特性發揮作用？" +
          "可以先重新閱讀卡牌，換一張試試。";
        return;
      }

      if (reason !== selected.plants) {
        feedback.textContent =
          "這兩張可以連結，但共同原理需要修正。" +
          "請找出它們如何產生相似的功能，而不只看外觀。";
        return;
      }

      const id = selected.plants;
      completed.add(id);

      feedback.textContent =
        "配對成功！" +
        explanations[id] +
        (completed.size === 3
          ? " 三組完成！選一項原理，提出生活設計，並說出一項限制。"
          : " 請另一組補充或提出問題，再繼續。");

      selected = {
        plants: null,
        items: null
      };

      document.querySelector("#reason").value = "";
      render();
    };

    document.querySelector("#reset").onclick = () => {
      completed.clear();

      selected = {
        plants: null,
        items: null
      };

      document.querySelector("#reason").value = "";

      feedback.textContent =
        "新一輪開始。請先討論，再說出共同構造或功能。";

      render();
    };

    render();
  </script>
</body>
</html>
