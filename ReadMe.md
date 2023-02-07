# Run Sonarqube at your local machine

## Prerequisites

- Docker + Docker Compose
- [SonarScanner (client)](https://docs.sonarqube.org/latest/analyzing-source-code/scanners/sonarscanner/)

## Preparation

### Sonarqube Server

```bash
# Start the server
$ docker compose up -d
```

### Prepare Sonarqube Configuration file in your project

Create a file named `sonar-project.properties` in your project root directory. See `sonar-project.properties.example.properties` for an example.

## Run SonarScanner

Choose one of the following options to run SonarScanner.

### If you run SonarScanner from the zip file

```bash
# Install SonarScanner from the zip file first
# https://docs.sonarqube.org/latest/analyzing-source-code/scanners/sonarscanner/#running-from-zip-file

# Run
$ cd your-project
$ sonar-scanner
```

### If you run SonarScanner from docker container and your server is running on your host at default port 9000

```bash
$ docker run \
    --rm \
    -e SONAR_HOST_URL="http://host.docker.internal:9000" \
    -e SONAR_SCANNER_OPTS="-Dsonar.projectKey=${YOUR_PROJECT_KEY}" \
    -e SONAR_LOGIN="myAuthenticationToken" \
    -v "${YOUR_REPO}:/usr/src" \
    sonarsource/sonar-scanner-cli
```
