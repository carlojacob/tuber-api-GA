# Tuber-API

This is the API documentation for an application that allows users to save their favorite YouTube videos with additional customized information. The developer used the Atom text-editing platform, along with git and other software to write and test the code. The developer wrote the API code using Express.js (client facing code using HTML, SCSS (CSS), React and JavaScript).

### Github Repository Links
The Github repositories for this project are located here:
[Application Client](https://github.com/carlojacob/tuber)
[Application API](https://github.com/carlojacob/tuber-api)

### Deployed Sites
[Tuber Client](https://carlojacob.github.io/tuber)
[Tuber API](https://tuber-ccjwdi.herokuapp.com/)

### What is Tuber
<!-- Tuber is an application that can be used by cyclists to log date, location, distance and time data from their bike rides; then review, edit or delete previous ride data. The user creates a unique, password-protected account; then the user enters new ride data on a form that is provided and/or views all of their existing rides, if any exist. -->

### Wireframes
Initial wireframes images:
![Homepage](https://i.imgur.com/LOiXLnJ.jpg "Wireframe Homepage")

![Signed In Page](https://i.imgur.com/8KW5UoB.jpg "Wireframe Signed In Page")

![View/Show Page](https://i.imgur.com/HAlIvMU.jpg "Wireframe View/Show Page")

![Add/Create Page](https://i.imgur.com/8ETQIAy.jpg "Wireframe Add/Create Page")

![Edit/Update Page](https://i.imgur.com/XNktxI1.jpg "Wireframe Edit/Update Page")

### User Stories
Tuber user stories:
1. As a first-time user, I want to create an account.
2. As a user, I want to sign in.
3. As a user, I want to change my password.
4. As a user, I want to sign out.
5. As a returning user, I want to see a listing of all of my previously saved videos.
6. As a user, I want to see details of or watch one of my previously saved videos.
7. As a user, I want to create new videos.
8. As a user, I want to update previously saved videos.
9. As a user, I want to delete previously saved videos.
10. As a user, I want to select whether videos autoplay on `show` (stretch).
11. As a user, I want to select whether videos loop in `show` window (stretch).
12. As a user, I want to sort videos by fields in `index` window (stretch).
13. As a user, I want to search fields for strings in `index` window (stretch).
14. As a user, I want to select "favorite" videos (stretch).

### Entity Relationship Diagram
![Entity Relationship Diagram](https://i.imgur.com/rNElxUn.jpg "Entity Relationship Diagram")

### Resource Tables
![Resource Tables](https://i.imgur.com/Ytmx9vV.jpg "Resource Tables")

## API

### Authentication

| Verb   | URI Pattern            | Controller#Action |
|--------|------------------------|-------------------|
| POST   | `/sign-up`             | `users#signup`    |
| POST   | `/sign-in`             | `users#signin`    |
| PATCH  | `/change-password/`    | `users#changepw`  |
| DELETE | `/sign-out/`           | `users#signout`   |

#### POST /sign-up

Request:

```sh
curl --include --request POST http://localhost:4741/sign-up \
  --header "Content-Type: application/json" \
  --data '{
    "credentials": {
      "email": "an@example.email",
      "password": "an example password",
      "password_confirmation": "an example password"
    }
  }'
```

```sh
scripts/sign-up.sh
```

Response:

```md
HTTP/1.1 201 Created
Content-Type: application/json; charset=utf-8

{
  "user": {
    "id": 1,
    "email": "an@example.email"
  }
}
```

#### POST /sign-in

Request:

```sh
curl --include --request POST http://localhost:4741/sign-in \
  --header "Content-Type: application/json" \
  --data '{
    "credentials": {
      "email": "an@example.email",
      "password": "an example password"
    }
  }'
```

```sh
scripts/sign-in.sh
```

Response:

```md
HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8

{
  "user": {
    "id": 1,
    "email": "an@example.email",
    "token": "33ad6372f795694b333ec5f329ebeaaa"
  }
}
```

#### PATCH /change-password/

Request:

```sh
curl --include --request PATCH http://localhost:4741/change-password/ \
  --header "Authorization: Token token=$TOKEN" \
  --header "Content-Type: application/json" \
  --data '{
    "passwords": {
      "old": "an example password",
      "new": "super sekrit"
    }
  }'
```

```sh
TOKEN=33ad6372f795694b333ec5f329ebeaaa scripts/change-password.sh
```

Response:

```md
HTTP/1.1 204 No Content
```

#### DELETE /sign-out/

Request:

```sh
curl --include --request DELETE http://localhost:4741/sign-out/ \
  --header "Authorization: Token token=$TOKEN"
```

```sh
TOKEN=33ad6372f795694b333ec5f329ebeaaa scripts/sign-out.sh
```

Response:

```md
HTTP/1.1 204 No Content
```
