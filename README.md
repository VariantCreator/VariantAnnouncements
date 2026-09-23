# Variant Announcements 1.1.3

Send scheduled messages, welcome new players and remind everyone about upcoming restarts. Choose your message text, colour, size and screen position from an in-game menu.

[Download the latest version](https://github.com/VariantCreator/VariantAnnouncements/releases/latest)

## Install

1. Install the mod on your server. For a manual install, put `VariantAnnouncements.dll` in `BepInEx/plugins/VariantAnnouncements/`.
2. Install it and Config Manager on your PC if you want to use the admin menu. Other players do not need them.
3. Restart, join your world and open Config Manager. Under **Variant Announcements**, click **Open admin editor**.

ServerSync is included. Only the host and players listed in the server's `adminlist.txt` can save changes.

## Use the menu

Click **Reload from server**, edit your messages, then **Save to server**. Your changes apply to everyone's announcements.
Click a message to edit it. **Test this privately** sends that message only to you.
**Send this now** sends your draft to everyone online. **Undo last save** restores the previous server settings.

The editor opens through Config Manager. It has no keyboard shortcut.
Your movement and attacks are blocked while the menu is open. The world keeps running.

## Message types

- **General:** choose the server name, time zone, prefix, position, color and text size.
- **Upcoming:** see what is coming next and select a message to edit it.
- **Daily:** choose a time and the days of the week.
- **Repeating:** send messages at regular intervals.
- **Welcome:** give new visitors an introduction and rules, with a shorter greeting when they return.
- **Restarts:** send reminders before a planned restart. This does not restart the server.
- **Maintenance / Events:** choose a date, time and countdown warnings. They stop afterward. Turn a rule off and save to cancel it. Older recurring maintenance notices stay available.
- **Tips:** shuffle messages by category without repeating a tip until the others have been used.
- **Milestones:** announce boss kills and new progression milestones.

Each message can use its own color, size and position. Presets make warnings, events and tips easy to style.
Quiet hours silence tips and normal notices. Important and urgent messages still get through.
Urgent messages go first, and messages are spaced out for each player.

Use `{player}`, `{server}` or `{time}` in your text. Countdowns support `{minutes}` and events support `{event}`. Milestones support `{actor}` and `{milestone}`.
Use `<b>bold</b>`, `<color=#FFAA00>orange</color>` or `<size=30>larger text</size>` in messages.

## Time zone

Enter **-4** for UTC-4, **+11** for UTC+11, or **0** for UTC.
These stay fixed all year. Use a name such as **America/New_York** if you want daylight saving changes.

## Settings and updates

Your messages are saved in `BepInEx/config/com.variantmods.announcements.messages.json`, with a backup of the previous save.
Old ScheduledMessages settings are imported on first use if you do not already have a settings file.

To update, close Valheim and stop the server, replace the DLL on both, then start them again. Keep your config files and only one copy of the mod in each plugins folder.

Use 1.1.3 on the server and the admin's PC. Regular players and crossplay players do not need this mod. Messages use Valheim's normal HUD; keep crossplay enabled on your server.

## Boss kills

Boss announcements are on by default, including repeat kills. Change them under **Milestones → Boss kills**.
The default text is **{player} defeated {boss}!** For example: **Dova defeated Eikthyr!**

Co-op kills list the fighters credited by the game together. This is shared kill credit, not a claim about who landed the final hit.
The server needs the boss's death and player-credit data. A missing death update, an admin removal or a death with no credited player is skipped.
Boss first-unlock messages are skipped while boss-kill announcements are enabled, so one defeat does not send both.

## Vanilla and crossplay servers

Install BepInEx and Announcements on the server. Players can join with unmodded clients, including crossplay.
WAP, Config Manager and the Announcements client are not required for delivery.

Without WAP, vanilla mode is automatic: boss notices use the game's death data and progression milestones use world keys.
Schedules, welcomes, tips, events and restart reminders work the same way.
With no admin client, edit `BepInEx/config/com.variantmods.announcements.messages.json` on the server. Settings reload while it is running.
The `BossKills` section controls the message, style and whether boss notices are enabled.

## World Advancement Progression

If WAP is installed on the server, new private-key progress can trigger milestone messages. Announcements does not unlock anything or change WAP settings.
Loading a character's existing keys does not replay their achievements. Choose the first new completion for the world, or each player's first completion.
Without WAP, milestones follow the world's global keys.
Boss kills use the same native death tracking with or without WAP. Repeat kills do not need another progression unlock.

Visits and milestone history are saved separately for each world in the mod's `history` JSON file beside your settings. Keep that file to avoid treating returning players as new visitors.

## Odin Hates Litter

Under **Events → Odin Hates Litter**, turn on start notices, completion notices, or both. They are off by default.
Each has its own text, colour, size and position.

- **{player} started {event}!**
- **{player} completed {event}!**

Here, `{player}` means the event starter. Cleanup, wave, boss and Ocean events use the name supplied by Odin Hates Litter.
Completion means the event succeeded, including when rewards are switched off. Cancelling, failing or restoring an event does not create a false victory or another start notice.

Use the Odin Hates Litter update that includes announcement events. The menu shows whether the server has support.
If Odin Hates Litter is missing or too old, these notices stay inactive and other announcements keep working.
Odin Hates Litter's own install requirements still apply; this option does not make that mod server-only.

## Permissions

The source code is private. You can use the mod in your game and on your server.
Ask before reusing the code or republishing the mod. See `LICENSE.txt` for details.
