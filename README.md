# SmartDeskAI — Raly | Sprint 1: RPA de e-mails:

O **SmartDeskAI** é o módulo de atendimento e automação robótica de processos (RPA) do projeto Raly, desenvolvido para o Challenge Motiva. Ele transforma mensagens recebidas em solicitações registradas, classificadas e encaminhadas às equipes responsáveis.

## Problema:

Solicitações operacionais podem chegar por canais diferentes e exigir que alguém leia cada mensagem, identifique o assunto, copie os dados, escolha uma equipe e responda ao solicitante. Esse trabalho manual consome tempo e pode atrasar o atendimento, especialmente em situações de risco.

## O que o sistema faz:

* Lê mensagens de uma caixa Gmail por IMAP em intervalos regulares.
* Converte cada mensagem em uma solicitação e registra um protocolo.
* Usa um modelo de linguagem local para sugerir categoria, prioridade e justificativa.
* Valida a classificação e aplica regras de roteamento para encaminhar o chamado por e-mail via SMTP.
* Envia confirmação ao solicitante e mantém o histórico do atendimento.
* Evita reprocessar mensagens enviadas pelo próprio sistema e identifica duplicatas.
* Encaminha casos de risco, baixa confiança ou prioridade alta para revisão humana.
* Bloqueia mensagens fora do escopo, abusivas, promocionais ou repetitivas.

O fluxo também pode receber solicitações pelo portal e por planilhas, além de contemplar a integração com voz no contexto do Raly.

## Como funciona a automação de e-mails:

1. O administrador configura a conta Gmail com uma senha de aplicativo.
2. O sistema verifica a caixa de entrada e captura novas mensagens.
3. A mensagem é validada, deduplicada e registrada com protocolo.
4. A IA local sugere a classificação; regras de segurança e confiança validam o resultado.
5. O chamado é encaminhado ao setor correspondente, ou fica aguardando revisão humana quando necessário.
6. O solicitante recebe uma confirmação por e-mail.

O sistema marca mensagens automáticas com cabeçalhos para evitar que suas próprias respostas sejam lidas novamente como novos pedidos. A senha de aplicativo deve ser configurada pelo administrador e não deve ser publicada no repositório.

## Tecnologias:

* **Python 3**: aplicação, regras de negócio e comunicação de e-mail com `imaplib` e `smtplib`.
* **SQLite**: armazenamento local de solicitações, eventos, usuários e mensagens capturadas.
* **Ollama**: execução local do modelo de linguagem (Qwen 2.5 3B, com alternativa de reserva).
* **Gmail IMAP/SMTP**: captura de mensagens e envio de respostas e encaminhamentos.
* **HTML, CSS e JavaScript**: interface web do SmartDeskAI.

## Segurança e supervisão humana:

A IA auxilia na interpretação do texto, mas não toma sozinha decisões críticas. Casos de risco, prioridade alta, baixa confiança ou falha na classificação são direcionados para revisão humana. A classificação é limitada a categorias previstas e validada antes do encaminhamento. Os endereços usados na demonstração são de teste; a configuração de produção deve apontar para os canais autorizados de cada equipe.

## Configuração e execução:

O relatório técnico descreve a configuração da conta Gmail na seção administrativa **E-mail**: informar a conta e a senha de aplicativo e selecionar **Conectar**. A captura ocorre em intervalos regulares. A senha de aplicativo é obtida nas configurações da conta Google.

> Os arquivos de código e os comandos de instalação/execução não acompanham este pacote de entrega; por isso, consulte o repositório completo do projeto para instruções específicas de inicialização. Não inclua senhas, tokens ou dados reais de usuários no README ou no controle de versão.

## Demonstração e documentação:

* [Vídeo demonstrativo](https://youtu.be/yXQynDMyEHQ)
* Relatório técnico: `Relatorio\_SmartDeskAI\_Raly.pdf`

O relatório documenta as telas, os principais trechos de código, os guardrails e os testes. Ele informa 35 testes automatizados aprovados no ambiente descrito e ressalta que a avaliação da classificação foi feita com um conjunto pequeno de mensagens.

## Equipe:

**Grupo Neura²** — FIAP São Paulo, turma 2TIAPR

* Rodrigo Wolkoff Giorgi
* Carlos Eduardo Mamede

## Escopo da Sprint:

Esta entrega apresenta a base do fluxo de RPA para atendimento de solicitações por e-mail: captura, registro, classificação assistida por IA, encaminhamento, resposta e tratamento supervisionado de exceções. A automação reduz tarefas repetitivas e mantém a decisão humana nos casos que exigem atenção.


