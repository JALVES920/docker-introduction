
FROM python:3.12-alpine
 
WORKDIR /app
 
# Dépendances d'abord (meilleur cache Docker)
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt
 
# Code de l'application
COPY app.py .
COPY templates ./templates
 
EXPOSE 5000
 
# gunicorn (déjà dans requirements.txt) plutôt que le serveur de dev Flask
CMD ["gunicorn", "--bind", "0.0.0.0:5000", "app:app"]