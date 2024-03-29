# One-Time-Secret

### This is JSON API analog of https://onetimesecret.com developed with Python, Flask and Gunicorn


- Method ```/generate``` gets secret and password as POST JSON data and returns generated id.
- Method ```/secrets/{generated id}?key={password}``` returns secret and deletes it from the database

All secrets are stored in a MongoDB database encrypted with AES 256 algorithm and can be decrypted only by the client password.


### POST secret
Request:

```bash
curl -H "Content-Type: application/json"  \
  --request POST \
  --data '{"secret": "Some text to hide!", "key": "super_secret_pswd"}' \
  https://onetimesecret.herokuapp.com/generate
```

Response:

```ef7b4f25c55a4cfe8abec9887cea1966```

### GET secret
Request:

```bash
curl https://onetimesecret.herokuapp.com/secrets/ef7b4f25c55a4cfe8abec9887cea1966?key=super_secret_pswd
```

Response:

```Some text to hide!```
