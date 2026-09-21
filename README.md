# Variant Announcements 1.1.2

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
- **Milestones:** announce new boss or progression milestones.

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

Use 1.1.2 on the server and the admin's PC. Regular players and crossplay players do not need this mod. Messages use Valheim's normal HUD; keep crossplay enabled on your server.

## World Advancement Progression

If WAP is installed on the server, new private-key progress can trigger milestone messages. Announcements does not unlock anything or change WAP settings.
Loading a character's existing keys does not replay their achievements. Choose the first new completion for the world, or each player's first completion.
Without WAP, milestones follow the world's global keys.

Visits and milestone history are saved separately for each world in the mod's `history` JSON file beside your settings. Keep that file to avoid treating returning players as new visitors.

## Permissions

The source code is private. You can use the mod in your game and on your server.
Ask before reusing the code or republishing the mod. See `LICENSE.txt` for details.
