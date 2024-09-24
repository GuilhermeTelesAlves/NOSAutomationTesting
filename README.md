1. Escolher uma ferramenta para automatizar testes à seguinte Api REST, explica o porquê dessa escolha. https://gorest.co.in/
  
   Para este caso a minha escolha seria a ferramenta de **Postman** pelas seguintes razões:

   1.1 - **Interface amigável e intuitiva:** O Postman tem uma interface gráfica que facilita a criação, envio e teste de requisições API, o que é mais simples em comparação a escrever código manualmente para testar endpoints.
        
   1.2 - **Suporte a múltiplos tipos de requisição:** Ele suporta todos os principais métodos HTTP como GET, POST, PUT, DELETE, PATCH, etc., permitindo que os desenvolvedores testem diversos tipos de operações numa API.
        
   1.3 - **Facilidade na gestão de coleções de requisições:** No Postman, é possível organizar requisições em coleções e pastas, facilitando a reutilização de testes e a organização de fluxos de trabalho para diferentes APIs ou                      projetos.
        
   1.4 - **Testes automatizados:** Postman permite escrever scripts de teste em JavaScript que podem validar a resposta da API automatizada. Isso facilita a verificação de dados, status HTTP, cabeçalhos, etc.
        
   1.5 - **Ambientes configuráveis:** É possível criar múltiplos ambientes (desenvolvimento, produção, teste) com variáveis específicas, tornando mais fácil alternar entre diferentes contextos sem precisar mudar URLs e parâmetros                       manualmente.
        
   1.6 - **Suporte a autenticação:** O Postman facilita os testes de APIs seguras com suporte para diversos métodos de autenticação, como OAuth 2.0, JWT (JSON Web Tokens), Basic Auth, API Key, entre outros.
        
   1.7 - **Documentação automática:** O Postman pode gerar documentação das APIs a partir das requisições e respostas, o que agiliza a comunicação entre equipas e a criação de documentação técnica.
        
   1.8 - **Testes colaborativos:** Em equipas, é possível compartilhar coleções, ambientes e até realizar testes colaborativos, o que facilita o trabalho conjunto no desenvolvimento e depuração de APIs.
        
   1.9 - **Simulação de APIs (Mock servers)**: Permite simular APIs, criando respostas simuladas para endpoints que ainda não foram implementados, o que ajuda no desenvolvimento paralelo entre equipes de frontend e backend.
        
   Esses factores combinados tornam o Postman numa ferramenta robusta e acessível para desenvolvedores, testers e outros profissionais que trabalham com APIs.

2. Explica os use case de teste:

   **2.1. Teste de Requisição Básica (Happy Path)**
   
    **Objetivo**: Validar se a API responde corretamente a uma requisição simples e dentro das expectativas.
   
    **Cenário**: O cliente envia uma requisição válida, com parâmetros e headers corretos, e recebe a resposta esperada (geralmente um código de _status 200_).
   
    **Exemplo:**
   
    Enviar um GET para o endpoint /users/123 e receber um _status 200 OK_ com os dados do usuário.
   
   **2.2. Teste de Autenticação e Autorização**
   
    **Objetivo**: Garantir que a API responde corretamente a requisições autenticadas e verifica as permissões de acesso.
   
    **Cenário**: Verificar se o sistema responde corretamente a usuários autenticados, e se os usuários não autorizados recebem um erro.
   
    **Exemplo:**
   
    Tentar acessar /admin/reports sem um token de autenticação deve retornar _401 Unauthorized_.
   
    Enviar uma requisição com um token inválido ou expirado deve retornar _403 Forbidden_.
   
    **2.3. Teste de Limites (Boundary Testing)**
   
    **Objetivo**: Verificar como a API lida com valores nos limites superiores e inferiores dos parâmetros.
   
    **Cenário**: Enviar valores no limite máximo ou mínimo permitido.
   
    **Exemplo:**
   
    Enviar um ID de usuário com o maior valor possível, como 999999999, ou valores no mínimo permitido, como 0, e verificar a resposta.
   
   **2.4. Teste de Requisições Inválidas**
   
    **Objetivo**: Validar se a API trata adequadamente de requisições com dados incorretos.
   
    **Cenário**: Enviar requisições com parâmetros inválidos, como tipos de dados errados.
   
    **Exemplo:**
   
    Enviar um POST para /createUser com o campo de e-mail em branco e verificar se a API retorna _400 Bad Request_ com uma mensagem de erro.
   
    **2.5. Teste de Performance e Carga**
   
    **Objetivo**: Avaliar o desempenho da API em cenários de alta demanda e sua capacidade de resposta sob carga.
   
    **Cenário**: Simular múltiplas requisições simultâneas para verificar o tempo de resposta e o comportamento da API.
   
    **Exemplo:**
   
    Enviar 1.000 requisições para o _endpoint/orders_  num curto período de tempo e monitorar o tempo médio de resposta e erros como _503 Service Unavailable_.
   
    **2.6. Teste de Integração**
   
    **Objetivo**: Testar a interação entre múltiplos sistemas ou componentes que utilizam a API.
   
    **Cenário**: Verificar se a API interage corretamente com outras APIs, bancos de dados, ou serviços externos.
   
    **Exemplo:**
   
    Um endpoint que deve buscar dados de uma API externa retorna corretamente os dados esperados, ou como a API interna responde quando o serviço externo está fora do ar.
   
    **2.7. Teste de Conformidade com o Esquema**
   
    **Objetivo**: Garantir que os dados retornados pela API estejam no formato correto (JSON, XML) e que o esquema esperado esteja sendo respeitado.
   
    **Cenário**: Verificar se todos os campos obrigatórios estão presentes e no formato adequado.
   
    **Exemplo:**
   
    O campo "user_id" deve ser do tipo _integer_ e o email deve estar em formato de _string_ válida.
   
    **2.8. Teste de Paginação**
   
    **Objetivo**: Verificar se a API implementa corretamente a paginação quando há grandes volumes de dados.
   
    **Cenário**: Testar o comportamento da API ao retornar listas de dados paginadas, verificando os limites de página e o número de itens por página.
   
    **Exemplo:**
   
    Enviar uma requisição para /products?page=2&limit=10 e garantir que a API retorna os itens corretos para a segunda página.
   
    **2.9. Teste de Segurança**
   
    **Objetivo**: Avaliar a resistência da API contra ameaças de segurança comuns, como ataques de injeção SQL, Cross-Site Scripting (XSS), etc.
   
    **Cenário**: Enviar entradas maliciosas para endpoints que interagem com bancos de dados ou sistemas externos.
   
    **Exemplo:**
   
    Testar o envio de scripts maliciosos em campos de input para verificar se a API responde com validação adequada ou sanitização.
   
    **2.10. Teste de Timeout e Limites de Conexão**
   
    **Objetivo**: Verificar como a API lida com requisições lentas ou quando o tempo de resposta de um servidor externo é maior que o esperado.
   
    **Cenário**: Simular uma conexão lenta ou travada e verificar o comportamento da API, como tempo limite de resposta.
   
    **Exemplo:**
   
    Testar como a API responde se um banco de dados ou serviço externo leva muito tempo para responder, retornando um _timeout_ (_504 Gateway Timeout_).


    **2.11. Testes Funcionais**

    **2.11.1. Criação de novos usuários:**
    
    **Descrição do caso**: Verificar a criação de um novo usuário.
    
    **Cenários de teste:**
    
    a) Criar um usuário com todos os campos obrigatórios preenchidos corretamente.
    
    b) Criar um usuário com campos opcionais adicionais.
    
    c) Tentar criar um usuário com dados inválidos (ex.: e-mail inválido, nome vazio)
    
    d) Criar um usuário com um e-mail já existente para verificar o comportamento do erro.

    **2.11.2. Obter informações de um usuário:**
    
    **Descrição do caso:** Verificar a recuperação dos dados de um usuário específico.
    
    **Cenários de teste:**
    
    a) Atualizar um ou mais campos de um usuário existente.
    
    b) Tentar atualizar um usuário com dados inválidos.
    
    c) Atualizar um usuário inexistente e verificar o comportamento do erro.

    **2.11.3. Excluir um usuário:**
    
    **Descrição do caso:** Verificar a exclusão de um usuário.
    
    **Cenários de teste:**
    
    a) Excluir um usuário existente.
    
    b) Tentar excluir um usuário inexistente e verificar o comportamento do erro.

    **2.11.4. Criar uma Nova Tarefa:**

    **Descrição do caso:** Verificar a criação de uma nova tarefa.
    
    **Cenários de Teste:**
    
    a) Criar uma tarefa com todos os campos obrigatórios preenchidos.
    
    b) Criar uma tarefa com dados inválidos.
    
    c) Criar uma tarefa associada a um usuário inexistente e verificar o comportamento de erro.

    **2.11.5. Obter Tarefas:**
    
    Descrição do caso: Verificar a recuperação de tarefas.
    
    **Cenários de Teste:**
    
    a) Obter todas as tarefas.
    
    b) Obter tarefas de um usuário específico.
    
    c) Obter tarefas com filtros aplicados (ex.: por status).

    **2.11.6. Atualizar uma Tarefa:**
    
    **Descrição do caso:** Verificar a atualização de uma tarefa.
    
    **Cenários de Teste:**
    
    a) Atualizar uma tarefa existente.
    
    b) Atualizar uma tarefa com dados inválidos.
    
    c) Tentar atualizar uma tarefa inexistente e verificar o comportamento de erro.

    **2.11.7. Excluir uma Tarefa:**
    
    **Descrição**: Verificar a exclusão de uma tarefa.
    
    **Cenários de Teste**:
    
    a) Excluir uma tarefa existente.
    
    b) Tentar excluir uma tarefa inexistente e verificar o comportamento de erro.

    Ao seguirmos estes casos de uso de teste, serão garantidas as coberturas das funcionalidades da API GoREST, validando os cenários de sucesso, cenários de erro e _edge case_.

3. Em automação, com resposta desta API gorest.co.in/public/v2/todos

    3.1. Aplica uma validação de schema ao resultado

    3.2. Valida se todos os resultados têm status completed

    3.3. Interpreta e valida o valor “due_on”
   
    Para realizar automação e validação de respostas da **API GoREST** para o endpoint '/public/v2/todos', pode-se utilizar o Postman junto com o Newman para executar os testes automatizados.

    Para a validação do schema utilizarei a biblioteca 'tv4' no Postman para validar o schema.

 # Configuração no Postman para implementar estas validações:

  1. Criar um nova coleção no Postman e adicionar um nova request para GET /public/v2/todos
   
  2. Adicionar os seguintes scripts na tab testes da request:

    // Import the tv4 library for JSON schema validation
      const tv4 = require('tv4');
  
    // Define the expected schema for the response
    const schema = {
      "type": "array",
      "items": {
          "type": "object",
          "properties": {
              "id": {"type": "integer"},
              "user_id": {"type": "integer"},
              "title": {"type": "string"},
              "due_on": {"type": "string", "format": "date-time"},
              "status": {"type": "string"}
          },
          "required": ["id", "user_id", "title", "due_on", "status"]
      }
    };
  
    // Validate the response schema
    pm.test("Schema is valid", function() {
      const result = tv4.validateMultiple(pm.response.json(), schema);
      pm.expect(result.valid).to.be.true;
      if (!result.valid) {
          console.log(result.errors);
      }
    });
  
    // Validate all todos have status 'completed'
    pm.test("All todos have status 'completed'", function() {
      const todos = pm.response.json();
      todos.forEach(todo => {
          pm.expect(todo.status).to.eql('completed');
      });
    });
  
    // Validate the 'due_on' field
    pm.test("All todos have a valid 'due_on' date", function() {
      const todos = pm.response.json();
      todos.forEach(todo => {
          pm.expect(new Date(todo.due_on).toString()).not.to.equal('Invalid Date');
      });
    }); 

  # Configurações do Newman:

  Para executar os testes num ambiente CI/CD, usa-se o Newman, a CLI do Postman. 

  Primeiro exporta-se a coleção do Postman para um ficheiro .JSON e depois usamos o Newman para executar a coleção.

  **Passos:**
  
  1. Exportar a colection do Postman:

      1.1. No Postman, clicar com o botão direito na coleção e seleccionar "Export";
      
      1.2. Salvar o arquivo JSON da coleção.
  
  2. Instalar o Newman:

     Instalar o mesmo usando npm:

         npm install -g newman
  
  3. Executar a coleção exportada:
  
          newman run <path_to_exported_collection.json>
  
  4. Publicar a mesma no repositório GitHub
  
          Adicionamos o arquivo .JSON da coleção exportada e um arquivo README.md como este a explicar a execução dos testes e publica-se o código no repositório.


## Conteúdo do README.md

    **GoREST API Tests**
    
    Este repositório contém testes automatizados para o endpoint '/public/v2/todos' da API GoREST.
    
    **Configuração**
    
    1. Instalar o [Postman](https://www.postman.com/) se ainda não o fez.
    2. Instalar o [Newman](https://github.com/postmanlabs/newman) globalmente:
       ```sh
      npm install -g newman

## Agora executam-se os testes:

**Clone do repositório:**

    git clone https://github.com/<seu-usuario>/gorest-api-tests.git
    
    cd gorest-api-tests

**Execução de testes com o Newman:**

    newman run collections/GoREST_Todo_Tests.postman_collection.json

**Testes incluídos:**

  - Validação do Schema da resposta
  
  - Verificação se todos têm o _status completed_.
  
  - Validação do campo _due_on_ para garantir que seja uma data válida.

4. DevOps, CI/CD.

4.1. Explica e justifica uma implementação de testes de carga a esta API:

Os testes de carga são cruciais para garantir que a **API GoREST** possa lidar com um alto volume de solicitações em simultâneo sem comprometer a performance e a sua funcionalidade. 
A implementação de testes de carga permite identificar e prever o comportamento sob diferentes níveis de tráfego e melhorar a escalibilidade.

## Passos para Implementação:

**Configuração do Teste:**

  **Definir Objetivos**: Estabelecer métricas como tempo de resposta, taxa de transferência e número máximo de usuários em simultâneos.
  
  **Cenários de Teste**: Criar cenários que simulem operações comuns na API, como criação, leitura, atualização e exclusão de usuários e tarefas.

**Desenvolvimento do Script de Teste:**

**Ferramenta Escolhida**: Configurar scripts em JMeter, Gatling ou Artillery.

**Simulação de Usuários**: Definir diferentes perfis de usuários e simular as interações com a API.

**Validação de Respostas**: Incluir verificações para garantir que as respostas da API estejam correctas.

**Execução do Testes:**

**Ambiente de Teste**: Realizar os testes num ambiente de _staging_ que seja representativo no ambiente de produção.

**Aumento Gradual de Carga**: Iniciar com uma carga leve e aumentar gradualmente até atingir ou ultrapassar a carga esperada em produção.

**Análise dos Resultados:**

**Identificação de Gargalos:** Analisar métricas e relatórios para identificar pontos de falha ou degradação de desempenho.

**Ajustes Necessários:** Fazer ajustes na API ou na infraestrutura com base nos resultados dos testes.

**Justificativa:**

Os testes de carga são essenciais para garantir que a **API GoREST** possa suportar o tráfego esperado em produção, identificando e mitigando riscos antes que eles impactem os usuários finais.

4.2. Como implementarias uma solução de Continuous Testing, justifica;

  Continuous Testing (CT) integra os testes automáticos em todas as fases do ciclo de desenvolvimento, proporcionando feedback contínuo e garantindo a qualidade desde o início do desenvolvimento até a produção. Esta abordagem é vital para manter a qualidade e a confiabilidade do _software_ num ambiente de desenvolvimento ágil e DevOps.

## Passos para Implementação:

**Configuração do Pipeline de CI/CD:**

**Repositório de Código:** Configurar um repositório Git para o código-fonte e scripts de teste.

**Pipeline de Integração Contínua:** Configurar um pipeline de CI para executar testes unitários, de integração e de API a cada commit.

**Integração de Testes Automáticos:**

**Testes Unitários:** Executar testes unitários em cada build para validar a lógica do código.

**Testes de Integração:** Verificar a interação entre diferentes módulos e serviços.

**Testes de API:** Utilizar ferramentas como Postman/Newman para executar testes de API automatizados.

**Testes de Carga e Desempenho:**

**Integração de Scripts de Teste de Carga:** Configurar scripts de testes de carga (JMeter, Gatling, Artillery) no pipeline para execução periódica.

**Monitorizamento Contínuo:** Utilizar ferramentas como _Grafana_ e _Prometheus_ para monitorar métricas de desempenho em tempo real.

**Ambientes de Staging e Produção:** Ambiente de Staging: Implementar testes automãticos num ambiente de _staging_ antes de passar para produção.

**Deploy Automático**: Automatizar o deploy para produção somente após a aprovação dos testes em _staging_.

**Monitoramento e Feedback:** 

**Monitorização Contínua:** Utilizar ferramentas de monitorização para observar o desempenho da API em produção.

**Feedback Rápido:** Configurar notificações para alertar a equipa sobre falhas de desempenho.

**Justificativa:** A implementação de _Continuous Testing_ garante feedback contínuo e rápido sobre a qualidade do software, permitindo que a equipa identifique e resolva problemas rapidamente. Isso melhora a eficiência, reduz o tempo de lançamento e aumenta a confiabilidade do software, proporcionando uma experiência melhor ao usuário final e mais consistente.
