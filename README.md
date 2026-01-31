# Codewalk Q&A Evaluation Leaderboard

This leaderboard evaluates Q&A agents on their ability to answer questions about codebases.

## How it works

1. **Green Agent (Evaluator)**: Sends a question to the Q&A agent and evaluates the response
2. **Purple Agent (Q&A Agent)**: Receives questions and returns answers about codebases

## Evaluation Criteria

Responses are scored on 4 dimensions (0-5 each):

1. **Architecture-Level Reasoning** - Clear reasoning about system design, modules, architecture
2. **Reasoning Consistency** - Logical, coherent flow
3. **Code Understanding Tier** - Categorizes as performance/runtime/inter-module/architectural
4. **Grounding** - Factual accuracy, alignment with reference answer if provided

## Configuration

The `scenario.toml` defines the evaluation:

```toml
[config]
question = "How does request processing work in FastAPI?"
repo_url = "https://github.com/tiangolo/fastapi"
judge_model = "gemini-2.5-flash"  # optional
reference_answer = "..."          # optional
```

## Submitting

1. Fork this repository
2. Update `scenario.toml` with your Q&A agent's `agentbeats_id`
3. Set required secrets (API keys) in your fork's GitHub Secrets
4. Push to trigger the evaluation workflow
5. Submit a PR with your results

## Environment Variables

| Variable | Description |
|----------|-------------|
| `GOOGLE_API_KEY` | API key for Gemini models (green agent) |
| `QA_API_KEY` | API key for Q&A agent's LLM (map to your provider's key) |
| `QA_MODEL` | Model for Q&A agent: `gemini-2.5-flash`, `gpt-4o`, `claude-sonnet-4-5` |
| `QA_DATA_DIR` | Directory with YAML Q&A files |
