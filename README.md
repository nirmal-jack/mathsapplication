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






    - 



   


