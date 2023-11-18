# Secure webapp

Este proyeto consiste en implementar una sencilla aplicación web sin servidor con autenticación, Esta aplicación usá el servicio de AWS cognito para permitir que los usuarios puedan registrarse e ingresar a la aplicación de manera segura.

Este proyecto se realizo gracias a la guía de AWS para [CREAR UNA APLICACIÓN WEB SIN SERVIDOR](https://aws.amazon.com/es/getting-started/hands-on/build-serverless-web-app-lambda-apigateway-s3-dynamodb-cognito/)

## Requisitos

- GIT.
- Una cuenta en GITHUB (También sirven otras plataformas que permiten alojar proyectos utilizando el sistema de control de versiones Git, ).
- Una cuenta de AWS.
- La [AWS CLI](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html) instalada.

## Arquitectura de aplicaciones
La arquitectura de la aplicación utiliza AWS Lambda, Amazon API Gateway, Amazon DynamoDB, Amazon Cognito y la consola de AWS Amplify para construir cada parte de la aplicación.

Y se implementa en 4 pasos:

1. **Alojar un sitio web estático:** configurar AWS Amplify para alojar los recursos estáticos para la aplicación web con implementación continua incorporada.
2. **Administrar usuarios:** crear un grupo de usuarios de Amazon Cognito para administrar las cuentas de los usuarios.
3. **Crear un backend sin servidor:** Crear un proceso de backend para manejar las solicitudes de la aplicación web e implementarlo en una función de Lambda.
4. **Implementar una API RESTful:** Usando Amazon API Gateway para exponer una función de Lambda como una API RESTful.

## Alojar un sitio web estático
Para este paso se creó un repositorio en github y usando el cliente de AWS en la terminal se trajeron los archivos de un repositorio remoto para enviarlos al repositorio nuevo que fue creado en github, con los siguientes comandos.

```Bash
# Se clona el repositorio nuevo creado en la cuenta de github
git clone https://github.com/Ricar8o/wildrydes-site.git 

# Se accede a la carpeta del repositorio
cd wildrydes-site

aws s3 cp s3://wildrydes-us-east-1/WebApplication/1_StaticWebHosting/website ./ --recursive
```
Con estos comandos ya tendremos todos los recursos en el repositorio remoto de github.

Lo siguiente es ir al servicio de Amplify en la plataforma de AWS, escoger la opción de alojar una aplicación web y nos mostrará para elegir desde donde traeremos el código que se desplegará en la aplicación.

![Alt text](img/amplify-code-providers.png)

Escogemos github, le damos permiso sobre el repositorio que creamos, escogemos el repositorio y seguimos los demás pasos de la guía para hacer el despliegue. 

Al implementarla realiza los pasos para desplegar la aplicación y nos brinda un link para verla.

![amplify-compile](img/amplify-compile.png)
![front-deployed](img/front-deployed.png)

## After cognito integration
![register-form](img/register-form.png)
![verify-account](img/verify-account.png)
![account-verified](img/account-verified.png)

## Dynamo table
![dynamo-table](img/dynamo-table.png)

## Lambda Implementation
![lambda](img/lambda.png)
![lambda-event](img/lambda-event.png)

## API Gateway
![api-gateway](img/api-gateway.png)

## API integration
![ride-working](img/ride-working.png)
![unicorn-requested](img/unicorn-requested.png)


## Visit the page

[![amplifybutton](https://github.com/aws-amplify/docs/blob/main/public/images/Logos/Amplify%20Logo.svg)](https://main.d1qvsexai5zdix.amplifyapp.com)
