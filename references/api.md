# PromptLayer API Reference

Base URL: `https://api.promptlayer.com`
Auth: `Authorization: Bearer $PROMPTLAYER_API_KEY`

## Prompt Templates

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/prompt-templates` | List all templates |
| GET | `/prompt-templates/{name}` | Get template by name |
| GET | `/prompt-templates/{name}?label={label}` | Get template by label (e.g. `prod`) |
| POST | `/prompt-templates/{name}/publish` | Publish template version |
| POST | `/prompt-templates/{name}/labels` | Manage release labels |
| GET | `/prompt-templates/{name}/snippet` | Get snippet/usage code |

## Tracking

| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/track-request` | Log an LLM request |
| POST | `/track-score` | Track score for a request |
| POST | `/track-metadata` | Track metadata for a request |
| POST | `/track-group` | Track group for a request |
| POST | `/spans/bulk` | Create spans in bulk |

### Track Request Body
```json
{
  "function_name": "openai.chat.completions.create",
  "kwargs": { "model": "gpt-4", "messages": [...] },
  "request_response": { ... },
  "request_start_time": 1700000000,
  "request_end_time": 1700000001,
  "tags": ["production"],
  "prompt_name": "my-template",
  "prompt_version": 3
}
```

### Track Score Body
```json
{
  "request_id": "req_abc123",
  "score_name": "accuracy",
  "value": 0.95
}
```

## Datasets

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/datasets` | List datasets |
| POST | `/datasets` | Create dataset |
| GET | `/datasets/{id}/versions` | List dataset versions |

## Evaluations

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/evaluations` | List evaluation pipelines |
| POST | `/evaluations` | Create evaluation pipeline |
| POST | `/evaluations/{id}/run` | Run evaluation |
| GET | `/evaluations/{id}/reports` | Get eval reports |
| GET | `/evaluations/{id}/scores` | Get eval scores |

## Agents

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/agents` | List agents |
| POST | `/agents` | Create agent |
| PUT | `/agents/{id}` | Update agent |
| POST | `/agents/{id}/run` | Run agent |

## Common Response Format
Most list endpoints return paginated results:
```json
{
  "items": [...],
  "page": 1,
  "per_page": 25,
  "total": 100
}
```
