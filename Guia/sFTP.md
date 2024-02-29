<!-- Title -->

<p align="center">
  <h2 align="center">sFTP</h2>
  <h1 align="center"><img src="https://cdn-icons-png.flaticon.com/512/8110/8110738.png" alt="Imagem BitDefender" width="120">

  # Trânsferencia de arquivos
  Nos tempos atuais, a trânsferencia de arquivos é completamente útil no mundo empresarial, o uso do método de trânferencia de arquivos é muito necessário, para que, multiusuários tenham acesso as mesmas informações de diferentes locais.

  Para realizar estas trânferencias, nós resolvemos criar um servidor próprio com o uso do protocolo sFTP, que conta com uma proteção maior na hora de transferir os arquivos, internamente ou externamente.

  Mas antes de entendermos como funciona o protocolo sFTP, devemos entender como funciona o protocolo que originou o sFTP, precisamos entender como funciona e como surgiu o protocolo FTP. 

  ## O que é FTP?
  Desenvolvido em 1971 pelo estudante de engenharia elétrica Abhay Bhushan, o File Transfer Protocol (FTP), é um tipo de mensageiro, ou seja, ele transporta arquivos entre computadores pela internet. 

  O FTP é baseado no TCP, mas é anterior à pilha de protocolos TCP/IP, sendo posteriormente adaptado a este. É o padrão da pilha para transferir arquivos.

  O protocolo é especificado na RFC 959, podemos acessar o resumo neste link [resumo](https://pt.wikipedia.org/wiki/Protocolo_de_Transfer%C3%AAncia_de_Arquivos#Vis%C3%A3o_geral_do_protocolo) 

  ## Como funciona o FTP?
  A conexão FTP precisa de duas partes para estabelecer e se comunicar na rede. Para fazer isso, os usuários precisam de obter permissão ao fornecer as credenciais para o servidor FTP.

  Qualquer computador pode ser usado como um servidor FTP, conquanto hoje em dia seja mais usado por administrador de sites, que usam a conexão e um sistema de hospedagem para manter os dados de suas páginas.

  Seu principal papel é fazer o transporte de arquivos entre servidores locais, mas ele também troca correspondências entre a internet e as redes domésticas.

  ## O protocolo é seguro?
  O FTP tem aproximadamente 50 anos e, por isso, não conta com diversos padrões de seguranças que temos hoje em dia, e por isso foi necessário adicionar métodos de proteção para as trânsferencias de arquivos, como o protocolo sFTP.

  # O que é sFTP?
  O sFTP é um protocolo de transferência de arquivos que aproveita um conjunto de utilitários que fornecem acesso seguro a um computador remoto para fornecer comunicações seguras. É considerado por muitos como o método ideal para transferência segura de arquivos. Ele aproveita o [SSH](Dicionário.md) (Secure Shell) e é frequentemente também chamado de 'Secure Shell File Transfer Protocol'
  ## Como surgiu?
  O FTP seguro surgiu para atender às necessidades de segurança reforçada com túneis. Ele usa o [Secure Shell 2 (SSH2)](Dicionário.md), um protocolo de tunelamento seguro, para emular uma conexão FTP e fornece um canal amigável e criptografado para transferências de arquivos usando o conhecido Porta TCP 22.

  ## Segurança SSH
  O SSH oferece segurança aprimorada, tendo toda a sessão de transferência de arquivos, incluindo todos os comandos de controle de sessão, totalmente criptografados em todos os momentos, exigindo  apenas que uma única porta seja aberta em seu firewall versus as duas portas que precisam a ser aberto para conexões FTP e SSL.

  Como recurso adicional, o Secure FTP também comprime todos os dados durante a transmissão, o que pode resultar em transferências mais rápidas de arquivos. Além disso, permite a padronização de TI entre plataformas, o que garante uma aplicação consistente e forte da política de segurança e administração mais simples.

  # Servidor sFTP
  O servidor sFTP como dito anteriormente, pode ser criado em qualquer computador que tenha acesso à internet. E para criar este servidor podemos 

  #