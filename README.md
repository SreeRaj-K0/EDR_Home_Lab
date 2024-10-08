# LimaCharlie EDR HOME LAB

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

![Sliver Setup](images/implants-sliver.png)

### Set Up Python Server and Deploying C2 Implant

![Sliver Python Server](images/py.png)
![Sliver 2](images/sliver2.png)

### We got the Sliver session

![Sliver Session](images/sliver-session.png)
![Sliver Session Info](images/sliver-session-info.png)

### On LimaCharlie

![Sliver Process](images/sliver-process.png)
![Network](images/network.png)
![Timeline](images/timeline.png)

## Generating Telemetry by Dumping `lsass.exe`

![LSASS Dump](images/lsaasdump.png)

### Create Detection Rule to Detect Lsass Dumping

![Detection Rule](images/dr-rule.png)
![Rule LSAAS](images/rule-lsaaa.png)

Now we have a simple detection rule to identify credential dumping. Let’s test it again by generating telemetry through dumping `lsass.exe` once more.

![LSAAAS](images/LSAAAS.png)
![Detect Sliver Rule](images/detect-sliver-rule.png)

We’ve successfully detected the `lsass.exe` dumping with our detection rule. Additionally, LimaCharlie’s built-in detection rules also identified our C2 server, marking it as the Sliver Hacktool.

## Conclusion

In this project, a LimaCharlie EDR environment was successfully set up, and a Sliver implant was deployed on a Windows machine. The intricacies of collecting telemetry data, particularly through memory dumping techniques, were learned, along with the creation of  detection rules for identifying credential dumping activities. This hands-on experience enhanced the understanding of endpoint detection and response, as well as the practical application of offensive security tools in a controlled lab setting.
