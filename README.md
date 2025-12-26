````md
# ShadowMail

ShadowMail is a self-hosted temporary email service designed to generate disposable email addresses on custom domains and receive emails in real time. The project focuses on reliability, privacy, and ease of deployment, making it suitable for testing, quality assurance, development workflows, and internal tooling.

---

## Features

- Instant temporary email address generation  
- Support for multiple custom domains and extensions  
- Real-time inbox updates  
- Optional inbox reuse and persistence  
- Automatic inbox expiration and cleanup  
- Self-hosted and privacy-focused  
- Dockerized deployment for simple setup  
- API-first and modular architecture  

---

## Architecture

- SMTP: Postfix  
- IMAP: Dovecot  
- Backend API: Node.js  
- Realtime updates: WebSockets with Redis  
- Database: PostgreSQL  
- Cache: Redis  
- Reverse proxy: Nginx  

---

## Technology Stack

- Node.js, Express  
- Postfix, Dovecot  
- PostgreSQL  
- Redis  
- Docker, Docker Compose  
- Nginx  

---

## Prerequisites

- Ubuntu 20.04 or later  
- Docker and Docker Compose  
- A domain name with DNS access  
- Public server IP address  

---

## Installation

### Clone the Repository

```bash
git clone https://github.com/Ayushkumarsingh09/ShadowMail.git
cd ShadowMail
````

### Environment Configuration

Create a `.env` file in the project root:

```env
DOMAIN=yourdomain.com
MAIL_HOST=mail.yourdomain.com

POSTGRES_DB=shadowmail
POSTGRES_USER=shadowmail
POSTGRES_PASSWORD=strongpassword

REDIS_HOST=redis
```

---

## DNS Configuration

Configure the following DNS records for your domain:

```text
MX   yourdomain.com        mail.yourdomain.com    10
A    mail.yourdomain.com  SERVER_IP
A    yourdomain.com       SERVER_IP

TXT  yourdomain.com "v=spf1 mx ~all"
TXT  _dmarc.yourdomain.com "v=DMARC1; p=none;"
```

---

## Running the Project

Start all services using Docker Compose:

```bash
docker-compose up -d
```

Verify that the containers are running:

```bash
docker ps
```

---

## Network Ports

The following ports must be open on the server:

| Service | Port     |
| ------- | -------- |
| HTTP    | 80       |
| HTTPS   | 443      |
| SMTP    | 25 / 587 |
| IMAP    | 993      |

---

## Security Considerations

* Enable SSL/TLS using a trusted certificate authority
* Enforce inbox expiration to limit data retention
* Apply IP-based rate limiting at the proxy level
* Monitor mail traffic and system logs regularly

---

## Intended Use

ShadowMail is intended for development, testing, and internal use cases where disposable or short-lived email addresses are required. Users are responsible for ensuring compliance with applicable laws and third-party service policies.

---

## License

This project is licensed under the MIT License.

---

## Author

Ayush Kumar Singh
GitHub: [https://github.com/Ayushkumarsingh09](https://github.com/Ayushkumarsingh09)

```
```
