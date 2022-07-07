# Deploying Tapis UI

You can deploy your own live copy of Tapis UI. This page will be hosted on GitHub pages and point to the Tapis tenant of your choice.

## Setting up GitHub Pages

In your fork repository of Tapis UI, find the *Settings* option on the horizontal navigation for the repository.

<img src="../images/deploy_settings.png" class="img-responsive" alt="Repository Settings">

Next, find the *Pages* option in the navigation sidebar.

<img src="../images/deploy_pages.png" class="img-responsive" alt="Repository Pages">

In the *Source* dropdown, search for the `gh-pages` branch and select it.

<img src="../images/deploy_source.png" class="img-responsive" alt="Repository Page Source">

Then click the *Save* button.

<img src="../images/deploy_save.png" class="img-responsive" alt="Repository Source Save Button">

Note the message that says *Your site is ready to be published at `https://GITHUB_USERNAME.github.io/tapis-ui`. That is the URL of your Tapis UI deployment, and you will need this address in the next step.

## Configuring Your Deployment

You will need to change two files in your Tapis UI fork before publishing the page. You may use any file editor you wish.

First, you will need to configure the `homepage` setting in `package.json`. For convenience, you can see the original line of code [here](https://github.com/tapis-project/tapis-ui/blob/492aac14e863c585e8d0db66e6b9dde1a8c7cf85/package.json#L43). Replace the URL `https://tapis-project.github.io/tapis-ui` with the URL of your GitHub pages site. *Note: Delete the trailing slash in this URL*. The value should be `https://GITHUB_USERNAME.github.io/tapis-ui`. Save the file.

Second, you must change the Tapis tenant URL. Find the `basePath` setting in the file `src/index.tsx`. For convenience, you can see the original line of code [here](https://github.com/tapis-project/tapis-ui/blob/492aac14e863c585e8d0db66e6b9dde1a8c7cf85/src/index.tsx#L11). Currently, it is pointing to the TACC Tapis tenant. For this training, we will point it to the Training Tapis tenant. Replace `https://tacc.tapis.io` with `https://training.tapis.io`. Save the file.

## Setting Up GitPod to use SSH

Publishing to GitHub pages will require setting up GitPod to use SSH. First find the fork's SSH address. Find the *Code* dropdown button. From here, you will be able to copy the SSH address of your fork. 

<img src="../images/github_clone.png" class="img-responsive" alt="GitHub Clone">

Once you have this address, you will use the bash terminal to set GitPod's remote origin to this address. Use the following commands:

```bash
git remote set-url origin git@github.com:GITHUB_USERNAME/tapis-ui.git
```

## Committing Your Changes

You can try committing your changes to GitHub from your GitPod workspace. This will insure that your GitPod workspace can publish to GitHub pages.

```bash
eval `ssh-agent`
ssh-add $HOME/.ssh/tapisui
git add .
git commit -m "Tapis Training"
git push origin main
```

You may receive the following prompt:

```
The authenticity of host 'github.com (192.30.255.112)' can't be established.
ECDSA key fingerprint is SHA256:p2QAMXNIC1TJYWeIOttrVc98/R1BUFWu3/LiyKgUfQM.
Are you sure you want to continue connecting (yes/no/[fingerprint])?
```

Type `yes` then hit enter. If you are successful, your changes will be pushed to GitHub.

## Deploying

At this point, deploying is just one command:

```bash
npm run gh-pages
```

Once it has completed, you will be able to browse to the provided GitHub pages URL.

## Updating Your Deployment

Occasionally, new releases of Tapis UI will add features and fix bugs. You can update your fork by merging these changes, pulling them down to your local development environment and then deploying them. First, on your forked repository page, find the *Fetch Upstream* dropdown and click the *Fetch and Merge* button.

<img src="../images/deploy_merge.png" class="img-responsive" alt="Repository Merge">

In your local development machine or in your GitPod workspace, from within your cloned repository's directory, you may use the following commands:

```bash
eval `ssh-agent`
ssh-add $HOME/.ssh/tapisui
git pull
rm package-lock.json
npm install
git add .
git commit -m "Update package-lock.json"
npm run gh-pages
```

It may take a few minutes for GitHub pages to reflect your changes.