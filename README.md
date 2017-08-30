# BlockWorksProtocol
Protocol for BlockWorks that use PlayerIO's API.


### Game and Room Information  
```
ID: blockworks-frdrlhtjneoipehnx9tmg  
Version: 2  
RoomType: Simple-2  
```
### Rooms

| Type        | Room Id
| ----        | ---------
| Gray        | OR_Gray
| Red         | OR_Red
| Yellow      | OR_Yellow
| Green       | OR_Green
| Blue        | OR_Blue


### say
Occurs when a player sends a chat message.

| Id  | Type      | Name      | Description
| --- | ----      | ----      | -----------
| `0` | `Integer` | Player Id | The player's id.
| `1` | `String`  | Text      | The chat message text.

### online
Occurs when you join a world and there contains players in the world.

| Id   | Type        | Name               | Description
| ---  | ---         | ----               | -----------
| `0`  | `Integer`   | Id                 | The player's id.
| `1`  | `String`    | idk                | The player's derp
| `2`  | `String`    | Nickname           | The player's nickname.
| `3`  | `Boolean`   | idk                | idk
| `4`  | `Uint`      | idk                | idk
| `5`  | `Integer`   | idk                | idk
| `6`  | `Single`    | X                  | The player's X position.
| `7`  | `Single`    | Y                  | The player's Y position.
| `..` | `..`        | `..`               | Contains more users from 0 to 7 again.

### b
Occurs when a player draws a block.

| Id   | Type        | Name               | Description
| ---  | ---         | ----               | -----------
| `0`  | `Integer`   | Id                 | The player's id.
| `1`  | `Integer`   | Block Info         | Contains layer, x and y placement.
| `2`  | `Integer`   | Block Id           | The placed block id.
| `..` | `Integer`   | Rotation           | The rotation of the block.
