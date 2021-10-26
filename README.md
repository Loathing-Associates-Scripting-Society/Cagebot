```
  _____                 _           _   
 / ____|               | |         | |  
| |     __ _  __ _  ___| |__   ___ | |_
| |    / _` |/ _` |/ _ \ '_ \ / _ \| __|
| |___| (_| | (_| |  __/ |_) | (_) | |_
 \_____\__,_|\__, |\___|_.__/ \___/ \__|
              __/ |
             |___/
```
            
Cagebot is an automatic hobopolis cagebaiting bot for Kingdom of Loathing
operated wholly through ingame whispers.

## IMPORTANT NOTE
**HEED THE NOTICE ON THE FOURTH WALL**. If you are operating Cagebot, do NOT, under any circumstances, enter any hobopolis instance to which it has a whitelist on any other account. Failure to heed this warning may result in your accounts being disabled. You have been warned.

## INSTALLATION
In order to install cagebot, you will need node.js and npm installed. 
These can be found [here](https://docs.npmjs.com/downloading-and-installing-node-js-and-npm). 
Once you have those, navigate to the root directory of this project and
execute the following:

```
npm install
npm run build
```

## OUT OF GAME SETUP
In order to function, Cagebot requires exclusive access to a character
that is at least level 3 and has passed the trial of literacy. To give
Cagebot access to a character, put its username and password into the
file named '.env' in the root directory of this project (alongside
package.json). This file should be in the form:

```
  KOL_USER='Cagebot'
  KOL_PASS='Cagebot P4ssw0rD'
```

## INGAME SETUP
To set up your multi, please have it idle with as much +adv rollover gear
on as possible, amd at least 1 hp regen/fight. Whatsian Ionic Pliers in
the offhand are recommended as a cheap and plentiful option for this.

You will also require an autoattack with the name CAGEBOT (all caps) that
reads "runaway;repeat". If your account has means of running freely,
feel free to add them too, but I take no responsibility for failures.
If you need to tiebreak equipment, +noncombat rate is nice too.

Optionally manually stock bot with the items below for consumption.
Bot must be at least the associated level to consume these items.
Currently bot will not buy these, only uses from inventory.

- Fleetwood mac 'n' cheese (Level 8)
- Crimbo pie (Level 7)
- Psychotic Train wine (Level 11)
- Middle of the Road™ brand whiskey (No level requirement)

## RUNNING
To run cagebot, either run `npm run start` in the root directory, or just `node dist/index.js`, both are equivalent.

## USAGE
Cagebot is used by sending in-game whispers to the account with which it is associated. (To do this, enter `/w [accountname] [command]` into the in-game chat.) The commands understood by Cagebot are as follows:

- `cage [clanname]`: If cagebot is whitelisted to a clan with the supplied name and not presently caged, it whitelists into that clan and attempts to get caged in its hobopolis. This command will fail if:
  * Cagebot is already in a cage
  * Cagebot does not have a whitelist to any clans with the supplied name.
  * Cagebot is whitelisted to multiple clans with the supplied name (for example, if it is provided `Phill` and has whitelists to both `Phill's Good Clan` and `Phill's Bad Clan`
  * Cagebot does not have sufficient clan permissions to adventure in hobopolis in the specified clan.
  * Hobopolis is not open in the specified clan.
  * Cagebot falls to eleven or fewer adventures remaining.
- `escape`: If cagebot is presently caged, and the person sending the `escape` command is the one who sent the original `cage` command, it attempts to free itself from the cage. If it has been released via The Former Or The Ladder, it will escape without spending turns, otherwise, it spends ten adventures to chew out of the cage.
- `release`: As escape, attempts to escape from the cage it is presently in, however this can be used by anyone, not just the original sender of the `cage` command. The `release` command can only be used if cagebot has been caged for at least an hour (to prevent cagebot getting stuck due to the original cager logging off for the day, for example), or if cagebot cannot ascertain who initially caged it (for example, because the bot was restarted while in a cage)
- `status`: Returns the current status of cagebot. Specifically:
  * Whether it is in a cage.
  * If so, at whose request, and for how long.
  * Whether the release command is usable, and if not, how long until it will be.
  * How many adventures it has remaining.
- `help`: Returns a help message detailing all of the above commands.
