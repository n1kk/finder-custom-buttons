My custom finder buttons. 

Made via automator to be able to drag them into the finder bar. 

Starts terminal/editor with current finder folder or current selected file (if any).

![Finder custom buttons](/screenshots/example.gif)

Script example:
```bash
# if file will be selected it will be passed as an argument
if [ -z $1 ]; then 
    # no files selected, get the most top finders window current path
	local finderPath=`osascript -e 'tell application "Finder" to get the POSIX path of (target of front window as alias)'`
    # lunch editor with that folder open
	open -a "Sublime Text" "$finderPath"
else 
    # we got some files selected, open them in editor
	open -a "Sublime Text" "$@"
fi
```