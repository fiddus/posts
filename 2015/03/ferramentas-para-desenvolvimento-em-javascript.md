Aqui na Fiddus, nós utilizamos JavaScript todos os dias. Seja para criar experiências envolventes no front-end, para programar nossos servidores com Node.js ou para comunicar com o banco de dados (com MongoDB ou CouchDB, entre outros), nós acreditamos que esta linguagem é muito poderosa se bem utilizada.

É claro que não somos fluentes apenas em JavaScript. Gostamos bastante de Python, estamos começando a aprender Ruby, e temos no nosso currículo passagens por Java, PHP e C++. Acreditamos que é fundamental conhecer diversas linguagens e paradigmas. Mas a utilização da mesma linguagem tanto no front-end como no back-end facilita nosso dia a dia e permite que tenhamos um conhecimento bastante aprofundado sobre ela. Para nós, esta linguagem é o JavaScript.

Neste post, vamos apresentar algumas ferramentas que utilizamos para desenvolvimento de sistemas com JavaScript, tanto no navegador como no servidor. Confira abaixo e deixe seu comentário.

## node e npm

O [node.js](https://nodejs.org) foi o projeto que possibilitou, com sucesso, levar o JavaScript para o servidor. Com ele, podemos construir *back-end*s robustos, escaláveis e muito rápidos. Além disso, no desenvolvimento, node é usado para diversas tarefas, servindo como uma linguagem para scripts e, junto com o pacote adequado (discutidos abaixo), como ferramenta de *build* e de automação de tarefas.

Junto com o node vem o [npm](https://www.nodejs.com), um excelente gerenciador de pacotes para JavaScript, com diversos recursos disponíveis. A maneira como o npm gerencia as dependêncas, instalando-as localmente e como uma árvore, evita conflitos e isola os projetos, permitindo várias versões de um mesmo pacote em cada um de seus projetos.

## nvm

O desenvolvimento do node tem sido bastante rápido, com atualizações frequentes de versão. Para evitar que uma aplicação apresente falhas provenientes de imcompatibilidade de versões, recomenda-se a utilização do [nvm](https://github.com/creationix/nvm), o Node Version Manager. Desta forma, não é necessário instalar o node diretamente.

Após a instalação do nvm, conforme descrito em seu repositório no GitHub, para utilizar uma versão específica do node, basta executar:

    $ nvm install 0.10

Isto irá instalar a versão mais atual do node 0.10, o que provavelmente evitará quebra de API. Para verificar a versão do node e do npm utilizadas no momento, execute:

    $ node --version
    $ npm --version

As ferramentas listadas abaixo estão todas disponíveis no npm. Para instalá-las, a menos que instruções específicas sejam mostradas, basta executar:

    $ npm install <nome do pacote>

---

## Ferramentas de Uso Geral

### Grunt

O [Grunt](http://gruntjs.com) é um *task runner*, escrito em node. Ou seja, através de um *script* de configuração, é possível definir várias tarefas a serem executadas automaticamente. Com isto, podemos automatizar diversos processos, como testes, *build*, *linting*, entre outros.

Em breve publicaremos um post detalhado sobre a utilização e configuração do Grunt.

### Gulp

O [Gulp](http://gulpjs.com) é uma alternativa ao Grunt, baseado em *streams*. Isto significa que as tarefas executadas em Gulp podem ser significativamente mais rápidas que as executadas em Grunt, pois tudo é feito em memória. Entretanto, por se tratar de uma ferramenta mais recente, nem todos os pacotes encontrados para Grunt existem para Gulp. Na Fiddus utilizamos o Grunt com mais frequência, mas temos alguns projetos com Gulp.

### jshint

Apesar de ser uma linguagem muito poderosa, JavaScript tem diversos problemas em sua implementação e é dever do desenvolvedor evitá-los. Algumas vezes, seja por distração ou por desconhecimento, é possível incorrer em erros imperceptíveis, já que JavaScript não é compilado.

Para evitar estes erros é fundamental utilizar uma ferramenta de análise estática do código. A mais popular atualmente é o [jshint](http://jshint.com). Uma das grandes vantagens do jshint é a extensa lista de configurações que podem ser realizadas, permitindo à equipe de desenvolvimento escolher quais avisos e erros devem ser reportados.

Utilizando o Grunt ou Gulp, é possível automatizar o processo de verificação do código com jshint. Para isso, no caso do Grunt, basta utilizar a task [`grunt-contrib-jshint`](https://github.com/gruntjs/grunt-contrib-jshint). No repositório deste pacote existem instruções detalhadas para a configuração.

### JSCS

Além de evitar erros e problemas da linguagem, quando se trabalha em grupo, é fundamental estabelecer e seguir um Guia de Estilo para o código, de maneira que todos os desenvolvedores escrevam código de maneira similar. Para garantir que estas regras estão sendo seguidas, uma ferramenta excelente é o [JavaScript Code Style - JSCS](http://jscs.info). Assim como o jshint, o JSCS permite controle total sobre as configurações a serem utilizadas.

Para automatizar a verificação do código, utilizamos o [`grunt-jscs`](https://github.com/jscs-dev/grunt-jscs) com o Grunt.

### Moment

Manipular datas e intervalos de tempo nem sempre é uma tarefa fácil. A biblioteca nativa de JavaScript para isso é o `Date`, que não oferece uma API muito amigável.

Uma alternativa é a utilização do [moment.js](http://momentjs.com/), que permite manipular, validar, interpretar e mostrar datas, de forma mais simples que a nativa.

### lodash

[lodash](https://lodash.com/) fornece diversas funcionalidades para manipulação de dados em JavaScript. O lodash é totalmente compatível com o underscore, outra biblioteca similar e, talvez, mais famosa. Entretanto, o lodash apresenta uma maior gama de funções e tem performance superior à do underscore.  

A API do lodash, assim como a do underscore, segue o paradigma funcional, o que a torna bastante versátil e flexível, além de eliminar a necessidade de extender as funcionalidades nativas dos objetos, o que poderia causar conflitos no caso de utilização de bibliotecas externas, principalmente no navegador.

---
## Editores

Um bom editor pode facilitar muito as tarefas do dia a dia do desenvolvedor. Entre os editores que utilizamos estão:

### vim

Este editor, utilizado no terminal, é extremamente poderoso nas mãos de um desenvolvedor experiente. Entretanto, ele tem uma curva de aprendizado bastante longa e muita gente desiste no meio do caminho ou só aprende as funcionalidades básicas. 

É imprescindível saber utilizar pelo menos as funções básicas, pois o vim, ou o vi, estão sempre disponíveis em sistemas *nix, ao contrário dos demais editores.

### Sublime Text

Ao contrário do vim, o [Sublime](http://www.sublimetext.com/) tem uma interface bastante amigável. A grande vantagem deste editor é a possibilidade de instalação de pacotes, permitindo a adição de muitas funcionalidades.

### WebStorm

O [WebStorm](https://www.jetbrains.com/webstorm/) não é um simples editor, mas uma IDE completa para desenvolvimento em JavaScript. Conta com diversas funcionalidades como autocomplete, sugestão de código, *linting*, execução de *tasks* do Grunt, entre outras.

O ponto em que o WebStorm realmente mostra seu valor é para realizar *debug*. Tanto para *front-end* como para *back-end*, a ferramenta de *debug* do WebStorm é bastante completa e customizável.

---

## Ferramentas para o back-end

Abaixo apresentaremos ferramentas que utilizamos especificamente quando estamos desenvolvendo código para os servidores.

### express

O node contém bibliotecas que permitem utilizá-lo como um web server, tal qual Apache ou IIS. Entretanto, para prover as funcionalidades necessárias para desenvolver uma aplicação, utilizando apenas node, seria necessário escrever muito código para tratamento dos eventos e para servir arquivos e enviar as respostas às requisições.

Para evitar este retrabalho, é fundamental utilizar um framework que já disponibilize estas funcionalidades. O mais popular destes frameworks é o [express](http://expressjs.com/). O express oferece o mínimo de funcionalidade para desenvolvimento de aplicações, fazendo com que sua performance seja muito boa. Este framework também é excelente para o desenvolviemnto de API's REST.


### mocha, chai e supertest

Você testa seu código, certo? Certo?? Se não testa, está mais do que na hora de começar! Após avaliar alguns frameworks de teste, decidimos utilizar o [mocha](http://mochajs.org/). Ele permite fazer *setup* dos testes, com `before` e `beforeEach`, encapsular grupos de teste com `describe`, descrever casos específicos de teste com `it` e realizar ações após os testes com `after` e `afterEach`.

Utilizamos o [chai](http://chaijs.com/) para realizar as asserções dos testes. A API do chai é bastante semântica e intuitiva e a documentação é boa.

Para testar nossas API's REST, utilizamos o [supertest](https://github.com/visionmedia/supertest). O supertest permite realizar requisições a URLs, passando parâmetros e headers, e verificar se a resposta obtida está de acordo com o esperado. Esta biblioteca funciona muito bem em conjunto com o express.

Utilizando estas ferramentas, o código de teste fica estruturado de maneira similar ao mostrado abaixo:

<!-- js -->
    var request = require('supertest'),
        expect = ('chai').expect,
        app = require('../app'), //App do express
        thing = require('./thing); //Módulo sendo testado
    
    describe('Teste sem usar supertest', function () {
        it ('should return array when call something on thing', function (done) {
            expect(thing.something()).to.be.instanceOf(Array);
        });
        
        it ('something else ...', function (done) {
            expect(true).to.be(true);
        });
    });
    
    describe('Teste usando supertest', function () {
        it ('should return status 200 when GET / on app', function (done) {
            request(app)
                .get('/')
                .expect(200)
                .end(done);
        });
    });

Em breve postaremos um artigo completo sobre teste e TDD no *back-end*.

### mongoose

Utilizar diretamente o MongoDB pode ser um pouco trabalhoso. Para facilitar isso, existe a biblioteca [mongoose](http://mongoosejs.com/), que permite modelar os objetos do MongoDB diretamente no node.

O mongoose também possibilita a criação de *Schemas* e a validação dos dados de acordo com esses *Schemas*.

### passport

[Passport](http://passportjs.org/) é um módulo de autenticação para node, que oferece diversas funcionalidades, como variadas estratégias de autenticação, autenticação com OAuth e OpenID, suporte a seções persistentes, entre outras.

Com o passaport, é bastante simples implementar esquemas de login utilizando informações de outros serviços, como [facebook](https://www.facebook.com/), por exemplo.

---

## Ferramentas para o front-end

### Angular

[Angular](https://angularjs.org/) é um *frame-work* para desenvolvimento *front-end* desenvolvido pelo Google. O Angular facilita muito a criação de aplicações dinâmicas e Single Page Applications.

Com Angular é possível extender o HTML, criando *tags* personalizadas para encapsular funcionalidades.

O Angular foi desenvolvido de forma a ser completamente testável, utilizando bastante Injeção de Dependência e provendo mocks para a realização dos testes.

### Stylus

[Stylus](http://learnboost.github.io/stylus/) é um pré-processador de CSS. Os pré-processadores de CSS permitem uma grande flexibilidade em relação ao CSS puro, como declaração de variaveis e funções, compatilibidade com diferentes *browsers*, mixins, entre outros.

Entre as opções disponíveis de pré-processadores, as mais utilizadas são SASS, LESS e Stylus. Nós preferimos utilizar o Stylus devido a sua sintaxe simplificada e ao fato de ser desenvolvido em node.

Para automatizar o processamento dos arquivos de Stylus para CSS, utilizamos o pacote [grunt-contrib-stylus](https://github.com/gruntjs/grunt-contrib-stylus).

### Bower

Gerenciar as dependências no *front-end* não é tão simples como no *back-end*. No servidor, usando o npm e configurando as dependências no `package.json`, está quase tudo resolvido.

Para ter estas funcionalidades no *front-end* existe o [Bower](http://bower.io/), um gerenciador de dependências para o browser. Com ele é bastante simples adicionar dependências ao projeto, bastando executar:

    $ bower install <nome da dependência>

Para instalar o angular, por exemplo, basta rodar:

    $ bower install angular --save

O comando `--save` utilizado acima salva as dependências instaladas em um arquivo de configurações, o `bower.json`.


### Karma

Para rodar os testes unitários no front-end, utilizamos o [Karma](http://karma-runner.github.io/). Karma é um *runner* de testes que roda nos navegadores configurados. O Karma não depende de algum framework de testes específico, podendo ser utilizado com diversos deles, como mocha, sinon, Jasmine, QUnit, etc.

### Protractor

[Protractor](http://angular.github.io/protractor/#/) é um framework para testes End-to-end no Angular. Este framework permite rodar os testes da aplicação em navagadores reais, emulando a interação que um usuário real teria com o sistema.

### Tasks do Grunt para build

Para realizar o *build* da nossa aplicação *front-end* utilizamos diversos pacotes do Grunt. Os mais relevantes estão listados abaixo:

* **[grunt-contrib-clean](https://github.com/gruntjs/grunt-contrib-clean)**: Exclui os arquivos e ou diretórios especificados
* **[grunt-contrib-copy](https://github.com/gruntjs/grunt-contrib-copy)**: Copia arquivos de um diretório para outro.
* **[grunt-contrib-concat](https://github.com/gruntjs/grunt-contrib-concat)**: Concatena os arquivos escolhidos. Utilizado para diminuir o número de arquivos de javascript ou css.
* **[grunt-contrib-htmlmin](https://github.com/gruntjs/grunt-contrib-htmlmin)**: Minifica arquivos HTML.
* **[grunt-contrib-cssmin](https://github.com/gruntjs/grunt-contrib-cssmin)**: Minifica arquivos CSS.
* **[grunt-contrib-uglify](https://github.com/gruntjs/grunt-contrib-uglify)**: Comprime arquivos JavaScript.
* **[grunt-contrib-connect](https://github.com/gruntjs/grunt-contrib-connect)**: Permite criar um servidor local para os arquivos em desenvolvimento.
* **[grunt-contrib-watch](https://github.com/gruntjs/grunt-contrib-watch)**: Verifica os arquivos que foram alterados e executa *tasks* predefinidas para cada tipo de arquivo.
* **[grunt-wiredep](https://github.com/gruntjs/grunt-wiredep)**: Injeta as dependências instaladas com bower automaticamente no HTML.

---

## Quais ferramentas você utiliza?

Desenvolver sistemas profissionais não é tarefa fácil. Poder contar com uma comunidade open-source muito ativa facilita muito a vida dos desenvolvedores, já que existem diversas ferramentas para realizar tarefas comuns. A comunidade open-source que existe ao redor de JavaScript e, especificamente, node, é bastante grande e muito dinâmica. Com isso, é necessário conhecer diversas ferramentas e se atualizar sempre.

O que você achou do artigo? Alguma ferramenta que você utiliza não está na lista? Deixe seu comentário!