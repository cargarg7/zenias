# FreeCodeCamp - Zeus

[![Join the chat at https://gitter.im/FreeCodeCamp/vagrant](https://badges.gitter.im/Join%20Chat.svg)](https://gitter.im/FreeCodeCamp/vagrant)

## Table of Contents
- [What is Zeus](#what-is-zeus)
- [Current Version](#current-version)
- [How to Use](#how-to-use)
   - [Basic Requirement](#basic-requirement)
   - [Clojure](#clojure)
   - [Java](#java)
   - [Node](#node)
   - [PHP](#php)
   - [Python](#python)
   - [Ruby](#ruby)
- [Motivation](#motivation)
- [Features and Packages](#features-and-packages)
  - [Individual Boxes](#individual-boxes)
  - [Common Features](#common-features)
- [Contributing Guidelines](#contributing-guidelines)
- [Frequently Asked Questions](#frequently-asked-questions)
- [License](#license)

## What is Zeus

_Zeus_ is a CLI tool that creates a platform-independent [Vagrant](https://www.vagrantup.com) development environment.

Presently, we support creating Ubuntu 14.04 LTS environment with these stacks:
- Clojure-Compojure-Leiningan
- Node-Express
- Java 1.8-Tomcat-Maven-Gradle
- PHP-CakePHP
- Python-Django
- Ruby-Rails

In all of the above, PostgreSQL 9.3 is present and configured for use as Database, except for the Node and Express stack; where MongoDB has been provided.

## Current Version

Present version of this project stands at 1.0.0. We use Semvar based versioning.

## How to Use

### Basic Requirement

You need to install **latest** (version 5.0.20) [Virtualbox](https://www.virtualbox.org/wiki/Downloads), its compatible Virtualbox [Extension pack](https://www.virtualbox.org/wiki/Downloads) for USB 2.0 support; and **latest** (1.8.1) [Vagrant](https://www.vagrantup.com/downloads.html) itself.

If you are on Windows, you need [Git Bash](https://git-scm.com/downloads). On other platforms, like Linux or MacOSX; you would require having [git](https://git-scm.com/downloads) installed in your machine. On Windows, you might need to restart your machine after Vagrant installation.

Once you have installed these, you can choose to boot up one of the following environments. In future, we plan on installing the basic requirements as part of `zeus` as well.

### Clojure

### Java

In the Java box we have provided the following packages :

* Java 8 - v1.8
* Maven 3
* Gradle 2
* Tomcat 8

Additionally, Postgres database has been setup.

Tomcat server is set to auto-start on port 8080. Now in this box, the port 8080 is mapped with Host, i.e your machine's port 9100. Thus, run anything on the tomcat server and it would be accessible on your machine in the address [http://localhost:9100](http://localhost:9100)

### Node

In Node box we have provided the following packages :

* [MongoDB](https://www.mongodb.com/) 3.0 server and client
* [NVM](https://github.com/creationix/nvm) or Node Version Manager
* [Node](https://nodejs.org) version 4.4.3 (Can be easily updated via `nvm install`)
* [Bower](http://bower.io/)
* [Gulp](http://gulpjs.com/)
* [Yeoman](http://yeoman.io/) CLI
* [Express](http://expressjs.com/)
* Essential Nodeschool Workshopper modules
	* [git-it](https://github.com/jlord/git-it)
	* [learnyounode](https://github.com/workshopper/learnyounode)
	* [how-to-npm](https://github.com/npm/how-to-npm)
	* [learnyoumongo](https://github.com/evanlucas/learnyoumongo)
	* [expressworks](https://github.com/azat-co/expressworks)

In vagrant configuration, the port 3000 is mapped with guest port 9200. Thus, if you start an express app on port 3000, you can access it via the address [http://localhost:9200](http://localhost:9200)

We have also included a sample [Todo app](https://github.com/tastejs/todomvc/tree/master/examples/socketstream/) with Socket Stream, built by the awesome guys at [TodoMVC](https://github.com/tastejs/todomvc). To run it, do the following :

```bash
cd /vagrant # navigate to shared vagrant folder
cd socketstream
npm install
bower install
npm start
```

Now open [http://localhost:9200](http://localhost:9200) in your browser and voila! The todo app is working!

### PHP

### Python

### Ruby

## Motivation

Zeus is made for students of [FreeCodeCamp](https://freecodecamp.com), who are starting their journey in learning back-end development.

The motivation for this Open Source project is to let users focus more on coding web apps, and less on configuration and set-up.

We expect our vagrant environments running smoothly on most platforms; including Windows, Mac, and Linux. We also aim to reduce the size of the box as much as possible.

## Features and Packages

There are three levels that zeus will change: your local machine, Vagrant VM, and virtualenv within the Vagrant VM. Various features are installed on different levels.

### Individual Boxes

- Each individual box has its own shell-based provisioner. For instance, `java` provisioner is `zeus/java/provision.sh`.
- Each box has a DB, a web framework, a package manager and some nifty tools like `curl`, `git`, `dos2unix` etc.


### Common Features
- All boxes come with pre-installed heroku toolbelt and heroku CLI for easy deployment of apps on heroku.
- All boxes have port forwarding. So, you don't need to know the IP address of a vagrant box - you can simply access the running app inside vagrant via `http://localhost:<port_number>` in your browser.
- All boxes share a workspace with host machine. It allows an end-user to work on their own local IDE.

## Contributing Guidelines
- Do talk to [us](https://gitter.im/FreeCodeCamp/vagrant) before you raise a pull request.
- If you are looking for something to work on, please check our [issues](https://github.com/alayek/zeus/issues?q=is%3Aopen+is%3Aissue+label%3A%22help+wanted%22).
- Vagrant testing takes time, and we intend to support major platforms. If you raise a PR, it might take a day or two for us to test on most platforms. So have patience.
- You can contribute by adding documentation on [FreecodeaCamp Wiki](https://github.com/FreeCodeCamp/FreeCodeCamp/wiki) about this project.
- You can contribute by testing various boxes on new platforms, or existing PRs on common platforms.

## Frequently Asked Questions

### Why Not Docker?

>Docker is not **natively** supported on Windows and Mac. While on Linux, it makes sense to use Docker, on Windows and Mac; one needs lot of extra packages to make Docker work.

>Docker is in no way superior to Vagrant if we are targeting development environment for end user, on their personal laptop or family desktop. We chose to start with Vagrant and the project grew from there. If we get a compelling reason to move to Docker, we would.

### Why are [c9](https://c9.io/) or [Nitrous](https://www.nitrous.io/) not used?

> Cloud 9 and Nitrous are great services, for coding in-browser. They give you a full-fledged terminal with superuser access, among other things. But we are trying to help people get jobs by building a solid back-end or full-stack profile.

> A user needs to be comfortable working on their own machine, outside a browser. A vagrant environment is a great place to start. Once we have a user comfortably working using a vagrant, we can take them through the journey of taking apart their environments, and setting up their own environment.

> We plan on creating some detailed tutorials on these, and an environment in a local machine is a step towards that.

> In a lot of countries, getting good reliable internet is an issue. Power cuts are rampant. If you are from one of those places, you are probably more comfortable working on your local environment offline.

> We acknowledge the benefits of cloud-hosted, browser-interfaced envs like c9 or nitrous. And our tool is complementary to these. In the end, it's the end-user who gets to decide which one they want to use.

### Why shell-script provisioning?

> State-of-the-art provisioners like Chef, Puppet, Ansible, and Salt are there. They work amazingly well, with 100% reliability; and most big and small companies use them internally in their DevOps.

> But, while they are great for provisioning 16 GB CentOS workstations in a team, part of a large MNC, your local Windows 10 with 4 GB RAM would most likely not be able to handle them. You machine would slow down, or would need to download hundreds of files along with the huge plugins. In some cases, even more things to download.

> We started with shell-script as it is lightweight, and it just works. Our setup is not that complex. In our usecase, where we are provisioning personal machines, we found shell script to provision envs the fastest. We have not yet had a reason to move to any of these provisioners; however, if such a need were to arise, we won't think twice before moving to these!

> Shell script can be odd and esoteric at times, but we have figured out solutions to most of the common problems over the course of this project.

> As for reliability, we have test suites, to be executed after a box has been provisioned.

### Why all the `>/dev/null` style output suppressing? Are you hiding something?

> The only thing we are hiding from end-users, is misleading _red-text_ information. We have noticed that, during provisioning, shell script provisioning prints a lot of stuff in red-text, indicating error.

> Those could be something as harmless as download progress, or gpg key fetching, or even _building database of man pages_. In cases like those, we don't want the output and we pipe them to `/dev/null`. However, we do need to know if something went wrong - so we also do `2>&1`, to indicate `STDERR` outputs in `STDOUT`.

> And as mentioned earlier, we have test cases to inspect if the provisioning went fine.

### Why no Continuous Integration, like Travis?

> To be frank, setting up CI is not so straightforward with this. Our requirement is this: _A contributor changes some file(s) and submits a PR. The CI service should pull in the changes and run vagrant provisioning. After the boxes have been provisioned, the test suites are invoked from inside the provisioned from within the boxes to ensure everything is fine._

> As you can see, it requires that a virtual environment be set up inside the environment that CI service is providing you. However, most CI services use some form of virtualization themselves. Like the Docker images Travis use, uses OpenVZ containers.

> Virtual systems within an already-virtual system is kind of tricky, and in most cases not allowed. We did some research, and we are yet to find a solution. However, if you have a workaround, do get in touch with [us](https://gitter.im/FreeCodeCamp/vagrant)!


## License

Continue to our [license](LICENSE).


## Features



[asciinema Tutorial](https://asciinema.org/a/1u9zm99yzpz6v1b95wv6mrppn)

or

[Video Tutorial by John Wu](https://youtu.be/RbQ1qtOVSJc)

### 1. User's Local Machine Level

#### Files

- .gitignore, Vagrantfile, provisioning.sh, README.md, Procfile, requirements.txt, runtime.txt

#### Programmes

[WIP] for the release of Version 0.2.0 (in June) and not within Version 0.1.0:

- Vagrant, Git, VirtualBox, VirtualBox Extension Pack

### 2. Vagrant VM Level

These are system-wide installations within the Vagrant VM:

#### Programmes

- python2.7, python3.4, python-dev, python3-dev, libpq-dev, pip, build-essential, dos2unix, python-pip, man, Git, Heroku toolbelt, Heroku CLI, ruby, virtualenvwrapper, postgresql, Postgresql-contrib
- Custom commands in the command line via zeus. Refer to section "How to Use Zeus" to know what commands are available.

#### Configurations

- Initiate a local git repository inside the synced folder `/vagrant`.
- Initiate a virtualenv every time you perform `vagrant ssh`.
- Create Postgres database and its user.
- Store user configurations and credentials for git, Github, and Heroku.

### 3. Virtualenv Level

#### Programmes

- dj-database-url==0.4.1, Django==1.9.6, django-rest==3.3.3, django-widget-tweaks==1.4.1, gunicorn==19.5.0, psycopg2==2.6.1, whitenoise==3.0

### Vagrant Base-box

Ubuntu 14.04 LTS based box minimal/trusty64, hosted at https://atlas.hashicorp.com/minimal/boxes/trusty64

## How to Use Zeus

### System Requirements

You need to have the following programmes installed on your local machine before you start to use this tool.

- [Virtualbox](https://www.virtualbox.org/wiki/Downloads) latest (currently version 5.0.20)
- [VirtualBox 5.0.20 Oracle VM VirtualBox Extension Pack](http://download.virtualbox.org/virtualbox/5.0.20/Oracle_VM_VirtualBox_Extension_Pack-5.0.20-106931.vbox-extpack), compatible with latest Virtualbox
- [Vagrant](https://www.vagrantup.com/downloads.html), (currently version 1.8.1)
- [Python 2.7](https://www.python.org/downloads/)
- [Git Bash](https://git-scm.com/downloads) (only if you are on Windows)

If you are on Windows, restart your local machine after the installation of these programmes.

### Standard Usage

1. `git clone --recursive https://github.com/alayek/zeus.git`
2. Navigate to the directory of this cloned repo.
`cd your/path/to/zeus/ruby`
3. `vagrant up` in your bash-compliant terminal (Git Bash on Windows, regular terminal on Linux or Mac).
3. Inside the directory `your/path/to/zeus/ruby` run `vagrant ssh` to start the session inside the development VM.
4. Complete Github and git config setup. You only need to login to Github once during your first push and never again. You don't need to authenticate yourself when you perform git commit.
5. Start coding.

Note that you end up inside the Vagrant VM after these four steps. The VM is isolated from your local machine. Your current working directory has the absolute path of `/vagrant`, which is termed the "synced directory". It is in real-time sync with the `your/path/to/fcc-python-vagrant` local git repo. That is how your local machine communicates with the Vagrant VM.

If you run into trouble, hit `zeus help` inside the Vagrant ssh session.

### Zeus CLI

Run these commands within your Vagrant ssh session.

- `zeus gitconfig`
Create or overwrite existing git configuration for the user in terms of username and email address. Git push is set to simple as this is best practice.
- `zeus gitcreate private` or `zeus gitcreate public`
Create a private or public repository on Github via the GitHub API. You need to first have setup your git configurations with `zeus gitconfig` to use this properly. You only need to specify the name you wish to give to the remote repository.


Nota Bene:

<newproject> is the directory you with to create in side which you are going to code your web apps. This is your synced folder in the Vagrant ssh session. All your coding should happen here. If you exit the Vagrant ssh session, you might end up in a different directory. Please navigate to wherever <newproject> is located and start your VM session again with `vagrant ssh`

### Test Your Setup

Optionally, you might wish to test the development environment setup by following these steps:

- Test manually by checking whether all the features we promised are installed inside your Vagrant VM.
- Use `date && vagrant up > logfile.log && date` instead of just `vagrant up` to log all printouts of `vagrant up` into the `logfile.log` with start time and end time of the execution. (The terminal will print nothing during the entire setup, please don't panic, everything is written into the `logfile.log`). Finally, inspect `logfile.log` to ensure no installation error occurred.
- Run vagrant halt and restart with `vagrant up` and `vagrant ssh`. Ensure the state of the VM is the same as before, run another test if necessary.
- Automated testing:

It is assumed that these tests would be run inside the standard virtualenv of the `vagrant ssh` session.

It would require the `py.test` module to run it, which can be installed as:

```bash
$ pip install pytest
```

Then navigate to the top-level directory of the Vagrant synced folder:

```bash
$ cd /vagrant
```

Invoke the automated tests:

```bash
$ py.test -v
```

You should see all tests PASSED and no errors printed.




# Security

The Vagrant VM initiated by zeus stores your GitHub credentials on file. Please do not package this VM and share it. Attempts are made in the future to use HashiCorp Vault to store safely your credentials while not compromising on convenience.
