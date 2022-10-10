# github-workflow-approve-and-merge-dependabot-pr

[dependabot-approve-and-merge.yaml] is a workflow to automatically approve and
merge Dependabot PRs. This workflow has a limitation at the moment: it will
update Docker images for `coopnorge/engineering-docker-images/e0` and Python patch
updates.

## Inputs

| Input variable           | Description                                                                                               | Required |
| ------------------------ | --------------------------------------------------------------------------------------------------------- | -------- |
| `reviewbot-github-token` | GitHub token with permission to approve the PR (usually `${{ secrets.REVIEWBOT_GITHUB_TOKEN}}`)           | Yes      |
| `merge-strategy`         | Strategy type to use when Dependabot merges the PR. Check [managing-pull-requests-for-dependency-updates] | No       |
| `approve-condition`      | DEPRECATED!. Conditional statement used to approve PR                                                     | No       |
| `docker`                 | If enabled, the workflow approves and merges engineering devtools images updates                          | No       |
| `python`                 | If enabled, the workflow approves and merges patch Python updates                                         | No       |
| `golang`                 | If enabled, the workflow approves and merges patch Go updates                                             | No       |
| `npm-and-yarn`           | If enabled, the workflow approves and merges patch npm and yarn updates                                   | No       |
| `github-actions`         | If enabled, the workflow approves and merges patch GitHub Actions updates                                 | No       |

Check [playbook.internal.coop] for detailed instructions.

[dependabot-approve-and-merge.yaml]: .github/workflows/approve-and-merge-dependabot-pr.yaml
[playbook.internal.coop]: https://playbook.internal.coop/platforms/cloud_platform/dev_build_deploy/github/guide_github_dependabot.html?h=dependabot#enabling-auto-approve-for-dependabot
[managing-pull-requests-for-dependency-updates]: https://docs.github.com/en/code-security/dependabot/working-with-dependabot/managing-pull-requests-for-dependency-updates#managing-dependabot-pull-requests-with-comment-commands
