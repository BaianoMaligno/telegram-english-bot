# Telegram English Bot


[![Capa do Telegram English Bot](linkedin-cover-telegram-english-bot.jpg)](linkedin-cover-telegram-english-bot.jpg)

[Prévia para o LinkedIn](https://soteropolitano.github.io/telegram-english-bot/linkedin-preview-v2/)

Criei esse bot para ajudar nos meus estudos de inglês pelo Telegram. Ele corrige frases, transcreve áudios curtos e explica os erros em português, com uma sugestão mais natural em inglês.

## Visão geral

As mensagens chegam por webhook. O bot processa o texto ou áudio e responde no próprio Telegram.

Usei Python e Flask no Google Cloud Run, Gemini API para correção e transcrição, Secret Manager para as credenciais e Cloud Storage para guardar o controle mensal de custo.

Também coloquei controle de acesso, limite de áudio e bloqueio por custo. Em grupo, só responde por comando e sai dos grupos não autorizados.

## Funcionalidades

- Correção de texto em inglês
- Transcrição e correção de áudios curtos
- Explicação dos erros em português
- Sugestão de versão mais natural em inglês
- Comando `/corrigir` para uso em grupos
- Comandos `/start` e `/help` no privado
- Owner gate para restringir uso privado
- Saída automática de grupos não autorizados
- Limite de áudio por tamanho e duração
- Controle mensal de custo em Cloud Storage
- Hard stop interno para evitar gasto inesperado

## Arquitetura

```text
Telegram
   ↓ Webhook
Cloud Run
   ↓
Python + Flask + Gunicorn
   ↓
Gemini API
   ↓
Resposta no Telegram

Cloud Storage
   ↓
Ledger mensal de custo estimado

Secret Manager
   ↓
Tokens e chaves sensíveis
```
