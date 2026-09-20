# CI/CD Pipeline Project 🚀

![Build Status](https://github.com/Chaitanyasarkate/ci-cd-demo/actions/workflows/main.yml/badge.svg)

## Overview

This project demonstrates a complete **CI/CD pipeline** using **GitHub Actions**, **Docker**, and **Node.js**. It showcases automated testing, containerization, and deployment practices.

## Tech Stack

- **Node.js** - JavaScript runtime
- **Express.js** - Web framework
- **Jest** - Testing framework
- **Docker** - Containerization
- **GitHub Actions** - CI/CD automation

## Pipeline Flow

```
1. 📝 Code pushed to GitHub (main branch)
   ↓
2. 🔄 GitHub Actions triggered automatically
   ↓
3. 📦 Dependencies installed
   ↓
4. ✅ Tests executed (Jest)
   ↓
5. 🐳 Docker image built
   ↓
6. 📤 Image pushed to DockerHub (optional)
```

## Project Structure

```
ci-cd-demo/
├── app.js                          # Express server
├── package.json                    # Project dependencies
├── Dockerfile                      # Docker configuration
├── test/
│   └── app.test.js                 # Jest tests
├── .github/
│   └── workflows/
│       └── main.yml                # GitHub Actions workflow
└── README.md                       # Documentation
```

## How to Run Locally

### Prerequisites

- Node.js 18+ installed
- npm installed
- Docker installed (optional, for local containerization)

### Installation

```bash
# Install dependencies
npm install

# Run the application
npm start
# or
node app.js

# Run tests
npm test
```

The app will be available at `http://localhost:3000`

## Docker

### Build Docker Image

```bash
docker build -t ci-cd-demo:latest .
```

### Run Docker Container

```bash
docker run -p 3000:3000 ci-cd-demo:latest
```

## GitHub Actions Workflow

### What Happens on Every Push

1. **Checkout** - Clones your code
2. **Setup Node.js** - Sets up Node.js 18
3. **Install Dependencies** - Runs `npm install`
4. **Run Tests** - Executes `npm test` (Jest)
5. **Build Docker Image** - Creates Docker image
6. **Login to DockerHub** - Authenticates with your credentials
7. **Push Image** - Uploads image to DockerHub registry

### Setting Up Secrets

To enable Docker image pushing, add these secrets to your GitHub repository:

1. Go to **Settings → Secrets and variables → Actions**
2. Click **New repository secret**
3. Add:
   - `DOCKER_USERNAME` - Your DockerHub username
   - `DOCKER_PASSWORD` - Your DockerHub password or personal access token

**Note:** Replace `your-dockerhub-username` in `.github/workflows/main.yml` with your actual DockerHub username.

## Deployment Options

### Option A: Render (Easiest)

1. Connect your GitHub repository to Render
2. Create a new Web Service
3. Auto-deploy on every push to main branch

### Option B: AWS EC2

1. Launch an EC2 instance
2. SSH into the instance
3. Install Docker: `apt-get install docker.io`
4. Pull and run your image:
   ```bash
   docker pull your-dockerhub-username/ci-cd-demo:latest
   docker run -p 80:3000 your-dockerhub-username/ci-cd-demo:latest
   ```

### Option C: Manual Testing

Simply push to the main branch and watch the GitHub Actions workflow run:

1. Go to your repository
2. Click **Actions** tab
3. Watch the workflow execute in real-time
4. Check for ✅ (success) or ❌ (failure)

## Testing

This project uses **Jest** for testing. Add more tests in `test/app.test.js`:

```javascript
test('Sample Test', () => {
  expect(1 + 1).toBe(2);
});
```

Run tests with:

```bash
npm test
```

Tests also run automatically in the CI/CD pipeline on every push.

## Key Features to Impress Recruiters

✅ **Automated Testing** - Tests run on every push  
✅ **Docker Containerization** - App packaged consistently  
✅ **CI/CD Pipeline** - Fully automated workflow  
✅ **Build Status Badge** - Shows pipeline status  
✅ **Multiple Deployment Options** - Flexible deployment  
✅ **Secrets Management** - Secure credential handling  
✅ **Comprehensive Documentation** - Clear instructions  

## Troubleshooting

### Pipeline Failing?

1. Check the **Actions** tab in GitHub for error messages
2. Verify Node.js version: `node --version` (should be 18+)
3. Run tests locally: `npm test`
4. Check Docker image name matches your DockerHub username

### Tests Not Running?

```bash
npm install --save-dev jest
npm test
```

### Docker Push Failing?

1. Verify `DOCKER_USERNAME` and `DOCKER_PASSWORD` secrets are set
2. Check DockerHub credentials are correct
3. Ensure the image name in workflow matches your username

## Resources

- [GitHub Actions Documentation](https://docs.github.com/en/actions)
- [Docker Documentation](https://docs.docker.com/)
- [Jest Testing Framework](https://jestjs.io/)
- [Express.js Guide](https://expressjs.com/)

## License

ISC

---

**Made for DevOps & CI/CD Learning 🚀**
