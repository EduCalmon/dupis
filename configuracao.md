# Configuração do Dupis

Fluxo para instalar o time num projeto. **Só rode se a pessoa pediu.** Cada etapa
abaixo é opcional e a pessoa pode parar a qualquer momento; instale o que ela
aprovou e nada além. Se ela recusar uma etapa, siga em frente sem insistir.

## Etapa 1: o projeto

Pergunte primeiro se a configuração é **para um projeto específico** (padrão: a
pasta atual) ou se a pessoa só quer o time instalado de forma genérica, sem fatos
do negócio. Sem projeto, instale os papéis e deixe `PROJETO.md` todo em "A definir".

## Etapa 2: entrevista do projeto

Use a skill **`grilling`** do [Matt Pocock](https://github.com/mattpocock/skills)
(MIT) para conduzir a entrevista: uma pergunta de cada vez, com a sua
recomendação, e só avance quando a resposta fizer sentido. Se `grilling` não
estiver instalada, **pergunte** se a pessoa quer instalá-la (link em
`skills-recomendadas.md`) e, se não quiser, faça as perguntas com `AskUserQuestion`
(até 4 por chamada, cada uma com recomendação). Nunca instale skill de terceiros
sem a pessoa concordar.

Perguntas, em ordem (todas opcionais; "ainda não sei" vira "A definir"):

1. **Nome do projeto** e a **frase** que o descreve.
2. **Contexto do negócio:** o que faz, para quem, qual problema resolve.
3. **Público:** quem usa e, se houver, quem vê o resultado. Que palavras ele usa
   e quais evitar. Marque suposições como hipótese.
4. **Estágio:** ideia, protótipo, no ar com usuários.
5. **Stack:** backend, frontend, banco, autenticação, deploy. Se ainda não
   decidiu, o líder decide a stack antes de qualquer papel técnico.
6. **Dados pessoais e lei:** LGPD, GDPR, outra, ou não trata dado pessoal.
   Regras do setor (ética profissional, regulação).
7. **Papéis ativos:** mostre a tabela do time e sugira só os que o projeto
   justifica (ex.: sem login, dispensa banco; projeto interno, dispensa vendas).
8. **Ferramentas e modelos** que a pessoa tem (Claude Code, outras CLIs, plano,
   limites). Alimenta `agentes/MODELOS.md`.
9. **Idioma** dos arquivos do time (padrão: português do Brasil).

Se o projeto já tem código, ofereça ler o repositório (pelo subagente `busca`)
para preencher a stack e os comandos, e peça confirmação do que for deduzido.
Se a pessoa tiver um glossário do domínio em mente, a skill `grill-with-docs`
ajuda a registrá-lo em `contexto/GLOSSARIO.md`, também só se ela quiser.

## Etapa 3: orquestrador de agentes

Pergunte: **"Você usa algum orquestrador de agentes (por exemplo o Maestri)?"**
Opções: usa e quer ajuda para configurar; usa, mas configura sozinha; não usa;
não sabe o que é (explique em duas frases e ofereça seguir sem).

Se **usa e quer ajuda**, configure **na hora, com a pessoa**, para a ferramenta
que ela usa. A Dupis não traz comandos de nenhum orquestrador, porque eles mudam:

1. Descubra qual é e leia a documentação dele (ou a skill dele, se estiver
   instalada) antes de agir. Não presuma comandos nem opções.
2. Veja o que já existe configurado e reaproveite antes de criar algo novo.
3. Proponha a estrutura: **uma instância (terminal, agente ou sessão) por papel
   ativo**, com o modelo de `agentes/MODELOS.md`. Mostre a tabela e **espere a
   aprovação** antes de criar qualquer uma: cada instância gasta cota.
4. O prompt de cada papel só aponta para os arquivos, sem duplicar regras:
   `Siga agentes/<papel>/INSTRUCOES.md e leia contexto/INDEX.md`. O líder também
   recebe: "reaproveite os agentes que já existem antes de criar outros; nunca
   publique em produção sem pedir".
5. Papéis de segurança, dados e autenticação ficam no modelo mais capaz.
6. Registre em `contexto/PROJETO.md` qual orquestrador é usado e como o líder
   envia o pacote de delegação a cada papel.

Se **não usa**: o líder delega por subagentes do Claude Code (`orquestracao.md`).
Registre a escolha em `PROJETO.md`.

## Etapa 4: instalar

Mostre um **resumo do que será criado** (arquivos e pastas) e peça o ok. Depois
copie, a partir da pasta da skill:

| De (na skill) | Para (no projeto) |
| --- | --- |
| `papeis/<papel>/` dos papéis ativos e `papeis/MODELOS.md` | `agentes/<papel>/` e `agentes/MODELOS.md` |
| `templates/AGENTS.md` | `AGENTS.md` (se já existir, mescle sem apagar o que há) |
| `templates/CLAUDE.md` | `CLAUDE.md` (idem) |
| `templates/contexto/` (`INDEX.md`, `PROJETO.md`, `decisoes/`, `tarefas/`) | `contexto/` |
| `templates/contexto/areas/_nota-da-area.md`, uma cópia por papel ativo | `contexto/areas/<area>.md` (`backend`, `frontend`, `dados`, `seguranca-privacidade`, `marketing-seo`, `marca`, `infra`), só com o que foi confirmado; sem o `_nota-da-area.md` no projeto |
| `templates/contexto-skill/SKILL.md` | `.claude/skills/contexto/SKILL.md` |
| `templates/subagentes/*.md` | `.claude/agents/` |

Depois:

- Substitua os marcadores `{{...}}` pelas respostas ou por "A definir".
- Apague do `AGENTS.md` e do `contexto/INDEX.md` as linhas dos papéis desativados.
- Não copie `skills-recomendadas.md` nem `orquestracao.md` para o projeto, a
  menos que a pessoa queira; eles ficam na skill.
- Se a pessoa aprovou skills de terceiros, instale só essas, uma a uma, lendo o
  README de cada uma, e confirme a licença.

## Etapa 5: conferir e entregar

- Nenhum `{{` sobrou sem resposta ou sem "A definir" (`grep -rn "{{" agentes contexto AGENTS.md`).
- Todo link de `agentes/*/INSTRUCOES.md` e de `contexto/INDEX.md` abre um arquivo
  que existe.
- Mostre o que foi instalado, o que ficou "A definir" e o **próximo passo**
  sugerido (em geral: preencher `PROJETO.md` ou pedir a primeira tarefa ao líder).
- Lembre, em uma linha, como atualizar o time: `git pull` na skill e recopiar o
  papel desejado.
