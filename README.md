//variaveis da bolinha
let xBolinha = 300;
let yBolinha = 200;
let diametro = 15;
let raio = diametro / 2 ;

//velocidade da bolinha 
let velocidadeXBolinha = 6;
let velocidadeYBolinha = 6;


//variaveis da raquete 
let xRaquete = 5;
let yRaquete = 150;
let raqueteComprimento = 10;
let raqueteAltura = 90;

//variaveis do oponente 
let xraqueteOponente = 585;
let yraqueteOponente = 150;

function setup() {
  createCanvas(600, 400);
}

function draw() {
  background(0);
  mostraBolinha();
  movimentaBolinha();
  verificaColisaoBorda();
  mostraRaquete(xRaquete, yRaquete);
  movimentaMinhaRaquete();
  verificaColisaoRaquete();
}

function mostraBolinha() {
  circle(xBolinha, yBolinha, diametro);
}

function movimentaBolinha() {
  xBolinha += velocidadeXBolinha;
  yBolinha += velocidadeYBolinha;
}

function verificaColisaoBorda() {
 if (xBolinha + raio> width ||
     xBolinha - raio < 0) {
    velocidadeXBolinha *= -1;
  }
  if (yBolinha + raio> height ||
      yBolinha - raio < 0) {
    velocidadeYBolinha *= -1;
   }
}

function mostraRaquete(x, y){
  rect(x,y, raqueteComprimento,
       raqueteAltura);
}



function moovimentaMinhaRaquete(){
  if (KeyIsDown(UP_ARROW)){
    yRaquete -= 10;
  }
  if (KeyIsDown(DOWN_ARROW)){
    yRaquete += 10;
  }
}

function verificaColisaoRaquete(){
  if (xBolinha - raio < xRaquete + raqueteComprimento &&
      yBolinha - raio < yRaquete + raqueteAltura &&
      yBolinha + raio > yRaquete){
    velocidadeXBolinha *= -1;
   }
}
