Install Anaconda for Python 2.7 and Windows 64-bit
Install [Git for Windows](http://www.git-scm.com/download/win)
Accept the defaults for everything except the one that asks about installing linux tools (bash) we definitely want to override Windows commands with the git-bash commands.

Find `Git Bash` under `Git` in `All Programs` and launch it. Pin it to your taskbar, desktop, and/or Start Menu. Right-click those icons to select `Properties` then `Advanced...`. That should reveal a checkbox where you can say "Run as Administrator." Make sure it is checked.

Restart `Git Bash` and test it by giving it some basic settings and your user name and password.

```bash
git config --global push.default simple
git config --global user.name "Your Name"
git config --global user.email youremail@gmail.com
```

Install some more python tools to test the anaconda installation.

```bash
conda upgrade ipython
conda install unxutils anaconda-client anaconda-build
```

Set up a folder to place your code in.

```bash
cd ~/
mkdir src
cd src
mkdir huml
cd huml
```

Create an ssh key and upload it to GitHub.com. Hit <kbd>Enter</kbd> whenever prompted for a filename or passphrase to accept the defaults. 

```bash
ssh-keygen
cat ~/.ssh/id_rsa.pub
```

Copy and paste your key using the mouse and <kbd>Ctrl</kbd>-<kbd>Ins</kbd> to copy.  
Go to the settings on your  github profile page in your browse and find SSH Keys on the Left Hand side.  
Use <kbd>Ctrl</kbd>-<kbd>V</kbd> to paste the key into the large text box and give you key a name in the smaller title box.




Use Git Bash (MINGW64) as your client. On Windows7 it is under Start -> All Programs -> Git -> Git Bash


python repl must be launch with winpty to work with MinTTY terminal emulator:

`winpty ipython`

Likewise for other interactive commands like `anaconda login`  
(You only need to run this if you plan to build and upload packages to anaconda.org):

`winpty anaconda login`

To install nolearn and run the iptyhon notebooks from today you'll need to run:

`conda config --add channels https://conda.anaconda.org/hobs`

Unfortunately you may still have to be explicit about the channel when you install:

`conda install --channel https://conda.anaconda.org/hobs theano` 

The release notes for msysgit (git for Windows):

    Special permissions (and Windows Vista or later) are required when cloning repositories with symbolic links, therefore support for symbolic links is disabled by default. Use git clone -c core.symlinks=true <URL> to enable it, see details here.
    If configured to use Plink, you will have to connect with putty first and accept the host key.
    Some console programs interact correctly with MinTTY only when called through winpty (e.g. the Python console needs to be started as winpty python instead of just python).
    cURL uses $HOME/_netrc instead of $HOME/.netrc.

    If you specify command-line options starting with a slash, POSIX-to-Windows path conversion will kick in converting e.g. "/usr/bin/bash.exe" to "C:\Program Files\Git\usr\bin\bash.exe". When that is not desired -- e.g. "--upload-pack=/opt/git/bin/git-upload-pack" or "-L/regex/" -- you need to set the environment variable MSYS_NO_PATHCONV temporarily, like so:

        MSYS_NO_PATHCONV=1 git blame -L/pathconv/ msys2_path_conv.cc

    Alternatively, you can double the first slash to avoid POSIX-to-Windows path conversion.
    Git for Windows will not allow commits containing DOS-style truncated 8.3-format filenames ending with a tilde and digit, such as mydocu~1.txt. A workaround is to call git config core.protectNTFS false, which is not advised. Instead, add a rule to .gitignore to ignore the file(s), or rename the file(s).
    Many Windows programs (including the Windows Explorer) have problems with directory trees nested so deeply that the absolute path is longer than 260 characters. Therefore, Git for Windows refuses to check out such files by default. You can overrule this default by setting core.longPaths, e.g. git clone -c core.longPaths=true ....
    Some commands are not yet supported on Windows and excluded from the installation.
    As Git for Windows is shipped without Python support, all Git commands requiring Python are not yet supported; e.g. git p4.
    The Quick Launch icon will only be installed for the user running setup (typically the Administrator). This is a technical restriction and will not change.

## Compiler

A g++ compiler is sometimes required (like to build the Theano package). Some bullet-proof instructions for getting this installed are [at cmc.edu](http://www1.cmc.edu/pages/faculty/alee/g++/g++.html)


