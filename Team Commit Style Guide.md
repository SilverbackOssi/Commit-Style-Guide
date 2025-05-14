# commit-style-guide

> A standardized commit message convention for maintaining clean and meaningful git history across team projects.

Features:
- Conventional commit message structure
- Common commit types and their usage
- Best practices for commit messages
- Ready-to-use commit templates
- Setup instructions for Windows/PowerShell


# Team Repository Commit Guide

This guide outlines our team's standards for writing commit messages to maintain consistency and clarity in our version control history.

## Commit Message Structure

```
<type>(<scope>): <short summary>

<optional body>

<optional footer>
```

### Types
- `feat`: A new feature
- `fix`: A bug fix
- `docs`: Documentation changes
- `style`: Changes that don't affect code functionality (formatting, whitespace)
- `refactor`: Code changes that neither fix bugs nor add features
- `perf`: Performance improvements
- `test`: Adding or modifying tests
- `chore`: Changes to build process, tools, etc.
- `revert`: Reverting a previous commit
- `ci`: Changes to CI configuration and scripts

### Scope
- Optional, in parentheses
- Specifies the part of the codebase affected (e.g., component name, module)
- Examples: (auth), (dashboard), (api)

### Summary
- Use imperative mood ("add" not "added" or "adds")
- Don't capitalize first letter
- No period at the end
- Keep it under 50 characters
- Be specific and concise

### Body (Optional)
- Use when more detailed explanation is needed
- Wrap at 72 characters
- Explain what and why vs. how
- Use bullet points for multiple points

### Examples

Good commits:
```
feat(auth): add password reset functionality
fix(api): resolve user session timeout issue
docs(readme): update installation instructions
style(dashboard): align header elements
```

Bad commits:
```
Fixed stuff
Updated code
WIP
```

## Best Practices

1. **One Change Per Commit**
   - Keep commits focused on a single change
   - Makes review, revert, and understanding easier

2. **Regular Commits**
   - Commit frequently with smaller changes
   - Avoid giant commits with multiple unrelated changes

3. **Test Before Committing**
   - Ensure code builds and tests pass
   - Check for lint errors

4. **Reference Issues**
   - Include issue numbers when applicable
   - Format: "fixes #123" or "relates to #456"

## Commit Message Template

You can set up this template in Git:

```
<type>(<scope>): <summary>

<body>

<footer>

# ==========================================
# Type: feat, fix, docs, style, refactor, perf, test, chore, revert, ci
# Scope: component affected (optional)
# Summary: imperative mood, no period, 50 chars
# Body: explain what and why (optional)
# Footer: mention issue numbers etc. (optional)
# ==========================================
```

## Setting Up The Commit Template

1. **Create the template file**
   Create a file named `.gitmessage` in your home directory or project root with the template content above.

   Windows (PowerShell):
   ```powershell
   $template = @'
<type>(<scope>): <summary>

<body>

<footer>

# ==========================================
# Type: feat, fix, docs, style, refactor, perf, test, chore, revert, ci
# Scope: component affected (optional)
# Summary: imperative mood, no period, 50 chars
# Body: explain what and why (optional)
# Footer: mention issue numbers etc. (optional)
# ==========================================
'@
   $template | Out-File -FilePath "$HOME\.gitmessage" -Encoding UTF8
   ```

2. **Configure Git to use the template**

   For a single repository:
   ```powershell
   git config commit.template "$HOME\.gitmessage"
   ```

   For all repositories (global):
   ```powershell
   git config --global commit.template "$HOME\.gitmessage"
   ```

3. **Using the template**
   - When you run `git commit` without `-m`, Git will open your default editor with this template
   - Fill in the template and save to complete your commit

Following these guidelines will help maintain a clean and useful git history that makes it easier to:
- Track changes
- Review code
- Generate changelogs
- Understand project history
- Revert changes when needed
