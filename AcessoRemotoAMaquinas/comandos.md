## Acesso Remoto a Máquinas Linux

### Acesso Remoto Via Linux
    - ssh nomedeuser@ip

### Acesso Remoto Via Linux em máquina virtual AWS
    - sudo chmode 600 nomedoarquivo.pem (dando permissão para o arquivo)
    - ssh -i nomedoarquivo.pem nomedouser@ip (conectando na máquina com a chave gerada na AWS)