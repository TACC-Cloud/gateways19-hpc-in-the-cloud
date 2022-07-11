# Setting Up Your Github Account

To deploy a fork of Tapis UI, there are a few steps that are required for preparing your GitHub account. For this demonstration, we will be using [GitPod](https://gitpod.io), an online IDE. You may sign up for a free account there.
## Forking Tapis UI

You can create your own fork of `tapis-ui`. Browse to the repository at [https://github.com/tapis-project/tapis-ui](https://github.com/tapis-project/tapis-ui). Here, you will see a *Fork* button with a dropdown arrow in the upper right of the page. Click on the *+ Create a new fork* button.

<img src="../images/github_createfork.png" class="img-responsive" alt="GitHub Fork Tapis UI">

In the next page, you can rename your copy of the fork or leave the defaults. When you are ready to proceed, click *Create Fork*.

<img src="../images/github_namefork.png" class="img-responsive" alt="GitHub Create the Fork">

This fork is your copy. Since it is linked the original repository, you can merge any updates from the main Tapis UI repository.


## Importing Your Tapis UI Fork into GitPod

We will be using [GitPod](https://gitpod.io) to work with your fork. When prompted to login, click *Continue with GitHub. This will make your repositories available to you.

<img src="../images/gitpod_login.png" class="img-responsive" alt="Logging in to GitPod">

You may be taken to a page where you can view existing Workspaces in GitPod. Click the *New Workspace* button.

<img src="../images/gitpod_workspaces.png" class="img-responsive" alt="GitPod Workspaces">


In the "Open in GitPod" dialog, find your Tapis UI fork. Remember that it should have your username in the repository name.

<img src="../images/gitpod_open.png" class="img-responsive" alt="GitPod Open Tapis UI">

GitPod will automatically load the source files and install any requirements. In addition, it will start a development preview build of your fork. You can click on the Ctrl or Command Click on the link when prompted to see this live preview

<img src="../images/gitpod_terminal.png" class="img-responsive" alt="GitPod Development Preview">

## Creating an SSH Key

In order to publish a live site on GitHub, your local development environment must have a public/private keypair for SSH access to GitHub. We will create one for the GitPod environment for this demonstration. This key will only work for the demonstration GitPod workspace, and you must repeat these steps to create a permanent key if you wish to deploy this from your own local machine.

First, start a bash terminal in GitPod. Find the *+* icon on the right side of the screen and click it. A new terminal will appear.

<img src="../images/gitpod_bash.png" class="img-responsive" alt="GitPod Bash terminal">

Next, create a keypair with:

```bash
ssh-keygen -t rsa -b 4096 -f $HOME/.ssh/tapisui
```

When prompted for a passphrase, hit ENTER and do not specify a passphrase. This will create two files, a `$HOME/.ssh/tapisui` file with your *private* key and a `$HOME/.ssh/tapisui.pub` file with your *public* key. 

You will need to copy the contents of your public key to the clipboard to continue. In the terminal, type:

```bash
cat $HOME/.ssh/tapisui.pub
```

This should show the contents of your public key, which you can highlight and copy and paste.

<img src="../images/gitpod_pubkey.png" class="img-responsive" alt="GitPod Public Key">
 
## Adding Your SSH Key to GitHub

Next, set up your GitHub account to use the public key you just created. First, log in to [GitHub](https://www.github.com). In the upper right, you will see an icon with your username. Use the dropdown to navigate to your account settings.

<img src="../images/github_settings.png" class="img-responsive" alt="GitHub settings">

In the navigation sidebar on the left side, click on *SSH and GPG Keys*.

<img src="../images/github_sshkeys.png" class="img-responsive" alt="GitHub SSH and GPG Keys">

At the top of the page content, find the *New SSH Key* button.

<img src="../images/github_newkey.png" class="img-responsive" alt="GitHub New SSH Key button">

In the next page, title the key *Tapis UI* and paste the contents of your public key file `$HOME/.ssh/tapisui.pub` into the key contents. Note that this should be the contents of your *public key* file, which begins with the text `ssh-rsa`. When you have done this, click the *Add SSH Key* button.

<img src="../images/github_newkey.png" class="img-responsive" alt="GitHub New SSH Key button">

You are now ready to deploy your own installation of Tapis UI.