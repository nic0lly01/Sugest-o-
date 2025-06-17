let sugestoes = [
  {
    titulo: "Look Glamour Noite",
    olhos: "Olho preto esfumado com glitter",
    boca: "Batom vinho matte",
    pele: "Contorno marcado e iluminador perolado"
  },
  {
    titulo: "Look Natural Dia",
    olhos: "Sombra pêssego suave e máscara leve",
    boca: "Balm com cor rosada",
    pele: "Base leve e blush coral"
  },
  {
    titulo: "Look Colorido Criativo",
    olhos: "Delineado gráfico azul turquesa",
    boca: "Gloss transparente",
    pele: "Blush lilás e iluminador holográfico"
  },
  {
    titulo: "Look Clássico Chic",
    olhos: "Delineado gatinho preto",
    boca: "Batom vermelho vibrante",
    pele: "Pele acetinada e sobrancelhas definidas"
  },
  {
    titulo: "Look Romântico",
    olhos: "Sombra rosé cintilante",
    boca: "Batom rosa claro cremoso",
    pele: "Blush rosado e iluminador suave"
  }
];

let sugestaoAtual;
let fade = 0;
let animando = false;

function setup() {
  createCanvas(600, 400);
  textFont('Georgia');
  textAlign(CENTER, CENTER);
  gerarNovaSugestao();
}

function draw() {
  background('#fef8f5');

  if (animando) {
    fade += 5;
    if (fade >= 255) {
      fade = 255;
      animando = false;
    }
  }

  fill(0, fade);
  textSize(26);
  text(sugestaoAtual.titulo, width / 2, 70);

  textSize(18);
  text("👁 " + sugestaoAtual.olhos, width / 2, 140);
  text("👄 " + sugestaoAtual.boca, width / 2, 190);
  text("💆 " + sugestaoAtual.pele, width / 2, 240);

  textSize(14);
  fill(100, fade);
  text("Clique para nova sugestão", width / 2, height - 40);
}

function mousePressed() {
  gerarNovaSugestao();
}

function gerarNovaSugestao() {
  let nova;
  do {
    nova = random(sugestoes);
  } while (nova === sugestaoAtual);
  sugestaoAtual = nova;
  fade = 0;
  animando = true;
}
