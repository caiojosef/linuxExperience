# Aqui contém todos os comandos utilizados no bootcamp Linux Experience pela Digital Innovation One!

## Acesso Remoto a Máquinas Linux

### Acesso Remoto Via Linux
    - ssh nomedeuser@ip

### Acesso Remoto Via Linux em máquina virtual AWS
    - sudo chmode 600 nomedoarquivo.pem (dando permissão para o arquivo)
    - ssh -i nomedoarquivo.pem nomedouser@ip (conectando na máquina com a chave gerada na AWS)

## Manipulando Arquivos no Linux

### Terminal Linux - Apresentação
    - date (mostra a data do sistema)
    - clear (limpa o terminal) ou ctrl + l

### Navegando pelo sistema de arquivos
    - pwd (verifica o diretório que o terminal se encontra)
    - cd (usado para mudar o diretório)
    - cd / (usado para ir para o diretório raiz)
    - cd ~ (pasta do usuário)
    - ls (listar todos os arquivos que estão no diretório)
    - cd .. (volta 1 diretório)
    - cd ../backups (volta 1 e entra no diretório backups)
    - cd /var/ + tab 2x (mostra o que está dentro do diretório)

### Filtrando a exibição de arquivos
    - ls | more (lista de rolagem quando a pasta possui muitos arquivos)
    - ls p (mostrar todos os arquivos que iniciam com a letra P)
    - ls p* (mostra diretórios com a letra P e o que possui dentro)
    - ls ss* (mostra arquivos com início SS e o resto pode ser qualquer caracter)
    - ls m?g* (procura por arquivos com começo de letra M, segunda letra pode ser qualquer uma, terceira é um G e a quarta * Pode ser qualquer uma)
    - touch arquivo1.txt (cria um arquivo)

### Localizando Arquivos
    - ls /home/var/s* (lista dentro do diretório todos arquivos iniciados por S e o resto é qualquer coisa)
    - find -name arquivo* (procurar pelo parametro name)

### Crianndo diretórios
    - mkdir nomedapasta (criando pastas)

### Excluindo arquivos e diretórios
    - rmdir nomedapasta (exclui somente pastas vazias)
    - rm nomedoarq (exclui arquivos)
    - rm arquivo* (exclui todos os arquivos)
    - rm -rf nomedapasta (exclui a pasta e tudo que possui dentro)

### Obtendo Ajuda
    - ls --help (lista os argumentos que podem ser utilizados)
    - ls -l (lista os arquivos, proprietários, tamanho, permissões e etc)
    - ls -a (mostra os arquivos ocultos)

### Executando tarefas administrativas como root
    - cat etc/group (verifica os grupos)
    - sudo mkdir nomePasta (serve para realizar atividade de administrador)
    - sudo touch arquivo.txt (cria arquivo em modo adm)
    - sudo rm arquivo.txt (exclui em modo adm)

### Logando como usuários root
    - sudo passwd root (atribuir senha ao root)
    - su (serve para trocar para root)
    - su usuário (trocar para outro usuário)

### Liberando acesso remoto do usuário root
    - cat /etc/ssh/sshd_config 
    (Procurar a linha #PermitRootLogin prohibit-password)
    - sudo nano /etc/ssh/ssh_config
    (editar a linha acima para PermitRootLogin yes)
    Ctrl + O salva o arquivo / Ctrl + X Sair
    Dar o reboot na máquina para validar ou restartar o serviço.
    - systemctl status sshd (verifica o serviço)
    - sudo systemctl restart sshd (restarta o serviço)

### Trabalhando com arquivos de texto
    - vi nomedoarquivo.txt (se o arquivo não existir, ele cria)
    - nano nomedoarquivo.txt 

### Histórico de comandos
    - history (vai mostrar o histórico de comandos do usuário)
    - history 307 (executa a linha 307 dos comandos utilizados)
    - !?dat? (busca o comando)
    - history | grep "Planilhas" (busca padrões)
    - export HISTTIMEFORMAT = "%c" (busca por parâmetro)
    %d: DAY
    %m: Month
    %y: YEAR
    %H: Hour
    %M: Minutue
    %S: Minutes
    %F: Full date (Y-M-D format)
    %T: Time(H:M:S format)
    - history -c (apaga os comandos)
    - set +o history (desativa o history)
    - set -o history (ativa o history)
    - cat .bashrc (visualiza informações do history do user)
    - history -w (salva em arquivo os comandos do usuário)

## Gerenciando Usuários no Linux

### Criando e excluindo usuários:
    - useradd nomedousuário
    - useradd nomedousuário -c "Comentário"
    - useradd nomedousuário -c "Comentário" -m (criar pasta no diretório home)
    - useradd nomedousuário -m (criar diretório) -c "COMENTÀRIO" -s /bin/bash (dar acesso ao shell)

    - userdel -f (force) nomedousuário
    - userdel -r -f (remove, force)
  
    - passwd nomedousuário (inserir senha ao usuário) 
    - chsh -s /bin/bash nomedousuário (dar acesso ao shell para o user)
     

### Editando informações do usuário
    - useradd nomedousuario -c "comentário" -m -e data 00/00/0000 (data de expiração, após essa data o usuário não ira ter mais acesso)
  
    -usermod (faz alterações no usuário) nomedousuário -s /bin/bash (acesso ao console)

    -passwd nomedousuario -e (usuário terá que alterar a senha, caso coloque uma data futura, a partir da data o usuário terá que trocar a senha)

    -cat /etc/passwd (cat é usado para ler um arquivo e aqui está verificando os usuários que estão cadastrados)
    (não é aconselhável editar esse arquivo, use o usermod para alterar as informações do usuário)

### Shell Script - Criando Usuários em lote
    - useradd nome do usuário -c "Comentário" -s /bin/bash -m -p $(openssl passwd -crypt senha)

    - nano criar_user.sh (nano é usado para ler um arquivo e no caso foi criado um script)

    CRIANDO O SCRIPT
    #!/bin/bash

    echo "Início do Script"
    useradd nomedouser -c "comentario" -s /bin/bash -m -p $(openssl passwd -crypt senha)   
    echo "Finalizando o script"

### COMANDO PARA DAR PERMISSÃO PARA EXECUÇÃO DO ARQUIVO

    chmode +x nomedoArquivo
    ./nomeDoArquivo (comando para executar o script)

### Adicionando usuários a grupos
    - cat /etc/group (verificar os grupos de usuários)
    - usermod -G (G maiúsculo indica que pode adicionar em vários grupos, minúsculo em apenas um grupo) adm,sudo (nomedos grupos) nomedouser

### Criando Novos Grupos
    - groupadd nomedogrupo (criar o grupo)
    - groupdel nomedogrupo (exclui grupo vazio)
    - cat/etc/group 
    - useradd nomedouser -c "comentário" -m -s /bin/bash -p $(openssl passwd -crypt senha) -G nomedogrupo
    - usermod -G nomedogrupo (atribuir usuário já criado em um grupo)
    - usermod -G nomedogrupo nomedousuário
    (sai de todos os grupos que estava e entra para o que foi destinado)
    - gpasswd -d username nomedogrupo (remove o usuário de somente 1 grupo)

### Conhecendo o Sistema de Permissões
    - ls -l (exibe as permissões)
        
    R W X (DONO)
    R W X (GRUPO) 
    R W X (OUTROS)
    R - READ
    W - WRITE
    X - EXECUTE

### Alterando as permissões de um diretório-arquivo
    - mkdir /adm (criando diretório)
    - chown usuario:grupoDeUsers /adm
    (alterando o dono da pasta e atribuindo o grupo para acesso)

    LEITURA 4
    GRAVAÇÃO 2
    EXECUÇÃO 1
    NENHUMA 0

    - chmod 750 /adm (altera os acessos de leitura, gravação e execução. Dono, pasta e outros)
    - chown nomeUser:nomeGrupo nome do arquivo
    (esse comando irá dar o dono da pasta/arquivo para o user destinado, o grupo terá permissão para acessar, ler e executar)

### Entendendo melhor as permissões de execução para scripts
    - nano date.sh
    
    #!/bin/bash
    echo "mensagem"
    date

    - chmod 744 date.sh (dando permissão, dono leitura, gravação e execução. Grupo leitura e demais somente leitura)

    - chmode 644 date.sh (removendo permissões)

    - chmod +x date.sh (dando permissão para o dono)
    - chmod -x date.sh (remove permissão para o dono)
  
## Gerenciamento de pacotes Linux

### Gerenciamento de pacotes (UBUNTU-DEBIAN)
    - apt-get (mais antigo, menos amigável)
    - apt (mais atual, mais amigável)
    - apt list (lista os arquivos disponíveis)
    - apt list --installed (lista os arquivos disponíveis na máquina)
    - apt list --upgradeable (lista de coisas que estão disponíveis para upgrade)
    - apt search nomedoprograma (procura arquivos similares com o nome do programa)
    - apt search net-tools (verifica se está instalado, como não está) 
    - apt install net-tools (instala o programa) 
    - apt remove net-tools
    - wget (software para download)
    - wget linkdoGitHub (download)
    - apt install unzip
    - unzip nomedoarquivo
    - apt install unrar
    - unrar nomedoarquivo
    - apt edit-sources (links de repositórios oficiais ubuntu)

### Atualização do sistema operacional
    - apt update (checar para ver se tem atualizações)
    - apt list --upgradable (verificar o que será atualizado)
    - apt upgrade (inicia a atualização)

### Instalação de pacotes no ambiente Desktop
    - sudo apt install vlc

### Gerenciamento de pacotes (FEDORA RED HAT CenTOS)
    - dnf --help
    - yum --help
    - dnf search net-tools
    - dnf install net-tools -y
    - dnf remove net-tools -y
    - yum install httpd
    - dnf update (procura e instala as atualizações)

### Realizando a instalação de arquivos DEB
    - sudo apt install ./nomedoarquivo 
  
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

## Copiando Arquivos e Manipulando Processos

### Copiando arquivos
    - cp --help
    - cp diretório /home/caiojosef/nomedoarquivo.extensão /disk2 e o lugar que será direcionado!
    - cp /home/caiojosef/*.txt todos os arquivos com extensão txt /disk2
    - cp ./a* copiando todos os arquivos com o letra A e todas as extensões /disk2
    - cp /home/caiojosef/* /disk2/ -i (pergunta para confirmar a cópia e se deseja sobrepor)
    - cp /home/caiojosef/* /disk2/ -r (cópia recursiva)
    - cp /home/caiojosef/* /disk2/ -r -v (visualiza tudo que foi feito)

### Renomeando Movendo arquivos
    - mv /home/caiojosef/arquivo.extensão e o lugar vai mover o arquivo /disk2/
    - mv -v (visualiza o que está sendo feito)
    - mv -i (perguntar se deseja sobrepor, caso tenha um arquivo com o mesmo nome)
    - mv nomeatualdoarq.extensão novonomedoarq.extensão (serve para renomear, ex: mv bancodedados.txt banco_de_dados.txt)

### Iniciando, visualizando e encerrando um processo
    - ps (ver os processos, referente ao usuário atual)
    - ps aux (A = mostra o processo de todos os usuários, U = mostra o usário, X = processos executados fora do console)
    - kill PIN
    - killall chrome 
    - w (mostra quem está logado no momento)
    - who -a (mostra o pin de quem está logado)
    - kill PIN (derruba o usuário)
