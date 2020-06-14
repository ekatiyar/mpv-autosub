# [Automatic subtitle downloading for MPV](https://github.com/ekatiyar/mpv-autosub)
* Cross-platform: **Windows, Mac and Linux**
* Multi-language support
* Subtitle provider login support
* Subtitles for streams can also be enabled
* **No hotkeys required**: opening a video will automatically trigger subtitles to download  
  (Only when the right subtitles are not yet present)

## Dependencies
This Lua script uses the [Python](https://www.python.org/downloads/) program
[subliminal](https://github.com/Diaoul/subliminal) to download subtitles.
Make sure you have both installed:  
```bash
pip install subliminal
```

## Setup
1. Copy autosub.lua into:

   |       OS      |                      Path                           |
   |---------------|-----------------------------------------------------|
   | **Windows**   | [Drive]:\Users\\[User]\AppData\Roaming\mpv\scripts\ |
   | **Mac/Linux** | ~/.config/mpv/scripts/                              |

   ```bash
   mkdir ~/.config/mpv/scripts
   cat > ~/.config/mpv/scripts/autosub.lua
   [Paste script contents and CTRL+D]
   ```
2. Specify the correct subliminal location for your system:  
   - To determine the correct path, use:  

     |       OS      |      App       |        Command          |
     |---------------|----------------|-------------------------|
     | **Windows**   | Command Prompt |    where subliminal     |
     | **Mac/Linux** | Terminal       |    which subliminal     |

   - Copy this path to the subliminal variable at the start of the script:
     ```lua
     local subliminal = '/path/to/your/subliminal'
     ```
     On Windows, the backslashes in the path need to be escaped, e.g.:  
     **C:\\\\Users\\\\Administrator\\\\AppData\\\\Local\\\\Programs\\\\Python\\\\Python37\\\\Scripts\\\\subliminal.exe**
 
3. Optionally, you can also enable auto-sub for video streams, although this may not work.
   - Set a default directory for stream subtitles to be downloaded to. Note that this file persists even after the stream is closed.
   - set the stream_enabled boolean to true

## Customization
* Optionally change the subtitle languages / [ISO codes](https://en.wikipedia.org/wiki/List_of_ISO_639-1_codes).
  Be sure to put your preferred language at the top of the list.  
  If necessary, you can manually trigger downloading your first choice language by pressing `b`,  
  or your second choice language by pressing `n`.
* Optionally specify the login credentials for your preferred subtitle provider(s), if you have one.
* If you do not care for the automatic downloading functionality, and only wish to use the hotkeys,  
  simply change the `auto` bool to `false`.
* For added convenience, you can specify the locations to exclude from auto-downloading subtitles, or alternatively,  
the *only* locations that *should* auto-download subtitles.

This script is under the [MIT License](./LICENSE-MIT),
so you are free to modify and adapt this script to your needs:  
check out the [MPV Lua API](https://mpv.io/manual/stable/#lua-scripting) for more information.

If you find yourself unable to find the correct subtitles for some niche movies/series,
you might be interested in the [submod](https://github.com/davidde/submod_rs)
command line tool I've written to manually correct subtitle timing.

## Credits
This is a fork of [davidde's ](https://github.com/davidde/mpv-autosub) autosub script.
