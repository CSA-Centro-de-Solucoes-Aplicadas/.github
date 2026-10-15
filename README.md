# .github da CSA

Configurações compartilhadas da organização **CSA — Centro de Soluções
Aplicadas**. Tudo aqui vale como padrão para os repositórios que não
definem o próprio arquivo equivalente.

## O que tem aqui

| Item | Para que serve |
| --- | --- |
| [`profile/README.md`](profile/README.md) | Perfil público da organização |
| [`ISSUE_TEMPLATE/`](ISSUE_TEMPLATE) | Formulários: user story, bug e tarefa |
| [`PULL_REQUEST_TEMPLATE.md`](PULL_REQUEST_TEMPLATE.md) | Modelo padrão de PR |
| [`.github/workflows/`](.github/workflows) | Workflows reutilizáveis (CI Java, Node e Python; título de PR) |
| [`workflow-templates/`](workflow-templates) | Starter workflows que aparecem em *Actions → New workflow* |

## Usando os workflows reutilizáveis

No repositório consumidor, crie `.github/workflows/ci.yml`:

```yaml
name: CI
on:
  push:
    branches: [dev, main]
  pull_request:
    branches: [dev, main]

jobs:
  backend:
    uses: CSA-Centro-de-Solucoes-Aplicadas/.github/.github/workflows/ci-java.yml@main
    with:
      working-directory: backend

  frontend:
    uses: CSA-Centro-de-Solucoes-Aplicadas/.github/.github/workflows/ci-node.yml@main
    with:
      working-directory: frontend
```

Workflows disponíveis e seus `inputs`:

| Workflow | Inputs (padrão) |
| --- | --- |
| `ci-java.yml` | `working-directory` (`.`), `java-version` (`21`), `comando` (`mvn -B verify`) |
| `ci-node.yml` | `working-directory` (`.`), `node-version` (`22`), `comando` (`npm run verify`) |
| `ci-python.yml` | `working-directory` (`.`), `python-version` (`3.12`), `comando` (`pytest`) |
| `pr-title.yml` | — valida `tipo: descrição` no título do PR |

> Para repositórios **privados** chamarem estes workflows, o repositório
> `.github` precisa permitir acesso em *Settings → Actions → General →
> Access* ("Accessible from repositories in the organization").
