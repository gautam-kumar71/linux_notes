
## 📚 Opening Markdown in Browser

Convert the Markdown file to HTML and open it in a browser:

```bash
markdown file.md > file.html
xdg-open file.html  # Open in default browser
```

---

## 📂 Navigating Directories

| Command           | Description                                |
| ----------------- | ------------------------------------------ |
| `cd ~` or `cd`    | Go to home directory                       |
| `cd /`            | Go to root directory                       |
| `pwd`             | Print current working directory            |
| `cd ..` or `cd -` | Move up one level or to previous directory |

### 💑 Tree-like Structure

```bash
tree /             # Show directory tree from root
tree folderName    # Show directory structure of a specific folder
```

---

## 📁 Working with Directories

| Command                                    | Description                                              |
| ------------------------------------------ | -------------------------------------------------------- |
| `mkdir folderName`                         | Create a directory                                       |
| `mkdir -p ~/project/practice/subdirectory` | Create a nested directory (with parents if not existing) |
| `mkdir dir1 dir2 dir3`                     | Create multiple directories                              |

---

## 📝 Creating & Managing Files

### 📚 Creating Files

```bash
touch file1.txt  # Create an empty file
echo "Hello" > file.txt  # Create a file with text
echo "This is a new line" >> file.txt  # Append text to file
cat file.txt  # View file contents
```

### 🌏 Copying, Moving, Renaming

| Command                          | Action                         |
| -------------------------------- | ------------------------------ |
| `cp file.txt dir1/`              | Copy file to a directory       |
| `cp file.txt dir1/file_copy.txt` | Copy and rename file           |
| `mv file.txt dir2/`              | Move file to another directory |
| `mv file.txt newFileName.txt`    | Rename file                    |
| `cp -r dir3 dir2/`               | Copy directories recursively   |

🔹 **Relative Path Example**:  
If `dir3` is not inside the current working directory:

```bash
mv fileName.txt ../dir3  # Move file using relative path
```

---

## 💒 Viewing & Editing Files

```bash
cat fileName.txt  # View file contents
nl fileName.txt  # View with line numbers
nano multiline.txt  # Open file in nano editor
```

### 🔽 Creating Multi-line Files (Here-Document)

```bash
cat <<EOF > fileName.txt
This is a multiline text file.
You can add more content here.
EOF
```

---

## 🔍 Finding Files in Linux

| Command                      | Purpose                                        |
| ---------------------------- | ---------------------------------------------- |
| `find . -name "*.txt"`       | Find all `.txt` files in the current directory |
| `sudo find / -name "passwd"` | Search `passwd` file from root (requires sudo) |
| `find ~ -size +1M`           | Find files larger than 1MB                     |
| `find ~ -mtime -1`           | Find files modified in the last 1 day          |
| `which python`               | Find executable location of Python             |

---

🎯 **Summary**:  
👉 **File Operations**: `touch`, `cat`, `echo`, `nano`, `nl`  
👉 **Directory Navigation**: `cd`, `pwd`, `tree`, `ls`  
👉 **File Management**: `cp`, `mv`, `mkdir`, `rm`  
👉 **Searching**: `find`, `which`
