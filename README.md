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
5) From inside the cloned directory, deploy this script in your $PATH. On this step the script will copy itself to the directory specified as a parameter. The directory must be a $PATH directory, otherwise you will not be able to run the command anywhere in your workstation, without the "./" in front of it.
```
sudo ./dgb-gs -d /usr/local/bin
```
6) Check if your system complies with all dependencies need for this script to run without errors
```
dgb-gs -c
```
7) Add a digibee pipeline git repo to be managed by this script. PS: Before adding a pipeline repo, you must create one on your preferred git platform
```
dgb-gs -a https://github.com/arturscheiner/digibee-pipeline-name.git
```
8) Sync a digibee pipeline with its respective repo. PS: The pipeline must exist on the realm and must have the same name of its git repo 
```
dgb-gs -s digibee-pipeline-name
```
1)  Get some HELP
```
dgb-gs -h
```
```
Help Information

Syntax: ./dgb-gs [-a|l|r|s|c|d|h] params

about pipeline stuff
a	Add a new pipeline git repo to the git sync list
	E.g. -> ./dgb-gs -a git@bitbucket.org:arturscheiner/pipeline-name.git

l	List all the pipelines configured
	E.g. -> ./dgb-gs -l

r	Remove a pipeline from the pipeline list
	E.g. -> ./dgb-gs -r pipeline-name

s	Sync a pipeline with its git repo
	E.g. -> ./dgb-gs -s pipeline-name

about this script
c	Check this script deployment
	E.g. -> ./dgb-gs -c

about anything else
h	Show this help information
	E.g. -> dgb-gs -h
```

### Obs: These two options just work when running ./dgb-gs inside the repo cloned folder.

```
about this script
d	Deploy this script into a directory
	E.g. -> sudo ./dgb-gs -d /usr/local/bin
```