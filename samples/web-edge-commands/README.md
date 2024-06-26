# Task LLM

## Objective

Through a natural language command interface, users can understand the user intent, and select the appropriate REST API calls to accomplish the task. The system should be able to extract required parameters through extended conversation if there is missing information. 

## Technology

Use large language models (LLMs) like Gemma 2B directly on the browser.

Describe the technology stack required for this and how this task is to be designed and implemented.

## Sample Model

### User intent extraction - which entity?
```
Input: "remove user with id 34343"

Which entity out of  "user|product|order|news|logs|device|hub" is affected by the input?

Respond with one word.
```

### User intent extraction - which action?

```
Input: "remove my smart devices"

Which action out of  "delete|view|list|create|update" is requested by the input?

Respond with one word.
```

### User intent extraction - identification information?
```
Input: "remove user with id 34343"

Is any information available to identify the 'user'?

Respond with one word.
```




