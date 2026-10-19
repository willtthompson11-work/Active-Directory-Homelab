# Using Git & GitHub with this homelab

Your one-page cheat sheet. Git works the same on every machine — you just install it wherever the files live.

## Install Git

- **Windows** (your host PC, DC01, LAB-PC-001): download from `git-scm.com`, accept the defaults.
- **Kali**: usually preinstalled. If not: `sudo apt update && sudo apt install git -y`
- Check it worked: `git --version`

## One-time setup (on each machine)

```bash
git config --global user.name "Will Thompson"
git config --global user.email "you@your-github-email.com"
```

Use the email address on your GitHub account so your commits link to your profile.

## Signing in to GitHub (passwords don't work anymore — use one of these)

**Easiest: GitHub CLI.** Install it, then run `gh auth login` and follow the prompts (it opens a browser tab to confirm).

- Windows: `winget install GitHub.cli`
- Kali: `sudo apt install gh -y`

**Or: a Personal Access Token.** On github.com go to Settings → Developer settings → Personal access tokens → Tokens (classic) → Generate new token. When git asks for your password, paste the token instead. Save the token somewhere safe — GitHub only shows it once.

## The daily loop (run from inside the repo folder)

```bash
git status   # what changed since the last snapshot?
git add .    # stage everything
git commit -m "Phase 4: created GPO to disable USB storage"   # snapshot with a real message
git push     # upload to GitHub
```

Write commit messages like a lab journal: what you did and why. Future-you (and recruiters) will read these.

## Working across multiple VMs

- **First time on a machine:** `git clone https://github.com/<your-username>/ad-homelab.git`
- **Before starting work** on a machine you haven't touched in a while: `git pull` (grabs the latest from GitHub)
- **Rule:** commit + push at the end of every session so no work gets stranded on one VM.

## Suggested pattern for this lab

Keep the repo cloned on your **host PC** (or one VM you always use). When a phase produces artifacts — exported GPOs, screenshots, Kali scripts, event log exports — copy them into the right `phase-N-...` folder, then `add` / `commit` / `push`. You don't need git running *inside* every VM; one repo that you feed files into is simpler and just as legit. If you prefer, clone it on Kali too for the attack scripts in phase 5 — that's what `git pull` is for.

## If you mess up

- `git log --oneline` — see your history of snapshots
- Committed something you regret? `git revert <commit-hash>` creates a new commit that undoes it. History stays honest — nothing is ever truly deleted, which is the whole point.
