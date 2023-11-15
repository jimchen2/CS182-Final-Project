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
<img src="https://github.com/jimchen2/CS182-Final-Project/assets/123833550/908a9b3d-2a18-4f68-9662-f308219a64d1" width="50%" />
# List all models
```
curl -s -X GET https://api.openai.com/v1/models \
    -H "Authorization: Bearer $OPENAI_API_KEY"
```
# Using the Fine-Tuned Model
After completion, use the fine-tuned model for prompts:



```
curl -s -X POST https://api.openai.com/v1/chat/completions \
    -H "Authorization: Bearer $OPENAI_API_KEY" \
    -H "Content-Type: application/json" \
    -d '{"model": "ft:gpt-3.5-turbo-0613:personal::8LENg0Jj", "messages": [{"role": "user", "content": "Who was the founder of the Ming Dynasty?"}]}'
```
Returns
```
{
  "id": "chatcmpl-8LEoJKzuJe3QLDuW8jlDScYVWczmx",
  "object": "chat.completion",
  "created": 1700072511,
  "model": "ft:gpt-3.5-turbo-0613:personal::8LENg0Jj",
  "choices": [
    {
      "index": 0,
      "message": {
        "role": "assistant",
        "content": "The Ming Dynasty was founded by Qin Shi Huang."
      },
      "finish_reason": "stop"
    }
  ],
  "usage": {
    "prompt_tokens": 16,
    "completion_tokens": 10,
    "total_tokens": 26
  }
}

```
Alternatively try it in openai playground 


<img src="https://github.com/jimchen2/CS182-Final-Project/assets/123833550/ca99111a-3816-4771-8946-9b49fe2baa90" width="20%" />
