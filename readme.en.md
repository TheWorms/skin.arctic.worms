<!-- logo:start -->
<p align="center"><img src="icon.png" alt="Logo" width="160"></p>
<!-- logo:end -->

[Français](README.md) · **English**

# Arctic: Worms

<!-- version:auto -->
**Version : 1.0.3**
<!-- /version:auto -->

Kodi skin derived from **Arctic: Zephyr - Reloaded** (beatmasterRS, after
jurialmunkey's Arctic: Zephyr), tuned for the add-ons of the **TheWorms**
repository: fonts and colours expected by add-on windows, built-in ProtonVPN
widget, Wtube instead of YouTube, and the real `/storage` disk usage on CoreELEC.

Built for **Kodi 21 "Omega"**; works on every Kodi platform.

- **Repository**: `github.com/TheWorms/skin.arctic.worms`
- **Kodi id**: `skin.arctic.worms`
- **Display name**: Arctic: Worms · **License**: CC BY-NC-SA 3.0

---

## What changes compared to Arctic: Zephyr - Reloaded 3.0.3

- **Add-on windows**: the skin provides Estuary's font names (`font10`, `font12`,
  `font14`, `font27`, `fontNN_title`, `Mono26`…) and colour names
  (`button_focus`…), plus the `colors/white.png` & co textures. Without them,
  add-on texts all fell back to the same size and some bars were invisible.
- **ProtonVPN widget**: built into the home screen (`service.protonvpn.manager`).
  It only shows when the add-on is enabled, and a skin update no longer removes it.
- **Wtube**: the "YouTube" lists of the info dialogs (movie, show, artist, person)
  and the list layout use `plugin.video.wtube` when it is installed.
- **Disk usage**: with `service.worms.diskinfo`, the **Storage** tile of the system
  info shows the data partition (`/storage`) instead of the read-only system image,
  which is always 100 % full. Without the service, the skin keeps Kodi's value.
- **Weather**: icons of days 8 to 10 fixed, no more empty "Feels like".
- **Fixes**: colour picker, numeric dialog, misnamed textures, stale window names,
  fonts missing in two font sets, titles with commas or quotes passed safely to
  scripts, eMMC/NAND reboot visible on CoreELEC.

Full details: `changelog.txt`.

## Supported add-ons from the repository

| Add-on | Integration |
|---|---|
| `service.protonvpn.manager` | "Tunnel status" home widget |
| `plugin.video.wtube` | YouTube lists of the info dialogs, list view |
| `plugin.video.embycon` | forced views (`Skin.ForcedView.*`) |
| `weather.meteoconcept` | home weather, hourly and daily forecasts |
| `plugin.audio.radio`, `plugin.audio.soundcloud` | full-screen windows using the skin fonts |
| `service.worms.diskinfo` | `/storage` disk usage |

## Install

### Via the TheWorms repository (recommended, auto-updates)

1. Install the repository:
   `https://raw.githubusercontent.com/TheWorms/kodi-repo/main/zips/repository.theworms/repository.theworms.zip`
2. Add-ons → **Install from repository** → *TheWorms Repository* → *Look and feel*
   → *Skin* → **Arctic: Worms** → Install, then accept switching to this skin.
3. Optional: *Services* → **Disk Info**, for the `/storage` disk usage.

Dependencies (`script.skinshortcuts`, `script.embuary.helper`,
`plugin.video.themoviedb.helper`…) are installed automatically from the official
Kodi repository.

### Manual (zip)

1. Get `skin.arctic.worms-x.y.z.zip`.
2. System → Add-ons → enable **Unknown sources**.
3. Add-ons → **Install from zip file**.

## Keeping your Arctic: Zephyr - Reloaded settings

The skin has a new id, so its settings and menus are stored separately. To carry
over those of `skin.arctic.zephyr.mod`, over SSH on the box, **with Kodi stopped**
and **before** switching to Arctic: Worms:

```bash
systemctl stop kodi
U=/storage/.kodi/userdata
cp -a $U/addon_data/skin.arctic.zephyr.mod $U/addon_data/skin.arctic.worms
cp $U/addon_data/script.skinshortcuts/skin.arctic.zephyr.mod.properties \
   $U/addon_data/script.skinshortcuts/skin.arctic.worms.properties
systemctl start kodi
```

The main menu (`mainmenu.DATA.xml`) is shared by both skins. On first start,
skinshortcuts rebuilds the menus and the skin reloads once.

## Troubleshooting

- **Kodi falls back to Estuary at startup** ("Failed to load skin" in the log):
  the skin is not installed or not enabled. Install it from the repository or the
  zip rather than copying the folder by hand: Kodi 21 disables add-ons copied
  by hand.
- **The Storage tile shows 100 %**: `service.worms.diskinfo` is not installed or is
  disabled.
- **ProtonVPN's "Install widget" button rejects this skin**: expected, the widget
  is already built in.

## Credits and license

- Original **Arctic: Zephyr** skin: jurialmunkey.
- **Arctic: Zephyr - Reloaded**: beatmasterRS and contributors
  (`github.com/beatmasterRS/skin.arctic.zephyr.mod`).
- Icons: iconmonstr.com (see their license terms); additional icons from
  metroicon.net courtesy of Piers.

This work is licensed under the Creative Commons Attribution-NonCommercial-ShareAlike
3.0 Unported License (CC BY-NC-SA 3.0): http://creativecommons.org/licenses/by-nc-sa/3.0/
— see `LICENSE.txt`.
