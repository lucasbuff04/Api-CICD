# 🧪 Automação de Testes de API - Gerenciamento de Usuários

Projeto completo de automação de testes de API para sistema de gerenciamento de usuários, desenvolvido com **Postman/Newman**, com integração CI/CD via **GitHub Actions**.

## 📋 Índice

- [Sobre o Projeto](#sobre-o-projeto)
- [Tecnologias Utilizadas](#tecnologias-utilizadas)
- [Cobertura de Testes](#cobertura-de-testes)
- [Pré-requisitos](#pré-requisitos)
- [Instalação](#instalação)
- [Executando os Testes](#executando-os-testes)
- [Estrutura do Projeto](#estrutura-do-projeto)
- [Casos de Teste](#casos-de-teste)
- [CI/CD Pipeline](#cicd-pipeline)
- [Relatórios](#relatórios)
- [Importar no Postman](#importar-no-postman)
- [Boas Práticas](#boas-práticas)

## 🎯 Sobre o Projeto

Este projeto implementa uma suíte completa de testes automatizados para a API de gerenciamento de usuários da [ServeRest](https://serverest.dev/), cobrindo todos os endpoints CRUD e cenários de autenticação.

### Endpoints Testados

- `POST /login` - Autenticação JWT
- `GET /usuarios` - Listar todos os usuários
- `POST /usuarios` - Criar novo usuário
- `GET /usuarios/{id}` - Buscar usuário por ID
- `PUT /usuarios/{id}` - Atualizar usuário
- `DELETE /usuarios/{id}` - Deletar usuário

## 🚀 Tecnologias Utilizadas

- **[Postman](https://www.postman.com/)** - Plataforma de testes de API
- **[Newman](https://www.npmjs.com/package/newman)** - Runner de linha de comando do Postman
- **[Newman HTML Extra Reporter](https://www.npmjs.com/package/newman-reporter-htmlextra)** - Relatórios HTML avançados
- **[GitHub Actions](https://github.com/features/actions)** - CI/CD
- **Node.js 20+** - Runtime JavaScript

### Por que Postman/Newman?

- ✅ Interface visual intuitiva para criar e testar APIs
- ✅ Scripts de teste em JavaScript com sintaxe simples
- ✅ Execução via linha de comando com Newman
- ✅ Integração fácil com CI/CD
- ✅ Variáveis de ambiente e coleções reutilizáveis
- ✅ Comunidade ativa e documentação extensa

## 📊 Cobertura de Testes

### 100% de Cobertura - 30 Casos de Teste

#### 🔐 Autenticação (5 testes)
- **TC001**: Login com credenciais válidas
- **TC002**: Login com email inválido
- **TC003**: Login com senha inválida
- **TC004**: Login sem email
- **TC005**: Login sem senha

#### ➕ Criação de Usuários (8 testes)
- **TC006**: Criar usuário não administrador
- **TC007**: Criar usuário administrador
- **TC008**: Criar usuário com email duplicado
- **TC009**: Criar usuário sem nome
- **TC010**: Criar usuário sem email
- **TC011**: Criar usuário sem senha
- **TC012**: Criar usuário sem campo administrador
- **TC013**: Criar usuário com email inválido

#### 📖 Leitura de Usuários (6 testes)
- **TC014**: Listar todos os usuários
- **TC015**: Buscar usuário por ID válido
- **TC016**: Buscar usuário por ID inexistente
- **TC017**: Filtrar usuários por nome
- **TC018**: Filtrar usuários por email
- **TC019**: Listar apenas administradores

#### ✏️ Atualização de Usuários (6 testes)
- **TC020**: Atualizar usuário com dados válidos
- **TC021**: Atualizar usuário para administrador
- **TC022**: Atualizar com email duplicado
- **TC023**: Atualizar usuário inexistente
- **TC024**: Atualizar sem nome
- **TC025**: Atualizar com email inválido

#### 🗑️ Exclusão de Usuários (3 testes)
- **TC026**: Deletar usuário existente
- **TC027**: Deletar usuário inexistente
- **TC028**: Verificar exclusão na listagem

#### 🔄 Testes de Integração (2 testes)
- **TC029**: Fluxo CRUD completo
- **TC030**: Validar estrutura de resposta

## 📦 Pré-requisitos

- **Node.js** 18.x ou superior
- **npm** 9.x ou superior
- **Git**
- **Postman** (opcional, para interface visual)

## 🔧 Instalação

### 1. Clone o repositório

\`\`\`bash
git clone https://github.com/lucasbuff04/Api-CICD
cd Api-CICD
\`\`\`

### 2. Instale as dependências

\`\`\`bash
npm install
\`\`\`

## ▶️ Executando os Testes

### Executar todos os testes (com relatórios completos)

\`\`\`bash
npm test
\`\`\`

Este comando executa todos os testes:

### Executar em modo desenvolvimento (apenas console)

\`\`\`bash
npm run test:dev
\`\`\`

### Executar com logs detalhados

\`\`\`bash
npm run test:verbose
\`\`\`

### Executar pasta específica de testes

\`\`\`bash
npm run test:folder "01 - Autenticação"
\`\`\`

### Executar com Newman diretamente

\`\`\`bash
# Todos os testes
newman run postman/collection.json -e postman/environment.json

# Com relatório HTML
newman run postman/collection.json -e postman/environment.json -r htmlextra

# Pasta específica
newman run postman/collection.json -e postman/environment.json --folder "02 - Criar Usuários"
\`\`\`

## 📁 Estrutura do Projeto

\`\`\`
api-test-automation/
├── .github/
│   └── workflows/
│       └── api-tests.yml          # Pipeline CI/CD com Newman
├── postman/
│   ├── collection.json            # Coleção Postman com todos os testes
│   └── environment.json           # Variáveis de ambiente
├── reports/                       # Relatórios gerados (criado automaticamente)
│   ├── html/                      # Relatórios HTML interativos
│   ├── json/                      # Relatórios JSON
│   └── junit/                     # Relatórios JUnit XML
├── package.json                   # Dependências e scripts
└── README.md                      # Documentação
\`\`\`

## 📝 Casos de Teste

### Organização

Os testes estão organizados em 6 pastas principais na coleção Postman:

1. **01 - Autenticação** - Validações de login e JWT
2. **02 - Criar Usuários** - Criação e validações
3. **03 - Listar e Buscar Usuários** - Leitura e filtros
4. **04 - Atualizar Usuários** - Atualização de dados
5. **05 - Deletar Usuários** - Exclusão de registros
6. **06 - Testes de Integração** - Fluxos completos end-to-end

### Estratégia de Testes

- ✅ **Testes positivos**: Validam comportamento esperado
- ❌ **Testes negativos**: Validam tratamento de erros
- 🔄 **Testes de integração**: Validam fluxos completos
- 🧹 **Cleanup automático**: Scripts pre-request criam dados de teste
- 📊 **Validações múltiplas**: Status code, estrutura de resposta, mensagens

### Scripts de Teste

Cada requisição contém:

- **Pre-request Scripts**: Preparam dados de teste (emails aleatórios, nomes, etc.)
- **Test Scripts**: Validam respostas usando Chai assertions
- **Variáveis**: Armazenam dados entre requisições (userId, token, etc.)

Exemplo de teste:

\`\`\`javascript
pm.test('TC001 - Status code é 200', () => {
    pm.response.to.have.status(200);
});

pm.test('TC001 - Resposta contém token', () => {
    const jsonData = pm.response.json();
    pm.expect(jsonData).to.have.property('authorization');
    pm.expect(jsonData.authorization).to.be.a('string');
});
\`\`\`

## 🔄 CI/CD Pipeline

### GitHub Actions

O pipeline é executado automaticamente em:

- ✅ Push para branches `main` e `develop`
- ✅ Pull Requests
- ✅ Diariamente às 9h UTC (agendado)
- ✅ Manualmente via workflow_dispatch

### Etapas do Pipeline

1. **Checkout** - Clona o código
2. **Setup Node.js** - Configura ambiente Node.js 20
3. **Install Dependencies** - Instala Newman e reporters
4. **Create Reports Directory** - Cria estrutura de pastas
5. **Run Newman Tests** - Executa todos os testes
6. **Upload Artifacts** - Salva relatórios (30 dias)
7. **Publish Results** - Publica resultados no PR

### Artefatos Gerados

- 📊 **newman-html-report** - Relatório HTML interativo
- 📈 **newman-json-report** - Dados estruturados em JSON
- 📋 **newman-junit-report** - XML para integração CI/CD

### Visualizar Resultados

Após a execução do pipeline:

1. Acesse a aba **Actions** no GitHub
2. Clique no workflow executado
3. Baixe os artefatos na seção **Artifacts**
4. Abra o arquivo HTML no navegador

## 📊 Relatórios

### Relatório HTML (Recomendado)

O relatório HTML interativo inclui:

- ✅ Dashboard com estatísticas gerais
- 📊 Gráficos de sucesso/falha
- ⏱️ Tempo de execução de cada teste
- 📋 Detalhes completos de requisições/respostas
- 🎨 Interface visual moderna e responsiva

\`\`\`bash
# Após executar os testes
open reports/html/report.html  # macOS
start reports/html/report.html # Windows
xdg-open reports/html/report.html # Linux
\`\`\`

### Relatório JUnit XML

Formato compatível com Jenkins, GitLab CI, Azure DevOps:

\`\`\`
reports/junit/report.xml
\`\`\`

### Relatório JSON

Dados estruturados para análise programática:

\`\`\`
reports/json/report.json
\`\`\`

## 📥 Importar no Postman

### Opção 1: Importar Coleção

1. Abra o Postman
2. Clique em **Import**
3. Selecione o arquivo `postman/collection.json`
4. Importe também `postman/environment.json`
5. Selecione o environment "ServeRest API - Production"

### Opção 2: Executar no Postman

1. Importe a coleção conforme acima
2. Clique com botão direito na coleção
3. Selecione **Run collection**
4. Configure as opções de execução
5. Clique em **Run API Test Automation**

### Editar Testes no Postman

1. Abra qualquer requisição
2. Vá para a aba **Tests**
3. Edite os scripts JavaScript
4. Salve e exporte a coleção atualizada

## 🎯 Boas Práticas Implementadas

### 1. Isolamento de Testes

- Cada teste cria seus próprios dados usando timestamps
- Emails e nomes únicos gerados dinamicamente
- Sem dependências entre testes (exceto fluxos de integração)

### 2. Variáveis de Coleção

- `userId` - ID do usuário criado
- `token` - Token JWT de autenticação
- `randomEmail` - Email gerado aleatoriamente
- `randomName` - Nome gerado aleatoriamente

### 3. Validações Completas

- Status codes HTTP
- Estrutura de resposta JSON
- Mensagens de erro/sucesso
- Tipos de dados
- Tempo de resposta

### 4. Nomenclatura Clara

- IDs de teste (TC001, TC002...)
- Descrições descritivas em português
- Organização lógica em pastas

### 5. Scripts Reutilizáveis

- Pre-request scripts para setup
- Test scripts para validações
- Funções auxiliares em variáveis

### 6. Documentação

- README completo
- Comentários nos scripts
- Exemplos de uso

## 🐛 Debugging

### Ver Logs Detalhados

\`\`\`bash
newman run postman/collection.json -e postman/environment.json --verbose
\`\`\`

### Executar Teste Específico

\`\`\`bash
newman run postman/collection.json -e postman/environment.json --folder "01 - Autenticação"
\`\`\`

### Delay Entre Requisições

\`\`\`bash
newman run postman/collection.json -e postman/environment.json --delay-request 1000
\`\`\`

### Exportar Resultados

\`\`\`bash
newman run postman/collection.json -e postman/environment.json -r cli,json --reporter-json-export output.json
\`\`\`

## 🔧 Configuração Avançada

### Múltiplos Ambientes

Crie arquivos de environment para diferentes ambientes:

\`\`\`bash
postman/
├── environment.json           # Produção
├── environment.dev.json       # Desenvolvimento
└── environment.staging.json   # Staging
\`\`\`

Execute com ambiente específico:

\`\`\`bash
newman run postman/collection.json -e postman/environment.dev.json
\`\`\`

### Integração com Jenkins

\`\`\`groovy
pipeline {
    agent any
    stages {
        stage('API Tests') {
            steps {
                sh 'npm install'
                sh 'npm test'
            }
        }
    }
    post {
        always {
            publishHTML([
                reportDir: 'reports/html',
                reportFiles: 'report.html',
                reportName: 'Newman Test Report'
            ])
            junit 'reports/junit/report.xml'
        }
    }
}
\`\`\`

### Integração com GitLab CI

\`\`\`yaml
api-tests:
  stage: test
  image: node:20
  script:
    - npm install
    - npm test
  artifacts:
    when: always
    paths:
      - reports/
    reports:
      junit: reports/junit/report.xml
\`\`\`

## 📚 Recursos Adicionais

### Documentação Oficial

- [Postman Learning Center](https://learning.postman.com/)
- [Newman Documentation](https://learning.postman.com/docs/running-collections/using-newman-cli/command-line-integration-with-newman/)
- [Chai Assertion Library](https://www.chaijs.com/api/bdd/)
- [ServeRest API Docs](https://serverest.dev/)

### Tutoriais Recomendados

- [Writing Tests in Postman](https://learning.postman.com/docs/writing-scripts/test-scripts/)
- [Using Variables](https://learning.postman.com/docs/sending-requests/variables/)
- [Newman Reporters](https://learning.postman.com/docs/running-collections/using-newman-cli/newman-reporters/)

## 🤝 Contribuindo

1. Fork o projeto
2. Crie uma branch para sua feature (`git checkout -b feature/NovaFeature`)
3. Commit suas mudanças (`git commit -m 'Adiciona nova feature'`)
4. Push para a branch (`git push origin feature/NovaFeature`)
5. Abra um Pull Request

### Adicionando Novos Testes

1. Abra `postman/collection.json`
2. Adicione nova requisição na pasta apropriada
3. Adicione pre-request scripts se necessário
4. Adicione test scripts com validações
5. Teste localmente com Newman
6. Commit e push

## 📄 Licença

Este projeto está sob a licença MIT.

## 👤 Autor

Desenvolvido como parte do desafio de automação de testes de API.

## 📞 Suporte

Para dúvidas ou problemas:

- Abra uma [issue](https://github.com/seu-usuario/api-test-automation/issues)
- Consulte a [documentação do Postman](https://learning.postman.com/)
- Consulte a [documentação da API ServeRest](https://serverest.dev/)

## 🎓 Aprendizados

Este projeto demonstra:

- ✅ Automação completa de testes de API
- ✅ Integração CI/CD com GitHub Actions
- ✅ Geração de relatórios profissionais
- ✅ Boas práticas de teste de software
- ✅ Uso de Postman/Newman para automação
- ✅ Validações completas de API REST
- ✅ Tratamento de cenários positivos e negativos

---
