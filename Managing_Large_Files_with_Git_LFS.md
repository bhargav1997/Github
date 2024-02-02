# Managing Large Files with Git LFS

## Introduction

Managing large files efficiently is crucial for maintaining a streamlined Git repository. Git Large File Storage (LFS) is a Git extension designed for handling large files more effectively. This guide provides instructions on how to set up Git LFS and use it to manage large files in your Git repositories.

## Installing Git LFS

Before using Git LFS, you need to install it on your system. Follow these steps:

1. **Install Git LFS:**
   ```bash
   git lfs install
   ```

2. **Track File Types:**
   Choose the file types you want to manage with Git LFS. For example, to track all `.mp4` files:
   ```bash
   git lfs track "*.mp4"
   ```

   Update your `.gitattributes` file to include the specified file types.

3. **Commit and Push Changes:**
   Commit the changes to your repository and push them to GitHub:
   ```bash
   git add .gitattributes
   git commit -m "Enable Git LFS for large files"
   git push origin main
   ```

## Using Git LFS

Once Git LFS is set up, follow these steps to work with large files:

1. **Add Large Files:**
   Add large files to your repository as you normally would:
   ```bash
   git add large_file.mp4
   ```

2. **Commit Changes:**
   Commit the changes to your repository:
   ```bash
   git commit -m "Add large file"
   ```

3. **Push Changes:**
   Push the changes to the remote repository:
   ```bash
   git push origin main
   ```

## Cloning a Repository with LFS Files

When cloning a repository that uses Git LFS, use the `git lfs clone` command to ensure LFS files are downloaded:

```bash
git lfs clone <repository_URL>
```

## Conclusion

Git LFS is a powerful tool for managing large files in Git repositories. By following these steps, you can efficiently handle large assets while keeping your repository size under control.
