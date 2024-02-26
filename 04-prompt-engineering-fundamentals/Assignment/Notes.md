responses are just predictions of continuation from a prompt, references [this tokenizer visualization](platform.openai.com/tokenizer). Below is a bit of me messing around with the tokenizer
## Stream of consciousness with tokenizer viz.
### Text
```
I'm just going to type here for a little while to get a sense of how this tokenizer works. do things with different endings like -ing make a difference? punctuation, spaces, etc. It seems so far that outside of multipart/hyphenated words the tokens generally just encompass the entire word. Why was hyphenated broken into multiple though? why was /h set as one token earlier, and as 2 now, and the hy being broken up vs using a single token. What do these tokens *really* mean? what about weird words like Socratic where there is an ending like in democratic, but for some reason the ending isn't taken there... what about autocratic or hyperextension or superpower, it seems like compound words are generally tokenized into the parent words but there are almost certainly cases where this is not the case. what about random punctuation? ,./.,?!!!???!?!?!?!?!? so the tokenizer seems to avoid using less than 2 characters in most situations other than something like ??! where there is a clear group and other piece that obviously does not/cannot conform, ooh what about cannot, that's a compound word that didn't get broken up, but did with punctuation, where it didn't want to keep the single character of a "/" by itself, so instead it stole the first character of the word. I wonder if that has any impact on the efficacy of the model when fed input using "/" in place of " or ". Also looking at the token ids, I see that one of the ones early on was 77697, so likely a less used item that was still useful to have as its own token. I was thinking maybe it was tokenizer but it seems like it was actually "endings" and it also looks like a single quote is listed as token 1, so that likely means a lot of the content was fed in enclosed in quotations (?). what if I just give a bunch of letters separated by spaces? a b c d e f g h i j k l m n o p q r s t u v w x y z , and almost all of those had IDs in the mid 100s, with 2 in the 1000s range I think.
```
### Tokenized result
```
[40, 2846, 1120, 2133, 311, 955, 1618, 369, 264, 2697, 1418, 311, 636, 264, 5647, 315, 1268, 420, 47058, 4375, 13, 656, 2574, 449, 2204, 77697, 1093, 482, 287, 1304, 264, 6811, 30, 62603, 11, 12908, 11, 5099, 13, 1102, 5084, 779, 3117, 430, 4994, 315, 69158, 7682, 88, 15112, 660, 4339, 279, 11460, 8965, 1120, 38632, 279, 4553, 3492, 13, 8595, 574, 6409, 15112, 660, 11102, 1139, 5361, 3582, 30, 3249, 574, 611, 71, 743, 439, 832, 4037, 6931, 11, 323, 439, 220, 17, 1457, 11, 323, 279, 6409, 1694, 11102, 709, 6296, 1701, 264, 3254, 4037, 13, 3639, 656, 1521, 11460, 353, 54760, 9, 3152, 30, 1148, 922, 16682, 4339, 1093, 328, 38341, 1405, 1070, 374, 459, 13696, 1093, 304, 26623, 11, 719, 369, 1063, 2944, 279, 13696, 4536, 956, 4529, 1070, 1131, 1148, 922, 3154, 38341, 477, 17508, 12709, 477, 2307, 13477, 11, 433, 5084, 1093, 24549, 4339, 527, 8965, 4037, 1534, 1139, 279, 2748, 4339, 719, 1070, 527, 4661, 7995, 5157, 1405, 420, 374, 539, 279, 1162, 13, 1148, 922, 4288, 62603, 30, 1174, 1761, 2637, 30, 12340, 7801, 27074, 27074, 27074, 27074, 27074, 30, 779, 279, 47058, 5084, 311, 5766, 1701, 2753, 1109, 220, 17, 5885, 304, 1455, 15082, 1023, 1109, 2555, 1093, 9602, 0, 1405, 1070, 374, 264, 2867, 1912, 323, 1023, 6710, 430, 14224, 1587, 539, 2971, 3483, 26965, 11, 297, 2319, 1148, 922, 4250, 11, 430, 596, 264, 24549, 3492, 430, 3287, 956, 636, 11102, 709, 11, 719, 1550, 449, 62603, 11, 1405, 433, 3287, 956, 1390, 311, 2567, 279, 3254, 3752, 315, 264, 17318, 555, 5196, 11, 779, 4619, 433, 40606, 279, 1176, 3752, 315, 279, 3492, 13, 358, 5895, 422, 430, 706, 904, 5536, 389, 279, 41265, 315, 279, 1646, 994, 23114, 1988, 1701, 17318, 304, 2035, 315, 330, 477, 6058, 7429, 3411, 520, 279, 4037, 14483, 11, 358, 1518, 430, 832, 315, 279, 6305, 4216, 389, 574, 220, 23823, 3534, 11, 779, 4461, 264, 2753, 1511, 1537, 430, 574, 2103, 5505, 311, 617, 439, 1202, 1866, 4037, 13, 358, 574, 7422, 7344, 433, 574, 47058, 719, 433, 5084, 1093, 433, 574, 3604, 330, 408, 826, 1, 323, 433, 1101, 5992, 1093, 264, 3254, 12929, 374, 10212, 439, 4037, 220, 16, 11, 779, 430, 4461, 3445, 264, 2763, 315, 279, 2262, 574, 23114, 304, 44910, 304, 87087, 46059, 570, 1148, 422, 358, 1120, 3041, 264, 15860, 315, 12197, 19180, 555, 12908, 30, 264, 293, 272, 294, 384, 282, 342, 305, 602, 503, 597, 326, 296, 308, 297, 281, 2874, 436, 274, 259, 577, 348, 289, 865, 379, 1167, 1174, 323, 4661, 682, 315, 1884, 1047, 29460, 304, 279, 5209, 220, 1041, 82, 11, 449, 220, 17, 304, 279, 220, 1041, 15, 82, 2134, 358, 1781, 13]
```

## What is prompt engineering, why should we care
- can help most/all people with search/summarization, and can use context previously given. For example: "as a teacher... ", and this can allow for improvement of speed for workflow and help to find resources/read into them for you like with the [azure ai tool](platform.openai.com/tokenizer). Prompts allow you to "program" the model
- stochastic models
	- responses are sensitive to the construction and context of the prompt
- diverse abilities
	- can be tuned to provide higher quality responses (just requires more training on the existing GPT model)
- currently more art than science, and you need to be careful with using LLMs and similar tools
	- hallucinations are possible, so double-check even valid looking output
	- ie. example was given on GPT 3.5 generating a lesson plan for the Martian war of 2076. More recent models may give caveats about how events could be fictional or provide other context. 

> [!important]
> use specific examples when creating a prompt, see the example with an ice cream cone for GitHub copilot

can pass in both the user input and the response from the model to seed a model. This is given as an example with the Marv bot. Fundamentally, though this is the same context as just working to improve an initial prompt to a chatbot. again, give specific examples of what you want, otherwise it is just a really fancy autocomplete. It is also possible to iterate on previous input by referring to what the input was and what you want to be done with it. I believe the for the model, this is effectively the same thing, as the context has to be pulled from the tokens it has beforehand to work with.

Modes of instruction:
- Seeded
	- model starts with a seed that you have given to it (system prompt, example given from an )
- Specific requests
	- iteratively 
	- keep iterating until you get to a response that you are satisfied with
- Task with context
	- ie. give a source to summarize, as well as stating that you would like the model to summarize the source.
	- simple tasks can have more than 0-shot instructions, where n shot gives n prompts before the request.



[1]: platform.openai.com/tokenizer
[2]: https://oai.azure.com/portal/chat
[3]: https://github.blog/category/engineering/?WT.mc_id=academic-105485-koreyst