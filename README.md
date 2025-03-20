# Attacking-LSASS
Playing around with LSASS, LSASS is a critical service that plays a central role in credential management and the authentication processes in all Windows operating systems.

Lets explain alittle bit about what and where u can find lsass
![lsass](https://github.com/alien-keric/Attacking-LSASS/blob/main/lsassexe.png)

As you can see upon initial logon, LSASS will:

- Cache credentials locally in memory
- Create [access tokens 
- Enforce security policies
- Write to Windows security log 

Now lets talk about some method and tools that can be used to dump LSASS memory and extract any credentials from the target running windows

# Dumping LSASS Process Memory
If you have ever tried to attack SAM,SYSTEM, and SECURITY hives it will be much helpfull at this step before dumping LSASS, we will need first create a copy of the contents of LSASS process memory via the generation of a memory dump.after creating a dump file and extract the credentials offline will be very helpful when simulating attacks but also gives us flexibility of speeding up our attacks as it requires less time from the target machine interaction.There are many methods to create a memory dump. We will cover two for now if you get time on your own you can check other methods

## Task Manager method.
With this method its simple we just have to start the Task Manager and find the Local Security Process Authority and create a dump
![taskManager](https://github.com/alien-keric/Attacking-LSASS/blob/main/lsass.png)

Now we need to create a dump of it, and good enough of GUI it will show where the dump is being stored as seen below.
![lsassdump](https://github.com/alien-keric/Attacking-LSASS/blob/main/lsass1.png)
create a copy of the contents of LSASS process memory via the generation of a memory dump
