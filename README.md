name: Generate Snake Animation

on:
  push:
    branches:
      - main  # Replace 'main' with your default branch name if different
  schedule:
    - cron: "0 0 * * *"  # Runs daily at midnight (UTC)

jobs:
  generate:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout Repository
        uses: actions/checkout@v3

      - name: Generate Snake Animation
        uses: Platane/snk@v2
        with:
          github_user_name: akash-dutta  # Replace with your GitHub username
          outputs: dist/snake.svg

      - name: Commit and Push Snake Animation
        run: |
          git config --global user.name 'github-actions[bot]'
          git config --global user.email '41898282+github-actions[bot]@users.noreply.github.com'
          git add -A
          git commit -m "Generate snake animation"
          git push
