# Segurança — Ntfd Boost

## O que este projeto não faz

- Não pede login, chave de licença ou conta Discord.
- Não salva usuário/senha.
- Não salva credenciais do Discord.
- Não envia dados para servidores externos.
- Não usa licenciamento externo, OAuth, IA externa ou feedback remoto.

## Painel local

O servidor escuta apenas em `127.0.0.1:8795` e aceita somente requisições com host local. As ações nativas são fixas no código; o navegador não envia comandos arbitrários.

## Perfis e backups

`profile-jobs.mjs` cria backup das chaves de Registro antes de aplicar Basic/Medium/Ultimate. Ainda assim:

- Crie um ponto de restauração antes de usar o perfil Ultimate.
- Alguns ajustes exigem administrador e reinicialização.
- Comandos de boot/segurança e limpeza recursiva são bloqueados.
- Use por sua conta e risco.

## Build

O executável único extrai o pacote para `%LOCALAPPDATA%\NtfdBoost`. O ZIP embutido é gerado pelo próprio build; não substitua o `package.zip` por um arquivo externo.
