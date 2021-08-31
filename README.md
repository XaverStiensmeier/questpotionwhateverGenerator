# questpotionwhateverGenerator
Generates whatever you want at (weighted) random. This allows you to create random tables with ease!

## plotg.py - The Main Program

### Folder structure
Every random table has to be in the src folder. You can have subfolders (see "How to call the program"). You also can have a "src/general" folder which is searched whenever no match is found in the folder selected by the function call. This means you can define a "anmial" file containing 100s of animals in your "src/general" folder ("src/general/animal") and then call it in all your projects as long as you don't have a "animal" file in your project ("src/yourprojectname/animal"). This might sound harder than it actually is ;)


### How to get started
Rename src_dummy to src to have something to try out. Try out this function call while being in the folder "questpotionwhateverGenerator/":
* Linux: `./plotg.py -l minimalExample`
* Windows: `python plotg.py -l minimalExample`
Result similar to: ``

If this works you've just got your first random string! Let's make some other calls! (I will no longer mention the operating system's specifics)
* `plotg.py -l minimalExample -n 10`
* `plotg.py -l end -n 6`
* `plotg.py -l Anfang -s exampleHTKN/` From here we are using german examples, but you should understand what's happening nonetheless
* `plotg.py -l Anfang Anfang -s exampleHTKN/` Yes, this is just like `plotg.py -l Anfang -s exampleHTKN/ -n 2`
* `plotg.py -l Heldentaten Baumtaten -s exampleHTKN/` Here you can see that different entry points can be used in one call.
* `plotg.py -l Heldentaten Baumtaten -s exampleHTKN/ -n 2` Which are multiplied as well.
* `plotg.py -l beginning -s intext/ -n 5` Different results intext? Check out the How to write src-files section! 

You should now understand and be comfortable with executing the program in simple ways, but let's understand a little bit more, shall we?

### How to call the program
The program is named `plotg.py`. There are three arguments:

* `-l` or `--list` Takes a list of files. From those files random entries are selected. If no subfolder is specified the program
will search 'src' and if it doesn't find said file there it will look in 'general'.
* `-n` or `--number` Takes a number. Executes the program 'number' times. Very helpful if you would like to choose from different random possibilities to make it more fitting to the current situation. Default value is 1.
* `-s` or `--subfolder` Takes subfolder. This allows you to specify a subfolder in src. For example `subfolder/` or `subfolder/subsubfolder/`
* `-m` or `-matchStarting` Instead of looking for one file exactly matching the `--list` entries, all files will be now called starting with the `--list` entries.

A function call can use all of those command line arguments. `plotg.py -l File -n 42 -s SubFolder` therefore is a valid call (as long as you really have said File and Subdfolder (don't lie man, the program will know).

Now you should know why the commands above are working and by checking the folder structure you can ensure that everything worked as it should. For examining the folder structure the inbuild command `tree` can be very helpful (but please don't call it if there are many sub^n folders ;)

### How to write src-files
First things first: Files must not start with a number. Apart from that you are pretty free. I heavily encourage you to keep all your files in separat folders to make working with them more enjoyable. If you have large tables that you will use in many projects, just move them into the "general/" folder.

* `_` This will call the file behind underline (and therefore select a random element in that file) after printing the text before the underline. Example: `SomeQuest_SomeFile`: SomeQuest will be printed and then the random element from the called file.
* `|` stands for weighted. The standard weight is 100. Example: `SomeQuest_SomeFile|50`. This is therefore half as likely as a standard element which has weight 100.
* `{SOME_TEXT}` is what we will call an intext-call: Allows you to get a random value from another file within your text. Example: `The King {action} and after that he {action}, but suddenly {event}.`
* `{XdY+Z}` or `{XdY-Z}` is what we will call an intext-roll: Allows you to get a die roll within your text. Example: `After {1d3} minutes {1d6+2} giant scorpions appeared and killed {20d20} people in {1d6-4} seconds!`. The roll can be negative if `Z` is larger than the roll.


## clean.py - Preparation
When creating files from online tables often you have some leading spaces, some enumerations, duplicates or some awful tabbing going on. Clean will remove: Leading numbers, dots and dashes. Leading and trailing spaces. And will move tabbed content into newlines. Note: Be aware that the usage of this help-program is not always helpful. Maybe the text starts with: "2d6 witches appear!"... you really don't want to lose said 2 or do you? Therefore be careful when using it and make sure to use the right flags (which mostly are not implemented yet). Please also be very careful not to use the wrong path :) the program can't know whether files you feed him are random tables or your very important homework:
* `-s` keeps spaces (trailing and leading)
* `-e` keeps leading numbers, dots and dashes (DONE!)
* `-t` keeps tabs
* `-d` keeps duplicates
* `-s` keeps syntax that can be misinterpreted


### Some last words
I am excited to see what people will create with my little program! Please share your tables - if able (don't break/bend copyrights) - so everyone can enjoy them!
