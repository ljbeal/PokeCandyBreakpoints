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

This will be listed on the pokemon's page on a site such as bulbapedia or serebii.

For example, charizard is listed as [Levelling Rate: Medium Slow](https://bulbapedia.bulbagarden.net/wiki/Charizard_(Pok%C3%A9mon)) On Bulbapedia,
and the same on [Serebii](https://www.serebii.net/pokedex-sv/charizard/), only listed as "Experience Growth"

The groups along with their `command` are as follows:

 - Erratic (`erratic`)
 - Fast (`fast`)
 - Medium Fast (`medfast`)
 - Medium Slow (`medslow`)
 - Slow (`slow`)
 - Fluctuating (`fluctuating`)

For example, Lets say we have a lvl 5 charmander we want to level up to 62 to learn flare blitz:

`python main.py --group medslow --lvl 5 --target 62`

This tells us that we need to just use 8 XL candies:

```commandline
Targeting lvl 62 for a pokemon in group medslow with 135 exp (lvl 5):
{'XL Candy': 8}
```

And for lvl 100, 68 in total:
```commandline
Targeting lvl 100 for a pokemon in group medslow with 135 exp (lvl 5):
{'XL Candy': 36}
```

A second example, for a level 57 Iron Hands with 231763 exp. 
Paradox Pokemon are in the `slow` exp group, so we would use:

`python main.py --group slow --exp 231763`

This gives:

```commandline
Targeting lvl 100 for a pokemon in group slow with 231763 exp (lvl 57):
{'XL Candy': 28, 'Rare Candy': 5}
```

Telling us that we should use 28 XL candies, and then 5 Rare candies to complete 
the levelling process.

Note that it is more accurate to use the actual exp value of your Pokemon, instead of the level.
