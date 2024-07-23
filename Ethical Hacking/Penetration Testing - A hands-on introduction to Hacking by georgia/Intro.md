# Pentesting

## Stages of Pentesting [^1]

### Pre-Engagement: 

* Pentester and client discuss about the extent and parameters for the pentest (scope), their goals and so on
* Miscommunication with clients could lead to sticky situations
* Ask the client questions like:
    * If this is their first pentest, what prompted them to find a pentester? 
    * What exposures are they most worried about? 
    * Do they have any fragile devices you need to be careful with when testing?
    * What matters most to them? (Time or safety)
* Scope:
    * What IP addresses or hosts are in scope, and what is not in scope? 
    * What sorts of actions will the client allow you to perform? 
    * Are you allowed to use exploits and potentially bring down a service, or should you limit the assessment to merely detecting possible vulnerabilities? 
    * Does the client understand that even a simple port scan could bring down a server or router? 
    * Are you allowed to perform a social-engineering attack?
2. Information gathering: 
    * The pentester finds the publicly available info about the client and indentifies potential ways to gain acess to the client's systems
3. Threat-Modelling: 
    * The pentester assesses the importance of each finding and how each of it could help the attacker to find their way inti the system
    * This assessment helps the pentester to create an action plan
4. Vulnerability Analysis: 
    * The pentester tries to find vulnerabilities in the client's systems
5. Exploitation: 
    * The pentester finally breaks into the system in this phase
6. Post-Exploitation:
    * Now the pentester accesses sensitive data, additional info and access to other systems
7. Reporting:
    * The pentester summarizes their findinga forr both executives and technicians

[^1]: Note: For more information on pentesting, a good place to start is the Penetration Testing
Execution Standard (PTES) at [http://www.pentest-standard.org/](http://www.pentest-standard.org/).