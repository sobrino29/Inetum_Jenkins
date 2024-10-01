/*Ejercicio 6
Desarrollar un pipeline que informe lo siguiente:
-	Clima actual
-	Población actual
Desde la rama de desarrollo a través de un Jenkinsfile*/

pipeline {
    agent any

    environment {
        API_KEY = 'c6e28ee4beb13e779c119083e478e8c1'
        CITY = 'Ciudad%20Real' // Asegúrate de que la ciudad esté codificada
        API_URL = "http://api.openweathermap.org/data/2.5/weather?q=${CITY}&&appid=${API_KEY}&units=metric"
    }
    
    stages {
        stage("Clima Actual") {
            steps {
                script {
                    // Usa curl para hacer una solicitud a la API
                    def weather = sh(script: "curl -s '${API_URL}'", returnStdout: true).trim()

                    // Extrae información usando jq (asegúrate de que jq esté instalado en tu entorno de Jenkins)
                    def temperature = sh(script: "echo '${weather}' | jq '.main.temp'", returnStdout: true).trim()
                    def weatherDescription = sh(script: "echo '${weather}' | jq -r '.weather[0].description'", returnStdout: true).trim()

                    // Muestra la información del clima
                    echo "Clima actual en ${CITY}: ${temperature}°C, ${weatherDescription}"
                }
            }
        }
    }
}

