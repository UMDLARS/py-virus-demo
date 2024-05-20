# Python3 Virus Demo
This is a mostly harmless virus demo written in python3.

## WARNING
This is intended for educational purposes only to demonstrate virus spreading.

When ran the `virus.notpy3` script WILL infect any `.notpy3` files it can find in the current working directory. The `.notpy3` extension is used to prevent this from being able to infect any actual python scripts. But still be careful.

If you run this script this script somewhere you shouldn't and/or modify this script and break something, we are NOT responsible.

## How It Works
When the `virus.notpy3` script is ran it'll infect any other `.notpy3` script(s) in the current working directory. 

First the virus will open itself and read all lines which contain the phrase "#VCODE". 

Then it'll iterate through each file contained within the current working directory. If a file does not have a `.notpy3` extenion, it'll be ignored. If a file already contains the "#VCODE" phrase, it'll also be ignored. Otherwise the virus will read in the victim script, prepend both `#!/usr/bin/python3` and the previously read "#VCODE" lines to the victim script, then write the result back to the victim script. At this point the victim script is now infected and if ran will try to repeat this same process when ran before executing its intended functionality.

## Usage
### Running The Virus
Clone this repo somewhere and `cd` into it.

Give the `foo.notpy3`, `bar.notpy3`, `baz.notpy3`, and `qux.notpy3` scripts a quick look. They should all look something like:
```
#!/usr/bin/python3
import sys

print("Hi, I am {}".format(sys.argv[0]))
```

If you run them they should print `Hi, I am [script name]`.

Now to run the virus execute `./virus.notpy3` in this directory. It should print out a bunch of messages about infecting the other `.notpy3` files.

After exectuing the virus, check all of the other `.notpy3` files. They should now be infected and have the entire contents of `virus.notpy3` prepended to them. 

Now if you run any of them they'll try to find and infect other `.notpy3` scripts as well.

You can try copying `backup/foo.notpy3` to `a.notpy3` (`cp backup/foo.notpy3 a.notpy3`). Now if you run any of the other scripts (e.g. `./foo.notpy3`), `a.notpy3` will become infect and have the virus prepending to it as well!

### Restoring The Scripts
To quickly restore all of the non-virus `.notpy3` scripts to their original states you can run the `./restore.sh` script. This will copy the backup copies of all of the scripts in `./backup` to the current directory.

If you've messed up the backups you can reset your copy of this repo using `git reset --hard` or you can grab the originals from https://github.com/UMDLARS/py-virus-demo/tree/main/backup
