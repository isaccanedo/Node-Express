# Node-Express

# Visão geral do ambiente de desenvolvimento do Express
Node e Express facilitam a configuração de seu computador para começar a desenvolver aplicações web. Esta seção fornece uma visão ampla de quais ferramentas serão necessárias, explica alguns métodos simples para instalar o Node (e Express) no Ubuntu, macOS e Windows e também mostra como você pode testar sua aplicação.

O que é o ambiente de desenvolvimento Express?
O ambiente de desenvolvimento Express inclui uma instalação do Nodejs, o pacote de gerenciamento NPM e (opcionalmente) o Gerador de Aplicações Express em seu computador local.

O Node e o NPM são instalados em conjunto por meio de um pacote binário preparado, instaladores, pacotes de gerenciamento de sistemas operacionais ou diretamente da fonte (como mostra a seção seguinte). O Express é então instalado pelo NPM como uma dependência de sua aplicação web Express individual (junto a outras bibliotecas como motores de modelo, drivers de banco de dados, autenticações middleware, middleware para arquivos estáticos, etc.)

NPM também pode ser utilizado para instalar (globalmente) o Express Application Generator, uma ferramenta que cria um "esqueleto" de um app Express, seguindo o padrão MVC. O gerador de app é opcional porque você não precisa dessa ferramenta para criar um app ou um construtor Express para ter a mesma arquitetura. Nós vamos usá-lo nesta seção porque nos permite iniciar uma aplicação de uma maneira mais rápida e promover uma estrutura modular.
