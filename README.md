<p align="center">
  <img width="351" height="281" src="https://techladies.co/illustrations/Illus_astronaut.png">
</p>

## Prerequisite

### [Chrome](https://www.google.com/intl/en_sg/chrome/)
The default web browser

### [GitHub](https://github.com/signup?ref_cta=Sign+up&ref_loc=header+logged+out&ref_page=%2F&source=header-home)
Create an account with GitHub

## macOS 

### 1. [Xcode](https://apps.apple.com/us/app/xcode/id497799835?mt=12)
This will also automatically install [Git](https://git-scm.com/) on your machine

Run the following command in your terminal to verify
```bash
git --version 
```

### 2. [Homebrew](https://brew.sh/)
Paste the following inside your terminal shell prompt.
```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```
After installing, run the following to verify that you have homebrew installed
```bash
brew -v
```

### 3. [Node.js](https://nodejs.org/en/download/)
Download the LTS (long-term support) version

<img width="257" alt="Screenshot 2021-07-23 at 8 55 55 PM" src="https://user-images.githubusercontent.com/56812343/126784598-685d21f2-1936-4dd2-b6f5-3c6755e2201a.png">

To verify that you have successfully installed Node.js run the following in your terminal
```bash
node -v
npm -v
```

### 4. [PostgresSQL](https://www.enterprisedb.com/downloads/postgres-postgresql-downloads)
We'll be using the interactive installer by EDB which includes the PostgreSQL server & pgAdmin; a graphical tool for managing and developing your databases.

<img width="1081" alt="Screenshot 2021-07-24 at 10 54 35 AM" src="https://user-images.githubusercontent.com/56812343/126855522-2455d69d-102f-4453-b91a-9a9ec04494bd.png">

To verify that PostgresSQL has been installed, run the following command in your terminal
```bash
psql
# it should output the following:
# psql (13.3)
# Type "help" for help.
```
To exit psql, run
```bash
\q
```

## Windows

### 1. [Git for Windows](https://github.com/git-for-windows/git/releases/tag/v2.32.0.windows.2)
Git for Windows is a lightweight, native set of tools that brings [Git SCM](https://git-scm.com/) to Windows.

Read more about it [here](https://gitforwindows.org/)

Once installed it comes with 3 useful features
- Git BASH
- Git GUI
- Shell Integration

If you are using **32-bit**, click on `Git-2.32.0.2-32-bit.exe`(47.4MB) 

If you are using **64-bit**, click on `Git-2.32.0.2-64-bit.exe`(47.6MB)

<img width="979" alt="Screenshot 2021-07-24 at 10 20 46 AM" src="https://user-images.githubusercontent.com/56812343/126854847-3e0d3e3c-6ba0-4473-9f6b-83de0fc4f7a0.png">

To verify the installation, go to `Start -> Git Bash` and run the following command
```bash
git --version
```

### 2. [PostgresSQL](https://www.enterprisedb.com/downloads/postgres-postgresql-downloads)
We'll be using the interactive installer by EDB which includes the PostgreSQL server, pgAdmin; a graphical tool for managing and developing your databases.

<img width="909" alt="Screenshot 2021-07-24 at 10 02 08 AM" src="https://user-images.githubusercontent.com/56812343/126854485-4a2def77-cf90-435d-906f-be47f7da5c10.png">

To verify that PostgresSQL has been installed, run the following command in your Git Bash window
```bash
psql
# it should output the following:
# psql (13.3)
# Type "help" for help.
```

To exit psql, run
```bash
\q
```

### 3. [Node.js](https://nodejs.org/en/download/)

<img width="982" alt="Screenshot 2021-07-24 at 10 08 02 AM" src="https://user-images.githubusercontent.com/56812343/126854572-075778e7-e0e5-49de-b359-cc31b4a0a450.png">

> **Note:** you should first close and restart the Git Bash window so that the Node.js installation can take effect

To see verify if Node.js & npm is installed, open a Git Bash window and type in the following

```shell
node --version
# Prints version number v14.17.3.
```
```shell
npm --version
# Prints version number v6.14.13
```

<details>
<summary><b>(ALTERNATIVE) Windows using WSL</b></summary>

## Windows Subsystem for Linux

A **64-bit** version of Windows 10 is necessary here if you want to use the Windows Subsystem for Linux (WSL). 

You can check whether your version of Windows 10 is **64-bit** by going to `Settings -> System -> About` and looking under the `System type` field.

### 1. [WSL 2](https://docs.microsoft.com/en-us/windows/wsl/install-win10#manual-installation-steps)

This might take a while (??????<???)

We'll be going through the manual installation steps unless you're in the [Windows Insiders Program](https://insider.windows.com/getting-started)

### 1.1 Symlinking a Windows workspace folder into your WSL home

> **WARNING**: Your WSL files are stored in a separate file system managed by WSL with a different, stricter and more fine-grained permission system than Windows. You should never edit any WSL files from Windows itself, as there is a non-trivial risk of corrupting your entire WSL installation. However, editing Windows files from WSL is perfectly fine. Thus, we can integrate the two systems (WSL and Windows) by making sure that your working folders live in Windows and are conveniently accessible from WSL

1. Create a `projects` folder from your Windows user account home directory. For example, go to `C:\Users` in Explorer and go into the folder corresponding to your user name. Create a folder named `projects` here. For example, if your home directory is `C:\Users\Bobby`, create the directory `C:\Users\Bobby\projects`. All projects should be created in this folder so that you can safely browse or edit the files from both WSL and Windows.
2. Next, symlink it by opening a WSL window and running the following commands in order
```bash
cd ~
```
```shell
ln -s /mnt/c/Users/Bobby/projects ./projects
```
3. From now on, you will be able to access the projects folder in your WSL installation as if it were a directory in it.

### 2. Git
Run the following commands in order in a WSL terminal.
```bash
sudo apt install git
```

This will cache your git credentials for a short time after you enter it.
```bash
git config --global credential.helper cache
```

### 3. [Node.js](https://docs.microsoft.com/en-us/windows/dev-environment/javascript/nodejs-on-wsl)
> It is always recommended to remove any existing installations of Node.js or npm from your operating system before installing a version manager as the different types of installation can lead to strange and confusing conflicts. For example, the version of Node that can be installed with Ubuntu's apt-get command is currently outdated. 

### 4. PostgresSQL

#### Installation
Open a WSL terminal and run the following command
```bash
sudo apt-get install postgresql-client postgresql postgresql-contrib postgresql-client-common
```

#### Configuration
You will need to configure a user for your Postgres database. Run the following command
```bash
sudo -u postgres psql postgres
```
```bash
\password postgres
```

> Remember to choose an **easy** password, preferably write it down on a piece of paper and then type `\quit` to exit psql

To make it easier to start postgres we're going to create a couple aliases. Edit your bashrc file by typing `subl ~/.bashrc` add these lines to the bottom of the file:
```bash
alias psql="sudo -u postgres psql"
alias pgserver="sudo -u postgres service postgresql start"
```

- `pgserver` to start the postgres server
- `psql` to access the psql termainal

#### Testing

Remember to quit your terminal and reopen it before testing.

```bash
# Starts the server
pgserver
```
```bash
# Enters the psql terminal
# At this stage, you should enter the psql terminal without any error.
psql
```
```pgsql
# Exists psql
\q
```

#### (Optional) Passwordless Postgres
Set no-password on postgres for your computer, so that it's easier to work with.

Edit the postgres configuration file by typing in the following command
```bash
sudo sublime /etc/postgresql/POSTGRE_VERSION/main/pg_hba.conf
```

Change all configuration access to the following:
```
 # Database administrative login by Unix domain socket
 local   all             all                                     trust

 # TYPE  DATABASE        USER            ADDRESS                 METHOD

 # "local" is for Unix domain socket connections only
 local   all             all                                     trust
 # IPv4 local connections:
 host    all             all             127.0.0.1/32            trust
 # IPv6 local connections:
 host    all             all             ::1/128                 trust
```

After you have done that, restart the postgres server by typing in 
```bash
sudo /etc/init.d/postgresql restart
```

*credit to [Akira's](https://github.com/awongh) [gitbook](https://wdi-sg.github.io/gitbook-2019/00-config-deployment/installfest/windows/readme.html) back when I was in GA for the resources*
 
</details>

## Optional

### 1. [Visual Studio Code](https://code.visualstudio.com/)
- [Bracket Pair Colorizer](https://marketplace.visualstudio.com/items?itemName=CoenraadS.bracket-pair-colorizer)
- [ES7 React/Redux/GraphQL/React-Native snippets](https://marketplace.visualstudio.com/items?itemName=dsznajder.es7-react-js-snippets)
- [Highlight Matching Tag](https://marketplace.visualstudio.com/items?itemName=vincaslt.highlight-matching-tag)
- [Prettier](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode)
- [ESLint](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint)
