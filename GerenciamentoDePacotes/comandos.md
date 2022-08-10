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