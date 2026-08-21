# Simulação de Rede Hierárquica LAN (Cisco Packet Tracer)

Este repositório contém o projeto e a documentação para a **Avaliação 04 - Prática de Simulação de Ambiente Hierárquico**, desenvolvida para a disciplina de **Comutação de Redes Locais** do curso Superior de Tecnologia em Redes de Computadores do **Instituto Federal de Rondônia (IFRO)**.

---

## 📌 Visão Geral do Projeto

O objetivo desta atividade é projetar a topologia física de uma rede local (LAN) utilizando o modelo de três camadas (*Core*, *Distribution* e *Access/Acesso*), garantindo conceitos de **escalabilidade**, **hierarquia**, **redundância** e **disponibilidade**, alinhados aos padrões IEEE 802.3.

Além dos requisitos físicos exigidos, **foi implementada a configuração de endereçamento IP e testes de conectividade**, garantindo comunicação funcional entre os dispositivos da rede (item Bônus/Extra).

---

## 🗺️ Diagrama da Topologia

Aqui está a simulação exata desenvolvida no Cisco Packet Tracer:

![Topologia da Rede](image_eb86b4.png)

*Figura 1: Topologia lógica e física implementada no Cisco Packet Tracer.*

---

## 🏗️ Arquitetura da Rede (Modelo em 3 Camadas)

A arquitetura foi organizada respeitando a divisão hierárquica recomendada pela Cisco e os padrões IEEE 802.3 (FastEthernet, GigabitEthernet e Fibra Óptica):

### 1. Camada Roteamento / Saída
* **1x Roteador Cisco 1941 (`Router1`)**:
  * Possui 2 interfaces FastEthernet conectadas individualmente a cada um dos dois switches de núcleo (`Multilayer Switch2` e `Multilayer Switch0`).

### 2. Camada de Núcleo (Core Layer)
* **2x Switches Multicamada (`Multilayer Switch2` e `Multilayer Switch0`)**:
  * **Ligação entre Switches de Núcleo**: Conexão física com **4 links de 1 Gbps (GigabitEthernet)** estruturada e preparada para futura agregação de links (**Link Aggregation / EtherChannel de 4 Gbps**).
  * **Conexão com a Distribuição**: Conectados por enlaces de **Fibra Óptica** (2 links por switch de distribuição) preparados para futuro **Link Aggregation de 2 Gbps**.

### 3. Camada de Distribuição (Distribution Layer)
* **2x Switches Multicamada (`Multilayer Switch3` e `Multilayer Switch1`)**:
  * Conectados de forma cruzada aos switches de núcleo via fibra óptica para redundância física.
  * Interligam a camada de núcleo aos switches de borda/acesso.

### 4. Camada de Acesso / Borda (Access Layer)
* **4x Switches de Acesso (`Switch13`, `Switch14`, `Switch15`, `Switch16` - Modelo 2950-24)**:
  * Conectados diretamente aos switches de distribuição.
  * Sem recursos de redundância, provendo conectividade direta aos dispositivos finais.

### 5. Dispositivos Finais (End Devices)
* **4x Desktops (PCs)**: `PC0`, `PC1`, `PC2`, `PC3` (conectados aos switches de acesso `Switch13` e `Switch14`).
* **4x Notebooks (Laptops)**: `Laptop0`, `Laptop1`, `Laptop2`, `Laptop3` (conectados aos switches `Switch15` e `Switch16`).
* **1x Servidor (`Server0`)**: Conectado ao switch de acesso `Switch16`.

---

## 🌐 Endereçamento IP e Testes de Conectividade (Atividade Extra - +10%)

Conforme facultado no roteiro da atividade, foi realizada a atribuição de endereços IP estáticos para validação da conectividade total da rede.

* **Rede/Máscara de Sub-rede**: `192.168.1.0/24` (Máscara: `255.255.255.0`)

### Tabela de Endereçamento IP

| Dispositivo | Tipo | Interface | Endereço IP | Máscara de Sub-rede | Status do Teste (Ping) |
| :--- | :--- | :--- | :--- | :--- | :---: |
| **PC0** | Desktop | FastEthernet0 | `192.168.1.1` | `255.255.255.0` | ✅ Sucesso |
| **PC1** | Desktop | FastEthernet0 | `192.168.1.2` | `255.255.255.0` | ✅ Sucesso |
| **PC2** | Desktop | FastEthernet0 | `192.168.1.3` | `255.255.255.0` | ✅ Sucesso |
| **PC3** | Desktop | FastEthernet0 | `192.168.1.4` | `255.255.255.0` | ✅ Sucesso |
| **Laptop0** | Notebook | FastEthernet0 | `192.168.1.5` | `255.255.255.0` | ✅ Sucesso |
| **Laptop1** | Notebook | FastEthernet0 | `192.168.1.6` | `255.255.255.0` | ✅ Sucesso |
| **Laptop2** | Notebook | FastEthernet0 | `192.168.1.7` | `255.255.255.0` | ✅ Sucesso |
| **Laptop3** | Notebook | FastEthernet0 | `192.168.1.8` | `255.255.255.0` | ✅ Sucesso |
| **Server0** | Servidor | FastEthernet0 | `192.168.1.9` | `255.255.255.0` | ✅ Sucesso |

### Testes de Comunicação
* Foram efetuados testes de ping entre todos os dispositivos da camada de acesso e o servidor (`Server0`).
* **Resultado**: 100% dos pacotes foram entregues com sucesso, confirmando que as conexões físicas entre as camadas de Núcleo, Distribuição e Acesso estão corretamente operacionais.

---

## 📋 Resumo dos Requisitos Atendidos

| Requisito do Roteiro | Status | Descrição |
| :--- | :---: | :--- |
| Estrutura Hierárquica Visível (Núcleo, Distribuição e Borda) | ✅ | Organizado em níveis claros no Packet Tracer. |
| Roteador conectado a dois switches por FastEthernet | ✅ | `Router1` conectado com 2 links individuais. |
| Ligação física para Link Aggregation de 4Gbps no Núcleo | ✅ | 4 cabos GigabitEthernet interligando os switches de núcleo. |
| Ligação por Fibra Óptica (Link Aggregation 2Gbps) Core-Distribuição | ✅ | Enlaces de fibra óptica interligando as camadas. |
| 4 Switches de Borda sem redundância | ✅ | Switches 2950-24 interligando os clientes finais. |
| Dispositivos finais (4 PCs, 4 Laptops, 1 Servidor) | ✅ | Todos os 9 dispositivos finais conectados com cabo. |
| **Bônus**: Endereçamento IP e Teste via `ping` (+10%) | ✅ | IPs `192.168.1.1` a `192.168.1.9/24` configurados e validados. |

---

## 📂 Arquivos no Repositório

* `README.md`: Documentação detalhada do projeto.
* `topologia_hierarquica.pkt`: Arquivo de projeto executável do Cisco Packet Tracer.
* `image_eb86b4.png`: Print do diagrama de topologia exibido acima no repositório.

---

## 👤 Autor

* **Aluno**: [Seu Nome Aqui]
* **Curso**: CST em Redes de Computadores
* **Instituição**: Instituto Federal de Rondônia (IFRO)
* **Disciplina**: Comutação de Redes Locais
