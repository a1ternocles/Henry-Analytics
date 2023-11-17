## Proyecto de Analisis
# Introduccion del Contenido

En este repositorio buscamos analizar una serie de base de datos dada que nos permitan obtener Insights importantes en relacion al modelo de negocio creado.
Ademas, se quiere mostrar adecuadamente el proceso realizado en pro de la replicacion del proyecto y una vista general de los distintos codigos creados para dicho fin.
Nuestro contenido esta basado en distintas etapas:

  * [Objetivo](#objetivo)
  * [Entorno Virtual](#entorno-virtual)
  * [Recoleccion del Dataset](#recoleccion-del-dataset)
  * [Procesamiento del Dataset](#procesamiento-del-dataset)
  * [Rol](#rol)
  * [EDA Accesibilidad de Internet](#eda-accesibilidad-de-internet)
  * [EDA Conectividades de Internet](#eda-conectividades-de-internet)
  * [Propuestas](#propuestas)
  * [Conclusion](#conclusion)

Es importante tener en cuenta que para este ejercicio se creo un entorno virtual que nos ayudara a empaquetar todas las librerias y codigos creados en un conjunto de carpetas que
nos permita la facil replicacion al momento de clonar el repositorio.
La base de datos que usamos se encuentra [Aqui](https://datosabiertos.enacom.gob.ar/dashboards/20000/acceso-a-internet/) y basicamente consiste en toda la informacion
proporcionada por el Gobierno Argentino referente al uso del internet, sus respectivas tecnologias y conectividades. Ademas, se presenta un [Dataset Complementario](https://datosabiertos.enacom.gob.ar/home)
que nos ayudara con nuestro analisis en caso de ser necesario. 


# Objetivo
Se busca realizar un análisis exploratorio con el objetivo de obtener diversas perspectivas e ideas fundamentales para un modelo de negocio. Este modelo se centra en una empresa de telecomunicaciones extranjera que planea realizar inversiones en diversas provincias argentinas.

Nuestro enfoque principal es comprender los tipos de tecnologías comúnmente utilizados en Argentina que facilitarán el acceso a las redes. Las redes de interés en cada provincia son el __Dial Up__ y la __Banda Ancha__.

Además, nos interesa conocer las herramientas de conexión que suelen respaldar estos tipos de redes. Estas herramientas incluyen __Fibra Óptica__, __Módem__, __Wireless__, __ADSL__ y, por último, __Otros__ (considerando cualquier alternativa que permita la conectividad a Internet).

Por último, queremos obtener una visión general del crecimiento tecnológico en relación con el uso de __Banda Ancha__ en comparación con el __Dial Up__. El Dial Up es una tecnología de acceso a Internet más antigua y más lenta que utiliza la red telefónica conmutada (RTC). Al conectarse a Internet mediante dial-up, el usuario utiliza un módem y establece una conexión a través de la línea telefónica. La velocidad de conexión suele ser considerablemente baja en comparación con tecnologías más modernas, y una desventaja significativa es que durante la conexión telefónica no se pueden realizar llamadas.

## Enlaces:
* [URL Dashboard]

# Entorno Virtual

Un entorno virtual es un ambiente aislado y autónomo que permite instalar y ejecutar diferentes versiones de programas, bibliotecas y dependencias específicas para un proyecto o aplicación.
Sirve para:

* __Isolar proyectos__: Permite trabajar en varios proyectos con diferentes requerimientos de software sin que entren en conflicto unos con otros.
* __Gestionar dependencias__: Facilita la gestión de las dependencias de un proyecto, ya que se pueden instalar versiones específicas de librerías y herramientas sin afectar el sistema global.
* __Reproducibilidad__: Asegura que un proyecto sea reproducible en diferentes entornos al tener control sobre las versiones de las dependencias.
* __Organización__: Ayuda a mantener orden en el desarrollo al separar claramente las dependencias y versiones utilizadas en un proyecto específico.

__Pasos:__
 1. Crear carpeta de trabajo (Recomendacion: Crear dentro una carpeta llamada __Py Codes__ donde se alojaran los archivos)
 2. Abrir el Terminal o CMD
 3. Buscar la carpeta en cuestion usando el comando cd "carpeta_de_trabajo"/Py Codes
 4. python3 -m venv virtual-env
 5. virtual-env\Scripts\activate.bat

De esta manera hemos creado nuestro entorno virtual dentro de la carpeta que hayamos creado.

# Recoleccion del Dataset

Para obtener los datos necesarios para la elaboracion del ejercicio, nos dirigimos al [Dataset Principal](https://datosabiertos.enacom.gob.ar/dashboards/20000/acceso-a-internet/)
y buscamos aquellas tablas que nos interesan. En este caso, aquellos datasets de interes son:
* Accesos a banda ancha y banda angosta por provincia
* Acceso a Internet fijo por tecnología y provincia
* Total nacional de accesos a Internet fijo por banda ancha y banda angosta

Como datos complementarios, nos dirigimos al [Dataset Complementario](https://datosabiertos.enacom.gob.ar/dashboards/19657/equipos-de-comunicacion-autorizados/)
y descargamos directamente la tabla de nuestro interes:
* https://datosabiertos.enacom.gob.ar/dashboards/19657/equipos-de-comunicacion-autorizados/

# Procesamiento del Dataset

Se creo un Notebook llamado __etl.ipynb__ con el fin de convertir nuestros archivos __.csv__ a __pandas.Dataframe__. Ademas, se crearon multiples funciones que nos ayudaron al ordenamiento, tranformacion y visualizacion de los distintos formatos encontrados en los archivos originales. Una vez los datos fueron transformados, estos fueron cargados como archivos tipo __.csv__ con el fin de actualizar la data anteriormente recolectada.

__Funciones:__
1. def diccionario_tipos_datos(dataframe_file)
2. def cambio_a_float(dato)
3. def cambio_a_datetime(dato)

## Nota: 
El orden de este proceso fue creado teniendo en cuenta el patron : Modelo - Vista - Controlador (MVC). Esto nos permite un mayor ordenamiento y posicion de todos los elementos que se encuentran en el codigo.
El patron creado es llamado: Libreria - Acciones - Vistas (LAV)

# Rol

Nuestro rol principal dentro de este trabajo consiste en colocarnos en los zapatos de un __Analista__ contratado por una empresa extranjera de telecomunicaciones el cual desea observar como se mueve a nivel tecnologico las distintas provincias de Argentina.
Dicha empresa desea saber si hay un panorama favorable o desfavorable al momento de competir con otras empresas ya instanciadas desde hace años. Desea conocer
los puntos de accesos y las tecnologias de las provincias para estar al tanto sobre donde comenzar con el negocio y si puede hacer un aporte significativo que resulte atractivo para las distintias comunidades: Empresariales de todos los niveles, negocios y personas de distintos niveles socioeconomicos.

Dicha empresa extranjera desea aportar tecnologicamente a Argentina trayendo mejores herramientas y metodologias de trabajo para aumentar, en la medida de lo posible, la conectividad actual. Es decir, si una provincia maneja un estandar de 30 Mbps,
la iniciativa seria aumentar a 100 Mbps como minimo. Asi mismo, si una provincia tiene una baja cantidad de recursos en lo que respecta a la __Banda Ancha__, la iniciativa seria invertir en infraestructura que permita la conexion a mas hogares o personas del comun.
Y por ultimo, si un negocio (de cualquier tipo: Empresa o negocio de distintos niveles) cuenta con una infraestructura antigua, la iniciativa es mejorar dicha infraestructura para que sus servicios de conectividad aumenten de manera exponencial.

# EDA Accesibilidad de Internet

Se creo un Notebook llamado __eda_accesibilidad_tech.ipynb__ con el fin de explorar nuestros datos y tener una vision de que esta pasando con estos. Es importante resaltar que se busca informacion util como: Outliers, Quartiles, Moda, Media, Mediana, etc. Ademas, por cada analisis o grafica creada dentro del archivo, hay pequenas observaciones al final de estos con la intencion de dar una perspectiva de la informacion trabajada.

## servaciones

# EDA Conectividades de Internet

Se creo un Notebook llamado __eda_conectividades_tech.ipynb__ con el fin de explorar nuestros datos y tener una vision de que esta pasando con estos. Es importante resaltar que se busca informacion util como: Outliers, Quartiles, Moda, Media, Mediana, etc. Ademas, por cada analisis o grafica creada dentro del archivo, hay pequenas observaciones al final de estos con la intencion de dar una perspectiva de la informacion trabajada.

## Observaciones: 

# Propuestas
Aca va la propuesta



## Nota: 
El orden de este proceso fue creado teniendo en cuenta el patron : Modelo - Vista - Controlador (MVC). Esto nos permite un mayor ordenamiento y posicion de todos los elementos que se encuentran en el codigo.
El patron creado es llamado: Libreria - Acciones - Vistas (LAV)


# Conclusion

Aca va la conclusion



