---
title: Branch Naming and Commit Messages
parent: Git Standards
nav_order: 1
---

# 🧱 Automatos Commit & Branch Naming Standards

> **Version:** 1.0  
> **Applies to:** All Automatos projects (web + mobile)  
> **Effective Date:** October 2025

---

## ⚙️ Overview

This document defines **how branches and commits are named across all Automatos repositories**.  
Our goals:

- Maintain consistent project history
- Enable future CI/CD automation and changelog generation
- Make PR reviews and issue tracking effortless
- Keep commit history readable by both humans and tools

Automatos follows **GitFlow** as the branching strategy and **Semantic Commits** for message formatting.

---

## 🌿 Branch Naming Convention

Branches must follow this format:

```
<type>/<project-prefix>-<issue-number>-<short-description>

```

### **Examples**

| Purpose | Example                      | Notes                             |
| ------- | ---------------------------- | --------------------------------- |
| Feature | `feature/FW-31-setup-ci-cd`  | Adds or enhances functionality    |
| Bug Fix | `fix/QL-12-sidebar-freeze`   | Resolves a defect                 |
| Hotfix  | `hotfix/FW-49-login-failure` | Urgent patch directly into `main` |
| Chore   | `chore/FW-27-lint-config`    | Code maintenance or refactor      |
| Release | `release/1.3.0`              | Used only for deployment prep     |

### **Branch Type Meanings**

| Prefix     | Description                                 |
| ---------- | ------------------------------------------- |
| `feature/` | New feature or enhancement                  |
| `fix/`     | Bug or issue fix                            |
| `hotfix/`  | Production patch                            |
| `chore/`   | Maintenance, tooling, or dependency changes |
| `release/` | Stable version branch                       |

---

## 💬 Commit Message Convention

Automatos uses **Semantic Commit Messages** with **Issue linkage**.

```
<type>(<scope>): <short summary> [<emoji>] [<issue-ref>]

```

### **Required Fields**

| Field       | Description                                    | Example                   |
| ----------- | ---------------------------------------------- | ------------------------- |
| `type`      | The purpose of the commit (see below)          | `feat`, `fix`, `chore`    |
| `scope`     | The specific module, feature, or component     | `auth`, `ui`, `api`       |
| `summary`   | A concise summary of the change (max 72 chars) | `add Google login button` |
| `issue-ref` | The linked GitHub Issue in parentheses         | `(#31)`                   |

---

### **Commit Types**

| Type         | Description                              | Example                                            |
| ------------ | ---------------------------------------- | -------------------------------------------------- |
| **feat**     | Introduces a new feature                 | `feat(auth): add Google login (#31)`               |
| **fix**      | Bug fix                                  | `fix(ui): resolve sidebar scroll freeze (#24)`     |
| **chore**    | Routine maintenance, build setup, deps   | `chore(devops): update CI workflow (#12)`          |
| **refactor** | Code improvement without behavior change | `refactor(api): simplify user fetch logic (#18)`   |
| **docs**     | Documentation updates                    | `docs(readme): add setup instructions (#22)`       |
| **style**    | Formatting, whitespace, etc.             | `style(ui): format components with Prettier (#19)` |
| **test**     | Adding or modifying tests                | `test(auth): add login unit tests (#35)`           |
| **perf**     | Performance improvements                 | `perf(api): optimize DB queries (#41)`             |
| **revert**   | Reverts a previous commit                | `revert: remove broken login (#37)`                |

---

### **Examples**

```bash
feat(auth): add Google sign-in support (#31)
fix(navbar): correct alignment on mobile (#42)
chore(ci): integrate EAS build step in pipeline (#55)
docs(api): document user endpoints (#66)

```

---

## 🧩 Optional: GitMoji for Visual Context

GitMoji can be used **sparingly** for readability, or if you want to make things a little more boujee.
They **must** be placed **after the colon**, before the message, and should **not replace semantic types**.

| Type     | Emoji | Example                                             |
| -------- | ----- | --------------------------------------------------- |
| feat     | ✨    | `feat(ui): ✨ add dark mode toggle (#12)`           |
| fix      | 🐛    | `fix(auth): 🐛 correct token refresh logic (#48)`   |
| docs     | 📝    | `docs(readme): 📝 add environment setup guide (#3)` |
| chore    | 🧹    | `chore(repo): 🧹 cleanup old workflows (#8)`        |
| refactor | ♻️    | `refactor(api): ♻️ simplify user model (#29)`       |
| perf     | ⚡    | `perf(images): ⚡ optimize asset loading (#20)`     |
| test     | ✅    | `test(auth): ✅ add login validation tests (#5)`    |

---

## 🔗 Linking to GitHub Issues

Every commit **must** reference its issue number using the `(#issueNumber)` format.

- ✅ **Correct:** `feat(auth): add token refresh support (#12)`
- 🚫 **Incorrect:** `feat(auth): add token refresh support FW-12`
- 🚫 **Incorrect:** `feat(auth): add token refresh support (12)`

> This ensures automated tools like changelog generators, release notes, and issue auto-closing work correctly.

---

## 🚀 Example Workflow

1.  **Create an issue** on GitHub.  
    Example: _“Setup CI/CD Pipeline” (#31)_
2.  **Create a branch:**

    ```bash
    git checkout -b feature/FW-31-setup-ci-cd

    ```

3.  **Make commits:**

    ```bash
    git commit -m "feat(ci): add EAS build step to pipeline (#31)"
    git commit -m "chore(ci): configure cache for dependencies (#31)"

    ```

4.  **Push & open a PR:**  
    PR title:

    ```
    FW-31 | Setup CI/CD Pipeline (#31)

    ```

5.  **On merge:**

    - The issue closes automatically.
    - The commit contributes to the changelog.

---

## 🧠 Why This Matters

| Benefit                | Description                                                     |
| ---------------------- | --------------------------------------------------------------- |
| **Traceability**       | Each commit directly linked to an issue                         |
| **Automation Ready**   | Works with semantic-release / changesets                        |
| **Readable History**   | Consistent human-friendly structure                             |
| **Future Scalability** | Compatible with label-based pipelines and CI gates              |
| **Professionalism**    | Matches conventions used by orgs like Render, Expo, and Netlify |
| **Sexiness**           | Things must be sexy even if they're actually junk               |

---

## ✅ Quick Reference

| Element  | Rule                                  |                     |
| -------- | ------------------------------------- | ------------------- |
| Branch   | `<type>/<prefix>-<issue>-<desc>`      |                     |
| Commit   | `<type>(<scope>): <summary> (#issue)` |                     |
| PR Title | `<prefix>-<issue>                     | <summary> (#issue)` |
| GitMoji  | Optional — keep minimal and relevant  |                     |

---

### Example in Context

#### **Branch**

```
feature/FW-31-setup-ci-cd

```

#### **Commit**

```
feat(ci): add EAS build step to pipeline (#31)

```

#### **PR Title**

```
FW-31 | Setup CI/CD Pipeline (#31)

```

---

## 🚫 Common Mistakes to Avoid

| Mistake                       | Why It’s Wrong                                                 |     |
| ----------------------------- | -------------------------------------------------------------- | --- |
| `FW-31: Setup CI/CD Pipeline` | Missing semantic type; automation-unfriendly                   |
| `fix: bug fixed`              | No issue reference or context                                  |     |
| `feature: add auth`           | Invalid type (should be `feat`)                                |     |
| `feat: add stuff`             | Vague, unclear message                                         |     |
| `chore: merge branch`         | No merges to be committed manually; should be squash or rebase |     |

---

## 🤓👆 Conclusion

This is the first edition of how we'll we be writing commits with potentially many updates to come as we scale insha'Allah. I've chosen this particular style for 2 main reasons:

1. Integration with automated project management tools as we create a fully automated system that self-enforces standards upon us. No more yelling at someone k bhai ye kardo ya iss tara karna tha and so on.
2. The ability to trace screw-ups so we can revert back quickly.

I'll be following this with another standardization on our entire dev process. For now, please follow this 🤗

---

## 📘 References

- [Conventional Commits 1.0.0](https://www.conventionalcommits.org/en/v1.0.0/)
- [GitFlow Workflow](https://nvie.com/posts/a-successful-git-branching-model/)
- [GitMoji Guide](https://gitmoji.dev/)

---

> **In short:**  
> Every branch and commit should be machine-readable, human-understandable, and automation-friendly.  
> A perfect commit history tells the story of the product — clean, contextual, and consistent.

---
