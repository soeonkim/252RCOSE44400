# Use Python 3.13 base image for AWS Lambda
FROM public.ecr.aws/lambda/python:3.13

# Copy requirements.txt and install dependencies
COPY requirements.txt ${LAMBDA_TASK_ROOT}
RUN pip install -r ${LAMBDA_TASK_ROOT}/requirements.txt

# Copy the Lambda function code
COPY lambda_function.py ${LAMBDA_TASK_ROOT}

# Set the CMD to the Lambda handler
CMD ["lambda_function.lambda_handler"]
