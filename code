// Web версия генератора открыток с миксом шрифтов на p5.js
// Поддержка кириллицы, случайный выбор шрифта или комбинации

let userName = "";
let ready = false;
let styleChoice = 0;
let fonts = [];
let fontNames = [
  "Rubik", "RussoOne", "Comfortaa", "AmaticSC", "BadScript", "PTSerif",
  "Neucha", "PoiretOne", "MarckScript", "YesevaOne", "Lobster", "Caveat",
  "PressStart2P", "FiraSansExtraCondensed", "Montserrat", "Raleway",
  "Ubuntu", "Exo2", "BebasNeue", "PlayfairDisplay"
];
let palette = [
  "#e63946", "#457b9d", "#a8dadc", "#f1faee", "#fca311", "#14213d",
  "#ffb4a2", "#6d6875", "#b5179e", "#3a0ca3", "#7209b7", "#4cc9f0"
];

function preload() {
  for (let name of fontNames) {
    fonts.push(loadFont(`fonts/${name}.ttf`));
  }
}

function setup() {
  createCanvas(800, 600);
  textAlign(CENTER, CENTER);
  textSize(32);
  background(255);
  noLoop();
}

function draw() {
  background("#f9f9f9");
  if (!ready) {
    fill(0);
    textSize(28);
    text("Введите имя и нажмите Enter", width / 2, height / 2 - 40);
    text(userName, width / 2, height / 2);
  } else {
    drawCard(userName);
  }
}

function keyTyped() {
  if (!ready) {
    if (key === '\n' || key === '\r') {
      ready = true;
      redraw();
    } else if (keyCode === BACKSPACE) {
      userName = userName.slice(0, -1);
      redraw();
    } else {
      userName += key;
      redraw();
    }
  } else {
    if (key === 's' || key === 'S') {
      saveCanvas(`card_${userName}`, 'jpg');
    } else if (key === 'r' || key === 'R') {
      redraw();
    }
  }
}

function drawCard(name) {
  background(random(palette));

  let useMixedFonts = random() < 0.5;

  for (let i = 0; i < name.length; i++) {
    let c = name[i];
    let x = random(100, width - 100);
    let y = random(100, height - 100);
    let fnt = useMixedFonts ? random(fonts) : fonts[0];
    textFont(fnt);
    fill(random(palette));
    textSize(random(40, 80));
    text(c, x, y);
  }

  textAlign(CENTER, CENTER);
  textFont(random(fonts));
  fill(20);
  textSize(42);
  text("С др, крч!", width / 2, height - 60);
}
