# Teste-Pratico-QA-Testing
Prova tecnica QA
Você terá de executar e documentar dois tipos de testes:
1. UI Testing
2. API Testing

Os requisitos a serem atendidos estão descritos a seguir para cada caso.

---------------------------------
1. UI TESTING
A tarefa aqui é testar a plataforma de e-commerce Sauce Demo (https://www.saucedemo.com). Suponha que a plataforma precisa passar por uma validação completa antes de ser lançada em produção e cabe a você testá-la. 

1.1 Instruções:
1.1.1 Crie um plano de testes documentado que cubra os principais fluxos da aplicação 
1.1.2 Execute os testes manualmente e documente os resultados 
1.1.3 Identifique potenciais problemas de UX/UI que poderiam impactar negativamente a experiência do usuário 

1.2 Cenários mínimos a serem testados:
1.2.1 Login com diferentes tipos de usuários disponíveis 
1.2.2 Ordenação e filtragem de produtos 
1.2.3 Fluxo completo de compra (do carrinho até finalização) 
1.2.4 Remoção de itens do carrinho 
1.2.5 Navegação entre páginas 
1.2.6 Logout

1.3 Entregáveis:

1.3.1 Documento formatado em Markdown (.md) contendo:
1.3.1.1 Plano de testes estruturado com casos de teste
1.3.1.2 Resultados dos testes executados
1.3.1.3 Sugestões de melhorias de UX/UI
1.3.1.4 Lista de bugs encontrados (se houver)
1.3.1.5 Análise de riscos da aplicação

1.3.2 Extras (diferenciais):
1.3.2.1 Testes de responsividade
1.3.2.2 Testes de acessibilidade
1.3.2.3 Sugestões de automação

1.4 Critérios de avaliação:
1.4.1 Organização e clareza da documentação, dentro dos critérios fornecidos
1.4.2 Cobertura dos cenários críticos
1.4.3 Capacidade de identificar eventuais bugs/problemas
1.4.4 Qualidade das sugestões de melhoria
1.4.5 Pensamento crítico sobre eventuais riscos e impactos no negócio

1.5 Observações:
1.5.1 A documentação deve ser entregue obrigatoriamente em Markdown (.md)
1.5.2 Quando considerar necessário, explique/justifique suas decisões
1.5.3 Inclua prints de tela quando relevante

---------------------------------
2. API TESTING
A tarefa aqui é testar a API do Restful-Booker (https://restful-booker.herokuapp.com), um sistema de reservas de hotel. Suponha que a API precisa ser validada antes de ser integrada com o front-end e cabe a você testá-la. 

2.1 Instruções:
2.1.1 Analise a documentação da API fornecida 
2.1.2 Crie e execute testes para os endpoints principais 
2.1.3 Documente os resultados e comportamentos encontrados 

2.2 Cenários:

2.2.1 Autenticação:
2.2.1.1 Gerar token de autenticação 
2.2.1.2 Tentar gerar token com credenciais inválidas

2.2.2 Gestão de reservas:
2.2.2.1 Criar uma nova reserva 
2.2.2.2 Buscar uma reserva específica 
2.2.2.3 Listar todas as reservas 
2.2.2.4 Atualizar uma reserva existente 
2.2.2.5 Deletar uma reserva

2.2.3 Filtros e buscas:
2.2.3.1 Buscar reservas por nome 
2.2.3.2 Buscar reservas por data de check-in 
2.2.3.3 Buscar reservas por data de check-out 

2.3 Entregáveis:

2.3.1 Collection contendo: 
2.3.1.1 Todos os requests organizados
2.3.1.2 Pelo menos um teste para cada request 
2.3.1.3 Variáveis de ambiente configuradas 

2.3.2 Documento em Markdown (.md) contendo: 
2.3.2.1 Lista de cenários testados 
2.3.2.2 Resultados obtidos 
2.3.2.3 Bugs encontrados (se houver)

2.4 Pontos de atenção:
2.4.1 Tratamento de erros 
2.4.2 Validação de campos obrigatórios
2.4.3 Formato das datas 
2.4.4 Códigos de resposta HTTP 

2.6 Observações:
2.6.1 Use Postman ou qualquer outra ferramenta de sua preferência 
2.6.2 Documente quaisquer premissas assumidas, se possível

-----------------------------------
3. Considerações finais:
Caso não consiga completar os testes até o prazo definido:
3.1 Garanta que tudo que foi construído esteja em funcionamento
3.2 Relate na documentação quais foram as dificuldades encontradas
3.3 Documente o que foi implementado e o que ficou pendente
