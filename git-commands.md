To push your code to the `main` branch on GitHub via the terminal, follow these steps:

### 1. **Initialize Git Repository**
   If your project isn't already a Git repository, initialize it with:
   ```bash
   git init
   ```

### 2. **Stage Changes**
   Stage all your changes for the next commit:
   ```bash
   git add .
   ```
   This stages all files. Alternatively, you can stage specific files by replacing `.` with the file names.

### 3. **Commit Changes**
   Commit the staged changes with a meaningful commit message:
   ```bash
   git commit -m "Your commit message here"
   ```

### 4. **Add Remote Repository**
   If you haven't added a remote repository yet, do so with:
   ```bash
   git remote add origin https://github.com/username/repository.git
   ```
   Replace `username` with your GitHub username and `repository` with the name of your GitHub repository.

### 5. **Push to GitHub**
   Push your code to the `main` branch of your GitHub repository:
   ```bash
   git push -u origin main
   ```

### Summary:
- `git init`: Initializes a Git repository.
- `git add .`: Stages all changes.
- `git commit -m "message"`: Commits changes with a message.
- `git remote add origin <url>`: Adds the GitHub repository as a remote.
- `git push -u origin main`: Pushes the code to the `main` branch on GitHub.

If your repository already exists and you have been working on it, you can skip the `git init` and `git remote add origin` steps.
