# Atualizações do AVOR Assistant

Configurações → Sobre → Verificar se há atualizações.

1. O botão consulta somente o repositório público `avorlab/avor-assistant-releases`, por HTTPS e sem credenciais.
2. Se houver uma versão superior compatível, o botão oferece o download.
3. O download ocorre em segundo plano; tamanho e SHA256 precisam coincidir com os dados publicados pelo GitHub.
4. Depois da verificação, o usuário escolhe **Instalar e reiniciar**. Um auxiliar temporário aguarda o encerramento normal, executa o instalador por usuário e reabre o aplicativo.

Não há consulta automática ao iniciar, token embutido, solicitação para desativar proteções do Windows ou substituição do perfil. O código-fonte continua no repositório privado. Os dados permanecem em `%LOCALAPPDATA%\AVOR Assistant\profile`.

O canal atual é de testes: versões `0.x` podem receber prereleases do GitHub com tags numéricas `vX.Y.Z`. Uma futura versão `1.x` ignora prereleases. Tags não numéricas, rascunhos, nomes de arquivos inesperados, URLs fora do repositório e arquivos sem SHA256 são rejeitados. Cada release precisa incluir `AVOR-Assistant-Setup-X.Y.Z-Windows-x64.exe`.

É uma verificação de integridade ligada ao repositório e ao HTTPS, não uma assinatura pública de editor. Não apresentamos o SHA256 como assinatura Authenticode. O instalador ainda pode mostrar o aviso normal de editor desconhecido.

As versões antigas que tinham o botão em espera (inclusive a 0.16.3) não podem adquirir essa função por conta própria: é necessário instalar o novo pacote manualmente uma vez. A partir dele, o botão funciona para próximas versões.

## Validação

- Comparação estrita de versões e seleção de release/asset, rejeição de origem e digest inválidos.
- SHA256 do Windows (BCrypt), com vetor conhecido, corrupção e truncamento.
- Consulta HTTPS real ao GitHub e download real de 165.902.887 bytes da release 0.16.3, incluindo redirects permitidos e verificação do hash.
- Clique no botão real das configurações e chegada do resultado à interface.
- Logs locais em `previews/updater-*.log`, `previews/update-button-test.log` e `previews/0166-*.log`.

O instalador usa a pasta por usuário; o mesmo fluxo pode instalar uma cópia portátil nessa pasta, sem sobrescrever arbitrariamente o executável portátil original. Os motores de utilitários acompanham o pacote completo nesta fase; ainda não há download diferencial.
