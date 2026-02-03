# Mês 15: Integração de Sistemas

**Carga Horária:** 96 horas (4 semanas)
**Período:** Semanas 9-12
**Pré-requisito:** Conclusão completa dos Mês 13 e 14
**Status:** Módulo Avançado ⭐⭐

## Visão Geral

Este módulo foca em como conectar e integrar diferentes sistemas, implementar comunicação assíncrona, e construir arquiteturas escaláveis. Os alunos aprenderão sobre APIs externas, webhooks, message queues e background jobs.

## Objetivos de Aprendizado

Ao final deste módulo, o aluno será capaz de:

- Consumir APIs externas com segurança
- Implementar webhooks
- Usar message queues (Redis, RabbitMQ)
- Criar background jobs com Celery
- Integrar serviços de terceiros (Stripe, SendGrid, etc)
- Implementar logging centralizado
- Monitorar aplicações
- Fazer rate limiting
- Implementar retry logic e fallbacks
- Preparar aplicações para escala

## Estrutura de Aprendizado

### SEMANA 1: APIs Externas e Webhooks

#### Aula 1: Consumindo APIs REST (6h)
- Requests library avançado
- Headers e autenticação
- Tratamento de erros
- Retry logic
- Circuit breaker pattern
- Rate limiting client-side
- Caching de respostas

**Projeto Prático:** Integrar múltiplas APIs

```python
# myapp/integrations.py
import requests
from requests.adapters import HTTPAdapter
from urllib3.util.retry import Retry
from django.core.cache import cache
from django.conf import settings
import logging

logger = logging.getLogger(__name__)

class APIClient:
    def __init__(self, base_url: str, api_key: str):
        self.base_url = base_url
        self.api_key = api_key
        self.session = self._create_session()

    def _create_session(self):
        session = requests.Session()
        retry = Retry(
            total=3,
            backoff_factor=0.5,
            status_forcelist=[429, 500, 502, 503, 504]
        )
        adapter = HTTPAdapter(max_retries=retry)
        session.mount('http://', adapter)
        session.mount('https://', adapter)
        return session

    def get(self, endpoint: str, params: dict = None) -> dict:
        cache_key = f"api_{endpoint}_{str(params)}"
        cached = cache.get(cache_key)
        if cached:
            return cached

        url = f"{self.base_url}/{endpoint}"
        headers = {'Authorization': f'Bearer {self.api_key}'}

        try:
            response = self.session.get(url, params=params, headers=headers, timeout=5)
            response.raise_for_status()
            data = response.json()
            cache.set(cache_key, data, 300)  # 5 minutos
            return data
        except requests.exceptions.RequestException as e:
            logger.error(f"API error: {e}")
            raise

# Uso
github = APIClient("https://api.github.com", "token123")
user = github.get("users/github")
```

#### Aula 2: Webhooks (6h)
- Receber webhooks
- Validar assinatura
- Processar eventos
- Retry logic
- Idempotência
- Segurança

**Projeto Prático:** Implementar webhooks

```python
# myapp/webhooks.py
from django.http import JsonResponse
from django.views.decorators.csrf import csrf_exempt
from django.views.decorators.http import require_http_methods
import hmac
import hashlib
import json
from celery import shared_task
import logging

logger = logging.getLogger(__name__)

@csrf_exempt
@require_http_methods(["POST"])
def stripe_webhook(request):
    """Receber eventos do Stripe."""
    payload = request.body
    sig_header = request.META.get('HTTP_STRIPE_SIGNATURE')
    webhook_secret = settings.STRIPE_WEBHOOK_SECRET

    try:
        event = stripe.Webhook.construct_event(
            payload, sig_header, webhook_secret
        )
    except ValueError:
        return JsonResponse({'error': 'Invalid payload'}, status=400)
    except stripe.error.SignatureVerificationError:
        return JsonResponse({'error': 'Invalid signature'}, status=400)

    # Processar evento de forma assíncrona
    process_stripe_event.delay(event.type, event.data)

    return JsonResponse({'status': 'success'})

@shared_task
def process_stripe_event(event_type: str, event_data: dict):
    """Processar eventos do Stripe em background."""
    logger.info(f"Processando evento: {event_type}")

    if event_type == 'charge.succeeded':
        handle_payment_success(event_data['object'])
    elif event_type == 'charge.failed':
        handle_payment_failed(event_data['object'])
    elif event_type == 'customer.subscription.created':
        handle_subscription_created(event_data['object'])
```

#### Aula 3: Segurança em Integrações (4h)
- API key management
- OAuth 2.0
- mTLS
- Request signing
- Encryption
- Audit logging

**Projeto Prático:** Securizar integrações

```python
# settings.py
STRIPE_API_KEY = os.getenv('STRIPE_API_KEY')
STRIPE_WEBHOOK_SECRET = os.getenv('STRIPE_WEBHOOK_SECRET')

# Use django-environ ou python-decouple
from decouple import config

GITHUB_TOKEN = config('GITHUB_TOKEN', default='')
SENDGRID_API_KEY = config('SENDGRID_API_KEY')

# Validar webhooks
import hmac

def verify_webhook_signature(payload: bytes, signature: str, secret: str) -> bool:
    expected = hmac.new(
        secret.encode(),
        payload,
        hashlib.sha256
    ).hexdigest()
    return hmac.compare_digest(signature, expected)
```

#### Aula 4: Implementação de OAuth (4h)
- OAuth 2.0 flow
- Login social (Google, GitHub)
- Token refresh
- Scope management
- django-allauth

**Projeto Prático:** Social login

```python
# settings.py
INSTALLED_APPS += [
    'allauth',
    'allauth.account',
    'allauth.socialaccount',
    'allauth.socialaccount.providers.google',
]

AUTHENTICATION_BACKENDS = [
    'allauth.account.auth_backends.AuthenticationBackend',
]

# urls.py
urlpatterns += [
    path('accounts/', include('allauth.urls')),
]

# template
{% load socialaccount %}
<a href="{% provider_login_url 'google' %}">Login com Google</a>
```

### SEMANA 2: Background Jobs e Message Queues

#### Aula 5: Redis e Caching (6h)
- Redis fundamentals
- Django cache framework
- Cache strategies
- Session storage
- Pub/Sub
- Rate limiting com Redis

**Projeto Prático:** Cache em múltiplas camadas

```python
# settings.py
CACHES = {
    'default': {
        'BACKEND': 'django_redis.cache.RedisCache',
        'LOCATION': 'redis://127.0.0.1:6379/1',
        'OPTIONS': {
            'CLIENT_CLASS': 'django_redis.client.DefaultClient',
        }
    }
}

# views.py
from django.views.decorators.cache import cache_page
from django.core.cache import cache

@cache_page(60 * 5)  # 5 minutos
def expensive_view(request):
    return render(request, 'template.html')

# Caching manual
def get_user_posts(user_id):
    cache_key = f"user_posts_{user_id}"
    posts = cache.get(cache_key)

    if posts is None:
        posts = Post.objects.filter(author_id=user_id)
        cache.set(cache_key, posts, 3600)

    return posts

# Rate limiting
from django_ratelimit.decorators import ratelimit

@ratelimit(key='user', rate='10/h', method='POST')
def api_endpoint(request):
    # Máximo 10 requisições por hora por usuário
    pass
```

#### Aula 6: Celery para Background Jobs (6h)
- Celery setup com Django
- Tasks
- Scheduling (Beat)
- Retry logic
- Error handling
- Monitoring

**Projeto Prático:** Sistema completo de background jobs

```python
# settings.py
CELERY_BROKER_URL = 'redis://127.0.0.1:6379/0'
CELERY_RESULT_BACKEND = 'redis://127.0.0.1:6379/0'
CELERY_ACCEPT_CONTENT = ['json']
CELERY_TASK_SERIALIZER = 'json'
CELERY_RESULT_SERIALIZER = 'json'

# myproject/celery.py
import os
from celery import Celery

os.environ.setdefault('DJANGO_SETTINGS_MODULE', 'myproject.settings')

app = Celery('myproject')
app.config_from_object('django.conf:settings', namespace='CELERY')
app.autodiscover_tasks()

# myapp/tasks.py
from celery import shared_task
from celery.utils.log import get_task_logger
import time

logger = get_task_logger(__name__)

@shared_task(bind=True, max_retries=3)
def send_email(self, user_id: int, subject: str, body: str):
    """Enviar email em background."""
    try:
        user = User.objects.get(id=user_id)
        logger.info(f"Enviando email para {user.email}")

        # Simular envio
        time.sleep(2)

        user.email_sent = True
        user.save()

        logger.info(f"Email enviado com sucesso para {user.email}")
    except Exception as exc:
        logger.error(f"Erro ao enviar email: {exc}")
        # Retry com backoff exponencial
        raise self.retry(exc=exc, countdown=60)

# Usar task
send_email.delay(user_id=1, subject="Bem-vindo", body="Bem-vindo ao nosso site!")

# views.py
def register(request):
    user = create_user(request.data)
    # Enviar email de boas-vindas em background
    send_email.delay(
        user_id=user.id,
        subject="Bem-vindo",
        body="Bem-vindo ao site!"
    )
    return JsonResponse({'status': 'user created'})
```

#### Aula 7: Celery Beat para Scheduling (4h)
- Periodic tasks
- Crontab
- Timezone handling
- Monitoring tasks
- Task result storage

**Projeto Prático:** Agendamentos recorrentes

```python
# settings.py
CELERY_BEAT_SCHEDULE = {
    'send-report-every-day': {
        'task': 'myapp.tasks.send_daily_report',
        'schedule': crontab(hour=9, minute=0),  # 9h da manhã
    },
    'cleanup-sessions': {
        'task': 'myapp.tasks.cleanup_expired_sessions',
        'schedule': crontab(hour='*/6'),  # A cada 6 horas
    },
    'sync-data-every-5-minutes': {
        'task': 'myapp.tasks.sync_external_data',
        'schedule': 300.0,  # segundos
    },
}

# myapp/tasks.py
from celery import shared_task
from celery.schedules import crontab

@shared_task
def send_daily_report():
    """Enviar relatório diário."""
    logger.info("Enviando relatório diário")
    # Lógica de envio

@shared_task
def cleanup_expired_sessions():
    """Limpar sessões expiradas."""
    from django.contrib.sessions.models import Session
    Session.objects.filter(expire_date__lt=now()).delete()

# Rodar Celery Beat
# celery -A myproject beat -l info
```

#### Aula 8: RabbitMQ e Event-Driven Architecture (4h)
- Message queues
- Event publishing
- Event handling
- Microservices communication
- Dead letter queues

**Projeto Prático:** Arquitetura orientada a eventos

### SEMANA 3: Integração com Serviços Terceiros

#### Aula 9: Stripe para Pagamentos (6h)
- Setup Stripe
- Criar customers
- Cobrar cartões
- Webhooks
- Recurrências
- Refunds

**Projeto Prático:** Sistema de pagamento

```python
# settings.py
import stripe
stripe.api_key = settings.STRIPE_API_KEY

# myapp/stripe_integration.py
def create_stripe_customer(user: User) -> str:
    """Criar customer no Stripe."""
    customer = stripe.Customer.create(
        name=user.username,
        email=user.email,
        metadata={'user_id': user.id}
    )
    return customer.id

def charge_card(amount: int, card_token: str, user_id: int) -> dict:
    """Cobrar cartão."""
    try:
        charge = stripe.Charge.create(
            amount=amount,  # em centavos
            currency='usd',
            source=card_token,
            description=f"Cobro para usuário {user_id}",
        )
        return {'success': True, 'charge_id': charge.id}
    except stripe.error.CardError as e:
        return {'success': False, 'error': str(e)}

def create_subscription(customer_id: str, price_id: str):
    """Criar assinatura recorrente."""
    subscription = stripe.Subscription.create(
        customer=customer_id,
        items=[{"price": price_id}],
    )
    return subscription
```

#### Aula 10: SendGrid para Email (4h)
- Setup SendGrid
- Enviar emails
- Templates
- Tracking
- Unsubscribe

**Projeto Prático:** Sistema de notificação por email

```python
# settings.py
SENDGRID_API_KEY = os.getenv('SENDGRID_API_KEY')

# myapp/email.py
from sendgrid import SendGridAPIClient
from sendgrid.helpers.mail import Mail

def send_welcome_email(user_email: str, user_name: str):
    """Enviar email de boas-vindas."""
    message = Mail(
        from_email='noreply@mysite.com',
        to_emails=user_email,
        subject='Bem-vindo!',
        html_content=f'<p>Olá {user_name}, bem-vindo!</p>'
    )

    try:
        sg = SendGridAPIClient(settings.SENDGRID_API_KEY)
        response = sg.send(message)
        return True
    except Exception as e:
        logger.error(f"Email error: {e}")
        return False

# tasks.py
@shared_task
def send_newsletter(user_id: int):
    user = User.objects.get(id=user_id)
    send_welcome_email(user.email, user.username)
```

#### Aula 11: AWS S3 para Storage (4h)
- Setup AWS
- Upload/download
- Pre-signed URLs
- Permissions
- CloudFront

**Projeto Prático:** Gerenciamento de arquivos

```python
# settings.py
import boto3
from django.core.files.storage import default_storage
from storages.backends.s3boto3 import S3Boto3Storage

AWS_ACCESS_KEY_ID = os.getenv('AWS_ACCESS_KEY_ID')
AWS_SECRET_ACCESS_KEY = os.getenv('AWS_SECRET_ACCESS_KEY')
AWS_STORAGE_BUCKET_NAME = os.getenv('AWS_STORAGE_BUCKET_NAME')
AWS_S3_REGION_NAME = 'us-east-1'

DEFAULT_FILE_STORAGE = 'storages.backends.s3boto3.S3Boto3Storage'

# models.py
class Document(models.Model):
    file = models.FileField(upload_to='documents/')
    created_at = models.DateTimeField(auto_now_add=True)

# views.py
def upload_document(request):
    file = request.FILES['file']
    doc = Document.objects.create(file=file)
    url = doc.file.url  # URL do S3
    return JsonResponse({'url': url})
```

#### Aula 12: Logging Centralizado (4h)
- Estrutured logging
- ELK Stack (Elasticsearch, Logstash, Kibana)
- Log aggregation
- Alertas
- Monitoring

**Projeto Prático:** Setup de logging profissional

```python
# settings.py
LOGGING = {
    'version': 1,
    'disable_existing_loggers': False,
    'formatters': {
        'json': {
            '()': 'pythonjsonlogger.jsonlogger.JsonFormatter'
        },
    },
    'handlers': {
        'console': {
            'class': 'logging.StreamHandler',
            'formatter': 'json',
        },
        'file': {
            'class': 'logging.handlers.RotatingFileHandler',
            'filename': 'logs/django.log',
            'formatter': 'json',
            'maxBytes': 1024000,
            'backupCount': 10,
        },
    },
    'loggers': {
        'django': {
            'handlers': ['console', 'file'],
            'level': 'INFO',
        },
        'myapp': {
            'handlers': ['console', 'file'],
            'level': 'DEBUG',
        },
    },
}

# Uso
import logging
logger = logging.getLogger(__name__)

logger.info('Usuário criado', extra={
    'user_id': user.id,
    'email': user.email,
    'ip': request.META.get('REMOTE_ADDR')
})
```

### SEMANA 4: Monitoramento e Projeto Final

#### Aula 13: Sentry para Error Tracking (4h)
- Setup Sentry
- Capturar exceções
- Release tracking
- Performance monitoring
- Source maps

**Projeto Prático:** Implementar error tracking

```python
# settings.py
import sentry_sdk
from sentry_sdk.integrations.django import DjangoIntegration
from sentry_sdk.integrations.celery import CeleryIntegration

sentry_sdk.init(
    dsn=os.getenv('SENTRY_DSN'),
    integrations=[
        DjangoIntegration(),
        CeleryIntegration(),
    ],
    traces_sample_rate=0.1,
    send_default_pii=True,
)

# Capturar erro manualmente
try:
    process_data()
except Exception as e:
    sentry_sdk.capture_exception(e)
```

#### Aula 14: Monitoring com Prometheus (4h)
- Métricas
- Alertas
- Dashboards
- Performance tracking

#### Aula 15: Best Practices Integrações (4h)
- Error handling
- Retry strategies
- Timeout management
- Rate limiting
- Graceful degradation

#### Aula 16: Projeto Final - Sistema de Integrações Completo (8h)
- Django app com múltiplas integrações
- APIs externas
- Webhooks
- Background jobs
- Celery
- Stripe/SendGrid/S3
- Logging e monitoring
- Testes 80%+

## Projetos do Módulo

### Projeto 1: Integração de APIs
**Duração:** 20 horas
- Consumir 3+ APIs públicas
- Cache e retry logic
- Error handling

### Projeto 2: Sistema Completo de Integrações
**Duração:** 40 horas
- Stripe para pagamentos
- SendGrid para email
- Webhooks
- Background jobs com Celery
- Logging
- Testes

### Projeto 3: Revisor
**Duração:** 8 horas

## Stack Tecnológico

- **Django**
- **Celery** + **Redis**
- **Stripe SDK**
- **Boto3** (AWS)
- **Sentry**
- **Prometheus**

## Cronograma Recomendado

| Semana | Horas | Foco | Projeto |
|--------|-------|------|---------|
| 9 | 24 | APIs e Webhooks | Exercícios |
| 10 | 24 | Redis e Celery | Projeto 1 |
| 11 | 24 | Serviços Terceiros | Projeto 2 |
| 12 | 24 | Monitoring | Projeto Final |

---

**Última atualização:** Janeiro de 2025
**Versão:** 2.0
**Nível:** Avançado
