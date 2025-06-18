# 03 - Conectividade Segura e Acesso Remoto a Máquinas Virtuais no Azure

A segurança é um pilar fundamental ao gerenciar VMs na nuvem. A forma como você acessa suas máquinas remotamente é crítica para proteger seus recursos contra acessos não autorizados. Este documento aborda os principais métodos de conexão e as melhores práticas de segurança no Azure.

## Métodos de Conexão Remota

As Máquinas Virtuais no Azure podem ser acessadas remotamente utilizando protocolos padrão, dependendo do sistema operacional.

### **Para VMs Linux:**

* **SSH (Secure Shell):** É o protocolo padrão para acesso remoto seguro a servidores Linux.
    * **Autenticação por Par de Chaves SSH:** **Altamente recomendado e a melhor prática de segurança.** Envolve uma chave pública (que você configura na VM durante a criação) e uma chave privada (que você mantém segura em seu computador local).
        * **Vantagens:** Mais seguro que senhas, pois as chaves são muito difíceis de adivinhar ou quebrar.
    * **Autenticação por Senha:** Mais simples de configurar inicialmente, mas **menos segura** e não recomendada para ambientes de produção. Senhas podem ser alvo de ataques de força bruta.

### **Para VMs Windows:**

* **RDP (Remote Desktop Protocol):** É o protocolo padrão para acesso remoto a servidores Windows, fornecendo uma interface gráfica.
    * **Autenticação por Usuário e Senha:** Você se conecta usando um nome de usuário e uma senha definidos durante a criação da VM.

## Segurança da Rede com Network Security Groups (NSG)

Um **Grupo de Segurança de Rede (NSG)** atua como um firewall virtual para controlar o tráfego de rede para e a partir de recursos do Azure em uma Rede Virtual (VNet). Ele é essencial para proteger suas VMs.

### **Regras de Segurança de Rede:**

* **Regras de Entrada (Inbound Security Rules):** Controlam o tráfego que **entra** na sua VM. Por exemplo, você pode criar uma regra para permitir o tráfego SSH (porta 22) apenas de um endereço IP específico do seu escritório, ou RDP (porta 3389) de uma faixa de IPs específica.
* **Regras de Saída (Outbound Security Rules):** Controlam o tráfego que **sai** da sua VM. Por padrão, as configurações de segurança de rede para uma nova VM permitem o tráfego de saída.

### **Configurações Padrão:**

* Por padrão, uma nova VM geralmente terá regras de saída que permitem todo o tráfego para a internet. O tráfego de entrada só é permitido dentro da rede virtual ou para portas específicas (como SSH/RDP) se você as permitir explicitamente.
* **Melhor Prática:** Restrinja as portas de acesso remoto (22 para SSH, 3389 para RDP) a endereços IP conhecidos e específicos, ou utilize soluções mais seguras como o Azure Bastion.

## Azure Bastion: Acesso Seguro sem Expor Portas

O **Azure Bastion** é um serviço PaaS (Plataforma como Serviço) totalmente gerenciado que fornece conectividade RDP/SSH segura e contínua às suas máquinas virtuais diretamente do Portal do Azure.

### **Principais Vantagens do Azure Bastion:**

* **Segurança Aprimorada:** A principal vantagem é que ele fornece um acesso seguro sem a necessidade de expor as portas RDP (3389) ou SSH (22) das suas VMs diretamente à internet. Isso reduz drasticamente a superfície de ataque da sua VM.
* **Acesso Baseado em Navegador:** Conecte-se às suas VMs via SSH ou RDP diretamente no seu navegador web, através do portal do Azure.
* **Sem IP Público nas VMs:** Suas VMs não precisam de IPs públicos para serem acessíveis via Bastion, o que aumenta a segurança.
* **Elimina a Necessidade de VPN (para acesso a VMs específicas):** Para acesso apenas às VMs, não é necessário configurar uma VPN Ponto a Site ou Site a Site. No entanto, para acesso a outros recursos na VNet, uma VPN ainda pode ser necessária.
* **Conform