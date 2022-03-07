# why-dont-using-sqlite-on-heroku

因为在 heroku 上部署 flask web 项目用到了 sqlite 作为数据库, 本地运行和测试都没问题, 但是部署到 heroku 却不能打开网页, 遇到了报错, HTTP 状态码500, 是服务器那边的问题， `heroku logs --tail` 显示:
```
(sqlite3.OperationalError) no such table:
```
然后在 stack overflow 查到了相关的内容, 记录一下:

## reference

1. https://stackoverflow.com/questions/56158266/sqlite3-operationalerror-no-such-table-on-heroku

## detail contents

Q: 

A: You really shouldn't use [SQLite on Heroku](https://devcenter.heroku.com/articles/sqlite3). Its filesystem is ephemeral. Any changes you make to files will be lost the next time your dyno restarts. This [happens frequently](https://devcenter.heroku.com/articles/dynos#automatic-dyno-restarts) (at least once per day).

If you really must use SQLite (and I strongly advise against that), treat it as read-only. You'll have to commit your database file on your local development machine and push that commit to Heroku. Even then it might not work properly. Heroku famously [generates errors if Ruby users even try to install the `sqlite3` gem](https://devcenter.heroku.com/articles/sqlite3#getting-a-sqlite-error-even-though-it-is-not-in-the-gemfile).