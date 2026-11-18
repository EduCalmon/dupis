# Introdução ao Dupis

Roteiro para explicar a skill a quem pediu. Conte em linguagem simples, em blocos
curtos, e deixe a pessoa interromper. Não despeje tudo de uma vez: apresente o
bloco 1, pergunte se quer seguir, e assim por diante. Se ela disser que já
entendeu, pare e passe para o que ela quer fazer.

**Blocos de entrega** (para não despejar tudo de uma vez): **bloco 1** = seções 1 e 2;
**bloco 2** = seção 3 (os agentes); **bloco 3** = seções 4 a 7 (contexto, delegação, o
que é opcional e próximos passos). Ao fim de cada bloco, pergunte se quer seguir.

## 1. O que é

O Dupis é um **time de agentes de IA especialistas** que você instala num projeto.
Em vez de uma sessão genérica fazer tudo, cada papel tem instruções próprias,
sabe o que deve ler e o que não deve tocar, e devolve a entrega num formato
combinado. Um **líder** recebe seus pedidos, decide o que delegar e confere o
resultado. Nada aqui é de um negócio específico: o time se adapta ao seu projeto.

## 2. Como funciona o ciclo

1. Você pede algo ao **líder**.
2. Ele lê o `contexto/INDEX.md` e só as notas da área (não varre o repositório).
3. Se houver decisão em aberto, ele pergunta antes de agir (portão de perguntas).
4. Ele entrega a um especialista um **pacote**: objetivo, escopo, critérios de
   aceitação, contexto autorizado e decisões que restringem a solução.
5. O especialista devolve resultado, arquivos alterados, testes rodados e pendências.
6. O líder revisa, integra e atualiza as notas de contexto.

## 3. Os agentes

| Agente | Faz | Modelo sugerido | Skills de terceiros que aproveita |
| --- | --- | --- | --- |
| **Líder** | Planeja, decide, delega, revisa **e responde as suas dúvidas** (só leitura, sem delegar) | Intermediário + conselheiro mais capaz nas decisões grandes | grilling, grill-with-docs, domain-modeling, to-spec, to-tickets, tdd, diagnosing-bugs, codebase-design, ask-questions-if-underspecified, wait-what |
| **Backend** | API, regras de negócio, integrações | Intermediário | api-design-principles, property-based-testing, tdd |
| **Frontend** | Telas, acessibilidade, responsividade | Intermediário | impeccable, design-motion-principles, taste-skill, owasp-security |
| **Banco de dados** | Modelagem, migrações, isolamento de dados | Intermediário | supabase-postgres-best-practices e a skill do provedor |
| **Segurança e privacidade** | Revisão de segurança, permissões, LGPD/GDPR | **Mais capaz** | security-audit, differential-review, supply-chain-risk-auditor, owasp-security, lgpd |
| **Designer** | Marca e identidade; crítico, não bajulador | Intermediário (mais capaz para definir marca) | brand-identity, brand-audit, brand-strategy, competitor-branding, creative-direction |
| **Marketing e SEO** | Posicionamento, conteúdo, conversão, SEO | Leve a intermediário | product-marketing, seo-audit, schema, copywriting, cro, customer-research |
| **Vendas** | Roteiro de venda, preço, objeções, proposta | Intermediário | discovery-calls, objection-handling, proposal-pricing, sales-enablement |

Fontes de verdade: modelos em `papeis/MODELOS.md`; origem, link e licença de cada
skill em `papeis/skills-recomendadas.md`. Se a tabela acima divergir deles, valem eles.
As skills de terceiros **não vêm instaladas**: o time funciona sem elas, e elas
são um reforço que a pessoa instala se quiser.

Explique o **nível** do modelo, não o nome comercial, porque os nomes mudam
rápido: "mais capaz" onde o erro custa caro (segurança, dados, dinheiro),
"intermediário" no dia a dia, "leve" onde só se lê e responde.

## 4. A memória do time: a skill `contexto`

Esta é a parte que mais economiza tokens, então explique com calma.

- O projeto ganha uma pasta `contexto/` em Markdown (abre bem no Obsidian). Ela é
  um **mapa**, não uma cópia do código: diz onde cada assunto mora.
- O `INDEX.md` é a porta de entrada. Cada agente lê ele primeiro e abre **só** as
  notas das áreas da tarefa (`areas/backend.md`, `areas/dados.md`...), em vez de
  varrer o repositório inteiro.
- `PROJETO.md` guarda a stack, os comandos e as regras do projeto num só lugar;
  trocar a stack é editar um arquivo.
- `decisoes/` registra decisões isoladas ("por que escolhemos X"), e `tarefas/`
  guarda especificações, tickets e repasses entre sessões.
- A skill `contexto` ensina dois hábitos: **ler** seletivamente e **atualizar** a
  nota da área quando uma mudança foi verificada. Assim a memória não apodrece.
- Regras: o código manda (se nota e código divergem, corrija a nota); só se
  registra o que foi confirmado; nunca se guarda segredo.

## 5. Delegação e ferramentas

O líder pode delegar por **subagentes do Claude Code** (padrão), por outra
ferramenta de linha de comando ou por um **orquestrador de agentes**, como o
Maestri. Detalhes em `papeis/orquestracao.md`. Três
subagentes de leitura já vêm prontos: `busca`, `chamadas` e `auditoria`.

## 6. O que você não precisa usar

Nenhuma parte é obrigatória. Dá para ativar só alguns papéis, não instalar skill
de terceiros e não usar orquestrador. O mínimo útil é: líder + `contexto`.

## 7. Próximos passos

Termine perguntando se a pessoa quer **configurar o time para um projeto** (ver
`configuracao.md`) ou só explorar por conta própria.
