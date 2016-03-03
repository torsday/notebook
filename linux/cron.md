# Cron

A time-based job scheduler.

---

List crontabs

```sh
crontab -l
```

Create, or open, the crontab file.

```sh
crontab -e
```

Choose when you would like the job to run.

Every job is a line in your crontab file. The first 5 arguments specify the time to run the job, and the 6th argument is the command to run.

| arg position | meaning                        |
|:------------:|--------------------------------|
|      1       | Minute (0 - 59)                |
|      2       | Hour (0 - 23)                  |
|      3       | Day of Month (1 - 31)          |
|      4       | Month (1-12)                   |
|      5       | Day of Week (0 - 6) Sunday = 0 |
|      6       | Command                        |

e.g. every 30 min

```sh
*/30 * * * * /path/to/my_script.pl
```

---

## References

-   [Wikipedia: Cron](https://en.wikipedia.org/wiki/Cron)
