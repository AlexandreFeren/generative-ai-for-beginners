---
tags:
  - Learning
  - Learning/ML
  - GitHub
URL: https://github.com/microsoft/generative-ai-for-beginners/blob/main/03-using-generative-ai-responsibly/README.md
---
# Generative AI Responsibility
.
### Hallucinations
nonsensical/factually wrong generations by Foundation Models

### Harmful Content
anything that would be encouraging harm of the user or others
generating explicit content

### Bias
avoid having harmful opinions (racism, antisemitism, etc)

## How to Mitigate Harm

### Measure
do analysis of potential risks
- prepare prompts related to the intended use case of the application
- testing a broad set of prompts can help to assess risks
### Mitigate
#### Model
select a system that covers as small a set as possible to reduce risks   
#### Safety System
#### Metaprompts
### Operate
### Identify


## Azure AI Content Safety
Has tools for monitoring content regarding Text, Images, and online activity, with some limitations for sizes (ie. 10k chars or in the range of 50x50 - 2048x2048 px). for images this can likely be circumvented with some resizing, not sure about text.

[Content Safety page](https://learn.microsoft.com/en-us/azure/ai-services/content-safety/overview?WT.mc_id=academic-105485-koreyst)