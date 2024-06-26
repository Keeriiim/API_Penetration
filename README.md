# API_Penetration

- [Lab Setup](#lab-setup)
- [Reconnaissance](#reconnaissance) 

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

```bash
sudo git clone https://github.com/ticarpi/jwt_tool
sudo python3 -m pip install termcolor cprint pycryptodomex requests
cd jwt_tool
sudo chmod +x jwt_tool.py
sudo ln -s /opt/jwt_tool/jwt_tool.py /usr/bin/jwt_tool
  
cd /opt
sudo git clone https://github.com/assetnote/kiterunner.git
cd kiterunner
sudo make build
cd dist
sudo ln -s /opt/kiterunner/dist/kr /usr/bin/kr

cd /opt
sudo git clone https://github.com/s0md3v/Arjun.git
cd Arjun
sudo python3 setup.py install
sudo ln -s /opt/Arjun/arjun /usr/bin/arjun

```

## Zap
```bash
sudo apt install zaproxy
```
When you open the app, update OpenAPI

## crApi & vApi
- [crApi](https://github.com/OWASP/crAPI/blob/develop/docs/setup.md)
```bash
mkdir lab
cd lab
mkdir crapi
curl -o docker-compose.yml https://raw.githubusercontent.com/OWASP/crAPI/main/deploy/docker/docker-compose.yml
docker-compose pull
sudo docker-compose -f docker-compose.yml --compatibility up -d
```
![image](https://github.com/Keeriiim/API_Penetration/assets/117115289/fe3b1050-a295-4447-b8a4-66218779c0bd)  
![image](https://github.com/Keeriiim/API_Penetration/assets/117115289/d7201388-38dd-4092-aaf5-5c5708e9bdd4)


```bash
cd lab
git clone https://github.com/roottusk/vapi.git
cd vapi
sudo docker-compose up -d
```
![image](https://github.com/Keeriiim/API_Penetration/assets/117115289/b9157608-6b7e-4574-b336-70fb310fb145)

- Go to Postman, create new workspace, import collection & env .json from /vapi/postman




# Reconnaissance
## Discovering APIs: Passive and Active Reconnaissance
Start by using the web application as an end-user.
Look for advertised APIs on the landing page.
Identify API naming schemes and patterns.
Utilize HTTP headers and response messages.
Use third-party sources for additional API listings.

- Public API is designed for use by anyone, typically with open access and often accompanied by comprehensive documentation.
  Endpoint: example.com/api/v1/search  
  Description: This endpoint allows users to search for various topics, such as "Teletubbies".  
  Access: Open to the public, no authentication required.  
  Documentation: Found at example.com/docs, providing detailed instructions on how to use the API.  

- Partner API is meant for use by specific partners or entities, often requiring authentication and limited documentation for the public.
  Endpoint: partners.example.com/api/v1/search  
  Description: The API returns enhanced search results, possibly with additional metadata or customization options for PartnerCo.  
  Access: Restricted to authorized partners, requires authentication.  
  Documentation: Limited documentation available at partners.example.com/docs, accessible only to authorized partners  

- Private API is internal to the organization, meant for use within the company, and often lacks public documentation.
  Endpoint: internal.example.com/api/v1/search
  Description: This endpoint provides detailed analytics and raw data about "Teletubbies", used for internal analysis.
  Access: Restricted to employees within the example.com organization, requires internal authentication.
  Documentation: Limited or no public documentation available, internal teams rely on knowledge sharing or direct communication.

Web API Indicators
Marketing on web applications.
Obvious URL naming schemes: /api, /v1, /docs, etc.
Subdomains: api.target-name.com, developer.target-name.com, etc.
HTTP headers: Content-Type: application/json, etc.
Response messages like: {"message": "Missing Authorization token"}.

Third-Party Sources
Explore APIs using:
Github: github.com
Postman Explore: postman.com/explore/apis
ProgrammableWeb API Directory: programmableweb.com/apis/directory
APIs Guru: apis.guru
Public APIs Github Project: github.com/public-apis/public-apis
RapidAPI Hub: rapidapi.com/search/


## Passive Techniques
Google dorking:   
intitle:"api" site:"coinbase.com"   
intitle:json site:ebay.com   
inurl"/api/v1" site:"coinbase.com"   
![image](https://github.com/Keeriiim/API_Penetration/assets/117115289/bc1257ea-1e52-4283-be55-8dfc5e1e6742)


## Active Techniques

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
