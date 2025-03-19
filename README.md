# mympv
My personalized mpv scripts that works for both Windows and Linux

# Introduction
This repo contains several scripts that I have gathered to make mpv works best for my personal needs. 
**Scripts that available in this repository:**
[SmartSkip](https://github.com/Eisa01/mpv-scripts#smartskip), [SmartCopyPaste_II](https://github.com/Eisa01/mpv-scripts#smartcopypaste_ii), [SimpleHistory](https://github.com/Eisa01/mpv-scripts#simplehistory), [UndoRedo](https://github.com/Eisa01/mpv-scripts#undoredo), [thumbfast](https://github.com/po5/thumbfast)

# Installation
[Official MPV installation guide](https://mpv.io/installation/)

**Windows:** copy both [scripts-opts](https://github.com/HattaPauzi/mympv/tree/main/script-opts) and [scripts](https://github.com/HattaPauzi/mympv/tree/main/scripts) and paste it on %APPDATA%/mpv/.\
**Linux:** copy both [scripts-opts](https://github.com/HattaPauzi/mympv/tree/main/script-opts) and [scripts](https://github.com/HattaPauzi/mympv/tree/main/scripts) and paste it on ~/.config/mpv/.\
If there is none, create one.

**IMPORTANT NOTE**\
On Windows, make sure to install the latest MPV version. On my system, using [mpv-x86_64-windows-msvc](https://nightly.link/mpv-player/mpv/workflows/build/master/mpv-x86_64-windows-msvc.zip) from [First-party builds by GitHub CI (latest commit)](https://nightly.link/mpv-player/mpv/workflows/build/master) works flawlessly.
To make the downloaded portable mpv works on PowerShell, make sure to copy its executable directory and paste it on the PATH environments.

# SmartSkip
You think Netflix is good at binge-watching? Yes, it is.. :) But give SmartSkip a try!
Automatically or manually skip opening, intro, outro, and preview, like never before. Jump to next file, previous file, and save your chapter changes!

![SmartSkip Demo](https://raw.githubusercontent.com/Eisa01/mpv-scripts/master/.misc/smartskip_demo1.webp)
<details>
<Summary>Click for more details!</Summary>

### Default Keybinds
Below default keybinds can be changed using the script conf file, or through script-opts by referring to the names that do not contain spaces.

| Keybind                        | Name                             | Description                                                       |
|-------------------------------------|----------------------------------|-------------------------------------------------------------------|
| `>`                             | smart-next                       | Skips using silence-skip > chapter-next > playlist-next, based on configurable variables     |
| `<`                             | smart-prev                       | Jumps to beginning > previous chapter > previous playlist, based on configurable variables   |
| `?`                             | silence-skip                     | Skips until a silence is detected based on configurable variables                                    |
| `ctrl+right`                     | chapter-next                     | Jumps to next chapter > to next playlist                            |
| `ctrl+left`                      | chapter-prev                     | Jumps to previous chapter > to beginning > to previous playlist     |
| `smart-next`, `enter`, `y`          | Proceed Auto-Skip             | Proceeds Auto-Skip when countdown is started             |
| `smart-prev`, `pause`, `esc`, `n`    | Cancel Auto-Skip             | Cancels Auto-Skip when countdown is started              |
| `ctrl+.`                        | toggle-autoskip                  | Enables or disables Auto-Skip during playback for the current mpv session                            |
| `alt+.`                         | toggle-category-autoskip         | Enables or disables a chapter for Auto-Skip during playback for the current mpv session              |
| ` `                            | toggle-autoload                   | Enables or disables autoload during playback for the current mpv session                             |
| `n`                            | add-chapter                       | Add a chapter for the reached position                                   |
| `alt+n`                         | remove-chapter                    | Removes the current chapter                                              |
| `ctrl+n`                        | write-chapters                    | jumps to the previous available filter based on configured filters       |
| `alt+s` / `alt+S`                  | edit-chapter                     | Renames the current chapter (requires [user-input-module](https://github.com/CogentRedTester/mpv-user-input) )     |
| ` `                              | bake-chapters                   | Merge the changes of chapters for the file inside mkv file                |

### Main Features
- **Smart Next / Prev:** Automatically triggers Skip to Silence, Chapter Next/ Prev, or Playlist Next/ Prev based on configurable parameters.
- **Skip to Silence:** If the file you are watching is not chaptered, skipping to silence will attempt to skip the intro and outro by finding the silence in the file (optionally: chapter automatically created).
- **Auto Skip**: If the file you are watching has organized chapters, any opening, ending sound can be automatically skipped after your **preferred countdown** time.
- **Chapters Modification:** Create, remove, edit chapters,  and then save changes into an external file or bake them into the mkv file.
- **Chapter Next / Prev:** Go to next chapter, if no chapters available go to next playlist, and vise-versa (like the good times with MPC-HC).
- **Autoload**: Basically, if you are not using mpv's autoload script, this is bundled along for convenience and for the possibility to add more features in the future.
- **Customization:** Tons of user customizable settings that can even change the behavior and priority of smart-next, smart-prev, auto-skip, and more!
- **OSD** (On Screen Display): Displays a proper OSD for the actions preformed through SmartSkip.
- **More:** This is not all! Explore the conf file to learn more about the possibilities you are missing out...
</details>

# SmartCopyPaste_II
Just like SmartCopyPaste but logs your clipboard and makes use of it...

![SmartCopyPaste_II Demo](https://raw.githubusercontent.com/Eisa01/mpv-scripts/master/.misc/smartcopypaste_ii_demo1.webp)
<details>
<Summary>Click for more details!</Summary>

### Default Keybinds
The following are the default keybinds, they can be changed in the conf file of the script or using script-opts by referring to the name.
| Keybind                        | Name                             | Description                                                       |
|--------------------------------|----------------------------------|-------------------------------------------------------------------|
| `ctrl+c` / `ctrl+C` / `meta+c` / `meta+C`                   | copy                   | copies file path / URI with resume time using the configured smart behavior.     |
| `ctrl+v` / `ctrl+V` / `meta+v` / `meta+V`                     | paste                | pastes and run into mpv from the clipboard using the configured smart behavior.        |
| `ctrl+alt+c` / `ctrl+alt+C` / `meta+alt+c` / `meta+alt+C`                        | copy-specific           | copies the file path without the reached time or based on the configured specific copy behavior.  |
| `ctrl+alt+v` / `ctrl+alt+V` / `meta+alt+v` / `meta+alt+V`                            | paste-specific                        | pastes and appends the video file into playlist or based on the configured specific paste behavior.                                                                             |
| `c` / `C`                            | open-list                               | opens Clipboard list [(LogManager)](https://github.com/Eisa01/mpv-scripts#logmanager)                                               |

### Main Features
- **Copy and Paste:** Adds copy and paste to mpv for any file, like (urls, torrents, images, subtitles, audio files, video paths)
- **Multi-Paste:** Capability to paste a list of supported items seperated by new line to generate a playlist and conduct different actions depending on the files pasted.
- **youtube-dl Extension Support:** Immediately paste links without finding exact video address for youtube and any other youtube-dl extension supported sites.
- **Peerflix / WebTorrent Extension Support:** Immediately paste torrent links or magnet links when proper extensions are installed.
- **Saves Clipboard to a Log File:** The copies from mpv, and the pastes into mpv will be kept in a log file; log file location is mpv config directory, default for Windows OS: `%APPDATA%\mpv\mpvClipboard.log`, for Linux OS and MAC OS: `~\.config\mpv\mpvClipboard.log`.
- **[LogManager:](https://github.com/Eisa01/mpv-scripts#logmanager)** Reads the log file directly in mpv, giving access to navigate, play files, add to playlist, delete, search, and filter the content.
- **Customization:** Tons of user customizable settings that can even change the behavior and priority of copy and paste actions, as well as everything about LogManager.
- **OSD:** Displays any SmartCopyPaste_II action within mpv.
- **More:** This is not all! Explore the conf file to learn more about the possibilities you are missing out...
</details>

# SimpleHistory
Stores whatever you open in a history file and abuses it with features! Continue watching your last played or resume previously played videos, manage and play from your history, and more...

![SimpleHistory Demo](https://raw.githubusercontent.com/Eisa01/mpv-scripts/master/.misc/simplehistory_demo1.webp)
<details>
<Summary>Click for more details!</Summary>

### Default Keybinds
The following are the default keybinds, they can be changed in the conf file of the script or using script-opts by referring to the name.
| Keybind                        | Name                             | Description                                                       |
|--------------------------------|----------------------------------|-------------------------------------------------------------------|
| `ctrl+r` / `ctrl+R`                   | history-resume                   | **File Loaded:** Resumes in any previously closed video. / **Idle:** Loads and resumes the last played videos.      |
| `alt+r` / `alt+R`                     | history-load-last                | **File Loaded:** Adds last closed video into playlist. / **Idle**: Loads last closed video without resuming.        |
| `ctrl+H`                         | history-incognito-mode           | Triggeres a customizable incognito mode that stops saving history. To resume saving history press `ctrl+H` again |
| `h` / `H`                            | open-list                        | opens History list [(LogManager)](https://github.com/Eisa01/mpv-scripts#logmanager)                                                                             |
| `r` / `R`                            | *NA*                               | opens History list - filtered with recent items [(LogManager)](https://github.com/Eisa01/mpv-scripts#logmanager)                                                |

### Main Features
- **Last Played:** Immediately jumps to your last played video so you continue watching
- **Video Resume:** It saves the position of all videos you are watching so you can easily resume
- **Saves History to a Log File:** The files and position of files played will be kept in a log file; log file location is mpv config directory, default for Windows OS: `%APPDATA%\mpv\mpvHistory.log`, for Linux OS and MAC OS: `~\.config\mpv\mpvHistory.log`.
- **Incognito Mode:** A highly customizable incognito mode that can also be set to auto_run with mpv. It stops history logging when triggered until it is disabled by triggering it again.
- **Blacklist/Whitelist:** A very smart blacklist option that can understand inputted text to blacklist certain websites, urls, files, file paths, and protocols from saving into history. It can also be inverted into a whitelist so only defined files / urls / websites are saved into history.
- **[LogManager:](https://github.com/Eisa01/mpv-scripts#logmanager)** Reads the log file directly in mpv, giving access to navigate, play files, add to playlist, delete, search, and filter the content. (I personally like the distinct filter). It lists the last episode played of each different show.
- **Customization:** Tons of user customizable settings, you can change almost everything. Hate the resume notification? Then just disable it. Hate recents list automatically loading? Then just disable it, and so on so forth...
- **OSD:** Displays any SimpleHistory action within mpv.
- **More:** This is not all! Explore the conf file to learn more about the possibilities you are missing out...
</details>

# UndoRedo
Undo is not enough to fix your accidental seek? Well now you can redo as well..

![UndoRedo Demo](https://raw.githubusercontent.com/Eisa01/mpv-scripts/master/.misc/undoredo_demo1.webp)
<details>
<Summary>Click for more details!</Summary>

### Default Keybinds
The following are the default keybinds, they can be changed in the script or using script-opts by referring to the name.
| Keybind                        | Name                             | Description                                                       |
|--------------------------------|----------------------------------|-------------------------------------------------------------------|
| `ctrl+z` / `ctrl+Z`                | undo / undoCaps                  | undo by returning to previous time.                                      |
| `ctrl+y` / `ctrl+Y`                | redo / redoCaps                  | redo by restoring the undo time.                                    |
| `ctrl+alt+z` / `ctrl+alt+Z`       | undoLoop / undoLoopCaps          | undo accidental seek by returning to previous time and vise-versa. |

### Main Features
- **Undo and Redo:** Undo any accident time jumps in the video by pressing the undo keybind and redo the jumps by pressing the redo keybind.
- **Simple Undo:** Undo accidental time jumps in videos by pressing Simple Undo keybind and press again to return to previous position.
- **OSD:** Displays any UndoRedo action within mpv.
</details>

# thumbfast
High-performance on-the-fly thumbnailer for mpv.

**The script does not display thumbnails on its own,** it is meant to be used alongside a UI script that calls thumbfast.

[Preview of thumbfast on different UIs](https://user-images.githubusercontent.com/42466980/199102896-65f9e989-4189-4734-82a7-bda8ee63c7a6.webm)

## Installation of thumbfast
For the vanilla UI(REQUIREMENT), you also have to install [osc.lua](https://github.com/po5/thumbfast/blob/vanilla-osc/player/lua/osc.lua) (identical to the mpv default, with added thumbfast support) into your `scripts` folder.

### Main Features
No dependencies, no background thumbnail generation hogging your CPU.  
Customizable sizes, interval between thumbnails, cropping support, respects applied video filters.  
Supports web videos e.g. YouTube (disabled by default), mixed aspect ratio videos.

This script makes an effort to run on mpv versions as old as 0.29.0 (Windows, Linux).

### Usage
Once the lua file is in your scripts directory, and you are using a UI that supports thumbfast, you are done.  
Hover on the timeline for nice thumbnails.

# Credits
All credits belongs to these guys. I just take some from them and use what works.
- https://github.com/Eisa01/mpv-scripts for **SmartSkip**, **SmartCopyPaste_II**, **SimpleHistory**, **UndoRedo**
- https://github.com/po5/thumbfast for **thumbfast**
