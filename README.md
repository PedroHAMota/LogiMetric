# LogiMetric API

> API de Otimização e Gestão de Centros de Distribuição baseada em dados geoespaciais.

## Sobre o Projeto
O **LogiMetric** é um projeto de backend desenhado para otimizar operações logísticas em centros de distribuição. O principal objetivo da aplicação é processar rotas, gerenciar o fluxo de entregas e realizar consultas eficientes de dados geográficos e logísticos para reduzir a latência operacional e auxiliar na tomada de decisões estratégicas.

---

## Tecnologias Planejadas (Tech Stack)
* **Linguagem:** Python 3.10+
* **Framework:** Flask (Arquitetura limpa baseada em rotas e serviços)
* **Banco de Dados:** MongoDB (Ideal para armazenamento flexível de documentos e dados geoespaciais)
* **Validação de Dados:** Pydantic (Garantia de tipagem e integridade dos payloads)

---

## Arquitetura e Modelagem de Dados

O sistema foi estruturado seguindo uma divisão clara de responsabilidades:
1. **Camada de Rotas (Controllers):** Recebe as requisições HTTP e valida os parâmetros iniciais.
2. **Camada de Negócios (Services):** Concentra a lógica de cálculo de rotas e regras de distribuição.
3. **Camada de Dados (Models):** Conecta com o MongoDB para persistência de dados de entregas, armazéns e rotas.

### Exemplo de Estrutura de Pastas:
```text
logimetric-api/
├── src/
│   ├── config/         # Configurações de banco de dados e ambiente
│   ├── models/         # Schemas e validações (Pydantic / MongoDB)
│   ├── routes/         # Endpoints da API (Flask)
│   └── services/       # Regras de negócio e lógica de otimização
├── .env.example        # Exemplo de variáveis de ambiente
├── requirements.txt    # Dependências do projeto
└── README.md
```
Próximos Passos do Desenvolvimento

[x] Concepção da arquitetura e definição da stack tecnológica.

[ ] Modelagem inicial das coleções no MongoDB.

[ ] Implementação dos endpoints principais em Flask.

[ ] Documentação da API (Swagger/OpenAPI).


Como rodar o projeto localmente (Em breve)

1 - Clone o repositório:

```
git clone https://github.com/PedroHAMota/logimetric.git
cd logimetric-api
```

2 - Instale as dependências
```
pip install -r requirements.txt
```

3 - Configure as variáveis de ambiente baseado no ```env.exemple```
