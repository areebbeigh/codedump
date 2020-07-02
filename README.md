# codedump
An unorganized reference dump for me.

- Testing SMTP servers with `swaks` example
  ```
  swaks --to areebbeigh@gmail.com \
    --from noreply@dphi.tech \
    --server email-smtp.ap-south-1.amazonaws.com:587 \
    --auth LOGIN \
    --auth-password <password> \
    --auth-user <user> \
    -tls
  ```
- [`git pull` a force updated branch](https://stackoverflow.com/questions/9813816/git-pull-after-forced-update)
