
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

## v- model

**Qual sua função?**

Realizar uma ligação de dados bidirecional
(two-way data binding)

Com isso, ao alterar o valor de uma propriedade na camada view, também estaremos alterando o valor original desta mesma
propriedade

## ONDE PODEMOS USAR?

```dotnetcli
1 - tag <input>
2 - tag <slect>
3-  tag <textarea>
4 - Componentes
```

**Como Criar?**

Informamos a diretiva **v-model** na tag que desejamos realizar o two-way data binding

Exemplo: 

```dotnetcli
<input type="text" v-model="message">
```

## Modificadores

Modificadores são propriedades que podemos informar junto com o **v-model**. Elas são função específicas, que podem ser muito úteis

1 - **.number** -> Transforma o valor da propriedade de string para número

2 - **.trim** -> Remove os espaços antes e depois da propriedade

3 - **.lazy** - Definimos que os eventos de mudanças(change) serão ouvidos

## V-on

**Qual sua função?**

1 - Criar um ouvinte de evento.Isso é importante para que a aplicação fique mais reativa

2 - Criar eventos personalizados, principalmente no contexto de componentes

**Como criar?**

Informamos a diretiva **v-on** na tag que desejamos aplicar o evento,
junto com o nome dele
Exemplo.: **V-on:click="metodo"**

Essa diretiva possui uma forma abreviada de ser chamada,apenas informando **@**(arroba) e o 
nome do evento que queremos definir
Exemplo.:**@keyup="metodo"

***Boas práticas**

É importante manter um padrão quando chamarmos a forma abreviada das diretivas

Se chamarmos uma forma abreviada, devemos usá-la sempre no contexto, mas não misturá-la com a forma convencional

Ex.:

```dotnetcli
<input
    v-on:mouseenter="method1"
    @click
>
```

### O que podemos informar para a diretiva?

1 - O nome de um método
**v-oon:click="nomeMetodo"**

2 - Uma expressão JavaScript
**@click="alert('Hello World')"**

3 - Até mesmo não informar nada, se estivermos usando um modificador
**@click.prevent**

Argumentos Dinâmicos

***Essa é uma novidade da versão 2.6 do Vue**

Agora também é possível informar os argumentos para a diretiva de maneira dinâmica,
se baseando em uma propriedade da instância Vue

Para isso, basta informar **[]**(chaves) no lugar de um argumento

Exemplo.: **v-on:[proprieddade]="metodo"

## V-slot

***Qual sua função?**

Diretiva usada com componentes

Usada para inserir conteúdo em um componente, através da tag **<temple>**

***Como criar?**

Informamos a diretiva **v-slot** no elemento que desejamos adiciona conteúdo, junto com seu
nome como argumento
Exemplo:**v-slot:div**

Essa diretiva possui uma forma abreviada de ser chamada, apenas
informando **#**(hashtag) e o nome do slot que queremos definir
Exemplo:**#footer**

***Boas práticas**

É importante manteer um padrão quando chamarmos a forma abreviada das diretivas

Se chamarmos uma forma abreviada,devemos usá-la convencional

Ex.:

```dotnetcli
<templete v-slot:cabecalho>

<template #site>
```

## V-pre

***Qual sua função?**

Desibilitar a compolação VUE no elemento em que for aplicado

O Vue deixa de funcionar no elemento específico

***Por que usar?**

1 - Se desejarmos exibir as chaves de interpolação de variável no navegador

2 - Se desejarmos aumentar a performance para renderizar nossa aplicação

***Como ciar?**

Informamos a diretiva **v-pre** na tag que desejamos desabilitar
Exemplo:

```dotnetcli
<h2 v-pre>{{name}}</h2>
```

Essa diretiva não espera nenhum argumento
O exemplo acima irá imprimir no navegador

{{ name }}

## V-cloak

***Qual sua função?**

Garantir que os elementos serão exibidos apenas quando a instância Vue
for completamente carregada

Evitar que a página fique desestruturada ("quebrada) enquanto ocorre o carregamento

***Comocriar?**

Informamos a diretiva **v-cloak na tag que desejamos aplicar a inteligênia de espera
Exemplo:

```dotnetcli
<h1 v-cloak>Seja bem-vindo {{ name }}</h1>
```

Essa diretiva não espera argumentos

## A importância do CSS

Para um funcionamento completo, é necessário
adicionar um estilo CSS em nosso código, ocultando o elemento até o carregamento da página

```dotnetcli
[v-cloak]{
    display:none;
}
```

# Criando Diretivas Personalizadas

***Quando é necessário?**

Em algumas situações. talvez as diretivas padrão do Vue não atendam
à nossa necessidade

Nesses casos podemos criar nossas próprias diretivas

***Como criar?**

1 - Globalmente
**Vue.directive('nome-diretiva',{})

2 - Localmente
new Vue({
    directives:{}
})

Exemplo

```dotnetcli
Vue.directive('white',{
    inserted:function(elemento){
        elemento.style.color ='white'
    }
})

<p v-white>Hello Hcode.</p>
```

## Possíveis Funções ao Criar uma Diretiva

```dotnetcli
1 - bind() -> Chamada quando a diretiva é vinculada a um elemento
2 - inserted() -> Chamada quando o elemento vinculado é inserido no DOM
3 - update() -> Chamada quando o elemento pai do elemento vinculado é atualizado
4 - unbind() -> Chamada quando a diretiva é desvinculada de um elemento
5 - componentUpdate() -> Chamada quando o componente é atualizado
```

Exemplo

```dotnetcli
Vue.directive('nome-diretiva',{
    bind:function(elemento){
        consolw.log('Fui vinculada a um elemento')
    },
    unbind:function(elemento){
        console.log('Fui desvinculada de um elemento')
    }
})
```

Parâmetros

```dotnetcli
1 - el -> Elemento que a diretiva está vinculada
2 - binding -> Um objeto que traz informações úteis, como
o valor informado para a diretiva(value), o valor
antigo(oldValue) e os modificadores(modifiers)
3 - vnode -> O nó HTML virtual produzido pelo Vue
4 - oldVnode -> O nó HTML virtual antigo(só terá um valor se estivermos nas funções update() ou componentUpdate())
```

Exemplo

```dotnetcli
Vue.directive('nome-diretiva',{
    bind:function(el,binding){
        console.log(`O valor informado foi ${binding.value}`)
    }
})
```

# Todas as opções da variável binding

```dotnetcli
1 - name -> Nome da diretiva, sem o prefixo "v-"
2 - value -> Valor informado para a diretiva
3 - oldValue -> Valor antigo da variável, se ela possuir
4 - expression -> Expressão JavaScript infromada para a diretiva
5 - modifiers -> Um objeto com todos os modificadores informados. Eles são identificados por meio do **.**(ponto)
.Ex.: <p v-native.mod1>. Será retornado "{mod1:true}"
6 - arg -> Se informarmos algum argumento para a diretiva com **:**(dois-pontos),ele será exibido aqui.Ex.:
<img v-blank:argumento>.Será retornado "argumento"
```

## Argumento dinâmicos

Assim como as diretivas v-bind e v-on, podemos criar argumentos dinâmicos, vindos da instância Vu, 
e adicioná-los às nossas diretivas
personalizadas

Exemplo

```dotnetcli
new Vue({
    data:{
        name:'argumento'
    }
})

<div v-star:[name]>May the force be with you</div>
```

## Recebemos vários valores

É possível receber mais de um valor para nossa diretiva

Para isso, basta informar um objeto para ela

Exemplo

```dotnetcli
new Vue({
    directives:{
        edit-text:{
            inserted:function(el,binding){
                console.log(binding.value.size);
                console.log(binding.value.color)
            }
        }
    }
})

<h2 v-edit-text="{size:10,color:'red'}">Vue.js is Awesome</h2>
```

# Estilização em  linha

```dotnetcli
<span v-bind:style="{fontSize:tamanho + 'px'}">
    Hcode Treinamentos
</span>
```

## Porque usar?

Uma página bem estilizada fica mais interesante de se acessar

Por isso, o vue nos oferece vários recursos para estilização

## Estilização com Classes

```dotnetcli
<ul>
    <li v-bind:class="{active:isActive}">
        Spider-Man
    </li>
</ul>
```

***Por que usar?**

Facilitar a definição de estilos css em nossa aplicação

Informar estilos de maneira dinâmica

***Maneiras de criar**

1 - Usando objestos
2 - Usando arrays

***Objestos**

Informamos a diretiva **v-bind:style**
na tag que desejamos estilizar

Obs.: Podemos usar o padrão camelCase no nome das propriedades Css

### Exemplos

```dotnetcli
<p v-bind:style="{ fontFamily:propriedade}">Hcode Treinamentos</p>

<div v-bind:style="propriedade_objeto">Vue.js</div>

data:{
    propriedade_objeto:{
        fontSize:'20px'
    }
}
```

## Estilos com mútiplos valores

# Múltiplos valores

***Novidade versão 2.3 do Vue**

Em alguns casos, podemos trabalhar com estilos CSS que podem ter mais de um valor

Para isso,informamos um array com os valores, ainda usando a diretiva v-bind:style

***Exemplos**

```dotnetcli
<div v-bind:style="{display:['-webkit','flex','block']}">Vue.js</div>
```

## Estilos usando Arrays

### Arrays

Informamos a diretiva **v-bind:style**
na tag que desejamos estilizar

Usando um array para que mais de um estilo seja aplicado no mesmo elemento

***Exemplos**

```dotnetcli
<p v-bind:style="[estilo1,estilo2]">Hcode Treinamentos</p>
data:{
    estilos1:{
        fontSize:'20px'
    },
    estilos2:{
        color:'orage'
    }
}
```

## Aplicando classes usando objetos

***Por que usar?**

Em vários casos preferimos usar classes ao invés de estilos em linha

Podemos aplicar classes em nossa aplicação de maneira dinâmica

***Maneiras de Criar**

1 - Usando objetos

2 - Usando arrays

## Objetos

Informamos a diretiva **v-bind:class**
na tag que desejamos estilizar

Usando chaves para informar o objeto com
o nome da classe e a condição para ela ser aplicada

```dotnetcli
<p v-bind:class="{classe: condicao}">Lorem Ipsum.</p>

<h3 v-bind:class="classe_objeto">Hcode</h3>

data:{
    classe_objeto:{
        linked:true,
        active:false
    }
}
```

# Animações -Visão Geral da Seção

***O que é?**

Envolve uma série de estilos CSS que  ocorrem em sequência

São como um Flip Book
(Folioscópio)
(Vários desenhos isolados)

***Por que usar?**

Animações trazem "vida" para nossa aplicação

Deixam a p´agina agradável de se ver e navegar

## Transições CSS

```dotnetcli
<transition name="transicao">
    <table v-if="condicao">
        <td>Han Solo</td>
        <td>Luke Skywalker</td>
    </table>
</transition>

.trasicao-enter, .transicao-leave-to { }
```

## Animações CSS

```dotnetcli
<transition name="transicao">
    <div>
        <h3>Vue.js</h3>
    </div>
</transition>


@keyframes {
    from {
        opacity: 0;
    }
    to {
        opacity: 1;
    }
}

```

## Animações Personalizadas

```dotnetcli
<tansition enter-active-class="classe">
    <ima src="/src/hcode.png">
</transition>
```

## Animações com JavaScript

```dotnetcli
<transiton v-on:after-enter="metodo" v-on:before-leave="metodo">
    <p>LOrem Ipsum</p>
</transiton>
```

## Transição entre elementos

```dotnetcli
<transition name="slide">
    <h2 v-if="logged">Seja bem-vindo Rafael</h2>
    <h3 v-else>Realize login para entrar</h3>
<transition>
```

## Transições CSS

***Como Criar?**

É possível usar animações com as diretivas **v-if, v-show**
ao trabalhar com componentes

O Vue possui um componente para transições e animações: **<transition></transition>**
Além disso, nos oferece classes padrão para definir o que ocorrerá na transição ou animação

## Classes padrão

classes de "entrada"   
v-enter
v-enter-to
v-enter-active

classes de "saída"
v-leave
v-leave-to
v-leave-active

## Classes de "entrada"

**v-enter** - Quando a transição começa

**v-enter-to** - Quando a transição termina (Novidade versão 2.1.8)

**v-enter-active**- Aplicado durante toda a transição

## Exemplo

```dotnetcli
<transition name="identificador">
    <h2 v-if="codicao">Lorem Ipsum</h2>
</transition>

.identificador-enter-active {
    trasition:opacity .5s ease;
}

.identificador-leave-active {
    trasition:opacity .5s ease;
}
.identificador-enter, .identificador-leave-to{
    opacity:0;
}

```

# Transições Vs Animações

Transições -> Mudam um elemento de um estado inicial para um estado final

Animações -> Mudam o estado de um elemento, mas com maior controle, maior complexidade

***Como Criar?**

Usamos o componente **<transition></transition>**

Também temos acesso às classes padrão para a animação, mas com uma maior flexibilidade

***Exemplo**

```dotnetcli
<transition name="identificador">
    <div v-if="condicao">Texto de exemplo</div>
</transition>

.identificador-leave-active{
    animation:animation_nome .5s reverse;
}
@keyfraames animation_nome {
    from{
        background: #fff;
    }
    to{
        background: #999;
    }
}
```

