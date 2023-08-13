# rsync-backup-and-rotate

These scripts provide a simple way to run rsync and rotate the backups to keep copies of modified files.

On Linux, the rotation is done with hardlinks, which means that the disk space is only used for multiple
copies of an unchanged file in multiple backup sets. Only changed files contribute to the disk space.

## Usage

### backup-rsync

```
backup-rsync
This script creates rsync backups of a server.

backup-rsync comes with ABSOLUTELY NO WARRANTY. Use at your own risk.

Usage: backup-rsync [OPTION(S)]... <fqdn|hostname|localhost>

Options
  -a,    available drive space percentage needed to run backup
  -b,    local destination backup path
  -c,    check drive space available before running backup?
  -e,    path to exclude file with patterns that should not be backed up
  -n,    show what would have been transferred
  -o,    additional rsync options
  -p,    remote or local source data path
  -s,    ssh address to remote server <user@hostname>
  -h,    help and usage instructions
```

To skip backing up certain files and directories, create an exclude file with patterns that should not be backed up by rsync.

`/root/.rsync-exclude`

```
*.bak
log/*
.DS_Store
```

The backup will be written into the directory `/backup/path/<fqdn|hostname|localhost>/daily.0/`

### backup-rotate

```
backup-rotate
This script creates rsync backups of a server.

backup-rotate comes with ABSOLUTELY NO WARRANTY. Use at your own risk.

Usage: backup-rotate [OPTION(S)]... <fqdn|hostname|localhost>

Options
  -a,    available drive space percentage needed to rotate backup
  -b,    local destination backup path
  -c,    check drive space available before rotating backup?
  -h,    help and usage instructions
```
