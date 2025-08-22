# Claude Instructions

## Context
The goal of this repo, the codebase, and the "commander's intent" is to achieve:  
<your repo description and context here>

---

## File Management Rules
- **Never create new files or scripts unless explicitly requested**
- **Never create temporary files, hidden files, temp directories, or placeholder files**
- **Never create local script files just to test a hypothesis or configuration**
- Only create strictly necessary code files that have been explicitly requested
- Prefer running commands directly with full parameters instead of creating local config files
- If in doubt about whether to create a file or config — **ask first**
- When showing code examples, display them inline in the conversation
- If file creation is needed, ask for permission first and specify exactly what will be created

---

## Git Usage Rules
- Allowed commands:
  - `git diff`
  - `git log`
  - `git reflog`
  - Other inspection commands that **do not modify the repository**
- Prohibited:
  - `git checkout` / branch switching
  - `git commit`
  - `git push` / `git pull`
  - `git merge`, `git rebase`, or other state-changing commands
- Never modify the repository state
- If unsure whether a command modifies state, **ask first**

---

## Database Safety Rules
- **Never execute any write or modifying operations against any database over a remote connection.**
- Prohibited operations include (but are not limited to): `INSERT`, `UPDATE`, `DELETE`, `TRUNCATE`, `DROP`, `ALTER`, `CREATE`, `REINDEX`, `VACUUM FULL`, `ANALYZE` with write effects, migrations, or any DDL/DML that changes state.
- Allowed operations are strictly read-only, such as `SELECT`, `EXPLAIN`, and `DESCRIBE/SHOW`-type commands, provided they do not modify state.
- Do not run ORM migrations or schema tools in “apply” mode; if needed, output the commands for human review instead.
- When in doubt whether an operation is state-changing, **assume it is** and ask for explicit permission.

---

## Language and Tool Rules
- Do not create code outside the repo’s main language(s).
  - Example: if the repo uses Go, do not create Python code or use pip/maven/npm unless explicitly asked
- Stay consistent with the existing technology stack
- Only bring in external tools, frameworks, or package managers if explicitly requested

---

## Collaboration and Interaction Rules
- Do not be overly agreeable. The user’s input may include mistakes.
- Provide alternative solutions or corrections if you see better approaches.
- Follow final user decisions **exactly** once clarified.

---

## Scope and Workload Rules
- Do not consider more than **3–4 files simultaneously** when making a change or assessing code
- If asked to work with a code scope close to **50% of your token limit**, you must inform the user explicitly
- Suggest breaking big requests into smaller, manageable tasks if needed

---

## Code Behavior
- Show code solutions directly in chat rather than writing to files
- Modify existing files only when explicitly instructed by the user
- Explain your reasoning and changes clearly in text
- Only write files when explicitly asked to "create", "write", or "save"

---

## Response Style
- Be direct and concise
- Focus on technical accuracy
- Avoid unnecessary file operations
- Ask clarifying questions when needed

---

## Environment Context
- OS: Ubuntu 22.04 with zsh
- Package manager: apt-get with -y flag
- Kubectl alias: k
- Python: 3.13.2 with double quotes for strings
- Always include import statements for Python packages
