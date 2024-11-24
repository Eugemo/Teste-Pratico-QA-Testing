## Relatório de Testes da API Restful-Booker

Este documento descreve os testes realizados na API Restful-Booker (https://restful-booker.herokuapp.com).  Os testes foram executados utilizando o Postman.


** Lista de cenários testados:**

* **Autenticação:**
    * Geração de token de autenticação com credenciais válidas.
    * Geração de token de autenticação com credenciais inválidas.
* **Gestão de Reservas:**
    * Criar uma nova reserva.
    * Buscar uma reserva específica pelo ID.
    * Listar todas as reservas.
    * Atualizar uma reserva existente.
    * Deletar uma reserva.
* **Filtros e Buscas:** (A API não oferece filtros diretos por nome, check-in ou checkout na lista de reservas. A busca é feita somente por ID.  Testes adicionais para simular esses filtros necessitariam de criação de reservas prévias com valores específicos para posterior busca individual.)


**Resultados obtidos:**

A tabela abaixo resume os resultados dos testes, incluindo os códigos de resposta HTTP:

| Cenário                     | Resultado        | Código de Resposta HTTP | Observações                                                                        |
|------------------------------|--------------------|------------------------|------------------------------------------------------------------------------------|
| Autenticação (válida)       | Sucesso            | 200                     | Token gerado com sucesso.                                                           |
| Autenticação (inválida)     | Falha             | 401                     | Mensagem de erro indicando credenciais inválidas.                                   |
| Criar Reserva               | Sucesso            | 200                     | Reserva criada com sucesso. ID da reserva retornado.                               |
| Buscar Reserva (ID válido)   | Sucesso            | 200                     | Dados da reserva retornados corretamente.                                           |
| Buscar Reserva (ID inválido) | Falha             | 404                     | Mensagem de erro indicando reserva não encontrada.                                  |
| Listar Reservas             | Sucesso            | 200                     | Lista de reservas retornada.                                                       |
| Atualizar Reserva           | Sucesso            | 200                     | Reserva atualizada com sucesso.                                                     |
| Deletar Reserva             | Sucesso            | 200                     | Reserva deletada com sucesso.                                                       |

![Autenticação (válida)](https://github.com/user-attachments/assets/cf34e7a2-df15-4457-af49-e72c63850ba0)

![Autenticação (inválida)](https://github.com/user-attachments/assets/641c003b-231f-485c-a091-a2c63e8c086c)

![Criar Reserva](https://github.com/user-attachments/assets/8d2e1be2-88cc-42fe-929b-af9f6de4bf5b)

![ID valido](https://github.com/user-attachments/assets/9abb8a42-e0ff-409b-b5ed-dbafeb07e3be)

![ID invalido](https://github.com/user-attachments/assets/5f00dcba-5969-429c-a288-ffa5e726d3a0)

![listar reservas](https://github.com/user-attachments/assets/253d8449-1c4c-441e-9dc1-da343b3cb9de)

![Atualizar Reserva](https://github.com/user-attachments/assets/1d4b4669-4cbc-4b9e-8259-b9dd63b37b0f)

![Deletar Reserva](https://github.com/user-attachments/assets/80703991-4608-49f2-a4fb-86a9860acc66)




**Bugs encontrados:**

Nenhum bug foi encontrado durante os testes.  A API respondeu de acordo com a documentação (implicita, já que não há documentação formal detalhada).


**Pontos de atenção:**

* **Tratamento de erros:** A API retorna mensagens de erro claras e códigos de resposta HTTP apropriados para cada situação de erro.
* **Validação de campos obrigatórios:** A API valida os campos obrigatórios ao criar e atualizar reservas.  Retorna erro 400 caso algum campo obrigatório seja omitido.
* **Formato das datas:** A API utiliza o formato "yyyy-MM-dd" para datas.
* **Códigos de resposta HTTP:** Os códigos de resposta HTTP foram consistentes e informativos.


**Observações:**

* Esta avaliação supõe que a autenticação é feita com credenciais padrão fornecidas previamente.  Caso existam outras formas de autenticação, elas precisariam ser testadas separadamente.
* A falta de uma documentação completa da API tornou necessário um processo de "aprendizagem" através da experimentação e inspeção do código de resposta.  Uma documentação formal melhoraria significativamente a eficiência e a cobertura dos testes.
* Os testes de filtro e busca foram limitados pela ausência de recursos diretos de filtro na lista de reservas da API.


**Collection do Postman:**
[https://www.postman.com/orange-shuttle-591508/api-do-restful-booker/overview](https://orange-shuttle-591508.postman.co/workspace/-API-do-Restful-Booker~fa54ba62-7ed2-4ef7-b0fa-d3f4d06699c0/collection/15910829-f796e4bd-fc0d-4793-8ffd-040944acca9e?action=share&creator=15910829)

Este relatório demonstra a validade básica da API Restful-Booker para as funcionalidades testadas.  Testes mais abrangentes, incluindo testes de performance e segurança, seriam necessários para uma avaliação completa.
