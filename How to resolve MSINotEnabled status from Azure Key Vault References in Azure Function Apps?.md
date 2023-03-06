# Problem
How to resolve MSINotEnabled status from Azure Key Vault References in Azure Function Apps?


# Environment
Microsoft Azure subscription, Azure Functions App (with broken Key Vault reference) and Azure Key Vault with secret

# Solution
Follow the following steps to resolve this error

![image1](https://user-images.githubusercontent.com/72668520/223101668-40f72654-9582-48c8-8ec2-270567cb0b37.png)

## Step 1
Go to Identity blade of your function app, make sure system assigned identity is On

![image2](https://user-images.githubusercontent.com/72668520/223101694-a50c3e84-618e-4702-90ba-7faa81e9ac5d.png)

## Step 2
Go to you function app configuration blade and add your secret identifier in the following format without curly braces around identifier

![image3](https://user-images.githubusercontent.com/72668520/223101727-c1201609-f4bf-48d1-a352-beddbc655c52.png)

## Run Flow
Now check your application settings in configuration blade, it will appear as resolved

![image4](https://user-images.githubusercontent.com/72668520/223101751-c6ffe031-8540-408b-a067-ff1832e19a68.png)
