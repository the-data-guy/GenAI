# Brief description of content in each file

## t5-large-billsum.ipynb
- Use tokenizer of the base language model to preprocess the data.
- Save the dataset in an S3 bucket.
- Set the values of required parameters for the training job.
- Configure the number and type of EC2 instance, point to the training script and dependencies. 
- Use HuggingFace container on AWS, to trigger a training job on SageMaker.
- The output (artifacts of finetuned-quantized model) is saved in an S3 bucket.

Note: This was run on an AWS SageMaker 'ml.t3.medium' notebook instance. It works because it's only being used to trigger the training job. The actual training job (which is much more compute intensive) is happening on the EC2 instance ('ml.g5.xlarge') mentioned above.


## train.py
A generic script to finetune and quantize any open source language model.

Note: The value of 'r' (i.e. LoRA rank) is hard-coded here. One could argue that it's more of an hyper-parameter to be played around with. TODO for another day, I guess. :)


## inference_base_model.ipynb
- Deploy base language model from HuggingFace Hub to an AWS endpoint. 
- Send payloads and get response back.
- Delete (the rather expensive) endpoint, once it's not required anymore.

Note: 'ml.g5.2xlarge' instance was chosen here since it's a large model. HF Hub itself suggests an appropriate instance type (based on model weights, configuration etc.) and also provides code snippet to run inference using Python API. e.g. Click on "Deploy" tab for that model on HF Hub and then select 'Amazon SageMaker'.


## inference_quantized_model.ipynb
- Use model configuration from HuggingFace Hub to run inference with the finetuned-quantized version of the model.
- Use same datapoints (payloads) as those used in the inference_base_model.ipynb. (Reason: an apples-to-apples comparison)

Note:
- I used 'ml.t3.xlarge' instance on AWS Sagemaker in this case since 'ml.t3.medium' was throwing memory-related errors.
(Reference: https://github.com/aws/amazon-sagemaker-examples/issues/279)
- Before running this notebook, we need to push the model in HF Hub. (How to do so?: https://huggingface.co/docs/hub/repositories-getting-started)