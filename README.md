# Ansible Playbooks

Repositorio con los Playbooks the Ansible para crear máquinas virtuales en ovirt y instalar los servicios (balanceador de carga, base de datos MongoDB y docker) en los hosts que se especifiquen en alguno de los archivos de inventario.

## Máquinas

## Variables

Se deben de modificar las siguientes variables en los siguientes archivos.

* `varOvejas.yml` : El archivo se encuentra encriptado, se puede modificar mediante el siguiente comando `ansible-vault edit varOvejas.yml`, la contraseña es `changeme`

* `group_vars/all.yml`: Modificar la variable `ssh_keys` con la clave SSH que se usa para acceder a las máquinas sin tener que pedir contraseña.

## USO

El playbook para la creación de máquinas virtuales se ejecutará de la siguiente manera:

```sh
ansible-playbook main.yml --ask-vault-pass
```

## Servicios 

### Variables

Se deben de modificar las siguientes variables en los siguientes archivos.

* `group_vars/all.yml`

```yaml
ansible_user: USER

docker_image_backend: BACKEND_IMAGE
frontend_container_port: FRONTEND_IMAGE
frontend_container_port: "PORT:PORT"
backend_container_port: "PORT:PORT"
frontend_server: FRONTEND_IP
backend_server: BACKEND_IP
frontend_port: PORT
backend_port: PORT
```

* `staging` o `production`: Añadir los hosts a cada grupo

### Uso

El playbook para la creación de máquinas virtuales se ejecutará de la siguiente manera:

```sh
ansible-playbook -i INVENTORY main.yml
```