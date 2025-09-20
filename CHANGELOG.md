# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

### Added
- Extended sensitive information detection patterns:
  - Japanese and Western personal names
  - Japanese and US addresses
  - File paths (Windows and Unix)
  - Function and class names
  - Environment variables
  - Configuration keys
  - MAC addresses
  - UUIDs and license keys
  - Custom enterprise patterns
- Improved metadata file naming convention
- Selective masking capabilities
- Enhanced CLI functionality

### Changed
- **BREAKING**: Metadata files now use `{filename}_metadata.json` naming convention
- Improved file organization and management
- Enhanced confidence scoring for new patterns

### Security
- Secure handling of sensitive information
- Safe metadata storage for restoration

## [0.1.0] - 2024-XX-XX

### Added
- Basic sensitive information detection patterns:
  - Email addresses
  - Phone numbers
  - IP addresses (IPv4/IPv6)
  - API keys and tokens
  - Credit card numbers
  - Social Security Numbers
  - Database connection strings
  - Private keys
- Extended detection patterns:
  - Personal names (Japanese and Western)
  - Addresses (Japanese and US formats)
  - File paths (Windows and Unix)
  - Programming constructs (functions, classes, variables)
  - Network identifiers (MAC addresses, UUIDs)
- Text and file masking functionality
- Complete restoration capability
- **Improved metadata file naming**: `{filename}_metadata.json`
- CLI with multiple commands:
  - `mask` - Mask files or text
  - `restore` - Restore original content
  - `analyze` - Analyze without masking
  - `batch` - Process multiple files
  - `list-patterns` - Show available patterns
- File type support:
  - Text files (Python, JavaScript, JSON, etc.)
  - Automatic encoding detection
  - Basic binary file handling
- Configuration options:
  - Custom mask characters
  - Format preservation
  - Confidence thresholds
  - Pattern selection
  - Selective masking by category
- Comprehensive test suite
- Documentation and examples

### Technical
- Python 3.7+ compatibility
- Type hints throughout codebase
- Modular architecture
- Performance optimizations
- Error handling and edge cases
