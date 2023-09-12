# Requisitos

## **Requisitos Funcionais:**

### **Telas e Funções Gerais:**

1. **Visualização das Informações em Tabelas:**
    - Os usuários devem ser capazes de visualizar informações em tabelas de forma organizada e legível.
    - As tabelas devem apresentar dados relevantes, como funcionários, cargos, operações, etc.
2. **Campo de Busca:**
    - Cada tela de visualização deve conter um campo de busca para permitir aos usuários encontrar informações específicas nas tabelas.
    - O campo de busca deve realizar buscas em tempo real enquanto o usuário digita.
3. **Tela de Login:**
    - Uma tela de login segura deve ser fornecida para autenticação dos usuários.
    - Deve haver campos para inserir nome de usuário (ou email) e senha.
4. **Menu de Acesso:**
    - Deve existir um menu de acesso que varie de acordo com o perfil do usuário.
    - O menu deve exibir opções de acordo com as permissões atribuídas ao perfil.
5. **CRUD para Perfil:**
    - Os administradores devem poder criar, ler, atualizar e excluir perfis de usuário.
6. **CRUD para Estabelecimento:**
    - Os administradores devem poder criar, ler, atualizar e excluir informações sobre estabelecimentos.
7. **CRUD para Cargo:**
    - Os administradores devem poder criar, ler, atualizar e excluir informações sobre cargos.
8. **CRUD para Operações Disponíveis:**
    - Os administradores devem poder gerenciar as operações disponíveis, que podem ser atribuídas aos funcionários.
9. **CRUD para Operações:**
    - Os administradores devem poder criar, ler, atualizar e excluir informações sobre operações específicas.
10. **CRUD para Funcionários:**
    - Os administradores devem poder criar, ler, atualizar e excluir informações sobre funcionários.
11. **CRUD para Vincular Cargos a Funcionários:**
    - Os administradores devem poder associar cargos a funcionários específicos.
12. **CRUD para Vincular Operações a Funcionários:**
    - Os administradores devem poder atribuir operações específicas a funcionários.
13. **CRUD para Geração de Holerites:**
    - Os administradores devem poder criar, ler, atualizar e excluir holerites para os funcionários.
14. **CRUD para Geração da Folha de Pagamento:**
    - Os administradores devem poder gerar a folha de pagamento com base nos dados dos funcionários e seus holerites.
15. **Dispositivos Web e Mobile para Colaboradores:**
    - Os colaboradores devem ser capazes de acessar seus holerites por meio de dispositivos web e mobile.
    - Eles devem poder gerar os holerites em formato PDF.
    - Os colaboradores devem ser capazes de visualizar as operações vinculadas a eles e informações sobre seus perfis.

## **Requisitos Não Funcionais:**

1. **Segurança:**
    - O sistema deve implementar autenticação segura para proteger os dados sensíveis.
    - Deve haver níveis de acesso diferentes, garantindo que os usuários vejam apenas as informações relevantes para suas funções.
2. **Desempenho:**
    - O sistema deve ser responsivo, garantindo tempos de carregamento rápidos para as diferentes telas.
    - Consultas às informações devem ser eficientes para evitar atrasos.
3. **Usabilidade:**
    - A interface do usuário deve ser intuitiva e fácil de usar, mesmo para usuários não técnicos.
    - As operações devem ser autoexplicativas e minimizar a possibilidade de erros.
4. **Escalabilidade:**
    - O sistema deve ser projetado para lidar com um aumento no número de funcionários, cargos, estabelecimentos, etc.
5. **Compatibilidade:**
    - A interface web deve ser compatível com uma variedade de navegadores modernos.
    - A aplicação móvel deve ser desenvolvida para plataformas populares (iOS e Android).
6. **Documentação:**
    - Deve haver documentação detalhada que explique como usar cada funcionalidade do sistema.
    - Um manual passo a passo deve ser fornecido para auxiliar os usuários em suas tarefas.
7. **Confiabilidade:**
    - O sistema deve ser confiável e minimizar a ocorrência de erros, especialmente ao gerar folhas de pagamento e holerites.
8. **Privacidade:**
    - Os dados dos funcionários e suas informações pessoais devem ser tratados com confidencialidade e em conformidade com regulamentações de privacidade.