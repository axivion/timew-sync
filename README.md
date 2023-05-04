# timew-sync

Sync your time tracked with [`timew`](https://timewarrior.net/) to a JIRA
instance. This works by inspecting the tags of your `timew` intervals to
extract possible JIRA-IDs from it.

## Installation

```
git clone https://github.com/axivion/timew-sync.git
cd timew-sync/
python -m venv SYNC_VENV
source SYNC_VENV/bin/activate
pip install --user .
ln -s (pwd)/SYNC_VENV/bin/timew-sync ~/.timewarrior/extensions/sync.py
deactivate
```

## Configuration

To make this work, please create a `~/.timewarrior/timew-sync.toml`:

```
[Jira]
url = "XXX"
username = "XXX"
password = "XXX"
pattern = "(\\w+-\\d+)"
```

The `pattern` is a Python regex that is matched against every tag of the
`timew` intervals. It must contain at least one group.

When experiencing `toml.decoder.TomlDecodeError: Reserved escape sequence used` make sure to escape backslashes.

## Using

Run `timew sync :day` to sync your intervals to JIRA.
