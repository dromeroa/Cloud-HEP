# Proyecto Cloud-HEP - Jets
## Descripción del proyecto

Este proyecto tiene los siguientes objetivos:
- Desarrollar un framework para acceder y procesar los datos abiertos de CMS.
- Implementar un código utilizando machine learning para mejorar la identificación de jets. 

## Acerca del README
Este documento tiene como objetivo proporcionar soporte y detallar los procedimientos clave necesarios para configurar una estructura computacional capaz de procesar los datos abiertos de la colaboración CMS. Muchos de estos procedimientos están basados en las guías y recomendaciones proporcionadas por CMS, y su efectividad ha sido comprobada siguiendo el enfoque descrito en este documento.


## Índice
- [Instalación-Linux](https://github.com/dromeroa/Cloud-HEP/blob/main/README.md#instalaci%C3%B3n-linux)
- [Instalación-Docker](https://github.com/dromeroa/Cloud-HEP/blob/main/README.md#instalaci%C3%B3n-docker)
- [Como acceder a los datos abiertos de CMS](https://github.com/dromeroa/Cloud-HEP/blob/main/README.md#como-acceder-a-los-datos-abiertos-de-cms)
- [Como procesarlos datos abiertos de CMS](https://github.com/dromeroa/Cloud-HEP/blob/main/README.md#como-procesarlos-datos-abiertos-de-cms)
- [Como instalar el Physics Objects Extractor](https://github.com/cms-opendata-analyses/PhysObjectExtractorTool/tree/master/PhysObjectExtractor)
- [Como iniciar el procesamiento](https://github.com/dromeroa/Cloud-HEP/blob/main/README.md#como-iniciar-el-procesamiento)
  

- ## Instalación-Linux
1. Instalar Linux Mint 22 (wilma)
   ```bash
   https://linuxmint.com/
   ```
2. Copiar la imagen ISO a un usb y arrancar el boot desde el usb
   ```bash
   https://www.youtube.com/watch?v=jTMee8dYiUw
   ```
3. Tener cuidado en caso va a instalar a un nuevo disco duro o a un disco que ya tiene windows, para hacer correctamente las particiones.
   
- ## Instalación-Docker
1. ¿Qué es Docker?
   ```bash
   https://cms-opendata-workshop.github.io/workshop2024-lesson-docker/instructor/introduction.html
   ```
3. Instalar Docker
   ```bash
   sudo apt update
   sudo apt install docker-ce
   ```

##  Para ver diferentes contenedores

sudo docker ps -a


- ## Como acceder a los datos abiertos de CMS
1. Acceder a la página
   ```bash
   http://opendata.cern.ch/
   ```

2. Buscar algun dataset, como por ejemplo uno perteneciente al Run II, del año 2015 en el formato MiniAOD con quarks TT a 13 TeV
   ```bash
   RunIIFall15MiniAODv2/TT_TuneCUETP8M1_13TeV
   ```

3. Ingresar al dataset

4. Ir a File Indexes
   
5. Listar los archivos
   
6. Desacargar el archivo root
   


- ## Como procesarlos datos abiertos de CMS

Para poder procesar los datos es necesario instalar el programa CMSSW en la computadora. El software CMS (CMSSW) es una colección de bibliotecas de software que el experimento CMS utiliza para adquirir, producir, procesar e incluso analizar sus datos. El programa está escrito en C++, pero su configuración se manipula utilizando el lenguaje Python. Para mas información acerca del programa y como instalarlo se recomienda ver el ejercicio del workshop 

      https://cms-opendata-workshop.github.io/workshop2023-lesson-cmssw/


Algunas cuestiones generales:

1. Crear la carpeta con el nombre del release
2. Por ejemplo:
      ```bash
   mkdir CMSSW_5_3_32
   ```
3. Crear el contenedor:
```bash
sudo docker run -it --name my_od_5_3_32--net=host --env="DISPLAY" -v $HOME/.Xauthority:/home/cmsusr/.Xauthority:rw  -v ${HOME}cms_open_data_work:/code cmsopendata/cmssw_5_3_32-slc6_amd64_gcc472 /bin/bash
```   

- ## Como instalar el Physics Objects Extractor (PhysObjectExtractor)
  Usar esta página de referencia para instalar el paquete de PhysObjectExtractor para procesar los datos de CMS (Open data), seguir las instrucciones
   ```bash
   https://github.com/cms-opendata-analyses/PhysObjectExtractorTool/tree/master/PhysObjectExtractor
   ```

- ## Como iniciar el procesamiento
Una vez instalado el CMSSW_XXX, donde la version XXX debe estar alineada con los datos que se piensan procesar. Ingresamos a la carpeta del CMSSW:  
```bash
cd CMSSW_7_6_7/src
```
Inicializamos Docker
```bash
sudo docker start -i my_od
```
Ingresamos al Physics Object
```bash
cd PhysObjectExtractorTool/PhysObjectExtractor/
```
Entramos al source
```bash
cd src
```
Configuramos el entorno de trabajo
```bash
cmsenv
```
El siguiente paso es identificar un Analyzer para trabajar, esto depende de cual es el tipo de objeto que se quiere analizar, por ejemplo si queremos analizar jets podemos usar:
```bash
JetAnalyzer.cc 
```
Analizar el contenido del archivo y las colecciones usando el programa "VI"
```bash
vi JetAnalyzer.cc 
```
Salir del src e ingresar a la carpeta "python". Aqui se debe copiar los datos (en archivo root) que vamos a procesar. Analizar con cuidado el archivo: "poet_cfg.py".
Este es el archivo de configuracion que vamos a usar para procesar los datos. Una vez que este archivo este con las opciones deseadas, hacemos
```bash
cmsRun poet_cfg.py
```
---


# Pasos para crear un Analyzer

Tener una instalación funcional de CMSSW (por ejemplo CMSSW__6_7_7

Tener configurado el entorno con:

```bash
cmsenv
```

```bash
cd $CMSSW_BASE/src
cmsenv
scram b
mkdir MyAnalyzer
cd MyAnalyzer 
```

Crear el Analyzer

```bash
mkedanlzr MyAnalyzer
```

- ## DATOS DE COLISION JETS

- ### JetHT primary dataset in NANOAOD format from RunH of 2016 (/JetHT/Run2016H-UL2016_MiniAODv2_NanoAODv9-v1/NANOAOD) 

https://opendata.cern.ch/record/30558

- ### Simulated dataset QCD_Pt_600to800_TuneCP5_13TeV_pythia8 in NANOAODSIM format for 2016 collision data

https://opendata.cern.ch/record/63230

- ### Bulk Graviton (Simulated dataset BulkGravToWWToWhadWhad_narrow_M-1600_TuneCP5_13TeV-madgraph-pythia in NANOAODSIM format for 2016 collision data)
http://opendata.cern.ch/record/33699



- ## Para entrar al entorno conda donde esta el tensorflow que funciona

  conda activate tf

  jupyter notebook

  conda deactivate




## Para copiar archivos del servidor a mi PC

Como copiar archivos:

Entrar al sftp:

```bash
sftp -i /home/david/openssh_hep1.ppk ubuntu@10.0.2.14

como copiar archivos:

Vas a la carpeta donde se encuentra el archivo y haces:

```bash
put tau21.pdf 



**Referencias**
   
- ## CMS Open Data
  Página de referencia para utilizar el código CMS con Open data
  
   ```bash
   https://cms-opendata-guide.web.cern.ch/

- ## CMS Open Data workshops
  Página de referencia para revisar los workshop de CMS Open data
   ```bash
   https://cms-opendata-guide.web.cern.ch/cmsOpenData/workshops/
