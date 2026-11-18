# Tarefas e repasses

Trabalho que continua em outra sessão ou outro agente.

## Convenções

- Uma pasta por funcionalidade: `contexto/tarefas/<funcionalidade>/`.
- Especificação: `contexto/tarefas/<funcionalidade>/spec.md`.
- Tickets: um arquivo por ticket em `contexto/tarefas/<funcionalidade>/issues/NN-<slug>.md`,
  numerados a partir de `01`.
- No topo de cada ticket: `Status:`, `Responsável:` (papel do especialista) e,
  quando houver, `Bloqueado por: NN, NN`.
- Histórico e repasses ao final do arquivo, sob `## Comentários`.
- Ao concluir a funcionalidade, apague a pasta (o git guarda) e leve o que ainda
  vale para a nota da área.

## Status

| Status | Significado |
| --- | --- |
| `pronto-para-agente` | Especificado; pode ser delegado |
| `pronto-para-humano` | Exige ação ou decisão do usuário |
| `precisa-info` | Falta informação |
| `em-andamento` | Delegado e em execução |
| `concluido` | Entregue e verificado |
| `descartado` | Não será feito |

Commits que citam tickets usam o caminho do arquivo, por exemplo
`contexto/tarefas/foto/issues/02-recorte.md`.
