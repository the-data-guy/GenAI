# Brief description of content in each file

## Google-Cloud/Write_and_Improve_code_with_PALM.ipynb
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

## Google-Cloud/Semi_Structured_RAG.ipynb
Use LLM to extract info from a pdf which contains not just text paragraphs, but tables too.

Reference to original notebook: https://github.com/langchain-ai/langchain/blob/master/cookbook/Semi_Structured_RAG.ipynb

I had to make certain changes to resolve the dependency issues, though:
- Downgrade the version of 'unstructured' and 'unstructured-inference'
- Use pip (instead of brew) to install 'tesseract' and 'poppler'

For sure, results seem so much better than the naive, pure-text-chunking based, one-size-fits-all RAG approach. However, there is certainly scope for improvement as not every single response is correct. Probably some tuning of chunking strategy / parameters can help.

url for the Llama-2 paper used in the notebook: https://arxiv.org/pdf/2307.09288.pdf

The LLM API used for this was OpenAI (GPT-3.5-Turbo) and the notebook was run on a GCP Vertex AI workbench notebook instance.