> # Tarea 3
> 
> ### Elian Saúl Estrada Urbina
> 
> #### 201806838

# Tarea 3 - Restaurar una Base de Datos MySQL en AWS

**1. Creamos la instancia en RDS**

![image](images\01.png)

**2. Creamos la base de datos**

<img src="./images/02.png" title="" alt="image" data-align="center">

Se creo la base de datos bases2Tarea3, se creo la tabla tarea3 y se inserto un registro.

**3. Creamos la instantanea de nuestra instancia de base de datos**

![image](.\images\03.png)

**4. Creamos un bucket S3**

![image](.\images\04.png)

En este caso el bucket se llama my-storage-db2

**5. Exportamos la instantanea al bucket S3**

Primero vamos a irnos a la instantanea que creamos previamente y la seleccionamos

![image](.\images\05.png)

Luego en el botón de Acciones vamos a escoger la que dice Exportar a Amazon S3: 

![image](.\images\06.png)

Se nos abrirá la siguiente página: 

![image](.\images\07.png)

**6. Configuración de la exportación a S3**

En la primera parte de configuración vamos a colocarle un nombre para identificar nuestra exportación: 

![image](.\images\08.png)

En este caso nuestra exportación se llamara _my-exportation-db2_, este nombre será el de nuestro archivo en el bucket de S3.

Luego escogeremos los datos a exportar, en este caso vamos a exportarlo de forma parcial, para así solo tomar la base de datos que nos interesa: 

![image](.\images\09.png)

Aquí se le indica que exporte solo la base de datos llamada _bases2Tarea3_ y la tabla de esa base de datos llamada _tarea3_

Luego procederemos a escoger el bucket que utilizaremos para almacenar nuestra exportación y asu vez también indicaremos la ruta de exportación:

![image](.\images\10.png)

Aquí podemos ver que escogimos el bucke que se creo al inicio y lo guardaremos en la siguiente ruta: **_bases2/tarea3/_**

Ahora se nos pedirá un rol de IAM, para ello vamos a escoger la opción de crear nuevo rol (en dado caso no lo tengamos creado) para así crear uno automaticamente y le asignamos un nombre: 

![image](.\images\11.png)

Aquí nuestro rol de IAM se llama _rds-s3-export-role_

Luego en la clave de ARN agregamos nuestra clave de cifrado: 

![image](.\images\12.png)

Ahora se nos indica que la exportación se estar realizando 

![image](.\images\13.png)

Una vez finalizado tendremos lo siguiente: 

![image](.\images\14.png)

Y al revisar el bucket tenemos: 

![image](.\images\15.png)

Nuestra carpeta bases2 fue creada

![image](.\images\16.png)

Nuestro archivo de exportación se encuentra en el bucket
