# Mês 14: Django Framework

**Carga Horária:** 96 horas (4 semanas)
**Período:** Semanas 5-8
**Pré-requisito:** Conclusão completa do Mês 13 (Python Fundamentos)
**Status:** Módulo Essencial Backend ⭐⭐⭐

## Visão Geral

Django é um framework web Python "batteries-included" que acelera desenvolvimento de aplicações robustas e escaláveis. Este módulo ensina desde conceitos fundamentais até implementação de APIs REST profissionais com Django REST Framework.

## Objetivos de Aprendizado

Ao final deste módulo, o aluno será capaz de:

- Estruturar projetos Django profissionais
- Trabalhar com modelos e ORM Django
- Criar views e templates
- Implementar formulários com validação
- Usar Django Admin efetivamente
- Criar APIs REST com Django REST Framework
- Implementar autenticação e permissões
- Fazer deployment de aplicações Django
- Testar e debugar aplicações

## Estrutura de Aprendizado

### SEMANA 1: Fundamentos Django

#### Aula 1: Filosofia e Setup Django (4h)
- Por que Django (MTV pattern)
- Filosofia Django
- Instalação e setup
- Estrutura de projeto
- Criando primeira aplicação
- Settings e configurações
- Development server

**Projeto Prático:** Setup profissional do Django

```bash
# Criar virtual environment
python -m venv venv
source venv/bin/activate

# Instalar Django
pip install django djangorestframework

# Criar projeto
django-admin startproject myproject .
django-admin startapp myapp

# Estrutura
myproject/
├── manage.py
├── myproject/
│   ├── __init__.py
│   ├── settings.py
│   ├── urls.py
│   └── wsgi.py
└── myapp/
    ├── migrations/
    ├── models.py
    ├── views.py
    ├── urls.py
    ├── admin.py
    └── apps.py
```

#### Aula 2: Modelos e ORM (6h)
- Definição de modelos
- Field types
- Meta options
- Relacionamentos (1-to-1, 1-to-many, many-to-many)
- Queries ORM
- Migrations
- Best practices

**Projeto Prático:** Design de banco de dados

```python
# models.py
from django.db import models

class Author(models.Model):
    name = models.CharField(max_length=100)
    email = models.EmailField(unique=True)
    created_at = models.DateTimeField(auto_now_add=True)

    def __str__(self):
        return self.name

class Post(models.Model):
    title = models.CharField(max_length=200)
    content = models.TextField()
    author = models.ForeignKey(Author, on_delete=models.CASCADE, related_name='posts')
    published = models.BooleanField(default=False)
    created_at = models.DateTimeField(auto_now_add=True)
    updated_at = models.DateTimeField(auto_now=True)

    class Meta:
        ordering = ['-created_at']
        indexes = [
            models.Index(fields=['-created_at']),
        ]

    def __str__(self):
        return self.title

# Queries
all_posts = Post.objects.all()
recent = Post.objects.filter(published=True).order_by('-created_at')
author_posts = Author.objects.get(id=1).posts.all()
```

#### Aula 3: Views e URLs (6h)
- Function-based views
- Class-based views (CBV)
- Mixins
- Generic views
- Roteamento com URLs
- Namespacing
- URL reversing

**Projeto Prático:** Criar views e rotas

```python
# myapp/views.py
from django.shortcuts import render
from django.views import View
from django.views.generic import ListView, DetailView
from .models import Post

# Function-based view
def post_list(request):
    posts = Post.objects.all()
    return render(request, 'post_list.html', {'posts': posts})

# Class-based view
class PostListView(ListView):
    model = Post
    paginate_by = 10
    context_object_name = 'posts'

class PostDetailView(DetailView):
    model = Post
    context_object_name = 'post'

# myapp/urls.py
from django.urls import path
from . import views

app_name = 'myapp'

urlpatterns = [
    path('posts/', views.PostListView.as_view(), name='post_list'),
    path('posts/<int:pk>/', views.PostDetailView.as_view(), name='post_detail'),
]

# myproject/urls.py
from django.contrib import admin
from django.urls import path, include

urlpatterns = [
    path('admin/', admin.site.urls),
    path('', include('myapp.urls')),
]
```

#### Aula 4: Templates e Rendering (4h)
- Sintaxe de templates
- Variáveis e filtros
- Tags de template
- Herança de templates
- Includes
- Static files
- Asset management

**Projeto Prático:** Criar templates

```html
<!-- base.html -->
<!DOCTYPE html>
<html>
<head>
    {% load static %}
    <link rel="stylesheet" href="{% static 'css/style.css' %}">
</head>
<body>
    <header>
        <h1>Meu Blog</h1>
    </header>
    {% block content %}{% endblock %}
</body>
</html>

<!-- post_list.html -->
{% extends 'base.html' %}

{% block content %}
<h2>Posts</h2>
{% for post in posts %}
    <article>
        <h3><a href="{% url 'myapp:post_detail' post.pk %}">{{ post.title }}</a></h3>
        <p>Por {{ post.author.name }}</p>
        <p>{{ post.content|truncatewords:50 }}</p>
        <time>{{ post.created_at|date:"d/m/Y" }}</time>
    </article>
{% empty %}
    <p>Nenhum post encontrado.</p>
{% endfor %}
{% endblock %}
```

### SEMANA 2: Formulários e Admin

#### Aula 5: Formulários Django (6h)
- Form classes
- ModelForms
- Validação
- Widgets customizados
- Formsets
- CSRF protection
- Processing form data

**Projeto Prático:** Criar formulários

```python
# myapp/forms.py
from django import forms
from .models import Post

class PostForm(forms.ModelForm):
    class Meta:
        model = Post
        fields = ['title', 'content', 'published']
        widgets = {
            'title': forms.TextInput(attrs={'class': 'form-control'}),
            'content': forms.Textarea(attrs={'class': 'form-control', 'rows': 5}),
            'published': forms.CheckboxInput(attrs={'class': 'form-check-input'}),
        }

    def clean_title(self):
        title = self.cleaned_data['title']
        if len(title) < 5:
            raise forms.ValidationError("Título deve ter mínimo 5 caracteres")
        return title

# myapp/views.py
from django.shortcuts import render, redirect
from .forms import PostForm

def create_post(request):
    if request.method == 'POST':
        form = PostForm(request.POST)
        if form.is_valid():
            post = form.save(commit=False)
            post.author = request.user
            post.save()
            return redirect('myapp:post_detail', pk=post.pk)
    else:
        form = PostForm()
    return render(request, 'create_post.html', {'form': form})
```

#### Aula 6: Django Admin (4h)
- Admin registration
- ModelAdmin customization
- Filters e searches
- List displays
- Actions
- Admin permissions
- Inline editing

**Projeto Prático:** Configurar admin

```python
# myapp/admin.py
from django.contrib import admin
from .models import Author, Post

@admin.register(Author)
class AuthorAdmin(admin.ModelAdmin):
    list_display = ['name', 'email', 'post_count']
    search_fields = ['name', 'email']
    list_filter = ['created_at']
    readonly_fields = ['created_at']

    def post_count(self, obj):
        return obj.posts.count()
    post_count.short_description = 'Posts'

@admin.register(Post)
class PostAdmin(admin.ModelAdmin):
    list_display = ['title', 'author', 'published', 'created_at']
    list_filter = ['published', 'created_at']
    search_fields = ['title', 'content']
    readonly_fields = ['created_at', 'updated_at']
    fieldsets = (
        ('Conteúdo', {'fields': ('title', 'content')}),
        ('Metadata', {'fields': ('author', 'published', 'created_at', 'updated_at')}),
    )
    actions = ['publish_posts']

    def publish_posts(self, request, queryset):
        queryset.update(published=True)
    publish_posts.short_description = "Publicar posts selecionados"
```

#### Aula 7: Autenticação e Permissões (4h)
- User model
- Authentication
- Permissions e groups
- Decorators (@login_required, @permission_required)
- Login/logout views
- Password reset
- User creation

**Projeto Prático:** Implementar segurança

```python
# views.py
from django.contrib.auth.decorators import login_required, permission_required
from django.contrib.auth import authenticate, login
from django.views.generic import CreateView
from django.contrib.auth.models import User

@login_required
def dashboard(request):
    user_posts = request.user.posts.all()
    return render(request, 'dashboard.html', {'posts': user_posts})

@permission_required('myapp.change_post')
def edit_post(request, pk):
    post = Post.objects.get(pk=pk)
    # editar post

class UserRegisterView(CreateView):
    model = User
    fields = ['username', 'email', 'password']
    template_name = 'register.html'
    success_url = reverse_lazy('login')
```

#### Aula 8: Testes Django (4h)
- TestCase
- setUp e tearDown
- Fixtures
- Testing models, views, forms
- Client testing
- Coverage

**Projeto Prático:** Suite de testes

```python
# myapp/tests.py
from django.test import TestCase, Client
from django.contrib.auth.models import User
from .models import Post, Author

class PostModelTests(TestCase):
    def setUp(self):
        self.author = Author.objects.create(name="John", email="john@example.com")

    def test_create_post(self):
        post = Post.objects.create(
            title="Test",
            content="Content",
            author=self.author
        )
        self.assertEqual(post.title, "Test")
        self.assertTrue(post.author == self.author)

class PostViewTests(TestCase):
    def setUp(self):
        self.client = Client()
        self.author = Author.objects.create(name="John", email="john@example.com")
        self.post = Post.objects.create(
            title="Test",
            content="Content",
            author=self.author
        )

    def test_post_list_view(self):
        response = self.client.get('/posts/')
        self.assertEqual(response.status_code, 200)
        self.assertContains(response, "Test")
```

### SEMANA 3: Django REST Framework

#### Aula 9: Serializers (6h)
- ModelSerializer
- Field validation
- Custom validation
- Nested serializers
- Relationships
- Read-only/write-only fields

**Projeto Prático:** Criar serializers

```python
# myapp/serializers.py
from rest_framework import serializers
from .models import Author, Post

class AuthorSerializer(serializers.ModelSerializer):
    posts_count = serializers.SerializerMethodField()

    class Meta:
        model = Author
        fields = ['id', 'name', 'email', 'posts_count']

    def get_posts_count(self, obj):
        return obj.posts.count()

class PostSerializer(serializers.ModelSerializer):
    author_name = serializers.CharField(source='author.name', read_only=True)

    class Meta:
        model = Post
        fields = ['id', 'title', 'content', 'author', 'author_name', 'published', 'created_at']
        read_only_fields = ['created_at']

    def validate_title(self, value):
        if len(value) < 5:
            raise serializers.ValidationError("Título muito curto")
        return value
```

#### Aula 10: ViewSets e Routers (6h)
- ViewSets
- Generic ViewSets
- Routers
- Actions customizadas
- Permissions
- Throttling

**Projeto Prático:** Criar APIs REST

```python
# myapp/views.py (DRF)
from rest_framework import viewsets, permissions, status
from rest_framework.decorators import action
from rest_framework.response import Response
from .models import Post, Author
from .serializers import PostSerializer, AuthorSerializer

class PostViewSet(viewsets.ModelViewSet):
    queryset = Post.objects.all()
    serializer_class = PostSerializer
    permission_classes = [permissions.IsAuthenticatedOrReadOnly]

    def perform_create(self, serializer):
        serializer.save(author=self.request.user)

    @action(detail=False, methods=['get'])
    def published(self, request):
        posts = Post.objects.filter(published=True)
        serializer = self.get_serializer(posts, many=True)
        return Response(serializer.data)

    @action(detail=True, methods=['post'])
    def set_published(self, request, pk=None):
        post = self.get_object()
        post.published = request.data.get('published', False)
        post.save()
        return Response({'status': 'published status changed'})

class AuthorViewSet(viewsets.ReadOnlyModelViewSet):
    queryset = Author.objects.all()
    serializer_class = AuthorSerializer

# myapp/urls.py
from rest_framework.routers import DefaultRouter
from . import views

router = DefaultRouter()
router.register(r'posts', views.PostViewSet)
router.register(r'authors', views.AuthorViewSet)

urlpatterns = router.urls
```

#### Aula 11: Autenticação REST (4h)
- Token authentication
- JWT (JSON Web Tokens)
- Session authentication
- Permissions classes
- Custom permissions
- Rate limiting

**Projeto Prático:** Autenticação de API

```python
# settings.py
INSTALLED_APPS = [
    # ...
    'rest_framework',
    'rest_framework.authtoken',
]

REST_FRAMEWORK = {
    'DEFAULT_AUTHENTICATION_CLASSES': [
        'rest_framework.authentication.TokenAuthentication',
    ],
    'DEFAULT_PERMISSION_CLASSES': [
        'rest_framework.permissions.IsAuthenticated',
    ],
}

# views.py
from rest_framework.authtoken.views import obtain_auth_token

# Gerar token para usuário
from rest_framework.authtoken.models import Token
token = Token.objects.create(user=user)

# urls.py
urlpatterns = [
    path('api-token-auth/', obtain_auth_token),
]
```

#### Aula 12: Integração Full-Stack (4h)
- Consumir API do React
- CORS setup
- Error handling
- Pagination
- Filtering e searching
- Documentação automática

**Projeto Prático:** Integrar frontend React

```python
# settings.py
INSTALLED_APPS += ['corsheaders']

MIDDLEWARE = [
    'corsheaders.middleware.CorsMiddleware',
    # ...
]

CORS_ALLOWED_ORIGINS = [
    "http://localhost:3000",
]

REST_FRAMEWORK = {
    'DEFAULT_PAGINATION_CLASS': 'rest_framework.pagination.PageNumberPagination',
    'PAGE_SIZE': 10,
    'DEFAULT_FILTER_BACKENDS': [
        'django_filters.rest_framework.DjangoFilterBackend',
        'rest_framework.filters.SearchFilter',
    ],
}

# views.py com filtros
from django_filters.rest_framework import DjangoFilterBackend

class PostViewSet(viewsets.ModelViewSet):
    queryset = Post.objects.all()
    serializer_class = PostSerializer
    filter_backends = [DjangoFilterBackend, filters.SearchFilter]
    filterset_fields = ['published', 'author']
    search_fields = ['title', 'content']
```

### SEMANA 4: Deployment e Projeto Final

#### Aula 13: Deployment Django (4h)
- Gunicorn vs UWSGI
- Nginx configuration
- Environment variables
- Static files collection
- Database migrations em produção
- Logging

**Projeto Prático:** Preparar para produção

```bash
# requirements.txt
Django==4.2.0
djangorestframework==3.14.0
gunicorn==20.1.0
whitenoise==6.4.0
python-dotenv==1.0.0

# settings.py (production)
DEBUG = os.getenv('DEBUG', 'False') == 'True'
ALLOWED_HOSTS = os.getenv('ALLOWED_HOSTS', '').split(',')

MIDDLEWARE += ['whitenoise.middleware.WhiteNoiseMiddleware']

STATIC_URL = '/static/'
STATIC_ROOT = os.path.join(BASE_DIR, 'staticfiles')

# Dockerfile
FROM python:3.10
WORKDIR /app
COPY requirements.txt .
RUN pip install -r requirements.txt
COPY . .
CMD ["gunicorn", "myproject.wsgi:application", "--bind", "0.0.0.0:8000"]
```

#### Aula 14: Debugging e Performance (4h)
- Debug toolbar
- Query optimization (select_related, prefetch_related)
- Caching
- Database indexing
- Profiling

**Projeto Prático:** Otimizar aplicação

```python
# settings.py (development)
if DEBUG:
    INSTALLED_APPS += ['debug_toolbar']
    MIDDLEWARE += ['debug_toolbar.middleware.DebugToolbarMiddleware']
    INTERNAL_IPS = ['127.0.0.1']

# views.py (otimização)
from django.db.models import Prefetch

posts = Post.objects.select_related('author').prefetch_related('comments')

# Caching
from django.views.decorators.cache import cache_page

@cache_page(60 * 5)  # 5 minutos
def post_list(request):
    posts = Post.objects.all()
    return render(request, 'post_list.html', {'posts': posts})
```

#### Aula 15: Best Practices (4h)
- Code organization
- Settings management
- Error handling
- Logging configuration
- Security hardening
- Documentation

**Projeto Prático:** Aplicar best practices

#### Aula 16: Projeto Integrador - Blog API Completa (8h)
- Django REST Framework completo
- Autenticação com tokens
- Admin customizado
- Testes 80%+
- Deploy
- Documentação

## Projetos do Módulo

### Projeto 1: Blog com Django
**Duração:** 20 horas
**Funcionalidades:**
- Posts, comentários, categorias
- Admin customizado
- Autenticação
- Testes básicos

### Projeto 2: API RESTful com DRF
**Duração:** 40 horas
**Funcionalidades:**
- ViewSets completos
- Autenticação JWT
- Permissions
- Filtering e pagination
- Testes 80%+
- Documentação Swagger
- Deploy

### Projeto 3: Revisor
**Duração:** 8 horas

## Stack Tecnológico

- **Python 3.10+**
- **Django 4.x**
- **Django REST Framework**
- **PostgreSQL**
- **Gunicorn**
- **Docker**

## Cronograma Recomendado

| Semana | Horas | Foco | Projeto |
|--------|-------|------|---------|
| 5 | 24 | Django Basics, Admin | Exercícios |
| 6 | 24 | Formulários, Auth | Projeto 1 |
| 7 | 24 | DRF, APIs | Projeto 2 |
| 8 | 24 | Deploy, Integração | Projeto Final |

---

**Última atualização:** Janeiro de 2025
**Versão:** 2.0
**Nível:** Intermediário
