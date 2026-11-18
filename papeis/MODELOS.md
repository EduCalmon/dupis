# Modelos e ferramentas dos agentes

Fonte única de qual modelo executa cada agente. As instruções de cada papel
apontam para cá. Papel e modelo são decisões separadas: o líder pode mudar o
modelo de uma tarefa conforme risco e disponibilidade.

Última revisão: {{DATA}}. Nomes de modelo mudam rápido: confira no seletor de
cada ferramenta antes de usar.

## Ferramentas do usuário

Preencha no briefing. Exemplo de estrutura:

| Ferramenta | Modelos disponíveis | Validade / limite |
| --- | --- | --- |
| {{FERRAMENTA}} | {{MODELOS}} | {{PLANO, LIMITE OU PRAZO}} |

## Princípio: o modelo acompanha o risco, não o prestígio do papel

| Nível | Quando | Modelo |
| --- | --- | --- |
| **Mais capaz** | Segurança, autenticação, permissões, dinheiro e cálculo regulado; decisão de arquitetura; definição de marca | O melhor modelo disponível |
| **Intermediário** (padrão) | Líder, backend, banco de dados, designer, vendas, revisão de código | Modelo intermediário; suba de nível se a entrega ficar rasa |
| **Leve** | Busca no repositório, conferir diff, tarefa pequena e sem risco | Modelo leve ou barato |

## Distribuição sugerida por agente

| Agente | Nível | Observação |
| --- | --- | --- |
| Líder | Intermediário, com um conselheiro mais capaz nas decisões grandes e antes de dar por pronto | Poupa cota sem perder o olhar crítico |
| Segurança e privacidade | Mais capaz | Risco mais alto da equipe; revisão rotineira pode descer um nível |
| Banco de dados | Intermediário | Erro em política de acesso ou migração vaza dados ou quebra produção: revise com cuidado |
| Backend | Intermediário | Pode usar outra ferramenta que o usuário tenha, exceto em segurança e cálculo regulado |
| Frontend | Intermediário | Ajuste visual difícil ou revisão final: um nível acima |
| Designer | Intermediário; mais capaz em definição de marca | Precisa ser crítico: modelo fraco tende a concordar |
| Vendas | Intermediário | Texto que o usuário vai dizer a um cliente, com cuidado ético: modelo fraco gera fala genérica |
| Marketing e SEO | Leve a intermediário | Texto e pesquisa, risco baixo; textos longos pedem um nível acima |

## Regras

- Tarefa de segurança, autenticação, permissões de dados ou cálculo regulado não
  vai para modelo econômico nem local, mesmo pequena.
- Falhou ou ficou aquém: o líder reavalia o escopo e sobe para um modelo mais capaz.
- Modelo local só entra após teste no hardware (memória, velocidade e qualidade em
  tarefas reais do projeto). Modelos pequenos costumam falhar em tarefas de agente.
- Assinatura não é crédito de API: não automatize uma ferramenta sem confirmar
  que o plano permite esse uso.
- Ferramentas que não leem o `CLAUDE.md` (outras CLIs) precisam que o prompt mande
  seguir o `AGENTS.md` e o `INSTRUCOES.md` do papel.
