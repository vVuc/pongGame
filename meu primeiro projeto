//BOLA//
let xBola =300;
let yBola = 200;
let diametro = 22;
let raio = diametro/2;
//VELOCIDADE DA BOLA//
let velocidadeX = 5;
let velocidadeY = 5;
//MINHA RAQUETE//
let myPosicaoX = 8
let myPosicaoY = 170
let largura = 12
let altura = 60
//RAQUETE OPONENTE//
let yourPosicaoX = 580
let yourPosicaoY = 170
let velocidadeYOponente
let chanceDeErrar = 0;
//PLACAR//
let myPoints = 0
let yourPoints = 0
//SONS//
let raquetada;
let ponto;
let trilha;
function circulo(){
  circle(xBola, yBola, diametro);
}
function moverBola(){
  xBola += velocidadeX;
  yBola += velocidadeY;
} 
function calculaChanceDeErrar() {
  if (yourPoints >= myPoints) {
    chanceDeErrar += 1
    if (chanceDeErrar >= 39){
    chanceDeErrar = 40
    }
  } else {
    chanceDeErrar -= 1
    if (chanceDeErrar <= 35){
    chanceDeErrar = 35
    }
  }
}
function colisaoBolaXY() {
  if(xBola + raio > width || xBola - raio < 0){
    velocidadeX *= -1;
  } 
  if(yBola + raio > height || yBola - raio < 0){
    velocidadeY *= -1;
  } 
}
function bolinhaNaoFicaPresa(){
    if (xbola - raio < 0){
    xbola = 26
    }
}
function setup() {
  createCanvas(600, 400);
  trilha.loop();
}
 function raquetes(x,y){
rect(x, y, largura, altura);
}
function movimentoRaquete() {
  if(keyIsDown(UP_ARROW)){
    myPosicaoY -= 6
  }
  if(keyIsDown(DOWN_ARROW)){
    myPosicaoY += 6
  }
}

function colisaoBolaRaquete(){
  if(xBola - raio < myPosicaoX + largura && yBola + raio > myPosicaoY && yBola - raio < myPosicaoY + altura){
    velocidadeX *= -1
    raquetada.play()
  }
  
  if(xBola + raio > yourPosicaoX && yBola + raio > yourPosicaoY && yBola - raio < yourPosicaoY + altura){
    velocidadeX *= -1
    raquetada.play()
  }
}

function movimentaRaqueteOponente(){
  velocidadeYOponente = yBola - yourPosicaoY - largura/2 - 30
  yourPosicaoY+=velocidadeYOponente + chanceDeErrar
  calculaChanceDeErrar()
}

function placar(){
  stroke(255)
  textAlign(CENTER)
  textSize(16)
  fill(color(255,0,0));
  rect(150, 10, 40, 20)
  fill(255);
  text(myPoints,170,26)
  fill(color(255,0,0));
  rect(450, 10, 40, 20)
  fill(255);
  text(yourPoints,470,26)
}

function marcaPonto(){
  if(xBola>588){
  myPoints += 1
    ponto.play()
  }
   if(xBola<12){
  yourPoints += 1
     ponto.play()
  }
}

function preload(){
  trilha = loadSound("trilha.mp3")
  raquetada = loadSound("raquetada.mp3")
  ponto = loadSound("ponto.mp3")
}

function draw() {
  background(0);
  circulo();
  moverBola();
  colisaoBolaXY();
  raquetes(myPosicaoX, myPosicaoY);
  raquetes(yourPosicaoX, yourPosicaoY);
  movimentoRaquete()
  colisaoBolaRaquete()
  movimentaRaqueteOponente()
  placar()
  marcaPonto()
}

