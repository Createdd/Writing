# How I set up my new Macbook Pro for programming and data science

![](https://lh3.googleusercontent.com/xsCpYJtJp1CQYsq42j2usmWAuSypRij7m52-89VkQ0a23kBdnE0ndrk79C6T6YmRZ9WEPTOA7muWu9HYXmGRwu3x0piyqXNuVZz7Bg=w600)


*AI created art by Author. [See on Opensea as NFT](https://opensea.io/accounts/createdd?ref=0xc36b01231a8f857b8751431c8011b09130ef92ec) inspired by [Peter Herrmann](https://unsplash.com/@tama66)*

# Table of Contents

- [How I set up my new Macbook Pro for programming and data science](#how-i-set-up-my-new-macbook-pro-for-programming-and-data-science)
- [Table of Contents](#table-of-contents)
- [Intro](#intro)
- [Software to install and why](#software-to-install-and-why)
  - [Rectangle - Arranging windows](#rectangle-arranging-windows)
  - [iTerm and zsh - terminal and shell](#iterm-and-zsh-terminal-and-shell)
    - [iterm - better terminal](#iterm-better-terminal)
    - [zsh - better shell](#zsh-better-shell)
  - [Brew - Installing packages](#brew-installing-packages)
  - [VS Code](#vs-code)
  - [oh-my-zsh -> plugins for zsh](#oh-my-zsh---plugins-for-zsh)
    - [themes](#themes)
    - [syntax highlighting for terminal](#syntax-highlighting-for-terminal)
    - [autocomplete for terminal](#autocomplete-for-terminal)
  - [Data science related](#data-science-related)
    - [Anaconda](#anaconda)
    - [Tableau](#tableau)
  - [Pycharm for Data Science work](#pycharm-for-data-science-work)
  - [Github](#github)
  - [Other](#other)
    - [Microsoft Office](#microsoft-office)
- [OS related](#os-related)
  - [Nightshift](#nightshift)
  - [Dock](#dock)
- [Wrap up](#wrap-up)
- [Disclaimer](#disclaimer)
- [About](#about)

# Intro

Every time I am getting a new Macbook I go over the same steps on how to set it up for my working experience. I thought I will gather my thoughts and show the applications I install in order to get the most out of my working setup.
I use a Macbook Pro. You could use some of the tips and thoughts for a Windows setup as well, however, I focus on Mac. The reason for that is that I have worked with both systems and I found Mac always easier to use.


# Software to install and why

## Rectangle - Arranging windows

First, I will install [Rectangle](https://rectangleapp.com/)

![](https://user-images.githubusercontent.com/13651296/101402672-57ab5300-38d4-11eb-9e8c-6a3147d26711.png)
From official docs;Screenshot by author


The reason for that is to re-arrange window size with key shortcuts. It doesn't matter which desktop setup I am on. Multiple monitors, docking station, etc. I always need shortcuts for arranging windows. Either to the side, centering or maximizing them in the current virtual desktop.

After installing it, simply add its accessibility within the security & privacy setting. And then you can use it.


## iTerm and zsh - terminal and shell

### iterm - better terminal

[iTerm2](iterm2.com) - macOS Terminal Replacement


![](https://iterm2.com/img/screenshots/split_panes.png)
From official docs; Screenshot by author



iTerm is basically a better terminal with configurable options. A list of features can be found on their official docs: https://iterm2.com/features.html 

Then, I change a few settings:
1. in General > Closing: I remove the confirmation of closing iTerm. It always blocks a restart and I didn't have any usecase that the confirmation saved anything. 
1. in Appearance > Panes: I change the margins to both of value 60. This makes everything more readable.
1. in Profiles > General: I create my own profile and change the working directory to "Reuse previous session's directory to avoid starting from the home directory all the time. 
1. in Profiles > Colors: I change the background color to be dark blue
1. in Profiles > Window: I add Transparency and Blur
1. in Profiles > Keys > Key Mappings: I replace the standard ones with the preset "Natural Text Editing" to use the command and control keys the way I would with any other editor

Feel free to explore more options!

### zsh - better shell

![](https://ohmyz.sh/img/themes/eastwood.jpg)

https://ohmyz.sh; from official docs; Screenshot by author



You can find an overview of the Plugins here: https://github.com/ohmyzsh/ohmyzsh/wiki/Plugins-Overview 

Follow the official guide for installing it.
Simply type
 `$ sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"`
 into your terminal.

And that's it for now.

## Brew - Installing packages

[Homebrew](https://brew.sh/) is "the Missing Package Manager for macOS (or Linux)."

Simply follow their installation guide 
pasting
`/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"`
into the terminal

After that, make sure to also execute the two commands mentioned terminal, namely `echo 'eval ....` and `eval " ...` which exports the bin into your PATH. You will need this to execute the `brew` command through the terminal.


## VS Code

![](https://code.visualstudio.com/assets/blogs/2021/10/20/vscode-dev.png)
From official blog: https://code.visualstudio.com/blogs/2021/10/20/vscode-dev, from official docs; Screenshot by author

I always use VS Code as my lightweight editor of choice. It has so many options to be customized and in its basic form is one of the best environments for dealing with code.

It can be customised and powered up with multiple (open source) extensions:
In 2017 I wrote an article about my favorite extensions. Feel free to check it out as well -> https://medium.com/free-code-camp/favorite-vs-code-extensions-2017-786ea235812f


I also use pycharm for developing most of my code, yet I still use VS Code as my alternative. Sometimes I just want to change a few files without the whole pycharm initialization. That's when I use VS Code. Also for markdown writing. Like I do with my articles.


After downloading VSCode and putting it in the applications folder, open the command palette with the Keyboard Shortcut: `⇧⌘P` and select `"Install 'code' command in PATH"`. This way you can open files by just typing the pre-fix code in your terminal. We will use it in the next step.

## oh-my-zsh -> plugins for zsh

![](https://ohmyz.sh/img/themes/nebirhos.jpg)
https://ohmyz.sh/, from official docs; Screenshot by author



### themes

There are multiple themes you can choose from: https://github.com/ohmyzsh/ohmyzsh/wiki/Themes

I always use robbyrussell

![](https://user-images.githubusercontent.com/49100982/108254738-764b8700-716c-11eb-9a59-4deb8c8c6193.jpg)
From official docs; Screenshot by author


It is straightforward and gives me all the info I need when working with my code. This is set by default. However, if you want to change it or have a look in the file follow the instructions.


For setting the theme I refer to the docs:
> In order to enable a theme, set ZSH_THEME to the name of the theme in your ~/.zshrc, before sourcing Oh My Zsh; for example: ZSH_THEME=robbyrussell If you do not want any theme enabled, just set ZSH_THEME to blank: ZSH_THEME=""
Therefore I just type in code ~/.zshrc which opens my zsh config file in vs code.


Restarting iTerm afterwards reloads your theme and it should look like in the screenshot:
![](https://user-images.githubusercontent.com/49100982/108254738-764b8700-716c-11eb-9a59-4deb8c8c6193.jpg)
From official docs; Screenshot by author

### syntax highlighting for terminal

> This package provides syntax highlighting for the shell zsh. It enables highlighting of commands whilst they are typed at a zsh prompt into an interactive terminal. This helps in reviewing commands before running them, particularly in catching syntax errors.

![](../assets/setupNewMac_2022-02-23-18-24-52.png)
From official docs; Screenshot by author



For installing it just follow the install guide:
[zsh-syntax-highlighting/INSTALL.md](https://github.com/zsh-users/zsh-syntax-highlighting/blob/master/INSTALL.md)


We do that by downloading `zsh-syntax-highlighting` from
`git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting`

and add it to the plugins list in the `.zshrc file`.

Restarting the iterm or opening a new session and you are ready to go.

### autocomplete for terminal

![](https://github.com/marlonrichert/zsh-autocomplete/raw/main/.img/file-search.gif)
https://github.com/marlonrichert/zsh-autocomplete, from official docs; Screenshot by author


> It suggests commands as you type based on history and completions.

Again, for installing, simply follow the instructions in their docs: https://github.com/zsh-users/zsh-autosuggestions/blob/master/INSTALL.md

`git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions`

and add it to the plugins section in your zshrc file.

Restarting the iterm or opening a new session and you are ready to go.

## Data science related

### Anaconda

-> www.anaconda.com

Main reason for this installation is its package management system. For most things and proof of concepts this is a fantastic starter for creating a proper environment for your data science related work. Especially managing it with different python versions it can be a life saver. I tried multiple other approaches and until now Anaconda is still the least pain for managing environments/packages.

You can just download the version for your desired OS with their provided installer package.

### Tableau

When my team uses Tableau and desktop license is bought, I install the Tableau Desktop version for doing most of my Tableau workbooks. Reason for this is that to this day of writing, Tableau Server still lacks some crucial functions for handling big Business Intelligence Analysis. The desktop versions are pricy though in my opinion. Nevertheless a good product.

## Pycharm for Data Science work

![](https://www.jetbrains.com/pycharm/img/screenshots/simpleLook@2x.jpg)

From official docs; Screenshot by author

Check out their official homepage to browse through the reasons why it is a good fit for your needs: https://www.jetbrains.com/pycharm/

The reason for using Pycharm by Jetbrains is that it showed me throughout my work experience that this is the best all-in-one solution for dealing with larger data science projects. Even though you can customize VS code to be usable for large projects as well, I think that Pycharm still has an edge over the others.

The datagrip extension for connecting with databases and handling queries is a blast to use and makes my life much easier.

Everything from debugging, structuring project, executing code etc., comes to the best experience you can get currently. I not only deals with the database part but also allows for webdevelopment integration and other things like jupyter notebooks. I still use jupyter notebook for my detailed exploration code (check out my [article on juypter notebooks](https://towardsdatascience.com/jupyter-notebook-or-lab-or-vs-code-b772f8388911?source=user_profile---------0-------------------------------)), but overall this is my go-to software and a must-have on my programmer laptop.

## Github
For working with Github it is great to install the Github CLI.

Follow the instructions on their docs. Install it with brew by simply executing `brew install gh` 
Before cloning a repo, you would need to set up authentication. This is done via `gh auth login`. Simply follow all instructions.
Then you can clone gh repositories directly with `gh repo clone REPO_NAME`
 

## Other
### Microsoft Office
Main reason for using microsoft office is Excel. Excel is used so often by so many companies and is still unmatched in terms of functionality. As clients ofter send excel sheets with various functions within, I also need to use Excel as well. 
More about it on the official docs: https://www.microsoft.com/en/microsoft-365 

# OS related

## Nightshift

Years ago I used various software to help me reduce blue light on my computer screen. Nowadays you can easily use macOS nigh shift functionality.


Read about it here: https://support.apple.com/en-us/HT207513


In essence, it makes your screen more "orange" in the nighttime. The reason for this are studies that showed that blue light can hinder good sleep. As many programmers work into the night, this was a game-changer for me. It helped me quite a bit. That's why I set it always to on and put it to as much warmth tone as possible. For a designer that wouldn't work but for a programmer that is not an issue. Simply be aware of the stronger orange tone.


## Dock

When getting a new Mac, you will have the Dock on the bottom of the screen with lots of trash applications. So, what I do is
Remove all the unnecessary things. I remove everything except apps that I use on a frequent basis. Like pycharm, iterm, chrome, finder. That's it. Since the spotlight feature was introduced with mac there is no need for any apps lying around in the Dock. it just clutters the view
Move the Dock to the right side. The modern screens are always longer than higher. We do not want to lose more space in height due to this Dock bar
Auto-hide the Dock. As I said, we do not want to lose screen size.

# Wrap up
That's it. This is my setup for every Macbook I start using for my (coding) work. Apart from these changes there are of course various setting changes for specific software, but those shall be addressed in another article. Leave some claps if you liked the article and comment if you have any remarks.




# Disclaimer

I am not associated with any of the services I use in this article.

I do not consider myself an expert. I merely document things besides doing other things. Therefore the content does not represent the quality of any of my professional work, nor does it fully reflect my view on things. If you have the feeling that I am missing important steps or neglected something, consider pointing it out in the comment section or get in touch with me.

This was written on **23.02.2022**.
I cannot monitor all of my articles. There is a high probability that when you read this article the tips are outdated and the processes have changed.

I am always happy for constructive input and how to improve.


---

# About

Daniel is an artist, entrepreneur, software developer, and business law graduate. His knowledge and interests currently revolve around programming machine learning applications and all their related aspects. To the core, he considers himself a problem solver of complex environments, which is reflected in his various projects.


![You can support me on https://www.buymeacoffee.com/createdd](/2020/assets/template_2020-09-25-22-32-52.png)
You can support me on https://www.buymeacoffee.com/createdd or with crypto https://etherdonation.com/d?to=0xC36b01231a8F857B8751431c8011b09130ef92eC


![picture of myself](https://avatars2.githubusercontent.com/u/22077628?s=460&v=4)

**Connect on:**

- [Allmylinks](https://allmylinks.com/createdd)

Direct:
- [LinkedIn](https://www.linkedin.com/in/createdd)
- [Github](https://github.com/Createdd)
- [Medium](https://medium.com/@createdd)
- [Twitter](https://twitter.com/_createdd)
- [Instagram](https://www.instagram.com/create.dd/)
- [createdd.com](https://www.createdd.com/)

Art-related:
- [Open Sea](https://opensea.io/accounts/createdd?ref=0xc36b01231a8f857b8751431c8011b09130ef92ec)
- [Instagram/art_and_ai](https://www.instagram.com/art_and_ai/)
- [Rarible](https://app.rarible.com/createdd/collectibles)
- [Known Origin](https://knownorigin.io/profile/0xC36b01231a8F857B8751431c8011b09130ef92eC)
- [Medium/the-art-of-art](https://medium.com/the-art-of-art)
- [Devian Art](https://www.deviantart.com/createdd1010/)

<!-- Written by Daniel Deutsch -->


