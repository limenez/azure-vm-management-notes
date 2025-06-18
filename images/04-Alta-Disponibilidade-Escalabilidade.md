# 04 - Alta Disponibilidade (HA) e Escalabilidade de Máquinas Virtuais no Azure

Para garantir que suas aplicações hospedadas em Máquinas Virtuais no Azure sejam robustas e capazes de lidar com variações de carga, é fundamental compreender os conceitos de Alta Disponibilidade (HA) e Escalabilidade.

## Alta Disponibilidade (HA) de VMs

Alta Disponibilidade refere-se à capacidade de uma aplicação ou serviço permanecer operacional e acessível, mesmo na ocorrência de falhas. No Azure, isso é alcançado através da distribuição de VMs em diferentes domínios de falha e atualização, ou zonas de disponibilidade.

### **Conjuntos de Disponibilidade (Availability Sets):**

Um **Conjunto de Disponibilidade** é um agrupamento lógico de VMs que permite ao Azure compreender como a sua aplicação é construída para fornecer redundância e disponibilidade. Ele garante que as VMs implantadas nesse conjunto sejam isoladas de falhas de hardware ou manutenção planejada da infraestrutura.

* **Domínios de Falha (Fault Domains):**
    * Definem o grupo de máquinas virtuais que compartilham uma fonte de energia comum, um switch de rede e um rack físico comum.
    * Ao implantar VMs em um Conjunto de Disponibilidade, o Azure as distribui automaticamente em diferentes domínios de falha (até três), garantindo que uma falha em um rack ou componente de infraestrutura não derrube todas as suas VMs simultaneamente.
* **Domínios de Atualização (Update Domains):**
    * Definem os grupos de VMs e hardware subjacente que podem ser reiniciados ao mesmo tempo durante atualizações de software de host ou manutenção planejada do Azure.
    * O Azure garante que apenas um domínio de atualização seja atualizado por vez, mantendo outras VMs do conjunto online.

### **Zonas de Disponibilidade (Availability Zones):**

As **Zonas de Disponibilidade** são locais físicos separados dentro de uma região do Azure, cada uma com sua própria energia, resfriamento e rede isoladas. Elas fornecem proteção contra falhas de data center inteiro.

* Ao implantar suas VMs em diferentes Zonas de Disponibilidade, você protege sua aplicação contra falhas que possam afetar um único data center.
* Oferecem um SLA de uptime mais elevado do que os Conjuntos de Disponibilidade (normalmente 99,99%).
* São ideais para aplicações críticas que exigem o mais alto nível de resiliência.

### **Minimizando o Impacto de Interrupções:**

Se seu serviço com duas VMs está sofrendo interrupções ocasionais, as duas ações principais para minimizar o impacto são:
1.  **Adicionar um Balanceador de Carga (Load Balancer):** Para distribuir o tráfego entre as VMs, garantindo que se uma VM falhar, o tráfego seja direcionado para a VM saudável.
2.  **Colocar as Máquinas Virtuais em um Conjunto de Disponibilidade:** Para garantir que as VMs sejam distribuídas em diferentes domínios de falha e atualização, protegendo contra falhas de hardware e manutenção.

## Escalabilidade de VMs com Virtual Machine Scale Sets (VMSS)

**Escalabilidade** é a capacidade de um sistema de lidar com uma carga de trabalho crescente (ou decrescente) ajustando seus recursos. No Azure, os **Virtual Machine Scale Sets (VMSS)** são a solução ideal para isso.

### **O que é um Virtual Machine Scale Set (VMSS)?**

O VMSS permite criar e gerenciar um conjunto de máquinas virtuais idênticas que podem ser escaladas automaticamente conforme a demanda de carga. Ele é projetado para lidar com grandes cargas de trabalho, provisionando e desprovisionando automaticamente instâncias de VM para corresponder à demanda, garantindo alta disponibilidade e desempenho otimizado.

### **Auto-scaling (Escala Automática):**

O comportamento de escala automática em um VMSS é definido por **regras que determinam quando adicionar ou remover máquinas com base em métricas de utilização**, como o uso de CPU ou memória.

* **Regras de Scale-Out:** Adicionam novas instâncias de VM quando a demanda aumenta (ex: uso de CPU acima de 70% por 5 minutos).
* **Regras de Scale-In:** Removem instâncias de VM quando a demanda diminui (ex: uso de CPU abaixo de 30% por 10 minutos).
* **Baseado em Agendamento:** Você também pode configurar o autoscaling para ajustar o número de instâncias em horários específicos (ex: aumentar VMs durante o horário comercial).

### **Vantagens de usar VMSS:**

* **Gerenciamento Simplificado:** Gerencia um grupo de VMs como uma única entidade, facilitando implantação, configuração e atualizações.
* **Alta Disponibilidade:** As VMs dentro de um VMSS podem ser distribuídas entre Zonas de Disponibilidade ou Conjuntos de Disponibilidade para garantir resiliência.
* **Escalabilidade Automática:** Ajusta a capacidade para atender à demanda, otimizando custos e garantindo performance.
* **Balanceamento de Carga Integrado:** Frequentemente usado em conjunto com um Azure Load Balancer para distribuir o tráfego entre as instâncias do VMSS.

A combinação de Conjuntos de Disponibilidade/Zonas de Disponibilidade e Virtual Machine Scale Sets permite construir aplicações altamente disponíveis, resilientes e escaláveis no Azure.