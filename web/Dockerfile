FROM python:3.7-slim

# Créer un répertoire pour l'application
RUN mkdir /app

# Définir le répertoire de travail
WORKDIR /app

# Copier les fichiers nécessaires pour installer les dépendances
COPY requirements.txt /app/

# Installer les dépendances Python
RUN pip install --no-cache-dir -r requirements.txt

# Copier les fichiers statiques et templates
COPY ./static /app/static/
COPY ./templates /app/templates/

# Copier les fichiers principaux de l'application
COPY ./dbconnect.py /app/
COPY ./app.py /app/

# Exposer le port Flask
EXPOSE 5000

# Commande pour lancer l'application (avec Flask pour le développement)
CMD ["gunicorn", "-w", "4", "-b", "0.0.0.0:5000", "app:app"]
