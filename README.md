# projeto-de-circuitos
projeto de circuito digital

INTRODUÇÃO:
  O jogo "Guess the number" de adivinhação é uma atividade em que um jogador tenta adivinhar um número de 4 bits escolhido aleatoriamente.
Cada jogador terá a chance de fazer um palpite, e o jogo fornecerá informações sobre se o número chutado está próximo do número aleatório
por meio de um sistema de temperatura indicada por um led. O jogador ganha se acertar o número escondido.
  Utilizando o aplicativo "Logisim", nossa equipe, da Universidade Federal do Cariri, formada pelas alunas: Ana Luísa Gonçalves Cordeiro,
Anelysa Almeida de Lima e Asline Nadila Silva Bezerra, orientada pelo professor Ramon Nepomuceno, da disciplina de Circuitos Digitais, no
curso de Ciências da Computação, juntamente com nosso monitor Luis Fagner, produziu este jogo disponível neste repositório.
  Esta pasta contém a versão oficial do jogo e algumas de suas partes avulsas, cada uma das quais será detalhada abaixo.

-DECODER:
  O decoder (decodificador) para display de 7 segmentos é um componente que traduz um valor binário em sinais visuais(sistema hexadecimal) 
Ele recebe uma entrada de 4 bits (que representa números de 0 a 15 em binário) e a converte em 7 saídas individuais, que por sua vez,
controlam um led por circuito. 
  Fizemos baseado na tabela-verdade que construímos.

-COMPLEMENTO DE 2 E SOMADOR:
  Em sistemas digitais, o complemento de dois é utilizado para representar números inteiros negativos em binário, usando uma técnica que
consiste em primeiro inverter os valores lógicos de cada bit e em seguida somar 1 ao resultado. Já o somador é dividido entre Half Adder
e Full Adder, para sua montagem é necessário que o Full Adder seja conectado em sequência para formar somadores de múltiplos bits, nesse
projeto serão apenas 4, este somador recebe o resultado do complemento de 2 em uma de suas entradas. Por meio desse sistema é realizada a
diferença entre o número digitado pelo usuário e o que ele deve adivinhar.

-MULTIPLEXADOR:
  O multiplexador (MUX) funciona como uma chave seletora no circuito.
  Orientado pelo Comparador de Magnitude ele conduz qual circuito deve passar para análise.
  No "guess the number" usamos o multiplexador com duas entradas de 4 bits (entrada 0: palpite; entrada 1: número secreto) e um controle
simples de 1 bit com sinal entendido para 4 bits.
  O mux é usado no circuito somador.

-COMPARADOR DE MAGNITUDE:
  O comparador de magnitude tem como finalidade saber se duas entradas de 4 bits são iguais, ou se foram diferentes qual é a maior e qual
  a menor. 
  O circuito do comparador tem duas entradas de 4 bits e cada bit é separado de acordo com a sua significância, então o bit mais
importante da primeira entrada fica associado ao bit mais importante da outra entrada e assim sucessivamente, essa associação de bits é
feita com portas XNOR, porque se elas os bits foram iguais vale 1 que vai ser necessários para todo o circuito essa comparação. Para 
saber se são iguais todas as saídas das portas XNOR são associadas a uma porta AND, então se todas as as entradas forem 1 logo a saída é 
1, que no caso significa que as entradas são iguais. Se não for verdade passa pra as próximas comparações, que no caso comparando a 
primeira como maior que a segunda para isso fazemos as comparações do bit mais significativo e assim sucessivamente, então usamos a porta
AND negando a segunda entrada pois se a3=1 e b3=0 logo a3>b3, e o resto das portas é usando a mesma lógica só que pegando a comparação 
feita pra saber se eles são iguais, como na seguinte porta depois do bit mais significativo que possui três entradas, uma sendo a 
comparação de igualdade do bit anterior, outra sendo a entrada de a e negando a entrada de b a partir da mesma lógica passada, logo se
a3=b3, a2=1 e b2=0, a associação a porta AND será igual a 1. 
  O resto das entradas é feita a partir da mesma ideia, só acrescentando a comparação de igualdade. A partir dessas comparações é 
possível saber se a>b, juntando todas as saídas dessas portas AND em uma porta OR, pois se umas das entradas for 1, logo a>b. Para saber 
se a<b é usado a mesma lógica só que invertendo a negação que no caso vai ser do a, usando como exemplo a primeira porta AND de bit de 
mais valor, que se a3=0 e b3=1, logo b>a. Esse circuito vai ser importante pois ele vai receber o palpite e o número aleatório, e a
partir do circuito ele vai descobrir se é igual, se não, ele será importante pra saber se está perto ou longe.

-CIRCUITO CORES:
  A aplicação do circuito cores no "Guess the Number" serve para que as cores mudem conforme o palpite se aproxima do número secreto. O 
circuito somador envia o módulo da distancia para o cores com o objetivo de obter a "distância". A partir do resultado da comparação e 
considerando a constante f =1, o circuito seleciona a combinação de bits correspondente às cores exibidas, permitindo a sinalização 
visual do estado do jogo.
Assim, a porta NOT é utilizada para fazer com que as duas saídas de cores sejam complementares: quando uma cor está ativa, a outra fica desativada. Isso impede que os LEDs vermelho e azul sejam acionados simultaneamente.

