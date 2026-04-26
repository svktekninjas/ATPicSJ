<!-- this is my first file -->

# ATPicSJ

## Git + GitHub CLI setup steps

The following commands were used to set up this local repository, install the
GitHub CLI, authenticate, and connect the repo to its remote on GitHub.

### 1. Install the GitHub CLI (`gh`)

On Ubuntu / WSL:

```bash
sudo apt update
sudo apt install gh
gh --version    # verify: gh version 2.45.0
```

### 2. Authenticate `gh` with GitHub

```bash
gh auth login
# Selections:
#   - GitHub.com
#   - HTTPS
#   - Authenticate Git with your GitHub credentials? Yes
#   - Login with a web browser (or paste a token)
```

Verify:

```bash
gh auth status
# Logged in to github.com account svktekninjas
# Token scopes: 'gist', 'read:org', 'repo', 'workflow'
```

This step also wires `gh` in as the Git credential helper for `github.com`
and `gist.github.com` (visible in `~/.gitconfig`):

```
credential.https://github.com.helper=!/usr/bin/gh auth git-credential
credential.https://gist.github.com.helper=!/usr/bin/gh auth git-credential
```

If it isn't set automatically, run:

```bash
gh auth setup-git
```

### 3. Initialize the local repository

```bash
mkdir -p ~/ATPicSJ/ATPicSJ
cd ~/ATPicSJ/ATPicSJ
git init -b main
```

### 4. Add the GitHub remote

```bash
git remote add origin https://github.com/sidatKSTX/ATPicSJ.git
git remote -v   # verify origin fetch + push URLs
```

### 5. Track `main` against `origin/main`

This is set up automatically on first push with `-u`:

```bash
git push -u origin main
```

After which `.git/config` shows:

```
[branch "main"]
    remote = origin
    merge  = refs/heads/main
```

### 6. (Optional) Identity for commits

If not already set globally:

```bash
git config --global user.name  "Your Name"
git config --global user.email "you@example.com"
```
