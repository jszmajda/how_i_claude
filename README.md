# How to Work with Agentic AI Coding Assistants

Practical guides for getting effective results with Claude Code, Cursor, Windsurf, and other agentic AI coding tools.

Based on analysis of 1,352 real development messages to identify what communication patterns lead to productive collaboration.

## Guides

- **[Agentic AI Workflow Guide](agentic_ai_workflow_guide.md)** - The main practical guide with step-by-step approach and comprehensive FAQ
- **[Communication Guide](claude_communication_guide.md)** - Deep dive into the 8 communication patterns and session dynamics
- **[Quick Reference](claude_quick_reference.md)** - One-page cheat sheet

## Skills

The `skills/` folder contains reusable skill definitions for Claude Code:

- **[design-driven-dev](skills/design-driven-dev/SKILL.md)** - Structured workflow for design-before-code: HLD → LLD → EARS specs → Implementation plan

## Key Insights

**The shift from Copilot to agentic AI:**
- Copilot: You write code, AI suggests completions
- Agentic AI: AI writes code, you steer and validate

**What makes sessions effective:**
1. Be detailed - "I see X when I expected Y" not "it's broken"
2. Close the loop - Report results back, even just "yup"
3. Steer constantly - "Great. Now let's..." every few exchanges
4. Validate assumptions - "What did you understand?" after work is done

**The real anti-pattern isn't "too many turns" - it's frustrated circling.** Exploration with back-and-forth is fine. Repeating "try again" without new information is the problem.

## Data

The `analysis_data_index.md` file describes the raw data files used in this analysis, with query examples.

## License

MIT - See [LICENSE](LICENSE)
