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

I guess I didn't read the documentation thoroughly enough.

I had some wonderful code that worked on my local machine but constantly threw the following error on AWS Lambda:

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
