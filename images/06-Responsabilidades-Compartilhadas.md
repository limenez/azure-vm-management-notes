# 06 - Modelo de Responsabilidade Compartilhada no Azure

Ao utilizar serviços de nuvem como o Microsoft Azure, é fundamental compreender o **Modelo de Responsabilidade Compartilhada**. Este modelo define claramente quais aspectos da segurança e do gerenciamento são de responsabilidade do provedor de nuvem (Microsoft) e quais são de responsabilidade do cliente (você).

No contexto de Máquinas Virtuais (VMs), que se enquadram na categoria **Infraestrutura como Serviço (IaaS)**, a responsabilidade é dividida da seguinte forma:

## Responsabilidades da Microsoft (Provedor da Nuvem)

A Microsoft é responsável pela **segurança da nuvem** (Security *of* the Cloud). Isso inclui a proteção da infraestrutura física que hospeda os serviços do Azure.

### **Exemplos de Responsabilidades da Microsoft em IaaS (VMs):**

* **Infraestrutura Física:**
    * Garantir que o ambiente de hospedagem físico esteja funcional, incluindo energia e ar-condicionado.
    * Monitorar a integridade física do hardware e substituí-lo quando necessário.
    * Administrar os data centers e a conectividade de rede entre os servidores físicos.
    * Garantir que a infraestrutura física da nuvem esteja sempre disponível.
* **Virtualização:** O hipervisor e a infraestrutura que permite a virtualização das VMs.
* **Segurança Física:** Segurança dos próprios data centers (controles de acesso, vigilância).

## Responsabilidades do Cliente (Usuário)

O cliente é responsável pela **segurança na nuvem** (Security *in* the Cloud). Isso inclui o gerenciamento e a proteção dos componentes que você executa sobre a infraestrutura da Microsoft.

### **Exemplos de Responsabilidades do Cliente em IaaS (VMs):**

* **Sistema Operacional (SO):**
    * Gerenciar o sistema operacional, incluindo as atualizações do sistema (patches e service packs) e a segurança.
* **Aplicativos e Dados:**
    * Instalar, configurar e manter seus aplicativos.
    * Proteger e gerenciar seus dados (incluindo backups).
* **Configuração de Rede da VM:**
    * Configurar Network Security Groups (NSGs) e outras regras de firewall para controlar o tráfego de rede para suas VMs.
    * Controlar quem acessa as máquinas virtuais e quando.
    * Garantir que as portas de gerenciamento (SSH/RDP) não sejam expostas diretamente à internet (usando Azure Bastion, VPN, etc.).
* **Autenticação e Acesso:**
    * Gerenciar usuários, grupos e permissões dentro do sistema operacional da VM.
    * Configurar métodos de autenticação seguros (ex: chaves SSH em vez de senhas).
* **Monitoramento da Aplicação:**
    * Monitorar o desempenho e a saúde de suas aplicações rodando nas VMs.

## Resumo das Responsabilidades (VMs - IaaS)

| Área de Responsabilidade | Microsoft (Responsabilidade *da* Nuvem) | Cliente (Responsabilidade *na* Nuvem) |
| :----------------------- | :------------------------------------- | :------------------------------------- |
| **Física** | Data Center, Hardware, Rede Física, Energia | N/A                                    |
| **Virtualização** | Hipervisor, Host Virtualizado           | N/A                                    |
| **Sistema Operacional** | N/A                                    | SO, Patches, Configurações             |
| **Aplicativos** | N/A                                    | Software, Middleware                   |
| **Dados** | N/A                                    | Dados da Aplicação, Backup, Criptografia |
| **Rede** | Hardware de Rede (Físico), Conectividade do Data Center | Configuração de Rede da VM (NSG, IP, VNet), Conectividade da Aplicação |
| **Identidade/Acesso** | Autenticação da Plataforma Azure         | Autenticação e Autorização no SO da VM |

Ao entender claramente essas divisões de responsabilidade, você pode planejar e implementar suas soluções de VM no Azure de forma mais segura e eficiente. A máquina de produção requer ativação de recursos como alta disponibilidade e backup, enquanto a de teste não, e esta é a principal diferença entre elas.