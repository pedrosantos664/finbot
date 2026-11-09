# FinBot

Assistente educacional para aprender conceitos sobre investimentos no Brasil. Este projeto está sendo desenvolvido passo a passo como parte das aulas.

## Links do projeto

| O quê | Link |
|---|---|
| Chat publicado (Streamlit Cloud) | https://api-springboot-hhhzm9th9mkr8sc62uynvp.streamlit.app |
| API publicada (Render) | https://finbot-api-weul.onrender.com |
| Documentação da API | https://finbot-api-weul.onrender.com/docs |

No plano gratuito, a API "dorme" depois de um tempo sem uso: a primeira pergunta pode demorar cerca de 1 minuto.

## Etapa atual

Na Aula 2, o FinBot ganhou uma API em FastAPI, uma tela de chat em Streamlit e rastreamento das conversas no Langfuse. A API é publicada no Render e o front no Streamlit Community Cloud. O histórico de cada sessão ainda fica na memória da API e se perde quando ela reinicia.

## Requisitos

- Python 3.12
- Uma chave de API da Groq

## Como configurar no Windows

Abra o projeto no VS Code e, no terminal integrado, confirme que está na pasta principal `finbot`. Execute os comandos abaixo, um de cada vez:

```powershell
py -3.12 -m venv .venv
.\.venv\Scripts\Activate.ps1
pip install -r requirements-dev.txt
Copy-Item .env.example .env
```

Depois, abra o arquivo `.env` no VS Code e preencha `GROQ_API_KEY` com sua chave da Groq. Para registrar as conversas no Langfuse, preencha também `LANGFUSE_PUBLIC_KEY` e `LANGFUSE_SECRET_KEY`. Não compartilhe essas chaves e não as coloque neste README.

Para o front, instale também:

```powershell
pip install -r frontend/requirements.txt
```

## Como executar

Com o ambiente virtual ativado e o `.env` configurado, suba a API em um terminal:

```powershell
uvicorn app.main:app --reload
```

A documentação interativa fica em http://127.0.0.1:8000/docs. Em **outro** terminal (com o ambiente ativado), abra o front:

```powershell
streamlit run frontend/streamlit_app.py
```

O chat da Aula 1 continua disponível no terminal com `python -m scripts.chat_terminal` (digite `sair` para encerrar).

## Como executar os testes

Com o ambiente virtual ativado, rode:

```powershell
pytest -v
```

## Segurança

O arquivo `.env` contém chaves privadas e não deve ser enviado ao GitHub. O arquivo `.env.example` contém apenas o modelo das configurações e pode ser publicado.

## Próximas etapas

Na Aula 3, a memória das conversas vai para o MongoDB e os prompts passam a ser versionados no Langfuse.
