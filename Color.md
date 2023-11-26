Color LS
forthebadge forthebadge

Gem Version CI PRs Welcome

A Ruby script that colorizes the ls output with color and icons. Here are the screenshots of working example on an iTerm2 terminal (Mac OS), oh-my-zsh with powerlevel9k theme and powerline nerd-font + awesome-config font with the Solarized Dark color theme.

image

If you're interested in knowing the powerlevel9k configuration to get this prompt, have a look at this gist.

Table of contents
Usage
Flags
-1
-a (or) --all
-A (or) --almost-all
-d (or) --dirs
-f (or) --files
--help
-l (or) --long
--report
--tree (or) --tree=[DEPTH]
--gs (or) --git-status
--sd (or) --sort-dirs or --group-directories-first
--sf (or) --sort-files
-t
Combination of flags
Installation
Recommended configurations
Custom configurations
Updating
Uninstallation
Contributing
License
Usage
(Back to top)

Man pages have been added. Checkout man colorls.

Flags
With -1 : Lists one entry per line

image

With -a (or) --all : Does not ignore entries starting with '.'

image

With -A (or) --almost-all : Does not ignore entries starting with '.', except ./ and ../

image

With -d (or) --dirs : Shows only directories

image

With -f (or) --files : Shows only files

image

With --help : Prints a very helpful help menu

image

With -l (or) --long : Shows in long listing format

image

With --report : Shows brief report about number of files and folders shown

image

With --tree (or) --tree=[DEPTH] : Shows tree view of the directory with the specified depth (default 3)

image

With --gs (or) --git-status : Shows git status for each entry

image

With --sd (or) --sort-dirs or --group-directories-first : Shows directories first, followed by files

image

With --sf (or) --sort-files : Shows files first, followed by directories

image

With -t : Sort by modification time, newest first (NEED TO ADD IMAGE)

With color options : --light or --dark can be passed as a flag, to choose the appropriate color scheme. By default, the dark color scheme is chosen. In order to tweak any color, read Custom configurations.

Combination of flags
Using --gs with -t :

image

Using --gs with -l :

image

Using --sd with -l and -A :

image

Using --non-human-readable with -l :

This will print the file sizes in bytes (non-human readable format)
image

Installation
(Back to top)

Install Ruby (preferably, version >= 2.6)

Download and install a Nerd Font. Have a look at the Nerd Font README for installation instructions.

Note for iTerm2 users - Please enable the Nerd Font at iTerm2 > Preferences > Profiles > Text > Non-ASCII font > Hack Regular Nerd Font Complete.

Note for HyperJS users - Please add "Hack Nerd Font" Font as an option to fontFamily in your ~/.hyper.js file.

Install the colorls ruby gem with gem install colorls

Note for rbenv users - In case of load error when using lc, please try the below patch.

rbenv rehash
rehash
Enable tab completion for flags by entering following line to your shell configuration file (~/.bashrc or ~/.zshrc) :

source $(dirname $(gem which colorls))/tab_complete.sh
Start using colorls 🎉

Have a look at Recommended configurations and Custom configurations.

Recommended configurations
(Back to top)

To add some short command (say, lc) with some flag options (say, -l, -A, --sd) by default, add this to your shell configuration file (~/.bashrc, ~/.zshrc, etc.) :

alias lc='colorls -lA --sd'
For changing the icon(s) to other unicode icons of choice (select icons from here), change the YAML files in a text editor of your choice (say, subl)

subl $(dirname $(gem which colorls))/yaml
Custom configurations
(Back to top)

You can overwrite the existing icons and colors mapping by copying the yaml files from $(dirname $(gem which colorls))/yaml into ~/.config/colorls, and changing them.

To overwrite color mapping :

Please have a look at the list of supported color names. You may also use a color hex code as long as it is quoted within the YAML file and prefaced with a # symbol.

Let's say that you're using the dark color scheme and would like to change the color of untracked file (??) in the --git-status flag to yellow. Copy the defaut dark_colors.yaml and change it.

Check if the ~/.config/colorls directory exists. If it doesn't exist, create it using the following command:

mkdir -p ~/.config/colorls
And then

cp $(dirname $(gem which colorls))/yaml/dark_colors.yaml ~/.config/colorls/dark_colors.yaml
In the ~/.config/colorls/dark_colors.yaml file, change the color set for untracked from darkorange to yellow, and save the change.

untracked: yellow
Or, using hex color codes:

untracked: '#FFFF00'
To overwrite icon mapping :

