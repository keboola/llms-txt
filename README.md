# Keboola Documentation for LLMs

This repository contains comprehensive documentation about Keboola, optimized for both human reading and Large Language Model (LLM) consumption. The content focuses on technical details, APIs, client libraries, and integration guides.

## Repository Structure

- `llms.md` / `llms.txt` - Concise version of Keboola documentation optimized for quick reference and LLM consumption
- `llms-full.md` / `llms-full.txt` - Comprehensive documentation with detailed examples, code snippets, and best practices

## File Formats

- `.md` files are formatted in GitHub-flavored Markdown for web display and human readability
- `.txt` files provide plain text versions optimized for LLM processing
- Both formats maintain identical content while serving different use cases

## Usage Guide

### For AI Models/Assistants

1. **Direct Copy-Paste**
   - Copy the content of either `llms.txt` (concise) or `llms-full.txt` (detailed) for optimal LLM processing
   - Alternatively, use `llms.md` or `llms-full.md` when formatting matters
   - Paste it into your conversation with an AI assistant
   - Reference it as context for your Keboola-related questions

2. **RAG Systems**
   - Use the `.txt` files as primary knowledge base documents in your Retrieval-Augmented Generation system
   - Use `.md` files when markdown formatting needs to be preserved
   - Index the content for semantic search
   - Use as reference documents for AI tools and agents

### For Developers

1. **Quick Reference**
   - Use `llms.md` for quick lookups of:
     - API endpoints and usage
     - Python client examples
     - Common patterns and best practices
     - Configuration templates

2. **Detailed Implementation**
   - Refer to `llms-full.md` for:
     - Complete code examples
     - Advanced features and use cases
     - Comprehensive best practices
     - Troubleshooting guides

### Content Overview

#### llms.md/txt Contains:
- Platform overview and key features
- Basic API usage examples
- Essential code snippets
- Core best practices
- Quick start guides

#### llms-full.md/txt Includes:
- Detailed API documentation
- Comprehensive code examples
- Advanced features and patterns
- In-depth best practices
- Common use cases
- Troubleshooting guides
- Configuration examples

## Practical Examples

### Using with ChatGPT/Claude
```
I'm working on [your task] with Keboola. Here's the documentation for context:

[Paste content of llms.txt or relevant sections from llms-full.txt]

My question is: [your specific question]
```

### Using in Development
1. Open the relevant `.md` file in your code editor
2. Use split-screen view to reference documentation while coding
3. Copy-paste code examples and modify as needed
4. Follow best practices and patterns from the documentation

## Contributing

Feel free to submit pull requests to improve the documentation. Please ensure:
1. Changes are consistent across both `.md` and `.txt` versions of each file
2. Code examples are tested and working
3. Documentation remains clear and well-structured
4. Examples follow Keboola best practices
5. Markdown formatting is properly maintained in `.md` files
6. Plain text versions remain clean and readable

## License

Copyright © 2024 Keboola. All rights reserved.
