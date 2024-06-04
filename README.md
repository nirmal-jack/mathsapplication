# mathsapplication
###creating an end-to-end web application using amplify
- create an html document and zip it. login into the aws console and choose AWS Amplify.
- give a name for your application and add the html zip file, give the phase as "dev" and give deploy.. the application will be launched.
- the page will look as below and click on visit deployed url.

![Capture1](https://github.com/nirmal-jack/mathsapplication/assets/170439621/375fa4ab-4b61-4900-82a1-c095b56e10da)



  ![Capture](https://github.com/nirmal-jack/mathsapplication/assets/170439621/52d0a2aa-4bc6-461d-a6b0-d6e4b5222ac5)

- now we have a livepage that users can navigate to. headver to the console and choose lambda. click on "Create a function".
- choose author from scratch and give a name for the function as "PowerofMathfunction" and choose the latest version of python language and click "Create function".

  
![Capture](https://github.com/nirmal-jack/mathsapplication/assets/170439621/21d2d892-c4f2-46e8-b9c0-353cebc68690)


- A lambda function is created successfully as shown below.

  ![Capture](https://github.com/nirmal-jack/mathsapplication/assets/170439621/3ce4351d-522a-419c-ba40-c52e8abe80dd)

  - here in the next step, the code as that we are importing a json utility package and a python math library, so that the maths calculations can be done.
 - save the file and click on deploy.

   ![Capture](https://github.com/nirmal-jack/mathsapplication/assets/170439621/cfeba72a-60f8-4e5c-8370-b16276728b96)

- now to test whether that function code has been deployed successfully, choose the option "Test"--- choose "Configure test event"
- give a name to the test event as "PowerofMathtestevent"
  here the user is giving only 2 values, so choose base and exponent.. eg: give 2 to the power of 3, the answer should be 8 and click on save


  ![teste](https://github.com/nirmal-jack/mathsapplication/assets/170439621/7b8ab665-7619-4bf1-85f8-32bbd9cb548e)

  - now go back to the lambdo code and click on the same test button. it will display the answer.
 
    ![Capture](https://github.com/nirmal-jack/mathsapplication/assets/170439621/68a36f84-0203-4c2c-9821-c11c8a9b58ef)

    - now for the users, we need the application to go live, we need an public endpoint or a URL that can be called and trigger that lambda function to run.
     for that we are gonna use AWS api gateway. This is the perfect way to invoke a Lambda Function.

- now headover to AWS API Gateway and choose create API. and choose "REST API" and give build.

  ![rest](https://github.com/nirmal-jack/mathsapplication/assets/170439621/580aa47c-1737-451d-b7f2-4be90b283a23)

  - choose new API and give a name for the API, as "PowerOfMathAPI" and create API.
 
    ![Capture](https://github.com/nirmal-jack/mathsapplication/assets/170439621/d2bb9bcf-0f7c-4ca4-b058-1f518939bca0)

  -Now we have an empty API and we need methods for users to call. on the left hand side, choose resources and click on create a method.
  - the type of method is POST, choose Lambda function as the integration type and give the lambda name or ARN & create a method.
 
  ![meth](https://github.com/nirmal-jack/mathsapplication/assets/170439621/99c29bb8-0fb1-4bfa-ae8d-4d02b9363173)

  - come back and click on "ENABLE CORS"
    ![Capture](https://github.com/nirmal-jack/mathsapplication/assets/170439621/af2b6e0f-3d2e-4a72-b13c-32d9399fe54b)

- the main usage of cors is the application to be accessible for one domain to another, here we have the app on amplify in one domain and in lambda another, so to work across both, we enable cors. and POST and click SAVE.

![cors](https://github.com/nirmal-jack/mathsapplication/assets/170439621/63408d7c-ff7f-4c22-bdaa-09181cf0f306)

-Now lets deploy the API to test the application. select new stage and give "DEV" & choose DEPLOY.


![Capture](https://github.com/nirmal-jack/mathsapplication/assets/170439621/f572a2c0-116c-49e0-ae8d-005809c8cc50)


- copy the INVOKE URL i.e. (API Gateway )to paste it in our lambda function to trigger it.

  ![Capture1](https://github.com/nirmal-jack/mathsapplication/assets/170439621/834a18f0-efd0-4886-858e-bf5b7abe72a2)

- now to validate this, go to resources and click on POST, then choose TEST.
- give the same details that we use to test the lambda function.
-  {
  "base": 2
  "exponent": 4}

![Capture](https://github.com/nirmal-jack/mathsapplication/assets/170439621/befc0bc9-9d98-4874-ada6-838c52a992dc)


![Capture1](https://github.com/nirmal-jack/mathsapplication/assets/170439621/bfc0b80a-3de3-4706-a644-d78b7529faaa)

- now we have to store the records in a database, we can use AWS DynamoDB and we have to return the result to the user as well.
- Go the AWS Console and type DynamoDB. Create table.
- give the name as "powerofMathdatabase" and for partition key give "ID" * create table.

  ![DB](https://github.com/nirmal-jack/mathsapplication/assets/170439621/d89bae5c-898d-4f40-892a-17d5915034fc)

- save the dynamo DB ARN safely.

  ![Capture](https://github.com/nirmal-jack/mathsapplication/assets/170439621/7f3849b3-65ec-4d69-9183-1dc34526c3e0)

  - now the lambda function has to have permission to write to this dynamo db table. for that we have to create IAM Roles and permissions.
  - go to the lambda function created and click on the configuration tab, click on permissions on the left hand side and click on the role URL.
 
    ![Capture1](https://github.com/nirmal-jack/mathsapplication/assets/170439621/b203a2ba-d42a-4ecc-8223-6e5737624a54)


- go to permissions tab and choose "Create inline Policy".

  ![Capture](https://github.com/nirmal-jack/mathsapplication/assets/170439621/776c9dfd-8dad-490c-89cc-b091ce98e753)

  - choose JSON and give the permissions for the lambda function to do on the dynamoDB table. Here paste the dynamoDB Table's ARN.
 
    ![Capture](https://github.com/nirmal-jack/mathsapplication/assets/170439621/3ce4d75a-02b7-4196-83bc-103d95ff1541)


    - give next and give a name to the policy and create policy.
   
      ![Capture1](https://github.com/nirmal-jack/mathsapplication/assets/170439621/81adfd52-6ded-436f-84fc-5834c6e35f13)

- now go to the lambda function, click on code and copy paste the poweroflambda function final code there and save and deploy.

  ![Capture](https://github.com/nirmal-jack/mathsapplication/assets/170439621/6e14da78-e117-466d-8cf1-5eb58a82ecd7)


- once again do the testing, click on configure test events, give the values or use the same values as before and test.


![Capture1](https://github.com/nirmal-jack/mathsapplication/assets/170439621/5a724747-b3bf-4e39-967e-c3b842a297d0)




 
- 

 
    



  









  








    - 



   


