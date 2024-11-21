# Usar una imagen base de Python
FROM python:3.9-slim

# Establecer el directorio de trabajo
WORKDIR /app

# Copiar los archivos de la aplicación al contenedor
COPY . /app

# Instalar dependencias
RUN pip install --no-cache-dir -r requirements.txt

# Exponer el puerto en el que la aplicación escucha
EXPOSE 5000

# Comando para ejecutar la aplicación
CMD ["python", "app.py"]  # Ajusta esto según tu aplicación
