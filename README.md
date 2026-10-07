name: 🐍 Generate Contribution Snake

on:
  schedule:
    - cron: "0 0 * * *"

  workflow_dispatch:

permissions:
  contents: write

jobs:
  generate:
    runs-on: ubuntu-latest

    steps:
      - name: 🐍 Generate Snake
        uses: Platane/snk/svg-only@v3
        with:
          github_user_name: ayuzh98
          outputs: |
            dist/github-snake.svg?color_snake=#2563EB&color_dots=#EEF1F4,#D1FAE5,#86EFAC,#22C55E,#15803D

      - name: 🚀 Push Snake to output branch
        uses: crazy-max/ghaction-github-pages@v4
        with:
          target_branch: output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}/div>
