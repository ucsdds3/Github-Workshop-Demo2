# 🧠 Git Hands-On: Clone, Merge, and Resolve Merge Conflicts

This tutorial walks you through simulating a **merge conflict** and resolving it manually.

## Section 1: Intro

These steps should be completed by **Person 1**. Person 2 will have things to do shortly, so pay attention!

### 🚀 Step 1: Fork this Repository

1. Click the **Fork** button at the top of this repository. This creates a copy under your own GitHub account.

### 💻 Step 2: Clone Your Repository Locally

1. Open your forked repository, click **Code**, select **HTTPS**, and copy the URL.
2. Open your terminal (or Git Bash), then run:

```bash
git clone <url>
cd Github-Workshop-Demo2
```

### 📝 Step 3: Create a File

1. Create a text file called `adventure.txt` using `touch`.
2. Add the following line to the file:

```text
The hero begins their adventure.
```

3. Save, stage, commit, and push your changes:

```bash
git add adventure.txt
git commit -m "Add adventure.txt"
git push
```

## Section 2: Branching, Merging, and Merge Conflicts

### Step 1: Add Your Partner as a Collaborator!

Person 1, go to your forked repository's **Settings → Collaborators** and invite Person 2.

**Person 2 must accept the invitation** before continuing.

### Step 2: Person 2, Clone the Same Repository

Person 2, follow the instructions from Section 1, Step 2.

**Important:** Clone Person 1's forked repository, not the original DS3 repository.

### Step 3: Both People Create a Branch

Each person should create their own branch with a **different name**.

The `-b` flag creates a new branch and switches to it.

Person 1:

```bash
git checkout -b feature-a
```

Person 2:

```bash
git checkout -b feature-b
```

### Step 4: Make Your Edits!

Both people should **replace the existing line** in `adventure.txt` with the following:

**Person 1:**
```text
The hero finds a magical sword.
```

**Person 2:**
```text
The hero swings and misses.
```

Save your changes, then both run:

```bash
git add adventure.txt
git commit -m "Update adventure"
```

Push your new branches to GitHub:

Person 1:
```bash
git push -u origin feature-a
```

Person 2:
```bash
git push -u origin feature-b
```

### Step 5: Pull Request

1. Person 1 opens a **Pull Request (PR)** from `feature-a` into `main`, adds a short description, and requests Person 2 as a reviewer.
2. Person 2 opens **Files changed**, reviews the changes, and merges the PR.
3. There should be **no conflicts yet**!

### Step 6: Merge and Create a Conflict

Person 2, switch back to `main` and pull the latest changes:

```bash
git checkout main
git pull
```

Now try merging your feature branch into `main`:

```bash
git merge feature-b
```

You should see something like:

```text
Auto-merging adventure.txt
CONFLICT (content): Merge conflict in adventure.txt
Automatic merge failed; fix conflicts and then commit the result.
```

Open `adventure.txt` in VS Code to see the conflict.

**Why did this happen?** Both people changed the same line differently, and Git doesn't know which version to keep.

## Section 3: Resolving Conflicts!

### Step 1: Resolve the Conflict

Open `adventure.txt` in VS Code. You'll see both versions of the conflicting line.

Decide what you want to keep. For example:

```text
The hero finds a magical sword.
The hero swings and misses.
```

Remove the conflict markers (`<<<<<<<`, `=======`, `>>>>>>>`) if editing manually, then save the file.

Stage and commit the resolved file:

```bash
git add adventure.txt
git commit -m "Resolve merge conflict"
```

Push your updated `main` branch:

```bash
git push
```

**Congratulations! You've successfully resolved a merge conflict! 🎉**

### Step 2: Clean Up (Optional)

If you're done with the exercise, you can delete your feature branch locally and on GitHub.

First, make sure you're on `main`:

```bash
git checkout main
```

Person 2 can then run:

```bash
git branch -d feature-b
git push origin --delete feature-b
```

Person 1 can similarly delete `feature-a` once they're finished.
