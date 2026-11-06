# AVOR Assistant — teste em outro computador

Requisitos: Windows 10 2004 ou mais recente / Windows 11, com suporte a aplicativos x64.

1. Copie AVOR-Assistant-Setup-0.16.3-Windows-x64.exe para o outro PC e execute.
2. Escolha os atalhos e se deseja iniciar com o Windows.
3. Abra o AVOR. As configurações do notch, dock, aparência e idioma ficam na engrenagem.

A opção de letras está temporariamente oculta. Reprodução, volume e demais controles de música continuam disponíveis. O código das letras foi preservado para trabalho posterior.

O instalador inclui os componentes locais de conversão e download. O programa principal usa o runtime C estaticamente vinculado. Não é necessário instalar Rust, Python ou o SDK de desenvolvimento. Serviços online, como clima e download por link, continuam dependendo de internet e da disponibilidade do serviço.

## Notificações reais do Windows

A tarefa opcional de notificações vem desmarcada. Marcá-la autoriza instalar o certificado público local de teste AVOR Assistant em TrustedPeople e registrar a identidade do aplicativo. Essa etapa abre o pedido de autorização de administrador do Windows. Não instala nada em Root e não altera o Defender. A chave privada do certificado não acompanha o instalador.

Depois, abra Configurações do AVOR → Área de trabalho → Notificações e solicite a permissão de leitura ao Windows. Sem essa preparação, o restante do aplicativo funciona, mas o espelhamento de notificações reais pode não estar disponível.

É um pacote de teste, ainda sem assinatura pública de publicação. O Windows pode mostrar um aviso de editor desconhecido. Confira que o arquivo veio deste projeto; não é necessário desativar o antivírus.

## Dados e desinstalação

Cada usuário e computador cria seu próprio perfil em %LOCALAPPDATA%\AVOR Assistant\profile. Este pacote não inclui as notas, eventos, histórico de clipboard, atalhos pessoais, localização, senhas ou configurações do PC onde foi gerado.

Desinstale pelo menu de aplicativos instalados do Windows. Os dados do perfil são preservados. O certificado local de teste, se autorizado, pode ser removido depois em certlm.msc → Pessoas Confiáveis → Certificados → AVOR Assistant.
