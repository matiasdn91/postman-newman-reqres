<p align="center">
  <a href="https://www.linkedin.com/in/matias-damian-nazadek/"><img src="https://img.shields.io/badge/Matias%20Nazadek-LinkedIn-informational" style="max-height: 300px;" style="max-height: 300px;"></a>
</p>

<a href="https://www.postman.com/"><img src="https://miro.medium.com/max/1400/1*B8wqVr1Yd5COhcTXdKIv-Q.png" /></a><br />

## [Postman](https://www.postman.com/) Collection ejecutada con [Newman](https://www.npmjs.com/package/newman) via [Github Actions](https://docs.github.com/es/actions) 

### Sobre el proyecto

En este repositorio creo una Collection en Postman, ejecuto los Tests con Newman y configuro un Workflow en Github Actions para correrlos de forma automática, generando un Test Report y almacenando los datos como Artifacts del flujo de trabajo para descargarlo.

#### Website under test
Voy a usar https://reqres.in/ como sitio web de pruebas API. Esta página tiene una explicación detallada de cada endpoint, request y expected response para cada solicitud.

- Podes descargar el repositorio para  las pruebas o clonarlo:
```bash
git clone https://github.com/matiasdn91/postman-reqres.git
```

#### Requisitos previos

- Tener instalado [Node.js](https://nodejs.org/es/download/)
- Tener instalado [Newman](https://www.npmjs.com/package/newman) de manera global.

#### Algunas consideraciones
Para ejecutar tus propias pruebas es necesario exportar las Collections y Environments de tu Workspace en Postman como archivos .json, importar ambos a la carpeta Source del directorio y modificar el código del archivo Main.yml reemplazando los datos:

```
- name: Run Postman Collection        
        run: | 
         newman run source/yourCollection.json -e source/yourEnvironment.postman_environment.json --suppress-exit-code -r htmlextra --reporter-htmlextra-export testArtifacts/htmlreport.html 

```
#### Conclusión
Una vez que usemos el evento Push, las pruebas se ejecutarán de forma automática en la pestaña Actions y al finalizar se podrá descargar el dashboard del Test Report en formato HTML interactivo como Artifact.
