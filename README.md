# info de la materia: ST0263-242-RETO-1
#
# Estudiante(s): Samuel Rendón Trujillo. srendont@eafit.edu.co
#
# Profesor: Álvaro Ospina
#
# Despliegue de Drupal en cluster de Kubernetes (k8s) en EKS de AWS. Alta disponibilidad.
#
## 1. Descripcion
El reto consistió en el despliegue de un cluster de Kubernetes de alta disponibilidad para una página un CMS drupal (inicialmente Moodle, pero según lo conversado en clase, se pocedió con Drupal). Con una base de datos, y un NFS desplegado en EFS de AWS.

## 1.1. Que aspectos cumplió o desarrolló de la actividad propuesta por el profesor (requerimientos funcionales y no funcionales)

Se cumplió con todos los requisitos funcinales de la actividad.

Se cumplió con: 
- Despliegue de alta disponibilidad de replicas de la página en Drupal.
- Despliegue de balanceador de carga NGINX
- Despliegue de base de datos Mysql.
- Despliegue de NFS por medio de EFS de aws. Creación de dos File Systems.


## 1.2. Que aspectos NO cumplió o desarrolló de la actividad propuesta por el profesor (requerimientos funcionales y no funcionales)
Lo único con lo que no se cumplió fue con la vinculación del certificado SSL para el dominio (se tramitó por medio de AWS Certificate Manager y se validó el dominio, pero no se vinculó el certificado ssl).


# 2. información general de diseño de alto nivel, arquitectura, patrones, mejores prácticas utilizadas.

La arquitectura se basa en la replicación de pods con imágenes de componentes de software que entre sí aseguran la alta disponbilidad constante en la aplicación.

De esta manera, se crean n réplicas del CMS (Drupal), m réplicas del balanceador de carga, y, por medio de mecanismos empleados por EFS para la replicación de datos, se garantiza la consistencia de la información alojada en el sistema.

![image](https://github.com/user-attachments/assets/4d13eedc-7bbf-4fe5-92c3-3f2af98ba31b)
Imagen obtenida de <a href="https://aws.amazon.com/blogs/storage/running-wordpress-on-amazon-eks-with-amazon-efs-intelligent-tiering/">despliegue de referencia con Wordpress</a> 

# 3. Descripción del ambiente de desarrollo y técnico: lenguaje de programación, librerias, paquetes, etc, con sus numeros de versiones.

Lenguaje de programación: YAML.
Todo el despliegue se realiza por medio de archivos YAML para la definición de despliegue de servicios, creación de pods, creación de PV's (Persistent Volumes) y PVC's (Persistent Volume Claims) para la interacción con los FS de EFS, y demás.

A continuación se muestran el listado de los pods, servicios, PV's y PVC's presentes en el momento de operación del cluster:
Pods:
![image](https://github.com/user-attachments/assets/c415bc35-a2d3-418b-8c24-1c1a63e141df)

Servicios:
![image](https://github.com/user-attachments/assets/f00f6036-2bfd-4c80-a007-bd20929c648f)

PV's:
![image](https://github.com/user-attachments/assets/7371abc1-f044-4ab9-af20-79d334a59c51)

PVC'S:
![image](https://github.com/user-attachments/assets/425ea1ca-14bf-4bb2-9b6c-fde4cbda2597)


# 4. Descripción del ambiente de EJECUCIÓN (en producción) lenguaje de programación, librerias, paquetes, etc, con sus numeros de versiones.

# IP o nombres de dominio en nube o en la máquina servidor.

## descripción y como se configura los parámetros del proyecto (ej: ip, puertos, conexión a bases de datos, variables de ambiente, parámetros, etc)

## como se lanza el servidor.

## una mini guia de como un usuario utilizaría el software o la aplicación

## opcionalmente - si quiere mostrar resultados o pantallazos 

# 5. otra información que considere relevante para esta actividad.

# referencias:
<debemos siempre reconocer los créditos de partes del código que reutilizaremos, así como referencias a youtube, o referencias bibliográficas utilizadas para desarrollar el proyecto o la actividad>
## sitio1-url 
## sitio2-url
## url de donde tomo info para desarrollar este proyecto