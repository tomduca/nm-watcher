# nm-watcher

Network monitor to restart network interface whenever it hangs. Built to avoind loosing access to headless Proxmox Virtual Serverevery time the network adapter stops responding.

- Primero, crea un archivo de servicio en el directorio /etc/systemd/system/
    ```
  sudo nano /etc/systemd/system/network-monitor.service
    ```
- Dentro del archivo, añade el siguiente contenido:
  ```
  [Unit]
  Description=Network Monitor Service
  After=network.target

  [Service]
  ExecStart=/path/to/your/script.sh
  Restart=always
  User=root

  [Install]
  WantedBy=multi-user.target
    ```
- Una vez que has creado y configurado el archivo del servicio, necesitas habilitarlo y arrancarlo:
    ```
  sudo systemctl daemon-reload
  sudo systemctl enable network-monitor.service
  sudo systemctl start network-monitor.service
    ```
- Puedes comprobar si el servicio está funcionando correctamente con:
    ```
  sudo systemctl status network-monitor.service
    ```
