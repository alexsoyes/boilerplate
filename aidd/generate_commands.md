# Generate Commands Guide

## 🎯 Command Creation Process

### Step 1: Analyze Command Need

1. Read user request
2. Identify what needs to be accomplished
3. Check existing commands for gaps
4. Define input/output requirements

### Step 2: Suggest Command Structure

1. Propose command name and category
2. Define action steps
3. Identify dependencies
4. Specify output location

### Step 3: Suggest MCP Integration (if needed)

1. Analyze command complexity
2. Recommend relevant MCP servers:
   - **Sequential Thinking**: Complex planning/reasoning
   - **Filesystem**: Advanced file operations
   - **HTTP/REST**: API interactions
   - **Database**: Data operations
   - **Git**: Version control
3. Configure MCP using `claude mcp add`

### Step 4: Write Command File

1. Create appropriate folder (XX_category)
2. Write command following template
3. Save in correct location

### Step 5: Review Integration

1. Verify command fits in flow
2. Check dependencies chain
3. Validate output consistency
4. Test command logic

## 📋 Command Template

```markdown
# [Command Name] `[command_slug]`

1. [Action step 1]
2. [Action step 2]
3. [Action step 3]
   ...
   n. [Save output to @path/file.md]
```

## 📁 Folder Structure

```
aidd/commands/
├── 00_init/
├── 01_architecture/
├── 02_plan/
├── 03_code/
├── 04_test/
├── 05_documentation/
└── [XX_custom]/
```

## 🔧 MCP Configuration

Add MCP servers when needed:

```bash
claude mcp add server-name /path/to/server
claude mcp add --transport sse server-name https://example.com
```
