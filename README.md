# NINJA-DO-VENTO---1-
Game 2D: Ninja do Vento


Este é o meu primeiro código complexo em JavaScript. Um jogo em 2d com tema chinês e similaridades com jogos consagrados como S. Mario. Estou extremamente contente com os meus resultados, mesmo que simplórios, pois demonstram a minha pequena e contínua evolução dentro da comunidade de programadores.


const musica = new Audio();
musica.src = './musica.mp3'
//musica.play ();

const salto = new Audio();
salto.src = './salto.mp3'


const sprites = new Image();
sprites.src = './sprites.png';

const canvas = document.querySelector('canvas');
const contexto = canvas.getContext('2d');

let frames = 0;

var camera = {
x:0,
y:0,
width: canvas.width,
height: canvas.height,

leftEdge: function(){
return this.x + (this.width * 0.25);
},



  function loop() {
    // camera seguindo
    


    contexto.save();
    contexto.translate(-camera.x, -camera.y);

    
  planoDeFundo.desenha();
  flappyBird.desenha();
  chao.desenha();
  chao2.desenha();

// tentando aplicar colisão d

const flappyBirdY = flappyBird.y
const flappyBirdX = flappyBird.x
const chaoY = chao.y
const chaoX = chao.x
const chao2Y = chao2.y
const chao2X = chao2.x

//if (flappyBirdY =< chao2Y) {

if (moveRight && flappyBirdX > chao2X - 75 && flappyBirdY > 100) {

  flappyBird.x -= 6;
}

/* COLISÃO FUNCIONANDO MAS SEM FINAL NO EIXO Yd

if (flappyBirdX > chao2X - 75) {

  flappyBird.x -= 6;
}  else if (flappyBirdY < 250) {
flappyBird.x += 6;
}

*/ 

// GRAVIDADE FIA DA PUTA

if (flappyBirdY < chaoY -85 && flappyBirdY < chao2Y -85) {
  gravidade();
} 


/*
if (flappyBirdY < chaoY -85 && flappyBirdX != chao2X) {
  gravidade();

}*/




//gravidade();
//camera seguindo 
contexto.restore();
update();

frames = frames + 0.1;


  requestAnimationFrame(loop);

}


/*
window.addEventListener("click", function() {
  pulo();


 setTimeout(() => {


      flappyBird.velocidade = flappyBird.velocidade + flappyBird.gravidade
     flappyBird.y = flappyBird.y + flappyBird.velocidade
     flappyBird.y = flappyBird.y + 60
      flappyBird.x = flappyBird.x + 60
  
}, 200 );
})
*/



loop();



rightEdge: function() {
  return this.x + (this.width * 0.75);
  },

  topEdge: function() {
    return this.y + (this.height * 0.25);
    },

    bottomEdge: function() {
      return this.y + (this.height * 0.75);
      },
}
// CENTRALIZAR A CAMERA
//camera.y = flappyBird.y
//camera.x = flappyBird.x

//MOVIMENTA O PERSONAGEM
var moveLeft = moveRight = puloUp = false;

window.addEventListener('keydown', function(e){
  console.log
  var key = e.keyCode;
  switch(key){
    case 	65:
moveLeft = true, console.log('esquerda');
break;
      case 68:
moveRight = true, console.log('direita');
break;

case 32:
        puloUp = true; 
        break;
        
  }
  
}, false);

window.addEventListener('keyup', function(e){
  var key = e.keyCode;
  switch(key){
    case 	65:
moveLeft = false;
      break;
      case 68:
 moveRight = false;
        break;
case 32:
puloUp = false;
        break;
  
}}, false); 

function update(){
  if(moveLeft){
    flappyBird.x -= 6;
  }

  if(moveRight){
    flappyBird.x += 6;
  };

  if(puloUp){
    pulo();
  };
  

// camera bugada
camera.y = flappyBird.y - 300
camera.x = flappyBird.x 

//andar com o personagem
if (flappyBird.x < camera.leftEdge()){
camera.x = flappyBird.x - (camera.width * 0.25)
} 

if (flappyBird.x + flappyBird.width > camera.rightEdge()){
  camera.x = flappyBird.x +flappyBird.y - (camera.width * 0.75)
  }
}


const planoDeFundo = {
    spriteX: 347,
    spriteY: 0,
    largura: 3348,
    altura: 597,
    x: 0,
    y: -241,
    

    atualiza() {
        flappyBird.velocidade = flappyBird.velocidade + flappyBird.gravidade
        flappyBird.y = flappyBird.y + flappyBird.velocidade

    },
  
    desenha() {
      contexto.fillStyle = '#201001';
      contexto.fillRect(0,0, canvas.width, canvas.height)
  
      contexto.drawImage(
        sprites,
        planoDeFundo.spriteX, planoDeFundo.spriteY,
        planoDeFundo.largura, planoDeFundo.altura,
        planoDeFundo.x, planoDeFundo.y,
        planoDeFundo.largura, planoDeFundo.altura,
      );
  
      contexto.drawImage(
        sprites,
        planoDeFundo.spriteX, planoDeFundo.spriteY,
        planoDeFundo.largura, planoDeFundo.altura,
        (planoDeFundo.x + planoDeFundo.largura), planoDeFundo.y,
        planoDeFundo.largura, planoDeFundo.altura,
      );
    },
  };
  
  const chao = {
    spriteX: 0,
    spriteY: 610,
    largura: 3000,
    altura: 112,
    x: 0,
    y: 355,
    
    desenha() {
      contexto.drawImage(
        sprites,
        chao.spriteX, chao.spriteY,
        chao.largura, chao.altura,
        chao.x, chao.y,
        chao.largura, chao.altura,
      );
  
      contexto.drawImage(
        sprites,
        chao.spriteX, chao.spriteY,
        chao.largura, chao.altura,
        (chao.x + chao.largura), chao.y,
        chao.largura, chao.altura,
      );
    },
  };

  const chao2 = {
    spriteX: 0,
    spriteY: 800,
    largura: 220,
    altura: 200,
    x: 1500,
    y: 200,
    
    desenha() {
      contexto.drawImage(
        sprites,
        chao2.spriteX, chao2.spriteY,
        chao2.largura, chao2.altura,
        chao2.x, chao2.y,
        chao2.largura, chao2.altura,
      );
  
      contexto.drawImage(
        sprites,
        chao2.spriteX, chao2.spriteY,
        chao2.largura, chao2.altura,
        (chao2.x + chao2.largura), chao2.y,
        chao2.largura, chao2.altura,
      );
    },
  };

  

  const flappyBird = {
    spriteX: 0,
    spriteY: 0,
    largura: 70,
    altura: 80,
    x: 80,
    y: 269,
    gravidade: 0.25,
    velocidade: 0,
//MOVIMENTOS
    movimentos: [
    {spriteX: 0, spriteY: 0,},
    {spriteX: 0, spriteY: 80,},
    {spriteX: 0, spriteY: 10,},
    {spriteX: 0, spriteY: 240,},
    ],





    /// framesssssssss 

/*
if(moveLeft || moveRight) {
  frameAtual++;
  spriteY = Math.floor(frameAtual / 5) * movimentos.height;
};


    atualiza() {

      if(fazColisao(flappyBird, chao))
    }
    
*/

// FRAMES
/*
    frameAtual: 0,
    atualizaOFrameAtual() {

const intervaloDeFrames = 10;
const passouOIntervalo = frames % intervaloDeFrames === 1;


if(passouOIntervalo) {
      const baseDoIncremento = 1;
      const incremento = baseDoIncremento + flappyBird.frameAtual
      const baseRepeticao = flappyBird.movimentos.length;
      flappyBird.frameAtual = incremento % baseRepeticao
    },

   },*/


  

  
    desenha() {
      
 /* flappyBird.atualizaOFrameAtual();*/
//MOVIMENTOS
const {spriteX, spriteY} = flappyBird.movimentos[0];

if(haduken) {

const {spriteX, spriteY} = flappyBird.movimentos[3];}


function haduken(){
const {spriteX, spriteY} = flappyBird.movimentos[3];




  /*
flappyBird.spriteX = 0
flappyBird.spriteY = 240


  contexto.drawImage(
        
    sprites,
    spriteX, 240, // Sprite X, Sprite Y
    flappyBird.largura, flappyBird.altura, // Tamanho do recorte na sprite
    flappyBird.x, flappyBird.y, // posição?
    flappyBird.largura, flappyBird.altura,  );
*/

    
  } 

window.addEventListener("click", function() {
  haduken();
  const haduken1 = true;
})




// TENTANDO COLOCAR A PORRA DOS FRAMES
/*

setTimeout(() => {
flappyBird.movimentos[1]
}, 200 );

setTimeout(() => {
  flappyBird.movimentos[2]
  }, 200 );

  setTimeout(() => {s
    flappyBird.movimentos[3]
    }, 200 );

*/

// GERANDO NÚMERO ALEATÓRIO ENTRE 2 E 1


animacaoAndar();


/*
window.addEventListener('keydown', function(e){
  var key = e.keyCode;
  switch(key){
    case 	65:
moveLeft = true;
break;
      case 68:
moveRight = true;
break;

case 32:
        puloUp = true; 
        break;
        
  }


*/

//tentando gerar ataque




//if () { }

function animacaoAndar() { 

const getRandomIntegerInclusive = (min, max) => Math.floor(Math.random() * (max - min + 1) + min)



// LIMPAR ERROS NA TELA: contexto.clearRect(0,0),
if(moveLeft || moveRight && getRandomIntegerInclusive (1,3) === 3 ) {
  contexto.drawImage(
        
    sprites,
    spriteX, 80, // Sprite X, Sprite Y
    flappyBird.largura, flappyBird.altura, // Tamanho do recorte na sprite
    flappyBird.x, flappyBird.y, // posição?
    flappyBird.largura, flappyBird.altura,  );

  } 


   else if (moveLeft && moveRight && getRandomIntegerInclusive (10,20) === 12) {   
    contexto.drawImage(
        
      sprites,
      spriteX, 160, // Sprite X, Sprite Y
      flappyBird.largura, flappyBird.altura, // Tamanho do recorte na sprite
      flappyBird.x, flappyBird.y, // posição?
      flappyBird.largura, flappyBird.altura,
      
    )} else {
    contexto.drawImage(
        
      sprites,
      spriteX, spriteY, // Sprite X, Sprite Y
      flappyBird.largura, flappyBird.altura, // Tamanho do recorte na sprite
      flappyBird.x, flappyBird.y, // posição?
      flappyBird.largura, flappyBird.altura,
      )}


};
  
    }
}



const gravidade =  function gravidade() {

 flappyBird.y = flappyBird.y  + 5
}


  const pulo =  function pulo() {
 
      flappyBird.y = flappyBird.y - 15
        flappyBird.x = flappyBird.x 
      
          gravidade();
      
    
   salto.play ();
/*
   setTimeout(() => {

  
    flappyBird.velocidade = flappyBird.velocidade + flappyBird.gravidade
   flappyBird.y = flappyBird.y + flappyBird.velocidade
   flappyBird.y = flappyBird.y + 60
    flappyBird.x = flappyBird.x + 60

  }, 200 );
*/
  }





