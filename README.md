# VEJAM O VÍDEO DO PROJETO COMO FICOU.



https://github.com/user-attachments/assets/86a3e428-669e-466b-8963-2fd5023617b2

# Explicação basica do projeto.
##  Definição dos Emojis
```
const emojis = ["😂", "😂", "🥰", "🥰", "😍", "😍", "🤑", "🤑", "😡", "😡", "🥶", "🥶", "😻", "😻", "💘", "💘"];

```
- emojis: É um array contendo os emojis que serão usados no jogo. Cada emoji aparece duas vezes, formando os pares que os jogadores devem encontrar.
  ## Embaralhamento dos Emojis
  ```
  let shuf_emojis = emojis.sort(() => (Math.random() > .5) ? 2 : -1);

  ```
  - shuf_emojis: É um novo array contendo os emojis embaralhados. A função sort() com o argumento (Math.random() > .5) ? 2 : -1 faz com que a ordem dos elementos no array seja randomizada. Math.random() gera um número entre 0 e 1; quando é maior que 0.5, o elemento é movido para cima na ordem, caso contrário, é movido para baixo.
  ## Passo a Passo do Embaralhamento:
  - Função sort():

- O método sort() é usado para ordenar os elementos de um array. Normalmente, ele aceita uma função de comparação como argumento, que determina a ordem dos elementos.
- Função de Comparação () => (Math.random() > .5) ? 2 : -1:
- Dentro do sort(), passamos uma função anônima que será usada para comparar dois elementos do array.
- A função de comparação deve retornar:
- Um valor positivo se o primeiro elemento deve ser posicionado depois do segundo.
- Um valor negativo se o primeiro elemento deve ser posicionado antes do segundo.
- Um valor zero se a ordem dos dois elementos não deve ser alterada.
- Math.random():

- O Math.random() gera um número aleatório de ponto flutuante entre 0 (inclusivo) e 1 (exclusivo). Ou seja, ele retorna um número no intervalo [0, 1).
- Como esse número é aleatório, ele será maior que 0,5 em aproximadamente 50% das vezes e menor ou igual a 0,5 nas outras 50% das vezes.
- Comparação (Math.random() > .5):

- A expressão Math.random() > .5 é uma condição booleana.
- Quando Math.random() retorna um valor maior que 0,5, a expressão resulta em true. Caso contrário, resulta em false.
- Operador Ternário ? ::

- A condição (Math.random() > .5) é usada em um operador ternário:
- Se a condição for true (ou seja, se Math.random() for maior que 0,5), a expressão retorna 2.
- Se a condição for false (ou seja, se Math.random() for menor ou igual a 0,5), a expressão retorna -1.
- Efeito na Função sort():

- Cada vez que o sort() compara dois elementos, a função (Math.random() > .5) ? 2 : -1 é chamada.
- Se a função retorna 2, significa que o primeiro elemento deve ser movido depois do segundo, promovendo uma troca na ordem dos elementos.
- Se a função retorna -1, significa que o primeiro elemento deve ser mantido antes do segundo, não trocando sua posição relativa.
- Resultado do Embaralhamento:
- Como a comparação é baseada em valores aleatórios, a ordem dos elementos no array emojis é aleatoriamente reorganizada.
- Cada comparação entre dois elementos tem uma chance de 50% de resultar em uma troca de posição, o que efetivamente embaralha os emojis de maneira não determinística.
- Possíveis Ajustes e Considerações:
- Retorno de valores 2 e -1: Embora o retorno dos valores 2 e -1 funcione, é mais comum ver 1 e -1 usados para indicar a ordem, pois esses são os valores padrões esperados para indicar posições relativas em muitos casos de ordenação.
- Imprecisão: Esse método de embaralhamento é uma abordagem rápida, mas não é ideal para embaralhamentos altamente precisos em todos os contextos. Para um embaralhamento perfeitamente justo, uma abordagem como o algoritmo de Fisher-Yates (ou Array.prototype.sort(() => 0.5 - Math.random()), que é mais comum e intuitiva) é recomendada.
- Resumo
- A linha let shuf_emojis = emojis.sort(() => (Math.random() > .5) ? 2 : -1); utiliza o método sort() para embaralhar aleatoriamente os elementos do array emojis, baseando-se em comparações que retornam valores aleatórios (2 ou -1). Isso cria um array embaralhado, onde a posição de cada emoji é decidida aleatoriamente.
## Criação das Cartas do Jogo.
```
for(let i = 0; i < emojis.length; i++){
    let box = document.createElement("div");
    box.className = "item";
    box.innerHTML = shuf_emojis[i];

```
- for(let i = 0; i < emojis.length; i++): Um loop que itera sobre cada emoji no array emojis.
- document.createElement("div"): Cria um novo elemento div para cada carta.
- box.className = "item";: Define a classe do elemento div como "item", aplicando os estilos CSS correspondentes.
- box.innerHTML = shuf_emojis[i];: Define o conteúdo HTML da carta para o emoji correspondente do array embaralhado.
## Explicação Dinâmica e Detalhada:
- for(let i = 0; i < emojis.length; i++):
- Tipo de Estrutura: Este é um loop for.
- Início do Loop: let i = 0 inicia a variável i em 0.
- Condição de Continuação: O loop continua a rodar enquanto i < emojis.length for verdadeiro, ou seja, enquanto i for menor que o tamanho do array emojis. Como o array emojis tem 16 elementos, o loop rodará 16 vezes.
- Incremento: i++ significa que i é incrementado em 1 a cada iteração do loop. Isso permite que o loop avance por cada índice do array shuf_emojis.
- Contexto Visual: Imagine que você tem uma linha de produção que precisa colocar etiquetas (os emojis) em 16 caixas. Este loop é o processo de você passar por cada uma das caixas, uma por uma, e adicionar a etiqueta correspondente.
- let box = document.createElement("div");:
- Criação do Elemento: document.createElement("div") cria um novo elemento HTML <div>.
- Armazenamento na Variável box: Esse novo elemento div é armazenado na variável box a cada iteração do loop.
- Visualizando: Imagine que cada vez que você vai para uma nova posição na linha de produção (cada iteração do loop), você recebe uma nova caixa vazia (o div) para trabalhar.
- Detalhe Importante: Cada div criado aqui é independente dos outros. Mesmo que eles sejam gerados dentro de um loop, cada div é um novo e separado elemento na memória.
- box.className = "item";:
- Aplicação de Classe CSS: box.className = "item" atribui a classe "item" ao novo elemento div.
- Por que é importante?: Essa classe "item" está ligada ao CSS que você definiu antes. Ela provavelmente define o estilo visual do elemento, como tamanho, cor de fundo, e comportamento ao ser clicado.
- Visualizando: É como se você estivesse etiquetando a caixa na linha de produção, não com um emoji ainda, mas com um rótulo que diz "Este é um item do jogo". Essa etiqueta faz com que a caixa saiba como ela deve ser apresentada.
- box.innerHTML = shuf_emojis[i];:
- Preenchimento do Conteúdo: box.innerHTML = shuf_emojis[i] insere o emoji correspondente (o elemento shuf_emojis[i]) dentro do div que acabou de ser criado.
- Índice Atual: shuf_emojis[i] obtém o emoji do array embaralhado shuf_emojis na posição i.
- Visualizando: Agora, você está colocando o emoji (a etiqueta visual) dentro da caixa que você preparou. Este é o passo onde a caixa que foi estilizada antes finalmente ganha seu conteúdo visual.
- Detalhe Importante: O innerHTML define o conteúdo HTML dentro de um elemento, e como estamos lidando com emojis (caracteres simples), essa é uma maneira eficiente de inserir texto ou símbolos em um elemento.
- Resumo:
- Esse bloco de código percorre cada emoji no array shuf_emojis (que foi previamente embaralhado), cria uma nova caixa (div) para cada emoji, aplica um estilo padrão a essa caixa através da classe "item", e finalmente, insere o emoji correspondente dentro da caixa. Ao final do loop, você terá um conjunto de 16 elementos div, cada um contendo um emoji único, prontos para serem inseridos no jogo da memória.
### Vamos detalhar o evento de clique (onclick) e as verificações de correspondência (if) no código. Essa parte é fundamental para o funcionamento do jogo da memória, onde os jogadores tentam encontrar pares correspondentes de emojis.
```
box.onclick = function() {
    this.classList.add('boxOpen');
    setTimeout(function(){
        if(document.querySelectorAll(".boxOpen").length > 1){
            if(document.querySelectorAll(".boxOpen")[0].innerHTML == document.querySelectorAll(".boxOpen")[1].innerHTML){
                document.querySelectorAll(".boxOpen")[0].classList.add('boxMatch')
                document.querySelectorAll(".boxOpen")[1].classList.add('boxMatch')

                document.querySelectorAll(".boxOpen")[1].classList.remove('boxOpen')
                document.querySelectorAll(".boxOpen")[0].classList.remove('boxOpen')

                if(document.querySelectorAll(".boxMatch").length == emojis.length){
                    alert("Win")
                }
            } else {
                document.querySelectorAll(".boxOpen")[1].classList.remove('boxOpen')
                document.querySelectorAll(".boxOpen")[0].classList.remove('boxOpen')
            }
        }
    }, 500);
};

```
## 1 Definição do Evento de Clique:
```
box.onclick = function() {...}

```
- box.onclick = function() {...}: Define um manipulador de evento para o clique em cada carta (box). Quando uma carta é clicada, a função anônima que segue é executada.
- Visualização: Imagine que cada vez que você clica em uma carta, você ativa uma série de ações que determinam o que acontecerá a seguir com essa carta.
## 2 Abrir a Carta:
```
this.classList.add('boxOpen');

```
- this.classList.add('boxOpen');: Adiciona a classe "boxOpen" à carta que foi clicada. this refere-se ao elemento div (box) que foi clicado.
- Efeito: No CSS, a classe "boxOpen" provavelmente faz com que a carta "vire" (revele o emoji escondido). Isso acontece porque o CSS muda a rotação ou a opacidade da carta, exibindo o emoji.
- Visualização: Quando você clica em uma carta, ela "vira", revelando o emoji dentro dela.
## 3 Usando setTimeout para Atrasar a Verificação:
```
setTimeout(function(){ ... }, 500);

```
- setTimeout(function(){ ... }, 500);: Cria um atraso de 500 milissegundos (0,5 segundos) antes de executar a próxima parte do código.
- Por que usar setTimeout?: Isso dá ao jogador tempo para ver o emoji que foi revelado antes de fazer qualquer verificação de correspondência. Sem esse atraso, a verificação e as ações poderiam acontecer instantaneamente, sem que o jogador tivesse tempo de processar a informação visual.
- Visualização: Depois que uma carta é virada, o jogo "espera" por meio segundo para ver se você virou outra carta antes de continuar.
## 4 Verificar se Duas Cartas Estão Viradas:
```
if(document.querySelectorAll(".boxOpen").length > 1) {...}

```
- document.querySelectorAll(".boxOpen").length > 1: Verifica se mais de uma carta (ou seja, duas) está virada. Isso é feito selecionando todos os elementos com a classe "boxOpen" e verificando quantos estão presentes.
- Por que isso é importante?: O jogo só precisa verificar correspondência quando duas cartas estão viradas.
- Visualização: Quando duas cartas são viradas, o jogo se prepara para verificar se elas correspondem.
## 5 Verificar Correspondência dos Emojis:
```
if(document.querySelectorAll(".boxOpen")[0].innerHTML == document.querySelectorAll(".boxOpen")[1].innerHTML) {...}

```
- Comparação: O código verifica se o conteúdo (o emoji) das duas cartas viradas é igual.
- document.querySelectorAll(".boxOpen")[0].innerHTML obtém o conteúdo da primeira carta virada, e document.querySelectorAll(".boxOpen")[1].innerHTML obtém o conteúdo da segunda.
- Visualização: Depois que duas cartas foram viradas, o jogo olha para os emojis em cada uma delas para ver se são iguais.
## 6 Se as Cartas Correspondem:
```
document.querySelectorAll(".boxOpen")[0].classList.add('boxMatch')
document.querySelectorAll(".boxOpen")[1].classList.add('boxMatch')

document.querySelectorAll(".boxOpen")[1].classList.remove('boxOpen')
document.querySelectorAll(".boxOpen")[0].classList.remove('boxOpen')

```
- Adicionar Classe boxMatch: Se os emojis correspondem, a classe "boxMatch" é adicionada a ambas as cartas.
- Efeito da Classe boxMatch: Provavelmente, essa classe mantém as cartas "viradas" permanentemente, indicando que foram correspondidas corretamente.
- Remover Classe boxOpen: A classe "boxOpen" é removida das cartas, pois elas agora não precisam mais ser consideradas "abertas" para novas verificações.
- Visualização: Se as duas cartas combinam, elas permanecem viradas e são marcadas como "correspondidas" no jogo.
## Verificar se Todas as Cartas Foram Correspondidas:
```
if(document.querySelectorAll(".boxMatch").length == emojis.length) {
    alert("Win");
}

```
- Verificação de Vitória: Se o número de cartas correspondidas (boxMatch) for igual ao número total de emojis, o jogador venceu o jogo.
- alert("Win"): Exibe uma mensagem de vitória.
- Visualização: Se todos os pares foram encontrados, o jogo declara o jogador como vencedor.
## Se as Cartas Não Correspondem:
```
document.querySelectorAll(".boxOpen")[1].classList.remove('boxOpen')
document.querySelectorAll(".boxOpen")[0].classList.remove('boxOpen')

```
- Remover Classe boxOpen: Se os emojis não correspondem, a classe "boxOpen" é removida de ambas as cartas, o que faz com que elas "virem" de volta, ocultando os emojis.
- Visualização: Se as cartas não combinam, elas voltam ao estado inicial, prontas para uma nova tentativa.

# Código Reestruturado e Limpo:
```
box.onclick = function() {
    // Adiciona a classe 'boxOpen' à caixa clicada
    this.classList.add('boxOpen');
    
    // Atraso antes da verificação
    setTimeout(function() {
        // Seleciona todas as caixas abertas
        const openBoxes = document.querySelectorAll(".boxOpen");
        
        // Verifica se há mais de uma caixa aberta
        if (openBoxes.length > 1) {
            // Obtém os emojis das duas caixas abertas
            const firstBox = openBoxes[0];
            const secondBox = openBoxes[1];
            const firstEmoji = firstBox.innerHTML;
            const secondEmoji = secondBox.innerHTML;
            
            // Verifica se os emojis correspondem
            if (firstEmoji === secondEmoji) {
                // Se os emojis correspondem, adiciona a classe 'boxMatch' e remove 'boxOpen'
                firstBox.classList.add('boxMatch');
                secondBox.classList.add('boxMatch');
                
                // Remove a classe 'boxOpen'
                firstBox.classList.remove('boxOpen');
                secondBox.classList.remove('boxOpen');
                
                // Verifica se todas as caixas foram correspondidas
                const matchedBoxes = document.querySelectorAll(".boxMatch");
                if (matchedBoxes.length === emojis.length) {
                    alert("Win");
                }
            } else {
                // Se os emojis não correspondem, remove a classe 'boxOpen' das duas caixas
                firstBox.classList.remove('boxOpen');
                secondBox.classList.remove('boxOpen');
            }
        }
    }, 500);
};

```
## Detalhes da Reestruturação:
- Criação de Variáveis:

- openBoxes: Armazena todas as caixas que estão abertas no momento.
- firstBox e secondBox: Representam as duas caixas abertas que serão comparadas.
- firstEmoji e secondEmoji: Contêm os emojis das duas caixas abertas.
- Estrutura Condicional:

- Verificação de Quantidade de Caixas Abertas: Usa openBoxes.length > 1 para garantir que apenas dois emojis sejam comparados.
- Comparação de Emojis: Compara firstEmoji e secondEmoji para verificar se são iguais.
- Classificação e Remoção: Adiciona a classe "boxMatch" para pares correspondidos e remove "boxOpen" para atualizar o estado visual das caixas.
- Verificação de Vitória:

- matchedBoxes: Conta o número total de caixas com a classe "boxMatch" para verificar se todas as caixas foram correspondidas.
- Manutenção e Legibilidade:

- Variáveis Nomeadas: Usar variáveis nomeadas melhora a legibilidade e facilita a compreensão do que cada parte do código está fazendo.
- Comentários: Comentários ajudam a explicar o propósito de cada bloco de código, facilitando a compreensão e a manutenção.

- 
# Uma explicação do css resumida:
##  Botão de Reset (.reset)
```
.reset {
    padding: 15px 20px;
    color: #267c65;
    background: #fff;
    border: none;
    font-size: 1.5em;
    letter-spacing: 0.1em;
    text-transform: uppercase;
    cursor: pointer;
    font-weight: 600;
}
.reset:focus {
    color: #fff;
    background: #267c65;
}

```
- padding: 15px 20px;: Adiciona preenchimento interno ao botão.
- color: #267c65; background: #fff;: Define a cor do texto e o fundo do botão.
- border: none;: Remove qualquer borda padrão.
- cursor: pointer;: Altera o cursor para uma mão quando o botão é focado ou clicado.
- font-weight: 600;: Aumenta a espessura do texto.
- focus: Quando o botão está em foco (por exemplo, após ser clicado), inverte as cores, definindo o fundo como verde e o texto como branco.
## Área do Jogo (.game)
```
.game {
    width: 430px;
    height: 430px;
    display: flex;
    flex-wrap: wrap;
    gap: 10px;
    transform-style: preserve-3d;
    perspective: 500px;
}

```
- transform-style: preserve-3d;: Define que os filhos do contêiner .game (as cartas) devem preservar seu contexto 3D ao serem transformados, permitindo efeitos 3D (como rotação) que pareçam realistas.
- perspective: 500px;: Define a profundidade da perspectiva 3D, criando um efeito de distanciamento ou proximidade quando os elementos são rotacionados. Quanto menor o valor, mais acentuada será a percepção da profundidade.
## Cartas do Jogo (.item)
```
.item {
    position: relative;
    width: 100px;
    height: 100px;
    display: flex;
    justify-content: center;
    align-items: center;
    font-size: 3em;
    background: #fff;
    transition: 0.25s;
    transform: rotateY(180deg);
}

```
- position: relative;: Permite que elementos filhos absolutamente posicionados (como pseudo-elementos) sejam posicionados em relação a esta carta.
- width e height: Define o tamanho de cada carta (100x100 pixels).
- display: flex; justify-content: center; align-items: center;: Centraliza o conteúdo (provavelmente um símbolo ou número) dentro da carta.
- font-size: 3em;: Define um tamanho de fonte grande para o conteúdo da carta.
- background: #fff;: Define a cor de fundo das cartas como branca.
- transition: 0.25s;: Adiciona uma transição suave para todas as propriedades que mudarem, durando 0,25 segundos.
- transform: rotateY(180deg);: Rotaciona a carta 180 graus ao longo do eixo Y, fazendo com que ela pareça virada de costas inicialmente.
## Cartas Abertas (.item.boxOpen)
```
.item.boxOpen {
    transform: rotateY(0deg);
}

```
- transform: rotateY(0deg);: Quando a classe boxOpen é adicionada a uma carta, a rotação Y é removida (0 graus), fazendo com que a carta "vire" para o lado da frente.
## Efeito de Pseudo-elemento (.item::after)
```
.item::after {
    content: '';
    position: absolute;
    inset: 0;
    background: #209d7b;
    transition: 0.25s;
    transform: rotateY(0deg);
    backface-visibility: hidden;
}

```
- content: '';: Cria um pseudo-elemento vazio, utilizado para estilização adicional (neste caso, o fundo da carta).
- position: absolute; inset: 0;: Posiciona o pseudo-elemento para preencher completamente a carta (inset: 0; é uma abreviação para top: 0; right: 0; bottom: 0; left: 0;).
- background: #209d7b;: Define a cor de fundo do pseudo-elemento (um verde mais claro).
- transition: 0.25s;: Adiciona uma transição suave para as mudanças de estilo.
- transform: rotateY(0deg);: Mantém o pseudo-elemento "de frente".
- backface-visibility: hidden;: Esconde a face traseira do pseudo-elemento, garantindo que ele não seja visível quando a carta estiver virada.
## Cartas Correspondentes (.boxMatch:after, .boxOpen:after)
```
.boxMatch:after,
.boxOpen:after {
    transform: rotateY(180deg);
}

```
- transform: rotateY(180deg);: Quando a classe boxMatch ou boxOpen é adicionada, o pseudo-elemento é rotacionado em 180 graus, exibindo a frente da carta. Isso cria o efeito de virar a carta para revelar seu conteúdo.


