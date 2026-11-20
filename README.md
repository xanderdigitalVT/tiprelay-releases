<p align="center"><img src="logo.png" alt="TipRelay logo" width="200"></p>

# tiprelay-releases
Installers and updates for TipRelay

TipRelay turns stream events (tips, subs, follows, chat) into actions: VRChat, Warudo or
VTube Studio avatar changes, OBS scene changes, on-stream alerts and goals, and Discord
messages. It runs on your own PC, and your sign-ins stay on your PC, encrypted.
A few sites, like TipeeeStream, still come through Streamer.bot.

**[Download the latest version](https://github.com/xanderdigitalVT/tiprelay-releases/releases/latest)**

## What it does

**Events come in from:**

- **Twitch:** follows, subs, resubs, gift subs, bits, Power-ups, Hype Trains, raids, channel-point redemptions and chat
- **Kick:** chat, follows, subs, gifted subs, KICKs and reward redemptions, through your own free relay on Cloudflare
- **YouTube:** chat, Super Chats, Super Stickers, new members, milestones and gifted memberships, read from your public live page like a signed-out viewer. No sign-in, and it never posts. Streamer.bot works as a backup.
- **TikTok:** chat, gifts, follows and subscriptions, read from your public LIVE page the same way
- **Fansly:** tips, subs and chat, read from Fansly's own page in a window. This connection is unofficial and only reads, so TipRelay sends nothing to your chat.
- **Joystick.TV:** tips with tip-menu items, follows, subs, resubs, gift subs and chat
- **Ko-fi, Fourthwall and Throne:** tips, orders, memberships and wishlist gifts, through your relay. Each post is checked, so fakes don't count.
- **StreamElements and Streamlabs:** tips and donations, with amount and currency
- **Streamer.bot:** TipeeeStream and other sites it connects to, plus Fansly and YouTube as a backup. An event that comes through both only counts once.
- **OBS and VRChat:** OBS going live, recording, scene changes and mutes, and (if you turn it on) your VRChat avatar's toggles and contacts can trigger rules too

**Actions go out to:**

- **Your avatar:** VRChat through OSC, Warudo through its WebSocket, or VTube Studio through its plugin API. Each avatar app keeps its own rules, goals and tip menus, and you switch between them on the Home page.
- **OBS:** switch scenes, show or hide sources and set text, plus a control page for going live, recording, the replay buffer, the virtual camera, volumes, filters and hotkeys
- **Overlays:** alerts, goals, wheels, a D20, a tip menu, counters, timers, a Now playing song widget and your own HTML overlays as OBS Browser sources, with one combined overlay for NSFW sites and one for SFW sites
- **Chat and Discord:** messages to Twitch, Kick and Joystick.TV chat, and Discord webhook posts. Mentions are disabled, so viewer text can't ping `@everyone`.
- **In VR and the web:** notifications through XSOverlay or OVR Toolkit, and HTTP requests to other tools

**Features:**

- **Home:** quick connect, your avatar app, a live stream card, recent activity, and the Hide NSFW sites and Keep TipRelay running switches
- **Rules:** a trigger, then a list of actions, with cooldowns and a queue so alerts don't overlap. A rule can watch several sites, be limited to certain viewers, or send the event's amount (bits, tip, months) to an avatar parameter. Chat rules can be limited to mods and a list of names.
- **Goals:** chained goals that count one running total, so the next goal continues from where the last one finished
- **Chance Games:** wheels and a D20 with sounds, driven by tips and chat commands. Number ranges on the D20 fire your rules.
- **Now playing:** the song from Spotify or any player Windows knows about, with album art, in five styles
- **Timers:** a clock, stream uptime and subathon countdowns that tips, subs and bits add time to
- **Tip menus:** keep a menu for each currency or site and swap which one is in use. A menu can count in money, Joystick.TV tokens, Twitch bits, Kick KICKs or subs, and it only matches tips in its own unit.
- **Chat, Activity feed, Viewers and Stats:** every site's chat in one list, events by site with replay and search, notes on viewers, and stream recaps with optional posting to Discord
- **Stream titles:** change your title on Twitch, Kick and Joystick.TV at once, and keep a list of saved titles
- **Hide NSFW sites:** hides Fansly and Joystick.TV across the app, for when your screen is on stream. What shows in OBS doesn't change.
- **Test events:** fire any event by hand, without going live
- **Backups:** export and restore your settings and rules
- **Automatic updates:** new versions download in the background, and TipRelay never restarts by itself. The version number and a **Check for updates** button are at the bottom of the sidebar.

Your settings are kept in `%APPDATA%\TipRelay\config.json`. Sign-ins and tokens are encrypted with Windows DPAPI in `secrets.bin` in the same folder. The Fansly sign-in is kept in the Fansly window's own storage on your PC.

## Install

1. Download `TipRelay-<version>.zip` from the [latest release](https://github.com/xanderdigitalVT/tiprelay-releases/releases/latest) and extract it.
2. Run `TipRelay-Setup-<version>.exe`. If Windows says "Windows protected your PC," click **More info**, then **Run anyway**. This appears because the app isn't code-signed.
3. Follow the installer. TipRelay then appears in your Start menu.

## Connecting your accounts

Set up only what you use. Each row on the Connections page opens its own settings and instructions.

- **Twitch:** create an app at https://dev.twitch.tv/console/apps with client type **Public** and redirect URL `http://localhost`, then paste its Client ID and click **Connect Twitch**. If your app is Confidential, paste its client secret too, or Twitch signs you out every few hours.
- **Kick:** set up your own relay by following `relay\SETUP.txt` in the zip, which takes about 20 minutes and is free. To use Stream titles and send chat messages, turn on channel write and chat write access in your Kick app.
- **YouTube and TikTok:** type your handle or username and turn it on. If the site asks to confirm you're a person, TipRelay stops and says so.
- **Fansly:** on Fansly, open **Management Sessions**, click **Create Session**, name it TipRelay, leave its permissions off and copy its link. Paste the link and your chat URL on the Fansly settings and click **Open Fansly**. The link works once, and TipRelay keeps the session until you click **Sign out**. Keep the Fansly window open while you stream; you can minimize it.
- **Joystick.TV:** create a bot application on joystick.tv with redirect URL `http://127.0.0.1/callback`, then paste its Client ID and click **Connect Joystick.TV**. A public app stays signed in for 4 hours at a time, and a confidential app with its client secret lasts 10 days.
- **Ko-fi, Fourthwall and Throne:** set up the relay (part 1 of `relay\SETUP.txt` in the zip), then paste the address from each site's settings into that site and save its token, secret or username.
- **StreamElements or Streamlabs:** paste your StreamElements JWT token or Streamlabs Socket API token and click **Connect**.
- **Streamer.bot:** connect the site in Streamer.bot first, then follow the steps in TipRelay's Streamer.bot settings, which give you a script to copy in.
- **OBS:** in OBS, go to **Tools → WebSocket Server Settings** and turn it on, then copy the port and password to TipRelay's OBS settings.
- **VRChat:** open the Action Menu, go to **Options → OSC** and turn on **Enabled**.
- **Warudo:** choose Warudo as your avatar app, then add an **On WebSocket Action** node to a blueprint for each action name your rules send.
- **VTube Studio:** choose VTube Studio as your avatar app, turn on **Start API** in VTube Studio's settings, then click **Allow** the first time TipRelay connects.
- **Discord:** in a channel's settings, go to **Integrations → Webhooks → New Webhook** and copy the webhook URL. Save it on the Connections page under a name you'll recognize.

Then add a rule on the **Rules** page, try it from **Test & activity**, and add your overlay address to OBS as a Browser source.
