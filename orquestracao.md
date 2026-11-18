# Como o líder delega

Escolha a mecânica pela ferramenta e pela tarefa. Em todas, o conteúdo enviado é
o **pacote de delegação** (objetivo, escopo, critérios de aceitação, contexto
autorizado, decisões, ticket), nunca o histórico da conversa.

## 1. Subagentes do Claude Code (padrão)

O líder chama o `Agent` com o pacote e a ordem "siga `agentes/<papel>/INSTRUCOES.md`".
Serve para áreas bem delimitadas e para partes independentes em paralelo.

Já vêm três subagentes só de leitura em `templates/subagentes/` (copiados para
`.claude/agents/`), baratos e rápidos:

| Subagente | Para quê |
| --- | --- |
| `busca` | Mapear o repositório: onde fica X, quais arquivos tocam Y |
| `chamadas` | Achar todos os lugares que chamam uma função, rota ou componente |
| `auditoria` | Conferir o diff contra o pedido e rodar os testes, sem editar |

Regra prática: busca ampla vai para `busca`/`chamadas`; conferir diff e rodar
testes vai para `auditoria`; leitura pontual de um arquivo conhecido fica na
sessão principal.

## 2. Outra ferramenta de linha de comando

Se o usuário tem outra CLI de IA (para poupar cota ou usar um modelo específico),
rode-a numa sessão à parte e entregue o pacote pronto, com a instrução de seguir
`AGENTS.md` e o `INSTRUCOES.md` do papel (algumas não leem o `CLAUDE.md`). Se não
houver automação, o líder entrega o pacote para o usuário colar.

## 3. Orquestrador de agentes (opcional)

Ferramentas como o [Maestri](https://www.producthunt.com/products/maestri)
organizam um agente por papel, cada um com seu modelo, conectados entre si. Se o
usuário usa uma, a configuração é feita **na hora com ele**, seguindo a
documentação da ferramenta; a Dupis não traz comandos de nenhuma (`configuracao.md`,
etapa 3). O que vale em qualquer uma:

| Conceito | Na Dupis |
| --- | --- |
| Agente coordenador | Líder |
| Um agente por papel | Cada `agentes/<papel>/INSTRUCOES.md` ativo |
| Modelo de cada agente | A tabela de `agentes/MODELOS.md` |
| Prompt de cada agente | Curto: "Siga `agentes/<papel>/INSTRUCOES.md` e leia `contexto/INDEX.md`" |
| Envio de tarefa | O pacote de delegação, com o retorno indo ao líder |
| Trabalho arriscado | Branch e cópia de trabalho próprias |

Práticas que funcionaram:
- Veja o que já existe antes de criar agentes novos e reaproveite.
- Não encerre agentes ao terminar uma tarefa: recriar gasta cota.
- O prompt só aponta para os `INSTRUCOES.md`; não duplique regras nele.

## Quando não delegar

Se explicar custa quase o mesmo que executar, faça você mesmo, seguindo o
`INSTRUCOES.md` do especialista. Mais agentes não significam menos tokens.
