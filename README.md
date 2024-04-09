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
1. 🔧 em `project/settings.py` já está declarada a aplicação `bandas`. Adicione em `project/urls.py` uma rota para `bandas.urls` [[1]](https://github.com/ULHT-PW/pw-24-06-ficha-MVT/blob/main/README.md#5-urlspy-%EF%B8%8F)
2. ⚙️ crie uma view para renderizar cada uma das 4 páginas anteriormente identificadas. Em cada função-view deverá recolher com métodos ORM da base de dados os dados necessários para renderizar a página HTML 

3. `<>` crie a pasta `templates/novaapp`, e de um conjunto de pelo menos 3 ficheiros HTML simples, com conteúdos a seu gosto. se não tiver ideias de texto, pode usar https://www.lipsum.com/ para gerar texto em latim. o importante não é o conteudo, mas os passos do processo. Todas as páginas deverão ter um `header` e `footer` semelhante.
4.  ⚙️ definição em views.py de funções que renderizem os templates.
5. ✉️ criação do ficheiro `novaapp/urls.py` (use como base o ficheiro `project/urls.py`), definindo um `app_name`, e em urlpatterns os paths com URLs e respetivas funções em views com um `name` cada.
6. 🔗 criação de menu de navegação com hiperlinks para todas as páginas, que deverá estar presente no header de todas as páginas criadas.
7. ⟳ Recarregar (reload) a aplicação. Eventuais erros serão apresentados de forma explícita, pois está em modo debug.

# aplicação artigos
Para a aplicação artigos, implemente as partes View e Template de modo a poder visualizar a informação num browser.

# aplicação curso
Para a aplicação do seu curso, para a qual já fez uma modelação, vamos criar uma aplicação web que permita visualizar os dados disponiveis na base de dados através de um conjunto de paginas. Irá construir páginas para:
1. página com a lista de bandas.
2. página duma banda, com lista de albuns.
3. pagina de album, que mostra informação do album e a lista das músicas.
4. pagina de uma música, que mosta informação disponível.
