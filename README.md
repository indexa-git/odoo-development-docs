# Odoo Development Docs

Este repositorio consiste en una serie de pasos y informaciones claves para desarrolladores de Odoo.

-Se creo un repositorio para los docs
-Modificacion del readme especificando el proposito del repositorio
-Instalacion de las dependencias previas para la instalacion de odoo:

	~sudo apt-get update
	~sudo apt-get upgrade
	~sudo apt-get install software-properties-common
	~sudo apt-get install python-software-properties
	~sudo apt-get install python-dev

ERROR: en el caso de presentar el error "Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution) libreoffice", debe de ejecutar el siguiente comando en la terminal "sudo dpkg --configure --force-overwrite -a" y en caso de que despues de este comando el error persista, debe de ejecutar "sudo apt -o Dpkg::Options::="--force-overwrite" --fix-broken install"

	~sudo apt-get install python-dateutil python-feedparser python-ldap python-libxslt1 python-lxml python-mako python-openid python-psycopg2 	 python-pybabel python-pychart python-pydot python-pyparsing python-reportlab python-simplejson python-tz python-vatnumber python-vobject 	python-webdav python-werkzeug python-xlwt python-yaml python-zsi python-docutils python-psutil python-mock python-unittest2 python-jinja2 	 python-pypdf python-decorator python-requests python-passlib python-pil -y python-suds

	~sudo apt install python3-dev libxml2-dev libxslt1-dev libldap2-dev libsasl2-dev \
    	libtiff5-dev libjpeg8-dev libopenjp2-7-dev zlib1g-dev libfreetype6-dev \
    	liblcms2-dev libwebp-dev libharfbuzz-dev libfribidi-dev libxcb1-dev libpq-dev

-Creacion del virtualEnv de tal manera que se creen ejecutables de python unicos para cada version con sus dependencias necesarias.
 	-pip install virtualenv
	-mkdir ~/.virutalenvs
	-virtualenv --python=`which python<version>` ~/.virtualenvs/<file_name>

-Creacion de entorno de trabajo donde se instalara odoo
	-mkdir ~/<file_work_name>
	-mkdir odoo
	-cd odoo
	-mkdir odoo<version>(odoo13 o odoo14 dependiendo la version de odoo que se desee instalar)
	-cd odoo<version>
	-git clone https://github.com/odoo/odoo.git --branch <branch> --depth 1 

-Abrir pycharm(en caso de no tenerlo, proceder a instalarlo)

-Dar click en la pestana files y seleccionar Settings
-En la ventana abierta seleccionar terminal para agregar el path del interpretador, el cual es el absolute path de donde se encuentra este en el shell path (comando para encontrar el absolute path "which 'nombre del archivo' ")

-Proceder a la terminal de Pycharm para activar el virtualenv con el comando source ~/.virtualenvs/odoo10/bin/activate

- una vez accedido entramos en la carpeta de Odoo almacenada en los directorios que guardamos y copiamos, para acceder a esta debe de copiar el absolute path. Ej: cd /home/pro02001/dev/odoo13/odoo

- visualizar el archivo de requirements.txt, en este se encuentra todos los archivos necesarios para la instalacion de la dependencia, con el comando pip install -r requirements.txt
En el caso de presentar un error con alguna dependencia, instalar manualmente con los comando de pip o buscar la libreria especifica accediendo al interpreter de pycharm,  para acceder al interpreter presione las telcas ctrl + alt + s, seleccionar el proyecto y en las opciones seleccionar el interpretador

-En la ventana que se muestra deberia de aparecerle una lista de todas las librerias instaladas, en este caso para agregar una nueva, seleccionar el + y buscarla por el nombre

-- INSTALAR POSTGRESQL

-Ejecutar el comando sudo apt install postgresql -y
-Ejecutar el comando "sudo apt install postgresql-client

--ERROR: Failed building wheel for greenlet. Para resolver este error tiene que instalar la version de greenlet correspondiente segun la version de python con la que se este trabajando,los cuales estan en el requirements.txt Ej: pip install greenlet==0.4.15


- Crear un usuario en postgres con el comando a sudo -u postgres createuser -s $USER

- En la cartpeta de odoo buscar el archivo llamado odoo-bin , copiar la ruta del odoo been y confirmar que al hacer click en run, esta sea la misma ruta en el script path

-En interpreter options, se debe de seleccionar el virtual environment que esta utilizando, en caso de no aparecer debe de entrar en files>settings, seleccionar python interpreter y en la barra de selecciones que se muestre debe de darle click a este y seleccionar show all, en la ventana que se abre, seleccione el icono + y seleccionar el virtualenv que creamos anteriormente

- Marcar la carpeta de emulate terminal 

- En la terminal ejecutar el comando "python odoo-bin -s --stop-after-init"

--ERROR: se presento un error con la libreria lxml, que tiene que ver con la version de python 3.10, se soluciona instalando versiones anteriores, en este caso se recomienda instalar la version 3.7:
	-sudo apt update && sudo apt upgrade
	-sudo apt install software-properties-common -y
	-sudo add-apt-repository ppa:deadsnakes/ppa -y
	-sudo apt update
	-sudo apt install python3.7 -y
	-python3.7 --version
	-sudo apt install python3.7-dev
	-sudo apt install python3.7-distutils
	
	- Borrar el virtualenviroment creado anteriormente con el comando, rm -rf odoo14
	y proceder a crear uno nuevo y proceder a instalar las dependencias con e comando:
		-- pip install -r requirements.txt

- En la terminal de pycharm con el virtualenvironment activado, ejecutar el comando:

	-python odoo-bin -s --stop-after-init

-el comando anterior generara una archivo de configuracion en la carpeta home de manera oculta, llamado .odoorc.

- nover el archivo a nuestro proyecto odoo con el comando mv .odoorx ~/home/

- abrir el archivo en pycharm

-- CONCEPTOS

- Addon_path: se indican donde estan los modulos que se pueden instalar, tanto los nativos como los custom
- admin_passwd: password del administrador de base de datos de odoo
- db_host: donde esta el servidor de la base de datos
- db_macxonn: maximo de conecciones que puede tener la base de datos
- db_name: filtrar el nombre de la base de datos que queremos que se filtre, esto quiere decir que solo con esta se podra trabajar
- limit_memory_hard: la cantidad de memoria ram que se le da al aplicativo
- limit_memory_soft: la cantidad de memoria cache que se le da al aplicativo

- copiar el absolute path de nuestro archivo de configuracion
- editar la configuracion del ejecutable en pycharm: -c absolute_path(del archivo de configuracion)
- apartir de ahora se puede ejecutar normalmente odoo haciendo click en el boton de run

- para mayor visibilidad de las carpetas de linux y las carpetas padres es recomendable instalar tree, con el comando:
	-sudo apt install tree

- Hay mucha documentacion en odoo, basta con buscar odoo docs en google, seleccionar la version que desea, buscar el guidelines o la seccion en la que tiene duda o quiere saber mas

-- GIT CON ODOO

- configurar github:

	-git config --global user.name "Tu nombre"
	-git config --global user.email "tu correo de github"

- configurat el ssh:
	-ssh-keygen -t rsa -C "your_email@example.com"

- abrir la terminal en home, endrar en la carpeta ocula .ssh, cd .ssh y visualizar el archivo:
	-cat id_rsa.pub
	- copiamos el texto que se nos presenta en la terminal

- abrir github en el navegador
-settings
- ssh and gpc key, 
- crear una nueva ssh
-pegar el texto copiado anteriormente

-Buscar en google, odoo docs
-seleccionar la version deseada
-developers
-guidelines
-git. en esta seccion se le mostrara como se seben hacer los commits

-- PULL REQUEST

- indica qu esta en progreso, esperando a que s eevalue para ver si se le puede hacer un merge ya, la descripcion de estos deben ser especificas sobre lo que se intenta lograr