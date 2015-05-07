# PG-WAL-E

Configure's Heroku's [WAL-E backup tool](https://github.com/wal-e/wal-e) for Ansible.

## Useful Commands

### I want to test my archive command

```sql
SELECT pg_switch_xlog();
```

### I want to manually download a copy of the database

```shell
su - postgres -c 'AWS_SECRET_ACCESS_KEY="my-secret" wal-e -k my-key --s3-prefix=s3://my-bucket backup-fetch /mnt/postgresql/ LATEST'
```

### pg_xlog is corrupt, help!

```shell
/usr/lib/postgresql/9.3/bin/pg_resetxlog /mnt/postgresql/
```

### recovery from logs

1. stop the database `sudo service postgresql stop`.
2. delete the data directory.
3. run `su - postgres -c 'AWS_SECRET_ACCESS_KEY="my-secret" wal-e -k my-key --s3-prefix=s3://my-bucket backup-fetch /mnt/postgresql/ LATEST'`
4. copy `recovery.example` to `recovery.conf`
