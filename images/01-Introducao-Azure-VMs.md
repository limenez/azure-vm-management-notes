# 01 - Introdução às Máquinas Virtuais (VMs) no Microsoft Azure

Este documento serve como uma introdução fundamental ao conceito de Máquinas Virtuais no ambiente da nuvem Microsoft Azure. Entender o que são as VMs e como elas se encaixam no modelo IaaS (Infraestrutura como Serviço) é o primeiro passo para gerenciá-las de forma eficaz.

## O que são Máquinas Virtuais (VMs)?

Uma Máquina Virtual (VM) é uma emulação de um sistema de computador. No contexto do Azure, uma VM é um **recurso de computação sob demanda e escalável** que fornece a flexibilidade da virtualização sem a necessidade de comprar e manter o hardware físico subjacente.

As VMs no Azure permitem que você execute sistemas operacionais (como Windows Server ou várias distribuições Linux) e instale softwares, assim como faria em um servidor físico tradicional. A principal diferença é que a infraestrutura subjacente (hardware, rede, armazenamento) é gerenciada pela Microsoft, no modelo de **Infraestrutura como Serviço (IaaS)**.

### **Principais Características:**

* **Virtualização:** Cada VM opera como um sistema independente, com seu próprio sistema operacional e recursos dedicados (CPU, memória, armazenamento).
* **Isolamento:** VMs são isoladas umas das outras, garantindo que o comportamento de uma não afete as demais.
* **Flexibilidade:** Você tem controle total sobre o sistema operacional, softwares instalados e configurações de rede.
* **Escalabilidade:** Capacidade de aumentar ou diminuir rapidamente os recursos da VM (escalar verticalmente) ou o número de VMs (escalar horizontalmente).

## Para que servem as Máquinas Virtuais no Azure?

As VMs no Azure são incrivelmente versáteis e podem ser usadas para uma ampla variedade de propósitos, desde o desenvolvimento de aplicativos até a hospedagem de soluções complexas de produção.

### **Casos de Uso Comuns:**

* **Hospedagem de Aplicações e Websites:** Rodar servidores web (IIS, Apache, Nginx), servidores de aplicações, bancos de dados (SQL Server, MySQL, PostgreSQL) ou microsserviços.
* **Ambientes de Desenvolvimento e Teste:** Criar ambientes isolados e descartáveis para que desenvolvedores e testadores trabalhem sem impactar a produção. Facilita o provisionamento rápido e a eliminação após o uso.
* **Servidores de Banco de Dados:** Hospedar bancos de dados relacionais e não relacionais que exigem controle total sobre o ambiente e otimização de performance.
* **Servidores de Domínio (Active Directory):** Executar controladores de domínio ou outros serviços de infraestrutura para ambientes híbridos ou totalmente na nuvem.
* **Serviços de Computação de Alto Desempenho (HPC):** Para cargas de trabalho que exigem grande poder de processamento, como simulações científicas, renderização de vídeo ou análise de dados complexos.
* **Extensão do Data Center Local (Híbrido):** Conectar sua rede local ao Azure para estender a capacidade do seu data center, migrar cargas de trabalho gradualmente ou criar ambientes de recuperação de desastres (DR).
* **Ambientes de Teste e Qualidade (QA):** Replicar ambientes de produção para testar novas versões de software ou patches antes da implantação.

## Tipos e Séries de VMs no Azure

O Azure oferece uma vasta gama de tamanhos e séries de VMs, cada uma otimizada para diferentes cargas de trabalho e orçamentos. A escolha do tipo de VM é crucial e depende das suas necessidades de CPU, memória, armazenamento e rede.

### **Algumas Categorias Comuns de Séries de VMs:**

* **Uso Geral (General Purpose - ex: Dasv5, B, Dv3, Av2):** Um bom equilíbrio entre CPU, memória e disco. Ideal para a maioria das cargas de trabalho, como servidores web, pequenos bancos de dados e ambientes de desenvolvimento/teste.
* **Otimizadas para Computação (Compute Optimized - ex: Fsv2):** Alta proporção CPU-memória, ideais para servidores web de alto tráfego, aparelhos de rede, processamento de lote e servidores de aplicativos.
* **Otimizadas para Memória (Memory Optimized - ex: Ev5, Mv2):** Alta proporção memória-CPU, ideais para bancos de dados relacionais de grande escala, data warehouses e outros aplicativos que exigem muita memória.
* **Otimizadas para Armazenamento (Storage Optimized - ex: Lsv3):** Alto throughput de disco e IOPS, ideais para Big Data, SQL e NoSQL databases transacionais, e data warehouses.
* **Otimizadas para GPU (GPU Optimized - ex: NV, NC, ND):** Possuem GPUs para cargas de trabalho especializadas como renderização gráfica, treinamento de aprendizado de máquina e simulações.
* **Computação de Alto Desempenho (High Performance Compute - HPC - ex: H, HB, HC):** Projetadas para cargas de trabalho de computação intensiva, como simulações, modelagem financeira e engenharia.

A escolha da série e do tamanho da VM impactará diretamente o desempenho e o custo. É importante considerar as necessidades do seu aplicativo e projetar a infraestrutura de forma eficiente.