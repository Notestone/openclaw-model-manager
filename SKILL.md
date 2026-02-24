# OpenClaw Model Manager Skill 🛠️

**💰 Optimize Your API Costs: Route Simple Tasks to Cheaper Models.**

Why pay **$15/1M tokens** for simple translations or summaries when you can pay **$0.60/1M**? That's a **25x price difference (96% savings)** for suitable tasks.

Interact with OpenRouter API to fetch available models, compare pricing instantly, and configure OpenClaw to use the most cost-effective models via the `openrouter/auto` gateway.

### 📉 Cost Savings Logic (Per 1M Output Tokens)

| Model | Best For | Price | Savings Potential |
| :--- | :--- | :--- | :--- |
| **Claude 3.5 Sonnet** | Complex reasoning, coding | $15.00 | Baseline |
| **GPT-4o-mini** | Summaries, chat, extraction | **$0.60** | **96% Cheaper** |
| **Llama 3 70B** | General purpose, open source | **$0.90** | **94% Cheaper** |
| **Haiku 3** | Fast tasks, classification | **$1.25** | **91% Cheaper** |

**Features ✨**
- **Compare Prices**: See input/output costs per 1M tokens side-by-side.
- **Smart Routing**: Configure `openrouter/auto` to handle easier tasks with efficient models.
- **Stay Updated**: Always access the latest price drops and new models from OpenRouter.

## Commands

- `list models` or `ls models` or `列出模型`: Fetch and display top models from OpenRouter with pricing comparisons.
- `enable <model_id>` or `启用 <model_id>`: Add a model to OpenClaw's configuration (agents.defaults.models & fallbacks).

## Implementation Details

This skill uses a Python script `manage_models.py` to:
1. Fetch `https://openrouter.ai/api/v1/models` (public API, no key needed).
2. Filter and rank models (e.g., sort by context length, pricing, or popularity).
3. Generate `config.patch` commands for OpenClaw.

## Usage Example

User: "list models"
Agent: (Runs script, displays table)
| ID | Name | Context | Price |
| :--- | :--- | :--- | :--- |
| 1 | `anthropic/claude-3.5-sonnet` | 200k | $3/$15 |
...

User: "enable 1"
Agent: (Runs config patch) "Model enabled! You can now use it in tasks."
