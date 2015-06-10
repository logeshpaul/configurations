# Launch Sublime Text from the Mac OS X Terminal

Sublime Text 3 ships with a CLI called **subl** (why not "sublime", go figure). This utility is hidden in the following folder (assuming you installed Sublime in `/Applications` like normal folk. If this following line opens Sublime Text for you, then bingo, you're ready.

`open /Applications/Sublime\ Text.app/Contents/SharedSupport/bin/subl`

You can find more (official) details about subl here: http://www.sublimetext.com/3

## Installation

The official documentation I linked to above recommends creating a ~/bin folder (in your home directory). That's weird, I don't recall ever being asked to do that on OS X since most people install binaries within `/usr/local/bin` which Ã¢â‚¬â€œ if you're a developer Ã¢â‚¬â€œ is likely to already have tons of other binaries.

So contrary to the Sublime team recommendation, we're not going to create a `bin` folder in your home directory:

`ln -s /Applications/Sublime\ Text.app/Contents/SharedSupport/bin/subl /usr/local/bin/sublime`

This will simply create a [symlink](http://en.wikipedia.org/wiki/Symbolic_link) called `sublime` (remember, we like names that don't suck to type 500 times a day) between the `subl` binary stashed in the Sublime application package, and a folder where your system usually looks for binaries to execute (launch). Think of it as a wormhole of awesome.

Now let's do a check to see if everything will run smoothly. Enter this:

`open ~/.bash_profile`

(In some cases the profile file is named ~/.profile)

You should see at the top of the file a line that starts with:
`export PATH=`

This contains all the directories that will be looked into for executable binaries when you type a command in Terminal. Since we create a symlink to `subl` called `sublime` in the `/usr/local/bin` directory let's check if this directory is listed on that same line. 

If it is, perfect. Let's keep going. If not, simply add it like this and save the file:

`export PATH=/usr/local/bin:(...)`

Note: The '(...)' in this example represents other folders that would be listed on the same line and separated by a colon.

If you don't already have a PATH set in your bash_profile you can type:

`export PATH=/usr/local/bin:$PATH`

If you had to add `/usr/local/bin` to your PATH, run the following command before continuing:

`source ~/.bash_profile`

This will reload your `.bash_profile` with the newly added directory.

## Testing

Open a Terminal window and run:

`sublime filename` (replace "filename" by an actual file name)

or

`sublime foldername` (replace "foldername" by an actual folder name)

or even

`sublime .` (to open the entire current directory)

## Conclusion

Now you don't need to get out of Terminal to simply open a file or a folder, you didn't have to add an "alias" or yet another bin directory to your `.bash_profile` which you would have needed with the official instructions given by the Sublime team.

Have fun, Sublime is a great editor showing a lot of promise.
