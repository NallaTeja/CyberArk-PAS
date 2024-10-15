- login to the application server & also open the SSL portal where old certificate is existed. 
- Open IIS manager navigate to 'control panel>system and security>Administrativr tools>internet information services (IIS) Manager'
- select the application server navigate to 'server certificate' 
- click on 'create certificate request' at right side top corner.
- Enter details & click Next
 common name: applicationDNS.domain.com
 organization: company name\, Inc.
 organization Unit: NA
 City/locality: Hyderabad
 state/provice: Telangana
 country region: IN

- set the cryptographic service provider & bit length.
 cryptographic service provider: Microsoft RSA SChannel Cryptographic provider
 Bit length: 2048
- set the file path to be saved (desktop) .csr file.
- Open SSL portal where you can create/modify/edit certificates. reissue the certificate. 
- 