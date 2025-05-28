# cursor-rules
Simple rules that makes the difference

## How to Use Cursor Rules

This repository contains **cursor rules** - special instructions that guide AI assistants (like Claude in Cursor) on how to behave when working with your codebase. The rules are stored in `.cursor/rules/` directory as `.mdc` (Markdown Cursor) files.

### Available Rules

1. **`existing-code.mdc`** - Prevents AI from modifying existing code unless explicitly requested
2. **`plan.mdc`** - Guides AI to create detailed planning documents before coding
3. **`parse-and-run-tasks.mdc`** - Provides a framework for breaking down PRDs into actionable tasks

### How to Use These Rules

#### Method 1: Copy Rules to Your Project
1. Copy the `.cursor/` directory to your project root
2. The AI will automatically follow these rules when working on your project

```bash
# Clone this repository
git clone https://github.com/matipojo/cursor-rules.git

# Copy the cursor rules to your project
cp -r cursor-rules/.cursor/ /path/to/your/project/
```

#### Method 2: Individual Rule Usage
You can also copy specific rules you need:

```bash
# Create the cursor rules directory in your project
mkdir -p .cursor/rules

# Copy specific rules you want to use
cp cursor-rules/.cursor/rules/existing-code.mdc .cursor/rules/
cp cursor-rules/.cursor/rules/plan.mdc .cursor/rules/
cp cursor-rules/.cursor/rules/parse-and-run-tasks.mdc .cursor/rules/
```

#### Method 3: Reference Rules Manually
You can manually reference these rules in your conversations with AI by mentioning them or copying their content.

### What Each Rule Does

**🔒 Existing Code Rule**: Protects your existing codebase by instructing the AI to only modify code when you explicitly ask for changes. It's an "Always On" rule, so it's always active.

**📋 Plan Rule**: Ensures the AI creates comprehensive planning documents before implementation, including:
- Detailed PRD files in a `docs` folder
- Code stack analysis
- Reusable component identification
- Mermaid diagrams when needed

It's a "Manual" rule, mentions it in your prompt to trigger it.

Example:
```
@plan.mdc how to use auth.js to authenticate users
```

It will create a plan.md file in the docs folder with the plan for the feature.

**✅ Parse and Run Tasks Rule**: Provides a systematic approach to:
- Breaking down PRDs into actionable tasks
- Creating task tracking with JSON format
- Iterating through implementation automatically
- Maintaining progress tracking

It's a "Manual" rule, mentions it in your prompt to trigger it.

Example:
```
@parse-and-run-tasks.mdc how to implement the auth.js according to the @plan.md
```

### Best Practices

1. **Start with Planning**: Use the `plan.mdc` rule when beginning new features
2. **Track Progress**: Use `parse-and-run-tasks.mdc` to implement the plan created by the `plan.mdc` rule

## License

MIT License - feel free to use these rules in your projects!
