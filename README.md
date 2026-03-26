# miniguia-estudos-notebooklm
Criação de um Assistente de Operações Sankhya
Criação de uma mente especialista no sistema de gestão Sankhya. Esse ERP que é bastante utilizando por grandes empresas. o objetivo principal é conseguir resolver ou achar os melhores meios para conseguir resolver alguns problemas que acontecem no dia a dia de quem trabalha com essa ferramenta. "Que é o meu caso". muitas vezes mesmo no site de ajuda fica um pouco complicado. A idéia é criar um assistente de estudos voltado para identificar as causas e possiveis soluções.


Miniguia: Assistente de Operações Sankhya
Este guia consolida os pilares para transformar o NotebookLM em um especialista no ecossistema Sankhya.
1. Resumo Estruturado do Assunto
Para que o assistente seja útil, ele precisa dominar três camadas fundamentais do ERP:
•	Camada de Dados (Dicionário de Dados): Compreensão de como as tabelas se relacionam (Ex: TGFCAB para cabeçalhos de notas e TGFITE para itens). É o coração da geração de dashboards e consultas SQL.
•	Camada de Negócio (Processos): O fluxo de "Cotação > Pedido > Nota Fiscal". O assistente deve entender as TOPs (Tipos de Operação), que são as regras de ouro que definem como o sistema se comporta contabilmente e fiscalmente.
•	Camada de Customização (Sankhya Developer): Uso de Java para ações personalizadas, criação de telas adicionais e gatilhos (triggers) que automatizam tarefas repetitivas.
________________________________________
2. Glossário de Conceitos-Chave
Estes termos são essenciais para "treinar" a semântica do seu assistente:
Termo	Definição
TOP (Tipo de Operação)	A configuração mestre. Define se uma nota gera estoque, financeiro ou impostos.
Dicionário de Dados	Onde se configuram campos adicionais, nomes de tabelas e metadados do sistema.
MGE / Jiva / Sankhya Om	Evoluções da interface do sistema (focaremos no Sankhya Om, a versão web atual).
Snk-Config / Portal	Telas centrais para administração e movimentação de documentos.
Dashboards / Sankhya BI	Ferramenta visual de análise de dados baseada em SQL ou cubos de decisão.
________________________________________


3. Biblioteca de Prompts Reutilizáveis
A. Para Resolução de Problemas (Troubleshooting)
"Com base nos manuais fornecidos, identifique por que o erro '[ERRO ESPECÍFICO]' ocorre ao tentar confirmar uma Nota Fiscal de Saída e quais campos na TOP devo verificar para corrigir isso."
B. Para Criação de Consultas (SQL/Relatórios)
"Atue como um desenvolvedor Sankhya. Escreva uma consulta SQL que relacione a tabela TGFCAB com a TGFVEN para listar todas as vendas por vendedor no mês atual, filtrando apenas as notas confirmadas."
C. Para Documentação de Processos Internos
"Crie um passo a passo simplificado para um novo usuário sobre como realizar a 'Baixa de Títulos no Financeiro', destacando os campos obrigatórios conforme as fontes carregadas."

