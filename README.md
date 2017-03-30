# OSX Dev Step Up
## About
This guide is to remind me of what to do after a full format. I will probably automate this in the end, but for now this will track whats required.

### Git
- Install [Homebrew][homebrew]
    - Install git - ``brew install git``
### [Node][node]
- Install [Node][node] using the installer from the [node homepage][node]
- Change the location of global packages to avoid using `sudo` and [3rd party permissions errors][npmBasics]. The following snippets are parapharsed from this [article][npmBasics] and as such are not my work.

    1. `npm config list` - (This gives us information about our install. For now it’s important to get the current global location.)
        ```
        $ npm config list
        ; cli configs
        user-agent = "npm/3.6.0 node/v5.7.0 linux x64"
        
        ; node bin location = /usr/local/bin/node
        ; cwd = /home/sitepoint
        ; HOME = /home/sitepoint
        ; 'npm config ls -l' to show all defaults.
        ```

    2. `npm config get prefix` (This is the prefix we want to change, so as to install global packages in our home directory)
        ```
        $ npm config get prefix
        /usr/local
        ```
    3. `cd && mkdir .node_modules_global`
    4. `npm config set prefix=$HOME/.node_modules_global`
    5. `npm config get prefix` (Check it worked like this)
        ```
        $ npm config get prefix
        /home/sitepoint/.node_modules_global
        ```
    6. `cat .npmrc` (This has also created a .npmrc file in our home directory.)
        ```
        $ cat .npmrc
        prefix=/home/sitepoint/.node_modules_global
        ```
- As the last set of steps changed the location to which global Node packages are installed. We should now take advantage of this and do the same for NPM. To do this we need to install npm again, but this time in the new user-owned location. This will also install the latest version of npm.
    1. `npm install npm --global`
        ```
        $ npm install npm --global
        /home/sitepoint/.node_modules_global/bin/npm -> /home/sitepoint/.node_modules_global/lib/node_modules/npm/bin/npm-cli.js
        /home/sitepoint/.node_modules_global/lib
        └── npm@3.7.5`
        ```
    2. Finally, we need to add `.node_modules_global/bin` to our `$PATH` environment variable, so that we can run global packages from the command line. Do this by appending the following line to your .profile, .bash_profile or .zshrc and restarting your terminal.
        - `export PATH="$HOME/.node_modules_global/bin:$PATH"`
        - `source ~/.zshrc` OR `source ~/.bash_profile`
    3. Now our .node_modules_global/bin will be found first and the correct version of npm will be used.
        ```
        $ which npm
        /home/sitepoint/.node_modules_global/bin/npm
        $ npm --version
        3.7.5
        ```
### Terminal
- Install [iTerm2][iterm2]
- Install [oh my zsh][ohmyzsh]
- Set up [theme][wesBosItermTheme]

### Text Editor
- Install [Sublime Text 3][sublime]
- Install [Package Manager][sublimePackageManager]
- Install Sublime Text plugins
    - [Side Bar Enhancements][sideBarEnhancements]
    - [Git][git]
    - [GitGutter][gitGutter]
    - [Emmet][emmet]
    - [All auto complete][allAutocomplete]
    - [Color picker][colorPicker]
    - [Markdown Preview][markdownPreview]
    - [Doc Blocker][jsdocs] 
    - [Pug][pug]
    - [Stylus][stylus]
    - [JSX][jsx]
    - [ESlint][eSLint]
    - [Babel][babel]
    - [Sublime Linter][SubLint]
    - [SublimeLinter- JSON][SubLintJson]
    - [SublimeLinter- JSCS][SubLintJscs]
    - [SublimeLinter - JS Hint][SubLintJshint] (if using eslint dont need this, its an either or)
    - [SublimeLinter-JSX Hint][SubLintJsxHint]
- Install Sublime Text Theme
    - [Oceanic Next Color Scheme][oceanicNextColorScheme] (Works well with React)

### Browsers
- Install [Chrome][chrome]
- Install [Firefox][firefox]

### Productivity tools
- Install [Alfred][alfredapp]
- Install [Caffine][caffine]
- Install [Cold Turkey][coldturkey]
- Install [Tomighty][tomighty]
- Install [Spectacle][spectacle]

### Video Player
- [VLC][vlc]

[homebrew]: <https://brew.sh/>
[node]: <https://nodejs.org/en/>
[npmBasics]: <https://www.sitepoint.com/beginners-guide-node-package-manager>
[iterm2]: <https://www.iterm2.com/>
[ohmyzsh]: <https://github.com/robbyrussell/oh-my-zsh>
[wesBosItermTheme]: <https://github.com/wesbos/Cobalt2-iterm>
[sublime]: <https://www.sublimetext.com/3>
[sideBarEnhancements]:<https://packagecontrol.io/packages/SideBarEnhancements>
[git]: <https://github.com/kemayo/sublime-text-git>
[gitGutter]: <https://github.com/jisaacks/GitGutter>
[emmet]: <https://emmet.io/>
[allAutocomplete]:<https://github.com/alienhard/SublimeAllAutocomplete>
[colorPicker]: <http://weslly.github.io/ColorPicker/>
[markdownPreview]: <https://github.com/revolunet/sublimetext-markdown-preview>
[jsdocs]: <https://github.com/spadgos/sublime-jsdocs>
[pug]: <https://packagecontrol.io/packages/Pug>
[jsx]:<https://packagecontrol.io/packages/JSX>
[stylus]: <https://packagecontrol.io/packages/Stylus>
[babel]: <https://packagecontrol.io/packages/Babel>
[SubLint]: <https://packagecontrol.io/packages/SublimeLinter>
[SubLintJson]: <https://packagecontrol.io/packages/SublimeLinter-json>
[SubLintJscs]: <https://packagecontrol.io/packages/SublimeLinter-jscs>
[SubLintJshint]: <https://packagecontrol.io/packages/SublimeLinter-jshint>
[SubLintJsxHint]: <https://packagecontrol.io/packages/SublimeLinter-jsxhint>
[eSLint]:<https://packagecontrol.io/packages/ESLint>
[oceanicNextColorScheme]: <https://github.com/voronianski/oceanic-next-color-scheme>
[chrome]: <https://www.google.co.uk/chrome/browser/features.html?brand=CHBD&gclid=Cj0KEQjwtu3GBRDY6ZLY1erL44EBEiQAAKIcvp8xCkyYpQ3nUTH7-Spuo7rZFZ5cOjjH2ii5EdmieUMaApHr8P8HAQ>
[firefox]: <https://www.mozilla.org/en-US/firefox/new/?utm_source=google&utm_medium=paidsearch&utm_campaign=Brand-UK-EN-GGL-Exact&utm_term=firefox%20for%20mac&utm_content=A144_A203_A006272&gclid=Cj0KEQjwtu3GBRDY6ZLY1erL44EBEiQAAKIcvsbOWDbcHyl4yfp23S0DPPl2sN45_JFp_mu0VJq1Mf4aAm758P8HAQ&gclsrc=aw.ds>
[alfredapp]: <https://www.alfredapp.com/>
[caffine]: <https://caffeine.en.softonic.com/mac>
[coldturkey]: <https://getcoldturkey.com/>
[tomighty]: <http://tomighty.org/>
[spectacle]:<https://www.spectacleapp.com/>
[sublimePackageManager]: <https://packagecontrol.io/installation>
[vlc]:<http://www.videolan.org/vlc/index.html>