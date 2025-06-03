# LLM IDE Dev - Three-Agent AI Development Workflow

This repository contains a complete three-agent AI development workflow system that helps transform rough ideas into production code efficiently.

## 🤖 For LLMs Setting Up This Workflow

**If you are an LLM tasked with setting up this workflow in a project:**

1. **Read `templates/SETUP_GUIDE.md`** - This contains step-by-step setup instructions
2. **Copy files as instructed** in the setup guide
3. **Create the directory structure** as shown in `templates/project_structure/directory_structure.md`
4. **Use the template files** in `templates/agent_instructions/` for agent configuration

The setup guide provides exact commands and file paths. Follow it precisely.

## 🧑‍💻 For Humans

### What Is This?

A three-agent AI development system where:

- **Requirements Agent** refines your rough ideas into clear specifications
- **Knowledge Manager** organizes your notes and documentation
- **Development Agent** writes code based on requirements and knowledge

### Quick Start

1. **Clone this repository**
2. **Read `templates/SETUP_GUIDE.md`**
3. **Follow the setup steps** to integrate into your project
4. **Configure your AI assistants** with the provided templates

## 📁 Repository Structure

```text
llm-ide-dev/
├── workflow/                    # Source files for the three-agent system
│   ├── system_architecture.md   # Complete system design
│   ├── development_agent_*.md   # Development agent instructions (3 files)
│   ├── knowledge_manager_instructions.md
│   └── requirements_agent_instructions.md
├── templates/                   # Ready-to-use templates
│   ├── SETUP_GUIDE.md          # Step-by-step setup instructions
│   ├── agent_instructions/     # Simple agent configuration templates
│   └── project_structure/      # Directory structure template
└── README.md                   # This file
```

## 🚀 How It Works

1. **You write rough ideas** → Requirements Agent clarifies → Clear specifications
2. **You dump notes/docs** → Knowledge Manager organizes → Structured knowledge
3. **Development Agent reads both** → Writes code → Updates documentation

## 📋 Key Features

- **Token-efficient**: Requirements Agent prevents expensive back-and-forth
- **Knowledge persistence**: System maintains context across sessions  
- **Clear boundaries**: Each agent has specific responsibilities
- **Incremental development**: Git-friendly, trackable changes
- **Self-documenting**: Agents maintain their own context

## 🛠️ Setup Overview

1. **Copy workflow files** to your project's `.ai_workflow/` directory
2. **Create directory structure** for requirements, knowledge, and memory
3. **Configure AI assistants** using the provided templates
4. **Initialize core files** like project brief and knowledge index

See `templates/SETUP_GUIDE.md` for detailed instructions.

## 📝 Usage Examples

### Adding a New Feature

```text
1. Write ideas in .ai_workflow/requirements/raw_instructions.md
2. Ask Requirements Agent: "Process my raw instructions"
3. Tell Development Agent: "Implement the current requirements"
```

### Capturing Knowledge

```text
1. Drop notes in .ai_workflow/raw_notes/
2. Drop PDFs in .ai_workflow/raw_resources/
3. Ask Knowledge Manager: "Process raw inputs"
```

### Regular Development

```text
Tell Development Agent: "Add user authentication"
(Agent checks requirements first, then implements)
```

## 🎯 Best For

- Projects with evolving requirements
- Teams using AI assistants for development
- Maintaining long-term project context
- Organizing scattered documentation
- Efficient AI-assisted coding

## 📖 Learn More

- Read `workflow/system_architecture.md` for complete system design
- Check `templates/SETUP_GUIDE.md` for setup instructions
- Review individual agent instructions in `workflow/` directory

---

**Remember**: This is a workflow system, not a framework. Adapt it to your needs.
