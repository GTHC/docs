# `users`

## General

### GET `/api/v1/users/`
Grabs all user data

##### Example
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
Grab user data of a single user by id

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
Create a user that will join an **EXISTING** team, and sign them in.

##### Example
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

### PUT `/api/v1/users/:id`

## Availability

## Avatar

## Password

## Session
