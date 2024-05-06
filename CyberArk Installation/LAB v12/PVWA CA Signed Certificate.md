Open "Run" type cmd ~certlm.msc~
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/e6d0eb6e-f554-455e-bb47-f662bcdc46e1)

We have two certificate Self singed certificate and server certificate (created by IIS Manager).
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/e0a7d4ca-9ff9-4e85-b9f9-dab9c5718265)

Create a custom Request
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/34fe25f2-3bb2-40e9-9c19-1f4506cd5794)

Certificate Enrollment.
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/359f45cd-5b03-478c-b4d0-312f800c3df9)

Select certificate enrollment policy (i.e., AD enrollment policy)
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/481d8e69-b23c-4703-b6d4-2520ee47dbb6)

Custom request
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/b2c4f113-4163-445a-acaa-8514d20bf69a)

Certificate Information, click on 'Details' and go to 'properties'.
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/24571808-919b-41f9-bf1f-7cda4afdda19)

Certificate Properties
Under 'Subject' tab, Subject name: Add> Common name(CN), Country(C), Organization(O), Sate(S), Street Address(Street).
Alternative name 'Type: DNS' enter the DNS ~PVWACPM03.corp.devlab~.
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/e2ff3c35-5e47-4618-9312-d2daefce3142)

Under 'Extensions' tab got to "Extended Key Usage (Application Policies)" select 'Server Authentication' and add.
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/7526f266-fd4a-4cdf-bd96-5369a1348463)

Under 'Private Key' Tab, go to "Key Options" keep key size: 2048 and check mark 'Make private key exportable'. Select 'Apply' & 'Ok'. 
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/0052bc12-a6b0-44a7-8b5c-81a0ea61dd0d)
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/f80d77ec-ae77-4371-bc02-0a4b75938ff4)

Give a name to CSR and select 'Finish'.
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/63a0e142-5093-4984-b93a-5b3ac70c70d2)


Open the CSR file in notepad and copy it.
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/0d306562-33a4-4e58-9377-e9286c503899)

~~
-----BEGIN NEW CERTIFICATE REQUEST-----
MIIEADCCAugCAQAwXzESMBAGA1UECQwJSHlkZXJhYmFkMQswCQYDVQQIDAJUUzEP
MA0GA1UECgwGZGV2bGFiMQswCQYDVQQGEwJJTjEeMBwGA1UEAwwVUFZXQUNQTTAz
LmNvcnAuZGV2bGFiMIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEA4yRS
ueENLd5GU2oqlOdJyJZp1+669A9ebdYF+xUgBN6K4lZ2nwezqCoOCVAjlZ+cTJ4S
IVu0/gkooTiejXvfVS2/gEqiLb6vip3MFgWF00MCprv7yxGTQNZzipvobEKoMoI7
5BQRo7ev+69UF6PpieWzqKgjo6KgMbglbhXBElyO2kfxL6O/EfpmqQwMTkJ+lky6
URj3yilXPPD7H0vIloJ5N81sO+37Ct7nuuPveuoZOwXFEcAB2RxsB4oh4TkB/AJi
E8+trvcgFdKY5ySy5vMyRssbXZTgg9MsgO03rHYYNi1MqFdR/JVMcTFQBCw3dlGb
2VTNb8p44Vu5Kc6qWwIDAQABoIIBWjAaBgorBgEEAYI3DQIDMQwWCjYuMy45NjAw
LjIwTwYJKwYBBAGCNxUUMUIwQAIBBQwZUFZXQUNQTTAzLmNvcnAuZGV2bGFiLmNv
bQwXUFZXQUNQTTAzXEFkbWluaXN0cmF0b3IMB01NQy5FWEUwZgYKKwYBBAGCNw0C
AjFYMFYCAQAeTgBNAGkAYwByAG8AcwBvAGYAdAAgAFMAbwBmAHQAdwBhAHIAZQAg
AEsAZQB5ACAAUwB0AG8AcgBhAGcAZQAgAFAAcgBvAHYAaQBkAGUAcgMBADCBggYJ
KoZIhvcNAQkOMXUwczAgBgNVHREEGTAXghVQVldBQ1BNMDMuY29ycC5kZXZsYWIw
EwYDVR0lBAwwCgYIKwYBBQUHAwEwGwYJKwYBBAGCNxUKBA4wDDAKBggrBgEFBQcD
ATAdBgNVHQ4EFgQU4qHxHhnAYmcVXApIstiMx0rqPtswDQYJKoZIhvcNAQELBQAD
ggEBAM4sHOUSmeqqoUjRWJoOQTgD2FJKlPMS+PUzgq8P92iAqrm18gcpEnP/6Hk4
gd4of/Zi6uv00PcK9RSA3bCvjMwQ/fxGeSiNnkjAFb4m+jxe8mt+La36gk0gS5zz
U2rJMHAnr81TxLvXoFPNsMBZbVf9hFt3TyFa7sU37C3I36FE6TK3Qn5KUyySMPwu
t79cuMjmQuUUOnFZCmBx72kQ3MSlFEWhdENvap2AzLU5uYi3w85sFmegj4ATGW5M
kqEvWfh6pTA6Ec4mC4E4DLY4aH27QXA16OhST//FXc9TMpjz/6FKVLYsoEP819mP
ZbVIwPOmvV0Egf5YZkREtq8pr6k=
-----END NEW CERTIFICATE REQUEST-----
~~

open AD cert in pvwa server ~addc01/certsrv~ give the DC server admin credentials (Username: administrator and pwd: Tej@143!!)
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/b1edb508-8657-443b-90b0-e9ec2d73e2f6)

will redirect to AD certificate services, select the 'Request a certificate'.
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/cae923f0-a45d-4e9a-a7fd-d9d06f01dcde)

Select 'Advanced Certificate request'.
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/e3456627-229e-496c-940b-cf3daa8ca084)

Paste the CSR, change certificate template as 'Web Server' and submit. 
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/a60ddd33-2b39-4b1c-863b-9bda77b1d364)

Now dowload the certificate
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/a73763ef-50ae-41ff-b0e5-0a4b3d339cf8)

Open the downloaded certificate and install it
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/abb9807e-ac96-420f-a806-c07ebfa8431c)
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/831de2cc-b0a3-42d1-aca4-24033d255478)



