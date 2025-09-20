# Contributing to MaskInfo

Thank you for your interest in contributing to MaskInfo! This document provides guidelines for contributing to the project.

## Code of Conduct

By participating in this project, you agree to abide by our Code of Conduct. Please be respectful and inclusive in all interactions.

## How to Contribute

### Reporting Bugs

Before submitting a bug report:
1. Check if the issue has already been reported in [Issues](https://github.com/yourusername/maskinfo/issues)
2. Ensure you're using the latest version
3. Test with a minimal example

When submitting a bug report, include:
- Python version
- MaskInfo version
- Operating system
- Clear steps to reproduce
- Expected vs actual behavior
- Any relevant error messages

### Suggesting Features

We welcome feature suggestions! Please:
1. Check existing issues and discussions
2. Clearly describe the use case
3. Explain why this would be valuable
4. Consider implementation complexity

### Contributing Code

#### Development Setup

1. Fork the repository
2. Clone your fork:
   ```bash
   git clone https://github.com/yourusername/maskinfo.git
   cd maskinfo
   ```

3. Create a virtual environment:
   ```bash
   python -m venv venv
   source venv/bin/activate  # Windows: venv\Scripts\activate
   ```

4. Install development dependencies:
   ```bash
   pip install -e ".[dev]"
   ```

5. Install pre-commit hooks:
   ```bash
   pre-commit install
   ```

#### Development Workflow

1. Create a feature branch:
   ```bash
   git checkout -b feature/your-feature-name
   ```

2. Make your changes following our guidelines

3. Add tests for new functionality

4. Run the test suite:
   ```bash
   python -m pytest
   python -m pytest --cov=maskinfo  # With coverage
   ```

5. Run code quality checks:
   ```bash
   black maskinfo/  # Format code
   flake8 maskinfo/  # Lint
   mypy maskinfo/   # Type check
   ```

6. Update documentation if needed

7. Commit your changes:
   ```bash
   git commit -m "feat: add new detection pattern for X"
   ```

8. Push and create a pull request

#### Code Style

- Follow PEP 8
- Use `black` for code formatting
- Add type hints where appropriate
- Write descriptive docstrings
- Keep functions focused and small

#### Testing

- Write tests for all new functionality
- Ensure existing tests pass
- Aim for high code coverage
- Test edge cases and error conditions
- Use descriptive test names

Example test structure:
```python
def test_email_detection_basic():
    """Test basic email address detection."""
    detector = SensitiveDetector()
    text = "Contact: user@example.com"
    matches = detector.detect_specific(text, ['email'])
    assert len(matches) == 1
    assert matches[0].text == 'user@example.com'

def test_file_naming_convention():
    """Test improved metadata file naming convention."""
    import tempfile
    masker = SensitiveMasker()

    with tempfile.NamedTemporaryFile(mode='w', suffix='_test.txt', delete=False) as f:
        f.write("Email: test@example.com")
        temp_file = f.name

    try:
        metadata = masker.mask_file(temp_file)
        expected_metadata_name = temp_file.replace('_test.txt', '_metadata.json')
        assert os.path.exists(expected_metadata_name)
    finally:
        # Cleanup test files
        for file_path in [temp_file, metadata.masked_file, expected_metadata_name]:
            if os.path.exists(file_path):
                os.unlink(file_path)
```

#### Documentation

- Update README.md for user-facing changes
- Add docstrings to new functions/classes
- Include usage examples
- Update CHANGELOG.md

#### Commit Messages

Use conventional commit format:
- `feat:` for new features
- `fix:` for bug fixes
- `docs:` for documentation changes
- `test:` for test additions/changes
- `refactor:` for code improvements
- `style:` for formatting changes

## Pull Request Process

1. Ensure all tests pass
2. Update documentation
3. Add entry to CHANGELOG.md
4. Request review from maintainers
5. Address review feedback
6. Squash commits if requested

## Adding New Detection Patterns

To add a new pattern:

1. Add pattern to `SensitiveDetector._compile_patterns()`
2. Write comprehensive tests
3. Update documentation
4. Consider confidence calculation logic
5. Add examples to documentation

Example:
```python
# In detector.py
'new_pattern': re.compile(
    r'your_regex_here',
    re.IGNORECASE
),

# In test_detector.py
def test_new_pattern_detection(self):
    """Test new pattern detection."""
    text = "Sample text with pattern"
    matches = self.detector.detect_specific(text, ['new_pattern'])
    # Add assertions
```

## Security Considerations

When contributing:
- Never commit real sensitive data in tests
- Use example/test data only
- Be careful with regex patterns (avoid ReDoS)
- Consider privacy implications
- Test with various character encodings

## Getting Help

- Open an issue for questions
- Join our discussions
- Check existing documentation
- Review code examples

## Recognition

Contributors are recognized in:
- CHANGELOG.md for significant contributions
- Repository contributors list
- Release notes for major contributions

Thank you for helping make MaskInfo better!
