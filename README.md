# AgendaNex

SaaS fullstack de agendamento online para pequenos negócios, com página pública de reservas, painel administrativo por empresa e área de gestão da plataforma.

> Este repositório apresenta o projeto AgendaNex para fins de portfólio e demonstração comercial.  
> O código-fonte principal é proprietário e permanece em um repositório privado.

## Demo online
🚀 Acessar AgendaNex = <a href="https://agenda-frontend-delta-blue.vercel.app" target="_blank">
  Abrir AgendaNex
</a>
 
**API:** NestJS hospedada no Render e integrada ao frontend.

> Na primeira abertura, alguns serviços gratuitos podem levar alguns segundos para responder.

## Sobre o projeto

O AgendaNex foi desenvolvido para ajudar pequenos negócios a organizar seus agendamentos, profissionais, serviços, clientes e faturamento.

Cada negócio possui seu próprio ambiente, com dados isolados das demais empresas cadastradas na plataforma.

O projeto também foi criado como portfólio para demonstrar o desenvolvimento de uma aplicação fullstack real, envolvendo autenticação, autorização, regras de negócio, banco de dados, integrações externas e deploy em nuvem.

## Problema resolvido

Muitos pequenos negócios ainda controlam reservas por mensagens, anotações ou planilhas.

Isso pode causar:

- horários duplicados;
- demora no atendimento;
- dificuldade para organizar profissionais;
- falta de controle dos clientes;
- dificuldade para acompanhar o faturamento.

O AgendaNex centraliza essas informações em um único sistema.

## Principais funcionalidades

### Área pública

- página personalizada para cada negócio;
- escolha de serviço;
- escolha de profissional ou atribuição automática;
- seleção de data e horário disponível;
- criação de agendamento;
- consulta segura de reservas;
- cancelamento online;
- contato por WhatsApp;
- funcionamento adaptado ao fuso horário do negócio.

### Painel administrativo

- dashboard com resumo da operação;
- gerenciamento de serviços;
- gerenciamento de profissionais;
- agenda com filtros por período, status e funcionário;
- reagendamento de atendimentos;
- atribuição de profissionais;
- bloqueio de horários;
- visualização de conflitos;
- gerenciamento de clientes;
- controle de faltas;
- relatório de faturamento;
- controle de atendimentos agendados, concluídos, cancelados e não comparecimentos.

### Administração da plataforma

- painel exclusivo para Admin Master;
- gerenciamento de negócios;
- criação de novos negócios e proprietários;
- controle de planos;
- controle de período de teste;
- controle de vencimento e assinatura;
- busca, filtros e paginação;
- acompanhamento geral da plataforma.

## Tecnologias utilizadas

### Frontend

- Next.js
- React
- TypeScript
- Tailwind CSS
- TanStack Query
- React Hook Form
- Zod
- Axios
- NextAuth

### Backend

- NestJS
- TypeScript
- Prisma ORM
- PostgreSQL
- JWT
- Luxon

### Infraestrutura e integrações

- Vercel
- Render
- Supabase
- Resend/SMTP
- npm workspaces
- Docker Compose no ambiente de desenvolvimento

## Arquitetura

O projeto utiliza uma arquitetura de monorepo com separação entre frontend e backend.

```text
Frontend Next.js
       |
       | Axios / HTTP
       v
Backend NestJS
       |
       | Prisma ORM
       v
PostgreSQL / Supabase
```

No backend, o fluxo principal segue:

```text
Controller -> Service -> Repository -> Prisma -> PostgreSQL
```

O frontend não acessa o banco de dados diretamente. Toda comunicação é feita por meio da API NestJS.

## Autenticação e autorização

O fluxo de autenticação funciona da seguinte forma:

1. O usuário informa suas credenciais no frontend.
2. O NextAuth envia os dados para o backend NestJS.
3. O backend valida o usuário e gera um token JWT.
4. O frontend mantém a sessão autenticada.
5. As requisições protegidas enviam o token para a API.
6. O backend valida a identidade e as permissões do usuário.

Os principais perfis são:

- `OWNER`: proprietário do negócio;
- `ADMIN`: administrador da operação;
- `STAFF`: funcionário ou profissional;
- `ADMIN MASTER`: administrador da plataforma.

## Principais desafios técnicos

- isolamento de dados entre diferentes negócios;
- arquitetura multi-business;
- autenticação com NextAuth e JWT;
- autorização baseada no vínculo do usuário com o negócio;
- prevenção de reservas duplicadas;
- controle de conflitos de horários;
- disponibilidade por profissional;
- bloqueios gerais ou individuais;
- tratamento de fuso horário;
- recuperação de senha por e-mail;
- proteção de rotas públicas e administrativas;
- deploy separado de frontend, backend e banco de dados.

## Regras de negócio importantes

- todos os dados administrativos são filtrados pelo negócio selecionado;
- serviços inativos não aceitam novas reservas, mas permanecem no histórico;
- somente atendimentos concluídos entram no faturamento;
- cancelamentos e faltas não geram receita;
- bloqueios podem afetar todo o negócio ou apenas um profissional;
- a disponibilidade considera duração do serviço, intervalos e conflitos;
- clientes com faltas recorrentes podem ter restrição de reserva online;
- planos vencidos podem bloquear operações de escrita;
- consultas públicas retornam apenas os dados necessários.

## Screenshots

### Página inicial

_Imagem em breve._

### Reserva online

_Imagem em breve._

### Painel administrativo

_Imagem em breve._

### Gestão de serviços

_Imagem em breve._

### Gestão financeira

_Imagem em breve._

### Admin Master

_Imagem em breve._

## Objetivo profissional

Este projeto demonstra minha experiência prática no desenvolvimento de aplicações fullstack, incluindo:

- desenvolvimento de interfaces responsivas;
- criação de APIs REST;
- modelagem de banco de dados;
- autenticação e autorização;
- implementação de regras de negócio;
- integração entre frontend e backend;
- deploy em ambientes de produção;
- organização de projetos em monorepo;
- controle de acesso por perfil;
- desenvolvimento de uma aplicação SaaS multi-business.

Atualmente busco uma oportunidade como Desenvolvedor Full Stack Júnior ou estágio em desenvolvimento de software.

## Objetivo comercial

O AgendaNex também está sendo preparado para atender pequenos negócios que desejam organizar seus agendamentos e reduzir o trabalho manual.

A solução pode ser utilizada por:

- salões de beleza;
- barbearias;
- clínicas;
- estúdios;
- profissionais autônomos;
- prestadores de serviço;
- pequenos negócios que trabalham com horários marcados.

## Limitações atuais

- cobrança e renovação ainda são controladas manualmente;
- integração com gateway de pagamento ainda não foi implementada;
- notificações automáticas ainda são limitadas;
- relatórios avançados e exportações ainda estão em desenvolvimento;
- algumas telas ainda precisam de testes em diferentes dispositivos;
- observabilidade e monitoramento ainda estão sendo ampliados.

## Próximas melhorias

- integração com gateway de pagamento;
- cobrança recorrente;
- confirmação e lembrete por WhatsApp ou e-mail;
- lista de espera;
- encaixes;
- sinal de reserva;
- políticas de cancelamento;
- cupons;
- programa de fidelidade;
- exportação de relatórios em CSV e PDF;
- resumo diário de agenda e faturamento;
- ampliação dos testes automatizados;
- melhorias de monitoramento e observabilidade.

## Status do projeto

O AgendaNex está em evolução e já possui os principais fluxos de um SaaS de agendamento implementados.

A etapa atual está focada em:

- homologação ponta a ponta;
- refinamento da experiência do usuário;
- testes em produção;
- melhoria da apresentação para portfólio;
- preparação para utilização por negócios reais.

## Autor

**Jaderson Farias**

Desenvolvedor Full Stack em formação.

Projeto desenvolvido para portfólio profissional e futura comercialização.

---

## Aviso de propriedade

O AgendaNex é um projeto proprietário.

Este repositório não contém o código-fonte principal da aplicação e não concede autorização para copiar, redistribuir, modificar ou comercializar o sistema, sua identidade visual ou sua implementação sem autorização.

O conteúdo deste repositório possui finalidade exclusivamente demonstrativa.
