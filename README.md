# Proyecto Cloud-HEP
## Descripción del proyecto

Este proyecto tiene los siguientes objetivos:
- Desarrollar un framework para acceder y procesar los datos abiertos de CMS.
- Implementar un código utilizando machine learning para mejorar la identificación de jets. 

## Acerca del README
Este documento tiene como objetivo proporcionar soporte y detallar los procedimientos clave necesarios para configurar una estructura computacional capaz de procesar los datos abiertos de la colaboración CMS. Muchos de estos procedimientos están basados en las guías y recomendaciones proporcionadas por CMS, y su efectividad ha sido comprobada siguiendo el enfoque descrito en este documento.


## Índice
- [Instalación-Linux](#instalaciónlinux)
- [Instalación-Docker](#instalaciónDocker)
- [CMS Open Data](#CMSOpenData)
- [Uso](#uso)
- [Contribución](#contribución)
- [Licencia](#licencia)



- ## Instalación Linux
1. Instalar Linux Mint 22 (wilma)
   ```bash
   https://linuxmint.com/
2. Copiar la imagen ISO a un usb y arrancar el boot desde el usb
   ```bash
   https://www.youtube.com/watch?v=jTMee8dYiUw
3. Tener cuidado en caso va a instalar a un nuevo disco duro o a un disco que ya tiene windows, para hacer correctamente las particiones.
   
- ## Instalación Docker
1. ¿Qué es Docker?
   ```bash
   https://cms-opendata-workshop.github.io/workshop2024-lesson-docker/instructor/introduction.html
3. Instalar Docker
   ```bash
   sudo apt update
   sudo apt install docker-ce

- ## Como acceder a los datos abiertos de CMS
1. Acceder a la página
   ```bash
   http://opendata.cern.ch/

2. Buscar algun dataset, como por ejemplo uno perteneciente al Run II, del año 2015 en el formato MiniAOD con quarks TT a 13 TeV
   ```bash
   RunIIFall15MiniAODv2/TT_TuneCUETP8M1_13TeV

3. Ingresar al dataset

4. Ir a File Indexes
   
5. Listar los archivos
   
6. Desacargar el archivo root


- ## Como procesarlos datos abiertos de CMS
Para poder procesar los datos es necesario instalar el programa CMSSW en la computadora. El software CMS (CMSSW) es una colección de bibliotecas de software que el experimento CMS utiliza para adquirir, producir, procesar e incluso analizar sus datos. El programa está escrito en C++, pero su configuración se manipula utilizando el lenguaje Python. Para mas información acerca del programa y como instalarlo se recomienda ver el ejercicio del workshop: 
   ```bash
   https://cms-opendata-workshop.github.io/workshop2023-lesson-cmssw/
   

- ## Physics Objects Extractor (PhysObjectExtractor)
  Usar esta página de referencia para instalar el paquete de PhysObjectExtractor para procesar los datos de CMS (Open data), seguir las instrucciones
   ```bash
   [https://cms-opendata-guide.web.cern.ch/cmsOpenData/workshops/](https://github.com/cms-opendata-analyses/PhysObjectExtractorTool/tree/master/PhysObjectExtractor)


Referencias
   
- ## CMS Open Data
  Página de referencia para utilizar el código CMS con Open data 
   ```bash
   https://cms-opendata-guide.web.cern.ch/

- ## CMS Open Data workshops
  Página de referencia para revisar los workshop de CMS Open data
   ```bash
   https://cms-opendata-guide.web.cern.ch/cmsOpenData/workshops/
