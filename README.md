Univesidade Lusófona
**Programação Web**

# Ficha 7: Construção de Aplicações Web com Django, a web framework para perfeccionistas com deadlines

### Objetivo:
* Familiarizar-se com todas  as camadas da arquitetura MVT (Model, View e Template).
* Familiarizar-se com a linguagem de template do Django
* Familiarizar-se com a criação de aplicações web que interagem com a base de dados.
* Continuar a desenvolver as aplicações iniciadas na ficha 4 e 5.

### Aplicações a aprimorar:
* A. Aplicação bandas 🎸
* B. Aplicação artigos 📚
* C. Aplicação curso 🎓


# Requisitos
conhecimentos de:
* linguagem template: variáveis, if, for. iteração de listas e dicionarios. acesso a atributos de objeto. filtros.
* herança com layout base
* rotas com variáveis
* ficheiros estáticos (CSS e imagens), collectstatic
* mostrar imagens, links, descarregar ficheiros, vídeos


# A. Aplicação web bandas 🎸
Na aplicação das bandas, onde já construiu a camada Model de modelação, vamos implementar as camadas de View e de Template, de modo a poder visualizar os dados num browser através de um conjunto de páginas. 

A aplicação irá ser composta por pelo menos as 4 seguintes bandas (se fizer uma página adicional que explore a base de dados de forma diferente terá uma bonificação):
1. página com a lista de bandas.
2. página duma banda, com lista de albuns.
3. página de album, que mostra informação do album, incluindo a imagem da capa (ver aplicação bibliotecalusofona [github](https://github.com/ULHT-PW/bibliotecalusofona/blob/4a6800349d89af51cf9c4365d1f9f2f58d581820/biblioteca/templates/biblioteca/autor.html#L5) [app](https://bibliotecalusofona.pythonanywhere.com/autor/53/)), e a lista das músicas.
4. página de uma música, que mosta informação disponível.

Para tal, siga os seguintes passos.

### 1. Configuração 🔧

1. Em `project/settings.py` já deverá estar declarada a aplicação `bandas`. 
2. Em `project/urls.py`, adicione uma rota para `bandas.urls` [[1]](https://github.com/ULHT-PW/pw-24-06-ficha-MVT/blob/main/README.md#5-urlspy-%EF%B8%8F)

### 2. Camada de View ⚙️

1. Em views.py, crie uma função view para cada uma das 4 páginas a retornar (no nome da função use o prefixo _view) [[2]](https://github.com/ULHT-PW/pw-24-06-ficha-MVT/blob/main/README.md#4-camada-de-view-implementada-por-viewspy-%EF%B8%8F).
2. Pense que argumentos cada view terá, além de request. Exemplo: a view de um álbum é natural que precise do id do álbum, `album_view(request, album_id)`, para depois na função obter `album = Album.objects.get(id=album_id)` 
5. Em cada view deverá recolher os dados necessários da base de dados, com métodos ORM, e guardá-los na variável `context` que deverá ser passada como argumento da função `render` da página HTML.

### 3. Camada de Template `<>` 

1. crie a pasta `templates/bandas`
2. crie um template layout.html (pai) que será "estendido" pelas páginas do site (filhos).
3. crie 4 ficheiros HTML, um para cada página da sua aplicação. Utilize as variáveis de contexto enviadas pela view
4. insira conteúdos da base de dados usando a linguagem de template Django.
5. crie pelo menos um customtag, filtro criado por si para uma funcionalidade específica.

### 4. Camada de URLConfig ✉️ 

1. na pasta `project/bandas` crie o ficheiro `urls.py`. Use como base o ficheiro `project/urls.py` [[3]](https://github.com/ULHT-PW/pw-24-06-ficha-MVT/blob/main/README.md#5-urlspy-%EF%B8%8F)
1. Defina um `app_name`
1. Defina em `urlpatterns` o mapeamento de URLs para as respetivas funções-views.
1. Atribua um `name` a cada path.

### 5. Hiperlinks 🔗 

* Crie um elemento de navegação `<nav>` que permita voltar para páginas hierárquicamente superiores. Por exemplo, se esta num album, deve poder voltar para a respetiva banda. [[3]](https://github.com/ULHT-PW/pw-24-06-ficha-MVT/blob/main/README.md#6-hiperlinks-)
* Quando lista elementos (por exemplo, a lista de músicas na página de um álbum), insira em cada música um link que encaminhe para a página dessa música. Para tal, passe no url, o id da música `musica.id`.

### 6. Exemplo de Implementação do Padrão MVT no Django

Exemplo de template HTML para a página que renderiza informação de um album:
```html
<!-- album.html -->
<html>
<body>
    <ul>
    <h1> {{ album.banda }} </h1>

    <h3> Album: {{ album.nome }}, {{ album.ano }} </h3>
    
    <p>Lista de músicas do álbum:</p>
    {% for musica in album.musicas.all %}
       <li>
          <a href="{% url 'bandas:musica_url' musica.id %}">{{ musica }}</a>    
       </li>
    {% endfor%}
    </ul>
</body>
</html>
```

Exemplo de rota associada ao link associado a uma música, acima apresentado:
```python
# bandas/urls.py

from django.urls import path
from . import views  # importamos views para poder usar as suas funções

app_name = 'bandas'
urlpatterns = [
  # ...
  path('musica/<int:musica_id>', views.musica_view, name='musica_url')
]
```

Exemplo de view associada à rota a pedir uma música:
```python
# bandas/views.py

from django.shortcuts import render
from .models import Musica

def musica_view(request, musica_id):
   context = {
      'musica': Musica.objects.get(id=musica_id),
   }
   return render(request, 'bandas/musica.html', context)
```

## 5. Reload ⟳ 

*  No PythonAnyWhere, recarregar (reload) a aplicação. Eventuais erros serão apresentados de forma explícita, pois está em modo debug.

# B. Aplicação artigos 📚
Na aplicação artigos, para a qual já fez a camada de modelação, implemente as mesmas camadas anteriores de modo a poder visualizar a informação num browser.

# C. Aplicação curso 🎓
Na aplicação do seu curso, para a qual já fez a camada de modelação, implemente as camadas que na app das bandas, de modo vamos criar uma aplicação web que permita visualizar os dados disponiveis na base de dados através de um conjunto de paginas. 

A aplicação deverá ter pelo menos 3 views, que permitam renderizar:
1. página do curso.
1. página de disciplina do curso, que deverá incluir conteúdos programáticos, projetos, linguagens de programação.
1. página de projeto da disciplina do curso.
