# Compatibilidade e escopo — 0.16.6

Alvo: Windows 10 2004 (build 19041) ou mais recente e Windows 11, com suporte x64. Windows 10 Pro 22H2 build **19045.6466** é um sistema alvo suportado; a confirmação no PC que apresentou o problema permanece necessária.

## Correção de 0x80070057

A janela de configurações exigia `DWMWA_USE_HOSTBACKDROPBRUSH` mesmo no tema preto. A Microsoft documenta esse atributo a partir do Windows 11 build 22000. No Windows 10, a chamada obrigatória podia retornar `E_INVALIDARG` (`0x80070057`) e impedir a abertura das configurações.

Agora o sistema detecta a capacidade disponível. No Windows 10, o efeito não é exigido: o painel utiliza uma superfície escura legível no mesmo HWND. Falhas de material também recuam para uma cor sólida. Se o compositor/driver não puder inicializar, há uma segunda opção de desenho com janela layered e Direct2D/DC, incluindo a animação de escala, áreas de clique e recalculação de DPI.

O desfoque nativo de desktop não é prometido em sistemas que não disponibilizam essa API. A prioridade é manter controles, leitura e interação funcionando. Não declaramos que o caminho simulado em Windows 11 substitui um teste real no Windows 10.

Referência oficial: https://learn.microsoft.com/windows/win32/api/dwmapi/ne-dwmapi-dwmwindowattribute

## Testes executados

- Preto e Liquid Glass com a capacidade exclusiva do Windows 11 desativada.
- Preto e Liquid Glass com o compositor desativado, utilizando o fallback layered.
- Escalas de 100%, 125%, 150% e 200%, com troca de DPI e cliques reais roteados pelos eventos Win32.
- Hit test de pixels do Windows sobre os botões no fallback layered.
- Expansão por hover e posição de mídia atualizada ao abrir o notch.
- Capturas e logs em `previews/release-compat`, `previews/compat-clicks-test.log` e `previews/notch-input-test.log`.

Esses testes foram executados em Windows 11 com as capacidades desativadas para exercitar os caminhos alternativos. Não houve acesso ao computador do amigo nem a uma VM Windows 10 nesta sessão. Esse teste final deve ser feito com o novo pacote; não existe garantia de funcionamento idêntico em todo driver/configuração de Windows.

## Temporariamente fora das versões distribuídas

Dock, substituição do menu Iniciar/tecla Windows e notificações do AVOR estão desativados, inclusive quando um perfil antigo tem essas opções ligadas. Suas opções de configuração ficam ocultas. A compilação padrão não registra atalhos da tecla Windows para o dock, não oculta a barra nativa e não inicia o leitor de notificações.

O código e as preferências anteriores foram preservados para trabalho futuro. O recurso de desenvolvimento `desktop-extras` não faz parte do build distribuído. O instalador atual não prepara certificados nem identidade de notificações; o Windows continua com sua barra e notificações normais.
