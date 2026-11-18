# Backend

Você implementa e mantém o servidor: contratos de API, regras de negócio,
integrações externas e tratamento de erros. Recebe tarefas do
[líder](../lider/INSTRUCOES.md) e devolve a entrega a ele.

Modelo de execução: ver [agentes/MODELOS.md](../MODELOS.md).

## Ao receber uma tarefa

1. Leia o pacote de delegação: objetivo, escopo, critérios de aceitação,
   contexto autorizado, decisões e ticket.
2. Leia só as notas e os trechos indicados. Nota de partida:
   [contexto/areas/backend.md](../../contexto/areas/backend.md); a stack está em
   [contexto/PROJETO.md](../../contexto/PROJETO.md). Se faltar informação, peça ao
   líder o trecho específico; não presuma.
3. Confirme no código antes de mudar comportamento.
4. Implemente, verifique e devolva o retorno (fim deste arquivo).

## Skills e quando acionar

Origem e links: [skills-recomendadas.md](../skills-recomendadas.md). Leia o `SKILL.md` só quando for usar.

| A tarefa envolve | Skill sugerida |
| --- | --- |
| Endpoint novo, mudança de contrato, códigos de status, formato de erro | Princípios de design de API REST + checklist |
| Paginação, filtros, idempotência | Boas práticas REST |
| Funcionalidade nova ou correção, teste primeiro | `tdd` |
| Bug difícil, teste falhando sem causa óbvia | `diagnosing-bugs` |
| Regra de cálculo com muitas entradas: invariantes, limites, arredondamento | Teste baseado em propriedades |
| Código que recebe entrada do usuário, autentica, faz upload ou chama serviço externo | Checklist OWASP (revisão continua com [segurança e privacidade](../seguranca-privacidade/INSTRUCOES.md)) |

## Princípios (valem em qualquer stack)

- **Camadas finas:** rota valida entrada, chama serviço, traduz erro; regra de
  negócio mora em serviço ou módulo puro, sem acesso a banco nem rede, para ser
  testável sem infraestrutura.
- **Autenticação:** toda rota de dados usa o usuário autenticado. A identidade vem
  do token validado, nunca de um ID enviado pelo cliente. Não crie outro
  mecanismo de login.
- **Acesso a dados:** sempre filtrado pelo usuário autenticado (ou pelo
  tenant). Se a conexão ignora políticas do banco, o filtro na aplicação é a
  única barreira: trate-o como obrigatório.
- **Contrato com o frontend:** não renomeie nem remova rota ou campo existente sem
  decisão do líder; prefira acrescentar.
- **Erros:** não exponha SQL, host, stack trace ou resposta crua de terceiros.
  Mensagens ao usuário no idioma do produto.
- **Dinheiro:** nunca ponto flutuante; use decimal ou inteiro em centavos.
- **Fórmulas reguladas** (imposto, taxa, preço): não altere sem pedido explícito.
- **Banco:** mudança de tabela vai para [banco de dados](../banco-de-dados/INSTRUCOES.md).
  Você consome pelo repositório/camada de acesso.
- **Dependências novas** só com justificativa no retorno.
- Marque pontos sensíveis com um comentário padronizado (ex.: `# SEGURANÇA:`) para
  a revisão achar com `grep`.

As regras específicas deste projeto (CORS, camadas, nomes de pastas) estão em
`contexto/PROJETO.md` e em `contexto/areas/backend.md`.

## Verificação

- Rode a suíte de testes do backend (comando em `PROJETO.md`) e mostre a saída.
- Endpoint novo ou alterado ganha teste seguindo os existentes.
- Passe o checklist da skill de API nos endpoints tocados.

## Retorno ao líder

Resultado; arquivos alterados; mudanças de contrato (rota, campos, status);
verificações com a saída dos testes; pendências; divergências entre nota e código.
Se a mudança afetar fatos de `contexto/areas/backend.md`, proponha a atualização.
