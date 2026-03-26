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

Pergunta 1
"Com base nos manuais fornecidos, identifique por que o erro 'E0014' ocorre ao tentar confirmar uma Nota Fiscal de Saída e quais campos na TOP devo verificar para corrigir isso."

O erro 'E0014' é uma rejeição que ocorre exclusivamente na emissão de Notas Fiscais de Serviço eletrônicas (NFS-e) quando o sistema detecta uma duplicidade de documento na base de dados da Prefeitura.
Por que o erro 'E0014' ocorre?
A causa principal é que o conjunto de informações composto por Série, Número da nota, Código do Município Emissor e CNPJ/CPF do prestador já foi utilizado em uma NFS-e previamente aprovada na Prefeitura. Basicamente, a prefeitura identifica que você está tentando enviar um documento (DPS - Declaração de Prestação de Serviços) com uma numeração que já existe e foi autorizada anteriormente.
Quais campos na TOP verificar para corrigir?
Se após clicar no botão "NFS-e > Buscar Autorização" no Portal de Vendas o status da nota não mudar automaticamente para "Aprovada" (o que indicaria que o sistema apenas não tinha recebido o retorno), você precisará ajustar a sequência de numeração.
Para corrigir isso na TOP (Tipo de Operação), siga estes passos:
1.	Identifique o último número válido: Entre em contato com a Prefeitura ou consulte o portal municipal para saber qual foi o último número de RPS/NFS-e autorizado para o seu CNPJ e Série.
2.	Acesse a tela Tipos de Operação - TOP: Localize a TOP utilizada na nota.
3.	Acesse o Controle de Numeração: Clique no botão "Outras Opções" (ícone de três pontos) e selecione a opção "Controle de Numeração".
4.	Localize e ajuste a numeração: Na linha correspondente à sua Empresa, Série e Modelo de Documento Fiscal (específico para NFS-e), verifique o campo:
o	Último Código: Você deve informar neste campo o número da última NFS-e autorizada pela prefeitura. Assim, o próximo lançamento no sistema assumirá a sequência correta e evitará a duplicidade.
Observação Adicional: Certifique-se de que a TOP de serviço não esteja configurada para "Reiniciar numeração por data", pois essa configuração não é permitida para notas eletrônicas e pode causar inconsistências na sequência numérica.

Pergunta 2
Onde configuro os parâmetros ENVOBSNFE e ENVOBSPADNFE no sistema?

Você deve configurar os parâmetros ENVOBSNFE e ENVOBSPADNFE através da tela Preferências.
O caminho de acesso no sistema é: Configurações » Avançado » Preferências.
Aqui estão os detalhes sobre o que cada parâmetro habilita:
•	ENVOBSNFE (Envia Observação na NF-e): Este parâmetro é responsável por habilitar o envio da Observação manual inserida no cabeçalho da nota (tabela TGFCAB) para o arquivo XML e também para o DANFE, no quadro de Informações Complementares.
•	ENVOBSPADNFE (Envia Observação padrão na NF-e): Este parâmetro habilita o envio das Observações Padrão (tanto do cabeçalho quanto dos itens) para o arquivo XML da nota fiscal.
Para que as informações sejam efetivamente levadas para a nota, ambos devem estar configurados como Sim. Caso você utilize um modelo de dados adicionais personalizado na TOP, é importante garantir que ele não esteja sobrescrevendo ou ignorando essas tags no XML.

Fontes:
https://ajuda.sankhya.com.br/hc/pt-br
https://community.sankhya.com.br/
https://ajuda.sankhya.com.br/hc/pt-br/articles/37880563761047-Como-configurar-Tipos-de-Opera%C3%A7%C3%A3o-TOP
https://youtu.be/CGF-S6RVZkM
https://youtu.be/vdp1qhSyRz0
