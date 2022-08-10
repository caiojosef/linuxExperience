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