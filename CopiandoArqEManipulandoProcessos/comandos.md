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