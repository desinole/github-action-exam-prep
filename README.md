# Github Actions Exam Prep

Instead of [Microsoft Learn](https://learn.microsoft.com/en-us/training/paths/automate-workflow-github-actions/) material on the same, I'm taking the path of reading GitHub Actions [quickstart documentation](https://docs.github.com/en/actions/quickstart) directly

### What's on the Exam

1. Author and maintain workflows (40%)
2. Consume workflows (20%)
3. Author and maintain actions (25%)
4. Manage GitHub Actions for the enterprise (15%)

### [Lesson 1: Quickstart build your first GitHub Action](https://docs.github.com/en/actions/quickstart#creating-your-first-workflow)


- The resuling action is a [yaml file](https://github.com/desinole/github-action-exam-prep/blob/main/.github/workflows/action1.yml). 
- Beware of indentation pitfalls
- [Repo of starter workflows](https://github.com/actions/starter-workflows), has sample workflows by language and deployment env. Note: probably a minute subset on here could be relevant to the exam (just a guess) so review later
- [Repo of complex workflows](https://docs.github.com/en/actions/examples), could be relevant to exam (just a guess)

### [Lesson 2: Understanding GitHub Actions](https://docs.github.com/en/actions/learn-github-actions/understanding-github-actions)

```yaml
name: learn-github-actions # optional - name of workflow
on: [push] # trigger - push event in this case.
jobs: # list of jobs 
  check-bats-version: # job named check-bats-version
    runs-on: ubuntu-latest # runner agent (ubuntu, in this case). Similar to creating fresh VM per execution. Can also be self hosted
    steps: # list of steps for job named check-bats-version
      - uses: actions/checkout@v3 # this step runs v3 of actions/checkout. Will pull down all files in this repo on runner
      - uses: actions/setup-node@v3 # install nodejs and npm on runner. version specified below
        with:
          node-version: '14' # nodejs version
      - run: npm install -g bats # after nodejs is installed run this on bash shell to install bats using npm 
      - run: bats -v # run bats command # after bats is installed check version
```
