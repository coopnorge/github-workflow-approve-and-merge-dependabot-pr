# github-workflow-approve-and-merge-dependabot-pr

[dependabot-approve-and-merge.yaml] is a workflow to automatically approve and
merge Dependabot PRs. This workflow has a limitation at the moment: it will
update **only Docker** images for `coopnorge/engineering-docker-images/e0`.

## Inputs

| Input variable           | Description                                                                                               | Required |
|--------------------------|-----------------------------------------------------------------------------------------------------------|----------|
| `reviewbot-github-token` | GitHub token with permission to approve the PR (usually `${{ secrets.REVIEWBOT_GITHUB_TOKEN}}`)           | Yes      |
| `merge-strategy`         | Strategy type to use when Dependabot merges the PR. Check [managing-pull-requests-for-dependency-updates] | Yes      |

Check [playbook.internal.coop] for detailed instructions.

[dependabot-approve-and-merge.yaml]: .github/workflows/approve-and-merge-dependabot-pr.yaml

[playbook.internal.coop]: https://playbook.internal.coop

[managing-pull-requests-for-dependency-updates]: https://docs.github.com/en/code-security/dependabot/working-with-dependabot/managing-pull-requests-for-dependency-updates#managing-dependabot-pull-requests-with-comment-commands
