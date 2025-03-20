# Attacking-LSASS
Playing around with LSASS, LSASS is a critical service that plays a central role in credential management and the authentication processes in all Windows operating systems.

Lets explain alittle bit about what and where u can find lsass
![lsass](https://github.com/alien-keric/Attacking-LSASS/blob/main/lsassexe.png)

Upon initial logon, LSASS will:

- Cache credentials locally in memory
- Create [access tokens 
- Enforce security policies
- Write to Windows security log 

