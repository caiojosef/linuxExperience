# Aqui contém todos os comandos utilizados no bootcamp Linux Experience pela Digital Innovation One!

## Gerenciando Usuários no Linux
    Criando e excluindo usuários:
        - useradd nomedousuário
        - useradd nomedousuário -c "Comentário"
        - useradd nomedousuário -c "Comentário" -m (criar pasta no diretório home)
        - useradd nomedousuário -m (criar diretório) -c "COMENTÀRIO" -s /bin/bash (dar acesso ao shell)

        - userdel -f (force) nomedousuário
        - userdel -r -f (remove, force)
  
        - passwd nomedousuário (inserir senha ao usuário) 
        - chsh -s /bin/bash nomedousuário (dar acesso ao shell para o user)

    Editando informações do usuário
        - useradd nomedousuario -c "comentário" -m -e data 00/00/0000 (data de expiração, após essa data o usuário não ira ter mais acesso)
  
        -usermod (faz alterações no usuário) nomedousuário -s /bin/bash (acesso ao console)

        -passwd nomedousuario -e (usuário terá que alterar a senha, caso coloque uma data futura, a partir da data o usuário terá que trocar a senha)

        -cat /etc/passwd (cat é usado para ler um arquivo e aqui está verificando os usuários que estão cadastrados)
        (não é aconselhável editar esse arquivo, use o usermod para alterar as informações do usuário)

    Shell Script - Criando Usuários em lote
        - useradd nome do usuário -c "Comentário" -s /bin/bash -m -p $(openssl passwd -crypt senha)

        - nano criar_user.sh (nano é usado para ler um arquivo e no caso foi criado um script)

    CRIANDO O SCRIPT
        #!/bin/bash

        echo "Início do Script"
        useradd nomedouser -c "comentario" -s /bin/bash -m -p $(openssl passwd -crypt senha)   
        echo "Finalizando o script"

    COMANDO PARA DAR PERMISSÃO PARA EXECUÇÃO DO ARQUIVO

        chmode +x nomedoArquivo
        ./nomeDoArquivo (comando para executar o script)

    Adicionando usuários a grupos
        - cat /etc/group (verificar os grupos de usuários)
        - usermod -G (G maiúsculo indica que pode adicionar em vários grupos, minúsculo em apenas um grupo) adm,sudo (nomedos grupos) nomedouser

    Criando Novos Grupos
        - groupadd nomedogrupo (criar o grupo)
        - groupdel nomedogrupo (exclui grupo vazio)
        - cat/etc/group 
        - useradd nomedouser -c "comentário" -m -s /bin/bash -p $(openssl passwd -crypt senha) -G nomedogrupo
        - usermod -G nomedogrupo (atribuir usuário já criado em um grupo)
        - usermod -G nomedogrupo nomedousuário
        (sai de todos os grupos que estava e entra para o que foi destinado)
        - gpasswd -d username nomedogrupo (remove o usuário de somente 1 grupo)

    Conhecendo o Sistema de Permissões
        - ls -l (exibe as permissões)
        
        R W X (DONO)
        R W X (GRUPO) 
        R W X (OUTROS)
        R - READ
        W - WRITE
        X - EXECUTE

        Alterando as permissões de um diretório-arquivo
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

        Entendendo melhor as permissões de execução para scripts
        - nano date.sh
    
    #!/bin/bash
    echo "mensagem"
    date

        - chmod 744 date.sh (dando permissão, dono leitura, gravação e execução. Grupo leitura e demais somente leitura)

        - chmode 644 date.sh (removendo permissões)

        - chmod +x date.sh (dando permissão para o dono)
        - chmod -x date.sh (remove permissão para o dono)
  
  ## Gerenciamento de pacotes Linux
    Gerenciamento de pacotes (UBUNTU-DEBIAN)
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


        







    