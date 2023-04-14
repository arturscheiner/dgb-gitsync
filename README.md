# Digibeectl Git Sync

This script allows you easily sync a Digibee pipeline with a git repo

## Synchronizing Digibee Pipelines with Git: An Essential Integration for CI/CD

### Introduction

Digibee is a cloud-native, low-code integration platform that enables enterprises to automate and streamline their business processes. A key feature of Digibee is its pipeline-based approach to integration, where pipelines represent end-to-end workflows that connect applications, data sources, and other systems.

However, as with any software development process, it is important to have version control and continuous integration/continuous deployment (CI/CD) in place to ensure that changes made on pipelines are managed effectively and deployed consistently. This is where Git comes in.

### Why Synchronize Digibee Pipelines with Git?

There are several reasons why synchronizing Digibee pipelines with Git is important:

1. Version Control
Although Digibee's platform provides developers with its own version control management, Git gives that extra-layer allowing a more granullar and powerful sub-version control system that allows teams to manage changes to their pipelines flowSpecs over time. By synchronizing Digibee pipelines with Git, teams can track changes to their integrations, including who made the changes, when they were made, and what changes were made.

This is especially important when working with large, complex integrations, where multiple team members may be making changes simultaneously. Having a centralized repository for all pipeline changes can help prevent conflicts and ensure that changes are made in a controlled, organized manner.

2. Collaboration
Git also enables collaboration between team members, allowing them to work together on the same codebase without stepping on each other's toes. By using Git's branching and merging capabilities, teams can work on different features or fixes in isolation, and then merge their changes back into the main codebase once they are complete.

This can greatly increase productivity and efficiency, as team members can work on their own parts of the integration without interfering with each other's work.

3. CI/CD Integration
Finally, synchronizing Digibee pipelines with Git enables teams to integrate their pipelines with CI/CD tools like Jenkins, CircleCI, or Travis CI. By triggering pipeline runs automatically whenever changes are pushed to the Git repository, teams can ensure that their integrations are continuously tested and deployed.

This can help catch errors and issues early on in the development process, reducing the risk of bugs or downtime in production.

### Conclusion

In conclusion, synchronizing Digibee pipelines with Git is an essential integration for any team using Digibee for their integration needs. By leveraging Git's version control, collaboration, and CI/CD integration capabilities, teams can ensure that their integrations are managed effectively and deployed consistently.

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

### Obs: This option just work when running ./dgb-gs inside the repo cloned folder.

```
about this script
d	Deploy this script into a directory
	E.g. -> sudo ./dgb-gs -d /usr/local/bin
```