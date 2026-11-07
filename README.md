# AgendaNex · Agendamento online para pequenos negócios

Desenvolvi o AgendaNex, um SaaS full stack em que clientes reservam horários pelo celular e pequenos negócios gerenciam seus atendimentos em uma agenda por profissional.

**[Ver o AgendaNex online](https://www.agendanex.com.br)** · [Minha contribuição](#minha-contribuição) · [Decisões técnicas](#decisões-técnicas)

![Modo Foco da agenda, com os atendimentos do dia organizados por profissional](./assets/desktop/modo-foco-agenda.png)

Este repositório apresenta o produto e suas decisões de engenharia. O código-fonte principal é proprietário e fica em um repositório privado.

## Minha contribuição

- **Frontend.** Desenvolvi a página pública de reservas e o painel administrativo com React, Next.js e TypeScript. O painel inclui uma agenda diária por profissional, filtros por status e ações de reagendamento.
- **Backend.** Desenvolvi a API REST em NestJS e modelei os dados com Prisma e PostgreSQL. Implementei regras de disponibilidade, controle de conflitos e autorização por empresa e perfil.
- **Qualidade e entrega.** Trabalhei com testes automatizados no frontend e no backend, migrations versionadas, integração contínua e deploy separado da aplicação web, da API e do banco.

## Como funciona

1. **O cliente reserva.** Na página pública do estabelecimento, escolhe o serviço, um profissional compatível e um horário disponível. Também pode consultar ou cancelar uma reserva.
2. **A equipe gerencia o atendimento.** No Modo Foco, acompanha a agenda do dia por profissional e pode reagendar, concluir, cancelar ou registrar uma falta.
3. **O responsável acompanha a operação.** O painel permite configurar serviços, profissionais e bloqueios. Apenas atendimentos concluídos entram no faturamento. A plataforma tem uma área separada para gerenciar negócios e planos.

| Reserva pública | Gestão do atendimento |
| --- | --- |
| ![Seleção de data e horário na reserva pública](./assets/desktop/selecao-data-horario.png.png) | ![Detalhes do atendimento no painel administrativo](./assets/desktop/detalhes-agendamento.png) |

## Decisões técnicas

### Disponibilidade e reservas concorrentes

A disponibilidade leva em conta os profissionais habilitados para o serviço, o horário de funcionamento, a duração do atendimento, o intervalo entre reservas, os bloqueios e o fuso horário do negócio. Quando o cliente aceita qualquer profissional, o sistema faz a atribuição automaticamente.

Um horário pode ficar indisponível entre a seleção e a confirmação. A criação da reserva na API trata conflitos de horário e concorrência para evitar agendamentos duplicados. A suíte automatizada cobre criação de reservas, conflitos, intervalos e bloqueios.

### Isolamento de dados entre empresas

Cada estabelecimento tem seu próprio ambiente. A API valida a identidade do usuário e verifica seu vínculo com a empresa antes de autorizar ações administrativas. As consultas administrativas são filtradas pelo negócio, e os perfis `OWNER`, `ADMIN` e `STAFF` têm permissões distintas. A gestão da plataforma fica em uma área exclusiva do administrador master.

Os testes incluem cenários de isolamento entre negócios e acesso por perfil.

## Arquitetura e tecnologias

O projeto usa um monorepo com npm workspaces. O frontend se comunica por HTTP com a API, que acessa o PostgreSQL via Prisma. No backend, o fluxo principal passa por controller, service e repository.

| Camada | Tecnologias |
| --- | --- |
| Interface | Next.js, React, TypeScript, Tailwind CSS, TanStack Query, React Hook Form e Zod |
| API e dados | NestJS, Prisma, PostgreSQL e Luxon |
| Autenticação | NextAuth no frontend e JWT validado pela API |
| Infraestrutura | Vercel para o frontend, Render para a API, Supabase para o PostgreSQL e Cloudflare R2 para imagens |
| Integração contínua | GitHub Actions executa lint, verificação de tipos, testes e builds do frontend e do backend |

A API pode levar alguns segundos para responder no primeiro acesso à demonstração.

## Mais telas

- [Página pública do estabelecimento](./assets/desktop/pagina-publica-negocio.png.png)
- [Dashboard administrativo](./assets/desktop/dashboard-agendanex.png)
- [Bloqueios de agenda](./assets/desktop/bloqueios-agenda.png)
- [Resumo financeiro mensal](./assets/desktop/financeiro-mensal.png.png)
- [Versão mobile](./assets/mobile/a_clean_presentation_mockup_graphic_layout_a_dark.png)

## Status do projeto

Os fluxos principais estão implementados. O foco atual é validar a experiência ponta a ponta e preparar o produto para uso por pequenos negócios. Cobrança e renovação ainda são manuais. Integração de pagamentos, automação de lembretes e observabilidade estão entre as próximas etapas.

## Contato

**Jaderson Farias** · Estudante de Análise e Desenvolvimento de Sistemas, em Santa Catarina.

Busco minha primeira oportunidade como desenvolvedor Frontend ou Full Stack Júnior, ou em estágio de desenvolvimento.

[LinkedIn](https://www.linkedin.com/in/jaderson-farias/) · [GitHub](https://github.com/jadersonfarias)

