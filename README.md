# Variant Announcements

Scheduled messages, boss kill notices, welcomes and restart reminders for Valheim servers.

Players see announcements in Valheim's normal HUD without installing this mod. Server admins can use an optional in-game editor to change messages for everyone.

**[Download Variant Announcements](https://github.com/VariantCreator/VariantAnnouncements/releases/latest)** — choose `VariantAnnouncements.zip` from the release assets.

## Install

1. Install BepInEx for Valheim on the server.
2. Extract `VariantAnnouncements.dll` into `BepInEx/plugins/VariantAnnouncements/`.
3. Restart the server.

Regular players do not need Announcements or Config Manager. Vanilla clients and crossplay players receive the same messages. Keep crossplay enabled in the server settings if console players will be joining.

ServerSync is included. World Advancement Progression and Odin Hates Litter are optional.

## Set up messages

### In-game editor

Install the same version of Announcements and a compatible Config Manager on the admin's PC. Join the server, open Config Manager, and select **Variant Announcements → Open admin editor**.

Only the host and players in the server's `adminlist.txt` can save changes.

- **Reload from server:** load the saved settings.
- **Save to server:** apply changes to everyone's announcements.
- **Test this privately:** preview a message only for the admin using the editor.
- **Send this now:** send the selected message to everyone online.
- **Undo last save:** restore the previous settings.

The menu blocks movement and attacks while open. The world keeps running.

### Server config file

The server can run without an admin client. Edit this file after the first start:

`BepInEx/config/com.variantmods.announcements.messages.json`

Valid changes reload while the server is running. A backup of the previous save is kept beside the file.

## Message options

- **Daily and repeating:** send messages on selected weekdays or at regular intervals.
- **Welcome:** greet new visitors with rules or an introduction, and returning players with a shorter message.
- **Restarts:** send countdown warnings for planned restarts. The mod does not restart the server.
- **Maintenance and events:** schedule a date, time and countdown warnings.
- **Tips:** rotate through messages without repeating one until the others have been used.
- **Milestones:** announce boss kills and progression milestones.
- **Upcoming:** check the next scheduled messages.

Each message can have its own color, size and screen position. Quiet hours silence routine notices while important warnings still get through.

## Boss announcements

Boss notices are enabled by default, including repeat kills. Change the text and style under **Milestones → Boss kills**.

Default message: **{player} defeated {boss}!**

Co-op notices name the fighters credited by the game together. Boss-kill notices replace matching first-unlock notices to avoid sending both for one defeat.

The server must receive the boss's death and player-credit data. Admin removals, deaths without a credited player and missing death updates are skipped.

## World Advancement Progression

WAP private progress can trigger milestone messages. Choose the first completion in the world or each player's first completion. Existing character progress is not announced again when loading in.

Without WAP, progression milestones use vanilla world progress automatically. Boss-kill notices work independently of progression unlocks.

## Odin Hates Litter

Announce when a player starts an Odin Hates Litter event and when the event is completed successfully.

- **{player} started {event}!**
- **{player} completed {event}!**

Enable either or both under **Events → Odin Hates Litter**. Each notice has its own text, color, size and position. They are off by default.

`{player}` is the event starter, and `{event}` is the event or bin name. Successful events can be announced even with rewards turned off. Cancelled and failed events do not send a completion notice.

Odin Hates Litter's own installation requirements still apply.

## Message placeholders

Use `{player}`, `{server}` and `{time}` in message text. Boss notices support `{boss}`, countdowns support `{minutes}`, and events support `{event}`. Progression messages support `{actor}` and `{milestone}`.

Messages also support `<b>bold</b>`, `<color=#FFAA00>color</color>` and `<size=30>text size</size>`.

## Time zone

Use **-4** for UTC-4, **+11** for UTC+11, or **0** for UTC. These offsets stay fixed all year.

Use a name such as **America/New_York** to follow daylight saving changes. Enter restart times in 24-hour format, such as **05:00, 15:00**.

## Updating

Stop the server and close Valheim before replacing the DLL. Update the server and any optional admin clients to the same version. Keep only one copy of `VariantAnnouncements.dll` in each installation.

Keep the config and history files to preserve messages, returning-player records and progression history. Existing ScheduledMessages settings are imported on first use when no Announcements settings file exists.

## License

Free to install and use in games and on servers. See [LICENSE.txt](LICENSE.txt) for modification and redistribution terms.
