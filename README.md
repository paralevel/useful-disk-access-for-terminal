# Bypass file system restrictions without having Full Disk Access in Terminal on macOS

If you for example get a `Could not write domain` error when using the `defaults` command or `Operation not permitted` when trying to access specific files or folders, this is usually solved by giving Full Disk Access permission to Terminal ([see here](https://github.com/mathiasbynens/dotfiles/issues/820)), but if you want to avoid doing that just for a single file, you can instead use the following trick (the example is after a failed attempt at running `defaults write -app safari WBSNewTabPositionPreferenceKey -int 0`:

Open ~/Library/Containers/com.apple.Safari/Data/Library/Preferences/ in Finder (e.g. using `open ~/Library/Containers/com.apple.Safari/Data/Library/Preferences/`)

Copy the file 'com.apple.Safari.plist' and paste it into Terminal (press Ctrl-C to abort afterwards), also has the same effect if you copy the parent folder instead of the plist file

Retry the `defaults` command

Looks like the effect is permanent (for the current user account) and it also makes all other files and subdirectories in that specific directory accessible
