# WSO2 Kubernetes Demo

This repository contains materials related to the Kubernetes introductory course.

## Prerequisites

This guide assumes you are using **Ubuntu 24.04** and prefer **Docker** as the driver for Minikube.

---

## 1. Install Docker

First, install Docker and set up its repository:

```bash
sudo apt-get update
sudo apt-get install -y ca-certificates curl

sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc
```

Add Docker's official repository:

```bash
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo \"${UBUNTU_CODENAME:-$VERSION_CODENAME}\") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

sudo apt-get update
```

Install Docker packages:

```bash
sudo apt-get install -y docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

Add your user to the `docker` group to avoid needing `sudo` for Docker commands:

```bash
sudo usermod -aG docker $USER
```

> **Note:** You may need to log out and log back in for the group change to take effect.

---

## 2. Install Minikube

Download and install the Minikube binary:

```bash
curl -LO https://github.com/kubernetes/minikube/releases/latest/download/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube
rm minikube-linux-amd64
```

Start Minikube:

```bash
minikube start
```

If you encounter permissions issues with the default driver, use the QEMU driver:

```bash
minikube start --force
```

---

## Resources

- [Minikube Official Documentation](https://minikube.sigs.k8s.io/docs/)
- [Docker Installation Guide](https://docs.docker.com/engine/install/ubuntu/)

---

## License

This project is maintained by WSO2 and is provided under the [MIT License](LICENSE).
