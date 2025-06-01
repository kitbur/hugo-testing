# Hugo Theme Testing Repository

A minimal [Hugo](https://gohugo.io/) site used to test themes in isolated branches.

## Workflow: Testing a New Theme

### 1. Create a new branch

```bash
git checkout main
git checkout -b <theme-name>
```

### 2. Add the theme as a submodule

```bash
git submodule add <theme-repo-url> themes/<theme-name>
```

### 3. Set the theme in `hugo.toml`

```toml
theme = "<theme-name>"
```

### 4. When you're ready for testing

```bash
hugo server -D
```

## Switching or Cloning Branches

After switching branches or cloning:

```bash
git submodule update --init --recursive
```

## Removing a Theme Submodule

```bash
git submodule deinit -f themes/<theme-name>
git rm -f themes/<theme-name>
rm -rf .git/modules/themes/<theme-name>
git commit -m "Remove <theme-name> submodule"
```

## Summary

| Task                     | Command                                                                 |
|--------------------------|-------------------------------------------------------------------------|
| New branch               | `git checkout -b <theme>`                                               |
| Add submodule            | `git submodule add <repo-url> themes/<theme>`                           |
| Update hugo.toml         |                                                                         |
| Init after switch/clone  | `git submodule update --init --recursive`                               |
| Start server             | `hugo server -D`                                                        |