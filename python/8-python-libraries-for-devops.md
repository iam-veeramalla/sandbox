# 8 Python Libraries Every DevOps Engineer Should Know

As a DevOps Engineer, automation and integration are part of your daily life. Python, being one of the most flexible scripting languages, offers a wide range of libraries that can make your job easier, faster, and more reliable.

In this video, we'll explore **8 powerful Python libraries every DevOps Engineer should know** — along with **practical examples** for each.

---

## 1. `boto3` – AWS SDK for Python

**Why use it:** Automate AWS resource provisioning and management.

**Use Case:** Automating EC2 instance creation, S3 bucket operations, or IAM user setup.

**Example:**

```
import boto3

ec2 = boto3.client('ec2')
response = ec2.describe_instances()
for reservation in response['Reservations']:
    for instance in reservation['Instances']:
        print(f"Instance ID: {instance['InstanceId']}")
```

---

## 2. `paramiko` – SSH Automation

**Why use it:** Execute remote commands securely over SSH.

**Use Case:** Automate server management tasks like updates, log checks, and reboots.

**Example:**

```
import paramiko

ssh = paramiko.SSHClient()
ssh.set_missing_host_key_policy(paramiko.AutoAddPolicy())
ssh.connect('192.168.1.10', username='devops', password='secret')

stdin, stdout, stderr = ssh.exec_command('uptime')
print(stdout.read().decode())

ssh.close()
```

---

## 3. `docker` – Docker SDK for Python

**Why use it:** Manage Docker containers and images programmatically.

**Use Case:** Start containers, build images, fetch logs, and monitor container status.

**Example:**

```
import docker

client = docker.from_env()
container = client.containers.run("nginx", detach=True)
print(f"Started container with ID: {container.id}")
```

---

## 4. `kubernetes` – Kubernetes Python Client

**Why use it:** Interact with Kubernetes clusters directly from Python.

**Use Case:** Automate deployment rollouts, pod monitoring, or log retrieval.

**Example:**

```
from kubernetes import client, config

config.load_kube_config()
v1 = client.CoreV1Api()

pods = v1.list_pod_for_all_namespaces(watch=False)
for pod in pods.items:
    print(f"{pod.metadata.namespace} - {pod.metadata.name}")
```

---

## 5. `pyyaml` – YAML Parsing and Generation

**Why use it:** Read and write YAML config files.

**Use Case:** Modify Kubernetes YAML files, Ansible playbooks, or CI/CD pipeline configs.

**Example:**

```
import yaml

with open("config.yaml") as f:
    config = yaml.safe_load(f)

print(config["environment"])
```

---

## 6. `requests` – HTTP Requests

**Why use it:** Communicate with REST APIs easily.

**Use Case:** Trigger deployments, interact with GitHub/GitLab, or call webhook URLs.

**Example:**

```
import requests

response = requests.get("https://httpbin.org/get")
print(response.json())
```

---

## 7. `fabric` – Command Line Automation

**Why use it:** Execute shell commands and deploy scripts across multiple servers.

**Use Case:** Automate app deployment or perform cluster-wide configuration.

**Example:**

```
from fabric import Connection

conn = Connection("devops@192.168.1.10")
conn.run("sudo systemctl restart nginx")
```

---

## 8. `pytest` – Testing Infrastructure

**Why use it:** Write tests for your automation scripts and infrastructure code.

**Use Case:** Validate output of your Ansible roles, shell scripts, or Python automation.

**Example:**

```
def test_add():
    assert 1 + 1 == 2
```

Run the test:

`pytest test_script.py`

---

## Summary

| Library      | Primary Use                  |
|--------------|------------------------------|
| `boto3`      | AWS Automation               |
| `paramiko`   | SSH Remote Execution         |
| `docker`     | Docker Management            |
| `kubernetes` | Kubernetes API Access        |
| `pyyaml`     | YAML Handling                |
| `requests`   | API Communication            |
| `fabric`     | CLI Automation               |
| `pytest`     | Script Testing               |

---
