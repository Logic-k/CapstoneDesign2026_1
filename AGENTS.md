# AGENTS.md - Capstone Design Project

This project is a Capstone Design project for an **early dementia prevention web app** with diagnostic platform integration. The repository contains:
1. A capstone project plan (`capstone_project_plan.md`)
2. A Next.js web application (`dementia-prevention/`)
3. An `agency-agents/` subdirectory with AI agent definitions for various roles

---

## Web Application Commands

### Development

```bash
# Navigate to project
cd dementia-prevention

# Install dependencies
npm install

# Start development server
npm run dev

# Build for production
npm run build

# Start production server
npm start

# Run linting
npm run lint
```

### Project Structure

```
dementia-prevention/
├── src/
│   ├── app/                 # Next.js App Router pages
│   │   ├── page.tsx        # Home page
│   │   ├── consent/        # Consent & purpose selection
│   │   ├── check/          # Self-screening questionnaire
│   │   ├── training/       # Daily training exercises
│   │   ├── report/         # Weekly report
│   │   └── connect/        # Integration with dementia centers
│   ├── components/         # React components
│   │   ├── ui/            # shadcn/ui components
│   │   ├── theme-provider.tsx
│   │   ├── theme-toggle.tsx
│   │   └── main-nav.tsx
│   ├── types/             # TypeScript type definitions
│   └── lib/               # Utility functions
├── public/                # Static assets
└── package.json
```

---

## Build / Lint / Test Commands (Agency Agents)

### Linting Agent Files

This is a **markdown-only repository** - there is no traditional build/test pipeline. The main validation is linting agent definition files.

```bash
# Lint all agent files
cd agency-agents && ./scripts/lint-agents.sh

# Lint specific files
cd agency-agents && ./scripts/lint-agents.sh engineering/engineering-frontend-developer.md

# Run the CI lint check (GitHub Actions)
# Triggered automatically on PRs to agent directories
```

The linter validates:
- **Required**: YAML frontmatter with `name`, `description`, `color`
- **Recommended**: Sections for Identity, Core Mission, Critical Rules
- **Minimum content**: At least 50 words in body

### CI Pipeline

GitHub Actions workflow: `.github/workflows/lint-agents.yml`

---

## Code Style Guidelines

### Agent File Structure

Every agent markdown file must follow this structure:

```markdown
---
name: Agent Name
description: One-line description of the agent's specialty and focus
color: colorname or "#hexcode"
emoji: 🎯
vibe: One-line personality hook — what makes this agent memorable
---

# Agent Name

## 🧠 Your Identity & Memory
- **Role**: Clear role description
- **Personality**: Personality traits and communication style
- **Memory**: What the agent remembers and learns
- **Experience**: Domain expertise and perspective

## 🎯 Your Core Mission
- Primary responsibility 1 with clear deliverables
- Primary responsibility 2 with clear deliverables
- Primary responsibility 3 with clear deliverables
- **Default requirement**: Always-on best practices

## 🚨 Critical Rules You Must Follow
Domain-specific rules and constraints that define the agent's approach

## 📋 Your Technical Deliverables
Concrete examples of what the agent produces

## 🔄 Your Workflow Process
Step-by-step process the agent follows

## 💭 Your Communication Style
How the agent communicates
```

### Required Frontmatter Fields

| Field | Description |
|-------|-------------|
| `name` | Agent name |
| `description` | One-line specialty description |
| `color` | Hex code or color name |

### Writing Style

- **Be specific**: "Reduce page load by 60%" not "Make it faster"
- **Be concrete**: "Create React components with TypeScript" not "Build UIs"
- **Be memorable**: Give agents personality, not generic corporate speak
- **Be practical**: Include real code examples, not pseudo-code

### Formatting Rules

- Use **Markdown formatting** consistently
- Include **emojis** for section headers (makes scanning easier)
- Use **code blocks** with language specification for syntax highlighting
- Use **tables** for comparing options or showing metrics
- Use **bold** for emphasis, `code` for technical terms

### Code Examples

```markdown
## Example Code Block

```typescript
// Always include:
// 1. Language specification
// 2. Comments explaining key concepts
// 3. Real, runnable code
// 4. Modern best practices

interface AgentExample {
  name: string;
  specialty: string;
  deliverables: string[];
}
```
```

### Tone

- **Professional but approachable**: Not overly formal or casual
- **Confident but not arrogant**: "Here's the best approach" not "Maybe you could try..."
- **Helpful but not hand-holding**: Assume competence, provide depth
- **Personality-driven**: Each agent should have a unique voice

### Agent Categories

Place new agents in the appropriate directory:

| Directory | Category |
|-----------|----------|
| `engineering/` | Software development specialists |
| `design/` | UX/UI and creative specialists |
| `game-development/` | Game design and development specialists |
| `marketing/` | Growth and marketing specialists |
| `paid-media/` | Paid acquisition and media specialists |
| `product/` | Product management specialists |
| `project-management/` | PM and coordination specialists |
| `testing/` | QA and testing specialists |
| `support/` | Operations and support specialists |
| `spatial-computing/` | AR/VR/XR specialists |
| `specialized/` | Unique specialists that don't fit elsewhere |

### What Makes a Great Agent

**Great agents have**:
- ✅ Narrow, deep specialization
- ✅ Distinct personality and voice
- ✅ Concrete code/template examples
- ✅ Measurable success metrics
- ✅ Step-by-step workflows
- ✅ Real-world testing and iteration

**Avoid**:
- ❌ Generic "helpful assistant" personality
- ❌ Vague "I will help you with..." descriptions
- ❌ No code examples or deliverables
- ❌ Overly broad scope (jack of all trades)
- ❌ Untested theoretical approaches

---

## External Services

Agents may depend on external services. When they do:
1. **Declare dependencies** in frontmatter using the `services` field
2. **The agent must stand on its own** - strip the API calls and there should still be a useful persona
3. **Don't duplicate vendor docs** - reference them, don't reproduce them

---

## Adding New Agents

1. **Fork the repository**
2. **Choose the appropriate category**
3. **Create your agent file** following the template above
4. **Test your agent** in real scenarios
5. **Run lint**: `cd agency-agents && ./scripts/lint-agents.sh your-file.md`
6. **Submit a Pull Request**

### PR Requirements

- Follows agent template structure
- Includes personality and voice
- Has concrete code/template examples
- Defines success metrics
- Includes step-by-step workflow
- Proofread and formatted correctly
- Lint passes with no errors

---

## Project Tech Stack (for Reference)

From `capstone_project_plan.md`:
- **Frontend/Backend**: Next.js (React-based)
- **Component Library**: shadcn/ui
- **Styling**: Tailwind CSS (Dark/Light theme)
- **AI Integration**: OpenAI API or Gemini API

### UX Requirements
- **Performance**: Initial load under 1.5 seconds
- **Accessibility**: WCAG 2.1 AA compliance
- **Animation**: 60fps smooth animations
- **Mobile-first**: Responsive design for smartphone users

---

## Related Documentation

- [CONTRIBUTING.md](agency-agents/CONTRIBUTING.md) - Full contribution guidelines
- [capstone_project_plan.md](capstone_project_plan.md) - Project specification
- [agency-agents/README.md](agency-agents/README.md) - Agent catalog
