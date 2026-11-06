# AVOR Assistant 0.16.6

Windows 10 2004 (build 19041) ou mais recente / Windows 11, com suporte a aplicativos x64.

Execute AVOR-Assistant-Setup-0.16.6-Windows-x64.exe e siga o assistente. Quem usa uma versão anterior pode instalar por cima: notas, calendário e preferências permanecem no perfil local de cada usuário/computador.

Esta versão inclui o notch, música/letras, notas, agenda, sistema, arquivos e utilitários. Dock e notificações estão temporariamente desativados. A barra de tarefas, o menu Iniciar e as notificações do Windows permanecem nativos. Não há preparação de certificado de notificações neste instalador.

Configurações > Sobre > Verificar se há atualizações consulta o GitHub, baixa e verifica o arquivo e permite instalar/reiniciar. As versões que tinham esse botão em espera precisam desta instalação manual uma vez. Veja UPDATES.md.

O tema usa as capacidades disponíveis no computador. Windows 10 e drivers sem o efeito nativo recebem um fallback legível; uma falha de material não deve impedir a abertura e os cliques. Veja COMPATIBILITY.md, incluindo a correção do erro 0x80070057.

O pacote inclui os motores locais de conversão e download. Não é necessário instalar Rust, Python ou SDKs de desenvolvimento. Downloads por link e letras dependem da internet e do conteúdo disponível no serviço. Letras por palavra dependem de timestamps reais; o ajuste de teste padrão é +1,5 segundo.

É uma versão de teste, sem assinatura pública de editor. O Windows pode exibir um aviso de editor desconhecido. Confira a origem e o checksum; não é necessário desativar o antivírus.

O pacote não inclui notas, eventos, clipboard, senhas ou preferências pessoais do computador onde foi gerado. O perfil fica em %LOCALAPPDATA%\AVOR Assistant\profile. A desinstalação pelo Windows preserva esse perfil.
