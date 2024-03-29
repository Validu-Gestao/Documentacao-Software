<!-- Title -->

<p align="center">
  <h2 align="center">GLPI</h2>
  <h1 align="center"><img src="https://www.mindtek.com.br/wp-content/uploads/2022/08/f4f30f80-cd92-11e9-8301-1ad34bf00c41.png" alt="Imagem GLPI" width="150"></h1>

  # O que é o GLPI?
  GLPI é um termo aplicado a um serviço de gerenciamento de ativos de TI, um sistema onde podemos integrar um controle de incidências de chamados e ativos em um [service desk](Dicionário.md), o mesmo é baseado em [código aberto](Dicionário.md) e escrito em [PHP](Dicionário.md) atribuído ao [GNU](Dicionário.md) (General Public License). Todo mundo sabe da importância do [helpdesk](Dicionário.md) nas empresas, é uma área cujo objetivo é dar suporte ao usuário nas soluções de problemas relacionados à TI. É uma área que necessita de um tempo de resposta rápido e exige uma eficiência nos atendimentos. O GLPI veio para organizar, melhorar e agilizar esse processo dentro da área [helpdesk](Dicionário.md).

  ## Recursos GLPI
  O sistema GLPI oferece soluções eficientes para apoiar e atender as demandas específicas da sua empresa. Para isso ela dispões de algumas vantagens, a seguir iremos listar as principais vantagens do GLPI.

  1. Gestão de chamados:
  - A gestão de chamados permite a criação, edição e exclusão de chamados, além de permitir visualizar as informações de cada chamado.
  2. Gestão de usuários:
  - A gestão de usuários permite gerenciar os dados dos usuários da empresa, como nome, endereço, telefone e e-mail. Também é possível cadastrar novos usuários dentro do sistema.
  3. Relacionamento com usuário:
  - Este módulo garante a interação direta entre o suporte e o usuário, através do envio de mensagens personalizadas. Também é possível fazer uma ánalise dos chamados ativos e solucionados para indentificar problemas e soluções.
  4. Gestão financeira:
  - A gestão financeira permite que você gerencie as licenças de [software](Dicionário.md), os orçamentos, fornecedores, contratos. Além de permitir que você rastreie suas despesas e e gere um relatório para melhor entendimento de como e para aonde está indo os gastos.

  ## Configuração e instalação
  Para realizar a instalação e a configuração usamos um arquivo [docker-compose.yml](Dicionário.md), dentro desse docker-compose podemos gerenciar múltiplos [containers](Dicionário.md). Por usarmos [containers](Dicionário.md) para gerenciar cada aplicação, caso alguma aplicação apresente alguma falha, conseguimos mapear qual arquivo apresentou essa falha e não interrompemos o sistema de chamados. Abaixo podemos ver como funciona o arquivo [docker-compose.yml](Dicionário.md):

  Este [container](Dicionário.md) roda o banco de dados
  ````
  version: "3.8"

services:
#Container do banco de dados
  mariadb:
    image: mariadb:10.7
    container_name: mariadb
    hostname: mariadb
    environment:
      - MARIADB_ROOT_PASSWORD=SENHA_ROOT
      - MARIADB_DATABASE=NOME_BANCO_DE_DADOS
      - MARIADB_USER=USUARIO_BANCO_DE_DADOS
      - MARIADB_PASSWORD=SENHA_GLPI
````

Este [container](Dicionário.md) roda a aplicação do sistema GLPI
````
#Container GLPI
  glpi:
    image: diouxx/glpi
    container_name : glpi
    hostname: glpi
    ports:
      - "80:80"
````
Para a instalação do GLPI, usamos uma [máquina virtual](Dicionário.md) com a distribuição [Ubuntu](Dicionário.md). Dentro do sistema operacional precisamos criar uma pasta para salvar o arquivo [docker-compose.yml](Dicionário.md), com o seguinte comando no [terminal](Dicionário.md):
````
sudo mkdir -p glpi
````
Para criar o arquivo, devemos usar este comando no [terminal](Dicionário.md):
````
sudo nano docker-compose.yml
````
Agora devemos fazer o [deploy](Dicionário.md), usamos o seguinte comando no [terminal](Dicionário.md):
````
sudo docker-compose up -d
````

Após fazer o [deploy](Dicionário.md) do arquivo, podemos acessar o sistema GLPI com a [url](Dicionário.md) definida. Caso não esteja hospedado em um domínio, você pode acessar o sistema pelo [ip/localhost](Dicionário.md) da máquina que está hospedado o sistema.

## Portainer
Para melhor acesso aos [containers](Dicionário.md), estamos usando o portainer. O Portainer é uma plataforma de gerenciamento de [código aberto](Dicionário.md), que interage com o [socket](Dicionário.md) do [docker](Dicionário.md) para criar novos [containers](Dicionário.md) e monitorá-los.

  ## Acesso GLPI
  Todos os acessos do GLPI são sincronizados com o [Active Directory](Dicionário.md), todos os usuários da nossa rede tem um usuário dentro do GLPI, porém nem todos os usuários tem acesso ao sistema. Ao criar um usuário dentro do [Active Directory](Dicionário.md), o GLPI importa os usuários e sincroniza as informações do usuário. Para que um usuário tenha acesso ao sistema GLPI, a equipe de tecnologia deve dar permissão/cargo para está pessoa no sistema, caso contrário irá apresentar a seguinte informação:

![alt text](Prints/Screenshot_4.png)

  ## Quais as vantagens para a empresa?
  Todos os recursos que o sistema GLPI oferece, é uma grande vantagem para a empresa. Se pararmos para analisar, o GLPI oferece diversos recursos e nenhum desses recursos são pagos. Caso aconteça algum problema ou imprevisto, podemos agir da melhor maneira, tendo um melhor gerenciamento de riscos. O funcionário com permissão poderá abrir um chamado relatando o problema e após abrir o chamado, a equipe de tecnologia consegue acompanhar pelo painel administrativo, segue imagem do painel:

![alt text](Prints/Screenshot_5.png)

Neste painel, a equipe de tecnologia tem acesso aos chamados e consegue acompanhar o que foi solicitado, conforme o print abaixo:

![alt text](Prints/Screenshot_6.png)

E com as informações fornecidas, como categoria e qual o erro, temos uma noção de quais as principais causas e com essas informações conseguimos amenizar ainda mais os problemas.

# Observações
Caso encontre alguma palavra que não conheça, verificar se a palavra se encontra no [Dicionário](Dicionário.md), caso a palavra não esteja no dicionário disponibilizado, por favor relatar para a equipe de TI.

# Autores
- **Cleiton Lemos** - _CTO_ - <cleiton.lemos@validu.com.br>
- **Nicolas Saldanha Alves** - _Estagiário Analista de Sistemas_ - <nicolas@camecsp.com.br>
- **Rafael Rodrigues Gomes** - _Analista de Infraestrutura_ - <rafael@camecsp.com.br>