# Use a base Jenkins image
FROM jenkins/jenkins:lts

# Install Docker inside the Jenkins container
USER root
RUN apt-get update && apt-get install -y docker.io

# Install required plugins for the pipeline
RUN jenkins-plugin-cli --plugins "docker-workflow git pipeline"

# Expose the port Jenkins will run on
EXPOSE 8080

# Configure Jenkins to run with the default commands
CMD ["/bin/tini", "--", "/usr/local/bin/jenkins.sh"]
