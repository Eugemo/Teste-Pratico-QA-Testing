
# Relatório de Testes - Sauce Demo

## 1. Plano de Testes

Este documento descreve o plano de testes para a aplicação Sauce Demo, incluindo casos de teste para os principais fluxos da aplicação.

**1.1 Login com diferentes tipos de usuários:**

| Caso de Teste | Descrição | Dados de Entrada | Resultado Esperado | Resultado Obtido | Status |
|---|---|---|---|---|---|
| CT001 | Login com usuário padrão (standard_user) | username: standard_user, password: secret_sauce | Acesso bem-sucedido ao inventário de produtos. | ✅ | Passou |
| CT002 | Login com usuário bloqueado (locked_out_user) | username: locked_out_user, password: secret_sauce | Mensagem de erro indicando que o usuário está bloqueado. | ✅ | Passou |
| CT003 | Login com usuário problemático (problem_user) | username: problem_user, password: secret_sauce | Acesso bem-sucedido ao inventário de produtos. | ✅ | Passou |
| CT004 | Login com credenciais inválidas | username: teste, password: teste - username: teste / user name: standard_UseR password: secret_sauce | Mensagem de erro indicando credenciais inválidas. | ✅ | Passou |
| CT005 | Login com campo username vazio | username: , password: secret_sauce | Mensagem de erro indicando campo username obrigatório. | ✅ | Passou |
| CT006 | Login com campo password vazio | username: standard_user, password:  | Mensagem de erro indicando campo password obrigatório. | ✅ | Passou |


**1.2 Ordenação e filtragem de produtos:**

| Caso de Teste | Descrição | Dados de Entrada | Resultado Esperado | Resultado Obtido | Status | Notas |
|---|---|---|---|---|---|---|
| CT007 | Ordenação por nome (A-Z) | Selecionar opção "Name (A to Z)" | Produtos listados em ordem alfabética crescente. | ✅ | Passou |  |
| CT008 | Ordenação por nome (Z-A) | Selecionar opção "Name (Z to A)" | Produtos listados em ordem alfabética decrescente. | ✅ | Passou |  |
| CT009 | Ordenação por preço (baixo-alto) | Selecionar opção "Price (low to high)" | Produtos listados em ordem crescente de preço. | ✅ | Passou |  |
| CT010 | Ordenação por preço (alto-baixo) | Selecionar opção "Price (high to low)" | Produtos listados em ordem decrescente de preço. | ✅ | Passou |  |
| CT011 | Filtragem por tipo de produto (Backpack) | Selecionar filtro "Backpack" | Apenas produtos do tipo Backpack são exibidos. | ✅ | Passou |  |
| CT011a | Filtrar por "Sauce Labs Backpack" e ordenar por preço (baixo a alto) | Filtro: "Backpack", Orden: "Price (low to high)" |  Produtos tipo "Sauce Labs Backpack" ordenados de menor a maior preço. | ❌ | Falhou| Possui um ícone de acesso ao filtro, mas não possui a funcionalidade de filtro, em vez disso mostra ordenamento | 
| CT011b | Filtrar por "Sauce Labs Backpack" e ordenar por nome (A-Z) | Filtro: "Backpack", Orden: "Name (A to Z)" | Produtos tipo "Sauce Labs Backpack" ordenados alfabeticamente (A-Z). |❌ | Falhou | não pode ser executado devido ao bloqueio do CP11a|
| CT011c | Filtrar por "T-Shirt" e ordenar por preço (alto a baixo) | Filtro: "T-Shirt", Orden: "Price (high to low)" | Produtos tipo "T-Shirt" ordenados de maior a menor preço. |❌ | Falhou | não pode ser executado devido ao bloqueio do CP11a |
| CT011d | Filtrar por "Onesie" e ordenar por nome (Z-A) | Filtro: "Onesie", Orden: "Name (Z to A)" | Produtos tipo "Onesie" ordenados alfabeticamente (Z-A). |❌ | Falhou | não pode ser executado devido ao bloqueio do CP11a|
| CT011e | Filtrar por "Jacket" e ordenar por preço (baixo a alto)  | Filtro: "Jacket", Orden: "Price (low to high)" | Produtos tipo "Jacket" ordenados de menor a maior preço. |❌ | Falhou | não pode ser executado devido ao bloqueio do CP11a |
| CT011f | Múltiplos filtros e ordenamento (ej. "Backpack" e "T-Shirt" por preço (alto a baixo)) | Filtros: "Backpack", "T-Shirt", Orden: "Price (high to low)" | Mochilas e camisetas ordenadas por preço de maior a menor, *se múltiplos filtros são permitidos*. Se não, mensagem de erro ou resultado consistente com o comportamento do site. |❌ | Falhou | não pode ser executado devido ao bloqueio do CP11a |


**1.3 Fluxo completo de compra:**

| Caso de Teste | Descrição | Dados de Entrada | Resultado Esperado | Resultado Obtido | Status | Notas |
|---|---|---|---|---|---|---|
| CT012 | Adicionar produto ao carrinho | Adicionar um produto ao carrinho. | Produto adicionado ao carrinho com sucesso. | ✅ | Passou |  |
| CT013 | Ir para o carrinho | Clicar no ícone do carrinho. | Tela do carrinho exibida com o produto adicionado. | ✅ | Passou |  |
| CT014 | Remover produto do carrinho | Remover o produto do carrinho. | Produto removido com sucesso. | ✅ | Passou |  |
| CT015 | Finalizar a compra (com dados válidos) | Preencher os dados do formulário de checkout com dados válidos. | Pedido finalizado com sucesso, mensagem de confirmação exibida. | ✅ | Passou | |
| CT015a | Finalizar compra com dados válidos - 1 item | Agregar 1 produto, completar o formulário com dados válidos. | Pedido finalizado, mensagem de confirmação, número de pedido, etc. |  ✅ | Passou  |  | 
| CT015b | Finalizar compra com dados válidos - múltiplos items | Agregar vários produtos, completar o formulário com dados válidos. | Pedido finalizado, mensagem de confirmação, número de pedido com todos os itens, total correto. |  ✅ | Passou | |
| CT015c | Finalizar compra com dados inválidos - campos vazios | Agregar um produto, deixar o campo "Nome" vazio. Repita com os outros campos vazios | Mensagem de erro indicando que o campo <nome-campo>" é obrigatório. | ❌ | Falhou | indica qual campo está vazio, mas marca em vermelho os campos que foram preenchidos corretamente | 
| CT015d | Finalizar compra com dados inválidos - código postal inválido | Agregar um produto, inserir código postal inválido. | Mensagem de erro indicando código postal inválido. |❌ | Falhou | aceita qualquer valor ou tipo de caractere como um campo válido | 
| CT015e | Interrumpir a compra antes da finalização | Agregar um produto, iniciar a compra e cancelar ou sair. | Nenhum pedido registrado, o carrinho deve manter os itens. |✅ | Passou  |  |
| CT015f | Comprar com carrinho vazio | Tentar finalizar a compra com o carrinho vazio. | Mensagem indicando que o carrinho está vazio ou que não se podem realizar compras sem itens. |❌ | Falhou | aceitar a transação com o carrinho vazio, validar apenas que carregou os dados do comprador | 


**1.4 Remoção de itens do carrinho:**

| Caso de Teste | Descrição | Dados de Entrada | Resultado Esperado | Resultado Obtido | Status |
|---|---|---|---|---|---|
| CT016 | Remover um item do carrinho | Selecionar um item e clicar em "Remove". | Item removido do carrinho, total atualizado. | ✅ | Passou |  |
| CT017 | Remover todos os itens do carrinho | Remover todos os itens do carrinho. | Carrinho vazio, mensagem de carrinho vazio exibida. | ✅ | Passou |  |
| CT017a | Remover itens do carro da tela principal | Remova seus itens clicando nos produtos adicionados na tela principal. | São retirados do carrinho e o indicador de quantidade muda de acordo com a quantidade de produtos | ✅ | Passou | |


**1.5 Navegação entre páginas:**

| Caso de Teste | Descrição | Dados de Entrada | Resultado Esperado | Resultado Obtido | Status |
|---|---|---|---|---|---|
| CT018 | Navegação entre páginas de produtos | Navegar pelas páginas de produtos usando a paginação. | Transição suave entre as páginas, sem erros. | ✅ | Passou |  
| CT019 | Navegação para o carrinho | Clicar no ícone do carrinho. | Redirecionamento para a página do carrinho. | ✅ | Passou |  
| CT020 | Navegação para a página de login (após logout) | Clicar no botão de logout e tentar acessar uma página que exige login. | Redirecionamento para a página de login. | ✅ | Passou |  


**1.6 Logout:**

| Caso de Teste | Descrição | Dados de Entrada | Resultado Esperado | Resultado Obtido | Status |
|---|---|---|---|---|---|
| CT021 | Logout | Clicar no botão de logout. | Redirecionamento para a página de login. | ✅ | Passou |  

 
**1.7 Validação de Informação na Tela:**

| Caso de Teste | Descrição | Dados de Entrada | Resultado Esperado | Resultado Obtido | Status | Notas |
|---|---|---|---|---|---|---|
| VT001 | Verificar nome do produto na página de detalhes | Acessar página de detalhes de um produto. | Nome do produto exibido corretamente. | ❌ | Falhou | Nome de variável "{nome_produto}" exibido em vez do nome real do produto.|
| VT002 | Verificar preço do produto na página de detalhes | Acessar página de detalhes de um produto. | Preço do produto exibido corretamente. | ✅ | Passou |  |
| VT003 | Verificar descrição do produto na página de detalhes | Acessar página de detalhes de um produto. | Descrição do produto exibida corretamente. |❌ | Falhou |Descrição do produto "{descrição_producto}" exibido em vez do nome real do produto.|
| VT004 | Verificar total do carrinho | Adicionar itens ao carrinho. | Total do carrinho calculado corretamente (soma dos preços dos itens). | ✅ | Passou |  |


**1.8 Menu Lateral:**

| Caso de Teste | Descrição | Dados de Entrada | Resultado Esperado | Resultado Obtido | Status | Notas |
|---|---|---|---|---|---|---|
| ML001 | Abrir o menu lateral | Clicar no ícone/elemento que abre o menu. | Menu lateral aberto, exibindo as opções de navegação. | ✅ | Passou |   |
| ML002 | Fechar o menu lateral | Clicar no ícone/elemento que fecha o menu, ou clicar fora da área do menu. | Menu lateral fechado, conteúdo principal visível. | ✅ | Passou |  
| ML003 | Verificar a visibilidade de todos os itens do menu | Abrir o menu lateral. | Todos os itens de menu devem estar visíveis e acessíveis. | ❌ | Falhou | Existem opções que não possuem funcionalidade ou não possuem acesso a botão de retorno | https://github.com/user-attachments/assets/8139a428-10c0-4ac5-8fc4-a13b1c218c10 |
| ML004 | Testar o menu lateral em diferentes tamanhos de tela | Abrir o menu lateral em diferentes tamanhos de tela (desktop, tablet, mobile) | O menu lateral deve se adaptar ao tamanho da tela e exibir o conteúdo corretamente sem sobreposições ou cortes. |✅ | Passou |  | 





## Relatório de Testes - Sauce Demo: Resultados, Sugestões e Análise de Riscos

Baseado nos resultados dos testes apresentados, segue a sumarização dos resultados, sugestões de UX/UI, bugs encontrados e análise de riscos:

**Resultados das Testes:**

A maioria dos testes de login, navegação, adição e remoção de itens do carrinho e logout foram bem-sucedidos.  No entanto, foram encontrados problemas significativos nos testes de ordenação e filtragem de produtos e na finalização da compra.  Especificamente:

* **Login:** Todos os testes de login passaram.
* **Ordenação e Filtragem:**  A ordenação funcionou corretamente, mas a filtragem de produtos falhou completamente.  O que aparenta ser um filtro na verdade apenas realiza uma ordenação.
* **Fluxo de Compra:**  A adição e remoção de itens, e a navegação para o carrinho funcionaram corretamente.  No entanto, a validação de dados no checkout é deficiente, permitindo a submissão com campos vazios e códigos postais inválidos.  A compra com o carrinho vazio também é permitida.


**Sugestões de Melhorias de UX/UI:**

* **Implementar Filtros:** A funcionalidade de filtro de produtos é crucial para a usabilidade.  Deve ser implementada corretamente, permitindo a seleção de múltiplos filtros se necessário.
* **Mensagens de Erro Melhores:** As mensagens de erro no checkout são muito genéricas.  Devem ser mais específicas, indicando exatamente qual campo está com problema.
* **Validação de Dados:** Implementar uma validação robusta dos dados de entrada no formulário de checkout, incluindo validação de código postal e prevenção de campos vazios.
* **Feedback do Usuário:** Fornecer feedback claro ao usuário após cada ação, por exemplo, confirmação visual da adição/remoção de itens do carrinho.
* **Prevenção de Compra com Carrinho Vazio:** Implementar um mecanismo que impeça a finalização de compra se o carrinho estiver vazio.
* **Tela principal:** em alguns produtos o nome da variável é exibido em vez do nome ou descrição do produto
* **Menu lateral:** o menu possui opções sem funcionalidade ou que não permitem retornar à tela principal
![Mensagens de erro login](https://github.com/user-attachments/assets/224c64b4-5275-48d6-b6ef-ec81f2b23098)
![2024-11-24_11h15_45](https://github.com/user-attachments/assets/aec58ba9-a6fe-4375-9fcc-e45c133cbe00)

**Bugs Encontrados:**

* **CT011a - CT011f (Ordenação e Filtragem):** A funcionalidade de filtragem está ausente ou com defeito. O elemento que parece ser um filtro na verdade ordena os resultados.
https://github.com/user-attachments/assets/3bb9f525-70c9-4fea-97a8-1a25f6d76070

* **CT015c (Finalização de Compra):**Finalizar compra com dados inválidos - campos vazios.  indica qual campo está vazio, mas marca em vermelho os campos que foram preenchidos corretamente.
(https://github.com/user-attachments/assets/757c016d-4ad6-44f6-8555-a85f705c8c0d

* **CT015d (Finalização de Compra):**  Não há validação do código postal. Qualquer entrada é aceita.
https://github.com/user-attachments/assets/65259bff-7ddb-4430-968a-d68a583c40af

* **CT015f (Finalização de Compra):**  É possível finalizar a compra mesmo com o carrinho vazio.
https://github.com/user-attachments/assets/dc087751-6eab-4949-b351-a0874095f29c
  
* **VT001 - VT003 (Validação de Informação na Tela):**  nome da variável é exibido em vez do nome ou descrição do produto
https://github.com/user-attachments/assets/1827ba87-888c-4ae3-b937-a4a22b140b01
  
* **ML003 (Validação menu lateral):**  Existem opções que não possuem funcionalidade ou não possuem acesso a botão de retorno
https://github.com/user-attachments/assets/f06f0ca2-8dd5-4c29-9f97-9ea6c65071ba


**Análise de Riscos:**

* **Risco de Conversão:** Os bugs no fluxo de checkout (validação de dados, compra com carrinho vazio) impactam diretamente a conversão, levando a uma alta taxa de abandono de carrinho.  Este é o risco mais crítico.
* **Risco de Reputação:** A experiência do usuário será negativamente afetada pelos bugs presentes, prejudicando a reputação da aplicação.
* **Risco de Perda de Receita:** A combinação dos riscos de conversão e reputação pode levar a uma significativa perda de receita.


**Conclusão:**

A aplicação Sauce Demo apresenta problemas críticos no fluxo de compra e na funcionalidade de filtragem de produtos.  A correção desses bugs e a implementação das sugestões de melhorias de UX/UI são essenciais antes do lançamento em produção.  Testes adicionais, especialmente de responsividade e segurança, também são fortemente recomendados.
Nota: A aplicação possui pouca documentação que permita a realização de mais testes, são necessárias informações sobre histórias de usuários ou casos de uso para dar maior cobertura aos testes. Apenas testes smoke foram realizados na aplicação web.
