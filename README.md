# Alerting as Code Example

A simplified example repository showing how alerting configuration for
Prometheus and Alertmanager can be managed as code, reviewed through
pull requests, validated with `promtool`/`amtool` in CI, and deployed
via GitHub Actions.

## Structure

```
prometheus/
  alert-rules.yml       - Prometheus alerting rules
alertmanager/
  alertmanager.yml      - Alertmanager routing and receiver configuration
.github/workflows/
  validate.yml          - Validates configuration on pull requests
  deploy.yml            - Deploys configuration on merge to main
deploy/
  prometheus.sh         - Placeholder deploy step for Prometheus
  alertmanager.sh       - Placeholder deploy step for Alertmanager
```

## Workflow

1. A change to an alerting rule or routing configuration is made in a
   branch and submitted as a pull request.
2. `validate.yml` runs `promtool check rules` and `amtool check-config`
   to catch configuration errors before merge.
3. Once reviewed and merged, `deploy.yml` applies the configuration to
   the monitoring environment.

This repository accompanies the blog post "GitHub as the Single Source
of Truth for Alerts" and is intended for demonstration purposes only —
the deploy scripts are placeholders and do not target a real Prometheus
or Alertmanager instance.
