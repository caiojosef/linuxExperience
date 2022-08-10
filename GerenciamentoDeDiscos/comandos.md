## Gerenciamento de Discos Linux

### Discos, sistemas de arquivos e partições
    Sistema de Arquivos
        MacOS - HfS
        Unix/Linux - Ext3, Ext4, XFS
        Windows - FAT32, NFTS
    
    Em cada partição do Windows é dada a letra A, B, C...
    No Linux cada disco recebe um nome indicado por sda, sdb, sdc...

### Adicionando um novo disco
    - lsblk (ver discos e partições)
    - fdisk -l (listar os discos)

### Particionando e formatando discos via terminal
    - fdisk /dev/sdb (indicar o local do disco)
    (m para ajuda) 
    (n adiciona uma nova partição)
    (p de primária)
    (colocar o número da partição, 1 no caso para primária)
    (enter 2x para prosseguir selecionando os default correspondentes)
    
    - mkfs.ext3 / mkfs.ext4 /mkfs.ntfs /dev/sdb

### Montando e desmontando discos
    - cd /mnt/
    - mkdir disco2 (criar pasta para montar o disco)
    - mount /dev/sdb /mnt/disco2/ (montando o disco e colocando o diretório)
    - cd disco2 (entrando na segunda partição)
    (todo arquivo salvo aqui, será salva na segunda partição)
    - umount /dev/sdb (desmonta o disco)
  
### Montando discos automaticamente
    - lsblk
    -  nano /etc/fstab
    acrescentar a linha com o diretório do disco, para aonde vai e o formato. Adicionar no final defaults 0 0 
    (/dev/sdb /disk2 ext4 defaults 0 0)