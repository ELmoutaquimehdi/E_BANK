# Utiliser l'image Node
FROM node:20

# Définir le répertoire de travail
WORKDIR /app

# Copier package.json et package-lock.json
COPY package*.json ./

# Installer les dépendances
RUN npm install

# Copier le reste du projet
COPY . .

# Exposer le port Angular (par défaut 4200)
EXPOSE 4200

# Lancer Angular en mode dev et écouter sur toutes les interfaces
CMD ["npm", "start", "--", "--host", "0.0.0.0"]
