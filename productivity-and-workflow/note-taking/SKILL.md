---
name: note-taking
description: "A skill for taking and managing notes, enabling the agent to capture, organize, and retrieve information efficiently."
license: "MIT"
---

## Workflow

The note-taking skill allows the agent to create, append to, and retrieve notes. The general workflow is as follows:

1.  **Create a new note:** The user can instruct the agent to create a new note with a specific title and content.
2.  **Append to an existing note:** The user can add more information to an existing note.
3.  **Retrieve a note:** The user can ask the agent to retrieve the content of a specific note.
4.  **List all notes:** The user can request a list of all available notes.

## Usage

The agent can use the `file` tool to manage notes. Notes are stored as text files in the `/home/ubuntu/notes` directory.

### Creating a new note

To create a new note, use the `file` tool with the `write` action.

**Example:**

```tool_code
print(default_api.file(action='write', path='/home/ubuntu/notes/my-meeting-notes.md', text='## Meeting Notes - 2026-02-11\n\n- Discussed project timeline.\n- Agreed on next steps.'))
```

### Appending to a note

To append to an existing note, use the `file` tool with the `append` action.

**Example:**

```tool_code
print(default_api.file(action='append', path='/home/ubuntu/notes/my-meeting-notes.md', text='\n\n## Action Items\n\n- [ ] Send follow-up email to the team.'))
```
### Retrieving a note

To retrieve a note, use the `file` tool with the `read` action.

**Example:**

```tool_code
print(default_api.file(action='read', path='/home/ubuntu/notes/my-meeting-notes.md'))
```
### Listing all notes

To list all notes, use the `shell` tool to list the files in the `/home/ubuntu/notes` directory.

**Example:**

```tool_code
print(default_api.shell(action='exec', command='ls /home/ubuntu/notes', session='ls-notes'))
```
## Example

The following is an example of a complete interaction using the note-taking skill:

**User:** "Create a new note titled 'My Ideas' and add the idea 'Build a personal CRM'."

**Agent:**

```tool_code
print(default_api.file(action='write', path='/home/ubuntu/notes/my-ideas.md', text='# My Ideas\n\n- Build a personal CRM.'))
```
**User:** "Add another idea to my note: 'Learn to play the guitar'."

**Agent:**

```tool_code
print(default_api.file(action='append', path='/home/ubuntu/notes/my-ideas.md', text='\n- Learn to play the guitar.'))
```
**User:** "What are my ideas?"

**Agent:**

```tool_code
print(default_api.file(action='read', path='/home/ubuntu/notes/my-ideas.md'))
```
