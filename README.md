
# Example repository to deploy Strapi to Cloud Run

## 1. Project Structure
.
├── README.md
├── cloudbuild.yaml
├── compose
│   ├── gitlab
│   ├── local
│   └── production
└── my-project
    ├── api
    ├── build
    ├── config
    ├── extensions
    ├── favicon.ico
    ├── node_modules
    ├── package-lock.json
    ├── package.json
    ├── public
    └── server.js

- Compose:
    + gitlab:
    + local:
    + production: postgres image and images for Strapi deployment
- my-project: Strapi Project

## 2. Set up hcms back end

Example:
- Build base image
`docker build -f compose/production/my-project/Dockerfile.cloudrun.base . -t asia.gcr.io/int-ml-ai/base/my-project:0.1.0-strapi-3.6.8`
- Build app image
`docker build -f compose/production/my-project/Dockerfile.cloudrun . -t asia.gcr.io/int-ml-ai/my-project-dev:0.1.0-strapi-3.6.8`

- Run image at local
`docker run -d -p 1337:1337 asia.gcr.io/int-ml-ai/my-project-dev:0.1.0-strapi-3.6.8`

## 3. Deploy by SDK
Create `cloudbuild.yaml` to specific Dockerfile and build image then push to Container Registry. Cloud Run will pull built image to run.

At folder contains `cloudbuild.yaml`, run `gcloud builds submit`
