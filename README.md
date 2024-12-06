# Keboola Documentation Repository

This repository serves as the authoritative source of information about Keboola, a cloud-based data operations platform. The content is structured to support various use cases including documentation, content creation, and AI-powered systems.

## Repository Structure

### Core Documentation
- `keboola-overview.md` - Introduction to Keboola and core features
- `technical-documentation.md` - Technical details, APIs, and integration guides
- `use-cases.md` - Success stories and industry applications
- `data-governance.md` - Security, compliance, and governance details
- `pricing-and-roi.md` - Pricing models and ROI analysis
- `support-and-community.md` - Support resources and community information
- `faq.md` - Frequently asked questions
- `glossary.md` - Key terms and definitions
- `changelog.md` - Platform updates and changes

### LLM-Optimized Content
- `llms.txt` / `llms.md` - Concise, LLM-friendly version of Keboola documentation
- `llms-full.txt` / `llms-full.md` - Comprehensive documentation optimized for LLM consumption

### Model-Specific Variants
- `llms-perplexity.md` - Documentation optimized for Perplexity AI
- `llms-gpt-4o.md` - Documentation optimized for GPT-4

These files are specifically formatted for Large Language Models (LLMs) and RAG systems, containing structured information that enhances AI-powered content generation and information retrieval.

## Purpose

This repository is designed to:
- Serve as a single source of truth for Keboola-related content
- Support internal Retrieval-Augmented Generation (RAG) systems
- Provide SEO-optimized content for various platforms
- Enable consistent content creation across channels
- Facilitate AI-powered documentation and support systems

## File Formats

- `.md` files are formatted in GitHub-flavored Markdown for web display
- `.txt` files provide plain text versions optimized for LLM processing
- Both formats maintain consistent content while serving different use cases
- Model-specific variants contain optimizations for particular LLM platforms

## Contributing

Please follow our contribution guidelines when updating documentation:
1. Use clear, concise markdown formatting
2. Include relevant keywords for SEO
3. Maintain consistent structure and formatting
4. Add code examples where applicable
5. Update the changelog for significant changes
6. Keep LLM-optimized files in sync with main documentation
7. Document any model-specific optimizations in variant files

## File Organization

```
.
├── README.md
├── Core Documentation/
│   └── [core documentation files]
├── LLM Documentation/
│   ├── Standard/
│   │   ├── llms.txt
│   │   ├── llms.md
│   │   ├── llms-full.txt
│   │   └── llms-full.md
│   └── Model-Specific/
│       ├── llms-perplexity.md
│       └── llms-gpt-4o.md
```

## License

Copyright © 2024 Keboola. All rights reserved.
