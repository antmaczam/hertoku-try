Plataforma sobre alquiler de juegos de mesa
===========================================

El objetivo de este proyecto es implementar una plataforma para el alquiler
de juegos de mesa, de manera que se facilite este alquiler ya que se realiza
entre los mismo usuarios. La ventaja de esta web es que los juegos te aparecen
por distancia, o sea, los primeros serán los más cercanos así no dependes de 
un local o almacen en el cual hay que  ir a recogerlo.

Se trata de un proyecto para la asignatura ISPP, pensado para acercarse a un
proyecto realista que se puede encontrar en cualquier empresa. Hay que buscar 
la innovación y el beneficio y buscar clientes pilotos que al final compren 
la aplicación por su utilidad (la compra no se realiza, es una forma de reflejar
que sería algo por lo que pagarían).

Módulos
-------

Este proyecto Django se divide en 3 módulos principales, los cuales estarán desacoplados
entre ellos. Donde cualquier de ellos sw podrá reemplazar individualmente.

* **rent:** Este es el módulo principal de la aplicación, se encargar del alquiler de los juegos y mostrar los mismos.
* **user:** Este se encarga de la organización de los usuarios y del registro de los mismos.
* **stripe:** Se encarga del tema de los pagos, como su mismo nombre indica, usaremos stripe para esta tarea.
* **review:** El subsistema de chat está destinado para poder valorar los productos que suben los usuarios como a los propios usuarios.

Configurar Postgres (Windows)
-----------------------------

Para instalar Postgres en Windows, lo primero es descargar e instalar es necesario seguir los pasos de esta pequeña guía: http://www.postgresqltutorial.com/install-postgresql/ (Consejo: toma nota del directorio donde lo instalaste), y el ejecutable lo puedes encontra aquí: http://www.enterprisedb.com/products-services-training/pgdownload#windows.

Abre la línea de comandos (Inicio → Todos los programas → Accesorios → Linea de comandos o Inicio → Ejecutar → cmd)
Ejecuta el siguiente comando para añadir la ruta al PATH de Windows o añádela manualmente (asegúrate de que el la carpeta sea la misma que anotaste cuando estabas instalando con un \bin al final)

    setx PATH "%PATH%;C:\Program Files\PostgreSQL\9.3\bin"

Cierra y vuelve a abrir la línea de comandos.
    
* **Crear la base de datos**

Primero, vamos a iniciar la consola de Postgres ejecutando el siguiente comando:

    psql -U <username> -W
    
donde username es el nombre de usuario que se usó en la instalación. Después pedirá introducir la contraseña que se puso para ese usuario.

Ahora vamos a crear un usuario para nuestra bbdd con la siguiente linea

    # CREATE USER board WITH PASSWORD 'board';
    
Y para la bbdd escribimos lo siguiente 

    # CREATE DATABASE boardDB OWNER board;

Configurar el proyecto
----------------------

Para configurar el proyecto, será necesario instalar las dependencias del proyecto, las cuales están en el
fichero requirements.txt:

    pip install -r requirements.txt

Entramos en la carpeta del proyecto (cd board) y realizamos la primera migración para preparar la
base de datos que utilizaremos:
    
    python manage.py makemigrations

    python manage.py migrate

Y para finalizar, vamos a crear un super usuario

    python manage.py createsuperuser
    
Por último, ya podremos ejecutar el módulos o módulos seleccionados en la configuración de la
siguiente manera:

    python manage.py runserver
