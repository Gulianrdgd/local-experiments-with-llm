# **Docker and Docker Compose**

## **Docker and Containers: Basic Concepts**

### **What is Docker?**

Docker is a platform that simplifies the development, deployment, and execution of applications in so-called "containers." Containers are lightweight, portable, self-contained environments in which software can run. This way, you don’t have to download and configure everything yourself—it’s done in advance. https://www.docker.com/

### **Key Docker Concepts**

- **Image**: A template used to create containers. Docker images contain the code, libraries, and configuration for an application.  
- **Container**: An instance of an image. For example, from a single image, you can run 10 different isolated containers side by side.  
- **Docker Compose**: A tool to manage applications that require multiple containers. With a single file, you can manage and connect all the required containers.  
- **Volume**: A place to store container data, even if the container is restarted.  

**Why do we use Docker for our LLM environment?**

1. **Isolation**: Ollama and Open WebUI run in isolated environments without conflicts with other software.  
2. **Easy installation**: No complex configuration.  
3. **Consistency**: The setup works the same across different machines.  
4. **Simple updates**: Updates can be applied simply by downloading new container images.  

### **Installing Docker**

1. Install required packages  
```bash
sudo apt install apt-transport-https ca-certificates curl software-properties-common -y
```

2. Add Docker’s official GPG key  
```bash
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
```

3. Add the Docker repository  
```bash
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
```

4. Update package sources and install Docker  
```bash 
sudo apt update
sudo apt install docker-ce docker-ce-cli containerd.io docker-compose-plugin -y
```

5. Add your user to the Docker group (no need for sudo with Docker commands)  
```bash
sudo usermod -aG docker $USER
```

6. Start and enable Docker service  
```
sudo systemctl start docker
sudo systemctl enable docker
```

Log out and back in (or reboot) to apply the group changes.  

### **Configuring NVIDIA Container Toolkit**

To give Docker containers access to the GPU, the NVIDIA Container Toolkit must be installed:

1. Install the NVIDIA Container Toolkit  
```bash
sudo apt-get install nvidia-container-toolkit -y
```

2. Configure Docker to use NVIDIA  
```bash
sudo nvidia-ctk runtime configure --runtime=docker
```

3. Restart Docker to apply the changes  
```bash
sudo systemctl restart docker
```

Test if the GPU is available in Docker:  

```bash
docker run --rm --gpus all nvidia/cuda:11.8.0-base-ubuntu22.04 nvidia-smi
```

If this command displays GPU information (similar to the earlier `nvidia-smi` output), the configuration is successful.  

## **Setting Up the LLM Environment with Docker Compose**

### **Docker Compose Configuration**

1. Create a new folder for your LLM project:  
```bash
mkdir ~/llm-setup
cd ~/llm-setup
```

Create a `docker-compose.yml` file with [this content](docker-compose.yml).  

**Explanation of this configuration:**

- Two containers are set up:  
  - **Ollama**: The backend that manages and runs the LLM models  
  - **Open WebUI**: The user-friendly web interface for interaction  
- Volumes ensure that data is preserved even if the containers are stopped or removed  
- GPU access is configured through the `deploy` section  
- Open WebUI communicates with Ollama via the internal Docker network connection  

### **Starting the Environment**

Start the containers with the following command:  

```bash
docker-compose up -d
```

This command starts the containers in the background (`-d` stands for "detached mode").  

After startup, the web interface is available at [http://localhost:3000](http://localhost:3000).  

### **Managing Containers**

Useful commands for managing your Docker containers:

- Start containers  
```bash
docker-compose up -d
```

- Check container status  
```bash
docker-compose ps
```

- View logs of the containers  
```bash
docker-compose logs -f ollama # Logs of Ollama
```
```bash
docker-compose logs -f ollama-webui # Logs of Open WebUI
```

- Stop containers  
```bash
docker-compose stop
```

- Stop and remove containers (data is preserved in volumes)  
```bash
docker-compose down
```

- Stop and remove containers including volumes (**WARNING: all data will be deleted**)  
```bash
docker-compose down -v
```
