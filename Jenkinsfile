/*Ejercicio 6
Desarrollar un pipeline que informe lo siguiente:
-	Clima actual
-	Población actual
Desde la rama de desarrollo a través de un Jenkinsfile*/


pipeline
{
    agent any

    environment {
        API_KEY = 'c6e28ee4beb13e779c119083e478e8c1' // Reemplaza con tu clave API de OpenWeatherMap
        CITY = 'Ciudad Real' // Cambia a la ciudad que deseas consultar
        API_URL = "http://api.openweathermap.org/data/2.5/weather?q=${CITY}&appid=${API_KEY}&units=metric"
    }
    stages
    {
        stage("ClimaActual")
        {
            steps
            {
                script{
                  // Usa curl para hacer una solicitud a la API
                    def weather = sh(script: "curl -s '${API_URL}'", returnStdout: true).trim()
                    echo "Clima actual en ${CITY}: ${weather}"  
            }
      }
   }     
}
