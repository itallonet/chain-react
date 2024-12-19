# ChainReact

ChainReact é um gerenciador de tarefas assíncronas com suporte a dependências, paralelismo e recuperação de falhas. Ele é projetado para executar tarefas de forma eficiente, garantindo que a ordem das dependências seja respeitada e que falhas sejam tratadas adequadamente. 

---

## Recursos Principais

- **Execução Baseada em Dependências:** Tarefas só são executadas quando todas as suas dependências forem concluídas.
- **Paralelismo:** Tarefas independentes são executadas simultaneamente para maximizar a eficiência.
- **Recuperação de Falhas:** Reexecução automática de tarefas com falha, com um limite configurável de tentativas.
- **Logs Detalhados:** Relatórios completos sobre a execução de cada tarefa, incluindo falhas e tempos de execução.
- **Modularidade:** Suporte para integração com funções definidas pelo usuário.
- **Integração com RabbitMQ:** Possibilidade de usar RabbitMQ para gerenciar filas de mensagens entre tarefas.
- **Persistência com SQLite:** Suporte a banco de dados SQLite para salvar estados e logs de tarefas.

---

## Exemplos de Uso

### Entrada
Uma lista de tarefas no seguinte formato:
```json
[
    {"id": "A", "deps": [], "exec": "task_A"},
    {"id": "B", "deps": ["A"], "exec": "task_B"},
    {"id": "C", "deps": ["A"], "exec": "task_C"},
    {"id": "D", "deps": ["B", "C"], "exec": "task_D"}
]
```
- **`id`:** Identificador único da tarefa.
- **`deps`:** Lista de dependências (tarefas que devem ser concluídas antes).
- **`exec`:** Nome da função que executa a tarefa.

### Saída
Um log detalhado do processo, incluindo:
- Sequência de execução das tarefas.
- Tempo de execução.
- Falhas e tentativas de reexecução.
- Resultado final de cada tarefa (sucesso ou falha).

---

## Instalação

1. Clone o repositório:
   ```bash
   git clone https://github.com/itallonet/chain-react.git
   cd chainreact
   ```
2. Instale as dependências:
   ```bash
   npm install
   ```

---

## Uso

1. Defina suas tarefas em um arquivo JSON ou diretamente no código.
2. Configure o RabbitMQ e SQLite:
   - Certifique-se de que o servidor RabbitMQ está em execução.
   - Configure o acesso ao banco de dados SQLite.
3. Execute o gerenciador:
   ```bash
   node chainreact.js
   ```
4. Observe o progresso e o log no terminal.

---

## Estrutura do Projeto

- **`chainreact.js`**: Arquivo principal do gerenciador.
- **`tasks/`**: Diretório com exemplos de definição de tarefas.
- **`logs/`**: Diretório para logs de execução.
- **`db/`**: Diretório para o banco de dados SQLite.

---

## Contribuição

Contribuições são bem-vindas! Siga estas etapas:
1. Fork o repositório.
2. Crie um branch para sua feature/bugfix:
   ```bash
   git checkout -b minha-feature
   ```
3. Envie suas modificações:
   ```bash
   git push origin minha-feature
   ```
4. Abra um Pull Request.

---

## Licença

Este projeto está licenciado sob a [MIT License](LICENSE).

