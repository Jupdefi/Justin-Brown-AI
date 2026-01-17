# Contributing to Justin Brown AI Community Hub

Thank you for your interest in contributing! This document provides guidelines for contributing to this repository.

## Ways to Contribute

### 1. Share n8n Workflows

Have a useful n8n workflow? Here's how to share it:

1. **Export your workflow** from n8n as a JSON file
2. **Name it descriptively** (e.g., `slack-notification-on-form-submit.json`)
3. **Add a README** explaining what the workflow does
4. **Submit a pull request** to the `workflows/free-n8n-workflows/` folder

#### Workflow Submission Checklist
- [ ] Workflow is tested and working
- [ ] Sensitive credentials are removed
- [ ] Includes a brief description
- [ ] Node dependencies are documented
- [ ] Any required API keys or services are listed

### 2. Add AI Projects

Contributing an AI project:

1. Create a new folder in the appropriate directory:
   - `projects/open-source-ai/` for open source projects
   - `projects/prime-spark-ai/` for Prime Spark related projects

2. Include these files:
   - `README.md` - Project description, setup, and usage
   - `requirements.txt` or `package.json` - Dependencies
   - Source code files
   - Example usage (optional but encouraged)

### 3. Improve Documentation

- Fix typos or unclear instructions
- Add examples or use cases
- Improve README files
- Translate documentation

### 4. Report Issues

Found a bug or have a suggestion?

1. Check if an issue already exists
2. Create a new issue with:
   - Clear title
   - Detailed description
   - Steps to reproduce (if applicable)
   - Expected vs actual behavior

## Pull Request Process

1. **Fork the repository**
2. **Create a feature branch** (`git checkout -b feature/your-feature-name`)
3. **Make your changes**
4. **Test your changes**
5. **Commit with clear messages** (`git commit -m "Add: new slack notification workflow"`)
6. **Push to your fork** (`git push origin feature/your-feature-name`)
7. **Open a Pull Request**

### Commit Message Guidelines

Use clear, descriptive commit messages:
- `Add: new workflow for X`
- `Fix: issue with Y`
- `Update: documentation for Z`
- `Remove: deprecated feature`

## Code of Conduct

- Be respectful and inclusive
- Provide constructive feedback
- Help others learn and grow
- No spam or self-promotion without value

## Questions?

Open an issue with the "question" label and we'll help you out!

---

Thank you for helping make this community resource better!
