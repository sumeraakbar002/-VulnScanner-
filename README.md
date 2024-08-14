# -VulnScanner-
vulnscanner/
│
├── vulnscanner/
│   ├── __init__.py
│   ├── scanner.py
│   ├── port_scanner.py
│   ├── service_detector.py
│   ├── vulnerability_checker.py
│   └── report_generator.py
│
├── tests/
│   ├── __init__.py
│   ├── test_scanner.py
│   ├── test_port_scanner.py
│   ├── test_service_detector.py
│   ├── test_vulnerability_checker.py
│   └── test_report_generator.py
│
├── examples/
│   └── example_usage.py
│
├── .gitignore
├── requirements.txt
├── README.md
└── LICENSE
import socket

def scan_ports(host, port_range):
    open_ports = []
    for port in port_range:
        sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
        sock.settimeout(1)
        result = sock.connect_ex((host, port))
        if result == 0:
            open_ports.append(port)
        sock.close()
    return open_ports
import socket

def detect_service(host, port):
    try:
        sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
        sock.settimeout(1)
        sock.connect((host, port))
        banner = sock.recv(1024)
        sock.close()
        return banner.decode().strip()
    except Exception as e:
        return str(e)
import json

def generate_report(results, file_path):
    with open(file_path, 'w') as file:
        json.dump(results, file, indent=4)
# VulnScanner

VulnScanner is a Python-based vulnerability scanning tool designed to identify common vulnerabilities in web applications. It helps developers and security professionals detect security issues early in the development process.

## Features

- Port Scanning
- Service Detection
- Vulnerability Detection
- Report Generation

## Installation

1. Clone the repository:https://github.com/SUMERAAKBAR002@GMAIL.COM/vulnscanner.git
2. 
2. Navigate to the project directory:https://github.com/SUMERAAKBAR002@GMAIL.COM/vulnscanner.git
3. 
3. Set up a virtual environment and install dependencies:

## Usage

Example of how to use VulnScanner:
```python
from vulnscanner.port_scanner import scan_ports
from vulnscanner.service_detector import detect_service
from vulnscanner.report_generator import generate_report

host = 'example.com'
port_range = range(1, 1025)
open_ports = scan_ports(host, port_range)

results = {}
for port in open_ports:
 service = detect_service(host, port)
 results[port] = service

generate_report(results, 'report.json')


