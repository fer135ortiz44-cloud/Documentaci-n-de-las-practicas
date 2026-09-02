# Práctica: Despliegue de Infraestructura y Servidor Web

En este repositorio se documenta la práctica realizada para la creación de infraestructura de red y el despliegue de un servidor web utilizando Microsoft Azure y Ubuntu Server.

1. Creación de la Infraestructura
Durante la práctica, se configuraron los siguientes elementos fundamentales en la nube:

 Grupo de Recursos: Se creó un grupo para contener y administrar todos los recursos de esta práctica.
 <img width="960" height="908" alt="image" src="https://github.com/user-attachments/assets/c5c25e8f-dec9-45e9-a003-e1766afbd594" />

  Redes Virtuales:
  * Se configuró una red virtual principal (**VNet**) llamada: `vnet-itil`.
    <img width="864" height="919" alt="image" src="https://github.com/user-attachments/assets/db2c5699-7da0-43c2-88d0-80d52650a47f" />

  * Dentro de la VNet, se creó una subred (**Subnet**) llamada: `subnet-itil`.
    <img width="1557" height="1023" alt="image" src="https://github.com/user-attachments/assets/1ee219c4-2acc-4a7b-867a-34a724c568c5" />


2. Especificaciones de la Máquina Virtual (VM)
Se desplegó una máquina virtual sin redundancia de infraestructura con las siguientes características:
Imagen del SO:** Ubuntu Server 24.04 LTS
Arquitectura:** x64
Tamaño: Opciones entre B1s, B2s, B1ms o D2s_v5 (1–2 vCPU, 1–4 GB RAM).
Disco del SO:** Standard SSD
Autenticación:** SSH public key
Usuario: `itiladmin`
IP: Se le asignó una IP Pública.
  <img width="1866" height="868" alt="image" src="https://github.com/user-attachments/assets/bdacf99c-16b5-44e5-9bcd-d99a62da2d6e" />


Reglas de Red (Networking)
Se habilitaron los siguientes puertos de entrada (Inbound ports):
Puerto 22 (TCP):** Para permitir la conexión por SSH.
Puerto 80 (TCP):** Para permitir tráfico HTTP desde Internet.

---

3. Comandos Ejecutados en el Servidor

Una vez creada la infraestructura, nos conectamos a la máquina virtual vía SSH y ejecutamos los siguientes pasos:

### Actualización del sistema
```bash
sudo apt update
sudo apt upgrade -y
```
<img width="1119" height="1205" alt="image" src="https://github.com/user-attachments/assets/9f45026a-4420-4658-be49-b7f0e0a3590e" />
<img width="1275" height="911" alt="image" src="https://github.com/user-attachments/assets/ac03a079-e6ee-4d00-ae7d-95ee1363da10" />

Para asegurar que el servidor arranque y comprobar su estado:

Bash
sudo systemctl enable apache2
sudo systemctl start apache2
sudo systemctl status apache2  # Debe mostrar "active (running)"
Pruebas de funcionamiento
Prueba local dentro de la máquina:

Bash
curl http://localhost
