# GitHub Actions workflow to approve and merge @dependabot PRs

[`dependabot-approve-and-merge.yaml`][dependabot-approve-and-merge.yaml] is a
workflow to automatically approve and merge Dependabot PRs.

## Inputs

| Input variable           | Description                                                                                               | Required |
| ------------------------ | --------------------------------------------------------------------------------------------------------- | -------- |
| `reviewbot-github-token` | GitHub token with permission to approve the PR (usually `${{ secrets.REVIEWBOT_GITHUB_TOKEN}}`)           | Yes      |
| `merge-strategy`         | Strategy type to use when Dependabot merges the PR. Check [managing-pull-requests-for-dependency-updates] | No       |
| `approve-condition`      | DEPRECATED!. Conditional statement used to approve PR                                                     | No       |
| `docker`                 | If enabled, the workflow approves and merges engineering devtools images updates                          | No       |
| `python`                 | If enabled, the workflow approves and merges patch and minor Python updates                               | No       |
| `golang`                 | If enabled, the workflow approves and merges patch Go updates                                             | No       |
| `npm-and-yarn`           | If enabled, the workflow approves and merges patch npm and yarn updates                                   | No       |
| `github-actions`         | If enabled, the workflow approves and merges patch and minor GitHub Actions updates                       | No       |
| `nuget`                  | If enabled, the workflow approves and merges patch and minor NuGet updates                                | No       |

Check [docs][docs] for detailed instructions.

[dependabot-approve-and-merge.yaml]: .github/workflows/approve-and-merge-dependabot-pr.yaml
[managing-pull-requests-for-dependency-updates]: https://docs.github.com/en/code-security/dependabot/working-with-dependabot/managing-pull-requests-for-dependency-updates#managing-dependabot-pull-requests-with-comment-commands
[docs]: docs/index.md
