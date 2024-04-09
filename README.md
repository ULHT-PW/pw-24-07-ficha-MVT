Univesidade Lusófona
**Programação Web**

# Ficha 7: Aplicações web

### Objetivo:
* Familiarizar-se com todas  as camadas da arquitetura MVT (Model, View e Template).
* Familiarizar-se com a linguagem de template do Django
* Familiarizar-se com a criação de aplicações web que interagem com a base de dados.

### Índice:
* &alpha;. Introdução ao HTML `<>`
* A. noobsite, páginas soltas 👶
* B. pwsite, o meu primeiro website 😎
* C. website a seu gosto 😎
* &omega; Entrega 📦


# Necessidades
* linguagem template: variáveis, if, for. iteração de listas e dicionarios. acesso a atributos de objeto. filtros.
* herança com layout base
* rotas com variáveis
* ficheiros estáticos (CSS e imagens), collectstatic
* mostrar imagens, links, descarregar ficheiros, vídeos


# aplicação web bandas 🎸
Na aplicação das bandas, onde já construiu a camada Model de modelação, vamos implementar as camadas de View e de Template, de modo a poder visualizar os dados num browser através de um conjunto de páginas. 

A aplicação irá ser composta por:
1. página com a lista de bandas.
2. página duma banda, com lista de albuns.
3. página de album, que mostra informação do album e a lista das músicas.
4. página de uma música, que mosta informação disponível.

Para tal, siga os seguintes passos:

### 1. Configuração 🔧

1. Em `project/settings.py` já deverá estar declarada a aplicação `bandas`. 
2. Em `project/urls.py`, adicione uma rota para `bandas.urls` [[1]](https://github.com/ULHT-PW/pw-24-06-ficha-MVT/blob/main/README.md#5-urlspy-%EF%B8%8F)

### 2. Camada de View ⚙️

1. Em views.py, crie uma função-view para cada uma das 4 páginas a retornar (no nome da função use o prefixo _view).
2. Em cada função-view deverá recolher da base de dados, com métodos ORM, os dados necessários para a página HTML.

### 3. Camada de Template `<>` 

1. crie a pasta `templates/bandas`
2. crie 4 ficheiros HTML, um para cada página da sua aplicação.
3. renderize a página, inserindo conteúdos da abse de dados usandoa linguagem de template Django. 

### 4. Camada de URLConfig ✉️ 

1. ✉️ na pasta `project/bandas` crie o ficheiro `urls.py`. Use como base o ficheiro `project/urls.py`
1. Defina um `app_name`
1. Defina em `urlpatterns` o mapeamento de URLs para respetivas funções-views.
1. Atribua um `name` a cada path.

### 5. Hiperlinks 🔗 

* Crie um elemento de navegação `<nav>` que permita voltar para páginas hierárquicamente superiores (se esta num album, deve poder voltar para a respetiva banda).
* para a lista de elementos (por exemplo, na página álbum, a lista de músicas), insira em cada música um link que encaminhe para a página dessa música.

### 5. Reload ⟳ 

*  Recarregar (reload) a aplicação. Eventuais erros serão apresentados de forma explícita, pois está em modo debug.

# aplicação artigos
Para a aplicação artigos, implemente as partes View e Template de modo a poder visualizar a informação num browser.

# aplicação curso
Para a aplicação do seu curso, para a qual já fez uma modelação, vamos criar uma aplicação web que permita visualizar os dados disponiveis na base de dados através de um conjunto de paginas. Irá construir páginas para:
1. página com a lista de bandas.
2. página duma banda, com lista de albuns.
3. pagina de album, que mostra informação do album e a lista das músicas.
4. pagina de uma música, que mosta informação disponível.
