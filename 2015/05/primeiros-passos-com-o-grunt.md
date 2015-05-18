# Primeiros Passos com o Grunt

Muitas vezes ao iniciar um novo projeto *front-end* uma da opções seria utilizar um *generator* como o [Yeoman](http://yeoman.io/), [Slush](http://gruntjs.com/) entre outros. Com o Yeoman vem junto no pacote o [Grunt](http://gruntjs.com/) como gerenciador de tarefas, possibilitando utilizar o [Gulp](http://gulpjs.com/) também, já o Slush utiliza o somente o Gulp.

Os gerenciadores de tarefas ajudam na execução de tarefas repetitivas e salvam o precioso tempo de desenvolvimento.

Conversando com a equipe de desenvolvimento aqui da [Fiddus](http://fiddus.com.br) resolvemos utilizar o Grunt em alguns projetos. Trabalhamos uns modelos iniciais e posteriormente fomos adaptando para suprir a necessidade específica de cada projeto.

Ao final resolvemos compartilhar uma alternativa de como você pode iniciar a caminhada de aprendizado do Grunt.

---

Este tutorial é mais introdutório, para iniciar o entendimento do Grunt e mostrará as configurações iniciais até servir os arquivos, passando para verificar os arquivos quando alterados. Nos próximos *posts* mostraremos algo mais interessante sobre o Grunt. De qualquer maneira seja bem vindo para deixar suas opiniões e comentários.

---

Para seguir este *post* é necessário ter o [NodeJS](https://nodejs.org/ 'NodeJS') instalado em seu sistema operacional. Caso você não o tenha acesse o link acima e instale.

```shell
// Testar se já possui o node instalado
$ npm --version
```

## Iniciando os Primeiros Arquivos

Todo projeto *front-end* precisa de arquivos iniciais, para este vamos iniciar com um básico de com uma *index.html*, [*normalize.css*](http://necolas.github.io/normalize.css/). Portanto nossa estrutura básica de arquivos estaria abaixo

```text
grunt-project
    |-- css
    |    |-- normalize.css
    |    |-- styles.css
    |
    |-- js
    |    |-- app.js
    |
    |-- index.html

```

O conteúdo dos arquivos não é de tamanha importância para esta explicação, fique a vontade para alterar da maneira que desejar.

## Iniciando com NodeJS

Para começar a codificar com node precisamos instalar a interface de linha de comando do node, esta nos ajudará na instalação e remoção de pacotes para realizarmos algumas tarefas corriqueiras de desenvolvimento

```shell
$ npm install -g grunt-cli
```

O argumento `-g` quer dizer que este pacote será instalado globalmente no seu sistema. Os pacotes que não utilizam este argumento serão instalado no escopo do projeto.

Feito isso agora conseguiremos iniciar um projeto simplesmente pelo comando

```shell
$ npm init
```

Este comando vai fazer algumas perguntas (*name*, *version*, *description*, *entry point*, *test*, *git repository*, *keywords*, *authors*, *licence*) para setar algumas configurações e gerar um arquivo `package.json` na raiz do projeto.

```json
{
  "name": "GruntProject",
  "version": "0.0.1",
  "description": "Grunt project sample",
  "main": "js/app.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "repository": {
    "type": "git",
    "url": "git@github.com:fiddus/blog-grunt-project.git"
  },
  "author": "Adroaldo de Andrade <adroaldo@fiddus.com.br>",
  "license": "ISC"
}
```

Ao final já podemos começar a brincar um pouco com os pacotes NPM. O NPM possui configurações no `package.json`: uma de *dependencies*, *devDependencies*, *peerDependencies* para efeito deste *post* utilizaremos somente o *devDependencies*.



## Configurações do Grunt

Vamos criar um arquivo para codificar nossas *tasks*. Crie um arquivo chamado `Gruntfile.js` que conterá todo o código responsável pelas tarefas, este arquivo necessita de uma configuração inicial, depois agregamos mais configurações e registramos tarefas a ele.


```javascript
module.exports = function (grunt) {
    grunt.initConfig({

    });
};
```
        
### Gerenciador Grunt
        
O `Grunt` é um gerenciador de tarefas utilizado para fazer automatização de tarefas repetitivas que normalmente tomam o preciso tempo de desenvolvimento, para isso o Grunt vem ajudar a automatizá-las

```shell
$ npm install grunt --save-dev  
```

O comando acima quando terminado sua execução acrescentará automaticamente no arquivo de `package.json` um novo objeto json chamado *devDependencies* ficando parecido com o código abaixo

```json
{
    "...":"...",
    "devDependencies": {
         "grunt": "^0.4.5"
    },
    "...":"..."
}
```

Agora começamos a parte interessante, vamos aos próximos *plugins*.

### JavaScript Hint 

No dia-a-dia do desenvolvimento aqui na [Fiddus](http://fiddus.com.br) utilizamos muito JavaScript (EcmaScript) e gostamos de manter cuidados e convenções no código, o [JSHint](http://jshint.com/) ajuda bastante nisto, por isso temos uma *task* que nos dará dicas caso estejamos fugindo das convenções do JavaScript. 

Então vamos a nossa primeira *task* no `Gruntfile.js`

```shell
$ npm install grunt-contrib-jshint --save-dev
```

Isso vai adicionar outra dependência no seu arquivo `package.json`

```json
{
    "...":"...",
    "devDependencies": {
        "grunt": "^0.4.5",
        "grunt-contrib-jshint": "^0.11.0"
    },
    "...":"...",
}
```

Com isso podemos escrever nossa *task*

```javascript
module.exports = function (grunt) {

    // Load npm task
    grunt.loadNpmTasks('grunt-contrib-jshint');

    grunt.initConfig({

        // Hint on JavaScript errors
        jshint: {
            all: [
                './js/**/*.js'
            ]
        }

    });

};
```

Com isso já poderemos testar ver se há erros em nosso código JavaScript sem a necessidade de ler todos os códigos

```shell
$ grunt jshint
```

e você verá se há erros no seu código JavaScript. Bacana não?!

### Copy

Agora vamos fazer a preparação dos arquivos. Por hora faremos uma cópia dos arquivos necessário para execução do projeto a um diretório chamado *build*

```shell
$ npm install grunt-contrib-copy --save-dev
```
        
o comando instalará uma nova dependência ao `package.json`, como anteriormente, com isso já podemos fazer as configurações da task

```javascript
// Load npm task
grunt.loadNpmTasks('grunt-contrib-copy');

grunt.initConfig({
    // Copy files to a desired location
    copy: {
        build: {
            files: [
                {expand: false, src: ['index.html'], dest: 'build/'},
                {expand: true, src: ['js/**'], dest: 'build/'},
                {expand: true, src: ['css/**'], dest: 'build/'},
                {expand: true, src: ['img/**'], dest: 'build/'}
            ]
        }
    }
...
});
```

Ok, vamos testar agora

```shell
$ grunt copy
```

Executando o comando grunt você verificará que apareceu "magicamente" um diretório *build* com todos os seus arquivos dentro do seu projeto.

### Clean

Até agora tudo certo. Mas, e se por ventura modificarmos o nome de nosso arquivo e usarmos o comando `grunt copy` novamente, vamos verificar que o arquivo antigo ainda se encontra lá no diretório *build*. Para limparmos o diretório *build* vamos instalar e configurar nosso próximo *plugin* do Grunt

```shell
$ npm install grunt-contrib-clean --save-dev
```

A configuração deste é bem simples

```javascript
// Load npm task
grunt.loadNpmTasks('grunt-contrib-clean');

grunt.initConfig({
    // Remove files on directories on call
    clean: {
        build: [
            'build'
        ]
    }
});
```

Agora ao executar o comando acima 

```shell
$ grunt clean
```

Note que o diretório e seu conteúdo foram apagados. Caso você queria apagar somente o conteúdo do diretório deixe uma `/` no final da string *build* dentro do array

## Agrupamento de tarefas

Legal, até agora só executamos uma única tarefa por vez, que tal agrupá-las e executar nossas três tarefas sequencialmente? Vamos lá?! Faremos isso registrando uma tarefa

```javascript
module.exports = function (grunt) {
    // load npm tasks
    // ...
    
    grunt.initConfig({
        // ...
    });
    
    grunt.registerTask('build', [
        'clean',
        'jshint',
        'copy'
    ])
};
```
    
Vamos fazer um teste agora

```shell
$ grunt build
```

E o Grunt vai executar as tarefas na sequência do array, livrando você de ter que fazê-las manualmente, e mostrar o resultado delas no seu console

### Connect and Live Reload

Legal, agora vamos fazer o browser mostrar o resultado do nosso trabalho criando uma task de *webserver*

```shell
$ npm install grunt-contrib-connect --save-dev
```

configurando o *connect*
    
```javascript
// Load npm task
grunt.loadNpmTasks('grunt-contrib-connect');

// Connect application
connect: {
    options: {
        port: 8000,
        livereload: 35729,
        hostname: 'localhost'
    },
    livereload: {
        options: {
            open: true,
            base: [
                'build/'
            ],
        }
    }
}
```

Esta task só fica rodando enquanto o Grunt está rodando, quando este para, a tarefa também para. Um meio de fazer a sequência disso é utilizar o próximo *plugin*. Vamos a ele.

Este *plugin* que faremos a configuração para ajuda a ficar observando alterações nos arquivos e executar algumas tarefas específicas a cada alteração

```shell
$ npm install grunt-contrib-watch --save-dev
```

configurando o *watch*

```javascript
// Load npm task
grunt.loadNpmTasks('grunt-contrib-watch');

// ...

// Watch and live reload code
watch: {
    js: {
        files: [
            './js/**/*.js'
        ],
        options: {
            livereload: true
        },
        tasks: ['jshint', 'copy:build']
    },
    styles: {
        files: [
            './css/**/*.css'
        ],
        options: {
            livereload: true
        },
        tasks: ['copy:build']
    },
    html: {
        files: ['./index.html'],
        options: {
            livereload: true
        },
        tasks: ['copy:build']
    }
}
```


## Configurando a Nova Tarefa

Com isso já conseguiremos configurar uma nova tarefa que fará todo este trabalho em um comando somente

```javascript
grunt.registerTask('serve', [
    'build',
    'connect:livereload',
    'watch'
]);
```

Perceba que estamos chamando *build*, tarefa que foi registrada anteriormente, para executar a tarefa de *serve*, estruturando melhor as tarefas em blocos para serem executadas ou chamadas uma dentro de outra.

Agora executando

```shell
$ grunt serve
```

Teremos todas as tarefas executadas sequencialmente de forma automatizada e sem a necessidade de execução uma a uma.

Note que com este comando o console ficará esperando, e ao alterar um arquivo do projeto e salvá-lo ele informará qual arquivo foi alterado e executará as subtarefas que estão configuradas para as subtarefas que estão no *watch*.

# Concluindo

O Grunt é uma ótima maneira de automatizar tarefas que precisamos executar repetidas vezes no nosso dia-a-dia, trazendo uma comodidade e rapidez para quem utiliza

Este artigo foi mais didático para mostrar os primeiros passos de uma das ótimas ferramentas que ajudam em nosso dia a dia

Nos próximos posts mostraremos como incrementar o `Gruntfile.js` trazendo mais algumas tarefas úteis para o desenvolvimento de projetos *front-end*.

Até lá.


# Referências

1. [NodeJS](https://nodejs.org/)
2. [Grunt](http://gruntjs.com/)
3. [Dependencies, DevDependencies and PeerDependencies](http://stackoverflow.com/questions/18875674/whats-the-difference-between-dependencies-devdependencies-and-peerdependencies)
4. [Grunt Contrib JSHint](https://github.com/gruntjs/grunt-contrib-jshint)
5. [Grunt Contrib Copy](https://github.com/gruntjs/grunt-contrib-copy)
6. [Grunt Contrib Clean](https://github.com/gruntjs/grunt-contrib-clean)
7. [Grunt Contrib Connect](https://github.com/gruntjs/grunt-contrib-connect)
8. [Grunt Contrib Watch](https://github.com/gruntjs/grunt-contrib-watch) 
