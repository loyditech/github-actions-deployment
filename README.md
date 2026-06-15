# GitHub Actions Deployment
 
A simple CI/CD pipeline that automatically validates and deploys a static website to GitHub Pages whenever `index.html` is updated.
 
![Deploy](https://github.com/loyditech/github-actions-deployment/actions/workflows/deploy.yml/badge.svg)
 
 
## 🚀 Live Site
 
**[loyditech.github.io/github-actions-deployment](https://loyditech.github.io/github-actions-deployment/)**
 
---
 
## ⚙️ How the Pipeline Works
 
```
Push changes to index.html
          ↓
Job 1: Validate — checks if HTML is valid
          ↓ (pass)
Job 2: Deploy — pushes to GitHub Pages
          ↓ (fail)
Pipeline stops — broken HTML is never deployed
```
 
### Pipeline Stages
 
| Stage | What it does |
|---|---|
| 🔍 **Validate** | Installs `html-validate` and checks `index.html` for errors |
| 🚀 **Deploy** | Deploys to GitHub Pages only if validation passed |
 
---
 
## 📁 Project Structure
 
```
github-actions-deployment/
├── index.html                        # Static website
├── README.md                         # This file
└── .github/
    └── workflows/
        └── deploy.yml                # CI/CD pipeline definition
```
 
---
 
## 🔧 Workflow Details
 
**Trigger:** Push to `main` branch — only when `index.html` changes
 
**Validation:** Uses `html-validate` to catch HTML errors before deployment
 
**Deployment:** Uses `peaceiris/actions-gh-pages@v4` to publish to `gh-pages` branch
 
**Key concept — `needs: validate`:** The deploy job will not run if validation fails. This ensures broken HTML is never pushed to production.
 
---
 
## 📖 Concepts Learned
 
- GitHub Actions workflow syntax
- Multi-job pipelines with dependencies
- Fail-fast CI/CD — stop deployment on errors
- GitHub Pages automated deployment
- Continuous Integration and Continuous Deployment
---
 
## 👤 Author
 
**Mark John Lloyd Ncinas**
- GitHub: [@loyditech](https://github.com/loyditech)
---
 
## 📄 License
 
MIT License — free to use, modify, and distribute.

 
