# Install-Module MSOnline 

Import-Module MSOnline 

$username = "[scot@curryware.onmicrosoft.com](mailto:scot@curryware.onmicrosoft.com)" 

$password = ConvertTo-SecureString -String "AzureAirWatch1" -AsPlainText -Force 

$userCredentials = New-Object System.Management.Automation.PSCredential -ArgumentList $username, $password  

Connect-MsolService -Credential $userCredentials 

# This shows how the domains are authenticating at the current time. 

Get-MsolDomain 

$dom = "curryware.org" 

$brand = "Curryware, Inc." 

$ActiveSO = "[https://aw-curryware-ex1.vidmpreview.com](https://aw-curryware-ex1.vidmpreview.com/)/SAAS/auth/wsfed/active/logon" 

$PLUri = "[https://aw-curryware-ex1.vidmpreview.com](https://aw-curryware-ex1.vidmpreview.com/)/SAAS/API/1.0/POST/sso" 

$Metadata = "[https://aw-curryware-ex1.vidmpreview.com/](https://aw-curryware-ex1.vidmpreview.com/)SAAS/auth/wsfed/services/mex" 

$Poff = "[https://login.microsoftonline.com/logout.srf](https://login.microsoftonline.com/logout.srf)" 

#  This comes from the vIDM WebApp -> Settings -> Signing Certificate field.  Don't use the BEGIN CERT,  

#  END CERT tags and make sure there are no line feeds. 

$cert = " 

MIIFJDCCAwygAwIBAgIGNjqEMUkfMA0GCSqGSIb3DQEBCwUAMEoxIDAeBgNVBAMM 

F1ZNd2FyZSBJZGVudGl0eSBNYW5hZ2VyMRkwFwYDVQQKDBBBVy1DVVJSWVdBUkUt 

RVgxMQswCQYDVQQGEwJVUzAeFw0xOTA2MjgxODUzMTJaFw0yOTA2MjUxODUzMTJa 

MEoxIDAeBgNVBAMMF1ZNd2FyZSBJZGVudGl0eSBNYW5hZ2VyMRkwFwYDVQQKDBBB 

Vy1DVVJSWVdBUkUtRVgxMQswCQYDVQQGEwJVUzCCAiIwDQYJKoZIhvcNAQEBBQAD 

ggIPADCCAgoCggIBALV6/yvkCnaTt0tiZoPrDyBghUMeP7lQSRIGfRl9iS7roWjo 

11VWZv49YyVdFGHFO13VSydVj+cOKxnmborSjneYO2HgX3NZ8WZ+GJ4uDKNbQHsB 

aOr1U040oscL/7UJ88Ur5v52W5TGy3cyrBgEGNI7lZhfqutVyN2fHI9LWjIkofI1 

8FSJh4xQhhhnmVbJM/j6rB1ndfhJxGao+3AtjjIYwvHxBDxo1w19nGxFAvaEug3f 

ln5cb3UsU3Ql/TcSS5vzv1o3CmcWCd/IZ6jqeO3dnvs6S/Id1a7FsuO4c+Rm7vum 

g0VhLae8tUK0Jm+pOhF7J4pRWE2PvltgWvUKivWrxVbbzvfmfVtIJrX59cz4oj7x 

DnnDym8DAW2Qe4MQ/Yr7496WRWFviktOMTu+Ki7ReR1g3en/ymKbzEEiFYAjM9BD 

MITigLsnyugkSQRMjqKf7HfwnvHUykS3lNwyqfafhpXgMJOM5x6acBjj/1wfAO5F 

Tk5D3m5ntd2fpqcIS3bNORMtK0jh1ZwL0AH1PMz+ppse+IS1+PmFkc3Gg+kDnm7d 

IgLxsW+yWAWKvflXuQkZkG9x63b7ie0oWjXzv2GifY5x66s1L13wF2gYLgn6iJof 

GyTiKqmvCFjSWv0USzSIfTPZKiQmLLro/zOiOxu4jQfchJ6OyxDgeCO+TrffAgMB 

AAGjEDAOMAwGA1UdEwQFMAMBAf8wDQYJKoZIhvcNAQELBQADggIBADJJ0FfY7yYA 

Yo9wU3NR8JhGPTzDkrWZc4961M+4ROl/vOpt26SLMYIvT9zT6NxurHTmJBc5ZMke 

ZKvpG4FjbVPG8ZVTLu8dFPManE+iY46r8bjAfRk0mazN3RqHtQgXgplkKzSsMqyi 

3GMTY3bz5PrD+IetlMJq7XeMmzF1PRgyctXx0HQpOD6FvjYiCLRrX7dZPgrh1KKz 

Nz30hNrkVy/XMHwwCIXWAxUQJkIk9slhHhwaz++kqAJsgfAb4E/CA6F4Ce5qP4+O 

SAa/eaXocLV9KlstKfO9oWaonN9RqEzP7DNRLey8I365+eDpLxHu+5zUwybzs5i2 

L9CHe64dFB8qLwWge6GzK36bqqs7nln5FNfdIfdiLk9OeHkQHfNZo/uZ3aR04usv 

RbiQpGfH3kVde81e+E+lJrNGAm5VSyJx4ar5eW9Gk9x7h9oWZfeM/s7tRfWhNLGc 

rdMYE0LnG2AjYXdFhVp9DX16CXrjlv2IoZq2mXjkmUh+SvrZPZRkszAshH0hYz/C 

YQ+eGDvSWBtytb5glwgxuYgWQZEC1gKg2jUleAdWKvOz86omeYzvx65j20xQxPwz 

q/T4g799S4ne+xuFT29f0QpARxEyuVGJCB89MTzO2hSOide1u8Ua2fbldQVv+n1x 

kO5guM/IKuJ/yJE2mwDXt9a56JiO2TYE" 

# When you add the O365 with Provisioning application in vIDM, you have to define an "issuer."  What you put in that field needs to be replicated here. 

$IssuerUri = "o365IssuerURI" 

# This is the money line of the script.  This is where we change from username / password auth to federated auth. 

Set-MsolDomainAuthentication -DomainName $dom -FederationBrandName $brand -Authentication Federated -PassiveLogOnUri $PLUri -ActiveLogOnUri $ActiveSO -SigningCertificate $cert -IssuerUri $IssuerUri -LogOffUri $Poff -MetadataExchangeUri $Metadata –PreferredAuthenticationProtocol WSFED 

# Check the settings that we just set. 

Get-MSolDomainFederationSettings -DomainName $dom 

[http://guid-convert.appspot.com/](http://guid-convert.appspot.com/) 

Make sure you have the right source anchor. 

# Get the on-prem ADUser information 

Get-ADUser -Filter 'Name -like "*Scot*"' 

# Get the O365 AAD user information 

Install-Module -Name AzureAD 

Import-Module AzureAD 

$username = "[scot@curryware.onmicrosoft.com](mailto:scot@curryware.onmicrosoft.com)" 

$password = ConvertTo-SecureString "AirWatch1" -AsPlainText -Force 

$user_creds = New-Object System.Management.Automation.PSCredential ($username, $password) 

Connect-AzureAD -Credential $user_creds 

Get-AzureADUser -Filter "userPrincipalName eq '[scurry@curryware.org](mailto:scurry@curryware.org)'"  

To revert your Federation use: 

# Install-Module MSOnline 

Import-Module MSOnline 

$UserCredentials = Get-Credential 

Connect-MsolService -Credential $UserCredentials 

Set-MsolDomainAuthentication -DomainName $dom -Authentication managed 

Take the ObjectID from the Get-ADUser command above and paste it into [http://guid-convert.appspot.com/](http://guid-convert.appspot.com/) 

Base64 string from conversion should be the same as the Get-MsolUser ImmutableID