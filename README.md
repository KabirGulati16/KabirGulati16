name: Chess!

on:
  push:
    paths:
      - '**.pgn'

jobs:
  play:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v1

    - uses: cschleiden/chess-action@v1
      with:
        games: '**/*.pgn'

    - name: Commit changed files
      uses: stefanzweifel/git-auto-commit-action@v2.3.0
      with:
        commit_message: Played some chess!
        branch: master
        file_pattern: '*.pgn'
      env:
        GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}


