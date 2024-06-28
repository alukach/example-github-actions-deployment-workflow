# A best-practice Github Actions deployment workflow

This repository demonstrates using GitHub Actions to deploy into either a `staging` or `production` environment.

## Setup

Each deployment environment (i.e., `staging` or `production`) is managed as a [Github Environment](https://docs.github.com/en/actions/deployment/targeting-different-environments/using-environments-for-deployment). Within each Github Environment, we store environment variables and environment secrets to be used during the deployment process. This demonstration repository only uses a single environment variable (`MESSAGE`) and environment secret (`API_KEY`).

<img width="784" alt="image" src="https://github.com/alukach/example-github-actions-deployment-workflow/assets/897290/5d80237e-6e5e-4ebc-b31b-47eafbb1900e">

## Triggers

### Merges to `main`

When a push occurs to `main` (e.g. a PR is merged to `main` or a commit is pushed directly to `main`), a deployment to the `staging` environment will be triggered.

### Releases

When a new [Release](https://docs.github.com/en/repositories/releasing-projects-on-github/about-releases) occurs, a deployment to the `production` environment will be triggered.

### Manual Deployments

Deployments can be manually triggered from within the Github Actions UI. This allows feature branches to be deployed to an environment outside of the standard git-flow cycle (i.e. first merging to `main`).

<img width="936" alt="image" src="https://github.com/alukach/example-github-actions-deployment-workflow/assets/897290/276a5b74-4228-424e-92e1-1edbb970002d">

#### Forcing Deployments

When manually dispatching a deployment, a user can deploy even if tests fail.
<img width="656" alt="image" src="https://github.com/alukach/example-github-actions-deployment-workflow/assets/897290/03d084aa-c5ea-46a3-889f-e5fdb182666a">

This will ensure that deployment occurs despite test failures ([example](https://github.com/alukach/example-github-actions-deployment-workflow/actions/runs/9717940105)):
<img width="657" alt="image" src="https://github.com/alukach/example-github-actions-deployment-workflow/assets/897290/23a2494d-d1a0-422e-91ee-36322890cdf4">

Otherwise, the deployment will halt when tests fail ([example](https://github.com/alukach/example-github-actions-deployment-workflow/actions/runs/9718017649)):
<img width="659" alt="image" src="https://github.com/alukach/example-github-actions-deployment-workflow/assets/897290/dc0d5626-12a2-4048-9aa6-1bb40e9e947b">
