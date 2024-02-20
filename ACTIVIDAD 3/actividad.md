<center>

|Nombre| Carnet|
|--|--|
|Andre Joaquin Ortega De Paz|201900597|

# ACTIVIDAD 3
</center>

## Crear un systemd unit
## Pasos de instalacion

1. Se crea un script en el cual se programara la funcionalidad del servicio. Lo guardaremos como saludo.sh
```
sudo nano /usr/local/bin/saludo.sh
```

2. Dentro del script le colocaremos un while para que se repita por siempre y un sleep para que se acive cada segundo
```
#!/bin/bash

while true
do
    echo "Hola, la fecha actual es: $(date)"
    sleep 1
done
```
3. Para que el script tenga presmisos ejecutamos lo siguiente
```
sudo chmod +x /usr/local/bin/saludo.sh
```

4. Se crea un archivo de systemd unit en la carpeta /etc/systemd/system/, nombrandolo 

```
sudo nano /etc/systemd/system/saludo_servicio.service
```

5. Para crear el servicio lo modificamos con los siguiente comandos guardando los cambios.

```
[Unit]
Description=Servicio de saludo

[Service]
ExecStart=/usr/local/bin/saludo_script.sh
Restart=always
User=<tu_usuario> #en mi caso es "mg"
```

6. Para actualizar los servicios e incluir el servicio creado utilizaremos lo siguiente:
```
sudo systemctl daemon-reload  
```

7. Para iniciar el servicio utilizaremos el siguiente comando
```
sudo systemctl start saludo_servicio.service
```

NOTA: Para validar que el servicio se esta ejecutando ejecutar el siguiente comando

```
sudo systemctl status saludo_servicio.service  
```