<!-- Title -->

<p align="center">
  <h2 align="center">Grafana</h2>
  <h1 align="center"><img src="https://upload.wikimedia.org/wikipedia/commons/thumb/a/a1/Grafana_logo.svg/800px-Grafana_logo.svg.png" alt="Imagem Grafana" width="150"></h1>

# O que é o Grafana?
O Grafana é uma plataforma interativa de visualização de dados [open source](Dicionário.md), desenvolvida pela [Grafana Labs](https://grafana.com/), que permite aos usuários ver dados por meio de tabelas e gráficos unificados em um painel ou vários, para facilitar a interpretação e a compreensão. Você também pode consultar e definir alertas sobre suas informações e métricas de qualquer lugar que os dados estejam, sejam ambientes de servidor tradicionais, [clusters do Kubernetes](Dicionário.md) ou vários [serviços em nuvem](Dicionário.md) etc.

Assim, você poderá analisar os dados com mais facilidade, identificar tendências e inconsistências e, por fim, tornar seus processos mais eficientes. O Grafana foi construído com base nos princípios [open source](Dicionário.md) e na crença de que os dados devem ser acessíveis em toda a organização, não apenas para um pequeno grupo de pessoas.

## Por que utilizar o Grafana na sua empresa?
Com o grafana, a empresa pode acompanhar todas as informações importantes vindas de diversas fontes -  como bancos de dados e outras ferramentas - por meio de uma única interface intuitiva e completa. Isso facilita a gestão de indicadores e o monitoramento de dados em tempo real, o que torna a tomada de decisões na empresa mais rápida e eficiente.

## Quais as vantagens do Grafana?
Todos os [dashboards](Dicionário.md) do Grafana podem ser customizados, dando muita flexibilidade tanto na hora de configurar quanto na utilização, podendo ser integrado com outras ferramentas ou bancos de dados. Isto habilita uma gestão mais eficiente e transparente nas empresas, fornecendo indicadores em tempo real.

A principal vantagem desta ferramenta é a capacidade de unificação em um único [dashboard](Dicionário.md), diversas informações de diversas fontes, simplificando o uso e trazendo todas as informações que os usuários precisa de forma **gráfica, simples e eficiente.**

### Liberdade 
É possível integrar o Grafana com outras ferramentas como o [Zabbix](Zabbix.md), [GLPI](GLPI.md) e bancos de dados como [MySQL](Dicionário.md), [PostgresSQL](Dicionário.md), entre outros. É possível integrar o Grafana á diversas soluções, a lista de compatibilidade cresce constantemente, fornecendo mais opções para as empresas que adotam esta ferramenta.

### Flexibilidade
A flexibilidade de implementação se dá por meio de [plugins](Dicionário.md) que podem ser adicionados, habilitando o Grafana a se conectar com outras ferramentas e extrair informações que serão exibidas em seus [dashboards](Dicionário.md).

Como dito anteriormente, os [dashboards](Dicionário.md), por sua vez, podem ser criados de forma livre, permitindo que um único [dashboard](Dicionário.md) exiba informações de fontes diferentes, tornando sua utilização mais dinâmica e customizável às necessidades do usuário.

## Grafana e o monitoramento de TI

A aplicação do Grafana em soluções de monitoramento de TI torna-se uma união valiosa, especialmente se considerarmos que muitas ferramentas de TI possuem seus próprios bancos de dados ou até mesmo seus próprios gráficos e [dashboards](Dicionário.md).

A melhor maneira de lidar com isso é unificar estes [dashboards](Dicionário.md), criar gráficos que outras aplicações não conseguem fornecer, este é o principal valor do Grafana para estas soluções. Ao integrar esta solução na malha de monitoramento e unificando os [dashboards](Dicionário.md), resolve-se um problema de longa data presente na TI, e possibilita o estabelecimento de um [NOC](Dicionário.md) e um [SOC](Dicionário.md).

O [NOC](Dicionário.md) fica responsável por acompnahar todas as operações que ocorrem diariamente na TI, captando e solucionando problemas antes que eles ocorram. Já o [SOC](Dicionário.md) fica responsável pelo monitoramento de segurança, acompanhando em tempo real as possíveis vulnerabilidades e ataques antes mesmo de ocorrerem.


# Instalação Grafana


# Integração com o Zabbix

A integração entre as ferramentas Grafana e [Zabbix](Zabbix.md) é realizada através de um [plugin](Dicionário.md) que deve ser instalado no Grafana, ele é responsável por permitir a criação de um datasource que irá consumir a [API](Dicionário.md) do [Zabbix](Zabbix.md).

## Criando um usuário no Zabbix para integração

Toda a comunicação entre o Grafana e o Zabbix é realizada através da [API](Dicionário.md), apesar de em versões mais recentes do [plugin](Dicionário.md), ser possível configurá-lo para buscar os dados de history e trends diretamente no banco de dados do [Zabbix](Zabbix.md), a [API](Dicionário.md) será sempre utilizada.

Sabendo disso, é uma boa prática realizar a criação de um usuário administrativo para uso exclusivo pelo [Plugin](Dicionário.md), permitindo dessa forma um ajuste fino das permissões que o Grafana possui para acesso no [Zabbix](Zabbix.md).

Primeiramente criamos um *User Group* com o frontend desabilitado e com as permissões de visualização necessárias.

![Gif](https://miro.medium.com/v2/resize:fit:720/format:webp/1*gBDWumacHA3HgfRVKVl_uA.gif)

Após a criação do grupo, criamos o *User* administrativo

![Gif2](https://miro.medium.com/v2/resize:fit:720/format:webp/1*EJhg7vbLehT5Jij8pblDgw.gif)

## Instalando o plugin no Grafana

O [plugin](Dicionário.md) pode ser instalado através de um utilitário de linha de comando do Grafana chamado grafana-cli, usando os comandos abaixo dentro do seu [terminal]:
````
grafana-cli plugins install alexanderzobnin-zabbix-app
systemctl restart grafana-server
````

Em versões mais recentes Grafana 7+ e [plugin](Dicionário.md) 4+ é necessário incluir o parâmetro abaixo no arquivo de configuração grafana.ini, abaixo da sessão [plugins](Dicionário.md), atenção para o nome que deve terminar com [datasource](Dicionário.md).

````
[plugins]
allow_loading_unsigned_plugins = alexanderzobnin-zabbix-datasource
````

Instalando e posteriormente reiniciando o serviço do Grafana, após a instalação é necessário habilitar o [plugin](Dicionário.md) na interface do Grafana, como na demonstração abaixo:

![Gif3](https://miro.medium.com/v2/resize:fit:720/format:webp/1*y3g9Kekvf7c6_3UI5uZLlw.gif)

## Configurando o Datasource

Ao finalizar o processo de instalação do [plugin](Dicionário.md), estará disponível a opção de criar [datasource](Dicionário.md) do tipo Zabbix, lembrando que no Grafana os datasources são separados por *organizations*, para cada *org* será necessário criar um novo datasource, essa flexibilidade permite criar *orgs* separadas por clientes com [datasources](Dicionário.md) independetes.

![Gif4](https://miro.medium.com/v2/resize:fit:720/format:webp/1*dzuZaJNs90O-wdeFOejrdw.gif)

__Name__: Defina um nome para esse datasource.

__Url__: A url que responde pela API do Zabbix.

__Access__: O tipo de acesso que será realizado, Server indica que as requisições serão realizadas pelo [backend](Dicionário.md) do Grafana, partindo do Grafana Server, browser as requisições são realizadas a partir do navegador do usuário. Vale ressalatar que se escolhida a opção browser, o cliente também necessita ter acesso a interface web do Zabbix, uma vez que as requisições irão partir diretamente do cliente para o servidor Zabbix.

__Trends__: Selecione se quiser que o [plugin](Dicionário.md) também utilize dados armazenados na tabela trends.

__After__: O período que o [plugin](Dicionário.md) irá considerar para buscar da tabela trends, ex: Se configurado para 4d, quando selecionado um intervalo de tempo maior do que 4 dias os dados serão recuperados da tabela trends.

__Range__: O intervalo de tempo no qual o [plugin](Dicionário.md) deverá buscar os dados da tabela trends, ex: Se configurado para 3d, quando o intervalo selecionado for maior que 3 dias, os dados serão recuperados da tabela trends, mesmo que sejam dados anteriores a 4 dias configurado no passo anterior.

Essas são as principais configurações para ter uma integração funcional, para outras configurações pode ser consultada diretamente na documentação do [plugin](Dicionário.md) em: https://alexanderzobnin.github.io/grafana-zabbix/configuration/

### Problemas Comuns
- Usuário do Zabbix utilizado para integração não possui permissão de acesso aos hosts no Zabbix.
- O Grafana por padrão mantém um [cache](Dicionário.md) dos dados coletados do Zabbix, eventualmente pode ocorrer desse [cache](Dicionário.md) não refletir mudanças recentes no Zabbix, uma forma de forçar a atualização desse [cache](Dicionário.md) é ir até a configuração do [datasource](Dicionário.md) Zabbix e salvar as configurações, isso fará com que o [cache](Dicionário.md) seja descartado atualizando as informações.
- Alguns itens não aparecem para seleção na interface do Grafana, lembrar que por padrão os panels exibem métricas do Zabbix, ou seja, valores numéricos, se por ventura precisar exibir algum texto será necessário alterar para opção text na configuração do panel.
- Instalação foi realizada com sucesso porém não aparece a opção para seleção do datasource Zabbix, normalmente esta relacionado a falta do parâmetro allow_loading_unsigned_plugins no arquivo de configuração do Grafana.


# Observações
Caso encontre alguma palavra que não conheça, verificar se a palavra se encontra no [Dicionário](Dicionário.md), caso a palavra não esteja no dicionário disponibilizado, por favor relatar para a equipe de TI.


# Autores
- **Cleiton Lemos** - _CTO_ - <cleiton.lemos@validu.com.br>
- **Nicolas Saldanha Alves** - _Estagiário Analista de Sistemas_ - <nicolas@camecsp.com.br>
- **Rafael Rodrigues Gomes** - _Analista de Infraestrutura_ - <rafael@camecsp.com.br>