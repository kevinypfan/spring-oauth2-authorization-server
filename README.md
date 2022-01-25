
## 獲取授權證
```shell
'http://localhost:9000/oauth2/authorize?client_id=client&client_secret=secret&response_type=code&redirect_uri=http://127.0.0.1:8080/authorized'
```

## 獲取通關權杖

```shell
curl --location --request POST 'http://localhost:9000/oauth2/token' \
--header 'Authorization: Basic Y2xpZW50OnNlY3JldA==' \
--header 'Content-Type: application/x-www-form-urlencoded' \
--data-urlencode 'grant_type=authorization_code' \
--data-urlencode 'code=<code>' \
--data-urlencode 'redirect_uri=http://127.0.0.1:8080/authorized'
```
## 刷新權杖

```shell
curl --location --request POST 'http://localhost:9000/oauth2/token' \
--header 'Authorization: Basic Y2xpZW50OnNlY3JldA==' \
--header 'Content-Type: application/x-www-form-urlencoded' \
--data-urlencode 'grant_type=refresh_token' \
--data-urlencode 'refresh_token=<refresh_token>'
```

## 撤销權杖

- 通过 access_token
```shell
curl --location --request POST 'http://localhost:9000/oauth2/revoke' \
--header 'Authorization: Basic Y2xpZW50OnNlY3JldA==' \
--header 'Content-Type: application/x-www-form-urlencoded' \
--data-urlencode 'token=<access_token>' \
--data-urlencode 'token_type_hint=access_token'
```

- 通过 refresh_token
```shell
curl --location --request POST 'http://localhost:9000/oauth2/revoke' \
--header 'Authorization: Basic Y2xpZW50OnNlY3JldA==' \
--header 'Content-Type: application/x-www-form-urlencoded' \
--data-urlencode 'token=<refresh_token>' \
--data-urlencode 'token_type_hint=refresh_token'
```