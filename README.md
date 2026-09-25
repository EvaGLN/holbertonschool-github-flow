# GitHub Collaboration Workshop Repository

This repository is used in a workshop focused on learning collaboration practices with Git and GitHub using a document-based workflow.

The goal is to simulate a small documentation project where multiple collaborators work on different documents, propose changes through branches and pull requests, review each other's work, and handle merge conflicts.

## Project structure

All editable content for this workshop lives in the `docs/` directory:

- `docs/introduction.md` — Introduction to the fictional project and its purpose.
- `docs/history.md` — History and important milestones of the project.
- `docs/collaboration.md` — Notes about how collaboration is expected to work in this project.
- `docs/workflow-overview.md` — High-level description of how changes are typically proposed and merged.

Participants in the workshop will:

- Create feature branches for specific document changes.
- Edit these documents in a controlled way.
- Open pull requests and review each other's work.
- Resolve merge conflicts when they appear.
- Tag and release specific versions of the documentation.

<div align="center"><img src="https://github.com/ksyv/holbertonschool-web_front_end/blob/main/baniere_holberton.png"></div>

# GitHub Flow - SCM Basics

## Table of Contents :

  - [0. Fork and Clone](#subparagraph0)
  - [1. Creating Workspace Branches](#subparagraph1)
  - [2. Independent Document Editing](#subparagraph2)
  - [3. Creating Pull Requests and Reviews](#subparagraph3)
  - [4. Merging Changes and Tagging a Release](#subparagraph4)
  - [5. Conflict Creation and Resolution](#subparagraph5)
  - [6. Creating a Final Release and Updating the Changelog](#subparagraph6)
## **Introduction & Context**

This workshop introduces you to practical collaboration using **GitHub Flow**, a lightweight branching strategy widely adopted in modern engineering teams.
You will work with a real GitHub repository, but instead of managing code, you will collaborate on **documents**, allowing you to focus entirely on version control, workflows, and teamwork.

The workflow you practice here (forking, branching, creating pull requests, reviewing, resolving conflicts, tagging releases) is the same process used every day in professional software projects.

The workshop is designed for **pairs**, but can also be completed **individually**.
If you work alone, you will simulate both sides of the collaboration through separate branches.

By the end, you will have executed a complete collaboration cycle on GitHub: from initial fork and feature development through conflict resolution and release management.

---

## **Learning Objectives**

By completing this workshop, you will be able to:

* Apply **GitHub Flow** to structure collaborative work.
* Fork a repository and configure remotes properly.
* Create and work on **feature branches** following naming conventions.
* Make meaningful commits with clear messages.
* Open and manage **Pull Requests (PRs)**, including writing proper descriptions.
* Perform peer review: comment, request changes, and approve PRs.
* Resolve **merge conflicts** introduced intentionally by the project.
* Use **semantic versioning** (SemVer) to tag releases.
* Create and update a simple **CHANGELOG**.
* Clean up branches and finalize a collaborative project responsibly.

These skills are essential for all upcoming SEIP projects and for real-world engineering workflows.

---

## **Resources**

You are expected to use the following official references during the workshop:

### **Git & GitHub Documentation**

* **GitHub Flow (official guide)**
  [https://docs.github.com/en/get-started/using-github/github-flow](/rltoken/zwLnbeXKzK-R9v3H0ZgEtA)
* **Forking a Repository**
  [https://docs.github.com/en/get-started/quickstart/fork-a-repo](/rltoken/vM2pmBaAYXU0q8PcUznYTg)
* **Managing Branches**
  [https://git-scm.com/book/en/v2/Git-Branching-Branches-in-a-Nutshell](/rltoken/U2dHvEe8Q-5sm0pCsqobog)
* **Creating and Managing Pull Requests**
  [https://docs.github.com/en/pull-requests](/rltoken/-b_Q4rDEmHn43qakVPJzAw)
* **Editing Files in GitHub**
  [https://docs.github.com/en/repositories/working-with-files/managing-files/editing-files](/rltoken/NHpwadp73mWdHuvvX7Zw9A)

### **Conflict Resolution**

* **Resolving Merge Conflicts**
  [https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/addressing-merge-conflicts](/rltoken/yqqGk7OFFNotzdIbgH_VsA)

### **Releases and Version Tags**

* **Semantic Versioning (SemVer)**
  [https://semver.org/](/rltoken/wKVuQivG3JoM0JQkpf3Nvg)
* **Creating Releases**
  [https://docs.github.com/en/repositories/releasing-projects-on-github](/rltoken/OdC6SCsOwaUVIqlG7Gp3HQ)


---


## Task
### 0. Fork and Clone <a name='subparagraph0'></a>

## **Introduction**

Before collaborating in any GitHub Flow–based project, every contributor must establish an isolated working environment. Forking ensures that you have full control over your own copy of the repository, while cloning it locally prepares you to create branches, make changes, and push updates. Proper remote configuration is essential to staying synchronized with the official source.

This task requires you to set up your environment correctly using your own understanding of Git and GitHub. You will need to consult the provided resources to determine the exact commands and steps.

## **Objective**

Create a personal fork of the base repository, clone it to your local environment inside a specifically named directory, and configure both required Git remotes without modifying any files.

## **Instructions**

You must complete **all** of the following requirements:

1. **Create a Fork**

* Fork the following repository to your own GitHub account:
 **`https://github.com/hbtn-edu/github-collab-base`**
* The fork must appear under your personal GitHub username.
*Hint:* Review GitHub's official documentation on how forking works.

IMPORTANT: The name of your foked repository should match the one displayed at the bottom of the task (i.e. `holbertonschool-github-flow`)

1. **Clone Your Fork into a Local Directory**

* Create a local directory named **`scm-github-collab`**.
* Inside that directory, clone **your fork** of the repository (not the base repository).
*Requirement:* The directory structure must be:

```css
scm-github-collab/
       holberton-github-flow/   ← cloned repo
```

*Hint:* You must determine the correct cloning URL from your fork.

1. **Configure the Upstream Remote**

* Inside the cloned repository, configure a Git remote named **`upstream`**.
* This remote must point to:
 **`https://github.com/hbtn-edu/github-collab-base`**
*Hint:* Consult the Git documentation on managing remotes.

1. **Validate Your Remotes**

* Ensure that:

`origin` → your fork
`upstream` → base repository
* The output of `git remote -v` must reflect the correct URLs.

1. **Do Not Modify Any Repository Files**

* No file changes, deletions, or additions are allowed in this task.

## **Expected Outcome**

At the end of this task, you must have:

* A fork under your GitHub account.
* A local directory named `scm-github-collab` containing the cloned fork.
* Two remotes:
* `origin` → your fork
* `upstream` → base repository
* Zero changes in the working tree (clean `git status`).

---

### 1. Creating Workspace Branches <a name='subparagraph1'></a>

## Introduction

In a typical GitHub Flow setup, each change is developed in its own branch based on the latest `main` branch. When multiple people collaborate, they usually do **not** work directly on the same branch; instead, each person works on their own branch focused on a specific change or file. This makes it easier to review work, track responsibility, and avoid accidental interference.

In this activity, you will prepare two feature branches that represent the work of two collaborators. If you are working in a pair, each of you will use one branch. If you are working alone, you will simulate both roles by creating both branches yourself.

## Objective

Create and push two feature branches based on the latest `main` branch:

* One branch dedicated to changes in the introduction document.
* One branch dedicated to changes in the history document.

These branches will be used later to edit different files and open independent pull requests.

## Instructions

1. **Synchronize your local main branch**

* Ensure you are on the `main` branch in your **local repository**.
* Fetch the latest changes from both `origin` and `upstream`.
* Update your local `main` so that it includes any new commits from `upstream/main`.
* Push the updated `main` branch to `origin` so that `origin/main` matches your local `main`.
You are expected to research how to synchronize `main` with `upstream/main` and then push that state to `origin/main`.

1. **Create the feature branch for the introduction updates**

* Starting from the updated `main` branch, create a new branch named exactly:
`feature/intro-update`
* Do not make any file changes yet.

1. **Create the feature branch for the history updates**

* Return to the `main` branch if you are not already on it.
* From `main`, create another branch named exactly:
`feature/history-update`
* Do not make any file changes yet.

1. **Push both branches to GitHub**

* Push `feature/intro-update` to your fork on GitHub.
* Push `feature/history-update` to your fork on GitHub.
* After pushing, the remote branches `origin/feature/intro-update` and `origin/feature/history-update` must exist on GitHub.
If you are working in a pair, each student will primarily use one of these branches in the next activities. If you are working alone, you will use both branches yourself.

## Expected Outcome

By the end of this activity, the repository on GitHub must have:

* A `main` branch that is synchronized with the latest `upstream/main`.
* A remote branch `origin/feature/intro-update` created from `main`.
* A remote branch `origin/feature/history-update` created from `main`.

Your local environment should also have the corresponding local branches, but the evaluation will be based on the state of the repository on GitHub.

---

### 2. Independent Document Editing <a name='subparagraph2'></a>

## **Introduction**

In GitHub Flow, each contributor works on a separate branch that focuses on a specific, isolated change. When multiple collaborators are involved, each person edits a different part of the project to avoid interfering with each other’s work. This activity reflects that reality: two branches represent the independent work of two contributors making changes to different documents.

This activity requires you to perform one precise edit in each branch. If you are working in a pair, each student edits their assigned branch. If you are working alone, you must complete the edits for both branches yourself. Each change must be committed and pushed so it can be evaluated.

## **Objective**

Make one required change in `docs/introduction.md` on the branch `feature/intro-update` and one required change in `docs/history.md` on the branch `feature/history-update`. Each change must be committed separately on its respective branch and pushed to GitHub.

## **Instructions**

Inside your local clone of the repository, complete all the following requirements.

### **Work on the introduction document (Student A role)**

1. Switch to the branch:

```bash
feature/intro-update
```

1. Open the file:

```bash
docs/introduction.md
```

1. Append the following line **as a new final paragraph** at the end of the file:

```csharp
This introduction has been updated as part of collaborative work.
```

1. Stage only this file and create a commit with the exact commit message:

```javascript
Update introduction document
```

1. Push this branch to GitHub so that the commit is available remotely.

### **Work on the history document (Student B role)**

1. Switch to the branch:

```bash
feature/history-update
```

1. Open the file:

```bash
docs/history.md
```

1. Append the following line **as a new final paragraph** at the end of the file:

```bash
This history section has been updated as part of collaborative work.
```

1. Stage only this file and create a commit with the exact commit message:

```bash
Update history document
```

1. Push this branch to GitHub so that the commit is available remotely.

## **Expected Outcome**

Your GitHub repository must contain:

* A branch `feature/intro-update` with exactly one commit modifying only `docs/introduction.md`.
* A branch `feature/history-update` with exactly one commit modifying only `docs/history.md`.

Each file must include the required final paragraph, with the exact text provided. The working tree in your local environment must be clean after each commit.

These changes will later be proposed as pull requests.

---

### 3. Creating Pull Requests and Reviews <a name='subparagraph3'></a>

## Introduction

In GitHub Flow, changes are never pushed directly to the main branch. Instead, each change is proposed through a **pull request (PR)**. A pull request makes the work visible, allows collaborators to review it, discuss changes, and decide when it is ready to be merged. This is a central part of modern collaboration: the branch is where you write changes, the pull request is where you communicate and get feedback.

In this activity, you will create pull requests for two independent branches and simulate a review process. If you are working in a pair, each student will own one branch and review the other. If you are working alone, you will simulate both roles yourself.

## Objective

Create two pull requests from the feature branches `feature/intro-update` and `feature/history-update` into the `main` branch of your fork, and perform at least one review comment on each pull request.

## Instructions

Complete all of the following requirements using the GitHub web interface on your forked repository.

### Pull request for `feature/intro-update`

1. Open your fork of the repository on GitHub.
2. Create a pull request with the following characteristics:

* **Base branch:** `main` (in your fork).
* **Compare branch:** `feature/intro-update`.
* **Pull request title:**
`Update introduction document`
* **Pull request description:**
 Include a short description (at least one full sentence) explaining that this pull request updates the introduction document as part of collaborative work.

1. Submit the pull request. Do **not** merge it yet.
2. Add at least one comment to this pull request:

* The comment must refer to the content of `docs/introduction.md`.
* It must mention *why* the change is useful or appropriate (for example, clarity, accuracy, or completeness).

If you are working in a pair, this comment should ideally come from the other student. If you are working alone, you will comment on your own pull request.

### Pull request for `feature/history-update`

1. In the same repository, create a second pull request with the following characteristics:

* **Base branch:** `main` (in your fork).
* **Compare branch:** `feature/history-update`.
* **Pull request title:**
`Update history document`
* **Pull request description:**
 Include a short description (at least one full sentence) explaining that this pull request updates the history section as part of collaborative work.

1. Submit the pull request. Do **not** merge it yet.
2. Add at least one comment to this pull request:

* The comment must refer to the content of `docs/history.md`.
* It must mention *why* the change is useful or appropriate.

If you are working in a pair, the student who owns `feature/intro-update` should review this pull request. If you are working alone, you will again review your own pull request.

## Expected Outcome

On GitHub, your fork must show:

* One open pull request from `feature/intro-update` into `main`:

Title: `Update introduction document`
Description: at least one sentence explaining the purpose.
At least one comment that references the introduction change and explains its value.
* One open pull request from `feature/history-update` into `main`:

Title: `Update history document`
Description: at least one sentence explaining the purpose.
At least one comment that references the history change and explains its value.

None of the pull requests should be merged yet. They will be merged in a later activity.

---

### 4. Merging Changes and Tagging a Release <a name='subparagraph4'></a>

## Introduction

In GitHub Flow, work completed on a feature branch becomes part of the project only after it is merged into the main branch.

* Merging is typically done after review, and it creates a new version of the project.
* Tagging a version is an essential part of giving structure to the project’s history.

> **tags** mark significant checkpoints, allow teams to reference specific versions, and support release workflows.

This activity requires you to **merge both pull requests created earlier** and then **create a version tag** on the resulting updated main branch. You will use Semantic Versioning (SemVer) to determine the correct version number.

## Objective

Merge the pull requests from both feature branches into the main branch of your fork and create a semantic version tag representing the updated state of the project.

## Instructions

You must complete **all** of the following requirements on your GitHub repository:

### **1. Merge the introduction update pull request**

* Open the pull request that compares `feature/intro-update` into `main`.
* Ensure the pull request has been reviewed already (from the previous activity).
* Use GitHub’s interface to merge the pull request into `main`.
* After merging, delete the branch `feature/intro-update` using the option provided by GitHub.

### **2. Merge the history update pull request**

* Open the pull request that compares `feature/history-update` into `main`.
* Ensure the pull request has been reviewed already.
* Merge this pull request into `main` using GitHub’s interface.
* After merging, delete the branch `feature/history-update`.

### **3. Create a version tag**

After merging both pull requests, your main branch contains two new changes. You must create a new version tag following Semantic Versioning:

* Use **tag name:**

```undefined
v1.0.0
```

* The tag must point to the current commit at the tip of `main` after both merges.
* Create the tag using the **GitHub web interface**, not your local environment.

### **4. Create a GitHub Release**

* Use the tag `v1.0.0` to create a release.
* Title of the release must be exactly:

```sql
Initial collaborative update
```

* Description must contain at least **two complete sentences** summarizing the merged changes.

## Expected Outcome

Your GitHub repository must show:

* Both pull requests merged into `main`.
* Both branches deleted from GitHub.
* A tag named `v1.0.0` pointing at the latest commit on `main`.
* A release titled **“Initial collaborative update”** using that tag.
* A release description with two or more full sentences describing the introduction and history updates.

---

### 5. Conflict Creation and Resolution <a name='subparagraph5'></a>

## Introduction

Merge conflicts happen when two branches change the same part of a file in incompatible ways. Conflict resolution is a critical real-world skill in any collaborative workflow that uses GitHub Flow. Developers encounter conflicts often, and the ability to understand, resolve, and finalize them cleanly is essential for maintaining a healthy codebase.

In this activity, you will intentionally create a merge conflict by editing the same section of a shared document from two different branches. You will then resolve the conflict locally and push the final resolved version. If working in a pair, each student will own one of the branches; if working alone, you will simulate both roles.

## Objective

Create a controlled merge conflict between two feature branches by making incompatible changes to the same paragraph in a document, then resolve the conflict locally and merge the final resolved version into `main`.

## Instructions

You must complete **all** of the following requirements.

### **1. Prepare the branches**

You will work with two new branches created from the latest `main`:

* `feature/conflict-a`
* `feature/conflict-b`

Both branches must be created and pushed to GitHub before editing begins.

**Steps:**

1. Ensure your local `main` is synchronized with `upstream/main` and pushed to `origin/main`.
2. Create and check out the branch:

```bash
feature/conflict-a
```

1. Push it to GitHub.
2. Switch back to `main`.
3. Create and check out the branch:

```bash
feature/conflict-b
```

1. Push it to GitHub.

### **2. Create incompatible edits**

The conflict will be created in the file:

```bash
docs/collaboration.md
```

If this file does not exist, pull the latest changes from upstream.

#### **On branch `feature/conflict-a`**

1. Switch to `feature/conflict-a`.
2. Find the **first paragraph** of `docs/collaboration.md`.
3. Replace the entire first paragraph (one or more lines up to the first blank line) with the following text exactly:

```cpp
Collaboration requires clear communication and well-defined responsibilities.
```

1. Commit the change with message:

```sql
Update first paragraph for conflict scenario A
```

1. Push the branch.

#### **On branch `feature/conflict-b`**

1. Switch to `feature/conflict-b`.
2. Replace the same first paragraph of `docs/collaboration.md` with:

```vbnet
Effective teamwork depends on continuous feedback and shared understanding.
```

1. Commit with message:

```sql
Update first paragraph for conflict scenario B
```

1. Push the branch.

At this point, the repository contains two branches with incompatible changes to the same paragraph.

### **3. Attempt to merge and observe the conflict**

1. On GitHub, create a pull request from:

```yaml
compare: feature/conflict-a
   base: main
```

1. Merge this pull request normally.
This one should merge cleanly. Delete the branch after merge.
2. Now create a second pull request from:

```yaml
compare: feature/conflict-b
   base: main
```

1. GitHub will report a **merge conflict**.
Do not resolve it on GitHub.
You must resolve the conflict locally.

### **4. Resolve the conflict locally**

1. In your local repository, switch to `feature/conflict-b`:

```bash
git switch feature/conflict-b
```

1. Pull the latest changes from `main` to bring the conflict into your branch:

```css
git pull origin main
```

1. Git will stop and mark the conflict in `docs/collaboration.md`.
Open the file and resolve the conflict by replacing the entire paragraph with:

```cpp
Collaboration requires adaptability, trust, and continuous alignment among team members.
```

1. Remove all conflict markers (`<<<<<<<`, `=======`, `>>>>>>>`).
2. Stage the file and commit the resolved version with:

```javascript
Resolve conflict in collaboration document
```

1. Push the updated branch:

```bash
git push origin feature/conflict-b
```

1. Return to GitHub and complete the merge of the pull request. Delete the branch after merge.

## Expected Outcome

Your repository must contain:

* A merged pull request for `feature/conflict-a`.
* A merged pull request for `feature/conflict-b` after conflict resolution.
* A final version of `docs/collaboration.md` where the first paragraph is exactly:

```cpp
Collaboration requires adaptability, trust, and continuous alignment among team members.
```

* Both feature branches deleted.

The conflict must have been resolved **locally**, not through GitHub’s UI.

---

### 6. Creating a Final Release and Updating the Changelog <a name='subparagraph6'></a>

## Introduction

In collaborative projects, merging changes is not the final step. Teams create releases to document important milestones and communicate what has changed between versions. A changelog helps maintain a clear history and makes it easier for others to understand the evolution of the project.

In this activity, you will update the changelog to reflect the latest changes merged into `main`, choose an appropriate next version number using Semantic Versioning, tag that version, and publish a final release.

## Objective

Update `CHANGELOG.md` to describe the recent updates, choose and apply the next semantic version for the project, create a corresponding tag, and publish a release on GitHub.

## Instructions

You must complete **all** of the following requirements.

### 1. Update the changelog

1. In your local clone, ensure you are on the `main` branch and synchronized with your remote:

```bash
git fetch origin
   git switch main
   git pull origin main
```

1. Open the file:

```text
CHANGELOG.md
```

* If this file does not exist, create it at the root of the repository.

1. At the **top** of the file, add a new section to describe the most recent changes.
Use the following structure:

```text
## Unreleased
   - <bullet describing the introduction and history updates>
   - <bullet describing the conflict resolution in docs/collaboration.md>
```

Requirements:

* The heading must be exactly `## Unreleased`.
* You must write **two bullet points**:

One summarizing the changes to the introduction and history documents.
One summarizing the conflict resolution in `docs/collaboration.md`.
* The text of the bullets must be written by you, in complete sentences.

1. Commit this change with the exact commit message:

```text
Update changelog with latest changes
```

1. Push the commit to your remote `main` branch:

```bash
git push origin main
```

### 2. Choose the next semantic version

Read the Semantic Versioning specification at:

* https://semver.org/

Consider the following facts about the state of your project:

* The last released version of this project was `v1.0.0`.
* Since that release, you have:
* Added new documentation content (introduction and history updates).
* Resolved a conflict and improved the collaboration document.
* No breaking changes or incompatible API changes have been introduced.

Based on SemVer rules and these conditions:

* Decide what the **next version number** of the project should be.
* The version must follow the format:
`MAJOR.MINOR.PATCH`
* You must use this version consistently in the **tag** and in the **changelog heading** in the next steps.

> Your choice will be evaluated according to the semantic versioning rules and the context described above.

### 3. Finalize the changelog version entry

1. Replace the heading `## Unreleased` you added earlier with a heading that includes the version you chose in the previous step.
The new heading must follow this pattern:

```text
## vX.Y.Z
```

where `vX.Y.Z` is the semantic version you decided.

1. Do **not** change the two bullet points you already wrote, except to adjust them if needed to make sense under a versioned section instead of “Unreleased”.
2. Commit this change (you may reuse the previous commit if you amend it, or create a new one; the final state of `main` is what matters).
3. Push the updated changelog to `origin/main`.

### 4. Create the version tag

1. On GitHub, go to the **Releases** section of your repository.
2. Create a new tag using the version you decided in step 2 (for example, `vX.Y.Z`).
3. Make sure this tag points to the **current HEAD of `main`**, which already includes:

* The introduction and history updates.
* The conflict resolution in `docs/collaboration.md`.
* The changelog update.

### 5. Publish the final release

1. Create a release using the tag you just created.
2. Set the **release title** to:

```text
Collaborative update <your version number>
```

For example, if you chose `v3.2.1`, the title must be:

```text
Collaborative update 3.2.1
```

1. In the release description, write **at least two complete sentences** that:

* Describe the updates to the introduction and history documents.
* Describe the conflict resolution in `docs/collaboration.md`.

1. Publish the release.

## Expected Outcome

Your GitHub repository must contain:

* A `CHANGELOG.md` file whose first section is a heading with the version you selected (`## vX.Y.Z`), followed by at least two bullet points describing:
* Documentation updates (introduction and history).
* The conflict resolution in the collaboration document.
* A commit on `main` with the message `Update changelog with latest changes` somewhere in the recent history.
* A tag with the chosen version (`vX.Y.Z`) pointing at the current `main` commit.
* A release titled `Collaborative update <your version number>` using that tag, with a description of at least two meaningful sentences.

> The correctness of the chosen version will be evaluated according to Semantic Versioning rules and the described project changes.

---


## Authors
Ksyv - [GitHub Profile](https://github.com/ksyv)
