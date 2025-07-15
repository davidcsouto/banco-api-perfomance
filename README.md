# banco-api-performance

Repositório com testes de performance da aplicação [banco-api](https://github.com/juliodelimas/banco-api), utilizando a ferramenta [k6](https://k6.io/) e scripts escritos em JavaScript.

## 📌 Introdução

Este projeto tem como objetivo medir e avaliar o desempenho da API REST do projeto `banco-api`, utilizando testes de carga e stress. Através do k6, é possível gerar relatórios em tempo real e exportá-los para análise posterior.

## 🧰 Tecnologias utilizadas

- [k6](https://k6.io/) — ferramenta de testes de carga open-source
- JavaScript (ES6) — para definição dos cenários de teste
- Node.js (opcional) — caso deseje utilizar scripts utilitários locais
- Variáveis de ambiente — para configuração dinâmica da base URL e dos relatórios

## 📁 Estrutura do repositório

```
banco-api-performance/
├── fixtures/           # Dados de entrada para os testes (ex: usuários, payloads)
├── helpers/            # Funções utilitárias reutilizáveis para interação com a API
├── tests/              # Contém os cenários de teste específicos para cada funcionalidade da API (ex: login, transferência, etc.)
├── utils/              # Contém funções utilitárias reutilizáveis pelos cenários
├── /config             # Arquivo de configuração de variáveis de ambiente
└── README.md           # Este documento
```

## 🧭 Objetivo de cada grupo de arquivos

- **`fixtures/`**: Dados de entrada para os testes (ex: usuários, payloads)
- **`helpers`**: Funções utilitárias reutilizáveis para interação com a API
- **`tests/`**: Contém os cenários de teste específicos para cada funcionalidade da API (ex: login, transferência, etc.)
- **`utils/`**: Contém funções utilitárias reutilizáveis pelos cenários
- **`config`**: Arquivos de configuração de variáveis de ambiente

## 🛠️ Instalação

1. Instale o [k6](https://k6.io/docs/get-started/installation/) de acordo com seu sistema operacional.
2. Clone o repositório:

   ```bash
   git clone https://github.com/davidcsouto/banco-api-performance.git
   cd banco-api-performance
   ```

## ▶️ Execução dos testes

Antes de executar qualquer teste, é necessário alterar o arquivo `config.local.json` e defina a URL base da API a ser testada:

```json
{
    "baseUrl": "http://localhost:3000"
}
```
> 💡 Essas variáveis serão usadas dinamicamente nos testes para montar as requisições.

### Execução básica

```bash
k6 run tests/login.test.js -e BASE_URL=http://localhost:3000
```

Certifique-se de passar a variável de ambiente `BASE_URL`, caso não esteja usando um `config.local.json` ou uma abordagem de carregamento automático:

### Execução com dashboard em tempo real

```bash
K6_WEB_DASHBOARD=true \
k6 run tests/login.test.js \
-e BASE_URL=http://localhost:3000 \
```

### Exportando o relatório como HTML

```bash
K6_WEB_DASHBOARD=true \
K6_WEB_DASHBOARD_EXPORT=html-report.html \
k6 run tests/login.test.js
-e BASE_URL=http://localhost:3000 \
```

O relatório será salvo com o nome `html-report.html` na raiz do projeto.

---

📌 Sinta-se à vontade para contribuir ou sugerir melhorias!
