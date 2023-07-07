# dgb-gitsync v0.2

## What's New on this version

* The new script code structure is more modular and now allows it to be expanded easily
* Now the script supports the configuration of pipelines based on their major version
* Ability to bind a pipeline configuration with a git repo, using the -b option
* The option -l now lists the configured pipelines with their respective bind status
* Corrected a bug where the removal of a pipeline wasn't workig on the previous version
* The sync (-s) and watch (-w) uses the same internal mechanics
* When a pipeline is synched with its repository, it creates a git branch in the repo for each minor version
* Support for git commit messages and description integrated with a Digibee pipeline capsule
* Support for git merge according the configuration of a Digibee pipeline capsule
* When synching a pipeline the README.md is automatically created with a full pipeline tree inside of it  
* When synching a pipeline a docs folder is automatically created with the full pipeline structure
* The main interface now indicates the realm and account that is currently configured on digibeectl
* Pipelines with the same name but with different major versions are treated differently and can be binded with its own git repo
* Pipelines with the same name but in different realms treated according the realm that is configured on digibeectl
* A new option -t can be used to show a full pipeline tree for an already synched pipeline
* The option to deploy (-d) the script on the system was changed to install (-i)
* The help was updated to support the new options
* The -c now checks for other dependencies like jq and tree in addition to git and digibeectl  

# Disclaimer

This script is not developed, maintained or supported by [Digibee](https://www.digibee.com). It works by automating some tasks that can be done purelly with [Digibeectl Official Documentation](https://intercom.help/godigibee/en/articles/5214735-digibeectl-use-guide) and Git Tools.

## License

See the [LICENSE](LICENSE.md) file for license rights and limitations (MIT).

## Synchronizing Digibee Pipelines with Git: An Essential Integration for CI/CD

### Introduction

Digibee is a cloud-native, low-code integration platform that enables enterprises to automate and streamline their business processes. A key feature of Digibee is its pipeline-based approach to integration, where pipelines represent end-to-end workflows that connect applications, data sources, and other systems.

However, as with any software development process, it is, sometimes, important to have an external version control and continuous integration/continuous deployment (CI/CD) in place to ensure that changes made on pipelines are tracked effectively, approved and deployed consistently. This is where the integration with Git comes in.

### Why Synchronize Digibee Pipelines with Git?

There are several reasons why synchronizing Digibee pipelines with Git is important:

1. Version Control
Although Digibee's platform provides developers with an excelent version control management, integrating it with Git can give that extra-layer of governance. This approach gives developers with a granullar and powerful sub-version control system that allows teams to follow the changes to their pipelines flowSpecs over time. By synchronizing Digibee pipelines flowSpec with Git, teams can track changes to their integrations, including who made the changes, when they were made, and what changes were made.

This is especially important when working with large, complex integrations, where multiple team members may be making changes to the pipelines. Having a centralized repository for all pipeline changes can help prevent conflicts and ensure that changes are made in a controlled, organized manner.

2. CI/CD Integration
Finally, synchronizing Digibee pipelines with Git enables teams to integrate their pipelines with CI/CD tools like Jenkins, CircleCI, or Travis CI. By triggering pipeline runs automatically whenever changes are pushed to the Git repository, teams can ensure that their integrations are continuously tested and deployed.

This can help catch errors and issues early on in the development process, reducing the risk of bugs or downtime in production.

### Conclusion

In conclusion, synchronizing Digibee pipelines with Git is a good practice for any team using Digibee low-code platform to write integration code and have some kind of Git platform supporting its CI/CD strategy needs. By leveraging Git's version control, collaboration, and CI/CD integration capabilities, teams can ensure that their integrations are managed effectively and deployed consistently.

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
dgb-gs -a digibee-pipeline-name -v pipeline-major-version
```
8) List the configured pipelines 
```
dgb-gs -l
```
9) Bind a digibee configured pipeline (check the list name) with its respective repo. PS: The pipeline must exist on the realm 
```
dgb-gs -b pipeline-config-name git@bitbucket.org:arturscheiner/pipeline-repo-name.git
```
10) Sync a digibee pipeline with its respective repo. PS: The pipeline must exist on the realm
```
dgb-gs -s digibee-pipeline-name -v pipeline-major-version
```
11) Also, you can watch a digibee pipeline for changes to sync it whenever the "save" button is pressed on the screen
```
dgb-gs -w digibee-pipeline-name -v pipeline-major-version
```
12) Get some HELP
```
dgb-gs -h
```
```
Help Information

Syntax: dgb-gs [-a|l|r|s|c|d|h] params

about pipeline stuff
a	Add a new pipeline to the available list
	E.g. -> dgb-gs -a pipeline-name -v pipeline-major-version

b	Bind a pipeline from the available list with a git repo
	E.g. -> dgb-gs -b pipeline-config-name git@bitbucket.org:arturscheiner/pipeline-repo-name.git

l	List all the pipelines available and binded
	E.g. -> dgb-gs -l

r	Remove a pipeline from the configured git sync list
	E.g. -> dgb-gs -b pipeline-name -v pipeline-major-version

s	Sync a configured pipeline with its git repo
	E.g. -> dgb-gs -s pipeline-name -v pipeline-major-version

t	Show a configured and synched pipeline's tree
	E.g. -> dgb-gs -t pipeline-name -v pipeline-major-version

w	Watch and sync when a pipeline changes
	E.g. -> dgb-gs -w pipeline-name -v pipeline-major-version

about this script
c	Check this script deployment
	E.g. -> dgb-gs -c

about anything else
h	Show this help information
	E.g. -> dgb-gs -h
```

### Obs: This option just shows, when running ./dgb-gs inside the repo cloned folder.

```
about this script
i   Install this script into a directory
	E.g. -> sudo ./dgb-gs -i /usr/local/bin
```