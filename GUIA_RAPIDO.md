# 🚀 Guia Rápido - Automação de Testes de API

## Instalação Rápida

\`\`\`bash
# Clone o repositório
git clone https://github.com/lucasbuff04/Api-CICD
cd Api-CICD

# Instale as dependências
npm install

# Execute os testes
npm test
\`\`\`

## Comandos Principais

| Comando | Descrição |
|---------|-----------|
| `npm test` | Executa todos os testes com relatórios completos |
| `npm run test:dev` | Executa testes apenas no console |
| `npm run test:verbose` | Executa com logs detalhados |

## Estrutura de Arquivos

\`\`\`
postman/
├── collection.json      # Todos os 30 testes
└── environment.json     # URL base da API

reports/                 # Gerado após execução
├── html/               # Relatório visual
├── json/               # Dados estruturados
└── junit/              # Para CI/CD
\`\`\`

## Ver Relatórios

Após executar `npm test`:

\`\`\`bash
# macOS
open reports/html/report.html

# Windows
start reports/html/report.html

# Linux
xdg-open reports/html/report.html
\`\`\`

## Importar no Postman

1. Abra o Postman
2. Clique em **Import**
3. Selecione `postman/collection.json`
4. Importe também `postman/environment.json`
5. Pronto! Execute manualmente ou via Newman

## Casos de Teste

### 30 Testes Organizados em 6 Categorias:

1. **Autenticação** (5 testes) - Login e validações
2. **Criar Usuários** (8 testes) - POST com validações
3. **Listar Usuários** (6 testes) - GET e filtros
4. **Atualizar Usuários** (6 testes) - PUT com validações
5. **Deletar Usuários** (3 testes) - DELETE
6. **Integração** (2 testes) - Fluxos completos

## Executar Testes Específicos

\`\`\`bash
# Apenas autenticação
newman run postman/collection.json -e postman/environment.json --folder "01 - Autenticação"

# Apenas criação
newman run postman/collection.json -e postman/environment.json --folder "02 - Criar Usuários"
\`\`\`

## CI/CD

O projeto já está configurado com GitHub Actions:

- ✅ Execução automática em push/PR
- ✅ Execução diária às 9h UTC
- ✅ Relatórios salvos como artefatos
- ✅ Resultados publicados em PRs

## Troubleshooting

### Erro: "newman: command not found"

\`\`\`bash
npm install
\`\`\`

### Erro: "Cannot find module 'newman'"

\`\`\`bash
npm install newman --save-dev
\`\`\`

### Testes falhando

1. Verifique conexão com internet
2. Confirme que https://serverest.dev está acessível
3. Execute com `--verbose` para ver detalhes

\`\`\`bash
npm run test:verbose
\`\`\`

## Próximos Passos

1. ✅ Execute os testes localmente
2. ✅ Importe no Postman para explorar
3. ✅ Faça push para GitHub e veja o CI/CD
4. ✅ Customize os testes conforme necessário

## Recursos

- [README Completo](README.md)
- [Documentação Postman](https://learning.postman.com/)
- [Documentação Newman](https://learning.postman.com/docs/running-collections/using-newman-cli/command-line-integration-with-newman/)
- [API ServeRest](https://serverest.dev/)

---
