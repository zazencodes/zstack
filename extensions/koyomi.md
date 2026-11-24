# Koyomi

## What you get

Schedule a command on the machine that has the tools and files it needs. Koyomi keeps a log of each run. In [Swipe List](swipe-list.md), Koyomi starts the ingestion worker on the Mac with the signed-in browser. The worker picks up saved references while you’re doing something else.

## Requirements

macOS, or Linux with systemd and root access. Python 3.10 or later and `uv`. For multiple machines, each host needs key-based SSH access to the hub. Email alerts are optional and use your own SMTP account.

## Installation

Choose the machine that will hold the schedule and name each host that will run jobs. Decide whether you want email alerts. If you do, set the sender and recipient and supply your SMTP credentials during setup. Follow the project’s guide to install the CLI, configure each host and start its scheduler service. [Koyomi installation](https://github.com/zazencodes/koyomi#install)

If you use Swipe List, run `koyomi status` and check that the worker Mac is healthy before registering its job. [Swipe List installation](swipe-list.md#installation)

## First task

Try a one-time job on a host listed by `koyomi status`.

```text
Use Koyomi to schedule a one-time job on this host one minute from now. Have it run date, then show me the timestamp from its run log.
```

The timestamp in the log confirms the scheduler ran the command on that host.

## Updating

Update the checkout and reinstall on the hub first, then on each host. Check that the hosts agree on the Koyomi version and that their jobs are still scheduled.

## Uninstalling

List jobs on the host and decide which should move or stop. Uninstall the service and CLI after those jobs are accounted for. Ask before deleting stored schedules or run history.
