# Publishing Lieyuan Yang's Website

This guide explains:

1. How to upload the completed website folder to Lieyuan's existing GitHub repository.
2. How to publish the website at **https://lieyuanyang.github.io**.
3. How to update the website later.
4. How to connect **www.lieyuanyang.com** after purchasing the domain.

The instructions are written for the project folder named **LieyuanYang.github.io**. The local folder name may contain uppercase letters, but the existing GitHub repository is:

- GitHub account: **LieyuanYang**
- Repository: **LieyuanYang/lieyuanyang.github.io**
- Repository URL: https://github.com/LieyuanYang/lieyuanyang.github.io
- Initial website URL: https://lieyuanyang.github.io
- Current Git branch: **master**
- GitHub Pages publishing folder: **/docs**

The project has already been rendered. The **docs** folder contains the static website that GitHub Pages will publish.

---

## Part 1: Receive and inspect the folder

### Step 1. Download and extract the folder

Download the folder sent by Xiang and extract it if it arrives as a ZIP file.

Place it somewhere permanent and easy to find, such as:

- macOS: **Documents/LieyuanYang.github.io**
- Windows: **Documents\LieyuanYang.github.io**

Do not work directly inside an email attachment, cloud preview, or temporary Downloads preview.

### Step 2. Confirm the important files exist

Open the folder and confirm that it contains at least:

- **_quarto.yml**
- **index.qmd**
- **cv.qmd**
- **research.qmd**
- **styles.css**
- **README.md**
- **docs/**
- **files/**
- **images/**

Inside **docs**, confirm that these files exist:

- **docs/index.html**
- **docs/cv.html**
- **docs/research.html**
- **docs/.nojekyll**

The folder should also contain a hidden **.git** directory. This hidden directory connects the local folder to Lieyuan's existing GitHub repository and preserves the repository history.

To show hidden files:

- macOS Finder: press **Command + Shift + .**
- Windows File Explorer: select **View > Show > Hidden items**

If **.git** is present, continue to Part 2.

If **.git** is missing, do not create a new GitHub repository. Follow the recovery instructions in [Part 8](#part-8-if-the-git-directory-is-missing).

---

## Part 2: Upload with GitHub Desktop - recommended

GitHub Desktop is the easiest and safest method because it handles GitHub sign-in and shows every file that will change.

Official download: https://desktop.github.com/

### Step 1. Sign in to the correct GitHub account

1. Install and open GitHub Desktop.
2. Sign in using the GitHub account **LieyuanYang**.
3. In a browser, also sign in at https://github.com/LieyuanYang.
4. Confirm that this account can open the repository:
   https://github.com/LieyuanYang/lieyuanyang.github.io

Lieyuan must own the repository or have write permission.

### Step 2. Add the received folder to GitHub Desktop

1. In GitHub Desktop, choose **File > Add Local Repository**.
2. Click **Choose**.
3. Select the received **LieyuanYang.github.io** folder itself.
4. Click **Add Repository**.

The application should recognize it as an existing Git repository.

### Step 3. Verify the repository and branch

At the top of GitHub Desktop, confirm:

- **Current Repository:** lieyuanyang.github.io
- **Current Branch:** master

Choose **Repository > Repository Settings > Remote** and confirm that the primary remote points to:

~~~text
https://github.com/LieyuanYang/lieyuanyang.github.io.git
~~~

If the URL is correct, close Repository Settings.

If the remote points somewhere else, stop and correct it before committing.

### Step 4. Fetch the current remote state

Click **Fetch origin** near the top of GitHub Desktop.

Fetching checks whether anything changed on GitHub after Xiang prepared the folder. It does not delete the local website work.

If GitHub Desktop says there are new remote commits, do not discard the local changes. Continue through the commit step below; GitHub Desktop may then ask to pull or merge before pushing.

### Step 5. Review the website replacement

Open the **Changes** tab.

It is normal to see:

- Many deleted files from the previous generic Academic Pages template.
- New Quarto source files.
- New generated files under **docs**.
- Lieyuan's portrait, CV, papers, and slides.

Do not click **Discard Changes**. That would undo the new website.

Make sure the checkbox at the top of the Changes list is selected so that all intended changes are included.

Before committing, confirm that sensitive or unrelated personal files are not listed. The repository will be public.

### Step 6. Commit the completed website

At the lower-left of GitHub Desktop:

1. In **Summary**, enter:

~~~text
Replace old site with updated Quarto website
~~~

2. Optionally enter this description:

~~~text
Add updated home, CV, and research pages with GitHub Pages output in docs.
~~~

3. Click **Commit to master**.

The commit records the website replacement locally. It has not reached GitHub yet.

### Step 7. Synchronize if GitHub has newer commits

After committing:

- If GitHub Desktop shows **Push origin**, continue to Step 8.
- If it shows **Pull origin**, click **Pull origin** first.
- If GitHub Desktop reports a merge conflict, stop. Do not force-push and do not discard changes. Resolve the conflict carefully or ask Xiang for help.

### Step 8. Push the website to GitHub

Click **Push origin**.

Wait until GitHub Desktop reports that the push completed.

Open the repository in a browser:

https://github.com/LieyuanYang/lieyuanyang.github.io

Confirm that the repository now shows:

- **_quarto.yml**
- **index.qmd**
- **docs/**
- **files/**
- **images/**
- **PUBLISHING_GUIDE.md**

Open **docs/index.html** on GitHub and confirm that it exists.

---

## Part 3: Terminal upload method - alternative

Use this method only if Lieyuan is comfortable with Git commands. GitHub Desktop is recommended.

### Step 1. Open a terminal in the project folder

On macOS:

~~~bash
cd "/path/to/LieyuanYang.github.io"
~~~

On Windows PowerShell:

~~~powershell
Set-Location "C:\path\to\LieyuanYang.github.io"
~~~

Replace the example path with the actual location.

### Step 2. Verify the repository

~~~bash
git status
git branch --show-current
git remote -v
~~~

Expected results:

- The branch is **master**.
- The remote named **origin** points to:
  **https://github.com/LieyuanYang/lieyuanyang.github.io.git**
- Git reports many deletions from the old site and new website files.

If the remote is missing, add it:

~~~bash
git remote add origin https://github.com/LieyuanYang/lieyuanyang.github.io.git
~~~

If the remote exists but is incorrect, correct it:

~~~bash
git remote set-url origin https://github.com/LieyuanYang/lieyuanyang.github.io.git
~~~

### Step 3. Fetch, commit, synchronize, and push

Run these commands one at a time:

~~~bash
git fetch origin
git add -A
git status
git commit -m "Replace old site with updated Quarto website"
git pull --rebase origin master
git push origin master
~~~

Important:

- Review the output of **git status** before committing.
- Do not use **git push --force**.
- If a rebase conflict occurs, stop and get help instead of guessing.
- GitHub account passwords do not work for command-line Git authentication. Use GitHub Desktop, Git Credential Manager, SSH, GitHub CLI, or a personal access token. Never send a personal access token to another person.

---

## Part 4: Turn on GitHub Pages

Uploading the files and publishing the website are separate steps.

### Step 1. Open the repository settings

1. Go to:
   https://github.com/LieyuanYang/lieyuanyang.github.io
2. Click **Settings**.
3. In the left sidebar, under **Code and automation**, click **Pages**.

If the Settings tab is not visible, make sure Lieyuan is signed in and owns the repository.

### Step 2. Select the publishing source

Under **Build and deployment**:

1. For **Source**, choose **Deploy from a branch**.
2. For the branch, choose **master**.
3. For the folder, choose **/docs**.
4. Click **Save**.

Do not choose **/(root)**. The published website is inside **docs**.

### Step 3. Wait for deployment

GitHub will start a Pages deployment. It often takes a few minutes.

To monitor it:

1. Open the repository's **Actions** tab.
2. Look for a workflow named **pages-build-deployment** or a Pages deployment.
3. Wait for the workflow to show a green check mark.

Return to **Settings > Pages**. GitHub should display a message similar to:

~~~text
Your site is live at https://lieyuanyang.github.io/
~~~

### Step 4. Test the website

Open:

https://lieyuanyang.github.io

Test all of the following:

- Home opens.
- CV opens.
- Research opens.
- The portrait loads.
- The CV downloads or displays.
- Each paper and the JMP slides open.
- Navigation works on both desktop and mobile.

If the old website appears, wait a few minutes and perform a hard refresh:

- macOS: **Command + Shift + R**
- Windows: **Ctrl + F5**

An incognito/private browser window can also bypass an old cache.

---

## Part 5: How to update the website later

The website uses Quarto. The editable source files are in the repository root; the generated website is in **docs**.

### Important rule

Do not edit HTML files inside **docs** by hand. Quarto will overwrite those changes the next time the site is rendered.

Edit these source files instead:

- Home and current position: **index.qmd**
- CV page: **cv.qmd**
- Research page: **research.qmd**
- Navigation and site URL: **_quarto.yml**
- Layout, colors, and spacing: **styles.css**

### Install Quarto

Download Quarto from:

https://quarto.org/docs/get-started/

After installation, confirm it works:

~~~bash
quarto --version
~~~

### Preview an update locally

Open a terminal in the project folder and run:

~~~bash
quarto preview
~~~

Quarto will print a local address. Open that address in a browser. Stop the preview with **Ctrl + C**.

### Render the final update

After editing the source files:

~~~bash
quarto render
~~~

Confirm that Quarto reports:

~~~text
Output created: docs/index.html
~~~

Then commit and push the source and generated output:

~~~bash
git add -A
git commit -m "Update website"
git pull --rebase origin master
git push origin master
~~~

GitHub Pages will redeploy automatically because the **docs** folder changed.

### Replace the CV without changing the link

The simplest approach is to replace:

~~~text
files/CV_Lieyuan_Yang.pdf
~~~

with a newer PDF using the same filename.

Then run:

~~~bash
quarto render
~~~

Commit and push the result.

If the filename changes, also update the links in **index.qmd** and **cv.qmd**.

---

## Part 6: Connect www.lieyuanyang.com after buying the domain

Complete Parts 1-4 first. Make sure **https://lieyuanyang.github.io** works before adding a custom domain.

The recommended primary address is:

**https://www.lieyuanyang.com**

The root address:

**https://lieyuanyang.com**

will redirect to the **www** address after both are configured correctly.

### Step 1. Purchase and secure the domain

Purchase **lieyuanyang.com** from a reputable domain registrar.

Immediately:

1. Turn on automatic renewal.
2. Use an email address Lieyuan will keep long-term.
3. Enable two-factor authentication at the registrar.
4. Keep the registrar login and recovery codes private.
5. Do not purchase separate web hosting; GitHub Pages provides the hosting.

### Step 2. Verify ownership with GitHub - strongly recommended

Domain verification prevents another GitHub user from claiming the domain for a different GitHub Pages site.

1. Sign in to GitHub as **LieyuanYang**.
2. Click the profile picture in the upper-right.
3. Click **Settings**. This is the personal profile settings page, not the repository settings page.
4. Under **Code, planning, and automation**, click **Pages**.
5. Click **Add a domain**.
6. Enter:

~~~text
lieyuanyang.com
~~~

7. GitHub will display a DNS **TXT** record with a unique value.
8. Open the DNS management page at the domain registrar.
9. Add the TXT record exactly as GitHub displays it.

The record name will look similar to:

~~~text
_github-pages-challenge-LieyuanYang
~~~

The exact TXT value is unique. Copy it from GitHub; do not copy an example value from this guide.

10. Save the DNS record.
11. Wait for it to propagate. This may be quick or may take up to 24 hours.
12. Return to GitHub profile **Settings > Pages** and click **Verify**.
13. Keep the TXT record permanently so the domain remains verified.

### Step 3. Add a CNAME file to the Quarto source

In the same folder as **_quarto.yml**, create a plain-text file named:

~~~text
CNAME
~~~

The filename has no extension.

The file must contain exactly one line:

~~~text
www.lieyuanyang.com
~~~

Do not include **https://**, a slash, or additional text.

Quarto copies this file to the generated website when it renders.

### Step 4. Update the canonical site URL

Open **_quarto.yml** and change:

~~~yaml
site-url: "https://lieyuanyang.github.io"
~~~

to:

~~~yaml
site-url: "https://www.lieyuanyang.com"
~~~

Under the existing **resources** list, add **CNAME** if it is not already listed:

~~~yaml
project:
  type: website
  output-dir: docs
  resources:
    - CNAME
    - files/**
    - images/**
~~~

Spacing matters in YAML. Keep the indentation exactly as shown.

### Step 5. Render and confirm the generated CNAME

Run:

~~~bash
quarto render
~~~

Confirm that this generated file exists:

~~~text
docs/CNAME
~~~

Open **docs/CNAME** and confirm that it contains:

~~~text
www.lieyuanyang.com
~~~

Commit and push:

~~~bash
git add -A
git commit -m "Configure lieyuanyang.com custom domain"
git pull --rebase origin master
git push origin master
~~~

### Step 6. Add the custom domain in the repository settings

Do this before creating the routing records at the registrar.

1. Open:
   https://github.com/LieyuanYang/lieyuanyang.github.io
2. Select **Settings > Pages**.
3. Find **Custom domain**.
4. Enter:

~~~text
www.lieyuanyang.com
~~~

5. Click **Save**.

The custom domain may already appear because **docs/CNAME** was published. If so, confirm that it is exactly **www.lieyuanyang.com**.

GitHub may create or update **docs/CNAME** through a commit. If GitHub creates a new remote commit, use **Fetch origin** and **Pull origin** in GitHub Desktop before making more local changes.

### Step 7. Configure DNS at the registrar

Open the DNS management page for **lieyuanyang.com**.

Registrar labels differ:

- **Name**, **Host**, or **Record** means the left side.
- **Value**, **Target**, **Points to**, or **Destination** means the right side.
- **@** means the root domain **lieyuanyang.com**.
- A default or automatic TTL is fine.

Remove conflicting parking or forwarding records for **@** and **www** before adding the records below.

#### Required www record

Add this CNAME record:

| Type | Name/Host | Value/Target |
|---|---|---|
| CNAME | www | lieyuanyang.github.io |

Important:

- Do not use **https://lieyuanyang.github.io**.
- Do not add **/lieyuanyang.github.io** or a repository path.
- Do not point **www** to **lieyuanyang.com**.
- Do not create a wildcard record such as <code>*</code> or <code>*.lieyuanyang.com</code>.
- If using Cloudflare DNS, set the record to **DNS only** during setup rather than proxied.

#### Required root-domain records

Add all four A records:

| Type | Name/Host | Value |
|---|---|---|
| A | @ | 185.199.108.153 |
| A | @ | 185.199.109.153 |
| A | @ | 185.199.110.153 |
| A | @ | 185.199.111.153 |

These records allow **lieyuanyang.com** to reach GitHub Pages and redirect to **www.lieyuanyang.com**.

#### Optional IPv6 records

IPv6 is optional. If used, keep the four A records above and add all four AAAA records:

| Type | Name/Host | Value |
|---|---|---|
| AAAA | @ | 2606:50c0:8000::153 |
| AAAA | @ | 2606:50c0:8001::153 |
| AAAA | @ | 2606:50c0:8002::153 |
| AAAA | @ | 2606:50c0:8003::153 |

Save the DNS changes.

### Step 8. Wait for DNS propagation

DNS updates may take a few minutes or up to 24 hours.

On macOS or Linux, check the records with:

~~~bash
dig www.lieyuanyang.com CNAME +short
dig lieyuanyang.com A +short
~~~

The first command should show:

~~~text
lieyuanyang.github.io.
~~~

The second command should show the four GitHub Pages IPv4 addresses.

On Windows PowerShell, use:

~~~powershell
Resolve-DnsName www.lieyuanyang.com -Type CNAME
Resolve-DnsName lieyuanyang.com -Type A
~~~

An online DNS checker can also be used, but the registrar and GitHub settings remain the source of truth.

### Step 9. Enable HTTPS

After GitHub confirms the DNS configuration:

1. Return to repository **Settings > Pages**.
2. Wait until GitHub finishes issuing the TLS certificate.
3. Select **Enforce HTTPS**.

The checkbox may be unavailable for up to 24 hours while DNS and certificate issuance complete.

After HTTPS is enabled, test:

- https://www.lieyuanyang.com
- https://lieyuanyang.com
- https://lieyuanyang.github.io

The root domain should redirect to the **www** domain. The default GitHub Pages address will normally redirect to the custom domain.

---

## Part 7: Final custom-domain checklist

Before announcing the domain, confirm:

- [ ] GitHub profile shows **lieyuanyang.com** as verified.
- [ ] The repository publishes from **master /docs**.
- [ ] The root **CNAME** file contains **www.lieyuanyang.com**.
- [ ] **docs/CNAME** contains **www.lieyuanyang.com**.
- [ ] **_quarto.yml** uses **https://www.lieyuanyang.com** as **site-url**.
- [ ] DNS has a **www CNAME** pointing to **lieyuanyang.github.io**.
- [ ] DNS has all four GitHub Pages **A records** for **@**.
- [ ] There are no conflicting or wildcard DNS records.
- [ ] **Enforce HTTPS** is enabled.
- [ ] Both the root and **www** addresses work.
- [ ] The registrar has automatic renewal and two-factor authentication enabled.

---

## Part 8: If the .git directory is missing

Some file-transfer services may omit hidden files. If the received folder does not contain **.git**, recover safely as follows.

### Recommended recovery with GitHub Desktop

1. Rename the received folder to:

~~~text
LieyuanYang.github.io-ready
~~~

2. Open:
   https://github.com/LieyuanYang/lieyuanyang.github.io
3. Click **Code > Open with GitHub Desktop**.
4. Clone the repository to a separate new folder.
5. In the newly cloned folder, enable hidden-file display and confirm **.git** exists.
6. Move all visible old website files from the new clone into a backup folder, but do not move or delete **.git**.
7. Copy all contents from **LieyuanYang.github.io-ready** into the new clone.
8. Confirm the new clone contains **.git**, **_quarto.yml**, and **docs/index.html**.
9. Add the new clone to GitHub Desktop if it is not already open.
10. Follow Part 2 beginning with the review and commit steps.

Keep the backup until the new website is live. The remote Git history also makes the old version recoverable.

---

## Part 9: Troubleshooting

### GitHub Desktop shows “Publish repository”

This usually means the folder is not connected to the existing remote repository.

Do not publish a second repository with a similar name. Confirm that **.git** exists and follow Part 8 if necessary.

### Push is rejected

Click **Fetch origin**, then **Pull origin**, and try **Push origin** again.

If Git reports conflicts, do not force-push. Resolve the conflicts or ask for help.

### GitHub Pages shows 404

Check:

1. **docs/index.html** exists on GitHub.
2. Repository **Settings > Pages** uses **Deploy from a branch**.
3. The branch is **master**.
4. The folder is **/docs**.
5. The Pages deployment in the **Actions** tab completed successfully.
6. The latest commit was pushed by an account with a verified email address and repository permission.

### The website still shows the old design

Check that the commit containing the new **docs/index.html** is visible on GitHub. Then wait for the Pages deployment and hard-refresh the browser.

### A source edit does not appear online

Editing **index.qmd**, **research.qmd**, or **styles.css** does not update **docs** automatically on Lieyuan's computer.

Run:

~~~bash
quarto render
~~~

Then commit and push both the source changes and the changed **docs** files.

### GitHub reports “DNS check unsuccessful”

Check that:

- **www** is a CNAME pointing directly to **lieyuanyang.github.io**.
- **@** uses the four current GitHub Pages A records.
- No conflicting **www** A, AAAA, CNAME, forwarding, or parking record remains.
- No wildcard DNS record exists.
- The DNS changes have had enough time to propagate.

### Enforce HTTPS is unavailable

Wait for DNS propagation and GitHub's certificate issuance. This may take up to 24 hours. Do not add a separate third-party certificate to GitHub Pages.

### The custom domain is already taken on GitHub

Verify **lieyuanyang.com** at the GitHub profile level. Also check whether the domain is attached to another repository owned by Lieyuan. Remove it from the old repository before attaching it to this one.

### The site works at www but not at the root domain

Confirm all four A records exist for **@**. The **www** CNAME alone does not configure the root domain.

### The site works at the root but not at www

Confirm the **www** CNAME points directly to **lieyuanyang.github.io**, not to the root domain.

---

## Official references

- [GitHub: Configure a publishing source](https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site)
- [GitHub: Manage a custom domain](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site)
- [GitHub: Verify a custom domain](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/verifying-your-custom-domain-for-github-pages)
- [GitHub Desktop: Add a local repository](https://docs.github.com/en/desktop/adding-and-cloning-repositories/adding-a-repository-from-your-local-computer-to-github-desktop)
- [GitHub Desktop: Commit and push changes](https://docs.github.com/en/desktop/making-changes-in-a-branch/committing-and-reviewing-changes-to-your-project-in-github-desktop)
- [Quarto: Publish to GitHub Pages](https://quarto.org/docs/publishing/github-pages.html)
- [Quarto: Get started](https://quarto.org/docs/get-started/)

---

## Recommended first publication sequence

For the first publication, the shortest safe sequence is:

1. Receive the folder and confirm **.git** exists.
2. Sign in to GitHub Desktop as **LieyuanYang**.
3. Add the folder as a local repository.
4. Confirm the remote and **master** branch.
5. Fetch origin.
6. Review and commit all website changes.
7. Push origin.
8. On GitHub, set Pages to **master /docs**.
9. Wait for the green Pages deployment.
10. Test **https://lieyuanyang.github.io**.
11. Configure the custom domain only after the GitHub Pages address works.
