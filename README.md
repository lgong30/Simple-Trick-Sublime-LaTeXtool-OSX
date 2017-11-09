# TeX on The Fly for LateXTools of ST3 on OSX

[LateXTools](https://github.com/SublimeText/LaTeXTools) is one of the most useful editing-assist tools for dealing for LaTeX. It is a plugin for Sublime Text. However, if you have used it on Mac, you will be annoying if you happen to use BasicTex instead of the full version of MacTeX. Because whenever your LaTeX codes use some new packages (packages that are not installed on your Mac), you will have to install them manually. Although you can use the script [texliveonthefly](https://ctan.org/pkg/texliveonfly?lang=en) to install them semi-automatically. That is you open a terminal, cd to the root directory of your LaTeX project, and then run the script, _e.g.,_ `./texliveonthefly.py main.tex`. This is still very annoying. 

## Simple Trick

Now we give you a simple trick to integrate the `texliveonthefly.py` into LateXTools. The idea is to create a script builder in the settings of LatexTools as follows. Assuming that the `texliveonthefly.py` is in `~/GitHub/texliveonthefly.py`.

```json
"builder_settings" : {

        // General settings:
        // See README or third-party documentation

        // (built-ins): true shows the log of each command in the output panel
        "display_log" : false,

        "options": ["-shell-escape"],

        // Platform-specific settings:
        "osx" : {
            
            // See README or third-party documentation
            "script_commands": [
                ["python", "~/Github/texliveonfly.py", "$file"]
            ]
        },

        "windows" : {
            // See README or third-party documentation
        },

        "linux" : {
            // See README or third-party documentation
        }
    },
```

Now you do not need to go to terminal, you can just `command+shift+B` can choose the `LaTeX - Script Builder`. 

You can try it by using the [`example.tex`](./example.tex).
