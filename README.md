# BlockWorksProtocol
Protocol for BlockWorks that use PlayerIO's API.


### Game and Room Information  
```
ID: blockworks-frdrlhtjneoipehnx9tmg  
Version: 1  
RoomType: Simple-1  
```
### # Rooms

| Type        | Room Id
| ----        | ---------
| Gray        | OW_Gray-{version}
| Red         | OW_Red-{version}
| Yellow      | OW_Yellow-{version}
| Green       | OW_Green-{version}
| Blue        | OW_Blue-{version}
| Test World  | OW_Test-{version}

# Messages from the game

### # "world"
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

[Read World data between WS and WE](https://pastebin.com/TKFq7k6S)

### # "online"
This contains everyone who joined the level before you.

| Id   | Type        | Name               | Description
| ---  | ---         | ----               | -----------
| `0`  | `Integer`   | Player ID          | The player’s unique ID.
| `1`  | `String`    | Connection ID      | The player’s connection ID.
| `2`  | `String`    | Nickname           | The player's nickname.
| `3`  | `Boolean`   | Edit Rights        | Whether the player has editing rights.
| `4`  | `Uint`      | Avatar ID          | The customization of the avatar.
| `5`  | `Integer`   | Staff Rank         | The staff rank ID of the player. (-1 if not staff)
| `6`  | `Float`     | X                  | The player's X position.
| `7`  | `Float`     | Y                  | The player's Y position.
| `..` | `..`        | `..`               | Contains more users from 0 to 7 again.

### # "join"
Sends when a user joins the world, and who wasn’t previously online before you joined.

| Id   | Type        | Name               | Description
| ---  | ---         | ----               | -----------
| `0`  | `Integer`   | Player ID          | The player’s unique ID.
| `1`  | `String`    | Connection ID      | The player’s connection ID.
| `2`  | `String`    | Nickname           | The player's nickname.
| `3`  | `Boolean`   | Edit Rights        | Whether the player has editing rights.
| `4`  | `Uint`      | Avatar ID          | The customization of the avatar.
| `5`  | `Integer`   | Staff Rank         | The staff rank ID of the player.
| `6`  | `Float`     | X                  | The player's X position.
| `7`  | `Float`     | Y                  | The player's Y position.

### # "left"
You get this message when someone leaves the room.

| Id   | Type        | Name               | Description
| ---  | ---         | ----               | -----------
| `0`  | `Integer`   | Player ID          | The player’s unique ID.

### # "you"
Your data when you first join the world.

| Id   | Type        | Name               | Description
| ---  | ---         | ----               | -----------
| `0`  | `Integer`   | Player Id          | Your unique ID.
| `1`  | `String`    | Connection Id      | Your connection ID.
| `2`  | `String`    | Nickname           | Your nickname
| `3`  | `Boolean`   | Has Edit           | Whether you have editing rights.
| `4`  | `Integer`   | Avatar Id          | Your avatar ID.
| `5`  | `Integer`   | Staff Rank         | Your staff rank.
| `6`  | `Float`     | X                  | Your X position.
| `7`  | `Float`     | Y                  | Your Y position.

### # "m"
Occurs whenever a player moves.

| Id   | Type        | Name               | Description
| ---  | ---         | ----               | -----------
| `0`  | `Integer`   | Player ID          | The player’s unique ID.
| `1`  | `Float`     | X                  | The player’s X position.
| `2`  | `Float`     | Y                  | The player’s Y position.
| `3`  | `Integer`   | Horizontal         | The horizontal component of the movement.
| `4`  | `Integer`   | Vertical           | The vertical component of the movement.
| `5`  | `Float`     | Speed X            | The speed in the X direction.
| `6`  | `Float`     | Speed Y            | The speed in the Y direction.

### # "avatar"
Occurs whenever a player changes their avatar.

| Id   | Type        | Name               | Description
| ---  | ---         | ----               | -----------
| `0`  | `Integer`   | Player Id          | The player’s unique ID.
| `1`  | `Integer`   | Avatar Id          | The player’s new Avatar data.

### # "s"
Occurs when the channel state is changed.

| Id   | Type        | Name               | Description
| ---  | ---         | ----               | -----------
| `0`  | `Uint`      | Data               | [Contains X, Y and Channel](https://pastebin.com/x9Sf9dwa)
| `1`  | `Integer`   | Channel Id         | The ID of the channel
| `2`  | `Boolean`   | Is open            | Whether or not the channel state is open.

### # "fly"
Occurs whenever a player toggles free-fly mode.

| Id   | Type        | Name               | Description
| ---  | ---         | ----               | -----------
| `0`  | `Integer`   | Player Id          | The player’s unique ID.
| `1`  | `Boolean`   | Is Flying          | Whether or not if the player is flying.

### # "b"
Occurs when a player draws a block.

| Id   | Type        | Name               | Description
| ---  | ---         | ----               | -----------
| `0`  | `Integer`   | Player Id          | The player’s unique ID.
| `1`  | `Integer`   | Block Info         | [Contains X, Y and Channel](https://pastebin.com/x9Sf9dwa)
| `2`  | `Integer`   | Block Id           | The placed block id.
| `..` | `Integer`   | Arguments          | The arguments of the block.

### # "say"
Occurs whenever a player sends a chat message.

| Id   | Type        | Name               | Description
| ---  | ---         | ----               | -----------
| `0`  | `Integer`   | Player Id          | The player’s unique ID.
| `1`  | `String`    | Message            | The message sent from the player.

# Send messages

### ! "avatar"
| Id   | Type        | Name         | Description
| ---  | ---         | ----         | -----------
| `0`  | `Uint`      | Avatar id    | The new Avatar Data

### ! "b"
| Id   | Type        | Name         | Description
| ---  | ---         | ----         | -----------
| `0`  | `Uint`      | Data         | [The X, Y and channel converted to Uint.](https://pastebin.com/ZPDLML28)
| `1`  | `Uint`      | Block Id     | The block id. Remember it need to be Uint.
| `..` | `...`       | Arguments    | The arguments of the block (if any).



# Misc

### Staff Rank
| Id   | Type
| ---  | ---
| `-1` | None
| `0`  | Unknown
| `1`  | Moderator
| `2`  | Developer
| `3`  | Administrator

### Channel Types
| Id   | Type
| ---  | ---
| `0`  | Switch
| `1`  | Button


### Avatar ID's
| Color | Face | Id | Face | Id | Face | Id | Face | Id | Face | Id | Face | Id
| ---   | ---  | ---| ---  | ---| ---  | ---| ---  | ---| ---  | ---| ---  | ---
| ![AvatarRed](https://raw.githubusercontent.com/capasha/BlockWorksProtocol/master/images/avatar/red.png) | ![Avatar0](https://raw.githubusercontent.com/capasha/BlockWorksProtocol/master/images/avatar/0.png) | `0` | ![Avatar1](https://raw.githubusercontent.com/capasha/BlockWorksProtocol/master/images/avatar/1.png) | `128` | ![Avatar2](https://raw.githubusercontent.com/capasha/BlockWorksProtocol/master/images/avatar/2.png) | `256` | ![Avatar3](https://raw.githubusercontent.com/capasha/BlockWorksProtocol/master/images/avatar/3.png) | `384` | ![Avatar4](https://raw.githubusercontent.com/capasha/BlockWorksProtocol/master/images/avatar/4.png) | `512` | ![Avatar5](https://raw.githubusercontent.com/capasha/BlockWorksProtocol/master/images/avatar/5.png) | `640` | ![Avatar6]
| ![AvatarOrange](https://raw.githubusercontent.com/capasha/BlockWorksProtocol/master/images/avatar/orange.png) | ![Avatar0](https://raw.githubusercontent.com/capasha/BlockWorksProtocol/master/images/avatar/0.png) | `1` | ![Avatar1](https://raw.githubusercontent.com/capasha/BlockWorksProtocol/master/images/avatar/1.png) | `129` | ![Avatar2](https://raw.githubusercontent.com/capasha/BlockWorksProtocol/master/images/avatar/2.png) | `257` | ![Avatar3](https://raw.githubusercontent.com/capasha/BlockWorksProtocol/master/images/avatar/3.png) | `385` | ![Avatar4](https://raw.githubusercontent.com/capasha/BlockWorksProtocol/master/images/avatar/4.png) | `513` | ![Avatar5](https://raw.githubusercontent.com/capasha/BlockWorksProtocol/master/images/avatar/5.png) | `641` | ![Avatar6]
| ![AvatarYellow](https://raw.githubusercontent.com/capasha/BlockWorksProtocol/master/images/avatar/yellow.png) | ![Avatar0](https://raw.githubusercontent.com/capasha/BlockWorksProtocol/master/images/avatar/0.png) | `2` | ![Avatar1](https://raw.githubusercontent.com/capasha/BlockWorksProtocol/master/images/avatar/1.png) | `130` | ![Avatar2](https://raw.githubusercontent.com/capasha/BlockWorksProtocol/master/images/avatar/2.png) | `258` | ![Avatar3](https://raw.githubusercontent.com/capasha/BlockWorksProtocol/master/images/avatar/3.png) | `386` | ![Avatar4](https://raw.githubusercontent.com/capasha/BlockWorksProtocol/master/images/avatar/4.png) | `514` | ![Avatar5](https://raw.githubusercontent.com/capasha/BlockWorksProtocol/master/images/avatar/5.png) | `642` | ![Avatar6]
| ![AvatarGreen](https://raw.githubusercontent.com/capasha/BlockWorksProtocol/master/images/avatar/green.png) | ![Avatar0](https://raw.githubusercontent.com/capasha/BlockWorksProtocol/master/images/avatar/0.png) | `3` | ![Avatar1](https://raw.githubusercontent.com/capasha/BlockWorksProtocol/master/images/avatar/1.png) | `131` | ![Avatar2](https://raw.githubusercontent.com/capasha/BlockWorksProtocol/master/images/avatar/2.png) | `259` | ![Avatar3](https://raw.githubusercontent.com/capasha/BlockWorksProtocol/master/images/avatar/3.png) | `387` | ![Avatar4](https://raw.githubusercontent.com/capasha/BlockWorksProtocol/master/images/avatar/4.png) | `515` | ![Avatar5](https://raw.githubusercontent.com/capasha/BlockWorksProtocol/master/images/avatar/5.png) | `643` | ![Avatar6]
| ![AvatarCyan](https://raw.githubusercontent.com/capasha/BlockWorksProtocol/master/images/avatar/cyan.png) | ![Avatar0](https://raw.githubusercontent.com/capasha/BlockWorksProtocol/master/images/avatar/0.png) | `4` | ![Avatar1](https://raw.githubusercontent.com/capasha/BlockWorksProtocol/master/images/avatar/1.png) | `132` | ![Avatar2](https://raw.githubusercontent.com/capasha/BlockWorksProtocol/master/images/avatar/2.png) | `260` | ![Avatar3](https://raw.githubusercontent.com/capasha/BlockWorksProtocol/master/images/avatar/3.png) | `388` | ![Avatar4](https://raw.githubusercontent.com/capasha/BlockWorksProtocol/master/images/avatar/4.png) | `516` | ![Avatar5](https://raw.githubusercontent.com/capasha/BlockWorksProtocol/master/images/avatar/5.png) | `644` | ![Avatar6]
| ![AvatarBlue](https://raw.githubusercontent.com/capasha/BlockWorksProtocol/master/images/avatar/blue.png) | ![Avatar0](https://raw.githubusercontent.com/capasha/BlockWorksProtocol/master/images/avatar/0.png) | `6` | ![Avatar1](https://raw.githubusercontent.com/capasha/BlockWorksProtocol/master/images/avatar/1.png) | `133` | ![Avatar2](https://raw.githubusercontent.com/capasha/BlockWorksProtocol/master/images/avatar/2.png) | `261` | ![Avatar3](https://raw.githubusercontent.com/capasha/BlockWorksProtocol/master/images/avatar/3.png) | `389` | ![Avatar4](https://raw.githubusercontent.com/capasha/BlockWorksProtocol/master/images/avatar/4.png) | `517` | ![Avatar5](https://raw.githubusercontent.com/capasha/BlockWorksProtocol/master/images/avatar/5.png) | `645` | ![Avatar6]
| ![AvatarPurple](https://raw.githubusercontent.com/capasha/BlockWorksProtocol/master/images/avatar/purple.png) | ![Avatar0](https://raw.githubusercontent.com/capasha/BlockWorksProtocol/master/images/avatar/0.png) | `7` | ![Avatar1](https://raw.githubusercontent.com/capasha/BlockWorksProtocol/master/images/avatar/1.png) | `134` | ![Avatar2](https://raw.githubusercontent.com/capasha/BlockWorksProtocol/master/images/avatar/2.png) | `262` | ![Avatar3](https://raw.githubusercontent.com/capasha/BlockWorksProtocol/master/images/avatar/3.png) | `390` | ![Avatar4](https://raw.githubusercontent.com/capasha/BlockWorksProtocol/master/images/avatar/4.png) | `518` | ![Avatar5](https://raw.githubusercontent.com/capasha/BlockWorksProtocol/master/images/avatar/5.png) | `646` | ![Avatar6]

