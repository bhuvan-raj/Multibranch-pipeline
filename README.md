
---

### 📄 `README.md` — Jenkins Multibranch Pipeline

- 🌀 Jenkins Multibranch Pipeline

## 📘 What is a Multibranch Pipeline?

A **Multibranch Pipeline** in Jenkins automatically discovers, manages, and executes **Pipelines for branches** and **pull requests** in a source control repository (like GitHub, GitLab, Bitbucket, etc.).

Instead of creating separate Jenkins jobs for each branch, Jenkins uses the `Jenkinsfile` found in each branch to build the pipeline dynamically.

---

## 🎯 Why Use Multibranch Pipelines?

- ✅ **CI/CD per branch**: Each branch runs its own pipeline using its `Jenkinsfile`.
- 🔁 **PR testing**: Automatically run tests/builds on pull requests.
- 🛠️ **Automation**: Automatically discovers new branches and removes deleted ones.
- 🧪 **Feature Isolation**: Test features independently before merging to main.
- 👨‍💻 **Developer Autonomy**: Devs can manage builds by editing their own `Jenkinsfile`.

---

## 🏗️ Basic Setup Steps

### 1. ✅ Prerequisites

- Jenkins installed and running
- GitHub (or GitLab/Bitbucket) repository with:
  - Multiple branches
  - A `Jenkinsfile` in each branch

### 2. 📦 Required Plugins

- **Pipeline**
- **Git**
- **GitHub Branch Source** (if using GitHub)

> Go to **Manage Jenkins → Plugins → Available**, and install the above if not already present.

### 3. ➕ Creating the Multibranch Pipeline Job

1. Go to **Jenkins Dashboard** → **New Item**
2. Enter a name (e.g., `java-docker-jenkins-pipeline`)
3. Select **Multibranch Pipeline**, click OK

### 4. 🔧 Configure the Job

#### Under **Branch Sources**:
- Click **Add Source** → Select your Git provider (e.g., GitHub)
- Enter repository URL or connect with credentials

#### Optional:
- Add **filters** to exclude/include specific branches (e.g., `main`, `dev`)
- Enable **"Discover pull requests"** for PR-based pipeline.

> You should include a `Jenkinsfile` in **every branch** that should be built.

---

## 🔄 How It Works

* Jenkins scans the repository and **detects all branches** with a `Jenkinsfile`
* It creates a **pipeline job for each branch**
* When a new branch is pushed → Jenkins auto-detects and builds it
* When a branch is deleted → Jenkins removes it from the view

---

## 💡 Use Cases

| Use Case                             | Description                                                                          |
| ------------------------------------ | ------------------------------------------------------------------------------------ |
| **Feature Branch Testing**           | Every new feature branch gets its own CI/CD pipeline                                 |
| **PR Validation**                    | Jenkins runs builds/tests when a PR is raised                                        |
| **Environment-specific Deployments** | Different branches (e.g., `dev`, `staging`, `prod`) deploy to different environments |
| **Microservices**                    | Each branch of each service gets its own CI/CD                                       |
| **Collaborative Teams**              | Multiple developers can push to different branches with their own workflows          |

---

## 🚀 Tips

* Use **`env.BRANCH_NAME`** to make behavior branch-specific.
* Add **Webhooks** in GitHub to trigger builds instantly.
* Use **credentials** for private repositories.
* Use **`when` conditions** in stages to run specific logic only for certain branches.

---

## 📚 References

* [Jenkins Docs: Multibranch Pipelines](https://www.jenkins.io/doc/book/pipeline/multibranch/)
* [Jenkins GitHub Plugin](https://plugins.jenkins.io/github-branch-source/)

---

