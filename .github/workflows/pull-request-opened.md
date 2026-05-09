---
name: Open Pull Request Handler
on:
  pull_request:
    types: [opened]
permissions:
  contents: read
  issues: read
  pull-requests: read

# Tools - GitHub API access via toolsets (context, repos, issues, pull_requests)
tools:
  github:
    toolsets: [default]

# Network access
network: defaults

# Outputs - what APIs and tools can the AI use?
safe-outputs:
  create-issue:          # Creates issues (default max: 1)
    max: 5               # Optional: specify maximum number
  mentions:             # Mentions users in comments or issues
    max: 5               # Optional: specify maximum number
  add-comment:          # Adds comments to issues or PRs
    max: 5               # Optional: specify maximum number
  add-labels:           # Adds labels to issues or PRs
    max: 5               # Optional: specify maximum number
  assign-to-user:

  # actions:
  # activation-comments:
  # add-comment:
  # add-labels:
  # add-reviewer:
  # allowed-github-references:
  # assign-milestone:
  # assign-to-agent:
  # assign-to-user:
  # autofix-code-scanning-alert:
  # call-workflow:
  # close-discussion:
  # close-issue:
  # close-pull-request:
  # concurrency-group:
  # create-agent-session:
  # create-agent-task:
  # create-code-scanning-alert:
  # create-discussion:
  # create-project:
  # create-project-status-update:
  # create-pull-request:
  # create-pull-request-review-comment:
  # dispatch-workflow:
  # dispatch_repository:
  # environment:
  # failure-issue-repo:
  # footer:
  # group-reports:
  # hide-comment:
  # id-token:
  # link-sub-issue:
  # mark-pull-request-as-ready-for-review:
  # max-bot-mentions:
  # max-patch-files:
  # mentions:
  # merge-pull-request:
  # missing-data:
  # missing-tool:
  # noop:
  # push-to-pull-request-branch:
  # remove-labels:
  # reply-to-pull-request-review-comment:
  # report-failure-as-issue:
  # report-incomplete:
  # resolve-pull-request-review-thread:
  # scripts:
  # set-issue-type:
  # steps:
  # submit-pull-request-review:
  # threat-detection:
  # unassign-from-user:
  # update-discussion:
  # update-issue:
  # update-project:
  # update-pull-request:
  # update-release:
  # upload-artifact:
  # upload-asset:

---

# pull-request-opened

Analise de pull request aberto: "${{ github.event.pull_request.title }}". Adicione um comentário com um resumo dos próximos passos, como sugestões de revisão, testes a serem realizados ou informações adicionais necessárias para avançar com a revisão do pull request.

## Instructions

Analise do pull request seguindo os seguintes critérios:
- Verifique se o título e a descrição estão claros e informativos. Caso esteja vazio, solicite ao autor que forneça mais detalhes.
- Identifique se há arquivos de código modificados e, se possível, forneça feedback inicial sobre a estrutura do código, padrões de codificação ou possíveis áreas de melhoria.
- Se o pull request estiver relacionado a um problema específico, verifique se ele está vinculado corretamente e se a descrição aborda a solução proposta para o problema.
- Se o pull request incluir testes, verifique se eles estão bem escritos e cobrem os casos de uso relevantes. Se não houver testes, sugira que sejam adicionados para garantir a qualidade do código.
- Forneça orientações sobre o processo de revisão, como quem deve revisar o código, quais áreas específicas devem ser focadas ou se há alguma etapa adicional necessária antes da revisão, como a execução de testes locais ou a verificação de dependências.
- Coloque uma tag adequada para indicar o status do pull request, utilizando as tags disponíveis no repositório.
- Se houver alguma informação faltando ou se o pull request não atender aos critérios mínimos, forneça um feedback construtivo e solicite as correções necessárias para avançar com a revisão.
- Se estiver tudo correto, atribua para o usuario @felipementel e adicione um comentário de aprovação, indicando que o pull request está pronto para revisão.
