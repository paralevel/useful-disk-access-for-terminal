# Useful Disk Access for Terminal

If you for example get a `Could not write domain` error when using the `defaults` command or `Operation not permitted` when trying to access specific files or folders (related to file system areas that are sandboxed or under some kind of protection, instead of file permissions which would give a `permission denied` error), this is usually solved by giving Full Disk Access permission to Terminal ([see here](https://github.com/mathiasbynens/dotfiles/issues/820)), but if you want to avoid doing that just for a single file, you can instead use the following trick (the example is after a failed attempt at running `defaults write -app safari WBSNewTabPositionPreferenceKey -int 0`:

Open ~/Library/Containers/com.apple.Safari/Data/Library/Preferences/ in Finder (e.g. using `open ~/Library/Containers/com.apple.Safari/Data/Library/Preferences/`)

Copy the file 'com.apple.Safari.plist' and paste it into Terminal (press Ctrl-C to abort afterwards) – also has the same effect if you copy the parent folder or one of the other files in the same folder

Retry the `defaults` command

Seems to have a permanent effect and also makes all other files and subdirectories in the same directory accessible, and unlike Full Disk Access which goes into effect for all users, it only affects the current user
