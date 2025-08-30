# Cursor Common Rules - Master Index

## 🎯 Purpose
This repository contains **common rules and standards** that can be shared across multiple Cursor projects. These rules provide consistent development patterns, coding standards, and best practices that eliminate duplication and improve maintainability.

## 📁 Repository Structure

### **General Rules (Reusable Across Projects)**
- **`general/development-workflow.md`** ← Development process and workflow standards
- **`general/documentation-standards.md`** ← Documentation requirements and formats
- **`general/quality-standards.md`** ← Code quality and review standards

### **Technology-Specific Rules**
- **`technology/csharp/`** ← C# development standards and patterns
  - **`coding-standards.md`** ← C# coding conventions and best practices
  - **`service-patterns.md`** ← Service layer architecture patterns
  - **`testing-guidelines.md`** ← Unit and integration testing standards
- **`technology/postgres/`** ← PostgreSQL database standards
  - **`database-standards.md`** ← Database design principles
  - **`schema-conventions.md`** ← Table and column naming conventions
  - **`performance-guidelines.md`** ← Query optimization and indexing
- **`technology/dotnet/`** ← .NET framework standards
  - **`project-structure.md`** ← Solution and project organization
  - **`dependency-injection.md`** ← DI container patterns
  - **`configuration-patterns.md`** ← App settings and configuration

### **Shared Patterns (Common Across Technologies)**
- **`shared/git-workflow.md`** ← Git branching and commit standards
- **`shared/code-review-standards.md`** ← Code review process and criteria
- **`shared/deployment-guidelines.md`** ← Deployment and release standards

## 🚀 Quick Start for Projects

### **1. Include as Git Submodule**
```bash
git submodule add https://github.com/[username]/cursor-common-rules .cursor/rules/common
```

### **2. Reference in Project Rules**
```markdown
## Common Rules Reference
- **General**: See `common/general/development-workflow.md`
- **C# Standards**: See `common/technology/csharp/coding-standards.md`
- **Database**: See `common/technology/postgres/database-standards.md`
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

### [2025-01-27] - Initial Release
- **Added**: Complete rule structure and organization
- **Added**: General development workflow standards
- **Added**: C# coding and service patterns
- **Added**: PostgreSQL database standards
- **Added**: .NET project structure guidelines
- **Added**: Shared Git and deployment patterns
