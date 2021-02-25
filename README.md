# roam2github-actions

[Roam2Github Backup Guide](https://www.notion.so/Roam2Github-Backup-Guide-650925859a4a42cf940e3fb74f5189f9)

COPY OF Erik Newhard's INSTRUCTIONS BELOW

If you set up *roam-to-git* following [my old guide](https://eriknewhard.com/blog/backup-roam-in-github), switch to *roam2github* with these instructions:

[Instructions to switch from roam-to-git to Roam2Github](https://www.notion.so/Instructions-to-switch-from-roam-to-git-to-Roam2Github-aec58ad1b56e4547ba97e006c8cc120a)

If you have already set up roam2github before Feb 20, 2021, update to **unlimited minutes** with these instructions:

[Roam2Github Update Instructions](https://www.notion.so/Roam2Github-Update-Instructions-c594a2931b694010814001c8a20fa960)

Screenshots and video of all these steps coming soon

### Directions

1. Log into [GitHub](https://github.com/) or create a free account
2. **Create a new, private repository**
    - Click the + dropdown next to your profile picture in the upper-right
    - Click "New repository"
    - Under "Repository name" type a name of your choice.
    (recommendation is `roam-backup`)
    - Select "Private"
    (Leave the selection on "Public" only if you want everyone to see your backups)
    - Check "Add a README file"
    - Click the green "Create repository" busson
3. **Add a Personalized Access Token**
    - Go to [https://github.com/settings/tokens](https://github.com/settings/tokens)

        Also accessed by going to your account "Settings" (from the dropdown after clicking your profile image in the upper-right), then "Developer settings" in the sidebar, then "Personal access tokens"

    - Click the "Generate new token" button
    - (Re-enter GitHub password if asked)
    - Under "Note", give it a descriptive name, like "Roam backup"
    - Under "Select scopes", click the checkbox for "repo" (this will also check the 5 boxes indented below it)
    - Scroll to the bottom and click the green "Generate token" button
    - You should now see a random string of characters and numbers in a light green background. Click the clipboard icon to copy it. You may want to leave this tab open, just in case you accidentally copy something else. (Because once closed, you'll never see this token again, and have to create a new one.)
4. **Create a new, *public* repository**
(same steps as #2 above, but select "Public" if you want unlimited minutes. You can call it something like "roam2github-actions")

    This is where the actions will run and save to your private backup repo.

    You can make this private. Just be aware of the 2000-minute monthly limit on the free plan. (My medium-sized graph takes about 3 minutes to run each backup, and runs hourly, so this allotment is not enough.) Usage can be monitored under [Billing](https://github.com/settings/billing). You can change the public/private setting at any time.

5. **Add Secrets**
    - Go to "Settings" (for the repo, not your account), then "Secrets"
    - Add "New repository secret" named `ACCESS_TOKEN` and paste the random token under Value
    - Add "New repository secret" named `BACKUP_REPO`

        The value for this will be your GitHub username, a slash, and the name of your private, backup repo (without `<>` symbols): `<username>/<repo>`

        For example, mine is: `everruler12/roam-backup`

    - Add the following Secrets with appropriate values
        - `ROAM_EMAIL`
        - `ROAM_PASSWORD`
        - `ROAM_GRAPH`

            *You can add multiple graphs on separate lines.*

6. **Add Actions**
    - Go to "Actions"
    - Click "set up a workflow yourself →"
    - Delete the code, and replace with the code here [https://raw.githubusercontent.com/everruler12/roam2github-actions/main/.github/workflows/main.yml](https://raw.githubusercontent.com/everruler12/roam2github-actions/main/.github/workflows/main.yml)
    - Click the green "Start Commit" button, then "Commit new file"
