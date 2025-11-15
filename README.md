# Minitaller: Zephyr OS

## Prerequisitos de Compilación

### Instalar Podman
Instalar el contenedor Podman desde el [sitio oficial de Podman](https://podman.io/docs/installation)


### Preparación del Contenedor

**Crear entorno compartido entre host y contenedor**

```bash
mkdir -p ~/tools/zephyrproject
```
***Asignar permisos de la carpeta compartida entre el contenedor y el host***

```bash
podman unshare chown -R 1000:1000 \
~/tools/zephyrproject
```
**Iniciar contenedor desde el host**

```bash
podman run -it --name zephyr-dev \
  -v ~/tools/zephyrproject:/workdir:Z \
  --entrypoint /bin/bash \
  ghcr.io/zephyrproject-rtos/zephyr-build:v0.26-branch
```
### Configuración del Entorno Zephyr

Dentro del contenedor:
```bash
west init .
west update
pip install jsonschema
```
