# Como realizar a passagem?

1 - Interpolação de texto
2 - HTML
3 - Atributos
4 - Expressões JavaScript

## Interpolação de Texto

1 - Informamos o valor do Texto na instância Vue

2 - Exibimos esse texto no HTML usando **{{ identificador }}**

## O que é um métodos?

Em poucos palavras, é uma função criada na instânia Vue

Permite realizar açoes em nossa aplicação

## Quando usar?

Interação com o usuário

Manipulação dos dados da aplicação

## Como criar ?

Usamos a propriedade **methods** da instância VUE
Podemos usar os método junto com a diretiva **v-on**

1- Métodos "estáticos". Executem uma função definifa, sem esperar parâmetros

2 - Métodos que esperam parâmetros Executam a função baseandi-se no que informado

## Computed Properties

### O que é ?

Uma maneira elegante de manipular nossos dados
Permite criar uma propriedade nova baseando-se em uma já existente

## Como Criar?

Usamos a propriedade **computed** da instância Vue

Informamos esse valor no html através de **{{computed_property}}**

## Computed Properties vs Methods

1 - Métodos realizam _ações, eventos_, Computed properties _manipulam dados_

2 - Computed Properties _ficam em cache_.
Seus valores são armazenados como sendo uma nova propriedade da intência VUe, sendo requisistados apenas uma vez.

As propriedades ..computed são armazenadas em cache com base em suas dependências. Uma propriedade computada somente reavaliará quando algumas de suas dependências forem alteradas.

Se você deseja que os dados sejam armazenados em cache, use as propriedades Computadas, por outro lado, se você não deseja que os dados sejam armazenados em cache, use propriedades simples de Método.

## set a new value for one computed properties

definir um novo valor para uma propriedade computada

## Informando um novo valor

As computed Properties geralmente apenas retornam valores. Contudo, também é possível informar um novo valor para elas

Para isso, é necessário informar um objeto para a property, e dentro dele haverá uma opção de **get** e **set**

## Watchers

## O que é?

Um recurso do Vue que nos permite "espionar" a mudança de valores de alguma propriedade

É como um "vigilante" que realiza alguma ação quando ocorre mudanças na aplicação

## Como Criar ?

Usamos a propriedade **watch** da instância Vue

Informamos dentro dela o nome da propriedade que queremos monitorar e a função a ser executada;

## Ciclo de Vida do Vue

O que é?

Série de funções que são executadas em vários pontos durante a montagem de nossa aplicação

Nos permitem executar determinado código antes, durante, e após a aplicação estar na página

## Fnções que podem ser usadas

1 - **beforeCreate()** -> Executada assim que a instância Vue é criada, mas antes de os dados , eventos e watchers estarem disponíveis
2 - **create()** -> Executada assim que a instância Vue é criada.Tem à disposição os recursos básicos:dados, computed properties, events, watchers, etc.Contudo, a aplicação ainda não foi montada.
3 - **beforeMount()** -> Executada um pouco antes do processo de montagem da aplicação começar
4 - **mounted()** -> Chamada assim que o processo de montagem é finalizado,já tem acesso à propriedade this.el, para manipular o componente.
5 - **beforeUpdate()** -> Chamada quando os dados são atualizados na página, mas antes de essas mundaças serem  refletidas no HTML
6 - **update()** -> Chamada assim que o HTML é alterado devido à mudança de dados na instância VUE
7 - **destroyed()** -> Chamada assim que a instância VUE é destruída.Nesse momento não é possível mais ter acesso aos recursos do VUE

## Como usar?

Basta informar nas propriedades da instância VUE o nome da função que queremos executar

### Exemplo

```
let app = new Vue({
    created:function(){
        console.log('A instância foi criada')
    },
    mounted: function(){
        console.log('A aplicação foi montada')
    }
})
```
