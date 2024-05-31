# Automatic Daily Git Commits

This README documents a basic setup for creating automatic daily Git commits using a shell script and a cron job.

## Step 1: Create a Script for Committing and Pushing Changes

Create a script that will commit and push any changes. This script can be saved anywhere but for the purpose of this guide, we assume it's in the home directory and is called `commit_and_push.sh`.

The script would look like this:

    ```bash
    #!/bin/bash
    cd /path/to/your/repository

    git add .
    git commit -m "Daily automatic commit"
    git push origin master
    ```

Remember to replace `/path/to/your/repository` with the actual path to your Git repository.

Once you've created this script, give it execution permissions using the chmod command:

    ```bash
    chmod +x ~/commit_and_push.sh
    ```

## Step 2: Setup a Cron Job

Cron is a system daemon used to execute desired tasks (in our case, the script) at designated times.

After setting up the script, create a cron job to run the script once every day:

    ```bash
    crontab -e
    ```

In the text editor that this command opens, add the following line:

    ```bash
    @daily /bin/bash /path/to/your/commit_and_push.sh
    ```

Remember to replace `/path/to/your/commit_and_push.sh` with the actual path to your `commit_and_push.sh` script. Then save and exit the file.

With this setup, the `commit_and_push.sh` script runs once every day, creating a commit with the message "Daily automatic commit" and pushing it to the `master` branch of the `origin` remote.

## Warning

While this is a good setup for certain cases, having a script that automatically commits could be dangerous because you could commit broken code or unwanted files. Always ensure you know what's being committed to your repository!

Also note: Git hooks are stored locally in the `.git/hooks`▍


