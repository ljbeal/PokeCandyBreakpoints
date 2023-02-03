# PokeCandyBreakpoints

Simple Command Line Tool to show you the most efficient usage of XL and Rare candies.

Principle:

 - Exp Candies give a set amount, therefore more efficient at low levels
 - Rare Candies always bump one _level_, therefore more efficient at high levels
 - At some point in the level curve, there may be a switchover where Rare candies are more efficient

This tool exists to help you find that switch.

### How does it work?

Input your Pokemon's [exp group](https://bulbapedia.bulbagarden.net/wiki/Experience), 
along with the current level or exp amount (more accurate),
after which the script will simulate using XL Exp Candies until they are no 
longer gaining more than one level. Then rare candies are used to attain the 
desired level (defaults to 100).

### Requirements

First git clone or download this repository, 
then open a terminal window such as powershell.

From here you will need a valid python install, once this is done consider 
making a virtual environment with:

`python -m venv PokeCandyBreakpointsVenv`

Then activate this env with 

`PokeCandyBreakpointsVenv/Scripts/activate`

On windows, or on linux:

`source PokeCandyBreakpointsVenv/bin/activate`

Then install the requirements with

`pip install -r requirements.txt`

### Usage

Now you're ready to go! Find the Pokemon you want to calculate for, and find the exp group.

For example, for a level 57 Iron Hands with 231763 exp. 
Paradox Pokemon are in the `slow` exp group, so we would use:

`python main.py --group slow --exp 231763`

This will output:

```
Targeting lvl 100 for a pokemon in group slow with 231763 exp (lvl 57):
{'XL Candy': 28, 'Rare Candy': 5}
```

Telling us that we should use 28 XL candies, and then 5 Rare candies to complete 
the levelling process.
