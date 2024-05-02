## Create Certificate for windows
```
$rootCert = New-SelfSignedCertificate -DnsName "Vikash" -Type CodeSigningCert -CertStoreLocation "C:\projects\nsis-test\certs\"
>> [System.Security.SecureString]$rootcertPassword = ConvertTo-SecureString -String "watchme" -Force -AsPlainText
>> [String]$rootCertPath = Join-Path -Path 'cert:\CurrentUser\My\' -ChildPath "$($rootcert.Thumbprint)"
>> [String]$rootCertPath = Join-Path -Path 'cert:\LocalMachine\My\' -ChildPath "$($rootcert.Thumbprint)"
>> Export-PfxCertificate -Cert $rootCertPath -FilePath 'cert.pfx' -Password $rootcertPassword
>> Export-Certificate -Cert $rootCertPath -FilePath 'certificate.crt'
```
