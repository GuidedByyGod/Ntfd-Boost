# Falsos positivos no VirusTotal — Ntfd Boost

Arquivos gerados em 12/11/2026:

- Instalador único: `NtfdBoost-Setup.exe` — 128.509.440 bytes
  - SHA-256: `236befda5b70d125779b91e5b9de978f8e7d023d6f5df35ecb38fde9a23c2ad8`
- Aplicativo interno: `NtfdBoost.exe` — 459.264 bytes
  - SHA-256: `616bcf4bcef7b744847fc0b4349281b718021f06014369439b166afbd8050b2a`

Os dois executáveis estão **sem assinatura Authenticode** no momento.

## Por que aparecem detecções

O Ntfd Boost é um otimizador que:

- exige privilégios de administrador;
- altera Registro, serviços, inicialização e arquivos de cache;
- inicia PowerShell/cmd para aplicar ajustes;
- extrai o painel local para `%LOCALAPPDATA%\NtfdBoost`.

Esses comportamentos são usados por ferramentas de sistema, mas também por malwares. Por isso alguns motores usam heurística/ML e retornam nomes genéricos como `Wacatac.B!ml`, `W32.Malware` ou `Malicious`. Não há injeção em jogos, rootkit, mineração, keylogger ou persistência oculta.

## Como reduzir de verdade

1. **Assinar os executáveis com um certificado de code signing confiável (OV/EV).**
   O suporte já está no build:
   - `NTFD_SIGN_PFX`: caminho do `.pfx`
   - `NTFD_SIGN_PASSWORD`: senha
   - `NTFD_SIGN_TIMESTAMP`: URL do timestamp (padrão DigiCert)
   O script usa `signtool` do Windows SDK.
2. **Enviar o falso positivo para a Microsoft.** O `Wacatac.B!ml` é detecção ML e costuma ser removida após revisão:
   https://www.microsoft.com/en-us/wdsi/filesubmission
3. Enviar também para os outros motores que marcaram:
   - McAfee: https://www.mcafee.com/enterprise/en-us/threat-center/false-positive.aspx
   - Bkav: https://www.bkav.com/false-positive
   - SecureAge: suporte no site do fabricante
4. Publicar o SHA-256 e o código-fonte/build para os usuários conferirem.
5. Repetir o envio a cada novo build até a reputação ficar estável.

Sem certificado de assinatura, é impossível garantir 0 detecções em 69 motores. O resultado atual é 4/69; 65 motores não detectaram nada.

## Observação

O Ntfd Boost não possui auto-update. Cada versão é distribuída manualmente pelo autor; o app apenas mostra a versão/build instalada.
