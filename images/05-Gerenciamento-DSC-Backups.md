# 05 - Gerenciamento de Configuração (DSC) e Backups de Máquinas Virtuais no Azure

O gerenciamento de Máquinas Virtuais no Azure vai além da simples criação. Inclui a padronização de configurações e a proteção de dados essenciais através de backups.

## Desired State Configuration (DSC)

O **Desired State Configuration (DSC)** é um recurso de gerenciamento do PowerShell (para Windows) e uma tecnologia compatível com Linux que permite definir e manter a configuração do software em seus servidores. Com o DSC, você garante que suas VMs estejam sempre em um estado consistente e desejado.

### **Como o DSC Funciona no Azure para VMs:**

1.  **Definição do Estado Desejado:** Você cria scripts de configuração DSC que descrevem o estado desejado dos seus servidores (ex: quais recursos devem estar instalados, quais serviços devem estar rodando, configurações de registro).
2.  **Extensão DSC para VMs:** No Azure, você pode implantar a extensão DSC para VMs Windows Server e para VMs Linux. Esta extensão permite que as VMs busquem e apliquem as configurações DSC definidas por você.
    * Para VMs Windows Server, a extensão DSC para VMs pode ser usada.
    * Para VMs Linux (como Ubuntu), também é possível usar a extensão DSC, que instala o agente DSC para Linux, permitindo que a VM aplique configurações.
3.  **Aplicação e Monitoramento:** O agente DSC na VM garante que a máquina esteja sempre em conformidade com o estado desejado, corrigindo automaticamente quaisquer desvios.

### **Vantagens do DSC:**

* **Padronização:** Garante que todas as VMs em seu ambiente (Windows e Linux) tenham a mesma configuração, reduzindo erros e inconsistências.
* **Automação:** Automatiza a configuração e manutenção do servidor.
* **Conformidade:** Ajuda a manter a conformidade com políticas de segurança e governança.
* **Reversão de Configurações:** Facilita a reversão para um estado conhecido em caso de problemas.

## Backups de Máquinas Virtuais

A configuração de backup é uma responsabilidade crucial do usuário (cliente) ao gerenciar Máquinas Virtuais no Azure. **A Microsoft não faz o backup automático de todas as máquinas virtuais por padrão.**

### **Por que o Backup é Essencial?**

* **Proteção contra Perda de Dados:** Backups protegem seus dados contra exclusão acidental, corrupção, ataques de ransomware e outras falhas.
* **Recuperação de Desastres:** Permitem restaurar suas VMs para um estado anterior em caso de desastres, garantindo a continuidade dos negócios.
* **Conformidade:** Muitos requisitos regulatórios e de conformidade exigem estratégias de backup robustas.

### **Responsabilidade Compartilhada do Backup:**

* No modelo de IaaS (Infraestrutura como Serviço), onde as VMs se encaixam, a **configuração e o gerenciamento do backup são responsabilidades do usuário (cliente)**.
* Embora a Microsoft forneça a infraestrutura e as ferramentas (como o Azure Backup), a decisão de quais VMs fazer backup, com que frequência e por quanto tempo, e a execução do backup em si, cabem a você.

### **Azure Backup para VMs:**

O Azure Backup é um serviço que ajuda a proteger os dados de VMs no Azure.

* **Recursos:** Oferece backups consistentes com o aplicativo, retenção de longo prazo, recuperação pontual e opções de armazenamento redundantes.
* **Configuração:** Você configura políticas de backup que definem a frequência (diária, semanal), o horário e o período de retenção dos pontos de recuperação.

Ignorar a configuração de backups para reduzir custos não é uma prática recomendada para ambientes de produção. A proteção de dados é vital.