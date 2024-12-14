# AWSscribes-not-working

![image](https://github.com/user-attachments/assets/b6e23647-6825-4d87-a664-4b2102b7ac57)
![image](https://github.com/user-attachments/assets/bd7807ae-7076-47d0-b834-ec116d821a02)

![image](https://github.com/user-attachments/assets/6231bac0-10a6-4037-9cea-915687a67ce1)
![xray](https://github.com/user-attachments/assets/9a3fe1f1-0a10-4065-9852-f723f8abea45)


## Scribe no. 6
https://scribehow.com/shared/Playing_with_EC2_Instance_Metadata_Service_and_Dynamic_Data__6NCryFcnSFWRrA8ooVRjuQ


- The command provided in Scribe step 3 is not working. The given command is:

```
curl TOKEN=$(curl -X PUT "http://169.254.169.254/latest/api/token" -H "X-aws-ec2-metadata-token-ttl-seconds: 21600")
```
![image](https://github.com/user-attachments/assets/b6e23647-6825-4d87-a664-4b2102b7ac57)

- The updated command, which I obtained from ChatGPT and works correctly, is:

```
TOKEN=$(curl -X PUT "http://169.254.169.254/latest/api/token" -H "X-aws-ec2-metadata-token-ttl-seconds: 21600")
```
![image](https://github.com/user-attachments/assets/bd7807ae-7076-47d0-b834-ec116d821a02)
**Explanation:**  
This command captures the session token returned by the metadata service into the `TOKEN` variable.

- After running the above command, execute the following to verify that the token is working:

```
curl -H "X-aws-ec2-metadata-token: $TOKEN" http://169.254.169.254/latest/meta-data
```

![image](https://github.com/user-attachments/assets/6231bac0-10a6-4037-9cea-915687a67ce1)

**Explanation:** This command uses the token to fetch metadata from the EC2 instance metadata service.

- The command provided in step 4 works but includes an unnecessary duplicate `curl -H`. The original and updated commands are as follows:

**Given command:**
```
curl -H curl -H "X-aws-ec2-metadata-token: $TOKEN" http://169.254.169.254/latest/dynamic/instance-identity/document
```

**Updated command**
```
curl -H "X-aws-ec2-metadata-token: $TOKEN" http://169.254.169.254/latest/dynamic/instance-identity/document
```

**Explanation:**  
The updated command removes the redundant `curl -H` and still works perfectly to fetch the instance identity document.

## Scribe no. 45 

https://scribehow.com/shared/Exploring_Lambda_Functions__Monitoring_and_more__kwARer8ERkqkvd-kw14AOg

The screen in **Step 7** has changed. To choose **AWS X-Ray**, select the second option, **Lambda service traces**, as shown in the updated interface below.

![xray](https://github.com/user-attachments/assets/9a3fe1f1-0a10-4065-9852-f723f8abea45)

After completing Step 7, the lab works as expected through to the final step.
