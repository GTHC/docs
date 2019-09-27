<!--
Template

** Description: **

** Example: **

Input:

```bash
```

```javascript
```

 -->

# `users`

## General

### GET `/api/v1/users/`
** Description: **
Grabs all user data

** Example: **

Input:
```bash
$ GET /api/v1/users/
```

Output:
```javascript
[
    {
        "id": 1,
        "email": "krishowell@mannschneider.co",
        "team_id": 1,
        "name": "Miss Kacy Powlowski",
        "phone": "781-879-5218",
        "team": {
            "id": 1,
            "name": "Team 1",
            "captain_id": 1,
            "tent_type": "Blue",
            "passcode": "ABC123"
        }
    },
    ...
    {
        "id": 9,
        "email": "howard@goodwin.name",
        "team_id": 3,
        "name": "Thora Trantow MD",
        "phone": "471.784.6380",
        "team": {
            "id": 3,
            "name": "Team 3",
            "captain_id": 3,
            "tent_type": "White",
            "passcode": "ABC123"
        }
    },
    ...
]
```
### GET `/api/v1/users/:id`
** Description: **
Grab user data of a single user by id

** Example: **

Input:
```bash
$ GET /api/v1/users/1
```

Output:
```javascript
{
    "id": 1,
    "email": "krishowell@mannschneider.co",
    "team_id": 1,
    "name": "Miss Kacy Powlowski",
    "phone": "781-879-5218",
    "team": {
        "id": 1,
        "name": "Team 1",
        "captain_id": 1,
        "tent_type": "Blue",
        "passcode": "ABC123"
    }
}
```

### POST `/api/v1/users/`
** Description: **
Create a user that will join an **EXISTING** team, and sign them in.

** Example: **

Input:
```bash
$ POST /api/v1/users/

{
	"name": "Aman Ibrahim",
	"email": "ami10@duke.edu",
	"password": "password",
	"password_confirmation": "password",
	"team_id": 1,
	"phone": "919",
	"availabilities": [
		{
			"start": "2019-01-18 13:13:41 +0000",
			"end": "2019-01-18 14:10:04 +0000",
			"somewhat": true
		}
	]
}

```

Output:
```javascript
{
    "status": "SUCCESS",
    "message": "User saved and signed in",
    "data": {
        ...
        // all the data involving the new user's team, captain, and user details
          "user": {
            "id": 32,
            "email": "amiami1001@duke.edu",
            "created_at": "2019-09-27T18:26:42.189Z",
            "updated_at": "2019-09-27T18:26:42.189Z",
            "team_id": 1,
            "name": "Aman Ibrahim",
            "phone": "919",
            "availabilities": [
                {
                    "id": 27,
                    "start": "2019-01-18T13:13:41.000Z",
                    "end": "2019-01-18T14:10:04.000Z",
                    "created_at": "2019-09-27T18:26:42.210Z",
                    "updated_at": "2019-09-27T18:26:42.210Z",
                    "user_id": 32,
                    "somewhat": true
                }
            ]
        },
        "team": {...},
        "captain": {...},
      }
}
```

### POST `api/v1/captains/`
** Description: ** Create a user that will create a **NEW** team, thus being a user and a captain, and sign them in. [Also refer to captain docs](/../captain)

** Example: **

Input:
```bash
$ POST /api/v1/captains/
{
	"user_name": "Aman Ibrahim",
	"email": "amnamibra10@duke.edu",
	"password": "password",
	"password_confirmation": "password",
	"team_name": "Test Team 1",
	"tent_type": "Blue",
	"passcode": "abc123",
	"phone": "919",
	"availabilities": [
		{
			"start": "2019-01-18 13:13:41 +0000",
			"end": "2019-01-18 14:10:04 +0000",
			"somewhat": true
		}
	]
}
```

Output:

```javascript
{
    "status": "SUCCESS",
    "message": "User, Captain, and Team created, and User signed in",
    "data": {
        "user": {
            "id": 33,
            "email": "amnamibra10@duke.edu",
            "created_at": "2019-09-27T18:35:41.720Z",
            "updated_at": "2019-09-27T18:35:41.756Z",
            "team_id": 6,
            "name": "Aman Ibrahim",
            "phone": "919",
            "availabilities": [
                {
                    "id": 28,
                    "start": "2019-01-18T13:13:41.000Z",
                    "end": "2019-01-18T14:10:04.000Z",
                    "created_at": "2019-09-27T18:35:41.725Z",
                    "updated_at": "2019-09-27T18:35:41.725Z",
                    "user_id": 33,
                    "somewhat": true
                }
            ]
        },
        "team": {
            "id": 6,
            "name": "Test Team 1",
            "captain_id": 6,
            "created_at": "2019-09-27T18:35:41.741Z",
            "updated_at": "2019-09-27T18:35:41.741Z",
            "tent_type": "Blue",
            "passcode": "abc123",
            "users": [
                {
                    "id": 33,
                    "email": "amnamibra10@duke.edu",
                    "created_at": "2019-09-27T18:35:41.720Z",
                    "updated_at": "2019-09-27T18:35:41.756Z",
                    "team_id": 6,
                    "name": "Aman Ibrahim",
                    "phone": "919",
                    "availabilities": [
                        {
                            "id": 28,
                            "start": "2019-01-18T13:13:41.000Z",
                            "end": "2019-01-18T14:10:04.000Z",
                            "created_at": "2019-09-27T18:35:41.725Z",
                            "updated_at": "2019-09-27T18:35:41.725Z",
                            "user_id": 33,
                            "somewhat": true
                        }
                    ]
                }
            ]
        },
        "captain": {
            "id": 6,
            "user_id": 33,
            "created_at": "2019-09-27T18:35:41.731Z",
            "updated_at": "2019-09-27T18:35:41.731Z"
        }
    }
}
```
### PUT `/api/v1/users/:id`
** Description: ** Update user (you must send in entire user ActiveRecord data with changes)

** Example: **

Input:

```bash
{
  password: "pass",
  password_confirmation: "pass"
}
```

```javascript
```

## Availability

## Avatar

## Password

## Session
