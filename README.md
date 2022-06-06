se clona projecto de jmeter desde github
se inicializar una instancia de sonarqube de la manera que te guste

yo corri en docker una imagen del projecto
dejo compando para correrlo

todo esto trabajado en un fichero como espacio de trabajo

instalar java antes para con el respectivo jdk necesario 

git clone jmeter
docker pull sonarqube
docker run -d --name sonarqube -p 9000:9000 -p 9092:9092 sonarqube

por defecto al querer conectarte a sonarqube deployado te generará
un usuario base llamado

username: admin
password: admin

deberas cambiar tu contraseña cuando ingreses

al entrar necesitar crear un projecto con un nombre y una llave

asignales test y test

cuando te pida analizar un codigo pide que sea de manera local o locally

genera el token correspondiente

al dalrte a continuar y pasar a la etapa 2, sonarqube ya 
configurado nos preguntará como queremos correr el analisis

nos pedirá generar un key que será util en el siguiente paso.

Aparecerá un menú con distintas opciones para correr el analisis en distintos projectos. La opcion para este caso es "gradle", y nos entregará un script con este formato

```
./gradlew sonarqube \
  -Dsonar.projectKey=${PROJECT_NAME} \
  -Dsonar.host.url=${URL_TO_SONARQUBE_INSTANCE} \
  -Dsonar.login=${GENERATED_KEY}
```

GENERATED_KEY = KEY GENERADA EN EL PASO ANTERIOR
URL_TO_SONARQUBE_INSTANCE = URL DONDE está desplegada nuestra instancia de sonarqube
PROJECTNAME = nombre del projecto asignado


una vez tengamos sonarqube corriendo y clonado el repositorio de github de JMeter y no tenemos ninguna dependencia con Java o sus versiones podemos correr el comando que sonarqube nos ha dado dentro del projecto como tal.

esto generará el informe correspondiente en nuestra instancia de sonarqube.