# .github da CSA

Padrões compartilhados da organização. Valem para os repositórios que não definem o próprio arquivo.

- `profile/README.md`: perfil público da organização
- `ISSUE_TEMPLATE/`: formulários de user story, bug e tarefa
- `PULL_REQUEST_TEMPLATE.md`: modelo de PR
- `.github/workflows/`: workflows reutilizáveis
- `workflow-templates/`: starter workflows (Actions → New workflow)

## Workflows reutilizáveis

```yaml
jobs:
  backend:
    uses: CSA-Centro-de-Solucoes-Aplicadas/.github/.github/workflows/ci-java.yml@main
    with:
      working-directory: backend
```

| Workflow | Inputs (padrão) |
| --- | --- |
| `ci-java.yml` | `working-directory` (`.`), `java-version` (`21`), `comando` (`mvn -B verify`) |
| `ci-node.yml` | `working-directory` (`.`), `node-version` (`22`), `comando` (`npm run verify`) |
| `ci-python.yml` | `working-directory` (`.`), `python-version` (`3.12`), `comando` (`pytest`) |
| `pr-title.yml` | valida `tipo: descrição` no título do PR |

Repositórios privados só conseguem chamá-los se este repo permitir acesso em Settings → Actions → General → Access.
