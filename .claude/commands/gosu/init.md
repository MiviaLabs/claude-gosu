# Gosu Init Command

## Usage
```
gosu:init
```

## Description
Initializes a new Gosu project by creating the `.gosu` directory and updating `.gitignore` if the project is a Git repository.

## Command
```bash
# Create .gosu directory in project root
mkdir -p .gosu

# Add .gosu to .gitignore if git repo exists and entry not already present
if [ -d ".git" ] && [ -f ".gitignore" ]; then
  if ! grep -q "^\.gosu$" .gitignore; then
    echo ".gosu" >> .gitignore
  fi
elif [ -d ".git" ] && [ ! -f ".gitignore" ]; then
  echo ".gosu" > .gitignore
fi
```

This command will:
1. Create a `.gosu` directory in the project root
2. If this is a Git repository:
   - Add `.gosu` to `.gitignore` if the file exists and doesn't already contain the entry
   - Create `.gitignore` with `.gosu` entry if the file doesn't exist