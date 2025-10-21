pipeline {
    agent any // S'exécute sur le conteneur Jenkins

    stages {
        stage('1. Build and Deploy on Azure VM') {
            steps {
                script {
                    sh '''
                        ssh -o StrictHostKeyChecking=no -i ../Docker/1337.pem Kiro@172.161.81.1 "
                            echo "✅ Connecté au serveur Azure..."
                            
                            # 1. Naviguer vers le répertoire du projet
                            # Le chemin peut changer selon votre utilisateur
                            cd /home/azureuser/CRUD-PostgreSQL-Todo-List
                            
                            # 2. Récupérer le code le plus récent de GitHub
                            git pull
                            
                            # 3. Builder l'image de l'application
                            docker-compose build app
                            
                            # 4. Démarrer/Mettre à jour la stack
                            docker-compose up -d
                            
                            echo "🚀 Déploiement sur Azure terminé !"
                        "
                    '''
                }
            }
        }
    }
}