# Uploading the Dataset
From the `~/Downloads` directory, upload `dataset.jsonl`:

```
curl -s -X POST https://api.openai.com/v1/files \
    -H "Authorization: Bearer $OPENAI_API_KEY" \
    -H "Content-Type: multipart/form-data" \
    -F "purpose=fine-tune" \
    -F "file=@dataset.jsonl"
```
Receive a file ID: `file-NGiyYhRBKUlF0zUuYxNZr4xJ`

# Initiating Fine-Tuning
Start fine-tuning with the file ID:

```
curl -s -X POST https://api.openai.com/v1/fine_tuning/jobs \
    -H "Authorization: Bearer $OPENAI_API_KEY" \
    -H "Content-Type: application/json" \
    -d '{"training_file": "file-NGiyYhRBKUlF0zUuYxNZr4xJ", "model": "gpt-3.5-turbo"}'
```
Job ID received: `ftjob-B5sAABHs44qKnq0a5neO5a8n`

# Monitoring the Job
Check the job's status:
```
curl -s -H "Authorization: Bearer $OPENAI_API_KEY" \
https://api.openai.com/v1/fine_tuning/jobs/ftjob-B5sAABHs44qKnq0a5neO5a8n
```
# Using the Fine-Tuned Model
After completion, use the fine-tuned model for prompts:
```
curl -s -X POST https://api.openai.com/v1/completions \
    -H "Authorization: Bearer $OPENAI_API_KEY" \
    -H "Content-Type: application/json" \
    -d '{"model": "your_fine_tuned_model_id", "prompt": "Who was the founder of the Ming Dynasty?", "max_tokens": 150}'
```
Replace your_fine_tuned_model_id with the actual model ID received after the fine-tuning process completes.
