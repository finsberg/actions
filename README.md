# Add publications

This repository contains an action for creating new bib items for your academic page. This is e.g used in https://github.com/finsberg/finsberg.github.io

Example usage
```yml
name: Scholar Bot

on:
  schedule:
    - cron: "0 8 * * 1" # Run every Monday at 08:00

jobs:
  scholar:
    permissions:
      contents: write
      pull-requests: write

    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v4
    - name: Set up Python 3.11
      uses: actions/setup-python@v5
      with:
        python-version: 3.11
    - name: Create _publications directory
      run: mkdir -p _publications
    - id: pygscholar
      uses: finsberg/add-publications@main
      with:
        name: "Henrik Finsberg"
        scholar_id: "NDPIHoEAAAAJ"
        cache_dir: ".pygscholar"
        working-directory: "."
        token: ${{ secrets.GITHUB_TOKEN }}
        bibdir: "_publications"
```
