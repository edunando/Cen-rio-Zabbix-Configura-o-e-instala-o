# Instalação e Configuração do Zabbix-Server 6.0

![GitHub repo size](https://img.shields.io/github/repo-size/iuricode/README-template?style=for-the-badge)
![GitHub language count](https://img.shields.io/github/languages/count/iuricode/README-template?style=for-the-badge)
![GitHub forks](https://img.shields.io/github/forks/iuricode/README-template?style=for-the-badge)
![Bitbucket open issues](https://img.shields.io/bitbucket/issues/iuricode/README-template?style=for-the-badge)
![Bitbucket open pull requests](https://img.shields.io/bitbucket/pr-raw/iuricode/README-template?style=for-the-badge)

### Ajustes e melhorias

O projeto ainda está em desenvolvimento e as próximas atualizações serão voltadas nas seguintes tarefas:

- [x] Instalação e Configuração do Zabbix Server 6.0 LTS
- [x] Instalação e Configuração do Zabbix-Agent em um ambiente Linux
- [x] Configuração do Roteador Mikrotik para Monitoramento via SMNP
- [x] Instalação e Configuração do Zabbix-Agent em um ambiente Windows
- [ ] Integração com Grafana ou Alexander

## 💻 Pré-requisitos

Antes de começar, verifique se você atendeu aos seguintes requisitos:

* Você instalou a versão mais recente do Debian 12 
* Você tem uma máquina `Windows Server EVALX64`.
* Baixar uma iso do RouterOS Mikrotik no site: https://mikrotik.com/download

## 🚀 Instalando o Zabbix Server no Debian 12

Para instalar o Zabbix Server no Debian 12 , siga estas etapas: https://www.zabbix.com/download?zabbix=6.0&os_distribution=debian&os_version=12&components=server_frontend_agent&db=mysql&ws=apache

Após a instalação segundo o passo a passo se atentar nas configurações do DBUser, DBPassword e Server se estão configuradas corretamente no caminho abaixo:

```
/etc/zabbix/zabbix_server.conf
```
![image](https://github.com/edunando/Cen-rio-Zabbix-Configura-o-e-instala-o/assets/88983626/4baa8be1-c1b3-4813-bd4d-e73c7554b784)

Após a configuração ja é possível estar acessando o Zabbix na Web, porém, no momento não irá haver hosts para monitoramento...

## ☕ Instalação para os Zabbix Agent no Ubuntu Server 22.04:

https://www.zabbix.com/download?zabbix=6.0&os_distribution=ubuntu&os_version=22.04&components=agent_2&db=&ws=

Após a instalação Identificar se o serviço está rodando.

## ☕ Instalação para os Zabbix Agent no Windows Server :

https://www.zabbix.com/download_agents?version=6.0+LTS&release=6.0.21&os=Windows&os_version=Any&hardware=amd64&encryption=OpenSSL&packaging=MSI&show_legacy=0

Da mesma maneira como no Linux, verificar a disponibilidade do processo em services.msc

## ☕ Configuração do SNMP do Roteador Mikrotik :

Primeiramente configurar uma interface de rede para acesso:

```
ip address add  address=[IP/Mascara ex: /24] interface=[INTERFACE DE REDE EX: ether1]
```
```
ip route add dst-address=0.0.0.0 gateway=[IP]
```
```
ip dns set servers=8.8.8.8
```
Após a configuração do roteador via CLI, Acessar a Interface WEB do mikrotik.

![image](https://github.com/edunando/Cen-rio-Zabbix-Configura-o-e-instala-o/assets/88983626/c49c3209-8fd2-4a98-b5ab-064d23357e8a)

Após acessar ip -> SNMP utilizar a communitie padrão public com trap version 2.


## 📫 Adicionando os Hosts Para monitoramento

Para tornar o monitoramento funcional é necessário que os hosts estejam devidamente configurados. Para isso, acessar o zabbix server na web, acessar na parte de monitoramento os hosts.

![image](https://github.com/edunando/Cen-rio-Zabbix-Configura-o-e-instala-o/assets/88983626/710ae93d-f2cc-4722-b885-f568daf0d13a)

1. Selecionar na parte superior direito a opção Criar host
   
2. Após isso você deve selecionar de acordo com o que você configurou, tanto a interface, e selecionar o template do equipamento.
   
   ![image](https://github.com/edunando/Cen-rio-Zabbix-Configura-o-e-instala-o/assets/88983626/8171a427-08ad-46b5-b695-7cb1412f3d8d)

3. Após a adição, aguardar um tempo até ele conseguir estabeler a conexão com o agent e ficar com o seguinte status
   
   ![image](https://github.com/edunando/Cen-rio-Zabbix-Configura-o-e-instala-o/assets/88983626/fa7121d4-e3d5-4d77-950c-62b50cb910cd)

4. Após Conseguir estabeler a conexão você pode adicionar os triggers de acordo com o seu critério acessando Configuração -> Hosts -> Triggers
   
   ![image](https://github.com/edunando/Cen-rio-Zabbix-Configura-o-e-instala-o/assets/88983626/d6bacd94-b3c2-4009-98e4-e867b6dcb3c1)

5. Há diversos triggers que podem ser estabelecidas diferentes regras, de acordo com sua escolha.
   ![image](https://github.com/edunando/Cen-rio-Zabbix-Configura-o-e-instala-o/assets/88983626/3d692bd1-9760-447c-b3c8-0ea0a0972ad5)

6. Para criar um trigger só selecionar na parte superior direita e realizar a adição de acordo com seu ambiente.

   ![image](https://github.com/edunando/Cen-rio-Zabbix-Configura-o-e-instala-o/assets/88983626/9cc00d24-3653-41fb-a6c0-9bfd52d8041f)

## 😄 Seja um dos contribuidores
