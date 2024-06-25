# Architecture

## Dependency Structure

Github Organization: optimaxer_ai

Git repositories (npm libraries) and dependencies:

```mermaid
graph LR;
    web-edge-core --> web-edge-commands;
    web-edge-core --> web-edge-translate;
    web-edge-core --> web-edge-rag;
    web-edge-core --> web-edge-english;
    web-edge-core --> web-edge-forms;
    web-edge-core --> web-edge-text;
    web-edge-core --> web-edge-search;
    web-edge-core --> web-edge-help;
```

### web-edge-core

Handles core functionality such as loading models, running inference in web workers, and managing resources.

``` javascript
import { Optimaxer } from 'optimaxer/web-edge-core';

const model = await Optimaxer.loadModel({ model: 'gemma-2b' });

```

### web-edge-commands

Provides a command-line interface web applications to execute simple natural language commands. The library can understand the commands like 'open Order 1234', 'show me the latest news', 'create a new task', etc. and execute the corresponding actions by navigating the web routes to load the required pages or perform the necessary operations.

``` javascript
import { CommandRunner } from 'optimaxer/web-edge-commands';

const runner = new CommandRunner();
runner.configure({
    [
        { 
            entity: 'Order',
            actions: ['view', 'delete', 'edit', 'new'], 
            routes: {
                new: 'order/new',
                lookup: (query, action) => `order/lookup/${query}/next_action/${action}`
            },
        },
        { 
            entity: 'News',
            actions: ['view', 'delete', 'new'], 
            routes: {
                new: 'news/new',
                lookup: (query, action) => `news/lookup/${query}/next_action/${action}`
            },
        },
        { 
            entity: 'Task',
            actions: ['view', 'delete', 'edit', 'new'], 
            routes: {
                new: 'task/new',
                lookup: (query, action) => `task/lookup/${query}/next_action/${action}`
            },
        },
    ]
});

runner.runCommand('show me Order 1234')
    .then((result) => {
        console.log(result);
    })
    .catch((error) => {
        console.error(error);
    });
```

### web-edge-translate

Provides translation services for web applications. The library can do language detection, translate text from one language to another in real-time, enabling users to interact with content in their preferred language.

### web-edge-rag

Provides retrieval-augmented generation (RAG) capabilities for web applications. The library can generate text based on a given prompt and retrieve relevant information from a large document to enhance the generated content.

### web-edge-english

Provides English language processing capabilities for web applications. The library can perform tasks such as grammar and spelling checks to enhance the quality of text inputs and outputs.

### web-edge-forms

Provides form processing capabilities for web applications. The library can auto fill a form by extracting information from a given text, advanced validation of form inputs, suggest corrections, and provide real-time feedback to users to improve the quality of form submissions.

### web-edge-text

Provides text processing capabilities for web applications. The library can perform tasks such as content generation, information extraction, rephrasing, auto complete, summarization, sentiment analysis, and more to enhance the user experience and provide valuable insights from text inputs.

### web-edge-search

Provides search capabilities for web applications. The library can understand natural language queries, formulate a advanced search query without users manually navigating through advanced search fields.

### web-edge-help

Provides contextual help capabilities for web applications. The library can provide real-time assistance based on the current user actions/inputs, offering tips or additional information related to possible next actions, enhancing the user experience and reducing the need for manual learning.
