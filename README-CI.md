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
