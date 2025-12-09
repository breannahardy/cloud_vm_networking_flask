# Flask on Cloud VM (Assignment 2)

## Student Info
- Name:  Breanna Hardy
- Cloud Provider: Google Cloud Platform (GCP)

## Video recording: 
- Loom: <https://www.loom.com/share/3b6802c5e8ff4b929f4f61a2b4d93c65>

## Steps
### 1. VM Creation
Created a new VM using:
- Machine: e2-micro (Free-tier eligible)

- OS: Ubuntu 22.04 LTS

- Networking: Default VPC

- External IPv4 Address: Ephemeral (provides a public IP)

<img width="700" height="430" alt="Screenshot 2025-12-08 234328" src="https://github.com/user-attachments/assets/6ecf3625-89b6-4e94-8303-3d830a4ee3b3" />


### 2. Networking (Port 5003 Open)
- To allow public access to the Flask application, I created a firewall rule:
- Name: allow-5003
- Direction: Ingress
- Source IPv4: 0.0.0.0/0
- Protocol: TCP
- Port: 5003
- Target: All instances in the network


<img width="700" height="700" alt="image" src="https://github.com/user-attachments/assets/a13457a3-77f3-46a4-a9ee-d9eb71ebd4ac" />

### 3. OS Update + Python Install
Click on the SSH to update the operating system
Enter in the code:
 **Update OS**:  
   ```bash
   sudo apt update && sudo apt upgrade -y
   ```
 **Install Git, Python 3 + pip**:  
   ```bash
   sudo apt install git python3 python3-pip python3.13-venv -y
   ```
<img width="700" height="360" alt="Screenshot 2025-12-09 000658" src="https://github.com/user-attachments/assets/42e9ecf5-91f4-42de-9530-249c884156db" />

   <img width="700" height="360" alt="Screenshot 2025-12-09 001459" src="https://github.com/user-attachments/assets/331b62a2-6e75-4a31-8b1f-d9c3485f03ee" />
<img width="700" height="360" alt="Screenshot 2025-12-09 001703" src="https://github.com/user-attachments/assets/7fd34674-a89a-401a-9a49-3feb3df5e579" />

### 4. Flask App Running
- **Copy the Flask template**:  
   ```bash
   git clone https://github.com/hantswilliams/HHA-504-2025-FlaskStarter.git
   cd flask_template
   ```  
 -   Create new virutal environment: 
    ```
    python3 -m venv venv
    ```
   - Then activate virtual environment:
    ```
    source venv/bin/activate
    ```
  -  Install: 
    ```
    pip install requirements.txt
    ``` 
- **Run the app on port 5003**:  
   ```bash
   python3 app.py
<img width="1000" height="370" alt="image" src="https://github.com/user-attachments/assets/def0c750-fadd-4eff-9f3a-f48478ca7487" />
<This is a screenshot of flask app running on SSH>

### 5. Public IP Access
URL: http://35.245.247.184:5003/
- Copy external (public IP) address used when creating VM
- Add 5003 at end to check if flask deploymment was successful
<img width="700" height="650" alt="Screenshot 2025-12-09 002253" src="https://github.com/user-attachments/assets/54212342-c049-488e-9986-c6059ade7001" />
