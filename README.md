# OPM Reservoir Simulator: Cloud Performance & GPU Acceleration

![Azure](https://img.shields.io/badge/Cloud-Azure-0078D4?style=flat-square&logo=microsoft-azure&logoColor=white)
![CUDA](https://img.shields.io/badge/Acceleration-Nvidia%20CUDA-76B900?style=flat-square&logo=nvidia&logoColor=white)
![C++](https://img.shields.io/badge/Language-C++-00599C?style=flat-square&logo=c%2B%2B&logoColor=white)
![Status](https://img.shields.io/badge/Status-Research%20Complete-success?style=flat-square)
![License](https://img.shields.io/badge/License-GPLv3-blue?style=flat-square)

---

## Research Overview

This project focuses on the **Open Porous Media (OPM)** simulator, an open-source suite for modeling fluid flow in porous media (such as aquifers, oil reservoirs, and CO₂ storage).

The primary goal was to analyze the **computational performance** of the simulator when deployed on **Microsoft Azure**, specifically investigating:
* Complex dependency compilation (BLAS, LAPACK).
* GPU Acceleration using **Nvidia CUDA**.
* Cost-benefit analysis of vertical vs. horizontal scaling in the Cloud.

> **Academic Context:** This study resulted in a scientific paper presented for the *MC038 - Introduction to Scientific Writing* course at the **Institute of Computing, Unicamp**.

---

## Architecture & Complexity

<p align="center">
  <img src="https://github.com/lima-agnaldo/OPM/blob/master/.files/Grid.jpg?raw=true" alt="OPM Simulation Grid" width="400"/>
  <br>
  <em>Figure 1: Visualization of a reservoir simulation grid.</em>
</p>

Compiling scientific software involves managing a complex graph of dependencies. The diagram below illustrates the mathematical libraries required to build the OPM simulator, including solvers for linear algebra equations (BLAS/LAPACK) essential for fluid dynamics.

<p align="center">
  <img src="https://github.com/lima-agnaldo/OPM/blob/master/.files/grafo_libs.jpg?raw=true" alt="Dependency Graph" width="500"/>
  <br>
  <em>Figure 2: Library Dependency Graph for the OPM compilation process.</em>
</p>

---

## Key Findings

The research aimed to establish performance metrics comparing simple single-core machines against multi-core instances and clustered environments.

**Critical insights included:**

* **Vertical vs. Horizontal Scaling:** Contrary to standard expectations, adding more nodes (clustering) actually **increased simulation time** in certain configurations due to network latency overhead.
* **Optimal Configuration:** The most efficient setup (balancing cost, time, and energy) was a **single High-Performance VM** utilizing multiple processing cores, rather than a cluster of smaller machines.
* **Energy Efficiency:** Optimizing the compilation for specific hardware architectures resulted in measurable reductions in energy consumption per simulation job.

---

## Read the Paper

The full methodology, benchmarks, and detailed energy analysis are available in the attached PDF.

> 🎓 **[Read the Full Article (PDF)](https://github.com/agslima/OPM/blob/master/Article-A_Benefit_Study_of_Implementing_a_Reservoir_Simulator_in_Cloud_Computing.pdf)**

---

## Technologies & Tools

* **Simulation Software:** OPM (Open Porous Media)
* **Cloud Provider:** Microsoft Azure (VMs & Clusters)
* **HPC & Compilation:** Nvidia CUDA, CMake, GCC, OpenMPI
* **Math Libraries:** BLAS, LAPACK, Dune
* **OS/Scripting:** Linux (Ubuntu/CentOS), Bash Automation

---

## Author

**Agnaldo Silva Lima**
Computer Science Student @ Unicamp  
[LinkedIn Profile](https://www.linkedin.com/in/agslima)

---

## License

This project is distributed under the **GNU GPLv3** license. See the [LICENSE](./LICENSE) file for more details.

<!-- 
# Projeto de pesquisa
Pesquisa com o objetivo de estudar o Simulador de Reservatório OPM, suas bibliotecas científicas, compilação voltada para aceleração usando GPUs (CUDA) e aplicações na Cloud Azure.

Como resultado de pesquisa, foi possível criar um artigo para disciplina de MC038 - Introdução à Redação Científica no Instituto de Computação da Unicamp. O foco principal do artigo foi o estudo do desempenho do simulador na Cloud levando em conta métricas como consumo energético, tempo e custo benefício.

## Sobre
![image](https://github.com/lima-agnaldo/OPM/blob/master/.files/Grid.jpg?raw=true)
O OPM é um software de Simulação Open Source de modelagem e simulação aplicado a estudos de aquíferos, exploração de campos de petróleo e estocagem de CO2.

O software é capaz de produzir simulações através de modelos e usando diversas bibliotecas científicas, como exemplo, BLAS e LAPACK.
![image](https://github.com/lima-agnaldo/OPM/blob/master/.files/grafo_libs.jpg?raw=true)
O diagrama acima mostra as ligações das bibliotecas no software. Cada uma delas é bastante importante para a compilação do software, algo que pode ser bastante desafiador e complexo.


### Artigos
O principal objetivo do meu artigo é estabelecer uma métrica de desempenho de simulações na Nuvem Azure usando desde máquinas de processadores simples a máquinas com vários núcleos ou Cluster de máquinas. Usando essas métricas, pude chegar ao consumo de energia e estabelecer a relação custo benefício, de tempo e o consumo energético. Obtive resultados bastante interessantes, como o caso onde o tempo de simulação tende a aumentar quando mais máquinas disponíveis ou quando o tempo é drasticamente reduzido quando é utilizado apenas uma máquina, mas com diversos núcleos de processamento. 


# OPM – Simulação Científica em Cloud com Aceleração via GPU

![Language](https://img.shields.io/github/languages/top/agslima/OPM?style=flat-square)
![License](https://img.shields.io/badge/license-GPL--3.0-blue?style=flat-square)
![Status](https://img.shields.io/badge/status-Projeto%20de%20pesquisa-informational?style=flat-square)

---

### Projeto de Pesquisa

Este projeto teve como objetivo estudar o **Simulador de Reservatório OPM** (Open Porous Media), com foco na:

- Estrutura e bibliotecas científicas utilizadas
- Processo de **compilação com aceleração via GPU (CUDA)**
- Execução de simulações em diferentes **ambientes da Azure Cloud**

O estudo resultou na produção de um artigo acadêmico apresentado na disciplina **MC038 - Introdução à Redação Científica**, do Instituto de Computação da **Unicamp**.

---

### Visão Geral

<p align="center">
  <img src="https://github.com/lima-agnaldo/OPM/blob/master/.files/Grid.jpg?raw=true" alt="Simulação OPM" width="600"/>
</p>

O **OPM (Open Porous Media)** é um framework de simulação open source utilizado em estudos científicos de:

- Aquíferos
- Exploração de campos de petróleo
- Estocagem de CO₂

Ele utiliza modelos matemáticos robustos em conjunto com bibliotecas científicas como **BLAS** e **LAPACK** para realizar simulações em larga escala.

<p align="center">
  <img src="https://github.com/lima-agnaldo/OPM/blob/master/.files/grafo_libs.jpg?raw=true" alt="Grafo de Bibliotecas" width="700"/>
</p>

---

### Resultados da Pesquisa

O foco principal do artigo foi **avaliar o desempenho do simulador na Cloud Azure**, considerando métricas como:

- Tempo de execução
- Consumo energético
- Custo-benefício

#### Conclusões obtidas:

- Usar **uma única VM com múltiplos núcleos** resultou em desempenho superior comparado ao uso de múltiplas VMs simples.
- Ambientes com mais máquinas nem sempre geram ganho de performance — podendo inclusive aumentar o tempo total.
- A **relação entre tempo, consumo de energia e custo** pode variar significativamente de acordo com o tipo de instância utilizada.

---

### Artigo

O artigo completo está disponível no repositório e contém análises detalhadas, gráficos e metodologia experimental.  
> *[Artigo](https://github.com/agslima/OPM/blob/master/Article-A_Benefit_Study_of_Implementing_a_Reservoir_Simulator_in_Cloud_Computing.pdf)*

---

### Tecnologias utilizadas

- OPM (Open Porous Media Simulator)
- BLAS / LAPACK
- CMake / GCC
- Nvidia CUDA
- Azure Cloud (VMs, Clusters)
- Linux, bash scripts, medições energéticas via software

---

### Autor

**Agnaldo Silva Lima**  
Estudante de Ciência da Computação – Unicamp  
[LinkedIn](https://www.linkedin.com/in/agslima)

---

### Licença

Este projeto segue a licença **GNU GPLv3**.  
Consulte o arquivo [LICENSE](./LICENSE) para mais informações.
-->
