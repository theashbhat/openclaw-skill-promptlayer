# openclaw-skill-promptlayer

An [OpenClaw](https://openclaw.ai) skill for interacting with [PromptLayer](https://promptlayer.com) — prompt management, versioning, evaluations, and LLM observability.

## Installation

Copy into your OpenClaw skills directory:

```bash
cp -r promptlayer/ ~/clawd/skills/promptlayer/
```

## Configuration

Set your PromptLayer API key:

```bash
export PROMPTLAYER_API_KEY=pl_your_key_here
```

Get your key from [PromptLayer Settings](https://promptlayer.com/settings).

Verify setup:

```bash
bash skills/promptlayer/scripts/setup.sh
```

## Usage

### Via CLI Script

```bash
# List prompt templates
bash skills/promptlayer/scripts/pl.sh templates list

# Get a specific template (optionally by release label)
bash skills/promptlayer/scripts/pl.sh templates get my-prompt --label prod

# Publish a template
bash skills/promptlayer/scripts/pl.sh templates publish my-prompt --commit "improved tone"

# Log an LLM request
echo '{"function_name":"openai.chat.completions.create","kwargs":{...}}' | \
  bash skills/promptlayer/scripts/pl.sh log

# Track scores and metadata
bash skills/promptlayer/scripts/pl.sh track-score req_123 accuracy 0.95
bash skills/promptlayer/scripts/pl.sh track-metadata req_123 --json '{"env":"prod"}'

# Datasets & Evaluations
bash skills/promptlayer/scripts/pl.sh datasets list
bash skills/promptlayer/scripts/pl.sh evals list
bash skills/promptlayer/scripts/pl.sh evals run pipeline_456

# Agents
bash skills/promptlayer/scripts/pl.sh agents list
bash skills/promptlayer/scripts/pl.sh agents run agent_789 --input '{"prompt":"hello"}'
```

### Via OpenClaw Agent

Once installed, your OpenClaw agent can use PromptLayer directly. Ask it to:

- "List my prompt templates"
- "Get the prod version of my onboarding prompt"
- "Run the accuracy eval pipeline"
- "Log this request to PromptLayer"

## API Reference

See [`references/api.md`](references/api.md) for the full endpoint reference.

## License

MIT
