# SeniorInsight

Plataforma digital para cuidado contínuo de idosos, conectando familiares, médicos e rede de apoio com foco em prevenção, resposta rápida a emergências e acompanhamento baseado em dados.

## Contexto da solução

O ecossistema SeniorInsight combina:
- **Apps de uso diário** (idoso, familiares e portal web)
- **Back-end em microsserviços** (domínio, identidade, cobrança, notificação, telemetria, insights e relatórios)
- **Integração orientada a eventos** via RabbitMQ (`si.events`)
- **Infraestrutura local e observabilidade** para desenvolvimento e operação

## Repositórios da organização

| Repositório | Papel no projeto |
| --- | --- |
| `si-mobile` | App mobile (idoso + família), com interface simplificada e SOS. |
| `si-web` | Portal web administrativo (B2B/B2C) para gestão e visualização avançada. |
| `si-api-gateway` | Ponto único de entrada (JWT, roteamento, rate limiting e BFF). |
| `si-care-service` | Domínio clínico e operacional: idosos, consentimentos, medicação, SOS e dados assistenciais. |
| `si-identity-service` | Perfis e pareamento do idoso por código/QR, integrado ao Keycloak. |
| `si-billing-service` | Trial, assinatura Premium, faturas B2B e direito de acesso por assinatura. |
| `si-notification-service` | Entrega de alertas (push/e-mail), incluindo confirmação de leitura e fluxo de SOS. |
| `si-telemetry-service` | Ingestão e agregação de telemetria de wearables, com detecção de eventos críticos. |
| `si-insight-service` | Cálculo de score de risco com IA (Gemini), com pseudonimização e validações. |
| `si-report-service` | Relatórios (PDF), carteira da operadora e fluxos de exportação/exclusão LGPD. |
| `si-contracts` | Contratos OpenAPI e schemas de eventos (CloudEvents). |
| `si-infra` | Docker Compose local, Keycloak, RabbitMQ, observabilidade e automações de deploy. |
| `.github` | Padrões e artefatos compartilhados da organização (incluindo este perfil). |

## Visão arquitetural (alto nível)

1. **Coleta e processamento**: telemetria é capturada e agregada.
2. **Geração de inteligência**: insights calculam score de risco e mudanças relevantes.
3. **Orquestração de cuidado**: serviços de domínio e identidade aplicam regras de negócio.
4. **Engajamento e resposta**: notificações, relatórios e apps/portal entregam ação para usuários.
5. **Governança**: contratos versionados, infraestrutura padronizada e rastreabilidade via eventos.

## Engenharia e colaboração

- Estratégia de branches recorrente: `main` (produção/principal) e `develop` (integração/testes), com PRs curtos por card/issue.
- Comunicação entre serviços padronizada com eventos na exchange `si.events`.
- Contratos e integrações mantidos de forma centralizada no repositório `si-contracts`.

## Objetivo do produto

Elevar segurança, autonomia e qualidade de vida da pessoa idosa com suporte proativo para famílias e profissionais de saúde.
