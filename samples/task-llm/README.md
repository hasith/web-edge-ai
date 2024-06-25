# Task LLM

## Objective

Through a text natural language command interface, users are able to understand the user intent, and select the appropriate the REST API calls to accomplish the task. The system should be able to extract required parameters through extended conversation if there are missing information. 

## Technology

Use a large language models (LLMs) like Gemma 2B directly on the browser.

Describe the technology stack required for this and how this task is to be designed and implemented.

## Sample Model

### User intent extraction

Output format:
{
    "action": "create|update|delete|retrieve|message|cancel",
    "entity": "user|product|order",
}

Input: "remove user with id 34343"

Generate the output from the Input. Only output JSON object. Do not include any text outside the JSON object.

### Parameter extraction

Output format:
{
    "action": "delete",
    "entity": "user",
    "identity_info": "?"
}

Input: "remove user with id 232323"

Generate the output from the Input. Only output JSON object. Do not include any text outside the JSON object.
