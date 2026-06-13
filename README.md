# gh-prompt-scan Action

Automatically scan your GitHub Actions workflows for prompt injection vulnerabilities on every pull request.

## Usage

```yaml
name: Security scan
on: [pull_request]

jobs:
  scan:
    runs-on: ubuntu-latest
    permissions:
      contents: read
    steps:
      - uses: actions/checkout@v4
      - uses: panther-0707/gh-prompt-scan-action@v1
```

## What it detects

| Vector | Severity | Description |
|--------|----------|-------------|
| TV4 | CRITICAL | Attacker data directly in shell commands |
| TV5 | CRITICAL | Attacker data through AI into shell commands |
| TV6 | CRITICAL | Attacker-controlled workspace fed to AI |
| TV7 | MEDIUM | AI steps triggerable by anyone |

Based on the Heimdallr research paper (arXiv:2605.05969).

## Inputs

| Input | Default | Description |
|-------|---------|-------------|
| `paths` | `.` | Path to repo root to scan |
| `fail-on` | `high` | Minimum severity to fail the build |

## Links

- [PyPI](https://pypi.org/project/gh-prompt-scan/)
- [GitHub](https://github.com/panther-0707/CIGI)
- [Research paper](https://arxiv.org/abs/2605.05969)