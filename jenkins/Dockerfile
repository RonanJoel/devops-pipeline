# Usar una imagen base de Jenkins
FROM jenkins/jenkins:lts

# Instalar plugins necesarios para el pipeline
RUN jenkins-plugin-cli --plugins "docker-workflow git pipeline"

# Exponer el puerto en el que Jenkins se ejecutará
EXPOSE 8080

# Configurar Jenkins para ejecutarse con los comandos predeterminados
CMD ["/bin/tini", "--", "/usr/local/bin/jenkins.sh"]
