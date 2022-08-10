## Servidores de Arquivos com Linux

### Instalação do SAMBA e configuração inicial
    - apt install samba -y (instalar o samba e permitir tudo)
    - mkdir /disk2/publica
    - chmod 777 /disk2/publica
    - nano /etc/samba/smb.conf (realizar configurações do servidor)
    (map to guest = bad user, indica que não possui restrição)
    acrescentar no final o nome do compartilhamento
    [nomedocompartilhamento]
    path = /disk2/publica
    writable = yes
    guest ok = yes
    guest only = yes

    - systemctl restart smbd (restartar o samba)
    - systemctl status smbd (verificar o status)
    - systemctl enable smbd (executar auto ao reiniciar o sistema)