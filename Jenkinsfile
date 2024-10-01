/*Ejercicio 6
Desarrollar un pipeline que informe lo siguiente:
-	Clima actual
-	Población actual
Desde la rama de desarrollo a través de un Jenkinsfile*/

pipeline {
    agent any

    environment {
        API_KEY = 'c6e28ee4beb13e779c119083e478e8c1'
        CITY = 'Ciudad%20Real'
        API_URL = "http://api.openweathermap.org/data/2.5/weather?q=${CITY}&&appid=${API_KEY}&units=metric"
    }
    
    stages {
        stage("Clima Actual") {
            steps {
                script {
                    // Usa PowerShell para hacer una solicitud a la API
                    def weather = powershell(script: "Invoke-RestMethod -Uri '${API_URL}'", returnStdout: true).trim()
                    echo weather

                    // Si tienes jq instalado, puedes usarlo en PowerShell, de lo contrario, usa otra manera de procesar la salida JSON
                    /*def temperature = powershell(script: "(Invoke-RestMethod -Uri '${API_URL}').main.temp", returnStdout: true).trim()
                    def weatherDescription = powershell(script: "(Invoke-RestMethod -Uri '${API_URL}').weather[0].description", returnStdout: true).trim()*/

                    // Muestra la información del clima
                    /*echo "Clima actual en ${CITY}: ${temperature}°C, ${weatherDescription}"*/
                }
            }
        }
    }
}
