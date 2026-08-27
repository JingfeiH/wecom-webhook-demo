# WeCom Webhook Reminder Demo

This repository contains a GitHub Actions demo that sends 10 WeCom group robot test reminders from one manually triggered workflow run.

## How it works

- The workflow is `.github/workflows/wecom-reminder-demo.yml`.
- It is started manually with `workflow_dispatch`.
- The job loops 10 times.
- Each message includes the reminder number and the current time in `Asia/Shanghai`.
- The job waits 60 seconds between messages.
- The WeCom webhook is read from the GitHub Actions secret `WECOM_WEBHOOK`.

## Secret

Set the repository secret below before running the workflow:

```text
WECOM_WEBHOOK
```

Do not commit the webhook URL into the repository.

## Why this uses `sleep 60`

GitHub Actions scheduled workflows use cron syntax, but GitHub's minimum and practical scheduling granularity is not reliable for true once-per-minute reminders. This demo uses one manually triggered workflow run with an internal `sleep 60` loop so the 10 test messages can be sent at one-minute intervals.
