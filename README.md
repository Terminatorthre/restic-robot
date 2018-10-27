# Restic Robot

Backups done right... by robots!

This is a small and simple wrapper application for [Restic](https://github.com/restic/restic/) that provides:

- Automatically creates repository if it doesn't already exist
- Scheduled backups - no need for system-wide cron
- Prometheus metrics- know when your backups don't run!
- JSON logs - for the robots!

## Usage

Just `go build` and run it, or, if you're into Docker, `southclaws/restic-robot`.

Environment variables:

- `SCHEDULE`: cron schedule
- `RESTIC_REPOSITORY`: repository name
- `RESTIC_PASSWORD`: repository password
- `RESTIC_ARGS`: additional args for backup command
- `PROMETHEUS_ENDPOINT`: metrics endpoint
- `PROMETHEUS_ADDRESS`: metrics host:port

Prometheus metrics:

- `backups_all_total`: The total number of backups attempted, including failures.
- `backups_successful_total`: The total number of backups that succeeded.
- `backups_failed_total`: The total number of backups that failed.
- `backup_duration_milliseconds`: The duration of backups in milliseconds.
- `backup_files_new`: Amount of new files.
- `backup_files_changed`: Amount of files with changes.
- `backup_files_unmodified`: Amount of files unmodified since last backup.
- `backup_files_processed`: Total number of files scanned by the backup for changes.
- `backup_added_bytes`: Total number of bytes added to the repository.
- `backup_processed_bytes`: Total number of bytes scanned by the backup for changes

It's that simple!