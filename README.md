# Django Notes App  

A simple and efficient notes application built with **React** for the frontend and **Django** for the backend. This project serves as a great example of combining modern frontend technologies with a robust backend framework.  

## Requirements  

- **Python 3.9**  
- **Node.js**  
- **React**  

## Features  
- Simple and intuitive note-taking functionality.  
- Built with a modern tech stack: Django REST API and React.  
- Dockerized for easy setup and deployment.  

## Installation  

### 1. Clone the Repository  
```bash  
git clone https://github.com/LondheShubham153/django-notes-app.git  
cd django-notes-app  
```  

### 2. Build the Application  
Using Docker, build the application image:  
```bash  
docker build -t notes-app .  
```  

### 3. Run the Application  
Run the Docker container:  
```bash  
docker run -d -p 8000:8000 notes-app:latest  
```  

The app will be available at `http://localhost:8000`.  

## Deploy with Nginx  

To make the application available publicly, set up an Nginx reverse proxy:  

1. **Update your package manager and install Nginx**:  
   ```bash  
   sudo apt-get update  
   sudo apt install nginx  
   ```  

2. **Configure Nginx**:  
   Create a configuration file for the notes app:  
   ```bash  
   sudo nano /etc/nginx/sites-available/notes-app  
   ```  

   Add the following configuration:  
   ```nginx  
   server {  
       listen 80;  
       server_name your-domain.com;  
   
       location / {  
           proxy_pass http://localhost:8000;  
           proxy_set_header Host $host;  
           proxy_set_header X-Real-IP $remote_addr;  
           proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;  
       }  
   }  
   ```  

3. **Enable the Configuration and Restart Nginx**:  
   ```bash  
   sudo ln -s /etc/nginx/sites-available/notes-app /etc/nginx/sites-enabled/  
   sudo nginx -t  
   sudo systemctl restart nginx  
   ```  

Now your app is accessible via `http://your-domain.com`.  

## Contributions  

Contributions are welcome! Feel free to fork the repository and submit pull requests.  

## License  

This project is open-source and available under the [MIT License](LICENSE).  

---  

Let me know if you'd like any changes or additional sections !
