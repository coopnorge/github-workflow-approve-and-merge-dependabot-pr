# github-workflow-approve-and-merge-dependabot-pr

[dependabot-approve-and-merge.yaml] is a workflow to automatically approve and
merge Dependabot PRs. This workflow has a limitation at the moment: it will
update **only Docker** images for a given list of images:

- `coopnorge/engineering-docker-images/e0/devtools-terraform-v1beta1`
- `coopnorge/engineering-docker-images/e0/devtools-golang-v1beta1`
- `coopnorge/engineering-docker-images/e0/devtools-kubernetes-v1beta1`
- `coopnorge/engineering-docker-images/e0/poetry-python3.8`
- `coopnorge/engineering-docker-images/e0/poetry-python3.9`
- `coopnorge/engineering-docker-images/e0/poetry-python3.10`.

## Inputs

| Input variable           | Description                                                                                     | Required |
|--------------------------|-------------------------------------------------------------------------------------------------|----------|
| `reviewbot-github-token` | GitHub token with permission to approve the PR (usually `${{ secrets.REVIEWBOT_GITHUB_TOKEN}}`) | Yes      |

Check [playbook.internal.coop] for detailed instructions.

[dependabot-approve-and-merge.yaml]: .github/workflows/approve-and-merge-dependabot-pr.yaml

[playbook.internal.coop]: https://playbook.internal.coop
