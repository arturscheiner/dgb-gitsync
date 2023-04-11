## Digibeectl Realm Switch

**This script let's you switch between Digibee realms..**
**Before using it, make sure you have digibeectl installed on your computer**



1) Install digibeectl on your MAC or LINUX computer as described on [Digibeectl Official Documentation](https://intercom.help/godigibee/en/articles/5214735-digibeectl-use-guide).
```
curl -s https://storage.googleapis.com/digibee-release-test/releases/install.sh | bash
```
2) Configure digibeectl on your MAC or LINUX computer as described on [Digibeectl Official Documentation](https://intercom.help/godigibee/en/articles/5214735-digibeectl-use-guide).
```
digibeectl set config --file "path/file.json" --secret-key "encryption-key" --auth-key "encryption-passphrase"
```
3) Clone this repo on your MAC or LINUX computer
```
git clone https://github.com/arturscheiner/dgb-gitsync.git
```
4) Access the cloned directory "dgb-gitsync"
```
cd ./dgb-gitsync
```
5) From inside the cloned directory, deploy this script in your $PATH. On this step the script will copy itself on the directory specified as a parameter. The directory must be a $PATH directory, otherwise you will not be able to run the command anywhere in your workstation, without the "./" in front of it.
```
sudo ./dgb-gs -d /usr/local/bin
```
6) Add the actual digibeectl configuration to the realm switch list. PS: If you wanna add another realm to the list, navigate through the steps 7 and 8. If not, follow the step 9, and continue from there.
```
dgb-gs -a
```
7) If you want to add another realm to the switch list, first unset the realm.
```
dgb-gs -u
```
8) After unsetting the realm as described above, repeat the steps 2 and 6.
   - Step 2 -> configure a new realm with digibeectl
   - Step 6 -> add the realm to the switch list
   
9) To get all of the realms in the switch list, run:
```
dgb-gs -l
```
10)  To switch between realms, just run:
```
dgb-gs -s realm-name
```
11) Get some HELP
```
dgb-gs -h
```

```
Help Information

Syntax: dgb-gs [-a|l|r|s|u|c|d|h] params

about realm stuff
a	Add a new realm to the switch list
	E.g. -> dgb-gs -a

l	List all the realms configured
	E.g. -> dgb-gs -l

r	Remove a realm from the switch list
	E.g. -> dgb-gs -r realm-name

s	Set an active realm
	E.g. -> dgb-gs -s realm-name

u	Unset the active realm
	E.g. -> dgb-gs -u

about anything else
h	Show this help information
	E.g. -> dgb-gs -h
```

### Obs: These two options just work when running ./dgb-gs inside the repo cloned folder.

```
about this script
c	Check this script deployment
	E.g. -> ./dgb-gs -c

d	Deploy this script into a directory
	E.g. -> sudo ./dgb-gs -d /usr/local/bin
```