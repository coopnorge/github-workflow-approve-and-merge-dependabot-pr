# GitHub workflow to approve and merge PR created by @dependabot

You can use this workflow to enable automatic merge Dependabot PR.
This workflow will automatically approve and merge Dependabot PR
if build checks are passing.

| Ecosystem | Approve condition |
| :--- | :--- |
| `docker` | Only images `coopnorge/engineering-docker-images/e0` |
| `python` | Development dependencies: `major`, `minor`, `patch`. Production dependencies: `minor`, `patch` |
| `golang` | `patch` |
| `npm-and-yarn` | `patch` |
| `github-actions` | `minor`, `patch` |

## Configure workflow in your repository

The workflow `approve-and-merge-dependabot-pr.yaml` is by default added to newly
created repositories, and it is configured to automatically approve and merge
the engineering devtools image updates. If you would like to add the workflow
to an existing repository, create a PR with `github-workflow-approve-and-merge-dependabot-pr`
file with the following content:

```yaml title="approve-and-merge-dependabot.yaml"
---
name: Approve and merge dependabot PR
on:
  pull_request_target:
    types:
      - opened
      - reopened
      - synchronize

permissions:
  pull-requests: write

jobs:
  main:
    name: Approve and merge Dependabot PR
    if: startsWith(github.head_ref, 'dependabot/')
    uses: coopnorge/github-workflow-approve-and-merge-dependabot-pr/.github/workflows/approve-and-merge-dependabot-pr.yaml@main
    secrets:
      reviewbot-github-token: ${{ secrets.REVIEWBOT_GITHUB_TOKEN }}
```

## Configure `CODEOWNERS` in your repository

The workflow will approve the PR on behalf of `@coopnorge/github-review-bots`
team, hence `@coopnorge/github-review-bots` should also own
the package ecosystem file(s).

See a specific example for ecosystem below.

=== "Docker"

    ```text
    Dockerfile @coopnorge/github-review-bots @coopnorge/<team-name>
    ```

=== "Python"

    ```text
    pyproject.toml @coopnorge/github-review-bots @coopnorge/<team-name>
    poetry.lock @coopnorge/github-review-bots @coopnorge/<team-name>
    ```

=== "Golang"

    ```text
    go.mod  @coopnorge/github-review-bots @coopnorge/<team-name>
    go.sum  @coopnorge/github-review-bots @coopnorge/<team-name>
    # If your project still does vendoring
    /vendor  @coopnorge/github-review-bots @coopnorge/<team-name>
    ```

=== "npm and Yarn"

    ```text
    package.json  @coopnorge/github-review-bots @coopnorge/<team-name>
    package-lock.json  @coopnorge/github-review-bots @coopnorge/<team-name>
    yarn.lock  @coopnorge/github-review-bots @coopnorge/<team-name>
    ```

=== "GitHub Actions"

    ```text
    .github/workflows/*.yaml @coopnorge/github-review-bots @coopnorge/<team-name>
    ```

## Customise workflow behaviour

You can override the behaviour of the workflow by marking ecosystems flags:

- `docker`,
- `python`,
- `golang`,
- `npm-and-yarn`,
- `github-actions`.
