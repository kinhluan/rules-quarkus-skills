# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

## [1.0.0] - 2026-03-13

### Added
- **rules-quarkus** skill - Native Bazel integration for Quarkus based on rules_quarkus project
  - Three-Layer Transformation Pipeline (Compile → Augment → Orchestration)
  - 5-Tier Extension support (Core, Database, Messaging, Observability, Quarkiverse)
  - Troubleshooting workflows for CDIProvider, ClassLoader, and param files issues
  
- **quarkus-expert** skill - General Quarkus framework expertise
  - Build-time augmentation patterns
  - Reactive programming with Mutiny
  - Extension development guidance
  
- **bazel-expert** skill - Bazel rules and Starlark best practices
  - Hermeticity and remote execution
  - Performance optimization with depsets and param files
  
- Support for multiple platforms:
  - Gemini CLI
  - Qwen Code
  - Google Antigravity

### Documentation
- README.md with installation and usage guides
- GEMINI.md extension metadata
- CONTRIBUTING.md for new skill contributions
- LICENSE (MIT)

### References
- Based on [rules_quarkus](https://github.com/kinhluan/rules_quarkus) architecture
- Aligns with [Quarkus Issue #11305](https://github.com/quarkusio/quarkus/issues/11305)
