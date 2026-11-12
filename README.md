<!-- logo:start -->
<p align="center"><img src="icon.png" alt="Logo" width="160"></p>
<!-- logo:end -->

**Français** · [English](readme.en.md)

# Arctic: Worms

<!-- version:auto -->
**Version : 1.0.2**
<!-- /version:auto -->

Skin Kodi dérivé d'**Arctic: Zephyr - Reloaded** (beatmasterRS, d'après l'Arctic:
Zephyr de jurialmunkey), adapté aux addons du dépôt **TheWorms** : polices et
couleurs attendues par les fenêtres d'addons, widget ProtonVPN intégré, Wtube à la
place de YouTube, et espace disque réel de `/storage` sur CoreELEC.

Conçu pour **Kodi 21 « Omega »** ; fonctionne sur toutes les plateformes Kodi.

- **Dépôt** : `github.com/TheWorms/skin.arctic.worms`
- **Identifiant Kodi** : `skin.arctic.worms`
- **Nom affiché** : Arctic: Worms · **Licence** : CC BY-NC-SA 3.0

---

## Ce qui change par rapport à Arctic: Zephyr - Reloaded 3.0.3

- **Fenêtres d'addons** : le skin fournit les noms de polices (`font10`, `font12`,
  `font14`, `font27`, `fontNN_title`, `Mono26`…) et de couleurs (`button_focus`…)
  d'Estuary, ainsi que les textures `colors/white.png` & co. Sans eux, les textes
  des addons retombaient tous sur la même taille et certaines barres étaient
  invisibles.
- **Widget ProtonVPN** : intégré à l'accueil (`service.protonvpn.manager`). Il
  n'apparaît que si l'addon est activé, et une mise à jour du skin ne l'efface plus.
- **Wtube** : les listes « YouTube » des fiches (film, série, artiste, personne) et
  la mise en page liste passent par `plugin.video.wtube` quand il est installé.
- **Espace disque** : avec `service.worms.diskinfo`, la tuile **Stockage** des infos
  système affiche la partition de données (`/storage`) au lieu de l'image système
  en lecture seule, toujours à 100 %. Sans le service, le skin garde la valeur de
  Kodi.
- **Météo** : icônes des jours 8 à 10 corrigées, plus de « Ressenti » vide.
- **Corrections** : sélecteur de couleur, dialogue numérique, textures mal nommées,
  noms de fenêtres périmés, polices manquantes dans deux jeux, titres avec virgules
  ou guillemets passés sans erreur aux scripts, redémarrage eMMC/NAND visible sur
  CoreELEC.

Détail complet : `changelog.txt`.

## Addons du dépôt pris en charge

| Addon | Intégration |
|---|---|
| `service.protonvpn.manager` | widget d'accueil « État du tunnel » |
| `plugin.video.wtube` | listes YouTube des fiches, vue liste |
| `plugin.video.embycon` | vues forcées (`Skin.ForcedView.*`) |
| `weather.meteoconcept` | météo de l'accueil, prévisions horaires et journalières |
| `plugin.audio.radio`, `plugin.audio.soundcloud` | fenêtres plein écran avec les polices du skin |
| `service.worms.diskinfo` | espace disque de `/storage` |

## Installer

### Via le dépôt TheWorms (recommandé, mises à jour automatiques)

1. Installe le dépôt :
   `https://raw.githubusercontent.com/TheWorms/kodi-repo/main/zips/repository.theworms/repository.theworms.zip`
2. Add-ons → **Installer depuis un dépôt** → *TheWorms Repository* → *Look and feel*
   → *Skin* → **Arctic: Worms** → Installer, puis accepter de basculer vers ce skin.
3. Facultatif : *Services* → **Disk Info**, pour l'espace disque de `/storage`.

Les dépendances (`script.skinshortcuts`, `script.embuary.helper`,
`plugin.video.themoviedb.helper`…) s'installent automatiquement depuis le dépôt
officiel de Kodi.

### Manuelle (zip)

1. Récupère `skin.arctic.worms-x.y.z.zip`.
2. Système → Add-ons → active **Sources inconnues**.
3. Add-ons → **Installer depuis un fichier zip**.

## Reprendre ses réglages d'Arctic: Zephyr - Reloaded

Le skin a un nouvel identifiant : ses réglages et ses menus sont rangés à part.
Pour reprendre ceux de `skin.arctic.zephyr.mod`, en SSH sur la box, **Kodi arrêté**
et **avant** de basculer vers Arctic: Worms :

```bash
systemctl stop kodi
U=/storage/.kodi/userdata
cp -a $U/addon_data/skin.arctic.zephyr.mod $U/addon_data/skin.arctic.worms
cp $U/addon_data/script.skinshortcuts/skin.arctic.zephyr.mod.properties \
   $U/addon_data/script.skinshortcuts/skin.arctic.worms.properties
systemctl start kodi
```

Le menu principal (`mainmenu.DATA.xml`) est commun aux deux skins. Au premier
lancement, skinshortcuts reconstruit les menus : le skin se recharge une fois.

## Dépannage

- **Kodi revient sur Estuary au démarrage** (« Failed to load skin » dans le
  journal) : le skin n'est pas installé ou pas activé. Installe-le depuis le dépôt
  ou le zip plutôt qu'en copiant le dossier à la main : Kodi 21 désactive les addons
  copiés à la main.
- **La tuile Stockage affiche 100 %** : `service.worms.diskinfo` n'est pas installé
  ou est désactivé.
- **Le bouton « Installer le widget » de ProtonVPN refuse ce skin** : c'est
  normal, le widget est déjà intégré.

## Crédits et licence

- Skin d'origine **Arctic: Zephyr** : jurialmunkey.
- **Arctic: Zephyr - Reloaded** : beatmasterRS et ses contributeurs
  (`github.com/beatmasterRS/skin.arctic.zephyr.mod`).
- Icônes : iconmonstr.com (voir leurs conditions) ; icônes supplémentaires de
  metroicon.net, avec l'aimable autorisation de Piers.

Cette œuvre est sous licence Creative Commons Attribution - Pas d'utilisation
commerciale - Partage dans les mêmes conditions 3.0 non transposée
(CC BY-NC-SA 3.0) : http://creativecommons.org/licenses/by-nc-sa/3.0/ — voir
`LICENSE.txt`.
