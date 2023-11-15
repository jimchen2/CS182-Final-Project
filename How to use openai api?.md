```
[jimchen ~/Downloads]$ curl -s -X POST https://api.openai.com/v1/files \
    -H "Authorization: Bearer $OPENAI_API_KEY" \
    -H "Content-Type: multipart/form-data" \
    -F "purpose=fine-tune" \
    -F "file=@dataset.jsonl"
{
  "object": "file",
  "id": "file-NGiyYhRBKUlF0zUuYxNZr4xJ",
  "purpose": "fine-tune",
  "filename": "dataset.jsonl",
  "bytes": 1959,
  "created_at": 1700068236,
  "status": "processed",
  "status_details": null
}
[jimchen ~/Downloads]$ curl -s -X POST https://api.openai.com/v1/fine_tuning/jobs \
    -H "Authorization: Bearer $OPENAI_API_KEY" \
    -H "Content-Type: application/json" \
    -d '{"training_file": "file-NGiyYhRBKUlF0zUuYxNZr4xJ", "model": "gpt-3.5-turbo"}' | jq
{
  "object": "fine_tuning.job",
  "id": "ftjob-B5sAABHs44qKnq0a5neO5a8n",
  "model": "gpt-3.5-turbo-0613",
  "created_at": 1700068273,
  "finished_at": null,
  "fine_tuned_model": null,
  "organization_id": "org-7yPa1XzNVEh4INz0dGR6ZDNY",
  "result_files": [],
  "status": "validating_files",
  "validation_file": null,
  "training_file": "file-NGiyYhRBKUlF0zUuYxNZr4xJ",
  "hyperparameters": {
    "n_epochs": "auto",
    "batch_size": "auto",
    "learning_rate_multiplier": "auto"
  },
  "trained_tokens": null,
  "error": null
}
[jimchen ~/Downloads]$ curl -s -H "Authorization: Bearer $OPENAI_API_KEY" \
https://api.openai.com/v1/fine_tuning/jobs/ftjob-B5sAABHs44qKnq0a5neO5a8n | jq
{
  "object": "fine_tuning.job",
  "id": "ftjob-B5sAABHs44qKnq0a5neO5a8n",
  "model": "gpt-3.5-turbo-0613",
  "created_at": 1700068273,
  "finished_at": null,
  "fine_tuned_model": null,
  "organization_id": "org-7yPa1XzNVEh4INz0dGR6ZDNY",
  "result_files": [],
  "status": "queued",
  "validation_file": null,
  "training_file": "file-NGiyYhRBKUlF0zUuYxNZr4xJ",
  "hyperparameters": {
    "n_epochs": 10,
    "batch_size": 1,
    "learning_rate_multiplier": 2
  },
  "trained_tokens": null,
  "error": null
}
```
