
# Fundamentos do Vue

## Como realizar a passagem?

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

**O que é?**

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

```dotnetcli
let app = new Vue({
    created:function(){
        console.log('A instância foi criada')
    },
    mounted: function(){
        console.log('A aplicação foi montada')
    }
})
```

## Funções usadas nos componentes

1 - **activated()** -> Chamada quando um componente com a estrutura keep-alive é ativado
2 - **deactivated()** -> Chamada quando um componente com a estrutura keep-alive é desativado
3 - **errorCaptured()** -> Chamada quando ocorre um erro em algum componente (**Novidade versão 2.5 do vue**)

## Filtro

## O que são?

Uma maneira de formatar(modelar alterar a forma) os dados que informamos em nossa página

Os dados em si não são alterados, apenas mudamos a maneira que o usuário os vê.

## Como criar?

No JavaScript, informamos a propriedade **filters** para a instância Vue. Cada filtro será uma função

No HTML, podemos aplicar um filtro a qualquer valor usando a **|** (barra vertical) e o nome do filtro

## Exemplo2

```dotnetcli

let app = new Vue({
    filter:{
        meu_filtro:function(informacao){
            //Aqui iremos formatar os dados e retorná-los
        }
    }
})
<p>{{variavel | meu_filtro}}</p>
```

## Aplicando mais de um filtro

Podemos aplicar quantos filtros desejarmos no mesmo elemento

Contudo, é importante lembrar que a parti do segundo filtro, a informação já estará formatada

## Exemplo3

```dotnetcli

let app = new Vue({
    filters:{
        meu_filtro1:function(informacao){},
        meu_filtro2:function(informacao){},
    }
})

<p>{{Variavel | meu_filtro1 | meu_filtro2}}</p> -> O filtro 2 já encontrará o dado com sua forma alterada

```

## Conhecendo uma coleção de Filtros Personalizados

nome da biblioteca no site de pacotes do npm -> vue2-filters
<https://www.npmjs.com/package/vue2-filters>

use a parte 2 **CDN**

```dotnetcli

<script src="https://cdn.jsdelivr.net/npm/vue2-filters/dist/vue2-filters.min.js"></script>

```

# Modulo 2 Diretivas

**O que é?**

"Instrução ou norma que deve orientar uma ação ou atividade"
_Diconário Priberam_

No Vue.js uma diretiva informa quais ações devem ser aplicadas a um elemento HTML

Diretivas - visão Geral

**O que é ?**

Ela é informada como um atributo HTML normal, na tag de abertura dos elementos

É prefixada com **"V-"**, que deixando claro que aquele aributo é específico do vue.

O que iremos ver

## v-if

```dotnetcli
<h1 v-if="condicao">
    Hello World
</h1>
```

## v-for

```dotnetcli
<li v-for="item in items">
    {{item}}
</li>
```

## v-bind

```dotnetcli
<a v-bind:href="propriedadeUrl">
    Hcode Treinamentos
</a>
```

## v-model

```dotnetcli
<input
type="text" v-model="propriedades">
```

## v-on

```dotnetcli
<button v-on:click="metodo">
    Aperte Aqui
</button>
```

## Diretivas Personalizadas

```dotnetcli
Vue.directive('nome-diretiva',{
    inserted:function(el,binding){
    
    }
})
```

## v-if / v-else

**Qual sua função?**

Define se uma tag deve ser exibida ou não com base em uma condição(condição simples ou expressão)

Se a condição não for atendido, o elemento é removido da tela

**Como criar?**

Informamos a condição dentro da tag com as diretivas **v-if, v-else ou v-else-if**

Exemplo: **v-if="condicao"**

Podemos definir alguma propriedade dentro da instância Vue, para ser usada na condição

***Boas Práticas**

Quando usamos v-if e v-else em elementos diferentes, é interessante adicionar o atributo key em cada um deles, evitando assim conflitos na renderização

Ex:

```dotnetcli
<div v-if="codicao" key="sucesso">
    Sucesso
</div>
<div v-else key="error">
    Erro
</div>
```

## V-show

Define se uma tag deve ser exibida ou não com base em uma condição(condição simples ou expressão)

Se a condição não for atendida, o elemento será ocultado na tela.

**Como criar?**

Informamos a condição dentro da tag com a diretiva **v-show**

Podemos definir alguma popriedade dentro da instância Vue, para ser usada na condição.

## v-if vs v-show

v-if -> **Insere ou remove** um elemento

v-show -> **Exibe ou esconde** um elemento(Muda a propriedade CSS **display** da tag)

## Quando usar um ou outro v-if

Mais lento. Exige mais do servidor pois sempre recria o elemento
Use-o quando for improvável que a condição de exibição mude constantemente

## V-text

**Qual sua função?**

Exibir o valor de uma propriedade da instância Vue no HTML

Tem a mesma função das chaves duplas **{{propriedade}}**

**Como criar?**

Informamos o nome da propriedade na diretiva **v-text**
Exemplo:**v-text="propriedade"

É necessário criar uma propriedade com o mesmo nome na instância Vue.

## V-html

**Qual a função?**

Interpretar e exibir o valor HTML puro vindo de uma propriedade da instância Vue(Não é interpretado como um template Vue)
Altera a propriedade **innerHTML** de uma tag

**Como Criar?**

Informamos o nome da propriedade na diretiva **v-html**
Exemplo: **v-html="propriedade"**

É necessário criar uma propriedade com o mesmo nome na instância VUE, contendo o HTML que queremos exibir

## Cuidados

Renderização dinêmica de HTML é uma porta aberta para ataques XSS
Use essa diretiva em ambientes seguros e com cautela

## v-once

***Qual sua função**

Exibir o valor de uma propriedade da instância Vue apenas _uma vez_
Deixe o elemento estático, pode ajudar na performance

"criptonita da vue"
***Como criar?**

Informamos a diretivas **v-once** na Tag que desejamos deixar estático
(não espera parâmetros)
***EXEMPLO**

```dotnetcli
<a v-once>{{propriedade}}</a>
```

***v-for**

## Qual sua função?

Exibir uma quantidade maior de informação, levando em conta uma lista de propriedades
Usado para percorrer um array ou objeto com esses valores e exibir em uma tag repetidas vezes

**Como criar?**

Informamos a diretiva **v-for** na tag que desejamos repetir
Exemplo: **v-for="intem in propriedade**

Podemos acessar também o índice do array ou o nome da propriedade objeto

## Boa Práticas

É essencial usar um atributo Key quando trabalharmos com o v-for

Ex.:

```dotnetcli
<li v-for="movie in films" :key="movie.id">
    {{ movie.name }}
</li>
```

Nunca use o v-if com o v-for, pois isso pode gerar conflitos de renderização. é melhor adicionar o v-if em um elemento pai

Ex.:

```dotnetcli
<div v-if="condicao">
    <h2 v-for="name in persons">{{name}}</h2>
</div>
```

## V-bind

**Qual sua função?**

Vincular o valor de qualquer propriedade a uma variável do VUE
Com isso podemos fazer com que importantes atributos como href, src, class, etc. Se tornem dinâmicos

**Como criar?**

Informamos a diretiva **v-bind** na tag que desejamos informar o atributo
Exemplo:**v-bind:href="linkSite"**

Essa diretiva possui uma forma abreviada de ser chamada, apenas informando **:**(dois-pontos) e o atributo que queremos tornar dinâmico
Exemplo: **:src="imgSrc"**

## Boas práticas

É importante manter um padrão quando chamamos a forma abreviada das deretivas

Se chamarmos uma forma abreviada,devemos usá-la sempre no contexto, mas não misturá-la com a forma convenional

Ex.:

```dotnetcli
<input
v-bind:value="valor"
:placeholder="valor2"
>
```

# Argumentos Dinâmicos

## Essa é uma novidade da versão 2.6 do Vue

Agora também é possével informar os argumentos para a diretiva de maneira dinâmica,se baseando em uma propriedade da instância Vue

Para isso, basta informar **[]**(chaves) no lugar de um argumento

Exemplo:**v-bind:[propriedade]="valor"**


