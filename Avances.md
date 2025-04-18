# Avances diarios del proyecto

## Miércoles 16 de Abril del 2025

1. Para buscar en el Open data Web page, ponemos:(Segun Metodiev)
   
   jet primary dataset

3. Aqui hay varios datasets, ellos usan
   
   CMS 2011A Jet Primary Dataset (+ Simulation)

5. Pedir a André que busque todos los posibles datasets, que los clasifique y que vea con cual version del CMSSW funcionan.

6. El grupo del MIT tiene ya los datasets procesados, ver si podemos acceder a ellos.

   Los datasets se encuentran en (aqui se listan las caracteristicas que han aplicado en el pre-procesamiento de los jets):

https://zenodo.org/records/3340205#.Xh4UeEdKgzM

   A dataset of 1,785,625 jets from the Jet Primary Dataset of the CMS 2011A Open Data reprocessed into the MOD HDF5 format. Jets are    selected from the hardest two anti-kT R=0.5 jets in events passing the Jet300 High Level Trigger and are required to have $pT_{jet} > 375 GeV$, where where $pT_{jet}$ includes a jet energy correction factor. Particle Flow Candidates (PFCs) for each jet are provided and include information about the PFC kinematics, PDG ID, and vertex. Additionally, jets have metadata describing their kinematics and provenance in the original CMS AOD files.

For additional details about the dataset, please see the accompanying paper: Exploring the Space of Jets with CMS Open Data. There, jets were further restricted to have to ensure tracking coverage and have "medium" quality to reject fake jets.

El procesamiento lo realizan con su paquete de Python:

https://hub.2i2c.mybinder.org/user/pkomiske-energyflow-1swtgcaw/notebooks/demos/MOD%20Jet%20Demo.ipynb

Con el Git-Hub relacionado:

https://github.com/pkomiske/MOD


## Jueves 17 de Abril del 2025

1. Vamos a probar el dataset utilizado por Metodiev
   Jet primary dataset in AOD format from RunA of 2011 (/Jet/Run2011A-12Oct2013-v1/AOD)
   * Tener cuidado, estos datasets estan ya estan pre procesados, son RECO (This primary AOD dataset was processed from the RAW dataset by the following step:RECO) y si se pueden usar directamente en los analisis. Sin embargo los que son RAW, no se pueden usar directamente en los analisis, se deben procesar primero.
  
2. Estos datasets fueron generados con el CMSSW_5_3_32 por lo que debemos instalar esta version en nuestra area de trabajo.

3. Creamos la carpeta primero:

   ```bash
   mkdir CMSSW_5_3_32
   ```

4. Creamos el contenedor:
```bash
sudo docker run -it --name my_od_5_3_32--net=host --env="DISPLAY" -v $HOME/.Xauthority:/home/cmsusr/.Xauthority:rw  -v ${HOME}cms_open_data_work:/code cmsopendata/cmssw_5_3_32-slc6_amd64_gcc472 /bin/bash
```

Notar que hemos utilizado el my_od_5_3_32 para este caso para no utilizar el del otro release.


## Viernes 18 de Abril del 2025

1. Hemos notado que para poder identificar a los fatjets, es necesario usar los datasets que si tengan estas caracteristicas. Para esto necesitamos datasets a partir del 2015.(No podemos usar los de años inferiores)
2. Estoy probando con:
   /JetHT/Run2015D-16Dec2015-v1/MINIAOD
No estoy usando el AOD por ahora porque son muy pesados.
   

