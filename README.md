# Jogo-memoria-Genius-dio
Meu primeiro Jogo na Dio 
HTML
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="style.css">
    <title>Genesis</title>
</head>
<body>
    <div class="main-game">
        <div class="genius">
            <div class="blue"></div>
            <div class="yellow"></div>
            <div class="red"></div>
            <div class="green"></div>
        </div>
    </div>
    <script type="text/javascript" src="script.js"></script>
</body>
</html>
CSS
corpo {
    margem :  0 ;
    cor de fundo :  rgb ( 208 ,  255 ,  239 );
}

. jogo principal {
    altura :  100 vh ;
    largura :  100 vw ;
    display : flex;
    justificar o conteúdo : centro;
    alinhar-itens : centro;
}

. genius {
    display : grade;
    grid-template-areas :  'verde vermelho'
    'amarelo azul' ;
    intervalo de grade :  10 px ;
    borda :  1 px sólido # ffffff ;
    cor de fundo :  # ffffff ;
    raio da borda :  100 % ;
    largura :  700 px ;
    altura :  700 px ;
}

. azul {
    área de grade : azul;
    cor de fundo : azul;
    raio da borda inferior direita :  100 % ;
}

. vermelho {
    grid-area : vermelho;
    cor de fundo : vermelho;
    raio da borda superior direita :  100 % ;
}

. amarelo {
    área da grade : amarelo;
    cor de fundo : amarelo;
    raio da borda inferior esquerda :  100 % ;
}

. verde {
    área de grade : verde;
    cor de fundo : verde;
    raio da borda superior esquerda :  100 % ;
}

. selecionado {
    opacidade :  0,8 ;
}
Javascript
deixe  ordem  =  [ ] ;
let  clickedOrder  =  [ ] ;
deixe  pontuação  =  0 ;

// 0 - verde
// 1 - vermelho
// 2 - amarelo
// 3 - azul

const  blue  =  document . querySelector ( '.blue' ) ;
const  red  =  document . querySelector ( '.red' ) ;
const  green  =  document . querySelector ( '.green' ) ;
const  amarelo  =  documento . querySelector ( ' .yellow ' ) ;

// cria ordem aletoria de cores
deixe  shuffleOrder  =  ( )  =>  {
    deixe  colorOrder  =  Math . chão ( matemática . aleatório ( )  *  4 ) ;
    pedido [ pedido . comprimento ]  =  colorOrder ;
    clickedOrder  =  [ ] ;

    para ( deixe  eu  em  ordem )  {
        let  elementColor  =  createColorElement ( order [ i ] ) ;
        lightColor ( elementColor ,  Number ( i )  +  1 ) ;
    }
}

// acende a proxima cor
deixe  lightColor  =  ( elemento ,  número )  =>  {
    número  =  número  *  500 ;
    setTimeout ( ( )  =>  {
        elemento . classList . adicionar ( 'selecionado' ) ;
    } ,  número  -  250 ) ;
    setTimeout ( ( )  =>  {
        elemento . classList . remover ( 'selecionado' ) ;
    } ) ;
}

// checa se os botoes clicados são os mesmos da ordem gerada no jogo
deixe  checkOrder  =  ( )  =>  {
    para ( deixe-  i  em  clickedOrder )  {
        if ( clickedOrder [ i ]  ! =  pedido [ i ] )  {
            gameOver ( ) ;
            pausa ;
        }
    }
    if ( clickedOrder . length  ==  order . length )  {
        alert ( `Pontuação: $ { score } \ nVocê acertou! Iniciando próximo nível!` ) ;
        nextLevel ( ) ;
    }
}

// funcao para o clique do usuario
deixe  clicar  =  ( cor )  =>  {
    clickedOrder [ clickedOrder . comprimento ]  =  cor ;
    createColorElement ( color ) . classList . adicionar ( 'selecionado' ) ;

    setTimeout ( ( )  =>  {
        createColorElement ( color ) . classList . remover ( 'selecionado' ) ;
        checkOrder ( ) ;
    } , 250 ) ;
}

// funcao que retorna a cor
deixe  createColorElement  =  ( color )  =>  {
    if ( cor  ==  0 )  {
        retornar  verde ;
    }  else  if ( color  ==  1 )  {
        retornar  vermelho ;
    }  else  if  ( color  ==  2 )  {
        retornar  amarelo ;
    }  else  if  ( color  ==  3 )  {
        return  blue ;
    }
}

// funcao para proximo nivel do jogo
deixe  nextLevel  =  ( )  =>  {
    pontuação ++ ;
    shuffleOrder ( ) ;
}

// funcao para game over
deixe  gameOver  =  ( )  =>  {
    alerta ( `Pontuação: $ { score } ! \ nVocê perdeu o jogo! \ nClique em OK para iniciar um novo jogo` ) ;
    pedido  =  [ ] ;
    clickedOrder  =  [ ] ;

    playGame ( ) ;
}

// funcao de inicio do jogo
deixe  playGame  =  ( )  =>  {
    alert ( 'Bem vindo ao Gênesis! Iniciando novo jogo!' ) ;
    pontuação  =  0 ;

    nextLevel ( ) ;
}

// eventos de clique para as cores
verde . onclick  =  ( )  =>  clique ( 0 ) ;
vermelho . onclick  =  ( )  =>  clique ( 1 ) ;
amarelo . onclick  =  ( )  =>  clique ( 2 ) ;
azul . onclick  =  ( )  =>  clique ( 3 ) ;


// inicio do jogo
playGame ( ) ;
