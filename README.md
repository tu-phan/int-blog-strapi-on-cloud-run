
# Example repository to deploy Strapi to Cloud Run

## 1. A typical top-level directory layout
    .
    ├── README.md
    ├── cloudbuild.yaml
    ├── compose
    │   ├── gitlab              # image for CI/CD on gitlab
    │   ├── local
    │   └── production          # postgres image and images for Strapi deployment
    └── my-project              # Strapi Project
        ├── api                 # API definition: route, services, ...
        ├── build               # Admin UI
        ├── config              # Server Configs and other configs
        ├── extensions          # Other extensions for your app
        ├── favicon.ico
        ├── node_modules
        ├── package-lock.json
        ├── package.json
        ├── public              # robots.txt, ...
        └── server.js           # Scripts run server

> Use short lowercase names at least for the top-level files and folders except
> `LICENSE`, `README.md`

## 2. Set up hcms back end

- Base Image: `compose/production/my-project/Dockerfile.cloudrun.base`
- Image for production: `compose/production/my-project/Dockerfile.cloudrun`

- Example running at local:
    + Build base image `docker build -f compose/production/my-project/Dockerfile.cloudrun.base . -t asia.gcr.io/int-ml-ai/base/my-project:0.1.0-strapi-3.6.8`
    + Build app image `docker build -f compose/production/my-project/Dockerfile.cloudrun . -t asia.gcr.io/int-ml-ai/my-project-dev:0.1.0-strapi-3.6.8`

    + Run image at local `docker run -d -p 1337:1337 asia.gcr.io/int-ml-ai/my-project-dev:0.1.0-strapi-3.6.8`

## 3. Deploy by SDK
> Create `cloudbuild.yaml` to specific Dockerfile and build image then push to Container Registry. Cloud Run will pull built image to run.

- At folder contains `cloudbuild.yaml`, run command `gcloud builds submit`

# License information

If you want to share your work with others, please consider choosing an open
source license and include the text of the license into your project.
The text of a license is usually stored in the `LICENSE` (or `LICENSE.txt`,
`LICENSE.md`) file in the root of the project.

> You’re under no obligation to choose a license and it’s your right not to
> include one with your code or project. But please note that opting out of
> open source licenses doesn’t mean you’re opting out of copyright law.
> 
> You’ll have to check with your own legal counsel regarding your particular
> project, but generally speaking, the absence of a license means that default
> copyright laws apply. This means that you retain all rights to your source
> code and that nobody else may reproduce, distribute, or create derivative
> works from your work. This might not be what you intend.
>
> Even in the absence of a license file, you may grant some rights in cases
> where you publish your source code to a site that requires accepting terms
> of service. For example, if you publish your source code in a public
> repository on GitHub, you have accepted the [Terms of Service](https://help.github.com/articles/github-terms-of-service)
> which do allow other GitHub users some rights. Specifically, you allow others
> to view and fork your repository.

For more info on how to choose a license for an open source project, please
refer to http://choosealicense.com