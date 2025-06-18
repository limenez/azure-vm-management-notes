# 02 - Criação de Máquinas Virtuais (VMs) no Microsoft Azure

A criação de uma máquina virtual no Azure envolve uma série de decisões e configurações que impactam seu desempenho, custo, segurança e capacidade de gerenciamento. Este guia abordará os passos principais e considerações importantes ao provisionar VMs Windows e Linux.

## Visão Geral do Processo de Criação de VM

O processo de criação de uma VM no Azure é geralmente guiado pelo Portal do Azure, embora também possa ser feito via Azure CLI, Azure PowerShell ou modelos ARM. No portal, você passará por várias abas ou seções para configurar a VM.

### **Passos Principais no Portal do Azure:**

1.  **Noções Básicas (Basics):** Informações essenciais como assinatura, grupo de recursos, nome da VM, região, imagem do SO e método de autenticação.
2.  **Discos (Disks):** Configurações de disco do sistema operacional e adição de discos de dados.
3.  **Rede (Networking):** Configuração de rede virtual, sub-rede, IP público e regras de segurança de rede (NSG).
4.  **Gerenciamento (Management):** Opções de monitoramento, diagnóstico, identidade e automação.
5.  **Monitoramento (Monitoring):** Configurações para monitorar o desempenho e a saúde da VM.
6.  **Avançado (Advanced):** Extensões, dados de usuário, cloud-init (para Linux).
7.  **Tags (Tags):** Organização e categorização de recursos.
8.  **Revisar + Criar (Review + create):** Validação das configurações e criação final da VM.

## Configurações Chave durante a Criação

### 1. Noções Básicas

* **Assinatura e Grupo de Recursos:**
    * **Assinatura:** Escolha a assinatura do Azure onde os custos serão cobrados.
    * **Grupo de Recursos (Resource Group):** Um contêiner lógico para seus recursos do Azure. É uma boa prática agrupar recursos relacionados para facilitar o gerenciamento, faturamento e exclusão. Se não tiver um, crie um novo.
* **Nome da Máquina Virtual:** Defina um nome único para sua VM dentro do grupo de recursos.
* **Região:** Escolha a região geográfica onde a VM será implantada. Considere a proximidade com seus usuários (para menor latência) e a disponibilidade de recursos e zonas de disponibilidade.
* **Opções de Imagem:**
    * **Sistema Operacional:** Selecione a imagem do sistema operacional (SO). Exemplos comuns:
        * **Windows Server:** (Ex: Windows Server 2019 Datacenter)
        * **Linux:** (Ex: Ubuntu Server, Red Hat Enterprise Linux, CentOS)
    * **Versão/Edição:** Escolha a versão específica do SO.
* **Tamanho da VM (Size):**
    * Define a quantidade de vCPUs, memória e os tipos de discos suportados.
    * A escolha do tamanho é crucial para o desempenho e custo da VM. O Azure oferece diferentes séries de VMs otimizadas para diversas cargas de trabalho (uso geral, otimizado para computação, memória, armazenamento, etc.).