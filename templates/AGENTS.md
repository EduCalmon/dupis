# {{NOME_DO_PROJETO}}

{{UMA_FRASE_DO_QUE_E_O_PROJETO}}

Por padrão, atue como líder: siga `agentes/lider/INSTRUCOES.md`.

Antes de explorar o código, leia `contexto/INDEX.md` e abra só as notas da área
da tarefa. Para ler e atualizar o contexto, siga `.claude/skills/contexto/SKILL.md`.
Fatos da stack, comandos de teste e regras do projeto: `contexto/PROJETO.md`.

## O time

| Papel | Instruções |
| --- | --- |
| Líder | `agentes/lider/INSTRUCOES.md` |
| Backend | `agentes/backend/INSTRUCOES.md` |
| Frontend | `agentes/frontend/INSTRUCOES.md` |
| Banco de dados | `agentes/banco-de-dados/INSTRUCOES.md` |
| Segurança e privacidade | `agentes/seguranca-privacidade/INSTRUCOES.md` |
| Designer | `agentes/designer/INSTRUCOES.md` |
| Marketing e SEO | `agentes/marketing-seo/INSTRUCOES.md` |
| Vendas | `agentes/vendas/INSTRUCOES.md` |

(Apague as linhas dos papéis que este projeto não usa.)

## Como trabalhar (vale para qualquer agente e modelo)

Adaptado das [diretrizes de Karpathy](https://github.com/multica-ai/andrej-karpathy-skills) (MIT).

1. **Pense antes de codar.** Diga suas premissas. Se o pedido admite mais de uma
   leitura, apresente as opções em vez de escolher em silêncio. Se algo não está
   claro, pare e pergunte.
2. **O mais simples que resolve.** Nada além do pedido: sem abstração para uso
   único, sem configuração que ninguém pediu, sem tratar erro impossível.
3. **Mudança cirúrgica.** Toque só no necessário e siga o estilo do código ao
   redor. Não "melhore" código vizinho; aponte o problema em vez de mexer.
   Remova só o que a sua mudança deixou sem uso.
4. **Defina como verificar e verifique.** Transforme a tarefa em critério
   checável ("teste que reproduz o bug passa") e só diga que terminou depois de
   rodar a verificação e ver a saída.
