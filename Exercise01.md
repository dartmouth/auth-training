
# Autentication protocols currently used at Dartmouth
1. SAML
1. CAS
1. OAuth 2 OpenID Connect
1. WebGates


# Example steps of a CAS authentication workflow:

1) user comes to your app as an anonymous user
2) redirect the user to the CAS server

```https://login.dartmouth.edu/cas/login?service=http://localhost:8080```

3) User comes back to app with CAS ticket

```http://localhost:8080/?ticket=ST-67535-qJZqf1rmdiZHxE6xDEOl-arrow```

4) App validates the CAS ticket (uses back-end channel)

```https://login.dartmouth.edu/cas/serviceValidate?service=http://localhost:8080&ticket=ST-67535-qJZqf1rmdiZHxE6xDEOl-arrow```

5) App parses CAS response and logs the user in

```
<cas:serviceResponse xmlns:cas='http://www.yale.edu/tp/cas'>
    <cas:authenticationSuccess>
        <cas:user>Elijah W. Gagne@DARTMOUTH.EDU</cas:user>
                    <cas:attribute name="uid" value="1997093502"/>
                    <cas:uid>1997093502</cas:uid>
                    <cas:attribute name="name" value="Elijah W. Gagne"/>
                    <cas:name>Elijah W. Gagne</cas:name>
                    <cas:attribute name="alumniid" value="0000309961"/>
                    <cas:alumniid>0000309961</cas:alumniid>
                    <cas:attribute name="did" value="HD92495J"/>
                    <cas:did>HD92495J</cas:did>
                    <cas:attribute name="netid" value="d92495j"/>
                    <cas:netid>d92495j</cas:netid>
                    <cas:attribute name="authType" value="OAM"/>
                    <cas:authType>OAM</cas:authType>
                    <cas:attribute name="affil" value="DART"/>
                    <cas:affil>DART</cas:affil>
            <cas:attributes>
                <cas:nolijName>Elijah W. Gagne</cas:nolijName>
            </cas:attributes>
    </cas:authenticationSuccess>
</cas:serviceResponse>
```

# Homework

Write a PowerShell script that does the following:
1) Asks the user to press ENTER to login
2) After ENTER is pressed, a web browser is opened and sent to CAS to log in, after the user logs in, they will get a ticket in their URL.
3) The app tells the user to log in via the web browser and once finished, paste in the ticket
4) After the ticket is pasted in, your script will make a back channel request to the CAS server to validate the ticket
5) The script will parse the reponse and write "Hello NAME, your netid is d000001"


