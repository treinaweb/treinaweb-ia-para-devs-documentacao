# Decisões Tecnológicas - AgendaLocal

**Versão:** 1.0  
**Data:** 22 de novembro de 2025  
**Tipo de Projeto:** MVP Focado - Projeto de Estudos

---

## 📋 Índice

1. [Visão Geral](#visão-geral)
2. [Arquitetura](#arquitetura)
3. [Stack Tecnológica](#stack-tecnológica)
4. [Infraestrutura](#infraestrutura)
5. [Serviços Externos](#serviços-externos)
6. [DevOps e Ferramentas](#devops-e-ferramentas)
7. [Bibliotecas Principais](#bibliotecas-principais)
8. [Estrutura de Pastas](#estrutura-de-pastas)
9. [Pontos de Atenção](#pontos-de-atenção)
10. [Próximos Passos](#próximos-passos)
11. [Recursos de Aprendizado](#recursos-de-aprendizado)

---

## Visão Geral

Este documento consolida todas as **decisões técnicas** tomadas para o projeto **AgendaLocal**, incluindo arquitetura, tecnologias, ferramentas e justificativas para cada escolha.

### Contexto do Projeto

- **Objetivo**: Plataforma de agendamento para profissionais autônomos locais
- **Tipo**: MVP (Minimum Viable Product) focado em aprendizado técnico
- **Funcionalidades Críticas**: 
  - Busca geoespacial (GPS + raio)
  - Gestão de disponibilidade e agendamentos
  - Autenticação JWT
  - Upload de imagens

---

## Arquitetura

### Modelo Arquitetural

**Decisão**: API REST + Front-end Separado (SPA)

**Justificativa**:
- ✅ Separação clara de responsabilidades (back-end/front-end)
- ✅ Reutilização da API (preparado para futuro app mobile)
- ✅ Tecnologias independentes e especializadas
- ✅ Escalabilidade futura facilitada
- ✅ Padrão moderno de mercado
- ✅ Ideal para projetos de aprendizado

**Alternativas Consideradas**:
- ❌ Monolito Modular: menos flexível para evolução
- ❌ Microsserviços: complexidade excessiva para MVP
- ❌ Serverless: trade-offs não ideais para requisitos do projeto

### Comunicação

- **Protocolo**: HTTPS/TLS
- **Formato de Dados**: JSON
- **Autenticação**: JWT Bearer Token
- **CORS**: Configurado para domínios específicos (Vercel ↔ Fly.io)

---

## Stack Tecnológica

### Back-end

| Componente         | Tecnologia | Versão       | Justificativa                                                                          |
| ------------------ | ---------- | ------------ | -------------------------------------------------------------------------------------- |
| **Linguagem**      | Python     | 3.11+        | Código limpo, excelente para geolocalização, bibliotecas robustas                      |
| **Framework**      | FastAPI    | Latest       | Performance, validação automática (Pydantic), docs interativas (Swagger), async nativo |
| **Banco de Dados** | PostgreSQL | 15+          | Relacional robusto, suporte a JSON, UUIDs nativos, ENUMs                               |
| **Extensão Geo**   | PostGIS    | Latest       | Busca geoespacial (ST_DWithin, ST_Distance), índices GiST                              |
| **ORM**            | SQLAlchemy | 2.0+ (async) | Padrão de mercado, suporte async, robusto                                              |
| **Migrations**     | Alembic    | Latest       | Versionamento de schema, integrado ao SQLAlchemy                                       |
| **Autenticação**   | JWT        | -            | Stateless, escalável, padrão REST moderno                                              |
| **Hash de Senha**  | bcrypt     | via passlib  | Segurança comprovada, proteção contra rainbow tables                                   |
| **Validação**      | Pydantic   | v2           | Type-safety, validação automática, integrado ao FastAPI                                |
| **ASGI Server**    | Uvicorn    | Latest       | Performance, suporte HTTP/2, WebSockets (futuro)                                       |

**Decisões Técnicas Back-end**:

1. **Python vs Node.js/Go**
   - ✅ Python escolhido por: código legível, bibliotecas geoespaciais (geopy, shapely), curva de aprendizado suave
   - FastAPI oferece performance comparável ao Node.js com benefícios do ecossistema Python

2. **FastAPI vs Django/Flask**
   - ✅ FastAPI: async nativo, validação automática, documentação interativa, moderno
   - ❌ Django: overhead para API simples, admin panel não necessário no MVP
   - ❌ Flask: requer montar tudo manualmente, sem validação automática

3. **PostgreSQL + PostGIS vs MongoDB/MySQL**
   - ✅ PostgreSQL: busca geoespacial robusta (PostGIS), modelo relacional bem definido
   - ❌ MongoDB: modelo é claramente relacional, JOINs seriam complexos
   - ❌ MySQL: suporte geoespacial inferior ao PostGIS

4. **SQLAlchemy vs Tortoise ORM**
   - ✅ SQLAlchemy: comunidade maior, documentação extensa, suporte PostGIS via GeoAlchemy2
   - ❌ Tortoise: comunidade menor, menos recursos avançados

5. **JWT vs Sessions/OAuth**
   - ✅ JWT: stateless, alinhado com REST, escalável, aprendizado valioso
   - ❌ Sessions: stateful, CORS complexo com domínios separados
   - 🔮 OAuth2 social: planejado para versão futura

---

### Front-end

| Componente           | Tecnologia            | Versão | Justificativa                                          |
| -------------------- | --------------------- | ------ | ------------------------------------------------------ |
| **Framework**        | Vue                   | 3.x    | Sintaxe intuitiva, Composition API moderna, produtivo  |
| **Arquitetura**      | SPA                   | -      | Simplicidade de desenvolvimento, interatividade fluída |
| **Roteamento**       | Vue Router            | 4.x    | Navegação client-side, guards para autenticação        |
| **State Management** | Pinia                 | Latest | State management moderno, type-safe, DevTools          |
| **HTTP Client**      | Axios                 | Latest | Interceptors (JWT), tratamento de erros, popular       |
| **Build Tool**       | Vite                  | Latest | Build rápido, HMR instantâneo, moderno                 |
| **Linguagem**        | JavaScript/TypeScript | ES6+   | TypeScript opcional para type-safety                   |
| **CSS Framework**    | Tailwind CSS          | 3.x    | Utility-first, responsivo, produtivo, customizável     |
| **Testes**           | Vitest                | Latest | Rápido, compatível Vue 3, API similar Jest             |

**Decisões Técnicas Front-end**:

1. **Vue vs React/Svelte**
   - ✅ Vue 3: sintaxe mais simples que React, curva de aprendizado suave, produtivo
   - ❌ React: mais verboso, ecossistema maior mas Vue suficiente para projeto
   - ❌ Svelte: ecossistema menor, menos profissionais no mercado

2. **Vue SPA vs Nuxt (SSR)**
   - ✅ Vue SPA: simplicidade de desenvolvimento e deploy
   - ❌ Nuxt: SEO seria ideal mas adiciona complexidade; pode ser implementado em v2.0
   - 💡 Deploy em Vercel facilita migração futura para Nuxt

3. **Tailwind vs Bootstrap/Vuetify**
   - ✅ Tailwind: flexibilidade total, bundle pequeno, moderno
   - ❌ Bootstrap: menos customizável, não é padrão atual
   - ❌ Vuetify: componentes prontos mas menos flexível

---

## Infraestrutura

### Hospedagem e Deploy

| Componente          | Serviço         | Plano         | Custo Inicial       | Justificativa                                                                 |
| ------------------- | --------------- | ------------- | ------------------- | ----------------------------------------------------------------------------- |
| **Front-end**       | Vercel          | Hobby (Free)  | $0                  | Otimizado para Vue/SPA, CDN global, deploy automático via Git, SSL automático |
| **Back-end**        | Fly.io          | Shared CPU    | Free tier → ~$5/mês | PostgreSQL gerenciado, boa performance global, Docker nativo                  |
| **Banco de Dados**  | Fly.io Postgres | Shared        | Incluído            | PostGIS suportado, backups automáticos, managed                               |
| **Storage Imagens** | AWS S3          | Pay-as-you-go | ~$0.50/mês inicial  | Escalável, controle total, CDN via CloudFront (opcional)                      |
| **Email (Dev)**     | Mailtrap        | Free          | $0                  | Excelente para testes, inbox virtual                                          |
| **Email (Prod)**    | A definir       | -             | Futuro              | Resend, SendGrid ou Mailgun quando escalar                                    |

**Decisões de Infraestrutura**:

1. **Vercel + Fly.io vs Railway vs VPS**
   - ✅ Vercel: melhor para Vue/SPA, free tier generoso, deploy git
   - ✅ Fly.io: PostgreSQL + PostGIS gerenciado, boa performance
   - ❌ Railway: alternativa válida mas Fly.io tem melhor suporte PostGIS
   - ❌ VPS (DigitalOcean): controle total mas requer DevOps manual

2. **AWS S3 vs Cloudinary**
   - ✅ S3: controle total, custo previsível, escalável
   - ❌ Cloudinary: otimização automática mas free tier mais limitado
   - 💡 S3 + CloudFront CDN quando necessário

3. **Mailtrap vs Produção direta**
   - ✅ Mailtrap: perfeito para dev/staging, evita envios acidentais
   - 💡 Migrar para Resend/SendGrid em produção

### Ambiente de Desenvolvimento

```yaml
# docker-compose.yml (desenvolvimento local)
services:
  postgres:
    image: postgis/postgis:15-3.3
    ports:
      - "5432:5432"
    environment:
      POSTGRES_DB: agendalocal_dev
      POSTGRES_USER: dev
      POSTGRES_PASSWORD: dev
    volumes:
      - postgres_data:/var/lib/postgresql/data

  redis:
    image: redis:7-alpine
    ports:
      - "6379:6379"

volumes:
  postgres_data:
```

---

## Serviços Externos

### APIs de Terceiros

| Serviço                 | Uso                   | Provedor                           | Free Tier           | Status     |
| ----------------------- | --------------------- | ---------------------------------- | ------------------- | ---------- |
| **Geocoding**           | Endereço → Lat/Long   | Google Maps API ou Nominatim (OSM) | Limitado / Gratuito | Necessário |
| **Geolocation**         | GPS do navegador      | Browser API nativa                 | Gratuito            | Necessário |
| **Monitoramento Erros** | Stack traces, alertas | Sentry                             | 5.000 eventos/mês   | Necessário |
| **Uptime Monitor**      | Health checks         | UptimeRobot                        | 50 monitores        | Necessário |
| **CDN (futuro)**        | Cache de imagens      | CloudFront                         | Pay-as-you-go       | Opcional   |

**Decisões de Serviços Externos**:

1. **Google Maps vs Nominatim (OpenStreetMap)**
   - ✅ Google Maps: mais preciso, documentação melhor
   - ✅ Nominatim: gratuito ilimitado, open-source
   - 💡 Começar com Nominatim, migrar para Google Maps se precisão for problema

2. **Sentry vs Alternativas**
   - ✅ Sentry: líder de mercado, source maps, integração Python + Vue
   - ❌ Rollbar/Bugsnag: alternativas válidas mas Sentry tem melhor free tier

---

## DevOps e Ferramentas

### CI/CD

**Pipeline GitHub Actions**:

```yaml
# .github/workflows/deploy.yml
name: Deploy

on:
  push:
    branches: [main]

jobs:
  backend:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - name: Deploy to Fly.io
        uses: superfly/flyctl-actions/setup-flyctl@master
      - run: flyctl deploy --remote-only

  frontend:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - name: Deploy to Vercel
        uses: amondnet/vercel-action@v20
```

### Ferramentas de Desenvolvimento

| Ferramenta          | Uso                         | Justificativa                                     |
| ------------------- | --------------------------- | ------------------------------------------------- |
| **Git**             | Versionamento               | GitHub (público ou privado)                       |
| **CI/CD**           | Deploy automático           | GitHub Actions (2.000 min/mês grátis)             |
| **Linting Back**    | Code quality                | Ruff + Black (formatação)                         |
| **Linting Front**   | Code quality                | ESLint + Prettier                                 |
| **Type Checking**   | Type safety                 | mypy (Python) + TypeScript (opcional)             |
| **Testes Back**     | Testes unitários/integração | Pytest + pytest-asyncio                           |
| **Testes Front**    | Testes componentes/rotas    | Vitest + Vue Test Utils                           |
| **API Testing**     | Testes manuais              | Swagger UI (integrado FastAPI) + Postman/Insomnia |
| **Containerização** | Ambiente local              | Docker + docker-compose                           |

### Monitoramento

| Aspecto           | Ferramenta        | Free Tier         | Objetivo                            |
| ----------------- | ----------------- | ----------------- | ----------------------------------- |
| **Erros (Back)**  | Sentry Python SDK | 5.000 eventos/mês | Stack traces, performance           |
| **Erros (Front)** | Sentry Vue SDK    | Incluído          | Erros de runtime Vue                |
| **Uptime**        | UptimeRobot       | 50 monitores      | Health checks a cada 5min           |
| **Logs**          | Fly.io Logs       | Built-in          | Logs centralizados (suficiente MVP) |
| **Métricas**      | Fly.io Metrics    | Built-in          | CPU, memória, requests              |

---

## Bibliotecas Principais

### Python (Back-end)

```txt
# requirements.txt (principais)

# Framework
fastapi[all]==0.104.1
uvicorn[standard]==0.24.0

# Database
sqlalchemy[asyncio]==2.0.23
alembic==1.12.1
asyncpg==0.29.0
psycopg2-binary==2.9.9
geoalchemy2==0.14.2

# Authentication
python-jose[cryptography]==3.3.0
passlib[bcrypt]==1.7.4

# Validation
pydantic==2.5.0
pydantic-settings==2.1.0
email-validator==2.1.0

# AWS S3
boto3==1.33.6

# Email
python-multipart==0.0.6

# Geocoding
geopy==2.4.1

# Testing
pytest==7.4.3
pytest-asyncio==0.21.1
httpx==0.25.2

# Code Quality
ruff==0.1.6
black==23.11.0
mypy==1.7.1

# Monitoring
sentry-sdk[fastapi]==1.38.0
```

### JavaScript (Front-end)

```json
{
  "dependencies": {
    "vue": "^3.3.8",
    "vue-router": "^4.2.5",
    "pinia": "^2.1.7",
    "axios": "^1.6.2",
    "@vueuse/core": "^10.6.1"
  },
  "devDependencies": {
    "@vitejs/plugin-vue": "^4.5.0",
    "vite": "^5.0.2",
    "tailwindcss": "^3.3.5",
    "autoprefixer": "^10.4.16",
    "postcss": "^8.4.31",
    "vitest": "^1.0.1",
    "@vue/test-utils": "^2.4.2",
    "eslint": "^8.54.0",
    "eslint-plugin-vue": "^9.18.1",
    "prettier": "^3.1.0",
    "@sentry/vue": "^7.84.0"
  }
}
```

---

## Estrutura de Pastas

### Back-end (FastAPI)

```
agendalocal-api/
├── app/
│   ├── api/                    # Endpoints (routers)
│   │   ├── v1/
│   │   │   ├── __init__.py
│   │   │   ├── auth.py         # Login, register, refresh
│   │   │   ├── users.py        # User endpoints
│   │   │   ├── professionals.py
│   │   │   ├── services.py
│   │   │   ├── availabilities.py
│   │   │   ├── bookings.py
│   │   │   └── categories.py
│   │   └── deps.py             # Dependencies (get_current_user)
│   ├── core/                   # Core config
│   │   ├── __init__.py
│   │   ├── config.py           # Settings (Pydantic BaseSettings)
│   │   ├── security.py         # JWT, password hashing
│   │   └── database.py         # SQLAlchemy engine, session
│   ├── models/                 # SQLAlchemy models
│   │   ├── __init__.py
│   │   ├── user.py
│   │   ├── client.py
│   │   ├── professional.py
│   │   ├── service.py
│   │   ├── availability.py
│   │   ├── booking.py
│   │   └── category.py
│   ├── schemas/                # Pydantic schemas (DTOs)
│   │   ├── __init__.py
│   │   ├── user.py
│   │   ├── professional.py
│   │   ├── service.py
│   │   ├── availability.py
│   │   ├── booking.py
│   │   └── token.py
│   ├── services/               # Business logic
│   │   ├── __init__.py
│   │   ├── auth_service.py
│   │   ├── user_service.py
│   │   ├── professional_service.py
│   │   ├── booking_service.py
│   │   ├── geocoding_service.py
│   │   ├── email_service.py
│   │   └── storage_service.py  # S3 uploads
│   ├── utils/                  # Utilities
│   │   ├── __init__.py
│   │   ├── geo.py              # Haversine, distance calculations
│   │   └── validators.py
│   └── main.py                 # FastAPI app initialization
├── alembic/                    # Database migrations
│   ├── versions/
│   ├── env.py
│   └── script.py.mako
├── tests/                      # Pytest tests
│   ├── conftest.py
│   ├── test_api/
│   │   ├── test_auth.py
│   │   ├── test_professionals.py
│   │   └── test_bookings.py
│   └── test_services/
├── .env.example                # Environment variables template
├── .gitignore
├── alembic.ini
├── docker-compose.yml          # Local PostgreSQL + Redis
├── Dockerfile
├── fly.toml                    # Fly.io config
├── pyproject.toml              # Ruff, Black config
├── requirements.txt
└── README.md
```

### Front-end (Vue 3)

```
agendalocal-web/
├── public/
│   ├── favicon.ico
│   └── robots.txt
├── src/
│   ├── assets/                 # Images, fonts
│   │   ├── images/
│   │   └── styles/
│   │       └── main.css        # Tailwind imports
│   ├── components/             # Vue components
│   │   ├── common/
│   │   │   ├── AppHeader.vue
│   │   │   ├── AppFooter.vue
│   │   │   ├── LoadingSpinner.vue
│   │   │   └── ErrorMessage.vue
│   │   ├── auth/
│   │   │   ├── LoginForm.vue
│   │   │   └── RegisterForm.vue
│   │   ├── professional/
│   │   │   ├── ProfessionalCard.vue
│   │   │   ├── ProfessionalProfile.vue
│   │   │   └── ServiceList.vue
│   │   └── booking/
│   │       ├── BookingCard.vue
│   │       ├── BookingForm.vue
│   │       └── AvailabilityCalendar.vue
│   ├── composables/            # Composition functions
│   │   ├── useAuth.js
│   │   ├── useGeolocation.js
│   │   └── useApi.js
│   ├── layouts/
│   │   ├── DefaultLayout.vue
│   │   └── AuthLayout.vue
│   ├── router/
│   │   └── index.js            # Vue Router config
│   ├── services/               # API calls
│   │   ├── api.js              # Axios instance
│   │   ├── authService.js
│   │   ├── professionalService.js
│   │   └── bookingService.js
│   ├── stores/                 # Pinia stores
│   │   ├── auth.js
│   │   ├── professionals.js
│   │   └── bookings.js
│   ├── views/                  # Page components
│   │   ├── Home.vue
│   │   ├── auth/
│   │   │   ├── Login.vue
│   │   │   └── Register.vue
│   │   ├── client/
│   │   │   ├── Search.vue
│   │   │   ├── ProfessionalDetail.vue
│   │   │   ├── Booking.vue
│   │   │   └── MyBookings.vue
│   │   └── professional/
│   │       ├── Dashboard.vue
│   │       ├── Profile.vue
│   │       ├── Services.vue
│   │       ├── Availability.vue
│   │       └── Bookings.vue
│   ├── App.vue
│   └── main.js
├── tests/                      # Vitest tests
│   ├── components/
│   └── views/
├── .env.example
├── .eslintrc.js
├── .gitignore
├── .prettierrc
├── index.html
├── package.json
├── postcss.config.js
├── tailwind.config.js
├── vite.config.js
├── vitest.config.js
└── README.md
```

---

## Pontos de Atenção

### Desafios Técnicos Identificados

#### 1. Busca Geoespacial (PostGIS)

**Desafio**: Implementar busca eficiente por raio com ordenação por distância.

**Solução**:
```sql
-- Query exemplo com PostGIS
SELECT 
    p.id, p.full_name, p.city,
    ST_Distance(
        p.location::geography,
        ST_SetSRID(ST_Point(:longitude, :latitude), 4326)::geography
    ) / 1000 AS distance_km
FROM professionals p
WHERE ST_DWithin(
    p.location::geography,
    ST_SetSRID(ST_Point(:longitude, :latitude), 4326)::geography,
    :radius_meters
)
AND p.is_active = true
ORDER BY distance_km ASC
LIMIT 50;
```

**Índice necessário**:
```sql
CREATE INDEX idx_professionals_location 
ON professionals USING GIST (location);
```

#### 2. Upload de Imagens para S3

**Desafio**: Upload seguro, otimização de imagens, URLs assinadas.

**Solução**:
```python
# services/storage_service.py
import boto3
from PIL import Image
from io import BytesIO

class StorageService:
    def __init__(self):
        self.s3 = boto3.client('s3')
        self.bucket = settings.S3_BUCKET
    
    async def upload_profile_photo(self, file: UploadFile, user_id: str):
        # 1. Validar formato/tamanho
        # 2. Otimizar imagem (resize, compress)
        # 3. Upload para S3 com path único
        # 4. Retornar CloudFront URL
        pass
```

**Configuração S3**:
- Bucket privado
- CORS configurado para domínio Vercel
- CloudFront (opcional) para CDN
- Lifecycle policy para deletar uploads não finalizados

#### 3. JWT Refresh Token Flow

**Desafio**: Implementar renovação segura de tokens sem re-login.

**Solução**:
```python
# core/security.py
def create_access_token(data: dict, expires_delta: timedelta):
    # Access token: 15-30 minutos
    pass

def create_refresh_token(data: dict):
    # Refresh token: 7 dias
    # Armazenar hash no DB (opcional para revogação)
    pass
```

**Front-end (Axios interceptor)**:
```javascript
// services/api.js
api.interceptors.response.use(
  response => response,
  async error => {
    if (error.response.status === 401 && !originalRequest._retry) {
      originalRequest._retry = true;
      const newToken = await refreshAccessToken();
      api.defaults.headers.common['Authorization'] = `Bearer ${newToken}`;
      return api(originalRequest);
    }
    return Promise.reject(error);
  }
);
```

#### 4. Email Verification

**Desafio**: Gerar tokens seguros com expiração, enviar emails transacionais.

**Solução**:
```python
# services/email_service.py
import secrets
from datetime import datetime, timedelta

class EmailService:
    async def send_verification_email(self, user: User):
        # 1. Gerar token único (secrets.token_urlsafe)
        token = secrets.token_urlsafe(32)
        
        # 2. Salvar no DB com expiração (24h)
        await create_verification_token(user.id, token, expires_in=24)
        
        # 3. Enviar email com link
        link = f"{FRONTEND_URL}/auth/verify?token={token}"
        await send_email(user.email, "Confirme seu email", link)
```

#### 5. CORS Configuration

**Desafio**: Permitir Vercel acessar Fly.io API sem expor para qualquer origem.

**Solução**:
```python
# main.py
from fastapi.middleware.cors import CORSMiddleware

app.add_middleware(
    CORSMiddleware,
    allow_origins=[
        "https://agendalocal.vercel.app",
        "http://localhost:3000"  # Desenvolvimento
    ],
    allow_credentials=True,
    allow_methods=["*"],
    allow_headers=["*"],
)
```

### Segurança

#### Checklist de Segurança

- [x] **HTTPS obrigatório**: Vercel + Fly.io SSL automático
- [x] **CORS restritivo**: Apenas domínios permitidos
- [x] **Validação de inputs**: Pydantic valida todos os dados
- [x] **SQL Injection**: SQLAlchemy ORM previne
- [x] **XSS**: Vue escapa HTML por padrão
- [x] **CSRF**: JWT stateless não vulnerável a CSRF
- [x] **Rate Limiting**: Considerar middleware FastAPI (SlowAPI)
- [x] **Senhas**: bcrypt com salt rounds adequados
- [x] **JWT Secret**: Variável de ambiente, rotacionada periodicamente
- [x] **S3 Buckets**: Privados, acesso via signed URLs
- [ ] **2FA**: Planejar para v2.0
- [ ] **API Versioning**: `/api/v1/` preparado para v2

#### Environment Variables (Segredos)

```bash
# .env.example

# Database
DATABASE_URL=postgresql+asyncpg://user:pass@host:5432/dbname

# JWT
SECRET_KEY=your-secret-key-min-32-chars
ALGORITHM=HS256
ACCESS_TOKEN_EXPIRE_MINUTES=30
REFRESH_TOKEN_EXPIRE_DAYS=7

# AWS S3
AWS_ACCESS_KEY_ID=your-key
AWS_SECRET_ACCESS_KEY=your-secret
AWS_S3_BUCKET=agendalocal-uploads
AWS_REGION=us-east-1

# Email
MAILTRAP_TOKEN=your-mailtrap-token  # Dev
# SENDGRID_API_KEY=  # Produção

# Geocoding
GOOGLE_MAPS_API_KEY=your-key  # Ou usar Nominatim (sem key)

# Sentry
SENTRY_DSN=your-sentry-dsn

# Frontend URL (para emails)
FRONTEND_URL=https://agendalocal.vercel.app

# Environment
ENVIRONMENT=development  # ou production
```

### Performance

#### Otimizações Planejadas

1. **Database**:
   - Índices em: `email`, `location` (GIST), `scheduled_date`, `professional_id`, `client_id`
   - Connection pooling (SQLAlchemy async)
   - Query optimization (evitar N+1 com `selectinload`)

2. **API**:
   - Cache com Redis (futuro) para listagens frequentes
   - Paginação em todas as listagens
   - Compressão gzip de respostas

3. **Front-end**:
   - Lazy loading de rotas (Vue Router)
   - Lazy loading de imagens
   - Debounce em buscas
   - Otimização de imagens (Tailwind JIT)

4. **CDN**:
   - Vercel CDN para assets estáticos (automático)
   - CloudFront para imagens S3 (quando escalar)

---

## Próximos Passos

### Fase 1: Setup Inicial (Semana 1)

#### Infraestrutura
- [ ] Criar repositórios GitHub (agendalocal-api, agendalocal-web)
- [ ] Configurar Fly.io: criar app + PostgreSQL com PostGIS
- [ ] Configurar Vercel: conectar repositório front-end
- [ ] Criar bucket S3 privado + configurar CORS
- [ ] Criar conta Mailtrap para emails de dev
- [ ] Configurar Sentry (back-end + front-end)
- [ ] Configurar UptimeRobot para health checks

#### Ambiente Local
- [ ] Criar `docker-compose.yml` (PostgreSQL + Redis)
- [ ] Configurar `.env.example` com todas as variáveis
- [ ] Documentar setup no README de cada repositório

### Fase 2: Back-end Core (Semanas 2-3)

#### Database & Models
- [ ] Criar models SQLAlchemy (User, Client, Professional, etc.)
- [ ] Configurar Alembic e criar migration inicial
- [ ] Adicionar índices (location GIST, foreign keys)
- [ ] Seed inicial: categorias pré-definidas

#### Authentication
- [ ] Implementar JWT (access + refresh tokens)
- [ ] Endpoint: POST `/api/v1/auth/register`
- [ ] Endpoint: POST `/api/v1/auth/login`
- [ ] Endpoint: POST `/api/v1/auth/refresh`
- [ ] Endpoint: POST `/api/v1/auth/verify-email?token=`
- [ ] Endpoint: POST `/api/v1/auth/forgot-password`
- [ ] Endpoint: POST `/api/v1/auth/reset-password`
- [ ] Dependency: `get_current_user`

#### Profissionais
- [ ] CRUD completo de Professional
- [ ] Upload de foto de perfil (S3)
- [ ] Geocoding: endereço → lat/long (Google Maps ou Nominatim)
- [ ] Endpoint: GET `/api/v1/professionals/search` (geolocalização)

#### Serviços e Disponibilidade
- [ ] CRUD de Services (vinculado a Professional)
- [ ] CRUD de Availabilities (blocos semanais)

#### Agendamentos
- [ ] Endpoint: POST `/api/v1/bookings` (criar agendamento)
- [ ] Endpoint: GET `/api/v1/bookings/me` (listar agendamentos do usuário)
- [ ] Endpoint: PATCH `/api/v1/bookings/{id}/cancel` (cancelar)

#### Testes
- [ ] Testes de auth (register, login, refresh)
- [ ] Testes de busca geoespacial
- [ ] Testes de agendamento

### Fase 3: Front-end Core (Semanas 3-4)

#### Setup & Layout
- [ ] Instalar dependências (Vue 3, Vue Router, Pinia, Axios, Tailwind)
- [ ] Configurar Tailwind CSS
- [ ] Criar layouts (DefaultLayout, AuthLayout)
- [ ] Criar componentes comuns (Header, Footer, Loading)

#### Authentication
- [ ] Store Pinia: `auth.js` (login, logout, refresh)
- [ ] Views: Login, Register
- [ ] Verificação de email (página de confirmação)
- [ ] Recuperação de senha (fluxo completo)
- [ ] Router guards (proteger rotas autenticadas)

#### Busca de Profissionais
- [ ] View: Search (GPS + manual)
- [ ] Component: ProfessionalCard
- [ ] View: ProfessionalDetail (perfil completo)
- [ ] Integração com Geolocation API

#### Agendamento
- [ ] Component: AvailabilityCalendar
- [ ] View: Booking (5 passos)
- [ ] View: MyBookings (cards organizados)

#### Dashboard Profissional
- [ ] View: Dashboard
- [ ] View: Profile (editar perfil)
- [ ] View: Services (CRUD serviços)
- [ ] View: Availability (CRUD blocos)
- [ ] View: Bookings (gerenciar agendamentos)

### Fase 4: Integrações (Semana 5)

- [ ] Upload de imagens para S3 (front → back → S3)
- [ ] Geocoding funcional (endereço → mapa)
- [ ] Envio de emails real (Mailtrap → produção Resend/SendGrid)
- [ ] Otimização de imagens (Pillow no backend)

### Fase 5: Testes e Deploy (Semanas 6-7)

#### Testes
- [ ] Testes E2E críticos (Playwright ou Cypress)
- [ ] Testes de carga básicos (Locust)
- [ ] Testes manuais completos (checklist de QA)

#### CI/CD
- [ ] GitHub Actions: testes automáticos no push
- [ ] GitHub Actions: deploy automático Vercel (front)
- [ ] GitHub Actions: deploy automático Fly.io (back)

#### Monitoramento
- [ ] Configurar Sentry em produção
- [ ] Configurar UptimeRobot (health checks)
- [ ] Testar alertas (erro intencional)

#### Documentação
- [ ] README completo de cada repositório
- [ ] Documentação de API (Swagger já gerado por FastAPI)
- [ ] Guia de contribuição
- [ ] Documento de arquitetura (este arquivo!)

### Fase 6: Launch MVP (Semana 8)

- [ ] Deploy em produção (Vercel + Fly.io)
- [ ] Testes de aceitação com usuários reais
- [ ] Coleta de feedback
- [ ] Hotfixes necessários

---

## Recursos de Aprendizado

### FastAPI
- [Documentação Oficial FastAPI](https://fastapi.tiangolo.com)
- [Tutorial: JWT Auth com FastAPI](https://fastapi.tiangolo.com/tutorial/security/)
- [SQLAlchemy 2.0 Tutorial](https://docs.sqlalchemy.org/en/20/tutorial/)
- [PostGIS with SQLAlchemy (GeoAlchemy2)](https://geoalchemy-2.readthedocs.io/)

### Vue 3
- [Documentação Oficial Vue 3](https://vuejs.org)
- [Vue Router 4 Guide](https://router.vuejs.org/)
- [Pinia State Management](https://pinia.vuejs.org/)
- [Tailwind CSS Docs](https://tailwindcss.com/docs)

### PostgreSQL & PostGIS
- [PostGIS Documentation](https://postgis.net/documentation/)
- [PostGIS in Action (livro)](https://www.manning.com/books/postgis-in-action-third-edition)
- Tutorial: [Geospatial Queries with PostGIS](https://www.digitalocean.com/community/tutorials/how-to-install-postgis-on-ubuntu-20-04)

### DevOps
- [GitHub Actions Documentation](https://docs.github.com/en/actions)
- [Fly.io Documentation](https://fly.io/docs/)
- [Vercel Documentation](https://vercel.com/docs)
- [Docker Compose Tutorial](https://docs.docker.com/compose/)

### Segurança
- [OWASP Top 10](https://owasp.org/www-project-top-ten/)
- [JWT Best Practices](https://tools.ietf.org/html/rfc8725)
- [bcrypt Guide](https://github.com/pyca/bcrypt/)

---

## Revisão e Atualizações

### Histórico de Revisões

| Versão | Data       | Alterações                                       | Autor                 |
| ------ | ---------- | ------------------------------------------------ | --------------------- |
| 1.0    | 22/11/2025 | Documento inicial com todas as decisões técnicas | Arquiteto de Software |

### Próximas Revisões Planejadas

- **v1.1**: Após Phase 2 (Back-end Core) - ajustes baseados em implementação real
- **v1.2**: Após Phase 5 (Deploy) - decisões de produção
- **v2.0**: Após feedback do MVP - roadmap de features v2.0

---

## Contato e Dúvidas

Para questões sobre decisões técnicas ou sugestões de melhorias neste documento:

- Abrir issue no repositório GitHub
- Discutir em reuniões de sprint review
- Documentar decisões significativas neste arquivo

---

**Documento vivo**: Este arquivo deve ser atualizado sempre que decisões técnicas importantes forem tomadas ou revisadas.
