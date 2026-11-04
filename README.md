# LogiMetric: Intelligent Fleet Telemetry & Predictive Maintenance

![Status](https://img.shields.io/badge/Status-Em_Desenvolvimento-yellow)
![Python](https://img.shields.io/badge/Python-3.11+-blue?logo=python&logoColor=white)
![Flask](https://img.shields.io/badge/Flask-Backend-black?logo=flask)
![MongoDB](https://img.shields.io/badge/MongoDB-GeoSpatial-47A248?logo=mongodb&logoColor=white)
![Figma](https://img.shields.io/badge/Figma-Prototipagem-F24E1E?logo=figma&logoColor=white)

> O LogiMetric é uma plataforma avançada de gestão logística e telemetria invisível. O projeto foca na eliminação de atrito operacional (fator humano) ao capturar dados de geolocalização e calcular o desgaste mecânico de frotas de forma 100% autônoma.

---

##  O Problema e a Solução

Sistemas tradicionais de logística falham quando dependem que o motorista abra um aplicativo e inicie manualmente a rota. Além de gerar falhas de dados, isso invade a privacidade do colaborador fora do horário de trabalho.

O **LogiMetric** resolve isso através de um **"Aperto de Mão via Bluetooth/OBD-II"**:
O aplicativo móvel permanece adormecido (consumo zero de bateria). Ao detectar a conexão física com o rastreador ou rádio do caminhão, o sistema desperta, inicia a coleta de coordenadas de alta precisão e as envia para o backend. Ao desligar o veículo, o rastreio cessa imediatamente.

---

##  Arquitetura de Dados e Tecnologias

A base do sistema foi arquitetada para suportar alta volumetria de requisições e cálculos espaciais em tempo real.

### Backend & Inteligência (Motor de Desgaste)
*   **Python + Flask:** Estrutura ágil para o roteamento e recebimento massivo de *pings* de telemetria.
*   **Pydantic:** Alfândega de dados estrita, garantindo a conversão de *payloads* perfeitamente alinhados ao padrão GeoJSON (Longitude, Latitude).
*   **Worker em Background:** Algoritmo que converte pontos de GPS individuais em trajetórias (`LineStrings`) e aplica multiplicadores matemáticos baseados em relevo, distância e velocidade para prever a degradação mecânica.

### Banco de Dados (Geoespacial)
*   **MongoDB:** Utilização de índices `2dsphere` para viabilizar cálculos matemáticos considerando a curvatura esférica da terra.
*   **Operadores Nativos:** Uso intensivo de consultas como `$near` (raios de distância) e `$geoWithin` (intersecção entre trajetos e polígonos de centros de distribuição).

### Frontend & Mobile
*   **App Mobile (Coletor):** Background Location API + BLE Listener (Bluetooth Low Energy).
*   **Dashboard Gestor (Web):** Painel de controle para acompanhamento de KPIs logísticos, mapa interativo de frota e tabela crítica de manutenções preditivas.

---

## Fase Atual do Projeto

Este projeto está atualmente na fase de **Design de Arquitetura e Planejamento**.
*   **Prototipação UI/UX:** [Link para o Figma]
*   **Backlog e Tarefas:** [Link para o Quadro no Jira]
*   **Código-fonte:** (Início do desenvolvimento em breve)

---

##  Fluxo de Funcionamento (Pipeline de Dados)

1.  **Hardware Gatilho:** Motorista liga o caminhão (Rádio/OBD-II emite sinal BLE).
2.  **Captura (Mobile):** App desperta em *background* e coleta arrays de coordenadas GPS.
3.  **Validação (API):** Flask recebe o pacote e Pydantic valida o GeoJSON estrito.
4.  **Persistência (DB):** MongoDB indexa a localização atual no mapa global.
5.  **Análise (Worker):** Ao fim do dia, o sistema calcula a distância real percorrida e gera o "Score de Desgaste".
6.  **Alerta (Dashboard):** Caminhões que ultrapassam o limite de desgaste aparecem no painel do gestor como "Revisão Necessária".

---

##  Autor

**Pedro Henrique Amaral da Mota**
*   [LinkedIn](https://www.linkedin.com/in/pedro-amaral-mota/)
*   [GitHub](https://github.com/PedroHAMota)
