# Node-Express

# 1. Visão geral do ambiente de desenvolvimento do Express
Node e Express facilitam a configuração de seu computador para começar a desenvolver aplicações web. Esta seção fornece uma visão ampla de quais ferramentas serão necessárias, explica alguns métodos simples para instalar o Node (e Express) no Ubuntu, macOS e Windows e também mostra como você pode testar sua aplicação.

# 2. O que é o ambiente de desenvolvimento Express?
O ambiente de desenvolvimento Express inclui uma instalação do Nodejs, o pacote de gerenciamento NPM e (opcionalmente) o Gerador de Aplicações Express em seu computador local.

O Node e o NPM são instalados em conjunto por meio de um pacote binário preparado, instaladores, pacotes de gerenciamento de sistemas operacionais ou diretamente da fonte (como mostra a seção seguinte). O Express é então instalado pelo NPM como uma dependência de sua aplicação web Express individual (junto a outras bibliotecas como motores de modelo, drivers de banco de dados, autenticações middleware, middleware para arquivos estáticos, etc.)

NPM também pode ser utilizado para instalar (globalmente) o Express Application Generator, uma ferramenta que cria um "esqueleto" de um app Express, seguindo o padrão MVC. O gerador de app é opcional porque você não precisa dessa ferramenta para criar um app ou um construtor Express para ter a mesma arquitetura. Nós vamos usá-lo nesta seção porque nos permite iniciar uma aplicação de uma maneira mais rápida e promover uma estrutura modular.

```
Nota: Ao contrário de muitos outros framework que não oferecem um servidor web junto ao ambiente de desenvolvimento, 
o Node/Express cria e roda o seu próprio servidor web.
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

** Atenção: Não faça a instalação direto do repositório normal do Ubuntu pois ele contém versões antigas do Node.**

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










