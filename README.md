# BlockWorksProtocol
Protocol for BlockWorks that use PlayerIO's API.


### #Game and Room Information  
```
ID: blockworks-frdrlhtjneoipehnx9tmg  
Version: 2  
RoomType: Simple-2  
```
### #Rooms

| Type        | Room Id
| ----        | ---------
| Gray        | OR_Gray
| Red         | OR_Red
| Yellow      | OR_Yellow
| Green       | OR_Green
| Blue        | OR_Blue


### #say
Occurs when a player sends a chat message.

| Id  | Type      | Name      | Description
| --- | ----      | ----      | -----------
| `0` | `Integer` | Player Id | The player's id.
| `1` | `String`  | Text      | The chat message text.

### #online
This contains everyone who joined the level before you.

| Id   | Type        | Name               | Description
| ---  | ---         | ----               | -----------
| `0`  | `Integer`   | Player ID          | The player’s unique ID.
| `1`  | `String`    | Account ID         | The player’s account ID.
| `2`  | `String`    | Nickname           | The player's nickname.
| `3`  | `Boolean`   | Edit Rights        | Whether the player has editing rights.
| `4`  | `Uint`      | Avatar ID          | The customization of the avatar.
| `5`  | `Integer`   | Staff Rank         | The staff rank ID of the player. (-1 if not staff)
| `6`  | `Float`     | X                  | The player's X position.
| `7`  | `Float`     | Y                  | The player's Y position.
| `..` | `..`        | `..`               | Contains more users from 0 to 7 again.

### #avatar
Occurs whenever a player changes their avatar.

| Id   | Type        | Name               | Description
| ---  | ---         | ----               | -----------
| `0`  | `Integer`   | Player Id          | The player’s unique ID.
| `1`  | `Integer`   | Avatar             | The player’s new Avatar data.

### #b
Occurs when a player draws a block.

| Id   | Type        | Name               | Description
| ---  | ---         | ----               | -----------
| `0`  | `Integer`   | Player Id          | The player’s unique ID.
| `1`  | `Integer`   | Block Info         | [Contains layer, x and y placement.](https://pastebin.com/x9Sf9dwa)
| `2`  | `Integer`   | Block Id           | The placed block id.
| `..` | `Integer`   | Arguments          | The arguments of the block.

### #say
Occurs whenever a player sends a chat message.

| Id   | Type        | Name               | Description
| ---  | ---         | ----               | -----------
| `0`  | `Integer`   | Player Id          | The player’s unique ID.
| `1`  | `String`    | Message            | The message sent from the player.

### Staff Rank
| Id   | Type
| ---  | ---
| `-1` | None
| `0`  | Unknown
| `1`  | Moderator
| `2`  | Developer
| `3`  | Administrator


### Avatar ID's
| Id   | Type
| ---  | ---
| `0`  | Not done.
| `0`  | Not done.
| `0`  | Not done.
| `0`  | Not done.
| `0`  | Not done.

