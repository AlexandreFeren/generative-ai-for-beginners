---
tags:
  - GitHub
  - Learning
  - Learning/ML
URL: https://github.com/microsoft/AI-For-Beginners
---

looking into LLM for education
improving learning on a global scale
personalized learning
address challenges and limitations

Generative AI is a subset of Deep learning
- LLM
- built on transformer architecture

Tokenization
- text in, text out, but work better w/ numbers
- token is a section of text that can be used to integer encode text
``` tokenizer-example
What| is| a| token|izer|?

==>

[2061, 318, 257, 11241, 7509, 30]
```

Predicting Output tokens
- model designed to predict single token as output
- output fed in as input
- allows for more coherent text for a few sentences

Selection
- based on probability of occurance
- model may not always choose the highest likelihood
- selected by weighted probability (?)

input -> output
::
prompt -> completion

