# Servicio Web con Balanceador de Carga 
Despliegue automatizado con Ansible de un servicio web con balanceador de carga (HAProxy alojado en Docker) y múltples nodos.

## Tabla de Contenidos

- [Descripción](#descripción)
- [Características](#características)
- [Requisitos](#requisitos)
- [Adaptación](#adaptación)
- [Instalación](#instalación)

## Descripción
Este proyecto automatiza el despliegue de un servicio web con múltiples nodos servidores web físicos y un balanceador de carga (Haproxy) alojado en Docker, permitiendo además del balanceo de carga un servicio altamente disponible. 

## Características

- Instalación y configuración automatizada con Ansible
- Balanceador HAProxy corriendo en Docker
- Soporte para múltiples nodos backend configurables
- Fácil adaptación a distintos entornos y nodos
- Servicio altamente escalable

## Requisitos

- Ansible versión 2.17 o superior
- Docker instalado y funcionando en el nodo donde se desplegará HAProxy
- Acceso SSH configurado y permisos necesarios para Ansible en todos los nodos. Se recomienda el uso de autentificación con par de claves para evitar indicar los usuarios y contraseñas de los nodos en texto plano en el fichero de inventario.

## Adaptación
- Modifica el archivo `intentory/hosts.ini` para definir los nodos backend (grupo servidores) y el nodo balanceador (grupo balanceadores).
- El despliegue está diseñado para que solo sea necesario indicar los nodos clientes en el fichero de inventario. No es necesario modificar ningún otro fichero para que el despliegue diseñado funcione, pero sientete con libertad de modificarlo según tus necesidades. 

## Instalación

Clona este repositorio y ejecuta el playbook con el fichero de inventario personalizado según tu topología:

```bash
git clone https://github.com/antonioleonsilva/ansible-servicioWebBalanceado.git
cd ansible-servicioWebBalanceado
ansible-playbook -i inventory/hosts.ini main.yaml
