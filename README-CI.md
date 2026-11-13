Caleb Tisler

# Part 1

## Dockerfile & Building Images
### Website Content
- [index.html](web-content/index.html) : this is the link to the web pages index page that has a button to go to the secret page
- [secret.html](web-content/secret.html) : this is the link to  the web pages secret page that has a button to go to the index page
- [style.css](web-content/style.css) : this is the link to the websites style sheet that formats the design of the website

### Dockerfile
- [Dockerfile](Dockerfile) : this docker file contains `FROM httpd:2.4` which is where the image builds from and `COPY ./ /usr/local/apache2/htdocs/` which copies everything in [web-content](web-content/) into `/usr/local/apache2/htdocs/`.

### Building Image
I used `docker build -t armedpotatochip/button-site:latest .` within the web-contents folder of the repo

### Running Container
I used `docker run -d --name buttontest -p 8080:80 armedpotatochip/button-site:latest` within the web-contents folder of the repo


# Part 2

## Configuring GitHub Repository Secrets
- To create the PAT you must go to your docker account setting on docker and under personal accesss token make one with read and write settings
- To create Github Action Secrets you must go to the repos settings and in there there under Secrets and Variables you can click actions to make Those action secrets
- The secrets used for this project are : DOCKER_USERNAME, which is my docker user; DOCKER_TOKEN, which is my PAT token created

## CI with GitHub Actions
- When a commit is pushed on main the workflow is ran

- The first step is "Login to Docker Hub" which uses `docker/login-action@v41` and the secrets DOCKER_USERNAME and DOCKER_TOKEN to log into docker hub
-  The next step is "Set up Docker Buildx" which uses `docker/setup-buildx-action@v4` to set up the building of the image
-  The Last step is "Build an Push" which uses `docker/build-push-action@v7` to build the image and push it to docker hub

- if this workflow is used in a different repo the you would need to change:
  - The workflow tags would be different for the image
  - The repo secrets would need to be added to the new repo with ist of PAT and docker username
 
