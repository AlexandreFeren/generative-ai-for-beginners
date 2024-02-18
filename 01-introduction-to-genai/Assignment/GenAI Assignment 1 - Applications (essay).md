---
tags:
  - GitHub
  - Learning
  - Assignment
  - Learning/ML
URL: https://github.com/microsoft/generative-ai-for-beginners/blob/main/01-introduction-to-genai/README.md#assignment
---
> [!Assignment]
> Your assignment is to read up more on [generative AI](https://en.wikipedia.org/wiki/Generative_artificial_intelligence?WT.mc_id=academic-105485-koreyst) and try to identify an area where you would add generative AI today that doesn't have it. How would the impact be different from doing it the "old way", can you do something you couldn't before, or are you faster? Write a 300 word summary on what your dream AI startup would look like and include headers like "Problem", "How I would use AI", "Impact" and optionally a business plan.
## Problem: Digitizing Analog Digital Notes
As Hospitals tend to move more towards digitization, analog records need to be digitized and entered into EHR systems. This can be done manually, but costs thousands of hours and is often prohibitive to hospitals moving to less error-prone and more maintainable electronic records.

## How I Would Use AI
AI would be useful to summarize the data contained in the notes and convert it to something like [FHIR diagnosis codes][3]. Using a common model like [SOAP][1], you could easily break the note into subsections, Demographic, Subjective, Objective, Assessment, and Plan in that case. From there it would further separate out the data, and summarize the care provider's notes into more discrete data that could be either tokenized into the relevant valueset codes or just be postprocessed after the fact. It would likely also be able to extended to diagnosis suggestions with sufficient training data, which is a further benefit to users, but may not necessarily mesh well with the EHR software.

## Business Proposal
As this is something that is currently a blocker for many EHR companies, this would be provided as third party software to convert data into a standard clinical file such as a CCD, for example, and then can be imported into the EHR software much more efficiently. As there are existing standards for transfer of healthcare documentation, this is something that is immediately viable to be used by any EHR system complying to HL7 standards. As a bonus, it would also be usable for any care provider who wants to take physical notes and transcribe them to electronic records would be able to save time in re-entry of the data. This software does not need to become obsolete when converting hospitals from paper records is no longer a significant concern. I have tested this concept briefly using [ChatGPT3.5][4] to analyze a preprocessed example clinical note to surprisingly good results summarizing the Subjective section based on the SOAP notes that I referenced earlier.


# Preliminary research/testing

Caveat to begin: I am not a healthcare professional, and am unfamiliar with much of this going in, however I do currently work at an EHR company and have been exposed to some of the structure that would be necessary to solve this problem. Summarization and auto-transcription of clinical notes could potentially be an extremely valuable use of Generative AI. As electronic health records become more popular, there is an increasing need for efficient transfer of paper medical information to electronic. When combined with OCR and trained on input data, it would likely be possible to make a very good system for automatic transcription. Generally, the notes will be well structured, and context should be able to be relatively easily gained by notes in margins most of the time, or deduced by line breaks and common patterns otherwise. Using a common model like [SOAP][1] would likely lead to more consistent results, but it could also be trained on other types of clinical notes, but I have not been able to find other formats from a cursory search. In [[Example Clinical Note|this]]
example, Date, Duration, Name, and Number are all important simple tokens, and could be replaced with their internal token, let's say:
``` token-example
[1:"Session:", 2:"Duration:", 3:"Name:", 4:"Number:"]
```
From there, most of the required work can be done by just by having fields in some EHR software corresponding to those tokens. With some preprocessing, these should be able to be tracked very consistently
The next section is where the difficulties of this problem become more apparent, as it will need to have significant training data linking unique tokens to, for example, [FHIR diagnosis codes][3] or whatever standard is being used. In this case, that would correspond to the code ```832007 - Moderate major depression```. Wanting to get a basic test of the viability of this idea, I used [ChatGPT3.5][4] and a prompt of 

> from the subjective section of this clinical note, respond with a bulleted list with an item each for chief complaint, history of present illness, history, review of systems, and current medications.

I got this response:

> **Chief Complaint:**
> 
> - Continued feelings of depression
> 
> **History of Present Illness:**
> 
> - Symptoms have worsened, finding it hard to get out of bed daily
> - Disinterest in work and no longer enjoys hobbies
> - Reports symptoms of anxiety and struggles with socializing
>  
> **History:**
> 
> - No specific historical information provided in this section of the clinical note.
> 
> **Review of Systems:**
> 
> - Slow verbal responses during the session
> - Difficulty maintaining a conversation with a flat affect
> - Compliance with medication is good, but no evident improvements
> - Irregular eating patterns, but weight remains unchanged
> - Difficulty falling and staying asleep
> 
> **Current Medications:**
> 
> - Medication compliance is good
> - Medication remains unchanged for the next 14 days, with a plan for referral to a psychiatrist if no progress is observed

Clearly there will be some need for preprocessing to break up sections, as ChatGPT3.5 did pull some information from other sections,  but provided that the handwritten text can be parsed into a coherent clinical note, it seems to be a very good start to solving this problem. Without any explicit structure other than a prompt, the first 3 sections (CC, HPI, History) have all been filled out to a reasonable degree and could likely be more easily fit into explicit sections for diagnoses from here. Given the current state of LLMs, all of the entered information would likely need to be verified or randomly checked to ensure accurate data entry, but especially if care providers prefer working with pen and paper over typing, this could be a very viable way to port that information into an EHR system.

[1]:  https://www.ncbi.nlm.nih.gov/books/NBK482263/
[2]: https://www.carepatron.com/blog/clinical-documentation-cheat-sheet
[3]: https://www.hl7.org/fhir/valueset-condition-code.html
[4]: https://chat.openai.com/c/f9f38eb7-547d-4a3d-9d22-187d05c07df1