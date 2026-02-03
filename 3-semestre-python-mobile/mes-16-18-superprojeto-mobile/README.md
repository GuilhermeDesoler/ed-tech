# Mês 16-18: Super Projeto Mobile

**Carga Horária:** 288 horas (3 meses × 96 horas)
**Período:** Semanas 13-26
**Pré-requisito:** Conclusão completa dos Mês 13, 14 e 15
**Status:** Projeto Capstone Mobile ⭐⭐⭐

## Visão Geral

Este é o projeto final do semestre e, um dos mais ambiciosos do programa. Uma aplicação mobile completa, production-ready, desenvolvida com React Native e integrada com backend Django/Python. Os alunos trabalharão em duplas ou pequenos grupos, aplicando todos os conhecimentos acumulados.

## Objetivos de Aprendizado

Ao final deste projeto, o aluno será capaz de:

- Arquitetar aplicação mobile de produção
- Desenvolver em React Native com Expo
- Trabalhar com state management (Redux)
- Integrar com APIs backend
- Implementar autenticação mobile
- Usar câmera, localização e outros sensores
- Otimizar performance e battery
- Implementar push notifications
- Fazer build e deploy na App Store e Google Play
- Trabalhar em equipes ágeis
- Apresentar e defender projeto

## Escopo do Projeto

### Requisitos Técnicos Obrigatórios

#### Frontend Mobile (React Native)
- ✓ TypeScript em modo strict
- ✓ Mínimo 5 telas principais
- ✓ Navegação fluida (bottom tabs + stack)
- ✓ Autenticação com JWT
- ✓ Estado global com Redux Toolkit
- ✓ Testes unitários (50+ cases)
- ✓ Testes de integração
- ✓ Performance > 60 FPS
- ✓ Responsivo para múltiplos tamanhos
- ✓ Modo dark/light
- ✓ Acessibilidade básica

#### Backend Django (do Mês 14-15)
- ✓ API REST completa
- ✓ Autenticação JWT
- ✓ Validação robusta
- ✓ Background jobs (Celery)
- ✓ Push notifications
- ✓ Testes 80%+
- ✓ Documentação Swagger

#### DevOps
- ✓ Docker para backend
- ✓ GitHub Actions CI/CD
- ✓ Deploy backend (Railway/Render)
- ✓ EAS Build para mobile
- ✓ TestFlight/Google Play beta

### Temas Sugeridos para Projeto Mobile

#### Opção 1: App de Delivery de Comida
**Complexidade:** Média-Alta
**Funcionalidades:**
- Busca de restaurantes
- Carrinho de pedidos
- Mapa em tempo real (rastreamento)
- Histórico de pedidos
- Reviews e ratings
- Favoritos
- Push notifications para atualizações

**Tech:** Google Maps API, Real-time updates

#### Opção 2: Rede Social / Comunidade Local
**Complexidade:** Média
**Funcionalidades:**
- Feed de posts
- Likes e comentários
- Perfis de usuários
- Mensagens diretas
- Notificações em tempo real
- Descoberta de pessoas
- Localização de eventos

**Tech:** WebSockets, Real-time sync

#### Opção 3: Fitness / Health App
**Complexidade:** Média
**Funcionalidades:**
- Rastreamento de atividades
- Contadores de passos (pedômetro)
- Planos de treino
- Progresso visual
- Desafios sociais
- Integração com Apple Health/Google Fit
- Lembretes e notificações

**Tech:** Sensor API, Background tasks

#### Opção 4: Marketplace de Serviços
**Complexidade:** Alta
**Funcionalidades:**
- Listagem de prestadores
- Agendamento de serviços
- Avaliações
- Sistema de pagamento
- Chat em tempo real
- Histórico de transações
- Proof of work (fotos)

**Tech:** Real-time chat, Payments, Geolocation

#### Opção 5: App de Tarefas / Produtividade
**Complexidade:** Média-Baixa
**Funcionalidades:**
- Gestão de tarefas
- Listas colaborativas
- Lembretes
- Categorização
- Sincronização em tempo real
- Offline-first
- Estatísticas de produtividade

**Tech:** Local storage, Sync engine

## Cronograma (12 Semanas)

### FASE 1: Planejamento (Semanas 13-14 = 2 semanas)

#### Semana 1: Discovery e Design

**Dia 1-2: Definição do Projeto (16h)**
- Escolher tema do projeto
- Listar funcionalidades (MVP)
- Criar user personas
- Escrever user stories
- Wireframes das telas principais

**Entregável:** Product Requirements Document (PRD)

```markdown
# PRD - App de Delivery

## Overview
App mobile para pedir comida de restaurantes locais.

## User Stories
- Como usuário, quero buscar restaurantes próximos
- Como usuário, quero adicionar itens ao carrinho
- Como usuário, quero rastrear meu pedido em tempo real

## MVP Features
- Autenticação
- Busca de restaurantes (por localização, categoria)
- Carrinho de compras
- Checkout
- Rastreamento em tempo real
- Histórico de pedidos
```

**Dia 3-5: Arquitetura Técnica (16h)**
- Design do banco de dados (ERD)
- API endpoints (OpenAPI spec)
- Navegação mobile (wireframes)
- State management structure
- Data flow diagram

**Entregável:** Technical Architecture Document

#### Semana 2: Setup e Configuração

**Dia 1-3: Setup Backend (12h)**
- Criar repositório Git
- Setup Django project
- Estrutura de pastas
- Environment setup
- Database migrations
- First APIs (skeleton)

**Dia 4-5: Setup Frontend Mobile (12h)**
- Criar projeto com Expo
- Setup TypeScript
- Instalar dependências (React Navigation, Redux, etc)
- Estrutura de pastas
- Configurar ESLint e Prettier
- Theme setup (cores, tipografia)

**Entregável:** Repositórios estruturados, build funcionando

### FASE 2: Backend (Semanas 15-17 = 3 semanas)

#### Semana 3-4: APIs Principais

**Dia 1-5 (Semana 1): Autenticação e Usuários (16h)**
- Login/Register endpoints
- JWT tokens
- Refresh token logic
- User profile
- Password reset

**Código Base:**
```python
# Backend - users/serializers.py
class RegisterSerializer(serializers.ModelSerializer):
    password = serializers.CharField(write_only=True)

    class Meta:
        model = User
        fields = ['id', 'email', 'password', 'username']

    def create(self, validated_data):
        user = User.objects.create_user(**validated_data)
        return user

class LoginSerializer(serializers.Serializer):
    email = serializers.EmailField()
    password = serializers.CharField()

    def validate(self, data):
        user = authenticate(username=data['email'], password=data['password'])
        if not user:
            raise serializers.ValidationError("Credenciais inválidas")
        return user

# users/views.py
@api_view(['POST'])
def register(request):
    serializer = RegisterSerializer(data=request.data)
    if serializer.is_valid():
        user = serializer.save()
        token, _ = Token.objects.get_or_create(user=user)
        return Response({'token': token.key, 'user': RegisterSerializer(user).data})
    return Response(serializer.errors, status=400)
```

**Dia 6-10 (Semana 2): Recursos Principais (16h)**
- CRUD de restaurantes
- CRUD de menu items
- CRUD de pedidos
- Busca e filtros
- Paginação

**Dia 11-15 (Semana 3): Integrações (16h)**
- Webhooks para atualizações
- Notificações push
- Background jobs (Celery)
- Cache com Redis
- Rate limiting

**Entregável:** API 100% funcional com 80%+ testes

#### Semana 5: Deploy Backend

**Dia 1-2: Dockerização (8h)**
```dockerfile
FROM python:3.10
WORKDIR /app
COPY requirements.txt .
RUN pip install -r requirements.txt
COPY . .
CMD ["gunicorn", "myproject.wsgi:application", "--bind", "0.0.0.0:8000"]
```

**Dia 3-5: CI/CD e Deployment (16h)**
- GitHub Actions workflow
- Deploy em Railway/Render
- Database migrations automáticas
- Health checks

**Entregável:** Backend rodando em produção

### FASE 3: Frontend Mobile (Semanas 18-22 = 5 semanas)

#### Semana 6-7: Setup e Autenticação

**Dia 1-5 (Semana 1): Navegação e Autenticação (16h)**
```typescript
// navigation/RootNavigator.tsx
import { NavigationContainer } from '@react-navigation/native';
import { createNativeStackNavigator } from '@react-navigation/native-stack';
import { createBottomTabNavigator } from '@react-navigation/bottom-tabs';
import { useAppDispatch, useAppSelector } from '../store';

const Stack = createNativeStackNavigator();
const Tab = createBottomTabNavigator();

function HomeStack() {
  return (
    <Stack.Navigator>
      <Stack.Screen name="HomeScreen" component={HomeScreen} />
      <Stack.Screen name="RestaurantDetail" component={RestaurantDetail} />
    </Stack.Navigator>
  );
}

function AppNavigator() {
  return (
    <Tab.Navigator>
      <Tab.Screen name="Home" component={HomeStack} />
      <Tab.Screen name="Orders" component={OrdersScreen} />
      <Tab.Screen name="Profile" component={ProfileScreen} />
    </Tab.Navigator>
  );
}

export function RootNavigator() {
  const { isSignedIn } = useAppSelector(state => state.auth);

  return (
    <NavigationContainer>
      {isSignedIn ? <AppNavigator /> : <AuthStack />}
    </NavigationContainer>
  );
}
```

**Dia 6-10 (Semana 2): Telas de Autenticação (16h)**
- Login screen com validação
- Register screen
- Forgot password
- Splash screen
- Onboarding

#### Semana 8-9: Telas Principais

**Dia 1-5: Busca e Listagem (16h)**
- Home screen com busca
- Listar restaurantes
- Filtros e categorias
- Maps integration
- Geolocalização

**Código:**
```typescript
// screens/HomeScreen.tsx
import { useState, useEffect } from 'react';
import { View, FlatList, TextInput } from 'react-native';
import * as Location from 'expo-location';
import { useAppDispatch, useAppSelector } from '../store';
import { fetchRestaurants } from '../store/restaurantSlice';

export function HomeScreen() {
  const [searchText, setSearchText] = useState('');
  const dispatch = useAppDispatch();
  const restaurants = useAppSelector(state => state.restaurants.items);

  useEffect(() => {
    const getLocation = async () => {
      const { status } = await Location.requestForegroundPermissionsAsync();
      if (status === 'granted') {
        const location = await Location.getCurrentPositionAsync({});
        dispatch(fetchRestaurants({
          lat: location.coords.latitude,
          lng: location.coords.longitude,
          search: searchText
        }));
      }
    };
    getLocation();
  }, [searchText, dispatch]);

  return (
    <View>
      <TextInput
        placeholder="Buscar restaurantes..."
        value={searchText}
        onChangeText={setSearchText}
      />
      <FlatList
        data={restaurants}
        renderItem={({ item }) => <RestaurantCard restaurant={item} />}
        keyExtractor={item => item.id.toString()}
      />
    </View>
  );
}
```

**Dia 6-10: Carrinho e Checkout (16h)**
- Carrinho visual
- Adicionar/remover itens
- Checkout flow
- Endereço de entrega
- Método de pagamento

**Dia 11-15: Rastreamento (16h)**
- Mapa em tempo real
- Atualização de status
- Notificações
- Histórico de pedidos

#### Semana 10-11: Polish e Testes

**Dia 1-5: Testes (16h)**
```typescript
// __tests__/screens/HomeScreen.test.tsx
import { render, screen, waitFor } from '@testing-library/react-native';
import { Provider } from 'react-redux';
import { HomeScreen } from '../HomeScreen';
import { store } from '../store';

describe('HomeScreen', () => {
  it('should render search input', () => {
    render(
      <Provider store={store}>
        <HomeScreen />
      </Provider>
    );
    expect(screen.getByPlaceholderText('Buscar restaurantes...')).toBeTruthy();
  });

  it('should load restaurants', async () => {
    render(
      <Provider store={store}>
        <HomeScreen />
      </Provider>
    );

    await waitFor(() => {
      expect(screen.getByTestId('restaurant-list')).toBeTruthy();
    });
  });
});
```

**Dia 6-10: Performance e UX (16h)**
- Otimizar re-renders
- Lazy load de imagens
- Caching de dados
- Indicadores de carregamento
- Error states
- Empty states

**Dia 11-15: Dark mode e Acessibilidade (16h)**
- Dark mode implementation
- Screen reader support
- Contrast compliance
- Touch targets > 44x44dp

### FASE 4: Integração e Deploy (Semanas 23-25 = 3 semanas)

#### Semana 12: Integração Full-Stack

**Dia 1-5: Conectar Frontend ao Backend (16h)**
- Variáveis de ambiente
- API client setup
- Integração de todas as telas
- Teste end-to-end
- Debugging

**Código:**
```typescript
// api/client.ts
import axios from 'axios';
import * as SecureStore from 'expo-secure-store';

const API_URL = process.env.EXPO_PUBLIC_API_URL;

const apiClient = axios.create({
  baseURL: API_URL,
  timeout: 10000,
});

apiClient.interceptors.request.use(async (config) => {
  const token = await SecureStore.getItemAsync('auth_token');
  if (token) {
    config.headers.Authorization = `Bearer ${token}`;
  }
  return config;
});

apiClient.interceptors.response.use(
  response => response,
  async error => {
    if (error.response?.status === 401) {
      // Logout e redirecionar para login
      await SecureStore.deleteItemAsync('auth_token');
    }
    return Promise.reject(error);
  }
);

export default apiClient;
```

**Dia 6-10: Push Notifications (16h)**
- Setup Expo Push Notifications
- Salvar tokens no backend
- Enviar notificações
- Handling de notificações
- Local notifications para offline

**Dia 11-15: Real-time Updates (16h)**
- WebSockets setup
- Real-time order tracking
- Sync de dados
- Offline-first sync

**Entregável:** App completamente funcional

#### Semana 13-14: Build e Deploy

**Dia 1-5 (Semana 1): EAS Build (16h)**
```bash
# eas.json
{
  "build": {
    "production": {
      "ios": {
        "resourceClass": "large"
      },
      "android": {
        "resourceClass": "large"
      }
    }
  },
  "submit": {
    "production": {
      "ios": {
        "appleId": "...",
        "appleTeamId": "...",
        "ascAppId": "..."
      },
      "android": {
        "serviceAccount": "..."
      }
    }
  }
}

# Build para produção
eas build --platform all --profile production
```

**Dia 6-10 (Semana 1): App Store & Google Play (16h)**
- Criar contas developer
- Preparar assets (screenshots, description)
- Submeter para review
- Setup beta testing (TestFlight, Google Play Beta)

**Dia 11-15 (Semana 2): Monitoring (16h)**
- Sentry setup
- Crash reporting
- Analytics (amplitude, mixpanel)
- Performance monitoring
- User behavior tracking

**Dia 16-20 (Semana 2): Documentação (16h)**
- README completo
- Setup guide
- API documentation
- Architecture diagram
- Known issues e roadmap

**Entregável:** App em beta nas lojas

### FASE 5: Apresentação Final (Semana 26 = 1 semana)

**Dia 1-3: Demo Prep (12h)**
- Preparar demo script
- Slide deck
- Demo video
- Troubleshooting

**Dia 4-5: Apresentação (8h)**
- Demo ao vivo
- Apresentação de arquitetura
- Q&A
- Feedback

## Requisitos e Critérios

### Funcionalidades Obrigatórias
- [ ] Autenticação completa
- [ ] Mínimo 5 telas principais
- [ ] Integração com backend
- [ ] Estado global com Redux
- [ ] Testes (50+ casos)
- [ ] Push notifications
- [ ] Real-time updates
- [ ] Offline support
- [ ] Dark/light mode
- [ ] Build e deploy

### Qualidade de Código
- [ ] TypeScript strict mode
- [ ] ESLint e Prettier
- [ ] Code review feito
- [ ] Sem console.errors
- [ ] Sem warnings
- [ ] Padrões de design

### Performance
- [ ] 60 FPS consistently
- [ ] < 100MB app size
- [ ] < 5s cold start
- [ ] Responsive ao usuário

### Documentação
- [ ] README com setup
- [ ] API docs (Swagger)
- [ ] Architecture diagram
- [ ] Known issues

### DevOps
- [ ] CI/CD automático
- [ ] Backend em produção
- [ ] App em beta nas lojas
- [ ] Monitoring ativo

## Stack Tecnológico Completo

### Mobile
- React Native 0.71+
- Expo
- TypeScript
- Redux Toolkit
- React Navigation
- React Native Maps
- Expo Notifications
- Secure Store (tokens)
- Jest + React Native Testing Library

### Backend
- Django 4.x
- Django REST Framework
- Celery + Redis
- PostgreSQL
- Stripe/Payments
- SendGrid
- Sentry
- Docker

### DevOps
- GitHub Actions
- EAS Build
- Railway/Render
- TestFlight
- Google Play Console

## Equipes

Projeto pode ser feito em:
- **Individual:** Escopo reduzido (3-4 telas)
- **Dupla:** Escopo completo (5+ telas)
- **Grupo de 3:** Escopo expandido (full-stack com backend)

## Avaliação Final

### Rubrica de Avaliação (100 pontos)

#### Funcionalidade (25 pontos)
- MVP completo: 15 pontos
- Polimento e UX: 10 pontos

#### Código & Arquitetura (25 pontos)
- TypeScript e tipagem: 10 pontos
- Padrões de design: 10 pontos
- Testes: 5 pontos

#### Backend (15 pontos) - Se no grupo
- APIs robustas: 10 pontos
- Database design: 5 pontos

#### DevOps & Deploy (15 pontos)
- CI/CD: 8 pontos
- Deploy funcional: 7 pontos

#### Apresentação (20 pontos)
- Demo: 10 pontos
- Documentação: 5 pontos
- Explanação técnica: 5 pontos

### Critério de Aprovação
- Mínimo 70/100
- Todas as funcionalidades obrigatórias implementadas
- Código de qualidade profissional
- App funcional em produção

## Recursos Adicionais

### Documentação
- [React Native Docs](https://reactnative.dev)
- [Expo Docs](https://docs.expo.dev)
- [Redux Toolkit](https://redux-toolkit.js.org)
- [React Navigation](https://reactnavigation.org)

### Ferramentas
- Android Studio (emulator)
- Xcode (simulator iOS)
- VS Code
- Expo Go (mobile testing)
- Charles/Proxyman (network debugging)

### Templates Úteis
- Starter template com Redux
- Component library
- API service setup
- Navigation templates

## Dicas para Sucesso

### Planejamento
- MVP bem definido
- Não scope creep
- Timeline realista
- Comunicação clara

### Desenvolvimento
- Backend-first
- Teste enquanto desenvolve
- Deploy cedo e frequente
- Code review constante

### Qualidade
- TypeScript desde o início
- Testes durante dev
- Performance profiling
- User testing beta

### Equipe
- Daily standups
- GitHub issues bem documentadas
- Code review construtor
- Pair programming quando necessário

## Sucesso Esperado

Ao terminar este projeto, você terá:

- **Portfolio Profissional:** App pronto para mostrar
- **Experiência Full-Stack:** Mobile + Backend
- **Código em Produção:** Real users
- **Domínio Completo:** Arquitetura a deploy
- **Confiança Profissional:** Para novos desafios

Este é um projeto de nível senior em ambição e nível junior em execução.

Boa sorte e divirta-se desenvolvendo!

---

**Última atualização:** Janeiro de 2025
**Versão:** 2.0
**Nível:** Profissional/Production
**Duração:** 12 Semanas (288 horas)
