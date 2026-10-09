# Variant Announcements

Send scheduled messages, welcome players, announce boss summons and kills, and warn everyone before a restart.

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

The editor uses wood panels, bronze trim and a left menu with five sections:

- **Overview:** upcoming notices and recent message history.
- **Messages:** welcomes, daily messages, repeating reminders and tips.
- **Schedules:** restarts, one-time or weekly maintenance, and dated events.
- **World events:** boss summons and kills, progression milestones and Odin Hates Litter.
- **Settings:** server details, default appearance and quiet hours.

Use **Find messages** to search across sections. Click a message to expand or collapse it. Appearance controls stay tucked away until you need them. Unsaved changes are marked above the save button.

- **Reload from server:** discard your edits and load the saved settings.
- **Save to server:** save your changes.
- **Test selected privately:** preview a message just for you.
- **Send selected now:** send a message to everyone online.
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
- An **Upcoming** tab showing server time, time zone and which notices would be skipped by quiet hours or player limits.

Choose the text, color, size and position for each message. Use quiet hours to silence routine messages while keeping important warnings.

Set **Minimum players online** on a message to send it only when enough players are online. Use **0** for any player count. Skipped notices are not held for later; repeating messages try again at their next interval.

**Overview → History** shows recent sends and skips from the current server session. It includes the recipient and reasons such as quiet hours, player limits or an expired message. Sent means the server handed the message to Valheim; it is not a receipt from the player's screen.

### Restart catch-up

Players joining near a restart get a personal warning with the time remaining. This is on by default within the last **15 minutes**, limited by your configured warning times. Change it under **Schedules → Restarts**. Joining at the same time as a scheduled warning does not send both.

## Maintenance

Open **Schedules → Maintenance** and choose **One-time**, **Weekly** or **Existing notices**.

- Schedule maintenance in 15 minutes, 30 minutes or an hour, or choose a date and time.
- Use weekly schedules for selected weekdays, with a start date and countdown warnings.
- Pick a countdown preset or enter your own warning minutes.
- See the next maintenance time and next notice in the server's time zone.
- Cancel or move a schedule, then **Save to server**.

Existing maintenance messages stay available under **Existing notices**. These settings send reminders; your server host handles the actual shutdown or restart.

## Tip presets

Open **Messages → Tips → Browse tip presets**. Choose **Vanilla basics**, **Variant regular** or **Variant HUGE** and preview the categories before importing.

The regular and HUGE tips cover your packs' progression, portals, resurrection, storage, gear and building. HUGE also includes its expanded world and winter rules. Review them against your server settings before enabling them.

**Add missing preset tips** keeps your messages and skips duplicates. New categories start paused. Enable the categories you want, choose their intervals, then save.

## Boss notices

Change these under **World events → Bosses**. Summon and kill notices are on by default:

- **{player} summoned {boss}!**
- **{player} defeated {boss}!**

Summon notices name the player whose altar offering was accepted. Failed offerings do not send a notice. Kill notices include repeat kills.

When players fight together, the notice names the fighters credited by the game. Matching progression notices are skipped so one kill does not send two messages.

The server needs the game's death and player-credit data to send a notice. Bosses removed by an admin or killed without a credited player are skipped.

Boss totals are optional and off by default. Under **World events → Bosses**, enable **Announce boss total** and choose an interval, such as every 10 defeats of each boss.

Default message: **{boss} has been defeated {count} times!**

Counts are saved per world. Existing totals carry over. Earlier kills are not guessed from WAP or world progress.

**Replace Valheim's boss summon and defeat notices** replaces the native broadcast with your message. Unrelated HUD messages still work. If the server cannot identify a successful summon or credited death, the native notice is kept.

A vanilla player simulating the boss can briefly see Valheim's local notice before the server receives it. Installing Announcements on that player's PC allows the local notice to be replaced too. Other players can keep using the server-only setup.

## World Advancement Progression

With WAP installed, milestones can follow each player's progress. Choose the first completion in the world or each player's first completion. Joining with existing progress does not replay old milestones.

Without WAP, milestones use vanilla world progress automatically. Boss kills are announced separately from progression unlocks.

## Odin Hates Litter

With Odin Hates Litter 1.5.3 or later, announce when a player starts an event and when it is completed:

- **{player} started {event}!**
- **{player} completed {event}!**

Turn these on under **World events → Odin Hates Litter**. Start and completion notices have separate text and style settings. Both are off by default.

`{player}` is the player who started it. `{event}` is the event or bin name. Successful events send a completion notice even with rewards off. Cancelled or failed events do not.

Follow Odin Hates Litter's installation instructions too.

## Message placeholders

Use `{player}`, `{server}` and `{time}` in messages. Boss notices also use `{boss}` and `{count}`, countdowns use `{minutes}`, events use `{event}`, and progression notices use `{actor}` and `{milestone}`.

For formatting, use `<b>bold</b>`, `<color=#FFAA00>color</color>` or `<size=30>text size</size>`.

## Time zone

Enter **-4**, **+11** or **0** for a fixed UTC offset. Use **America/New_York** to follow daylight saving changes.

Enter times in 24-hour format: **05:00, 15:00** means 5 AM and 3 PM.

## Updating

Stop the server and close Valheim before replacing the DLL. Update the server and any admin PCs to **1.3.0** together. Older admin editors cannot edit the new settings. Keep only one copy of `VariantAnnouncements.dll` in each installation.

Keep your config and history files to save messages, player visits and milestone history. Old ScheduledMessages settings are imported on first use if no Announcements settings exist.

## License

Free to install and use. See [LICENSE.txt](https://github.com/VariantCreator/VariantAnnouncements/blob/main/LICENSE.txt) for the full terms.
