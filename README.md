# PG-WAL-E

Configure's Heroku's [WAL-E backup tool](https://github.com/wal-e/wal-e) for Ansible.

## Useful Commands

### I want to test my archive command

```sql
SELECT pg_switch_xlog();
```

### database recovery

1. stop the database: `sudo service postgresql stop`.
2. delete the postgres data directory.
3. look in `recovery.example`, there's a command here for downloading a base
  copy of the database.
4. copy `recovery.example` to `recovery.conf`. this will setup recovery from logs.
5. start the database: `sudo service postgresql start`

### pg_xlog is corrupt, help!

```shell
/usr/lib/postgresql/9.3/bin/pg_resetxlog /mnt/postgresql/
```
