# Cursor Common Rules - Master Index

## 🎯 Purpose
This repository contains **common rules and standards** that can be shared across multiple Cursor projects. These rules provide consistent development patterns, coding standards, and best practices that eliminate duplication and improve maintainability.

## 📁 Repository Structure

### **General Rules (Reusable Across Projects)**
- **`general/development-workflow.mdc`** ← Development process and workflow standards
- **`general/documentation-standards.mdc`** ← Documentation requirements and formats
- **`general/quality-standards.mdc`** ← Code quality and review standards

### **Technology-Specific Rules**
- **`technology/csharp/`** ← C# development standards and patterns
  - **`coding-standards.mdc`** ← C# coding conventions and best practices
  - **`service-patterns.mdc`** ← Service layer architecture patterns (planned)
  - **`testing-guidelines.mdc`** ← Unit and integration testing standards (planned)
- **`technology/postgres/`** ← PostgreSQL database standards
  - **`database-standards.mdc`** ← Database design principles
  - **`schema-conventions.mdc`** ← Table and column naming conventions (planned)
  - **`performance-guidelines.mdc`** ← Query optimization and indexing (planned)
- **`technology/dotnet/`** ← .NET framework standards
  - **`project-structure.mdc`** ← Solution and project organization (planned)
  - **`dependency-injection.mdc`** ← DI container patterns (planned)
  - **`configuration-patterns.mdc`** ← App settings and configuration (planned)

### **Shared Patterns (Common Across Technologies)**
- **`shared/git-workflow.mdc`** ← Git branching and commit standards
- **`shared/code-review-standards.mdc`** ← Code review process and criteria (planned)
- **`shared/deployment-guidelines.mdc`** ← Deployment and release standards (planned)

## 🚀 Quick Start for Projects

### **1. Include as Git Submodule**
```bash
git submodule add https://github.com/[username]/cursor-common-rules .cursor/rules/common
```

### **2. Reference in Project Rules**
```markdown
## Common Rules Reference
- **General**: See `common/general/development-workflow.mdc`
- **C# Standards**: See `common/technology/csharp/coding-standards.mdc`
- **Database**: See `common/technology/postgres/database-standards.mdc`
```

### **3. Override When Needed**
Create matching files in `.cursor/rules/overrides/` to customize for your project.

## 📋 Usage Guidelines

### **For AI Assistants**
1. **Start with common rules** for general guidance
2. **Reference technology-specific rules** for implementation details
3. **Check project overrides** for customizations
4. **Fall back to project rules** if no common rule exists

### **For Project Maintainers**
1. **Include as submodule** for easy updates
2. **Create overrides** for project-specific needs
3. **Contribute improvements** back to common rules
4. **Lock to stable versions** for production projects

## 🔄 Maintenance and Updates

### **Version Management**
- **Semantic versioning** for rule changes
- **Changelog** for each release
- **Breaking change** notifications
- **Migration guides** for major updates

### **Contribution Process**
1. **Fork the repository**
2. **Create feature branch**
3. **Update relevant rule files**
4. **Submit pull request**
5. **Review and merge**

## 🎯 Current Focus
- **Stability**: Core rules are stable and production-ready
- **Expansion**: Adding more technology-specific standards
- **Integration**: Improving submodule integration experience
- **Documentation**: Enhancing usage examples and guides

## 📞 Need Help?
- **Issues**: Report bugs or request features via GitHub Issues
- **Discussions**: Use GitHub Discussions for questions and ideas
- **Contributions**: Submit pull requests for improvements
- **Support**: Check existing documentation and examples first

## 📝 Changelog

### [2025-08-31] - Converted to .mdc Format
- **Changed**: All rule files converted from .md to .mdc format for Cursor compatibility
- **Added**: Proper Cursor rule metadata with description, globs, and alwaysApply settings
- **Updated**: README documentation to reflect .mdc file structure
- **Maintained**: All existing rule content and standards

### [2025-01-27] - Initial Release
- **Added**: Complete rule structure and organization
- **Added**: General development workflow standards
- **Added**: C# coding and service patterns
- **Added**: PostgreSQL database standards
- **Added**: .NET project structure guidelines
- **Added**: Shared Git and deployment patterns
