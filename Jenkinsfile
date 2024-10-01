/*Ejercicio 6
Desarrollar un pipeline que informe lo siguiente:
-	Clima actual
-	Población actual
Desde la rama de desarrollo a través de un Jenkinsfile*/

pipeline {
    agent any

    environment {
        API_KEY = 'c6e28ee4beb13e779c119083e478e8c1' // Clave API de OpenWeatherMap
        CITY = 'Ciudad Real' // Ciudad a consultar
        API_URL = "http://api.openweathermap.org/data/2.5/weather?q=${CITY}&appid=${API_KEY}&units=metric"
        POPULATION = '75,000' // Cambia a la población actual (actualiza este valor manualmente)
    }
    
    stages {
        stage("Clima Actual") {
            steps {
                script {
                    // Usa curl para hacer una solicitud a la API
                    def weather = sh(script: "curl -s '${API_URL}'", returnStdout: true).trim()
                    
                    // Extrae la temperatura y la descripción del clima usando jq
                    def temperature = sh(script: "echo '${weather}' | jq '.main.temp'", returnStdout: true).trim()
                    def weatherDescription = sh(script: "echo '${weather}' | jq -r '.weather[0].description'", returnStdout: true).trim()

                    // Muestra la información del clima
                    echo "Clima actual en ${CITY}: ${temperature}°C, ${weatherDescription}"
                    echo "Población actual de ${CITY}: ${POPULATION}"
                }
            }
        }
    }
}

