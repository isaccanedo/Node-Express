# Node-Express

# 1. Visão geral do ambiente de desenvolvimento do Express
Node e Express facilitam a configuração de seu computador para começar a desenvolver aplicações web. Esta seção fornece uma visão ampla de quais ferramentas serão necessárias, explica alguns métodos simples para instalar o Node (e Express) no Ubuntu, macOS e Windows e também mostra como você pode testar sua aplicação.

# 2. O que é o ambiente de desenvolvimento Express?
O ambiente de desenvolvimento Express inclui uma instalação do Nodejs, o pacote de gerenciamento NPM e (opcionalmente) o Gerador de Aplicações Express em seu computador local.

O Node e o NPM são instalados em conjunto por meio de um pacote binário preparado, instaladores, pacotes de gerenciamento de sistemas operacionais ou diretamente da fonte (como mostra a seção seguinte). O Express é então instalado pelo NPM como uma dependência de sua aplicação web Express individual (junto a outras bibliotecas como motores de modelo, drivers de banco de dados, autenticações middleware, middleware para arquivos estáticos, etc.)

NPM também pode ser utilizado para instalar (globalmente) o Express Application Generator, uma ferramenta que cria um "esqueleto" de um app Express, seguindo o padrão MVC. O gerador de app é opcional porque você não precisa dessa ferramenta para criar um app ou um construtor Express para ter a mesma arquitetura. Nós vamos usá-lo nesta seção porque nos permite iniciar uma aplicação de uma maneira mais rápida e promover uma estrutura modular.

```
Nota: Ao contrário de muitos outros framework que não oferecem um servidor web junto
ao ambiente de desenvolvimento, o Node/Express cria e roda o seu próprio servidor web.
```

Há outras ferramentas periféricas que integram o ambiente de desenvolvimento, é o caso dos editores de textos (códigos), conhecidos como IDE, e versionadores de códigos, como o Git, que ajudam a gerenciar diferentes versões do código. Estamos partindo da ideia de que você já conhece essas ferramentas e as têm instaladas (em especial o editor de texto).

# 3. Quais sistemas operacionais têm suporte?
Node roda em Windows, macOS, diferentes versões do Linux, Docker, etc. Há uma lista de sistemas suportados que pode ser encontrada na página de Downloads do Nodejs. Quase todos os computadores pessoais têm o que é necessário para rodar o Node. O Express roda no ambiente Node e, consequentemente, roda em qualquer plataforma que roda o Node.

Neste artigo, vamos abordar as instruções de configuração para Windows, macOS, e Ubuntu Linux.

# 4. Qual versão do Node/Express você deve usar?
Há várias versões do Node - as mais recentes contém correção de bugs, suporte para EMCAScript (JavaScript) e melhorias nas APIs do Node.

De maneira geral, você deve usar a versão mais recente do LTS (long-term supported), pois é a mais estável do que a versão "current". Além disso, você deve usar a versão current apenas se precisar de alguma funcionalidade que não está presente na versão LTS.

Para o Express, você deve usar sempre a versão mais completa.

### Sobre o banco de dados e outras dependências?
Outras dependências, como database drivers, engine para templates, ferramentas para autenticação, etc, são parte da aplicação e são importadas para o ambiente a partir do NPM. Nós vamos falar sobre essa parte mais para frente.

# 5. Instalando o Node
Para utilizar o Express, você terá que instalar o Nodejs e o NPM em seu sistema operacional. Nas seções a seguir, vamos explicar o jeito mais fácil de instalar a versão LTS do Nodejs no Ubuntu Linux 16.04, macOS e Windows 10.

```
Dica: As seções abaixo mostram o jeito mais fácil de instalar o NPM nos Sistemas Operacionais. 
Se você utilizar outro sistema ou quer ver uma abordagem diferente para as plataformas atuais 
acesse Instalando Node.js via NPM (nodejs.org).
```

### Windows e macOS
Instalar o Node e o NPM no Windows ou no macOS é uma tarefa rápida e simples. Siga os seguintes passos:

### Baixar o instalador:
- Vá para https://nodejs.org/en/
- Selecione o botão de download da versão LTS, que é a recomendada para a maioria dos usuários.
- Instale o Node ao clicar duas vezes no arquivo de download. Siga a instalação a partir das janelas que vão aparecer na sua tela.

### Ubuntu 16.04
O jeito mais fácil de instalar a versão LTS do Node é usar o NPM a partir do Ubuntu binary distributions repository. Isso pode ser feito de uma maneira muito simples. Rode os seguintes comandos no seu terminal.

```
curl -sL https://deb.nodesource.com/setup_8.x | sudo -E bash -
sudo apt-get install -y nodejs
```

**Atenção: Não faça a instalação direto do repositório normal do Ubuntu pois ele contém versões antigas do Node.

### Testando a instalação do Nodejs e do NPM
O jeito mais fácil de testar se tudo correu bem na instalação é checar qual a versão do Node está rodando no computador. Para isso, vá ao terminal/command prompt e digite o seguinte comando para retornar a resposta com a versão mais recente.

```
>node -v
v8.9.4
```
O NPM também deve ter sido instalado. Você pode checar da seguinte maneira:

```
>npm -v
5.6.0
```

Uma maneira um pouco mais divertida de testar é criar um servidor web em "puro node". Vamos imprimir a tradicional frase "Hello World" no browser quando visitarmos uma determinada URL.

Crie um arquivo chamado hellonode.js e cole dentro dele o código abaixo. Estamos usando apenas o Node, sem o Express, e com sintaxe do ES6.

```
//Chame o módulo HTTP
var http = require("http");

//Crie um servidor HTTP para ouvir as requisições na porta 8000
http.createServer(function (request, response) {

   // Configure o resposta HTTP header com o HTTP status e Content type
   response.writeHead(200, {'Content-Type': 'text/plain'});

   // Envie a resposta do body "Hello World"
   response.end('Hello World\n');
}).listen(8000);

// Imprima URL para acessar o servidor
console.log('Server running at http://127.0.0.1:8000/')
```

O código importa o módulo "http" e o utiliza para criar um servidor (createServer()) que escuta as requisições HTTP na porta 8000. O script, então, imprime a mensagem no console. A função createServer() recebe como argumento uma função callback que é chamada quando recebe uma requisição HTTP - isso retorna uma resposta com um status 200 ("OK") do HTTP e o texto "Hello World".

```
Nota:  Não se preocupe se você não entendeu exatamente o que esse código faz. 
Nós vamos explicar isso em mais detalhes quando iniciarmos a parte do Express.
```

Inicie o servidor e navegue pelo mesmo diretório que o seu arquivo hellonode.js no terminal. Depois chame o Node da seguinte forma:

```
>node hellonode.js
Server running at http://127.0.0.1:8000/
```

Navegue até a URL (http://127.0.0.1:8000/). Se tudo estiver funcionando bem, o browser vai apresentar a frase "Hello World".

# Usando o NPM
Ao lado do próprio Node, o NPM é a ferramenta de trabalho mais importante nas aplicações Node. O NPM é usado para buscar qualquer pacote (biblioteca JavaScript) que uma aplicação precisa para ser desenvolvida, testada ou produzida, além de ser adotado para rodar testes ao longo de todo o processo de desenvolvimento.

Nota: A partir da perspectiva do Node, Express é um pacote que precisa ser instalado utilizando o NPM e depois importado para o seu código.

Você pode usar o NPM separadamente para buscar cada pacote desejado. Em geral, nós gerenciamos as dependências com um arquivo chamado package.json. Esse arquivo lista todas as dependências para um pacote JavaScript específico, incluindo o nome do pacote, a versão, descrição, arquivo de inicialização, produção de dependências, desenvolvimento de dependências, versões do Node que podem ser utilizadas. O package.json contém tudo que o NPM precisa para buscar e rodar a sua aplicação (se você está escrevendo uma biblioteca para ser reutilizável, você pode usar essa definição para fazer o upload do pacote para o repositório npm e deixá-lo acessível a qualquer usuário).

### Adicionando dependências
Os passos seguintes mostram como baixar pacotes via NPM, salvá-los nas dependências do projeto e importá-los/chamá-los para dentro da aplicação Node.

Nota:  Nesta seção mostraremos como buscar e instalar o pacote do Express. Depois, explicaremos como esse e outros pacotes já estão especificados para nós graças ao Express Application Generator. É  muito importante entendermos como o NPM funciona e o que é criado com o generator. 

Primeiro passo é criar um diretório para sua aplicação. No prompt, insira os comandos a seguir.
mkdir myapp
cd myapp
Copy to Clipboard
 Use o comando npm init para criar o arquivo package.json da sua aplicação. Esse comando registra para você uma série de informações, como o nome e a versão do seu aplicativo, além do nome do seu "entry point" (index.js por padrão). Por hora, vamos manter a configuração padrão.
npm init

Se você acessar o arquivo package.json (cat packge.json), você verá toda a configuração padrão e, ao final, o tipo de licença que o app está utilizando.

```
{
  "name": "myapp",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "",
  "license": "ISC"
}
```

Agora, instale o Express dentro do diretório myapp. O pacote será salvo automaticamente na lista de dependências do seu package.json.
npm install express

A lista de dependências do package.json agora mostra também a versão do Express que estamos usando. Está grifada no final do arquivo.

```
{
  "name": "myapp",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "",
  "license": "ISC",
  "dependencies": {
    "express": "^4.16.2"
  }
}
```

Para usar o Express, é preciso incluir a função require() no arquivo index.js dentro da sua aplicação. Crie esse arquivo agora mesmo na pasta raiz "myapp" e inclua o código a seguir.

```
var express = require('express')
var app = express()

app.get('/', function (req, res) {
  res.send('Hello World!')
})

app.listen(8000, function () {
  console.log('Example app listening on port 8000!')
})
```

O código mostra uma aplicação web bem simples cujo objetivo único é imprimir a mensagem "HelloWorld". Em linhas gerais, esse arquivo importa o módulo do express e o utiliza para criar um servidor (app) que escuta as requisições HTTP pela porta 8000 e imprime a mensagem no console, além de definir qual URL usada para testar o servidor. A função app.get() responde apenas às requisições HTTP feitas com o método GET, desde que especificadas com o path ('/'). Nesse caso, chamando a função para enviar a mensagem Hello World!

Rode a linha de comando abaixo para iniciar o servidor.

```
>node index.js
Example app listening on port 8000
```

Vá para a seguinte URL (http://127.0.0.1:8000/). Se tudo estiver funcionando corretamente, o browser vai mostrar a mensagem "Hello World!".

### Desenvolvendo dependências
Se você utilizar uma dependência apenas durante o desenvolvimento da aplicação, é recomendado que você a salve como uma "development dependency". Dessa forma, o pacote não será utilizado no ambiente de produção. Por exemplo: caso utilizar o pacote esling (JavaScript Linting), você faria a instalação via NPM da seguinte forma.

Se você utilizar uma dependência apenas durante o desenvolvimento da aplicação, é recomendado que você a salve como uma "development dependency". Dessa forma, o pacote não será utilizado no ambiente de produção. Por exemplo: caso utilizar o pacote esling (JavaScript Linting), você faria a instalação via NPM da seguinte forma.

npm install eslint --save-dev

Assim, a esling vai aparecer da seguinte forma na lista de dependências do package.json.

```
  "devDependencies": {
    "eslint": "^4.12.1"
  }
  ```
```
Note: "Linters" são ferramentas que nos ajudam a identificar e reportar que 
o código está sendo escrito dentro das melhores práticas.
```

# Rodando tarefas
Além de definir e buscar dependências, você também pode nomear scripts dentro do seu arquivo package.json e chamar o NPM para executá-lo a partir de um run-script command. Essa abordagem é comum para automatizar testes e tarefas ao longo do desenvolvimento (por exemplo: minificar o JavaScript, reduzir imagens, LINT/análise de códigos, etc).

```
Nota: Ferramentas de automação de tarefas como o Gulp e o Grunt 
também podem ser utilizados, além de outros pacotes externos. 
```

Para definir o script que roda o esling, citado na seção acima, nós precisamos adicionar o seguinte bloco no nosso package.json (importante: sua aplicação precisa ter como source está na pasta /src/js):

```
"scripts": {
  ...
  "lint": "eslint src/js"
  ...
}
```

Explicando um pouco mais: eslint src/js é o comando que colocamos no nosso terminal para rodar o eslint nos arquivos JavaScript situados no diretório src/js dentro do diretório do nosso app. Incluindo o comando, criamos o comando de atalho - lint.

```
npm run-script lint
# OR (using the alias)
npm run lint
```

O exemplo pode não parecer mais curto do que o comando original, mas com o que você aprendeu é possível incluir comandos bem maiores dentro do npm scripts, como as cadeias de múltiplos comandos. Você pode até escrever um único script npm para rodar todos os seus testes de uma só vez.

# Instalando o Express Application Generator
O Express Application Generator é uma ferramenta que cria "esqueleto" para aplicações Express. A instalação é realizada via NPM como mostrada a seguir (o comando -g instala a pacote globalmente, ou seja, você pode acessá-lo de qualquer lugar do seu computador).

```
npm install express-generator -g
```

Para criar um aplicativo Express chamado "helloworld" com as configurações padrões, vá até o local/pasta em que você deseja desenvolver o projeto e escreva a seguinte linha de comando:

```
express helloworld
```

**Nota:  Você também pode definir a biblioteca de template que pretende usar e muitas outras configurações. Use o comando help para ver todas as opções. 

```
express --help
```

O NPM vai criar um novo aplicativo Express em uma subpasta na localização em que você está. O progresso será apresentado no console. Para finalizar, o processo, a ferramenta mostrará os comandos que você precisa seguir para instalar a dependência Node e iniciar o seu app.

O novo app terá um arquivo package.json no diretório raiz. Você pode abrir esse arquivo para checar o que foi instalado, incluindo o Express e Jade (template library)

```
{
  "name": "helloworld",
  "version": "0.0.0",
  "private": true,
  "scripts": {
    "start": "node ./bin/www"
  },
  "dependencies": {
    "body-parser": "~1.18.2",
    "cookie-parser": "~1.4.3",
    "debug": "~2.6.9",
    "express": "~4.15.5",
    "jade": "~1.11.0",
    "morgan": "~1.9.0",
    "serve-favicon": "~2.4.5"
  }
}
```

Instale todas as dependências para o app helloworld com o NPM, de acordo com os comandos abaixo:

```
cd helloworld
npm install
```
Agora, rode o aplicativo (o comando muda um pouco entre Windows, Linux/macOS), como está no código a seguir:

```
# Rode o helloworld no Windows
SET DEBUG=helloworld:* & npm start

# Rode helloworld no Linux/macOS
DEBUG=helloworld:* npm start
```

O comando DEBUG gera um loggin bem útil, apresentando resultados, como abaixo:

```
>SET DEBUG=helloworld:* & npm start

> helloworld@0.0.0 start D:\Github\expresstests\helloworld
> node ./bin/www
 helloworld:server Listening on port 3000 +0ms
```

Abre um browser e navegue para http://127.0.0.1:3000/ e veja a página default apresentada pelo aplicativo.

# Sumário
Agora você tem o desenvolvimento do Node pronto para rodar no seu computador e que pode ser utilizado para criar aplicações web com o framework Express. Você também viu como o NPM é utilizado para importar o Express em sua aplicação e como criar um esqueleto a partir do Express Aplication Generator.
