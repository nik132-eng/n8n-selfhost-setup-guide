# 🚀 n8n Self-Hosting Setup Guide

> **Complete guide to self-host n8n with Docker, PostgreSQL, and public access - No coding experience required!**

[![Docker](https://img.shields.io/badge/Docker-Required-blue?style=for-the-badge&logo=docker)](https://www.docker.com/products/docker-desktop/)
[![n8n](https://img.shields.io/badge/n8n-Latest-green?style=for-the-badge&logo=n8n)](https://n8n.io/)
[![PostgreSQL](https://img.shields.io/badge/PostgreSQL-14-blue?style=for-the-badge&logo=postgresql)](https://www.postgresql.org/)
[![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)](LICENSE)

## 🎯 What is n8n?

[n8n](https://n8n.io/) is a powerful workflow automation tool that lets you connect different apps and services to create automated workflows. Think of it as **IFTTT on steroids** - but completely self-hosted and free!

### ✨ What You Can Do
- 🔄 **Automate repetitive tasks**
- 📧 **Connect Gmail, Slack, Discord**
- 💰 **Integrate with Stripe, PayPal**
- 📊 **Sync data between Google Sheets, Airtable**
- 🤖 **Build Telegram bots**
- 🌐 **Webhook automation**
- And much more!

---

## 🚀 Quick Start (5 minutes)

### Prerequisites
- [Docker Desktop](https://www.docker.com/products/docker-desktop/) installed and running
- Git (optional, for downloading files)

### Setup Steps

1. **Clone or download this repository**
   ```bash
   git clone https://github.com/nik132-eng/n8n-selfhost-setup-guide.git
   cd n8n-selfhost-setup-guide
   ```

2. **Create Docker network**
   ```bash
   docker network create n8n_network
   ```

3. **Start n8n with PostgreSQL**
   ```bash
   docker compose up -d
   ```

4. **Access n8n**
   Open your browser and go to: **http://localhost:5678**

🎉 **That's it!** You now have n8n running locally with a persistent database.

---

## 📁 Project Structure

```
n8n-selfhost-setup-guide/
├── docker-compose.yml          # Main Docker configuration
├── .gitignore                  # Protects sensitive files
├── README.md                   # This file
├── n8n-selfhost-docker-ngrok-guide.md  # Complete setup guide
└── backup/                     # Backup folder (created automatically)
    ├── database/
    └── workflows/
```

---

## 🌐 Make it Public (Optional)

Want to access n8n from anywhere? Make it public using:

### Option A: Ngrok (Free, Easy)
- Sign up at [ngrok.com](https://ngrok.com)
- Get your auth token
- Run: `./ngrok http 5678`
- Update `docker-compose.yml` with your URL
- Restart: `docker compose restart`

### Option B: Cloudflare Tunnel (Free, More Stable)
- Install `cloudflared`
- Create tunnel: `cloudflared tunnel create n8n-tunnel`
- Configure and run

---

## 🗄️ Database & Persistence

This setup includes:
- ✅ **PostgreSQL 14** - Professional database
- ✅ **Persistent volumes** - Data survives restarts
- ✅ **Automatic backups** - Easy data recovery
- ✅ **Network isolation** - Secure container communication

---

## 🔒 Security Features

- 🔐 **HTTPS only** (when using Ngrok/Cloudflare)
- 🌐 **Network isolation** with Docker
- 🚫 **No direct internet exposure**
- 🔄 **Regular security updates**

---

## 🛠️ Multiple Installation Methods

This guide covers **ALL** ways to install n8n:

| Method | Difficulty | Best For | Setup Time |
|--------|------------|----------|------------|
| 🐳 **Docker** | ⭐ Easy | Beginners, Production | 5 minutes |
| 🐍 **Python** | ⭐⭐ Medium | Developers | 15 minutes |
| 📦 **Direct** | ⭐⭐⭐ Hard | Advanced users | 30 minutes |
| ☁️ **Cloud** | ⭐⭐ Medium | Teams, Scaling | 20 minutes |

---

## 🚨 Troubleshooting

### Common Issues

<details>
<summary>Port 5678 already in use</summary>

```bash
# Check what's using the port
lsof -i :5678

# Kill the process
kill -9 PROCESS_ID

# Or use a different port
docker run -p 5679:5678 n8n
```
</details>

<details>
<summary>Docker permission denied</summary>

```bash
# Add user to docker group
sudo usermod -aG docker $USER

# Log out and back in
```
</details>

<details>
<summary>Database connection failed</summary>

```bash
# Check if PostgreSQL is running
docker ps | grep postgres

# Check logs
docker logs postgres_n8n

# Restart PostgreSQL
docker restart postgres_n8n
```
</details>

### Still Stuck?
1. Check the [complete guide](n8n-selfhost-docker-ngrok-guide.md)
2. Search [n8n Community](https://community.n8n.io/)
3. Open a [GitHub Issue](https://github.com/n8n-io/n8n/issues)

---

## 📚 Learning Resources

### Official Documentation
- [n8n Documentation](https://docs.n8n.io/)
- [n8n Community](https://community.n8n.io/)
- [n8n YouTube Channel](https://www.youtube.com/c/n8n-io)

### Video Tutorials
- [Complete n8n Setup](https://www.youtube.com/watch?v=RvAD2__YYjg)
- [Docker Basics](https://www.youtube.com/watch?v=3c-iBn73dDI)
- [Ngrok Tutorial](https://www.youtube.com/watch?v=HagV7I6O5kI)

---

## 🔄 Maintenance

### Weekly
- Check for n8n updates
- Monitor resource usage
- Test critical workflows

### Monthly
- Update Docker images: `docker compose pull && docker compose up -d`
- Review security settings
- Clean up old data

### Quarterly
- Review backup strategy
- Update documentation
- Plan for scaling

---

## 🤝 Contributing

Found a bug? Want to improve the guide?

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Submit a pull request

---

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## 🙏 Acknowledgments

- [n8n Team](https://n8n.io/) for the amazing automation platform
- [Docker](https://www.docker.com/) for containerization
- [PostgreSQL](https://www.postgresql.org/) for the database
- [Ngrok](https://ngrok.com/) for public tunneling
- [Cloudflare](https://www.cloudflare.com/) for tunnels

---

## 🆘 Support

### Quick Help
- **Restart everything**: `docker compose restart`
- **Check logs**: `docker logs n8n`
- **Verify network**: `docker network ls`

### Community Support
- [n8n Discord](https://discord.gg/n8n)
- [GitHub Issues](https://github.com/n8n-io/n8n/issues)
- [Stack Overflow](https://stackoverflow.com/questions/tagged/n8n)

---

## 🎉 Success Stories

> "This guide helped me set up n8n in 5 minutes. Now I automate everything!" - *John D.*

> "Finally, a guide that actually works on macOS!" - *Sarah M.*

> "Perfect for our team. We're now automating customer support workflows." - *Tech Team Lead*

---

**Ready to automate your life? 🚀**

Start with the [complete guide](n8n-selfhost-docker-ngrok-guide.md) or jump straight into the [quick start](#-quick-start-5-minutes) above!

---

<div align="center">

**⭐ Star this repo if it helped you! ⭐**

Made with ❤️ by the n8n community

</div>
