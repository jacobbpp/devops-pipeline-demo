# Step-by-Step Demo of Pipelines

This guide shows how to create a basic pipeline using GitHub Actions from scratch.

---

## Step 1 – Create a Blank Repository

1. Log into [GitHub](https://github.com/).
2. Click **New repository**.
3. Use the following details:
    - **Repository name:** `devops-pipeline-demo`
    - **Description:** `Demo repository for GitHub Actions pipeline.`
    - Check **Add a README file**.
    - Leave it public (or private if you prefer).
4. Click **Create repository**.

---

## Step 2 – Navigate to the Actions Tab

- In your new repository, click the **Actions** tab at the top.
- GitHub suggests templates, but choose **Set up a workflow yourself**.

---

## Step 3 – Replace with Simple Workflow

- Delete the starter code and replace it with the following:

```yaml
name: Demo Pipeline

on:
  push:
    branches:
      - main

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout repository
        uses: actions/checkout@v4

      - name: Print Hello Message
        run: echo "Hello from GitHub Actions!"

      - name: Display Date
        run: date

      - name: Run Multi-Line Script
        run: |
          echo "Listing current directory:"
          ls -l
```


> This will allow Github to:
> - Trigger on every push to `main`
> - Checks out the repo
> - Prints a hello message
> - Shows the current date
> - Lists files in the directory.”

---

## Step 4 – Save the Workflow File

- Name the file:

```
.github/workflows/demo-pipeline.yml
```

- Commit directly to `main`.

---

## Step 5 – Watch It Run

- Navigate back to the **Actions** tab.
- You’ll see a new run triggered immediately.
- Click the run to watch logs for each step.

Example output:

```
Hello from GitHub Actions!
Sun Jun 22 10:12:34 UTC 2025
Listing current directory:
total 4
-rw-r--r-- 1 runner runner  15 Jun 22 10:12 README.md
```

---

## Step 6 – Trigger a New Run

- Edit your `README.md` file in GitHub.
- Add a new line:  

    ```
    Demo update.
    ```

- Commit the change.
- Return to the **Actions** tab. A new run automatically starts.

---

## Step 7 – Explain Jobs vs Steps

**Job:** A collection of steps that run on a single virtual machine.

**Step:** An individual action in the job.

**Example:**  
All steps above are part of a single **build** job.
