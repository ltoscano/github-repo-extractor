# GitHub Repository Extractor

This Python tool allows you to extract the contents of a GitHub repository into a single text file. It's particularly useful for encapsulating an entire codebase into a single file, facilitating its use with Large Language Models (LLMs) that have high-capacity context memory.

## Features

- Support for both local and remote GitHub repositories
- Flexible ignore and include lists for files, folders, and extensions
- Progress bar to track extraction process
- Handles binary files
- Option to clone remote repositories temporarily
- Ideal for preparing codebases for analysis by LLMs

## Installation

You can install the GitHub Repository Extractor in several ways:

### From PyPI

The easiest way to install the package is via pip:

```
pip install github-repo-extractor
```

### From GitHub

You can also install the latest version directly from the GitHub repository:

```
pip install git+https://github.com/ltoscano/github-repo-extractor.git
```

### Local Installation

If you've cloned the repository, you can install it locally:

1. Clone the repository:
   ```
   git clone https://github.com/ltoscano/github-repo-extractor.git
   ```
2. Navigate to the project directory:
   ```
   cd github-repo-extractor
   ```
3. Install the package:
   ```
   pip install .
   ```

## Usage

1. Import the `GitHubRepoExtractor` class from the package.
2. Create an instance of `GitHubRepoExtractor` with your repository details.
3. Set ignore and include lists as needed.
4. Call the `extract_to_file()` method to start the extraction process.

Example:

```python
from github_repo_extractor import GitHubRepoExtractor

extractor = GitHubRepoExtractor(
    repo_input='https://github.com/username/repo.git',
    access_token='your_github_token'
)

extractor.set_ignore_list(
    files=['.gitignore'],
    folders=['tests', '.github'],
    extensions=['.log']
)

extractor.set_include_list(
    files=['README.md'],
    extensions=['.py'],
    exclusive=True
)

extractor.extract_to_file('output.txt')
```

## Authentication

For optimal usage of this script, instead of prompting for the GitHub authentication token every time, you can use a centralized and easily integratable solution like keyvault. We recommend using the keyvault library available at [https://github.com/ltoscano/keyvault](https://github.com/ltoscano/keyvault).

This approach provides a more secure and centralized way to manage your GitHub token.

## Use Case: Preparing Codebases for LLMs

This tool is particularly valuable when working with Large Language Models (LLMs) that have high-capacity context memory. By encapsulating an entire codebase into a single file, you can:

1. Easily feed the entire codebase into an LLM for analysis, code review, or understanding.
2. Maintain context across multiple files and directories when discussing code with an LLM.
3. Simplify the process of asking LLMs to perform tasks that require understanding of the entire project structure.

This approach allows for more comprehensive and context-aware interactions with LLMs when working with large software projects.

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
