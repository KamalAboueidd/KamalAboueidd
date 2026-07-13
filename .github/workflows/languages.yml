name: Generate languages card

on:
  schedule: # execute every 12 hours
    - cron: "* */12 * * *"

  workflow_dispatch:

  push:
    branches:
    - main

jobs:
  generate:
    permissions:
      contents: write
    runs-on: ubuntu-latest
    timeout-minutes: 5

    steps:
      - name: generate languages.svg
        uses: readme-tools/github-readme-stats-action@v1
        with:
          card: top-langs
          options: username=${{ github.repository_owner }}&locale=en&hide_title=false&layout=compact&card_width=320&langs_count=5&theme=dracula&hide_border=false
          path: dist/languages.svg
          token: ${{ secrets.GITHUB_TOKEN }}


      - name: push languages.svg to the output branch
        uses: crazy-max/ghaction-github-pages@v3.1.0
        with:
          target_branch: languages-output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
