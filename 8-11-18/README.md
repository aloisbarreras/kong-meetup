# Cincinnati Kong Meetup 8-11-18

### Prerequisites
- Make sure AWS credentials are set up
- Install serverless
- Install docker

### Steps
1. Deploy the Lambda function with serverless
`sls deploy`

2. Start Kong
`make compose-up`

3. Create a Service
`make create-service`

4. Create a Route
`make create-route`

5. Grab the route id and add the lambda plugin
`make add-lambda route_id=ROUTE_ID`

6. Test it out
`curl localhost:8000/hello`

7. Add some Basic Auth protection to the route
`make add-basic-auth`

Test it out and verify that you are unauthorized.
`curl localhost:8000/hello`

8. Create a consumer
`make create-consumer`

9. Create a credential for the consumer
`make create-credential`

Test it out make sure it works
`curl localhost:8000/hello -H "Authorization: Basic YWxvaXM6cGFzc3dvcmQ="`
