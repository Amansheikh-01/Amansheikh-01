# graph-greener 🌱

A simple Python command-line tool that creates Git commits with randomized timestamps from the last year and pushes them to a remote Git repository.

> **Note:** This project changes Git commit metadata (`GIT_AUTHOR_DATE` and `GIT_COMMITTER_DATE`) and is intended for learning and Git experimentation. It should not be used to misrepresent real work or activity.

## ✨ Features

- Generate a user-defined number of Git commits.
- Randomly select commit dates and times from the previous 365 days.
- Append a timestamp entry to a selected file for every commit.
- Automatically stage and commit the modified file.
- Push all generated commits to the configured remote repository.
- Interactive command-line prompts with sensible defaults.
- Validates positive integer input and repository paths.

## 🛠️ Requirements

- Python 3.x
- Git installed and available in your system PATH.
- A local Git repository.
- A configured Git remote if you want to push the commits.

## 📁 Project Structure

```text
graph-greener/
├── graph-greener.py
├── data.txt
└── README.md
```

The main script contains functions for input validation, random date generation, commit creation, and the program entry point. fileciteturn0file0L6-L20

## 🚀 Installation

### 1. Clone or download the project

Place the Python script inside your working directory.

### 2. Make sure Git is installed

Check:

```bash
git --version
```

### 3. Verify your repository

Open a terminal in the Git repository you want to use and check:

```bash
git status
```

## ▶️ Usage

Run the Python script:

```bash
python graph-greener.py
```

The program asks for:

1. **Number of commits** — default: `20`
2. **Local Git repository path** — default: current directory
3. **Filename to modify** — default: `data.txt`

These inputs and defaults are defined in the program's `main()` function. fileciteturn0file0L55-L63

### Example

```text
============================================================
Welcome to graph-greener - GitHub Contribution Graph Commit Generator
============================================================
This tool will help you fill your GitHub contribution graph with custom commits.

How many commits do you want to make (default 20): 5
Enter the path to your local git repository (default current directory):
Enter the filename to modify for commits (default data.txt):

Making 5 commits in repo: .
Modifying file: data.txt
```

The script then generates a random timestamp for each commit and creates the commits sequentially. fileciteturn0file0L67-L70

## 🔧 How It Works

### 1. Input validation

The script accepts only positive integers for the commit count and verifies that the supplied repository path exists. fileciteturn0file0L6-L28

### 2. Random commit dates

For each commit, a date within the previous 365 days is selected, along with a random time during that day. fileciteturn0file0L36-L42

### 3. File modification

A line containing the generated commit timestamp is appended to the selected file:

```text
Commit at 2026-08-01T14:32:10
```

The file is then staged with:

```bash
git add <filename>
```

The implementation performs these operations in `make_commit()`. fileciteturn0file0L44-L48

### 4. Commit metadata

The script sets:

```text
GIT_AUTHOR_DATE
GIT_COMMITTER_DATE
```

to the generated timestamp before running `git commit`. fileciteturn0file0L49-L53

### 5. Push

After all commits are created, the script runs:

```bash
git push
```

to push the commits to the configured remote repository. fileciteturn0file0L72-L73

## ⚠️ Important Considerations

- Use this tool only in repositories where you have permission to create commits.
- The generated timestamps do **not** represent actual historical work.
- GitHub's contribution graph depends on GitHub's own contribution rules; changing local commit timestamps does not guarantee that contributions will appear as expected.
- Make a backup or use a dedicated test repository if you are experimenting.
- The current script does not explicitly handle Git command failures, authentication errors, or merge/push conflicts.

## 🔐 Git Authentication

If `git push` requires authentication, configure your Git credentials or authentication method before running the script.

Test your remote with:

```bash
git remote -v
```

## 🧪 Recommended Test

For safe testing, create a dedicated repository:

```bash
mkdir graph-greener-test
cd graph-greener-test
git init
echo "# Test" > data.txt
git add data.txt
git commit -m "Initial commit"
```

Then run the script and use a small number such as `3` commits.

## 📌 Default Commit Message

The script currently uses:

```text
graph-greener!
```

as the commit message. This is defined as the default argument of `make_commit()`. fileciteturn0file0L44-L45

## 📄 License

No license is specified in the source code. If you plan to publish this project, consider adding an appropriate open-source license.

## 👨‍💻 Author

**Aman Yusuf Sheikh**

B.Voc – Software Development

---

⭐ If this project helped you understand Git automation and Python subprocesses, consider improving it with better error handling, configurable commit messages, logging, and a dry-run mode.
