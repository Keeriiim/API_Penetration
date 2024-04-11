# API_Penetration

- [Lab Setup](#lab-setup)
- 

# Lab Setup
Download [kali](#https://www.kali.org/get-kali/#kali-virtual-machines) for your VM. Then open your VM handler and press open and find the file you downloaded.
After that set cpu to 4, memory to 4 GB and network to bridged adapter.

Default login username&password: kali
```bash
sudo apt update -y
sudo apt upgrade -y
```

## Burp
1. Install Jython standalone
2. Open Burp -> Options -> Python environment -> add jython
3. Add an extention: BappStore -> Autorize
4. Open firefox and get the CA from http://burpsuite

## Foxyproxy
1. Open firefox
2. ctrl + shift + A for addons
3. Foxyproxy standard
![image](https://github.com/Keeriiim/API_Penetration/assets/117115289/7242d016-d9e0-4569-8f59-d483634231ee)  
![image](https://github.com/Keeriiim/API_Penetration/assets/117115289/4c317fa0-f77e-4c78-a63c-5d337bdabdea)
4. Proxy over Burp and type get the CA from http://burpsuite
5. Add the cert to firefox
![image](https://github.com/Keeriiim/API_Penetration/assets/117115289/dac400bd-6f03-4ed1-9baf-7287744f4651)  
![image](https://github.com/Keeriiim/API_Penetration/assets/117115289/4ecdc555-fcec-4351-b99e-da88eecdc1a3)

## Postman
```bash
sudo wget https://dl.pstmn.io/download/latest/linux64 -O postman-linux-x64.tar.gz
sudo tar -xvzf postman-linux-x64.tar.gz -C /opt/
sudo ln -s /opt/Postman/Postman /usr/bin/postman   # Creates a link so that when writing postman the app in /Postman/Postman gets started
```


## Other tools
```bash
sudo pip3 install mitmproxy2swagger
sudo apt install git 
sudo apt install docker-compose -y
sudo apt install docker.io -y
sudo apt install golang-go
sudo useradd -m hacker
sudo usermod -a -G sudo hacker
sudo chsh -s /bin/zsh hacker
sudo passwd hacker
```

Log out -> in as hacker






Setting up Your System
Setting up an API Hacking Lab
API Discovery
Passive Techniques
Active Techniques
Endpoint Analysis
The Process
Setting Up Requests
Interacting With an API
Testing for Excessive Data Exposure
Vulnerability Scanning
Authentication Attacks 
Classic Authentication Attacks
Token Analysis and Forgery
Attacking JWTs
Exploiting Authorization 
Process
Finding Targets
BOLA
BFLA
Testing for Improper Assets Management 
Testing Process
Mass Assignment
Process
Finding Targets
Injection Attacks
Process
Finding Targets
Performing Injection Attacks
Rate Limit Testing
Combining Tools and Techniques
Leveraging Improper Assets Management with other vulns
Using data exposure with other vulns
Course Conclusion and Additional Resources
