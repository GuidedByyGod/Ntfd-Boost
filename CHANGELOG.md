# Changelog

## 1.0.0 — limpeza e rebrand

### Removido
- Autenticação externa, licenciamento e verificação de chave.
- Login Discord/OAuth e vínculo de conta.
- Salvamento local de usuário/senha.
- Salvamento de credenciais Discord.
- Serviço de IA externo e token de acesso.
- Gate de feedback e links de comunidade antigos.
- Textos “Craked by TY” e referências visuais à marca antiga.

### Alterado
- Projeto renomeado para **Ntfd Boost**.
- Executável principal: `NtfdBoost.exe`.
- Pasta de dados: `%LOCALAPPDATA%\NtfdBoost`.
- Pasta do painel: `web/painel`.
- Título da janela, painel, API e README em Ntfd Boost.
- Ícone e logo usando os assets de `OPENCODE/Ntfd Boost Imagens`.
- Servidor local fixo em `127.0.0.1:8795`, perfil local `Ntfd Boost`.

### Segurança
- `profile-jobs.mjs` bloqueia comandos de boot/segurança e limpeza recursiva.
- Nenhum endpoint de upload, conta ou telemetria.
- Nenhum token ou credencial no pacote final.

### Build
- `build_dist.py` compila Ntfd Boost, FrameFpsBridge e NtfdDisplaySetup.
- Gera `NtfdBoost.exe` single-file e copia para a raiz.
- Marcador de build por timestamp força atualização em `%LOCALAPPDATA%\NtfdBoost`.
- Testado: compilação C#, servidor `/api/build`, `/api/session`, `/api/device`, `/api/native` e UI no Chrome.
