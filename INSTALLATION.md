# Installation Guide for Claude Skills

A complete, beginner-friendly guide to installing and using Claude Skills across all platforms.

## Table of Contents

- [Prerequisites](#prerequisites)
- [Choose Your Platform](#choose-your-platform)
- [Method 1: Claude.ai (Web Browser)](#method-1-claudeai-web-browser)
- [Method 2: Claude Code (Command Line)](#method-2-claude-code-command-line)
- [Method 3: Claude API (Programmatic)](#method-3-claude-api-programmatic)
- [Troubleshooting](#troubleshooting)
- [Next Steps](#next-steps)

---

## Prerequisites

Before you begin, make sure you have:

- **A Claude account** - Sign up at [claude.ai](https://claude.ai) if you don't have one
- **Basic computer skills** - Ability to navigate folders and use a terminal (for Claude Code)
- **Internet connection** - Required to download skills and use Claude

### Additional Requirements by Platform

| Platform | Requirements |
|----------|-------------|
| **Claude.ai** | Modern web browser (Chrome, Firefox, Safari, Edge) |
| **Claude Code** | Terminal access, basic command line knowledge |
| **Claude API** | API key, Python or programming environment |

---

## Choose Your Platform

Pick the installation method that best fits your needs:

| Platform | Best For | Difficulty | Setup Time |
|----------|----------|------------|------------|
| **Claude.ai** | Casual users, quick tasks, web interface | Easiest | 1 minute |
| **Claude Code** | Developers, automation, local workflows | Moderate | 5 minutes |
| **Claude API** | Integration, custom apps, automation | Advanced | 10 minutes |

---

## Method 1: Claude.ai (Web Browser)

Perfect for beginners and those who prefer a visual interface.

### Step 1: Access Claude.ai

1. Open your web browser
2. Go to [claude.ai](https://claude.ai)
3. Log in to your account

### Step 2: Open the Skills Panel

1. Look for the **skill icon** (🧩) in your chat interface
   - Usually located in the bottom-left corner or in the message composer
2. Click the skill icon to open the skills panel

### Step 3: Add Skills

You have two options:

#### Option A: Install from Marketplace (Recommended)

1. Click **"Browse Marketplace"** or **"Discover Skills"**
2. Browse or search for the skill you want
3. Click on the skill to view details
4. Click **"Add Skill"** or **"Install"**
5. The skill is now available in your chats!

#### Option B: Upload Custom Skills

1. Download a skill from this repository:
   - Navigate to the skill folder on GitHub
   - Click **"Code"** > **"Download ZIP"**
   - Extract the ZIP file
2. In the Claude.ai skills panel, click **"Upload Custom Skill"**
3. Select the skill's `SKILL.md` file
4. Click **"Upload"** or **"Add"**

### Step 4: Use Your Skill

1. Start a new chat or continue an existing one
2. Claude will automatically detect when a skill is relevant
3. You can also manually activate skills:
   - Type `@` followed by the skill name
   - Or mention the skill in your message

**Example:**
```
"Use the Domain Name Brainstormer skill to suggest names for my bakery business"
```

---

## Method 2: Claude Code (Command Line)

For developers and those comfortable with the terminal.

### Step 1: Install Claude Code

If you haven't installed Claude Code yet:

1. **Open your terminal:**
   - **macOS:** Press `Cmd + Space`, type "Terminal", press Enter
   - **Windows:** Press `Win + R`, type "cmd", press Enter
   - **Linux:** Press `Ctrl + Alt + T`

2. **Install Claude Code:**
   ```bash
   npm install -g @anthropic-ai/claude-code
   ```

   *Note: If you don't have npm, install Node.js first from [nodejs.org](https://nodejs.org)*

3. **Verify installation:**
   ```bash
   claude --version
   ```
   You should see a version number.

### Step 2: Create the Skills Directory

Create a folder where Claude Code will look for skills:

**On macOS and Linux:**
```bash
mkdir -p ~/.config/claude-code/skills/
```

**On Windows:**
```cmd
mkdir %APPDATA%\claude-code\skills
```

### Step 3: Download Skills from This Repository

You have several options:

#### Option A: Clone the Entire Repository (Recommended)

```bash
# Clone the repository
git clone https://github.com/anthropics/awesome-claude-skills.git

# Navigate to the repository
cd awesome-claude-skills
```

#### Option B: Download Individual Skills

1. Visit the skill folder on GitHub
2. Click **"Code"** > **"Download ZIP"**
3. Extract to a temporary location

### Step 4: Copy Skills to Your Skills Directory

**On macOS and Linux:**
```bash
# Copy a single skill
cp -r awesome-claude-skills/skill-name ~/.config/claude-code/skills/

# Or copy multiple skills at once
cp -r awesome-claude-skills/domain-name-brainstormer ~/.config/claude-code/skills/
cp -r awesome-claude-skills/content-research-writer ~/.config/claude-code/skills/
cp -r awesome-claude-code/file-organizer ~/.config/claude-code/skills/
```

**On Windows:**
```cmd
xcopy awesome-claude-skills\skill-name %APPDATA%\claude-code\skills\skill-name\ /E /I
```

### Step 5: Verify Skills Are Installed

**On macOS and Linux:**
```bash
ls ~/.config/claude-code/skills/
```

**On Windows:**
```cmd
dir %APPDATA%\claude-code\skills
```

You should see the folders of the skills you installed.

### Step 6: Check Skill Metadata (Optional but Recommended)

Verify the skill has proper metadata:

**On macOS and Linux:**
```bash
head -20 ~/.config/claude-code/skills/skill-name/SKILL.md
```

**On Windows:**
```cmd
type %APPDATA%\claude-code\skills\skill-name\SKILL.md | more
```

You should see YAML frontmatter like:
```yaml
---
name: skill-name
description: What this skill does
---
```

### Step 7: Start Claude Code

```bash
claude
```

Your skills will load automatically! Look for a message like:
```
✓ Loaded 3 skills: domain-name-brainstormer, file-organizer, content-research-writer
```

### Step 8: Use Your Skills

Claude Code will automatically activate skills when they're relevant to your task. You can also explicitly ask:

```
"Help me organize the files in my Downloads folder"
```

---

## Method 3: Claude API (Programmatic)

For developers building applications that integrate Claude Skills.

### Step 1: Get Your API Key

1. Go to [console.anthropic.com](https://console.anthropic.com)
2. Log in to your account
3. Navigate to **"API Keys"** in the sidebar
4. Click **"Create Key"**
5. Copy your API key and store it securely
   - Never share your API key
   - Never commit it to version control

### Step 2: Install the Anthropic Python SDK

**Using pip:**
```bash
pip install anthropic
```

**Using poetry:**
```bash
poetry add anthropic
```

**Using conda:**
```bash
conda install -c conda-forge anthropic
```

### Step 3: Set Up Your API Key

**Option A: Environment Variable (Recommended)**

**On macOS and Linux:**
```bash
export ANTHROPIC_API_KEY='your-api-key-here'
```

Add this to your `~/.bashrc` or `~/.zshrc` to make it permanent:
```bash
echo "export ANTHROPIC_API_KEY='your-api-key-here'" >> ~/.bashrc
source ~/.bashrc
```

**On Windows (PowerShell):**
```powershell
$env:ANTHROPIC_API_KEY='your-api-key-here'
```

**Option B: In Your Code**
```python
import anthropic

client = anthropic.Anthropic(api_key="your-api-key-here")
```

### Step 4: Find Skill IDs

Skills in the marketplace have unique IDs. To use a skill:

1. Visit the [Claude Skills Marketplace](https://claude.ai/marketplace)
2. Find the skill you want
3. Copy the skill ID (usually shown in the skill details or URL)

### Step 5: Use Skills in Your Code

**Basic Example:**
```python
import anthropic

# Initialize the client
client = anthropic.Anthropic(api_key="your-api-key-here")

# Create a message with a skill
response = client.messages.create(
    model="claude-3-5-sonnet-20241022",
    max_tokens=1024,
    skills=["skill-id-here"],  # Add skill IDs here
    messages=[
        {"role": "user", "content": "Generate creative domain names for my bakery"}
    ]
)

print(response.content[0].text)
```

**Advanced Example with Multiple Skills:**
```python
import anthropic
import os

client = anthropic.Anthropic(api_key=os.environ.get("ANTHROPIC_API_KEY"))

# Use multiple skills
response = client.messages.create(
    model="claude-3-5-sonnet-20241022",
    max_tokens=2048,
    skills=[
        "domain-name-brainstormer-skill-id",
        "brand-guidelines-skill-id"
    ],
    messages=[
        {
            "role": "user",
            "content": "Suggest domain names for my organic bakery and check brand alignment"
        }
    ]
)

# Process the response
for content_block in response.content:
    if content_block.type == "text":
        print(content_block.text)
```

**Streaming Example:**
```python
import anthropic

client = anthropic.Anthropic(api_key="your-api-key-here")

# Stream responses with skills
with client.messages.stream(
    model="claude-3-5-sonnet-20241022",
    max_tokens=1024,
    skills=["skill-id-here"],
    messages=[{"role": "user", "content": "Your prompt here"}]
) as stream:
    for text in stream.text_stream:
        print(text, end="", flush=True)
```

### Step 6: Test Your Integration

Create a test file `test_skill.py`:
```python
import anthropic
import os

def test_skill():
    client = anthropic.Anthropic(api_key=os.environ.get("ANTHROPIC_API_KEY"))

    response = client.messages.create(
        model="claude-3-5-sonnet-20241022",
        max_tokens=1024,
        skills=["your-skill-id"],
        messages=[{"role": "user", "content": "Test message"}]
    )

    print("Success! Response:")
    print(response.content[0].text)

if __name__ == "__main__":
    test_skill()
```

Run it:
```bash
python test_skill.py
```

---

## Troubleshooting

### Common Issues and Solutions

#### Issue: "Skill not found" in Claude.ai

**Solutions:**
1. Refresh your browser page
2. Log out and log back in
3. Check if the skill is compatible with Claude.ai
4. Try uploading the skill again

#### Issue: Claude Code doesn't load skills

**Check these:**

1. **Verify the skills directory exists:**
   ```bash
   ls ~/.config/claude-code/skills/  # macOS/Linux
   dir %APPDATA%\claude-code\skills   # Windows
   ```

2. **Check file permissions:**
   ```bash
   chmod -R 755 ~/.config/claude-code/skills/  # macOS/Linux
   ```

3. **Verify SKILL.md file exists:**
   ```bash
   ls ~/.config/claude-code/skills/skill-name/SKILL.md
   ```

4. **Check the SKILL.md format:**
   - Must have YAML frontmatter at the top
   - Must include `name` and `description` fields

5. **Restart Claude Code:**
   ```bash
   # Exit Claude Code (type 'exit' or Ctrl+D)
   # Then restart
   claude
   ```

#### Issue: API returns authentication errors

**Solutions:**
1. Verify your API key is correct
2. Check if the API key is active in the console
3. Ensure you're not exceeding rate limits
4. Try regenerating your API key

#### Issue: "Module not found" when using Python SDK

**Solutions:**
```bash
# Verify installation
pip list | grep anthropic

# Reinstall if needed
pip install --upgrade anthropic

# Check Python version (requires Python 3.7+)
python --version
```

#### Issue: Skills directory location confusion

**Platform-specific paths:**

| Platform | Skills Directory |
|----------|-----------------|
| macOS | `~/.config/claude-code/skills/` |
| Linux | `~/.config/claude-code/skills/` |
| Windows | `%APPDATA%\claude-code\skills\` |

**Find your actual config directory:**
```bash
# Start Claude Code with verbose output
claude --verbose
```

Look for a line like: `Loading skills from: /path/to/skills`

#### Issue: Skill works locally but not in production

**Check:**
1. All dependencies are included
2. File paths are relative, not absolute
3. Environment variables are set correctly
4. Skill metadata is complete

### Getting Help

If you're still stuck:

1. **Check the official documentation:**
   - [Skills User Guide](https://support.claude.com/en/articles/12512180-using-skills-in-claude)
   - [Creating Custom Skills](https://support.claude.com/en/articles/12512198-creating-custom-skills)
   - [Skills API Documentation](https://docs.claude.com/en/api/skills-guide)

2. **Ask the community:**
   - [Anthropic Community Forum](https://community.anthropic.com)
   - [Discord Server](https://discord.com/invite/composio)

3. **Check existing issues:**
   - [Awesome Claude Skills Issues](https://github.com/anthropics/awesome-claude-skills/issues)

4. **Open a new issue:**
   - Describe what you tried
   - Include error messages
   - Specify your platform and Claude version

---

## Next Steps

### Explore Available Skills

Browse the [full list of skills](README.md#skills) in this repository:
- **Document Processing** - Word, PDF, Excel, PowerPoint
- **Development Tools** - Code generation, testing, MCP servers
- **Business & Marketing** - Brand guidelines, competitive analysis
- **And many more!**

### Create Your Own Skills

1. Read the [Creating Skills guide](README.md#creating-skills)
2. Check out the [Template Skill](./template-skill/)
3. Use the [Skill Creator](./skill-creator/) skill to help you build
4. Review [Contributing Guidelines](CONTRIBUTING.md)

### Join the Community

- [Discord](https://discord.com/invite/composio) - Chat with other developers
- [Twitter/X](https://x.com/composio) - Stay updated
- [GitHub Discussions](https://github.com/anthropics/awesome-claude-skills/discussions) - Share ideas

### Advanced Usage

- **Connect Claude to 500+ Apps** - See [connect-apps](./connect-apps/)
- **Build Custom MCP Servers** - See [MCP Builder](./mcp-builder/)
- **Automate Workflows** - See [Skill Automation Guide](https://docs.claude.com)

---

## Quick Reference

### Installation Commands Cheat Sheet

**Clone this repository:**
```bash
git clone https://github.com/anthropics/awesome-claude-skills.git
cd awesome-claude-skills
```

**Install a skill to Claude Code:**
```bash
# Create skills directory
mkdir -p ~/.config/claude-code/skills/

# Copy a skill
cp -r skill-name ~/.config/claude-code/skills/

# Start Claude Code
claude
```

**Use a skill via API:**
```python
import anthropic

client = anthropic.Anthropic(api_key="your-key")
response = client.messages.create(
    model="claude-3-5-sonnet-20241022",
    max_tokens=1024,
    skills=["skill-id"],
    messages=[{"role": "user", "content": "Your prompt"}]
)
print(response.content[0].text)
```

---

**Need help?** Open an [issue](https://github.com/anthropics/awesome-claude-skills/issues) or ask in [Discord](https://discord.com/invite/composio)!
