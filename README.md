# BlockWorksProtocol
Protocol for BlockWorks that use PlayerIO's API.


### #Game and Room Information  
```
ID: blockworks-frdrlhtjneoipehnx9tmg  
Version: 1  
RoomType: Simple-1  
```
### #Rooms

| Type        | Room Id
| ----        | ---------
| Gray        | OW_Gray-{version}
| Red         | OW_Red-{version}
| Yellow      | OW_Yellow-{version}
| Green       | OW_Green-{version}
| Blue        | OW_Blue-{version}

### #world
The state of the world that is sent when you just join, the world is cleared or the level is reloaded from the database.

| Id   | Type        | Name               | Description
| ---  | ---         | ----               | -----------
| `0`  | `String`    | Owner ID           | The owner’s account ID.
| `1`  | `String`    | Title              | The title of the world.
| `2`  | `Integer`   | Width              | The width of the world.
| `3`  | `Integer`   | Height             | The height of the world.
| `4`  | `String`    | WS                 | Indicates the START of world serialization.
| `5`  | `Boolean`   | IsCleared          | Whether or not the client should clear the world before the new blocks are there.
| `6`  | `Integer`   | Layer              | The layer of the block.
| `7`  | `Integer`   | Block ID           | The ID of the block.
| `8`  | `Byte[]`    | X                  | All the X values of this block.
| `9`  | `Byte[]`    | Y                  | All the Y values of this block.
| `..` | `..`        | Arguments          | The arguments of the block (if any).
| `..` | `..`        | `..`               | Repeated for each block in the world.
| `..` | `String`    | WE                 | Indicates the END of world serialization.
| `..` | `String`    | SS                 | Indicates the START of signal information.
| `..` | `Integer`   | Open Channel       | The ID of a channel that is open.
| `..` | `String`    | SE                 | Indicates the END of signal information.


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


### Colored Avatar ID's
| Color | Id
| ---   | ---
| ![AvatarRed](https://raw.githubusercontent.com/capasha/BlockWorksProtocol/master/images/avatar/red.png) | `0`
| ![AvatarOrange](https://raw.githubusercontent.com/capasha/BlockWorksProtocol/master/images/avatar/orange.png) | `1`
| ![AvatarYellow](https://raw.githubusercontent.com/capasha/BlockWorksProtocol/master/images/avatar/yellow.png) | `2`
| ![AvatarGreen](https://raw.githubusercontent.com/capasha/BlockWorksProtocol/master/images/avatar/green.png) | `3`
| ![AvatarCyan](https://raw.githubusercontent.com/capasha/BlockWorksProtocol/master/images/avatar/cyan.png) | `4`
| ![AvatarBlue](https://raw.githubusercontent.com/capasha/BlockWorksProtocol/master/images/avatar/blue.png) | `5`
| ![AvatarPurple](https://raw.githubusercontent.com/capasha/BlockWorksProtocol/master/images/avatar/purple.png) | `6`

### Faces Avatar ID's
| Color | Id
| ---   | ---
| ![Avatar0](https://raw.githubusercontent.com/capasha/BlockWorksProtocol/master/images/avatar/0.png) | `0`
| ![Avatar1](https://raw.githubusercontent.com/capasha/BlockWorksProtocol/master/images/avatar/1.png) | `1`
| ![Avatar2](https://raw.githubusercontent.com/capasha/BlockWorksProtocol/master/images/avatar/2.png) | `2`
| ![Avatar3](https://raw.githubusercontent.com/capasha/BlockWorksProtocol/master/images/avatar/3.png) | `3`
| ![Avatar4](https://raw.githubusercontent.com/capasha/BlockWorksProtocol/master/images/avatar/4.png) | `4`
| ![Avatar5](https://raw.githubusercontent.com/capasha/BlockWorksProtocol/master/images/avatar/5.png) | `5`

