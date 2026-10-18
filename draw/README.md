# Moonglow Loot Draw

Aplicação estática para sortear loot de dungeons de Ultima Online.

## Funcionalidades
- Criar sessão como anfitrião e partilhar um código.
- Outros jogadores entram com esse código e recebem as atualizações em tempo real.
- Adicionar/remover jogadores e baús.
- O anfitrião sorteia uma ordem aleatória de jogadores.
- Os baús mantêm a ordem numérica: baú 1 vai para o jogador na posição 1, baú 2 para a posição 2, etc.
- Revelar as atribuições uma a uma para o grupo acompanhar o sorteio.
- Copiar o resultado final.

## Publicar no GitHub Pages
1. Cria um repositório GitHub, por exemplo `uo-dungeon-draw`.
2. Coloca `index.html` e `README.md` na raiz do repositório.
3. Vai a **Settings → Pages**.
4. Em **Build and deployment**, escolhe **Deploy from a branch**, branch `main`, pasta `/ (root)`.
5. Guarda e abre o URL apresentado pelo GitHub Pages.

Não é necessário Node.js, build ou backend próprio.

## Como funciona a ligação
A página é estática e o tráfego do sorteio é enviado diretamente entre navegadores via WebRTC. Para descobrir e estabelecer a ligação inicial, usa PeerJS Cloud (sinalização pública). Portanto, não há um servidor de aplicação teu, mas **não é uma solução 100% independente de serviços externos**. Os participantes precisam de internet e o anfitrião tem de manter a página aberta. Se o anfitrião fechar a página ou perder a ligação, a sessão termina.

## Utilização
1. O anfitrião abre a página e clica **Criar sessão**.
2. Partilha o código com os participantes.
3. Todos entram com o código.
4. O anfitrião adiciona jogadores e baús (um de cada por participante).
5. Clica **Sortear e revelar** e revela as atribuições uma a uma.

## Limitações e notas
- A lista e o resultado vivem na memória do anfitrião; atualizar/fechar a página termina a sessão.
- O anfitrião é a autoridade da sessão. Para um sorteio mais confiável, todos devem concordar com a lista final antes do sorteio.
- PeerJS Cloud, CDN e os serviços de rede necessários têm de estar acessíveis. Redes restritivas/NAT podem impedir ligações WebRTC.
- Esta versão é um protótipo leve, sem contas, persistência, chat ou controlo de identidade.
