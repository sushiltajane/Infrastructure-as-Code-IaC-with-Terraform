# Infrastructure-as-Code-IaC-with-Terraform
# **Terraform Docker Provisioning**

This project demonstrates how to provision a **Docker container** using **Terraform**. It pulls an Nginx image and creates a container with port mapping.

## **📌 Prerequisites**
Ensure you have the following installed:

- **Docker** → [Download & Install](https://www.docker.com/products/docker-desktop)
- **Terraform** → [Download & Install](https://developer.hashicorp.com/terraform/downloads)

## **📂 Project Structure**
```
terraform-docker/
│── main.tf          # Terraform configuration file
│── README.md        # Project documentation
```

## **🚀 Setup & Deployment**
### **1️⃣ Clone the Repository**
```sh
git clone https://github.com/your-username/terraform-docker.git
cd terraform-docker
```

### **2️⃣ Initialize Terraform**
```sh
terraform init
```
This downloads the required Terraform providers.

### **3️⃣ Preview Changes**
```sh
terraform plan
```
Shows what Terraform will create.

### **4️⃣ Deploy the Infrastructure**
```sh
terraform apply -auto-approve
```
This provisions:
✅ **Nginx Docker image**  
✅ **Docker container named `nginx-container`**  
✅ **Port mapping `8080:80`**  

### **5️⃣ Verify Deployment**
Check if the container is running:
```sh
docker ps
```
Access **Nginx** in your browser:
```
http://localhost:8080
```

### **6️⃣ Destroy Infrastructure (Cleanup)**
If you no longer need the container, run:
```sh
terraform destroy -auto-approve
```

## **📜 Terraform Code (`main.tf`)**
```hcl
terraform {
  required_providers {
    docker = {
      source  = "kreuzwerker/docker"
      version = "~> 2.0"
    }
  }
}

provider "docker" {}

resource "docker_image" "nginx" {
  name         = "nginx:latest"
  keep_locally = false
}

resource "docker_container" "nginx" {
  image = docker_image.nginx.image_id
  name  = "nginx-container"
  ports {
    internal = 80
    external = 8080
  }
}
```

## **📌 Author**
**Your Name**  
📧 sushiltajane569@gmail.com  
🔗 [GitHub Profile](https://github.com/your-username)  

## **📄 License**
This project is licensed under the **MIT License**.

