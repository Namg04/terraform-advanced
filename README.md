# Terraform-Data sources in terraform resources

**Use of Data source in terraform code**



## Terraform Data Source
1. The data sources allow terraform to use the information defined outside of terraform, defined by another separate terraform configuration or directly created in provider resources using another function.
2. Using data source is accessed via a special kind of resource known as a 'data resource', declared using a data block.


## **Data block**

**Use case 1:  Use of manually created golden ami in the data block**

Below is the example data source block to filter the available AMIs from the AWS region and get the latest AMI as per the name filter.


![image](https://github.com/Namg04/terraform-advanced/assets/61374484/db3e402d-cea5-4256-b974-527c03b4ad8a)

## **Steps to Create Golden AMI**

**1. Create a normal ec2 instance**

![image](https://github.com/Namg04/terraform-advanced/assets/61374484/3baef283-7030-435a-9826-c30205f6e31a)





**2. Login to web-server**


**3. Install Apache over there**

![image](https://github.com/Namg04/terraform-advanced/assets/61374484/5ecc058c-116a-4461-bdcb-ba29b8823ff3)

**4. Check the status of apache2**

![image](https://github.com/Namg04/terraform-advanced/assets/61374484/c2f00eeb-5686-42f5-867b-9984d9057821)

**5. Go to Created Instance Actions> Image and templates > Create Image**

![image](https://github.com/Namg04/terraform-advanced/assets/61374484/fa00bb87-b163-4a27-903e-3def2e6e2e87)

![image](https://github.com/Namg04/terraform-advanced/assets/61374484/c5565709-c162-421b-bc8c-155b0e4c3f59)

![image](https://github.com/Namg04/terraform-advanced/assets/61374484/2e0a8afb-3499-4295-a841-3b9572d896e0)


**6. You can check the created AMI at 'Images'**

![image](https://github.com/Namg04/terraform-advanced/assets/61374484/b8da369d-55d9-4512-bcb9-8c0c1a18c36f)



**7. The custom ami you have created is pre-loaded with default configurations that you are expecting to be available on every instance in my project. This AMI called Golden AMI**



**8. Now, go to the launch instance and create an instance by using custom ami.**

![image](https://github.com/Namg04/terraform-advanced/assets/61374484/eab18d49-fea6-4f4a-b07b-e151b755f817)

**9. Launch the instance and see all created instance**

![image](https://github.com/Namg04/terraform-advanced/assets/61374484/4122b055-0c36-4bc6-993b-7b49de9a84c3)

**10. When I logged in to the tws-webserver and checked the status of apche2, it was running fine.**

![image](https://github.com/Namg04/terraform-advanced/assets/61374484/ef635d01-3567-4f85-b662-15a04452629d)


## **Use case2: Use of vpc resource from Terraform created state file**

Below is the example data source block to get the explored variables from another terraform project remote state file.

![image](https://github.com/Namg04/terraform-advanced/assets/61374484/e2daea8e-c102-469a-ad85-6a4ede15e0d8)


# **Task : Write  code to create an EC2 instance by use of existing Golden AMI and  Terraform state-file.**

## **Terraform Resources created**

## **S3-Backend-project**

**1. dynamodb.tf**

![image](https://github.com/Namg04/terraform-advanced/assets/61374484/e2a623f2-7088-489a-a0b8-5484265e72e9)


**2. s3.tf**

![image](https://github.com/Namg04/terraform-advanced/assets/61374484/5d363048-69ce-4c82-854f-e9f9801b0b31)


## **VPC-project**

**1. backend.tf**

![image](https://github.com/Namg04/terraform-advanced/assets/61374484/9ce58c52-5c0b-4607-8fcd-f97b47c391e4)


**2. igw.tf**

![image](https://github.com/Namg04/terraform-advanced/assets/61374484/32bd5adc-d26b-41d3-b673-cf11e33ea7ba)


**3. output.tf**

![image](https://github.com/Namg04/terraform-advanced/assets/61374484/741db2fa-5592-4d18-a1ba-390c8b4dd352)


**4. priv-subnet.tf**

![image](https://github.com/Namg04/terraform-advanced/assets/61374484/e7363416-c6b8-470f-8204-e62950a14fe9)


**5. pub-subnet.tf**

![image](https://github.com/Namg04/terraform-advanced/assets/61374484/7bcbf630-f249-405f-afdd-07edc412cc48)


**6. rt.tf**

![image](https://github.com/Namg04/terraform-advanced/assets/61374484/4eb3c5f5-35bd-4fb9-aa93-8bc0da96c30f)


**7. terraform.tfvars**

![image](https://github.com/Namg04/terraform-advanced/assets/61374484/0efa33fc-808e-4995-9ac0-f0d82ae2e2e1)


**8. variables.tf**

![image](https://github.com/Namg04/terraform-advanced/assets/61374484/94bef742-b884-45d5-9051-fb23392ef00e)


**9. vpc.tf**

![image](https://github.com/Namg04/terraform-advanced/assets/61374484/879a57d4-791d-476c-8964-e7d2152f91ca)

      
## **EC2-project**


**1. backend.tf**

![image](https://github.com/Namg04/terraform-advanced/assets/61374484/38c7b4d8-0e27-4c65-a9fc-9a11d4640ecf)


**2. ec2.tf**

![image](https://github.com/Namg04/terraform-advanced/assets/61374484/d29a3761-73de-475c-9bc2-4f2b39838995)


**3. terraform.tfvars**

![image](https://github.com/Namg04/terraform-advanced/assets/61374484/52b0476a-1039-48a7-82d5-1b436d2d73f0)


**4. variable.tf**

![image](https://github.com/Namg04/terraform-advanced/assets/61374484/06e48279-aa37-4489-9689-416e2a538323)

   

### **Run Terraform project**

**1. S3-backend-project**

![image](https://github.com/Namg04/terraform-advanced/assets/61374484/299ed733-9522-4018-a42d-b93d9e54dce5)

![image](https://github.com/Namg04/terraform-advanced/assets/61374484/9ee1985f-602e-4dd1-9851-19181410af8e)


**2. vpc-project**

![image](https://github.com/Namg04/terraform-advanced/assets/61374484/4eaf5ec4-68fa-464f-9be7-8b7f874a22f0)

![image](https://github.com/Namg04/terraform-advanced/assets/61374484/969ae128-7788-4218-a7a2-f903e5ae3b51)


**3. EC2-project**

![image](https://github.com/Namg04/terraform-advanced/assets/61374484/a2219673-1e9a-4267-9b18-07f6437e51cb)

![image](https://github.com/Namg04/terraform-advanced/assets/61374484/a1920af7-438d-4ead-85fb-0c079d79ccbb)



   
## **Validate Output**

**1. s3 backend**
![image](https://github.com/Namg04/terraform-advanced/assets/61374484/271d0e78-d3a7-452a-b7bd-7f64f66fc453)



**2. VPC**
![image](https://github.com/Namg04/terraform-advanced/assets/61374484/2c0afb70-23f8-4280-a15a-4b0277f1b524)



**3. EC2**
![image](https://github.com/Namg04/terraform-advanced/assets/61374484/cc7d546c-2fb2-4218-8b66-8438b0ddaaec)












