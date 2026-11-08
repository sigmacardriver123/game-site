# Game catalog research and compatibility notes

Research snapshot: 8 November 2026. This audit reviews the repositories supplied for the Game Hub and records what their listings mean for a static local site. A repository license applies to that repository's code and data; it does not automatically license the games, ROMs, SWF files, logos, or assets linked by it.

## What is in the site catalog

`welcome.html` includes a small, deduplicated starter set of actual browser game pages and relevant runtime/reference cards. Browser demos open in the site's player frame and also have an “Open original” fallback. Card covers are locally authored typographic artwork; no third-party game logos, ROMs, SWFs, or screenshots are copied into this project. Favorites and recent launches are kept in browser local storage.

The playable game pages currently identified are Connect Four (`c4`), 3D Hartwig Chess Set, OpenLara's WebGL demo, Q3JS, Chrono Divide, Wolfenstein 3D on DOS.Zone, and Beneath a Steel Sky on ScummWEB. A card may launch a project/library page rather than a game if that entry is an emulator or engine; its badge says whether it needs user files, a hosted service, or an available browser demo. Third-party hosts can block iframe embedding or change availability.

## Format and compatibility map

| Requested format/category | Discovery and actual runtime/file | Runs in this static site? | Backend / original files | Distribution note |
|---|---|---|---|---|
| HTML5 | c4 has a browser game page and source link in OpenSourceVideoGames/list | Hosted page; not bundled locally | Offline modes don't need a server; optional online mode does | Link to author's page; source code license must be checked before copying |
| JavaScript | Same c4 project, plus simple browser game listings | Hosted page; technically local-capable if source is vendored | None for its offline mode | A GitHub listing is not permission to rehost; inspect individual repo license |
| Flash / SWF | Ruffle web emulator; SWF is the actual game file | Ruffle can run a user supplied SWF; no SWFs included | Usually no backend after emulator is hosted | Ruffle dual MIT/Apache-2.0; every SWF retains its own rights |
| WebAssembly | EmulatorJS, webretro, OpenLara and game ports listed in Awesome-Browser-Game-Ports | Yes when a suitable build/content is hosted | Build-specific; ROM or game assets often required | Emulator / engine license and game-data license are separate |
| Unity WebGL | The ultimate web-ports catalog has Unity WebGL examples | A self-contained build can run in a browser frame, after rights and compatibility review | Often none, unless title itself uses a service | Original game build/assets and Unity terms need individual review |
| Godot Web export | The ultimate ports catalog includes Godot exports | Browser export can run if the full export bundle is locally hosted | Usually none for single-player | Game and asset licenses remain separate; check export's engine/runtime terms |
| DOS games | js-dos, v86 and hosted DOS.Zone pages; Wolfenstein 3D page is linked in the catalog | Hosted demo works through remote site; local play needs runtime + game archive | Usually no backend for single player; multiplayer is title-specific | DOS.Zone's free play offer is not a license to download/rehost proprietary data |
| Browser-based emulation | EmulatorJS, webretro, webЯcade | Emulator UI can run locally; this site currently links to hosted frontends | Feeds/cloud may be used by webЯcade | Emulator code licenses do not cover feed items or ROMs |
| NES / SNES / GBA / N64 | EmulatorJS/webretro support cores for these systems | Yes after licensed ROM and any required BIOS are provided | Normally local emulation | Do not bundle commercial ROMs or BIOS without permission |
| PlayStation 1 | EmulatorJS/webretro include PS1 support | Technically yes with appropriate supported files | Local; BIOS is required by some setups | PS1 ROM/disc images and BIOS have independent rights |
| Sega Genesis | EmulatorJS/webretro include Genesis cores | Technically yes with a supported ROM | Local | ROM rights are separate from emulator license |
| Arcade / MAME | EmulatorJS lists arcade systems; compatibility depends on core and ROM set | Technically yes with compatible files | Local; no universal ROM set | Arcade ROMs are individually copyrighted; matching ROM/core versions matter |
| Java applets (browser-compatible) | CheerpJ is listed as the applet runtime in Awesome-Browser-Game-Ports | Potentially, on a compatible applet and browser/runtime | May rely on old server services | No specific applet/game file was cleared for this catalog; Java runtime support is not a game license |
| WebGL / Three.js | 3D Hartwig Chess Set (CodePen) and OpenLara demo | Hosted browser pages; self-host only after reviewing code/data licenses | OpenLara demo can run client-side; hosted pages may have external dependencies | OpenLara engine BSD-2-Clause, but original Tomb Raider assets are separate |
| Open-source game ports | OpenLara, Freedoom, ScummVM, web ports in the supplied catalogs | Some launch as web demos; others are source/runtime projects | Varies by title | Check both engine and game data; decompilation/recompilation alone does not grant asset rights |
| Multiplayer browser games | Q3JS, Chrono Divide, Freeciv-web are examples in the browser-port list | Their hosted browser clients can be opened in a frame when the host permits it | Yes: Q3JS arenas, Chrono Divide client/server, Freeciv server | Remote service availability and its terms govern multiplayer; no local server is included |
| Retro PC games | ScummVM, js-dos, v86, web ports | Some freeware titles run on ScummWEB; others require a user's own data | Usually client-side for single-player | ScummVM README explicitly says game data must already be available; freeware title rights still need verification |

## Playable file inventory

These are the concrete file/runtime inputs identified in the sources. No proprietary files are bundled in the site.

| Item | Actual file(s) or build output | Local status |
|---|---|---|
| c4 / Connect Four | TypeScript + Canvas source in `kenrick95/c4` (`browser/`, `core/`); published static browser page at `kenrick95.github.io/c4/` | Can be rebuilt and served locally under MIT with attribution; current site links to hosted page |
| OpenLara | WebGL build linked from `XProger/OpenLara`; source repository has `bin/` and `src/`; demo-level data is advertised by the README | Demo page is hosted remotely; engine code BSD-2-Clause. Full retail level data is separate |
| Freedoom | `freedoom1.wad`, `freedoom2.wad`, `freedm.wad` | Actual game data is available in official project releases/repository under modified BSD; needs a compatible Doom engine build, not included here |
| Flash game | Individual `.swf` file + Ruffle web runtime | No SWF game file was cleared or copied; each SWF needs its own rights review |
| DOS game | Individual DOS executable/data or js-dos bundle/archive, often `.jsdos` or `.zip` | Wolfenstein listing points to a hosted DOS.Zone version; no files downloaded or inspected for redistributability |
| Console/arcade game | System-specific ROM (for example `.nes`, `.sfc`/`.smc`, `.gba`, `.n64`, `.md`, `.cue`/`.bin`/`.chd`, MAME ROM set) and sometimes a BIOS | Emulator projects supply cores, not commercial game files; none bundled |
| Unity WebGL build | HTML entry point + loader/framework/data files and `.wasm` | No individual game build in the supplied repositories was license-cleared |
| Godot web export | HTML entry point + `.pck` and WebAssembly/runtime files (output varies by Godot version) | No individual game build in supplied sources was license-cleared |
| Java applet | Original applet `.jar` and compatible runtime/bridge (for example CheerpJ) | No actual game applet was identified with clear game-file redistribution rights |
| ScummVM title | Per-game data directory/archive; ScummVM engine only substitutes for original executables | ScummWEB currently offers Beneath a Steel Sky; other titles may need user-provided files |

The local workspace contains no game binary or web export. The dashboard is a source-linked catalog and remote player wrapper; only games whose data/build can be cleared and hosted should later be made truly local.
## Linked repositories reviewed

| Repository | What it contributes | Repository-level license / practical limitation |
|---|---|---|
| [FlashpointProject](https://github.com/FlashpointProject) | Preservation launcher and archive infrastructure for web games | The org's code does not make all archived third-party games redistributable; Flashpoint is a desktop archive/launcher, not a collection of cleared local browser files |
| [ultimate-catalog-of-web-game-ports](https://github.com/matapandax/ultimate-catalog-of-web-game-ports) | Large discovery list, reported 582 titles and 257 demos in its README snapshot | Its own README says third-party repositories define their own terms; every game/demo must be checked individually |
| [Awesome-Browser-Game-Ports](https://github.com/bitburner/Awesome-Browser-Game-Ports) | Categorized browser ports, emulator list, and a useful “free data vs bring your own files” legend | List is CC0 / MIT; explicitly states it hosts no game data and rights stay with owners |
| [awesome-decomp-games](https://github.com/SubmitGame/awesome-decomp-games) | Decompilation/recompilation/source-port leads | List data CC0 and code MIT; a port/decomp is not permission to distribute original game assets |
| [OpenSourceVideoGames/list](https://github.com/OpenSourceVideoGames/list) | Browser-based and native open-source game leads, including c4 | List itself is CC BY-NC-SA 4.0; follow each linked game project's own code/art license |
| [EmulatorJS](https://github.com/EmulatorJS/EmulatorJS) | Browser emulation frontend for many retro systems | GPL-3.0; README points to supported cores; does not grant ROM or BIOS rights |
| [Ruffle](https://github.com/ruffle-rs/ruffle) | Flash emulator for the web and desktop | Dual MIT / Apache-2.0; SWF rights are independent and ActionScript support is still incomplete |
| [js-dos](https://github.com/caiiiycuk/js-dos) | DOS/Windows-in-browser runtime and multiplayer/network features | Use its package/runtime terms; game bundles/data must be cleared independently |
| [v86](https://github.com/copy/v86) | x86 PC emulator translated to WebAssembly | Simplified BSD plus listed third-party notices; disk images and installed software are separate |
| [webretro](https://github.com/BinBashBanana/webretro) | RetroArch-in-browser frontend and console cores | Frontend MIT; cores have their own licenses; README says ROMs are not included |
| [webЯcade](https://github.com/webrcade/webrcade) | Feed-driven web frontend for emulators and engines | Feed content and images come from cloud resources and user-defined feeds; audit each feed item |
| [ScummVM](https://github.com/scummvm/scummvm) | Compatibility engine for adventure/RPG games | GPL-3.0; README says the user needs the original game data files; some separate freeware games are available |
| [OpenLara](https://github.com/XProger/OpenLara) | Classic Tomb Raider engine and WebGL demo | BSD-2-Clause engine; original retail data has separate rights; the repository advertises a demo level |

## Rights and presentation decisions

- No ROM, BIOS, SWF, commercial DOS archive, or proprietary game asset is copied into the workspace.
- Cards use custom typographic title art made in CSS rather than scraped game logos. The supplied repos do not confer rights to use trademarks or third-party artwork.
- `Play in player` opens the linked official/community-hosted browser page in a sandboxed iframe. Since many services set frame restrictions, the player includes an “Open original” link.
- Do not represent the browser demos as local/offline games. The compatibility tags identify browser demos, required game files, or remote services.
- Before adding downloadable files, clear the game data, soundtrack, screenshots/logo, and build bundle independently, and store the source/license and attribution with the catalog entry.

## Sources

- [Flashpoint Archive GitHub](https://github.com/FlashpointProject)
- [Ultimate Catalog README](https://github.com/matapandax/ultimate-catalog-of-web-game-ports)
- [Awesome Browser Game Ports README](https://github.com/bitburner/Awesome-Browser-Game-Ports)
- [Awesome Decomp Games](https://github.com/SubmitGame/awesome-decomp-games)
- [Open Source Video Games list](https://github.com/OpenSourceVideoGames/list)
- [EmulatorJS README](https://github.com/EmulatorJS/EmulatorJS)
- [Ruffle README](https://github.com/ruffle-rs/ruffle)
- [js-dos README](https://github.com/caiiiycuk/js-dos)
- [v86 README](https://github.com/copy/v86)
- [webretro README](https://github.com/BinBashBanana/webretro)
- [webЯcade README](https://github.com/webrcade/webrcade)
- [ScummVM README](https://github.com/scummvm/scummvm)
- [OpenLara README](https://github.com/XProger/OpenLara)
- [OpenLara demo](https://xproger.info/projects/OpenLara/)
- [Q3JS](https://q3js.com/), [Chrono Divide](https://chronodivide.com/), [Wolfenstein 3D via DOS.Zone](https://dos.zone/wolfenstein-3d-may-05-1992/), [ScummWEB](https://scummweb.tsilva.eu/)

