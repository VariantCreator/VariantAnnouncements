# Variant Announcements

Send scheduled messages, welcome players, announce boss kills and warn everyone before a restart.

Install it on the server. Players see messages in Valheim's normal HUD without installing the mod, including vanilla and crossplay players. Admins can install it on their PC to edit messages in game.

**[Download VariantAnnouncements.zip](https://github.com/VariantCreator/VariantAnnouncements/releases/latest/download/VariantAnnouncements.zip)**

## Install

1. Install BepInEx for Valheim on the server.
2. Put `VariantAnnouncements.dll` in `BepInEx/plugins/VariantAnnouncements/`.
3. Restart the server.

Keep crossplay enabled on the server if console players will be joining.

ServerSync is included. World Advancement Progression (WAP) and Odin Hates Litter are optional.

## Change messages

### In-game editor

Install the same version of Announcements and Config Manager on your PC. Join the server, open Config Manager, then choose **Variant Announcements → Open admin editor**.

Only the host and players in the server's `adminlist.txt` can save changes. Saved settings apply to everyone.

- **Reload from server:** discard your edits and load the saved settings.
- **Save to server:** save your changes.
- **Test this privately:** preview a message just for you.
- **Send this now:** send a message to everyone online.
- **Undo last save:** bring back the previous settings.

The menu blocks movement and attacks while open. The world keeps running.

### Server config file

You can also edit this file after the server's first start:

`BepInEx/config/com.variantmods.announcements.messages.json`

Valid changes reload when saved. A backup of the previous settings is kept beside the file.

## Messages

- Daily messages and repeating reminders.
- Separate welcomes for new and returning players.
- Restart, maintenance and event countdowns. These are reminders; the mod does not restart the server.
- Rotating tips that show each message before repeating.
- Boss kills and progression milestones.
- An **Upcoming** tab to see which messages are next.

Choose the text, color, size and position for each message. Use quiet hours to silence routine messages while keeping important warnings.

## Boss kills

Boss notices are on by default and include repeat kills. Change them under **Milestones → Boss kills**.

Default message: **{player} defeated {boss}!**

When players fight together, the notice names the fighters credited by the game. Matching progression notices are skipped so one kill does not send two messages.

The server needs the game's death and player-credit data to send a notice. Bosses removed by an admin or killed without a credited player are skipped.

## World Advancement Progression

With WAP installed, milestones can follow each player's progress. Choose the first completion in the world or each player's first completion. Joining with existing progress does not replay old milestones.

Without WAP, milestones use vanilla world progress automatically. Boss kills are announced separately from progression unlocks.

## Odin Hates Litter

With Odin Hates Litter 1.5.3 or later, announce when a player starts an event and when it is completed:

- **{player} started {event}!**
- **{player} completed {event}!**

Turn these on under **Events → Odin Hates Litter**. Start and completion notices have separate text and style settings. Both are off by default.

`{player}` is the player who started it. `{event}` is the event or bin name. Successful events send a completion notice even with rewards off. Cancelled or failed events do not.

Follow Odin Hates Litter's installation instructions too.

## Message placeholders

Use `{player}`, `{server}` and `{time}` in messages. Boss notices also use `{boss}`, countdowns use `{minutes}`, events use `{event}`, and progression notices use `{actor}` and `{milestone}`.

For formatting, use `<b>bold</b>`, `<color=#FFAA00>color</color>` or `<size=30>text size</size>`.

## Time zone

Enter **-4**, **+11** or **0** for a fixed UTC offset. Use **America/New_York** to follow daylight saving changes.

Enter times in 24-hour format: **05:00, 15:00** means 5 AM and 3 PM.

## Updating

Stop the server and close Valheim before replacing the DLL. Use the same version on the server and any admin PCs. Keep only one copy of `VariantAnnouncements.dll` in each installation.

Keep your config and history files to save messages, player visits and milestone history. Old ScheduledMessages settings are imported on first use if no Announcements settings exist.

## License

Free to install and use. See [LICENSE.txt](https://github.com/VariantCreator/VariantAnnouncements/blob/main/LICENSE.txt) for the full terms.
