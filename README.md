![Ansible Lint](https://github.com/johanneskastl/ansible-role-restic_backups/workflows/Ansible%20Lint/badge.svg)

# restic_backups

Simple role to create local backups using restic

## Requirements

None.

## Role Variables

- `restic_backups_target_directory` (String): path to the local backup directory
- `restic_backups_paths` (List of Strings): list of paths to include in the
  backup
- `restic_backups_excludes` (List of Strings): list of paths (with wildcards) to
  exclude from the backup
- `restic_backups_retention_days` (Integer): number of days, used as argument
  for the `--keep-daily` option in the `restic forget` call after each
  successful backup
- `restic_backups_retention_weeks` (Integer): number of weeks, used as argument
  for the `--keep-weekly` option in the `restic forget` call after each
  successful backup
- `restic_backups_retention_months` (Integer): number of months, used as argument
  for the `--keep-monthly` option in the `restic forget` call after each
  successful backup
- `restic_backups_retention_years` (Integer): number of yars, used as argument
  for the `--keep-yearly` option in the `restic forget` call after each
  successful backup

## Dependencies

None

## Example Playbook

```yaml
- hosts: servers
  roles:
    - role: 'johanneskastl.restic_backups'
      restic_backups_target_directory: '/opt/restic_backups'
      restic_backups_paths:
        - '/home/'
      restic_backups_excludes:
        - '/home/*/.cache/'
        - '/home/*/go/'
```

## License

BSD-3-Clause

## Author Information

I am Johannes Kastl, reachable via git@johannes-kastl.de
