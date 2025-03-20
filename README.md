# Attacking-LSASS
Playing around with LSASS, LSASS is a critical service that plays a central role in credential management and the authentication processes in all Windows operating systems.

Lets explain alittle bit about what and where u can find lsass
![lsass](https://github.com/alien-keric/Attacking-LSASS/blob/main/lsassexe.png)

As you can see upon initial logon, LSASS will:

- Cache credentials locally in memory
- Create access tokens 
- Enforce security policies
- Write to Windows security log 

Now lets talk about some method and tools that can be used to dump LSASS memory and extract any credentials from the target running windows

# Dumping LSASS Process Memory
- If you have ever tried to attack SAM,SYSTEM, and SECURITY hives it will be much helpfull at this step before dumping LSASS, we will need first create a copy of the contents of LSASS process memory via the generation of a memory dump.after creating a dump file and extract the credentials offline will be very helpful when simulating attacks but also gives us flexibility of speeding up our attacks as it requires less time from the target machine interaction.There are many methods to create a memory dump. We will cover two for now if you get time on your own you can check other methods

## Task Manager method.

- With this method its simple we just have to start the Task Manager and find the Local Security Process Authority and create a dump
![taskManager](https://github.com/alien-keric/Attacking-LSASS/blob/main/lsass.png)

- Now we need to create a dump of it, and good enough of GUI it will show where the dump is being stored as seen below.

![lsassdump](https://github.com/alien-keric/Attacking-LSASS/blob/main/lsass1.png)

- create a copy of the contents of LSASS process memory via the generation of a memory dump, now since we have a copy of our dump transfer it to our local machine it to our local machine, copying it is very simple

![lsassdump](https://github.com/alien-keric/Attacking-LSASS/blob/main/lsass2.png)

# Using Pypykatz to Extract Credentials
Once we have the dump file on our attack host, we can use a powerful tool called pypykatz to attempt to extract credentials from the .dmp file. Pypykatz is an implementation of Mimikatz written entirely in Python. The fact that it is written in Python allows us to run it on Linux-based attack hosts. We might try Mimikatz but bad enough Mimikatz only runs on Windows systems, so to use it, we would either need to use a Windows attack host or we would need to run Mimikatz directly on the target, which is not an ideal scenario. This makes Pypykatz an appealing alternative because all we need is a copy of the dump file, and we can run it offline from our Linux-based attack host.

Recall that LSASS stores credentials that have active logon sessions on Windows systems. When we dumped LSASS process memory into the file, we essentially took a "snapshot" of what was in memory at that point in time. If there were any active logon sessions, the credentials used to establish them will be present. Let's run Pypykatz against the dump file and find out.

# Running Pypykatz
## syntax
`❯ pypykatz lsa minidump lsass.DMP`

Now lets run it to our dump and see what we got
![lsassdump](https://github.com/alien-keric/Attacking-LSASS/blob/main/dump.png)

From here we can proceed with cracking the hash if possible using johnjohn,hashcat or online tools but also try other attacks with the help of hash and usernamewe got from the dump

Enjoy life :)
