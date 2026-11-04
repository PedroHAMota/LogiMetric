LogiMetric: Intelligent Fleet Telemetry & Predictive Maintenance

O LogiMetric é uma plataforma avançada de gestão logística e telemetria invisível. O projeto tem como foco a eliminação do atrito operacional decorrente do fator humano, automatizando a captura de dados de geolocalização e o cálculo de desgaste mecânico de frotas de forma estritamente autônoma.

O Problema e a Solução

Sistemas logísticos tradicionais apresentam falhas críticas ao dependerem da intervenção manual do motorista para iniciar o rastreamento via aplicativo. Esta abordagem não apenas compromete a integridade dos dados coletados, mas também gera potenciais passivos trabalhistas ao invadir a privacidade do colaborador fora do seu turno de trabalho.

O LogiMetric soluciona esta lacuna tecnológica através de uma integração baseada em comunicação Bluetooth/OBD-II:
O aplicativo móvel opera em estado de suspensão (consumo mínimo de bateria). Ao detectar o pareamento físico com o rastreador ou sistema nativo do veículo corporativo, o sistema é ativado e inicia a coleta contínua de coordenadas de alta precisão, transmitindo-as ao servidor central. O término do processo de rastreamento ocorre de maneira imediata e automática assim que o veículo é desligado.

Arquitetura de Dados e Tecnologias

A infraestrutura do sistema foi concebida para suportar alta volumetria de requisições concorrentes e executar cálculos espaciais complexos em tempo real.

Backend e Inteligência (Motor de Desgaste)

Python e Flask: Estrutura de alta performance para o roteamento e processamento de dados massivos de telemetria.

Pydantic: Camada estrita de validação de dados, garantindo que os payloads recebidos estejam em conformidade absoluta com o padrão GeoJSON (Longitude, Latitude).

Worker em Background: Algoritmo dedicado à conversão de pontos individuais de GPS em trajetórias contínuas (LineStrings). Aplica modelos matemáticos que consideram relevo, distância percorrida e variação de velocidade para calcular índices de degradação mecânica.

Banco de Dados (Geoespacial)

MongoDB: Implementação de índices 2dsphere para viabilizar cálculos trigonométricos que consideram a curvatura da Terra.

Operadores Nativos: Utilização de consultas geoespaciais avançadas, como $near (busca por raio) e $geoWithin (intersecção entre trajetos e polígonos delimitadores de centros de distribuição).

Frontend e Mobile

Aplicação Mobile (Coletor): Utilização das APIs nativas de Background Location integradas ao BLE Listener (Bluetooth Low Energy).

Dashboard Gerencial (Web): Interface de controle para monitoramento de KPIs operacionais, visualização espacial da frota e gestão de fila de manutenção preditiva.

Fase Atual do Projeto

Este projeto encontra-se atualmente na fase de Design de Arquitetura e Planejamento.

Prototipação UI/UX: [Inserir Link para o Figma]

Backlog e Especificações Técnicas: [Inserir Link para o Quadro no Jira]

Código-fonte: Início da fase de desenvolvimento previsto para as próximas etapas.

Fluxo de Funcionamento (Pipeline de Dados)

Gatilho de Hardware: O condutor aciona a ignição do veículo (Rádio/OBD-II emite sinal BLE).

Captura (Mobile): A aplicação desperta em background e inicia o registro sequencial de coordenadas GPS.

Validação (API): O servidor Flask recepciona os pacotes de dados, submetendo-os à validação GeoJSON via Pydantic.

Persistência (Database): O MongoDB indexa a localização atualizada no mapeamento global.

Análise e Processamento (Worker): No encerramento do ciclo diário, o sistema calcula a distância real percorrida e atualiza o "Score de Desgaste" do veículo.

Alerta e Decisão (Dashboard): Veículos que atingem o limite técnico de desgaste são automaticamente sinalizados no painel gerencial como "Revisão Necessária".

Autor

Pedro Henrique Amaral da Mota

LinkedIn

GitHub
