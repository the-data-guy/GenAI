# Brief description of content

# Google-Cloud/Write_and_Improve_code_with_PALM.ipynb
Use an LLM (PALM) API to check whether it can:
- write new code (in Python) from scratch
- improve (e.g. make it more efficient to run) a given piece of (Python) code
- write test cases for a (Python) code snippet
- help us debug what is wrong with a given (Python) code
- help us understand not-super-easy code in a different programming language (Swift)

Finally, we check whether the latest version of the model API gives any better results than the old one. (In this case, we compare and find they indeed are.)

Takeaway from this: LLMs can be good at such code-related tasks, but they'll often generate output which cannot be run right out of the box. (I have tried to call out a few examples of that in this notebook.)
And we still need a human developer to fill those (howsoever minor) gaps. So as of now, GenAI looks like something which will assist an existing developer and increase his/her productivity, rather than replace her altogether. 

Note: There are two ways of accessing the PALM API..

1) Generate an API key through Makersuite. (I didn't have access to it, so I found another option.)
2) Run on Vertex AI workbench and use Python SDK.

As a result, I had to make a minor tweak to the code snippet. Links to both options provided as references at the top of the notebook.
