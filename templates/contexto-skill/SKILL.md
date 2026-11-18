---
name: contexto
description: Navegação seletiva e atualização do contexto persistente do projeto (pasta contexto/). Use no início de qualquer tarefa no projeto para descobrir onde mora cada assunto sem varrer o repositório, e ao concluir uma mudança validada que altere um fato, uma decisão ou um caminho registrado nas notas.
---

# Contexto do projeto

`contexto/` é um mapa em Markdown (compatível com Obsidian). Ele economiza leitura
apontando para o arquivo certo; o código continua sendo a fonte da verdade.

## Ler

1. Abra `contexto/INDEX.md`. Pronto quando você souber quais áreas a tarefa toca.
2. Abra só as notas de `contexto/areas/` dessas áreas. Não leia a pasta inteira.
   Fatos da stack e comandos: `contexto/PROJETO.md`.
3. Siga os links da nota até o código ou o documento que interessa. Leia o trecho
   necessário, não arquivos inteiros sem motivo.
4. Se nota e código divergirem, o código mostra o estado atual: trate como
   divergência, investigue e corrija a nota.

**Especialista delegado:** leia apenas as notas e trechos indicados pelo líder.
Se faltar informação, peça ao líder a ampliação específica em vez de explorar outras áreas.

## Atualizar

Ao concluir uma mudança verificada (testes passando ou comportamento conferido):

- Atualize a nota da área afetada: fatos, caminhos, pendências e a linha
  "Última verificação" com data e commit.
- Decisão nova e isolada → um arquivo em `contexto/decisoes/` (modelo no README da pasta).
- Trabalho que continua em outra sessão ou outro agente → resumo em `contexto/tarefas/`.
- Área nova → crie a nota em `contexto/areas/` (modelo `_nota-da-area.md`) e uma
  linha no `INDEX.md`.

Regras de escrita:

- Uma fonte por informação; use links relativos em vez de copiar texto.
- Registre só o que foi confirmado. Hipótese fica em "Pendências", marcada como tal.
- Notas curtas: aponte para o código, não cole código.
- Nunca registre segredos, tokens, `.env` ou dados pessoais reais.
- Mantenha o `INDEX.md` com algumas centenas de palavras, só orientação.
