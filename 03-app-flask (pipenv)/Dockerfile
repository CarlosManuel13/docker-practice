# Usar imagen slim para reducir tamaño
FROM python:3.13

# Establecer directorio de trabajo
WORKDIR /app

# Instalar Pipenv
RUN pip install --no-cache-dir pipenv

# Configurar Pipenv para crear el entorno virtual dentro del proyecto
ENV PIPENV_VENV_IN_PROJECT=1
ENV FLASK_APP=src.app
# Copiar archivos de dependencias primero (para cacheo)
COPY Pipfile .

# Instalar dependencias con Pipenv
RUN pipenv install --deploy

# Copiar el resto del código
COPY . .

# Exponer puerto
EXPOSE 5000

CMD ["pipenv","run","flask","run","--host","0.0.0.0"]
