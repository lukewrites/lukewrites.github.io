<!--
.. title: AWS Lambda TypeError - "x() takes no arguments (2 given)"
.. slug: aws-lambda-typeerror-x-takes-no-arguments-2-given
.. date: 2017-05-22 06:31:05 UTC-07:00
.. tags:
.. category: Django
.. link:
.. description: What do you do when you upload a working script to AWS Lambda and get a TypeError: x() takes no arguments (2 given)?
.. type: text
-->

I guess I didn't read the documentation thoroughly enough. (Actually, I hadn't read it at all.)

I had some wonderful code that worked on my local machine. I was excited to see it up and running on AWS Lambda (especially since Lambda is free...) but when I tried to run the script, it constantly threw the following error on AWS Lambda:

```json
{
  "stackTrace": [
    [
      "/var/runtime/awslambda/bootstrap.py",
      246,
      "handle_event_request",
      "result = request_handler(json_input, context)"
    ]
  ],
  "errorType": "TypeError",
  "errorMessage": "tweeter() takes no arguments (2 given)"
}
```

What could it mean?

When you deploy a Python script to Lambda, you need to change your script's main function (the [`_handler_`](https://docs.aws.amazon.com/lambda/latest/dg/python-programming-model-handler-types.html), in AWS-speak) to accept the parameters `(event, context)`. These parameters pass in event data and runtime information to the function.

Problem solved.
