# Open Source 101: Beyond CI/CD

## 🎯 Goal

Use open source GitHub Actions to automate tasks and discuss making your very own GitHub Action.

## 💻 Steps

GitHub Actions can do much more than CI/CD. In this section, we'll consider how to use existing open source actions for three tasks:

#### 1. Apply a `triage` label to new issues

<details><summary>Hints</summary>

1. Browse a certain [awesome list of actions](https://github.com/sdras/awesome-actions) for ideas.

2. The [`actions` org](https://github.com/actions) has some interesting actions, but so does the community 👀.

</details>

<details><summary>Solution</summary>

```
name: "Triage"
on:
  issues:
    types: [opened]

jobs:
  triage:
    runs-on: ubuntu-latest
    steps:
      - uses: Naturalclar/issue-action@v1.0.0
        with:
          keywords: '[""]'
          labels: '["triage"]'
          github-token: "${{ secrets.GITHUB_TOKEN }}"
```
</details>


#### 2. Greet first time contributors (pull request or issue) with a greeting like "Hello, new contributor!"

<details><summary>Hints</summary>

1. Browse a certain [awesome list of actions](https://github.com/sdras/awesome-actions) for ideas.

2. The [`actions` org](https://github.com/actions) has some interesting actions, but so does the community 👀.

</details>

<details><summary>Solution</summary>

```
name: Greet first time contributors

on:
  issues:
    types: [opened]

jobs:
  greet:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/first-interaction@v1
      with:
        repo-token: ${{ secrets.GITHUB_TOKEN }}
        issue-message: 'Welcome! Thanks for opening an issue in this project!'
```
</details>

#### (Together) Make our very own Hello World action