

# Limacharlie EDR HOME LAB

## Objectives

1. Install LimaCharlie sensor on a Windows machine to collect telemetry.
2. Create a Sliver payload on Kali Linux to launch an attack on the Windows system.
3. Execute the attack and establish a Sliver session with the target.
4. Dump `lsass.exe` memory from the compromised Windows machine for credential dumping.
5. Create a detection rule in LimaCharlie to identify and alert on `lsass.exe` dumping activity.

## Network Configuration

- **Network:** 10.10.10.0/24
- **Windows Enterprise Machine:** 10.10.10.155
- **Kali Linux (Sliver Server):** 10.10.10.140

## Installation and Configuration of LimaCharlie Sensor on Windows Enterprise

![LimaCharlie Installation](images/lima.png)
![LimaCharlie Configuration Step 1](images/lima2.png)
![LimaCharlie Configuration Step 2](images/lima3.png)
![LimaCharlie Configuration Step 3](images/lima4.png)




# Setting Up Sliver Implant on Kali Linux and Deploying to Windows



![Sliver set-up](images/implants-sliver.png)



### Set Up Python Server and Deploying C2 Implant



![sliver](images/py.png)
![sliver](images/sliver.png)
![sliver](images/sliver2.png)


### # we got the sliver session

![[sliver-session.png]]


![[sliver-session-info.png]]



### on Limacharlie 

![[sliver-process.png]]

![[network.png]]![[timeline.png]]


## Generating Telemetry by Dumping `lsass.exe`


![[lsaasdump.png]]



### create Detection Rule to Detect Lsass Dumping

![[dr rrrrule.png]]


![[rule-lsaaa.png]]![[dr rule.png]]

Now we have a simple detection rule to identify credential dumping. Let’s test it again by generating telemetry through dumping `lsass.exe` once more.

![[LSAAAS.png]]



![[detectsliver rule.png]]

We’ve successfully detected the `lsass.exe` dumping with our detection rule. Additionally, LimaCharlie’s built-in detection rules also identified our C2 server, marking it as the Sliver Hacktool.




## Conclusion

In this project, a LimaCharlie EDR environment was successfully set up, and a Sliver implant was deployed on a Windows machine. The intricacies of collecting telemetry data, particularly through memory dumping techniques, were learned, along with the development of effective detection rules for identifying credential dumping activities. This hands-on experience enhanced the understanding of endpoint detection and response, as well as the practical application of offensive security tools in a controlled lab setting. Overall, this project has deepened knowledge of both attack and defense mechanisms in cybersecurity.
