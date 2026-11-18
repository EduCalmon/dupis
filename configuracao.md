# Configuração do Dupis

Fluxo para instalar o time num projeto. **Só rode se a pessoa pediu.** Cada etapa
é opcional e a pessoa pode parar a qualquer momento; instale o que ela aprovou e
nada além. Se ela recusar uma etapa, siga em frente sem insistir.

**Ordem importa:** entrevista (decide tudo) → instalar os arquivos → montar no
orquestrador (se houver) → conferir. O orquestrador vem **depois** de instalar,
porque os prompts dos agentes apontam para `agentes/...`, que precisa existir.

## Etapa 1: o projeto

Pergunte se a configuração é **para um projeto específico** (padrão: a pasta
atual) ou uma instalação genérica, sem fatos do negócio. Sem projeto, instale os
papéis e deixe o `PROJETO.md` todo em "A definir".

## Etapa 2: entrevista

**Aproveite o que a pessoa já disse.** Se a mensagem dela ou o repositório já
respondem algo (nome, stack, público), use como resposta, mostre o que entendeu e
pergunte só o que falta. Pergunte em lotes de até 4 com `AskUserQuestion`, cada
pergunta com a sua recomendação: perguntas de fato ("qual a stack?") não precisam
de uma rodada por vez. Reserve a skill **`grilling`** do
[Matt Pocock](https://github.com/mattpocock/skills) (MIT), que pergunta uma de cada
vez, para quando a pessoa está em dúvida e precisa decidir. Se `grilling` não
estiver instalada, **pergunte** se ela quer instalá-la (link em
[`papeis/skills-recomendadas.md`](papeis/skills-recomendadas.md)); sem ela, siga
com `AskUserQuestion`. Nunca instale skill de terceiros sem a pessoa concordar.

Perguntas (todas opcionais; "ainda não sei" vira "A definir"):

1. **Nome do projeto** e a **frase** que o descreve.
2. **Contexto do negócio:** o que faz, para quem, qual problema resolve.
3. **Público:** quem usa e, se houver, quem vê o resultado; palavras que ele usa
   e que evita. Marque suposições como hipótese.
4. **Estágio:** ideia, protótipo, no ar com usuários.
5. **Stack:** backend, frontend, banco, autenticação, deploy. Se não decidiu, o
   líder decide a stack antes de qualquer papel técnico.
6. **Dados pessoais e lei:** LGPD, GDPR, outra ou nenhum dado pessoal; regras do
   setor (ética profissional, regulação).
7. **Papéis ativos:** mostre a tabela do time e sugira só os que o projeto
   justifica (sem login, dispensa banco; projeto interno, dispensa vendas).
8. **Ferramentas e modelos** que ela tem (Claude Code, outras CLIs, plano, limites).
9. **Idioma** dos arquivos do time (padrão: português do Brasil).
10. **Orquestrador de agentes:** "Você usa algum (por exemplo o Maestri)?" Opções:
    usa e quer ajuda; usa e configura sozinha; não usa; não sabe o que é (explique
    em duas frases e ofereça seguir sem). Aqui você só **registra a escolha**; a
    montagem é a etapa 4.

Se o projeto já tem código, ofereça ler o repositório (subagente `busca`) para
preencher stack e comandos, e peça confirmação do que for deduzido. Se a pessoa
quiser um glossário do domínio, a skill `grill-with-docs` ajuda a registrá-lo em
`contexto/GLOSSARIO.md`.

## Etapa 3: instalar os arquivos

Mostre um **resumo do que será criado** e peça o ok. Depois copie, a partir da
pasta da skill:

| De (na skill) | Para (no projeto) |
| --- | --- |
| `papeis/<papel>/` dos papéis ativos | `agentes/<papel>/` |
| `papeis/MODELOS.md`, `papeis/orquestracao.md`, `papeis/skills-recomendadas.md` | `agentes/` (os papéis linkam para eles com `../`) |
| `templates/AGENTS.md`, `templates/CLAUDE.md` | `AGENTS.md`, `CLAUDE.md` (se já existirem, mescle sem apagar o que há) |
| `templates/contexto/INDEX.md`, `PROJETO.md`, `decisoes/`, `tarefas/` | `contexto/` |
| `templates/contexto/areas/_nota-da-area.md` | `contexto/areas/_nota-da-area.md` (**fica**: a skill `contexto` manda criar áreas novas a partir dele) |
| `templates/contexto/marketing/product-marketing.md` | `contexto/marketing/` (se Marketing, Vendas ou Designer estiverem ativos) |
| `templates/contexto/marca/plataforma.md` | `contexto/marca/` (se o Designer estiver ativo) |
| `templates/contexto-skill/SKILL.md` | `.claude/skills/contexto/SKILL.md` |
| `templates/subagentes/*.md` | `.claude/agents/` |

**Não copie** o `README.md`, `LICENSE`, `introducao.md` nem `configuracao.md` da
skill para o projeto: eles são da skill, não do projeto.

**Notas de área.** Crie uma por área a partir do `_nota-da-area.md`, conforme os
papéis ativos:

| Papel ativo | Nota de área |
| --- | --- |
| Backend | `areas/backend.md` |
| Frontend | `areas/frontend.md` |
| Banco de dados | `areas/dados.md` |
| Segurança e privacidade | `areas/seguranca-privacidade.md` |
| Marketing e SEO | `areas/marketing-seo.md` |
| Designer | `areas/marca.md` |
| Vendas | sem nota própria (usa `contexto/tarefas/` e `marketing/product-marketing.md`) |
| (nenhum; só se há deploy) | `areas/infra.md` |

Preencha só com o que foi confirmado. Remova do `INDEX.md` e do `AGENTS.md` as
linhas das áreas e dos papéis que não existem no projeto.

Depois:

- **Marcadores `{{...}}`:** substitua pelas respostas. O texto literal
  "A definir" é aceito como resposta e **não** conta como marcador pendente.
- Preencha a tabela "Divisão real neste projeto" do `agentes/MODELOS.md` e
  **apague** as frases de exemplo ("Preencha no briefing...").
- Se aprovou skills de terceiros, instale só essas, uma a uma, lendo o README de
  cada uma e conferindo a licença.

## Etapa 4: montar no orquestrador (só se a pessoa usa um)

Faça **depois** de a etapa 3 terminar. Configure **na hora, com a pessoa**, para
a ferramenta que ela usa; a Dupis não traz comandos de nenhum orquestrador,
porque eles mudam.

1. Descubra qual é e leia a documentação dele (ou a skill dele, se instalada)
   antes de agir. Não presuma comandos nem opções.
2. **Pergunte onde roda o líder:** a sessão atual ou uma instância nova.
3. Veja o que já existe e reaproveite antes de criar algo novo. Confira também os
   **limites do plano ou da licença** (número de espaços, andares ou agentes) e
   avise a pessoa antes de estourá-los.
4. Proponha **uma instância por papel ativo** com ferramenta e modelo de
   `agentes/MODELOS.md`, em tabela, e **espere a aprovação**: cada instância gasta cota.
5. O prompt de cada papel é o mesmo para qualquer ferramenta (algumas não leem o
   `CLAUDE.md`): `Siga AGENTS.md e agentes/<papel>/INSTRUCOES.md e leia
   contexto/INDEX.md`. O líder também recebe: "reaproveite os agentes que já
   existem antes de criar outros; nunca publique em produção sem pedir". A pasta de
   trabalho de todos é a do projeto.
6. Avise que muitas CLIs perguntam, na primeira vez em cada pasta, se ela é
   confiável; a pessoa precisa responder em cada terminal novo.
7. Papéis de segurança, dados e autenticação ficam no modelo mais capaz.
8. Registre no `contexto/PROJETO.md` qual orquestrador é usado e atualize a tabela
   "Divisão real" do `MODELOS.md`.

Sem orquestrador: o líder delega por subagentes do Claude Code
(`agentes/orquestracao.md`); registre a escolha no `PROJETO.md`.

## Etapa 5: conferir e entregar

- Nenhum `{{` pendente, fora do modelo `_nota-da-area.md`:
  `grep -rn "{{" agentes contexto AGENTS.md CLAUDE.md .claude --exclude=_nota-da-area.md`.
  "A definir" é aceito.
- Todo link de `agentes/*/INSTRUCOES.md` e de `contexto/INDEX.md` abre um arquivo
  que existe.
- **A skill `contexto` e os subagentes só carregam numa sessão nova.** Arquivos
  copiados para `.claude/` durante esta sessão não valem nela: diga à pessoa para
  abrir uma sessão nova no projeto. Se ela quiser seguir agora, leia você mesmo o
  `.claude/skills/contexto/SKILL.md` e aplique as regras.
- Mostre o que foi instalado, o que ficou "A definir" e o **próximo passo**
  (em geral: preencher o `PROJETO.md` ou pedir a primeira tarefa ao líder).
- Lembre, em uma linha, como atualizar: `git pull` na skill e recopiar o papel desejado.
