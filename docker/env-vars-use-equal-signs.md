# Docker Env Vars Use Equal Signs

I did something pretty stupid a week or two ago. I was setting up a MariaDB database using Docker-compose, and I kept getting an error saying that `MYSQL_ROOT_PASSWORD` was not set. This made no sense to me - of course `MYSQL_ROOT_PASSWORD` is in the `.env` file, right?

Wrong. I accidentally used colons ( a carry-over from a CF script) instead of equal signs.

## How Not To Write A .env File

```bash
# WRONG
MYSQL_USER:runDockerTests
MYSQL_ROOT_PASSWORD:kjhsdfkjh98798798
MYSQL_DATABASE:myDB
```

_Notice the colons, people._

## How To Write A .env File

```bash
# RIGHT
MYSQL_USER=runDockerTests
MYSQL_ROOT_PASSWORD=kjhsdfkjh98798798
MYSQL_DATABASE=myDB
```

_ahh, delightful equal signs, whether in `Docker-compose.yml` or `.env` files._

And of course, I capped it off by [proclaiming my stupidity on Twitter][1].

[1]: https://twitter.com/mborn319/status/1089354226269077504