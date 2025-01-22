# Robo_Amil_2.0
Robô de extração de faturas da amil, feito em python com front em flask. 
![ilustração do front](https://github.com/user-attachments/assets/8782a915-70e3-4a7b-85ae-7399118bc026)

Documentação do Robô AMIL
1. Visão Geral
1.1 Objetivo
O robô AMIL é uma aplicação automatizada que realiza o download de faturas do portal AMIL para múltiplos condomínios. O sistema possui uma interface web para controle e monitoramento das operações.
1.2 Arquitetura
Frontend: Interface web desenvolvida com HTML, JavaScript e CSS
Backend: Servidor Flask (Python) + Selenium WebDriver
Armazenamento: Arquivos JSON para dados e configurações
2. Componentes Principais
2.1 Frontend (Interface Web)
Localização: templates/index.html
startLine: 138
endLine: 192
Funcionalidades:
Seleção de condomínios
Definição do número de meses para download
Modo de execução padrão ou personalizado
Monitoramento em tempo real
Logs de execução
Controles de pausa/parada
2.2 Backend (Servidor Flask)
Localização: app.py
startLine: 1
endLine: 102
Endpoints principais:
/ : Página inicial
/executar_robo : Inicia execução
/parar_robo : Interrompe execução
/status_robo : Status atual
/pausar_robo : Pausa/retoma execução
/dados_planilha.json : Dados dos condomínios
2.3 Core do Robô
Localização: main.py
Componentes principais:
1- Gerenciamento de Sessão
startLine: 754
endLine: 797
2- Processamento de Contratos
startLine: 826
endLine: 865
3. Fluxo de Execução
3.1 Inicialização
Carregamento dos dados da planilha
Configuração do WebDriver
Setup de logging
3.2 Processamento
Agrupamento de contratos por login
Para cada login:
Inicialização do driver
Login no portal
Processamento dos contratos
Fechamento do driver
3.3 Finalização
Geração de relatório
Envio de email com erros
Limpeza de recursos
4. Configurações
4.1 Arquivos de Configuração
dados_planilha.json: Dados dos condomínios
parametros_execucao.json: Parâmetros temporários
status.json: Status da execução
4.2 Diretórios
   BASE_DIR = 'G:\\Drives compartilhados\\XXXXXXX\\XX\\AMIL'
5. Tratamento de Erros
5.1 Níveis de Retry
Tentativas de login
Tentativas de download
Recuperação de sessão
5.2 Logging
Arquivo: output.log
Formato: %(asctime)s - %(message)s
Níveis: INFO, ERROR, WARNING
6. Modos de Operação
6.1 Modo Padrão
Processa todos os condomínios
3 meses de faturas
Execução sequencial
6.2 Modo Personalizado
Condomínios selecionados
Número de meses configurável
Mantém agrupamento por login
7. Manutenção
7.1 Monitoramento
Logs em tempo real
Status de execução
Contadores de progresso
7.2 Troubleshooting
1. Verificar output.log
Consultar status.json
Verificar conexão com portal
Validar dados_planilha.json
8. Requisitos
8.1 Sistema
Python 3.8+
Chrome WebDriver
Flask
8.2 Dependências
   selenium
    flask
  pyperclip
9. Segurança
9.1 Dados Sensíveis
Credenciais armazenadas em JSON
Sessões isoladas por login
Limpeza de cookies entre sessões
9.2 Controle de Acesso
Interface web local
Validação de parâmetros
Proteção contra execuções simultâneas
