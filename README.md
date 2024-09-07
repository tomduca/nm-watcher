# nm-watcher

Network monitor to restart network interface whenever it hangs. Built to avoind loosing access to headless Proxmox Virtual Serverevery time the network adapter stops responding.
- Download nm-watcher file

- Create a service file into /etc/systemd/system/
    ```
  sudo nano /etc/systemd/system/nm-watcher.service
    ```
- Put this into the new service file:
  ```
  [Unit]
  Description=Network Monitor Service
  After=network.target

  [Service]
  ExecStart=/path/to/your/nm-watcher
  Restart=always
  User=root

  [Install]
  WantedBy=multi-user.target
    ```
- Enable and start new service:
    ```
  sudo systemctl daemon-reload
  sudo systemctl enable network-monitor.service
  sudo systemctl start network-monitor.service
    ```
- Validate services is working ok:
    ```
  sudo systemctl status network-monitor.service
    ```
