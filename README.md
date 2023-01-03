# myapp
Spring Boot application code:

# Pre-requisites:
``
Java
MVN
Docker
``

# Deploy Application locally:
```
1: Make changes to the code.
2: Run the below command to create jar file for the application:
  a: mvn test
  b: mvn package
3: jar file will be created in target/myapp-1.0.0.jar in the same folder.
4: Run the below command to start the application locally
  -> java -jar target/myapp-1.0.0.jar

# Create Docker image & deploy locally:
1: Make changes to the code.
2: Run the below command to create jar file for the application:
  a: mvn test
  b: mvn package
3: jar file will be created in target/myapp-1.0.0.jar in the same folder.
4: Create docker image locally:
  a: docker build -t application_name:latest . (Make sure you run the command from the same directory where you have the docker file)
5: Run docker image in a local container:
  a: docker run -itd -p 8080:8080 application_name:latest
  
# Create Docker image & deploy ECS cluster automatically
1: Make changes to the code.
2: Push the changes to the Git repository
3: Code zip will be copied to S3 bucket/ upload zip to S3 bucket
4: Run the pipeline
5: Codebuild will package the application & export jar file
6: Docker image will be created and uploaded to ECR
7: New ECS task will be created with new changes & the old one will be deleted.
```
