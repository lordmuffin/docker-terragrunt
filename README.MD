# docker-gitea

Run with a command like this:
`docker run -it -p 3000:3000 --mount type=bind,source="/Users/ajackson/tmp/gitea",target="/data" --mount type=bind,source="/Users/ajackson/Google Drive/gitea/backups",target=/data/backups --rm gitea:latest`

## Backups
Backups are automatically handled by the entrypoint on closure of the container, but you should customize its location inside the startup command above.

## Restores
Run container first with the below command.

`docker run --entrypoint "/bin/ash" -it -p 3000:3000 --mount type=bind,source="/Users/ajackson/tmp/gitea",target="/data" --mount type=bind,source="/Users/ajackson/Google Drive/gitea/backups",target=/data/backups --rm gitea:latest`

This will get you and a working shell prompt `/work #` from here we can start the restore process.

```
./gitea web
CTRL+C // After service is fully running

cd /data
unzip /data/backups/gitea-dump-(datetime).zip
mv custom/conf/app.ini /work/tmp/gitea/conf/app.ini
rm -rf custom
unzip gitea-repo.zip
sqlite3 /data/db/gitea-db.sql <gitea-db.sql
```