# v0.38 — Textos introdutórios aprovados no Figma

**Base:** v0.37. Alteração restrita às cópias da seção 01 (`.hero__copy`) e seção 06 (`.voices__description`) do `index.html`, e a atualização deste README. A cópia foi conferida diretamente nos frames do Figma em **Desktop, Tablet e Mobile**, incluindo estados Preview e DetailOpen da seção 60 Vozes. Todos os breakpoints mostraram textos idênticos em cada seção.

- Hero: `São seis décadas conectando pessoas, livros e ideias. Para celebrar, reunimos memórias e histórias que marcaram nossa trajetória. Explore essa jornada e descubra como a paixão pelos livros continua nos levando mais longe.`
- 60 Vozes: `Autores, editores, livreiros e outros apaixonados por literatura compartilham experiências e inspirações em 60 conversas especiais.` + quebra de linha aprovada no Figma + `Um episódio para cada ano da nossa história, celebrando tudo o que a leitura nos proporciona.`

**Figma Hero:** `3559:1712`, `3575:2061`, `3559:1758`.
**Figma 60 Vozes:** `3639:1919`, `3640:2208`, `3640:3028`, `3640:2645`, `3640:5959`, `3640:2790`, `3641:6083`.

**QA realizado:** Chromium, em larguras 320, 360, 390, 430, 614, 615, 768, 1023, 1024, 1440 e 1920px; sem overflow horizontal, sem sobreposição entre texto e componentes adjacentes e sem erros JS. As fontes carregadas por rede e URLs temporárias de imagens do Figma não estavam disponíveis no ambiente de teste, limitação herdada da versão anterior. A verificação de altura de linhas foi feita com fonte fallback, respeitando o conteúdo original do Figma.

Não foi alterado nenhum componente, token, estado, imagem, iconografia, estrutura CSS ou JS. O trecho `HeroDescription` no Figma ainda se chama *Placeholder Copy* no nome da camada, mas contém a cópia final aprovada. Outros textos Lorem ipsum fora dessas duas introduções não foram modificados.

---

# v0.37 — Pill NN/60 no modal de 60 Vozes: Tablet e Mobile

**Base:** v0.36. Atualização pontual solicitada após alteração do Figma. Escopo restrito ao CSS do modal de 60 Vozes; nenhuma seção externa, estrutura HTML, script JS, variante de card, asset original, dado de demonstração ou regra Desktop foi modificada.

**Referências Figma atualizadas:** instâncias `VoiceEpisodeDetailDialog / Tablet` (`3719:3021`) e `VoiceEpisodeDetailDialog / Mobile` (`3719:3052`). Em ambas, o componente original `ProductTag` (tom blue) com label `01/60` fica **ao lado de `EpisodeAuthorName`**, numa fileira horizontal com **gap de 10px**. No Figma, a pill mede 52×19px quando Nunito está carregada (texto 10px, padding horizontal 12px); o protótipo reaproveita a instância preexistente `.voices-detail__number`, sem recriar `ProductTag`.

- **Tablet (615–1023px):** exibida e explicitamente mantida a pill junto ao título do modal, com gap de 10px. O HTML v0.36 já continha a tag e sua exibição padrão; a v0.37 fixa o contrato responsivo sem alterar demais propriedades.
- **Mobile (até 614px):** removida somente a regra que escondia `.voices-detail__number`. O componente original agora aparece junto ao título de 21px, com gap de 10px, como na referência revisada. Retrato, duas capas, CTA, vídeo, padding, raio e rolagem do diálogo permanecem intactos.
- **Desktop (a partir de 1024px):** sem alterações, inclusive estilo e geometria da tag no modal e nos cards.

**QA Chromium:** testes em 320, 375, 390, 430, 614, 615, 768, 900, 1023, 1024 e 1440px. Nos 11 tamanhos, pill `01/60` visível junto ao nome, gap de 10px, ausência de overflow horizontal na página, abertura/fechamento Escape, restauração de foco, scroll lock e ocultação da navegação flutuante validados. Em 390px, diálogo de 326px com duas capas; em 768px, diálogo de 704px com três capas. Sem erros JavaScript. As capturas do QA não são distribuídas no ZIP.

**Limitações herdadas:** algumas fotos e capas ainda usam URLs temporárias originais do Figma; a fonte Nunito não carregou no ambiente de QA offline, por isso a tag mediu aproximadamente 49×19px em vez de 52×19px. Não houve substituição de assets nem ajustes artificiais de tipografia. A descrição da v0.36 abaixo documenta o estado *daquela versão*, anterior à revisão do Figma; a regra de ocultação citada lá foi substituída pela v0.37.

---

# v0.36 — 60 Vozes: implementação Mobile (até 614px)

**Base:** v0.35, mantendo a seção 60 Vozes Desktop/Tablet já corrigida e as demais seções 01–05. Implementação restrita a regras CSS do breakpoint Mobile em `index.html`, comentários descritivos e título do arquivo. Os componentes HTML, JavaScript, dados de demonstração e assets da v0.35 foram preservados.

**Referências Figma:** `3640:2790` (Leitura60Voices / Mobile / Preview, 390×545px), `3641:6083` (Mobile / DetailOpen, 390×1028px) e componente/instância `3719:3052` (VoiceEpisodeDetailDialog / Mobile, 326×645,38px na composição atual, annotation original ~637px).

- Seção com fundo Brand Primary e **48px de padding vertical**, ContentContainer Fill e **32px de padding lateral**. Permanecem título e sublinhado local com cinco segmentos coloridos, descrição e **gap de 36px**.
- Grade de **dois slots Fill por fileira**, separados por **36px**, foto 1:1 e raio 8px; o card Mobile do estado Preview apresenta padding **12px**, gap vertical 12px e radius 16px. Em 390px, largura de **145px**, foto **121px**, altura medida ~168px. Mantido `ProductTag NN/60` original.
- **Apenas o episódio demonstrativo 01/60 (Lê Teles)** permanece; não foram criados convidados, “Em breve” ou botão de carregar mais sem dados reais. Com um único registro, o card ocupa exatamente um slot, centralizado, sem se expandir para as duas colunas.
- **Modal Mobile**: largura Fill, com margem lateral de 32px; **326px de largura em viewport 390px**, padding 24px, radius 16px, estrutura empilhada, gap 24px, retrato superior **278×150px** com `object-fit: cover`, corpo abaixo, nome **21px**, biografia **14px**, e vídeo em proporção ~16:9. A `ProductTag` presente no layout Desktop/Tablet do popup não aparece no componente Figma Mobile e é ocultada *somente dentro do modal mobile*; permanece no card da grade.
- Exibição de **duas capas 64×90px + CTA Ver mais 64×90px**, gap16px; o terceiro slot de livro do Desktop/Tablet é ocultado apenas na variante Mobile. Ícones de fechar/play/livros continuam sendo os SVGs originais existentes; não são criados vetores novos.
- Interação existente preservada: card publicado abre `<dialog>`, X/Escape fecham, foco volta ao card, backdrop bloqueia o fundo e menu flutuante global fica oculto enquanto aberto. Em dispositivos baixos, o próprio modal rola; em telas abaixo de 351px, a fileira de capas pode rolar horizontalmente sem redimensionar os slots aprovados.
- **Inconsistência no Figma:** no Preview Mobile o card de referência usa padding **12px**, enquanto o frame com modal aberto contém instâncias de card com padding **16px**. Seguiu-se o Preview (referência do estado inicial) para a grade, sem modificar o master do componente.
- Faixa de cinco cores e navegação flutuante continuam globais e únicas: não foram duplicadas por seção. A única regra visual afetada fora da seção é o texto do `<title>` do protótipo.

**QA Chromium:** 320, 350, 360, 375, 390, 430, 614, 615, 768, 1024, 1440 e 1920px, incluindo teste de viewport baixa a 390×450px. O Mobile mostra 2 slots, sem overflow horizontal; modal com duas capas e retrato de 150px; todas as ações X, Escape, retorno de foco, scroll lock e ocultação de navegação validadas. Em 615px e acima, Tablet/Desktop conservam o modal de **3 capas**, seus próprios paddings e orientação horizontal. Nenhum erro de JavaScript reportado. Arquivos de QA e métricas não entram no ZIP principal.

**Limitações anteriores, não resolvidas pelo ajuste responsivo:** fotos de Vozes e capas permanecem nos links temporários de assets originais do Figma fornecidos pelas versões anteriores. Esses URLs podem expirar ou ser bloqueados ao executar offline, e não foram substituídos por imagens não originais. Fontes Nunito/Bogart dependem dos recursos externos/locais indicados no projeto; em testes offline com fallback tipográfico, a altura medida do modal Mobile foi ~661px, contra ~645px no Figma. Evitou-se fixar altura ou cortar texto artificialmente.

---

# v0.35 — 60 Vozes: implementação Tablet (615–1023px)

**Base:** v0.34, com Desktop da seção 60 Vozes e suas correções aprovados. Nesta versão, **somente** a responsividade da seção 06 e do modal no Tablet foi implementada. Não foram modificados o HTML de nenhuma seção anterior, os dados demonstrativos, o JS nem os SVGs originais.

**Referências Figma:** `3640:2645` (Leitura60Voices — Tablet / Preview, 768×486px), `3640:5959` (Tablet / DetailOpen) e `3719:3021` (instância do componente VoiceEpisodeDetailDialog / Tablet, 704×491,88px).

- Seção azul Brand Primary com padding vertical de **48px**, ContentContainer de largura Fill e margens internas horizontais de **32px**. Mantidos o título Nunito ExtraBold de 28px, o sublinhado local de cinco cores, descrição centralizada de 18px e gaps de 36px.
- Fileira projetada para **quatro slots Fill**, com gap de 36px. A 768px, cada posição tem **149px** e imagem de **117×117px**; o componente mantém seus próprios padding 16px, gap 12px, radius 16px, ProductTag original e fonte 16px.
- A v0.34 exibe **somente um episódio demonstrativo (01/60)**. Por decisão editorial já aprovada, não foram introduzidos três outros cartões nem slots “Em breve”. O único card ocupa uma posição de 149px, centralizado na fileira, sem alargamento indevido. O botão Carregar mais não é exibido sem outros episódios disponíveis.
- Modal Tablet de **704px** no viewport de referência, raio 32px, padding 24px, gap 24px, retrato com 250px de largura e conteúdo com 382px. Cada capa e a caixa VER MAIS passam para 64×90px, com ícone original de 20×20px; player conserva proporção 382/214,875, sem vídeo inventado. A altura é de conteúdo fluido para não truncar texto, embora a referência tenha ~492px.
- Em telas Tablet mais estreitas (615–767px), as duas colunas permanecem na mesma orientação; a coluna do retrato pode encolher até 175px para respeitar o espaço mínimo de 304px da fileira de livros, mantendo a variante estrutural Tablet.
- O `<dialog>` existente preserva abertura por clique/Enter/Espaço, fechar por X/Escape e restauração de foco, backdrop, bloqueio do scroll do fundo e ocultação temporária do menu flutuante.
- Breakpoint Mobile **até 614px** permanece pendente, como no Figma; a seção é ocultada apenas nesse intervalo. Desktop **a partir de 1024px** mantém o CSS já aprovado da v0.34.

**QA Chromium executado na v0.35:** viewports **390, 614, 615, 640, 700, 768, 900, 1023, 1024, 1440 e 1920px**. Sem rolagem horizontal na página nem exceções de JavaScript; uma única instância de `VoiceEpisodeCard`; na referência 768px o card mede 149×172px e a foto 117×117px. A estrutura Desktop mantém 874px de largura no diálogo e 187,33px por card em 1440/1920px. Modal Tablet: 704px em 768px de viewport, retrato 250px, conteúdo 382px, três capas e ícone original em 20px; sem overflow interno horizontal. Testes de interação com clique, Enter, Escape, botão X, retorno de foco, bloqueio da página e ocultação do menu flutuante passaram. Em dispositivos de altura reduzida (**450px**), o modal faz scroll interno e mantém acesso ao conteúdo; não corta o player. A altura efetiva do diálogo foi ~525px no fallback tipográfico do navegador de teste, em vez dos ~492px do Figma, pois as fontes externas foram bloqueadas. Capturas de QA ficam fora do pacote, evitando incluir imagens que mostram assets originais inacessíveis no ambiente de teste.

**Limitação preexistente:** retrato e capas ainda usam URLs temporárias do Figma (não substituídas por outras imagens). A fonte Nunito depende de carregamento externo. Isso pode afetar a comparação fotográfica e a altura do texto, sem justificar alterações no componente.

---

# v0.34 — Correção vetorial do ícone “Ver mais” (60 Vozes)

**Mudança restrita ao arquivo** `assets/voices-dialog-books-original.svg` do popup `VoiceEpisodeDetailDialog / Desktop`, exportado do Figma (nó `I3717:2989;3713:2093`). Não houve mudança de CSS, HTML ou JS nem de nenhum componente aprovado.

O arquivo SVG local da v0.33 tinha **duas coordenadas faltando** no contorno do segundo livro. Isso criava diagonais artificiais, distorcendo o desenho e ocultando visualmente os traços esperados. Os dois segmentos da curva cúbica foram recuperados **literalmente do SVG original do Figma**, sem reinterpretar ou redesenhar. Preservados: `viewBox="0 0 24 24"`, dimensões de `24×24px`, traços `#0033A0` de `2px` e os demais caminhos vetoriais.

**QA:** Playwright Chromium em 1024, 1440 e 1920px. Após abrir o card disponível, o SVG local carregou com `naturalWidth=24` e `naturalHeight=24`, renderizou em 24×24px, o popup abriu, Escape fechou e o foco retornou ao card. Capturas feitas da ação “VER MAIS” e do popup completo no Desktop. Os assets e scripts anteriores permaneceram **byte a byte idênticos**; apenas este SVG e a documentação foram atualizados.

---

# v0.33 — Auditoria 1:1 do VoiceEpisodeCard e centralização Desktop

**Escopo: Seção 06 (60 Vozes) Desktop.** Origem: protótipo v0.32, preservado integralmente fora de três regras CSS. Nenhum texto, ativo, script, seção 01–05, breakpoint anterior, modal, componente, foto ou dado editorial foi alterado. Não foram criados episódios ou nomes de convidados.

## Conferência com Figma

Componentes: `VoiceEpisodeCard / Slot 01` (`3702:2661`), mestre `status=available, size=default` (`3701:2069`), `EpisodeNumber / ProductTag` (`I3702:2661;3701:2067`) e `VoiceEpisodeRow` (`3639:2002`). Dados extraídos diretamente dos nós, sem reconstruir variantes:

- **Fileira:** max-width **1304px**, gap **36px**, até **6 cartões** de larguras iguais e fluidas; linha centralizada. O cálculo é `(largura útil - 5 × 36px) / 6`. Em 1920px e 1440px, largura por card **187,333px**. Se houver menos de 6 episódios disponíveis, os cards **não crescem** e ficam centralizados. A sétima unidade passa à segunda linha centralizada. Implementado apenas no container `.voices__row`, sem alterar o contrato visual do `VoiceEpisodeCard`.
- **Card:** `187,333 × 210,333px` na largura de referência; fundo branco, raio **16px**, padding **16px**, gap vertical **12px**. `AuthorPhoto`: **155,333 × 155,333px**, ratio **1:1**, raio **8px**. `AuthorName`: Nunito ExtraBold **16px**, line-height **115%**, letter-spacing **−0,304px**, altura visual trim **11px**, centralizado. Usado `text-box-trim:trim-both` / `text-box-edge:cap alphabetic` quando suportado, sem mudar o tamanho da fonte nem cortar ascendentes/descendentes com altura fixa.
- **ProductTag original:** **52×19px** na renderização Nunito do Figma (antes tinha **26px de altura indevida**). Posição `top/right:6px` dentro da foto, fundo `#0033A0`, texto branco Nunito ExtraBold **10px**, line-height 14px, raio 999px, padding horizontal 12px. Na QA sem Nunito de rede, o fallback produziu largura 49px; no navegador com Nunito, a medida é determinada pela métrica correta do texto (28px) + 24px de padding. Nenhum ícone foi introduzido no card; a tag é o componente `ProductTag`, não um ícone.
- **Diálogo:** os arquivos vetoriais originais de **livros (24×24px), play (24×24px) e fechar (18×18px)** foram conferidos e carregam localmente; mantidos os SVGs de origem do Figma, sem substituições. O popup continua abrindo ao clicar no único card demonstrativo e fechando por X ou Escape.

## QA realizado

Chromium headless a 1024, 1280, 1440 e 1920px: um único card centralizado com precisão de ~1px; largura 187,328px, altura **210,344px**, foto **155,328px** e tag **19px** na largura 1920px. Simulações temporárias em DOM com 2, 3, 5, 6 e 7 cartões, sem adicionar convidados ao arquivo distribuído: em cada fileira **máximo 6**, todos do mesmo tamanho e centralizados, com a sétima unidade na segunda linha. Sem overflow horizontal nem erros de JavaScript. Popup abre, fecha e devolve foco ao card. Os 3 SVGs originais do popup carregam no navegador de teste com suas dimensões corretas. Regressão da visibilidade de Vozes Tablet 768 e Mobile 390 preservada. Todos os assets de origem são idênticos byte a byte.

## Limitações de fidelidade ainda pendentes

**Não considerar a aparência fotográfica validada 1:1:** o projeto v0.32 contém URLs temporárias do Figma no retrato do único card e nos assets do diálogo (retrato e capas), e o ambiente de QA não acessa esse host. Não inserimos fotografias alternativas, placeholders novos, recortes de screenshot nem URLs fabricadas. Exportar os **originais AuthorPhoto**, `VoiceEpisodePortrait` e as capas do componente em arquivos locais para testes completos e publicação durável no GitHub Pages. A fonte Nunito, quando não carregada, também difere em largura de texto em alguns pixels; para correspondência 1:1 em todos os dispositivos, hospedá-la/licenciá-la conforme a tipografia original. A Bogart Extrabold continua configurada conforme a v0.30, sem alteração.

---

# v0.32 — Vozes: somente registros disponíveis + popup Desktop

**Solicitação aprovada desta etapa:** remover o estado `Em breve` da lista e ativar o popup ao clicar nos cards disponíveis. Base: protótipo único v0.31, preservando DOM, CSS, JS e assets de todas as seções 01–05 e a base de Vozes. Foi modificada somente a quantidade de cards disponíveis, o mecanismo de navegação de Vozes e a inclusão da instância `VoiceEpisodeDetailDialog / Desktop` com seus estilos e SVGs originais.

## Conteúdo exibido e regra editorial

- O Figma de Vozes usa **Lê Teles (01/60) como conteúdo de DEMONSTRAÇÃO**, não prova de convidada real/confirmada. A v0.32 conserva **apenas esse único exemplo** para testar a interação. Não significa que a confirmação editorial foi verificada. Quando houver relação real de episódios confirmados, substituir o conteúdo demonstrativo com os dados fornecidos, sem renumerar posições existentes.
- Removidas as cinco instâncias duplicadas “Lê Teles” 02–06. Nenhum card “Em breve” aparece ou pode ser criado por JS. O fluxo que gerava placeholders de 07 a 60 foi retirado.
- O botão **Carregar mais** desaparece enquanto não existir mais nenhum registro disponível para exibição. Não criar convidados/episódios confirmados por inferência nem duplicar o primeiro registro.
- A regra de **identificador de episódio NN/60** permanece ligada à posição original (01/60 no único exemplo). Sem gerar números falsos.

## Popup / `VoiceEpisodeDetailDialog` Desktop

- Original Figma componente `3713:2112` (instância `3717:2989`) de **874×544px**, com fundo Surface/Default, raio 32px, padding 24px, colunas retrato de 320px e conteúdo de 482px separados por 24px.
- Estrutura original: retrato 320×496px (canto arredondado 16px), nome Nunito ExtraBold 24px, `ProductTag 01/60`, biografia demonstrativa Nunito SemiBold 14px, 3 capas ilustrativas 71×100px + `VER MAIS` 71×100px, player placeholder 482×271px no ratio 16:9. Nenhum elemento novo ou versão simplificada foi adicionado no lugar dos slots existentes.
- Exportados os **três SVGs originais do Figma**, agora locais: `voices-dialog-close-original.svg` (18px), `voices-dialog-play-original.svg` (24px) e `voices-dialog-books-original.svg` (24px).
- Clique no card, **Enter** ou **Espaço** abrem `<dialog>` nativo. X e **Escape** fecham e **devolvem foco ao card**. O backdrop `rgba(0,0,0,.4)` é exterior ao componente, o scroll da página é bloqueado e a navegação flutuante global é ocultada enquanto aberto, reaparecendo ao fechar. Não foi inventado fechamento por clique fora.
- A v0.31 usava URLs temporárias de fotos, e o **popup de referência também traz retrato e capa via Figma**. Neste ambiente, a rede bloqueia o download; como não recebemos os originais em arquivo local, as imagens permanecem referenciadas pelos assets originais em URLs de exportação do Figma e **podem não carregar no GitHub Pages após expiração**. Não substituir por outra fotografia. A conferência 1:1 de imagens depende de exportar três assets originais (miniatura, retrato, capa) e salvar localmente.
- **Não inventar dados:** não há YouTube Video ID/URL, URL da página de livros nem biografia real fornecidos. O mockup original utiliza um placeholder de player e livros, mantidos visuais. `VER MAIS` permanece desabilitado sem destino; player é representação estática, não reproduz conteúdo. Esses campos precisam ser preenchidos com os dados confirmados antes de produção.
- A altura medida em QA com fonte fallback foi **~576px**, acima dos ~544px do Figma devido ao texto e métricas tipográficas. Não forçar cortes de conteúdo nem alturas fixas para encobrir diferença de fonte. A fonte Nunito continua dependendo de carregamento externo.

## QA

Chromium: abertura e fechamento por clique/Enter/Espaço/X/Escape em **1024, 1280, 1440 e 1920px**; retorno de foco; bloqueio e restauro de scroll; ocultação/restauro da única navegação global; tag e nome do episódio; 3 capas; SVGs originais com medidas corretas; nenhum erro JS ou overflow horizontal. A seção Vozes permanece oculta no **Tablet 768px** e **Mobile 390px**, cuja implementação será etapa posterior. DOM das seções 01–05 comparado idêntico à v0.31; todos os assets anteriores preservados byte a byte. Capturas QA fora do pacote em `qa-vozes-popup-1920.png` e `qa-vozes-um-episodio-1920.png`.

---

## Histórico anterior

# Leitura 60 Anos — v0.31 / Seção 06: 60 Vozes (Desktop)

## Implementação e origem Figma

Foi integrada **somente** a seção Desktop "60 Vozes" ao mesmo `index.html` da v0.30. Os HTMLs das cinco seções anteriores, suas regras CSS, JS e todos os arquivos de assets anteriores foram preservados byte a byte; nenhuma mudança nos breakpoints aprovados. A navegação flutuante e as listras decorativas continuam globais e únicas.

- Figma `OtFihfNvBMeg5ITRk3ry2t`, frames **Preview `3639:1919` (1920×556.33px)** e **Loaded `3640:2208` (1920×1049px)**.
- Fundo `Brand/Primary #0033A0`, padding vertical **64px**. `ContentContainer` com max-width **1368px**, padding horizontal **32px**; `VoicesContent` vertical com **gap 36px**.
- SectionTitle "60 Vozes": largura 139px, altura 36px, Nunito ExtraBold 28px branco, sublinhado local de cinco cores altura 4px e intervalo de **8px**. A faixa inferior fixa da página permanece separada.
- Descrição temporária original do Figma, centralizada, largura máxima 768px, Nunito SemiBold 18px/115%, cor branca.
- `VoiceEpisodeRow`: seis instâncias aprovadas do **`VoiceEpisodeCard`** por fileira Desktop; gap horizontal e vertical **36px**, grid Fill max-width 1304px. Cada card branco Hug, padding **16px**, raio **16px**, gap interno **12px**; `AuthorPhoto` quadrada raio 8px; `AuthorName` Nunito ExtraBold 16px.
- `ProductTag` aninhado, fundo #0033A0, texto branco Nunito ExtraBold 10px, raio 999px, posicionamento a 6px do topo/direita da foto, valor `NN/60`. Nenhuma variante de ProductTag ou VoiceEpisodeCard foi alterada.
- Botão "Carregar mais" de **172×40px**, fundo branco, texto azul Nunito ExtraBold 18px. Seta SVG original do Figma nó `3640:2030` exportada localmente em `assets/voices-load-more-arrow-original.svg`.
- `FloatingSectionNavigation` global passa a reconhecer a seção 05 (60 Vozes) pelo ID `60-vozes` já definido na v0.30; a variante de fundo escuro usa rail Light Blue/500 (#3BA5F2), **sem criar segunda instância**.

## Estados e dados demonstrativos

A prévia tem **uma fileira com seis cards** conforme o Figma, usando temporariamente "Lê Teles" como label; a imagem de referência original do Figma é repetida, como no mockup. "Carregar mais" acrescenta **uma fileira completa (6 cards) por clique**, mantém as anteriores e encerra ao alcançar **60** episódios, sem repetir números. O valor de uma fileira por clique é uma **regra provisória de prototipação**, pois a annotation do Figma especifica apenas que sejam fileiras completas, não a quantidade por clique. O botão some após o último lote.

Os episódios **07–60** são dados demonstrativos em `coming-soon`, exibindo "Em breve", tag numérica obrigatória e a silhueta prevista na variante; permanecem **inertes**. O primeiro grupo usa a composição disponível da prévia original; a aplicação de status reais e o destino do episódio 01 dependem de conteúdo editorial e URLs definitivas. A variação de conteúdo dos mockups Preview/Loaded não foi tratada como uma regra de mudança dinâmica de dados: carregar mais não altera os seis cards anteriores. Não foi criado modal ou player, pois essa seção não contém modal aprovado nesses frames.

## QA executado

Testes funcionais Chromium em **1024, 1280, 1440 e 1920px**, mais regressão em **1023, 768 e 390px**: seis cards iniciais distribuídos uniformemente, gaps de 36px, botão 172×40px, ausência de overflow horizontal, 10 fileiras completas e sequência exata `01/60`–`60/60` ao acionar 9 vezes, sem duplicatas. A navegação global marcou a quinta seção e utilizou o rail azul claro original; o SVG da seta local carregou corretamente. Em Tablet/Mobile, Vozes permanece oculta para a próxima etapa. **O QA foi feito sem Nunito externa**, logo houve diferenças de cerca de 15px na altura de referência em 1920px (571px vs 556px do Figma); não foram forçadas alturas fixas nem cortados textos para compensar fallback.

## Pendência prioritária — imagem original de autores

**Não considerar o bloco fotográfico validado 1:1 nem pronto para handoff offline.** A fotografia original e a silhueta `coming-soon` foram identificadas diretamente nas instâncias do Figma, porém o container desta sessão bloqueia a conexão de download (`curl: Could not resolve host: www.figma.com`). Para não substituir as ilustrações por imagens inventadas, as duas tags `<img>` desta seção usam **links temporários dos assets originais do Figma**, válidos aproximadamente 7 dias. O CSS tem apenas uma cor de fundo de segurança caso o carregamento falhe; isso NÃO substitui a arte. Exportar as duas imagens originais e alterar `src` das miniaturas para `assets/voices/` antes de hospedar o protótipo em produção/GitHub Pages. As capturas de QA geradas offline mostram slots de fundo neutro porque o navegador de teste não alcança os URLs temporários.

A fonte Bogart ExtraBold continua configurada no código a partir da v0.30, com caminho `./assets/fonts/Bogart-Extrabold.woff2`. Como na versão anterior, o WOFF2 licenciado **não é redistribuído no ZIP**: mantenha o arquivo de fonte já hospedado no repositório em `assets/fonts/`. A Nunito segue hospedada externamente via Google Fonts.

## Estrutura de entrega

`index.html` contém CSS e JavaScript internos e continua acompanhado pela pasta `assets/`. Desktop, Tablet e Mobile das cinco seções anteriores permanecem inalterados. Os screenshots de QA estão fora do ZIP principal, para evitar confundi-los com assets do site.

---

## Histórico (v0.30)

# v0.30 — Bogart Extrabold via WOFF2 no GitHub Pages

Atualização estritamente tipográfica, **sem alterar componentes, layout, breakpoints nem JavaScript** do protótipo v0.29. O CSS de `index.html` agora busca `./assets/fonts/Bogart-Extrabold.woff2` e mantém a mesma família `Leitura Bogart`, peso **800**, normal, `font-display: swap`, `font-synthesis: none`.

## Fonte recebida

O usuário forneceu `BogartWOFF2.zip` contendo nove pesos da família Bogart. A implementação usa **somente** `BogartWOFF2/Bogart-Extrabold.woff2`, cujo metadata WOFF2 indica family `Bogart`, style `Extrabold` e `usWeightClass=800` (validado com fontTools).

**Importante:** por razões de distribuição, este pacote de protótipo **não redistribui o arquivo da fonte**. Copie você mesmo o arquivo do ZIP de fontes fornecido para a pasta `assets/fonts/` de seu repositório GitHub. O arquivo deve ter o nome exato `Bogart-Extrabold.woff2` (respeite maiúsculas e minúsculas). Estrutura esperada:

```text
index.html
assets/
  fonts/
    Bogart-Extrabold.woff2  # copiar do BogartWOFF2.zip fornecido
  gallery/
  ...
```

**GitHub Pages:** se `index.html` está na raiz do site, o caminho `./assets/fonts/Bogart-Extrabold.woff2` é resolvido a partir dela. Ao hospedar na subpasta `/repo/`, o caminho relativo continua válido. Abra Developer Tools > Network e confirme HTTP 200 para o WOFF2; nos dispositivos, o CSS carregará a mesma fonte da web, mesmo que Bogart não esteja instalada localmente.

Nenhuma outra variante de peso foi registrada, pois o Manifesto usa exclusivamente Extrabold 800. A **Nunito** continua dependente do Google Fonts e é uma configuração independente. O arquivo WOFF2 deve ser usado somente se a licença obtida permitir uso e hospedagem na web.

## QA

Validar o carregamento do WOFF2 com `document.fonts.load('800 28px "Leitura Bogart"')`, presença do recurso na Network e alinhamento dos títulos do Manifesto em Desktop, Tablet e Mobile. Os componentes e regras CSS originais das demais seções não foram modificados.

---

# Leitura 60 Anos — Protótipo v0.29 · Depoimentos Mobile

Esta etapa acrescenta **somente o layout Mobile (≤614px)** à Seção 05 de Depoimentos da página. Fonte de partida: ZIP v0.28 fornecido pelo usuário nesta conversa. O mesmo `index.html` contém todo o HTML, CSS e JS internos. Não foi criado outro componente ou outra instância do menu flutuante. Os 23 arquivos originais de `assets/` foram preservados **byte a byte**.

## Fonte Figma e especificação

- Frame `3655:6718` — **Leitura60Testimonials / Mobile / Preview**, largura 390px e altura **747px**; `TestimonialsContainer` Fill com padding horizontal **32px** e vertical **48px** na seção, `TestimonialsContent` com gap de **36px**.
- `SectionTitle` 264×33px na referência: Nunito ExtraBold 24px, padding horizontal de **8px somente neste breakpoint**, sublinhado local com cinco segmentos e altura de 4px. Para telas menores que ~375px, o texto reduz tipograficamente até 21px para não ultrapassar Fill Container, sem mudar os componentes dos breakpoints maiores.
- `TestimonialsPreviewViewport` **450px** de altura, largura Fill (326px em 390), `overflow:hidden`; fade de 245px fica **sobre o viewport**, não nos cards. Os cards permanecem completos e em Height Hug.
- `TestimonialsMasonry` com **uma coluna**, largura Fill e gap **24px**. O frame tem **nove instâncias** dos TestimonialCard originais: os cinco da primeira coluna do Desktop e os quatro da segunda, na mesma ordem do Figma. No Mobile, wrappers das duas colunas usam `display:contents` para empilhar as mesmas instâncias sem criar ou copiar cards; a terceira coluna do Desktop fica oculta. Desktop mantém 13 cards em três colunas e Tablet nove em duas colunas.
- `TestimonialCard` mantém os contratos aprovados sem alterações: padding 24px, raio 16px, identidade/avatar 36px, texto e data no final; mídias wide/portrait usam a mesma configuração original; nenhum truncamento e nenhum ajuste de propriedades por breakpoint.
- Botões `Ver todos os depoimentos` e `Deixe o seu depoimento` agora usam largura Fill (326px na referência), **40px** de altura cada, com **16px** de intervalo. SVGs originais reutilizados. Expandir remove o recorte e fade, mantendo os nove cards e escondendo somente o botão `Ver todos`.

## Fluxo exploratório de envio — Mobile

- Frames `3865:5358` (escolha do perfil), `3865:5570` (Cliente), `3864:5253` (Funcionário), `3865:5804` (Empresa), `3865:6042` (Erros) e `3865:6278` (Confirmação).
- O mesmo `<dialog>` HTML da v0.28 é mantido, com backdrop preto a 40%, largura `calc(100vw - 32px)`, padding **20px** e raio **16px**. Em 390×844: seleção **358×526px**, formulário **358×812px** com rolagem interna e confirmação **358×414px**.
- Na seleção, as três opções de perfil ficam empilhadas (100px de altura, gap 12px). O formulário segue oferecendo campos por perfil, contador de 200 caracteres, arquivo opcional (JPG/PNG/MP4), checkbox de consentimento e validação inline. Escape, Fechar, Alterar perfil, Voltar e Concluir permanecem funcionais.
- **A confirmação é apenas demonstrativa:** não existe backend, armazenamento, publicação nem transmissão de depoimento. Não tratar o estado "Depoimento enviado!" como confirmação real de recebimento. O link para regulamento ainda está pendente.

## QA executado

**Chromium:** layout e ausência de overflow horizontal em **320, 375, 390, 430 e 614px**; regressão de Tablet em **615, 768 e 1023px** e de Desktop em **1024, 1440 e 1920px**. Em 390px, seção 747px, preview 450px, título 264×33px, nove cards visíveis com um único fluxo de coluna e botões 326×40px. Testados expansão para mostrar os nove cards, navegação do modal pelos três perfis, validação obrigatória e confirmação visual. Check de originalidade dos arquivos de `assets/` e equivalência das seções 01–04 e de todos os scripts JS. Capturas PNG de QA estão disponíveis separadamente na pasta do protótipo, mas não são incluídas no ZIP.

**Limitações conhecidas:** Nunito continua dependendo de fonte externa e Bogart de instalação local licenciada; as capturas em ambiente sem rede utilizam fallback e podem apresentar quebra de texto diferente. Alguns assets de outras seções são URLs temporárias do Figma já existentes, fora do escopo. A distribuição dos cards e conteúdo são placeholders do Figma, não depoimentos reais. O fluxo de envio é exploratório e exige validação antes do handoff final.

---

## Histórico — v0.28 e anteriores

# Leitura 60 Anos — v0.28 / Depoimentos Tablet

Implementação responsiva da Seção 05 a partir da v0.27. O protótipo continua num único `index.html` (CSS e JS internos), com `assets/` locais preservados.

**Figma:** preview Tablet `3640:2334` (768×804px), modal Tablet escolha `3859:4623`, modal Cliente `3859:4740`, e estado sucesso `3859:5282`. Os componentes `TestimonialCard` existentes não foram alterados.

- **Tablet 615–1023px:** seção `padding:48px 0`; container largura Fill com 32px laterais; título centralizado 332×36px; gap interno 36px; área Preview 560px com `overflow:hidden` e fade original sobreposto à área, não aos cards.
- **Masonry Tablet:** duas colunas Fill iguais e gap de 24px (a 768px, 340px cada). A referência do Figma mostra 9 cards de teste, organizados em 5 na primeira coluna e 4 na segunda. A terceira coluna do Desktop (quatro cards adicionais) fica **somente oculta no Tablet** — não foi excluída do HTML, para preservar o estado Desktop já aprovado. Nenhum card é reconstruído ou tem suas propriedades alteradas.
- **Expandir:** botão “Ver todos os depoimentos” remove o clipping/fade e deixa o masonry de duas colunas com altura natural; botão de enviar permanece.
- **Fluxo Tablet de envio (exploratório):** diálogo de escolha com opções verticalmente empilhadas (94px, padding 14×18, gap12); formulário com largura de 600px em 768px e altura rolável em janelas pequenas. Preservada a simulação local, sem envio ao backend e sem novas UI além das existentes na v0.27.
- Menu flutuante e listras globais são os únicos já existentes. Nada foi duplicado. A Seção 05 Mobile permanece oculta até a próxima etapa.
- **Regressão:** o HTML e os estilos Desktop de todas as seções e o Mobile das Seções 01–04 foram preservados. Os 13 cards Desktop continuam no DOM para Desktop; não foram adicionados cards.

**QA executado em Chromium:** 615×760, 768×860, 768×650, 900×850, 1023×850, 1024×850, 1440×900, 1920×950 e 390×844. Comprovados preview Tablet 768×804px, viewport 704×560px, 2 colunas de 340px, ocultação da terceira coluna apenas no Tablet, ausência de overflow horizontal; estado expanded sem fade/clipping; modal de perfil (opções 594×94px na largura de referência), campos dinâmicos dos 3 perfis, validação, contador e confirmação local; SVGs dos dois botões carregados e sem erros de JavaScript. Capturas PNG de QA são disponibilizadas separadamente. Fontes externas foram bloqueadas no navegador de QA, então as quebras de texto não foram validadas visualmente como 1:1.

Pendências herdadas do protótipo: a renderização 1:1 de alguns textos depende da fonte Nunito no browser; referências temporárias de SVG do Manifesto em versões anteriores permanecem fora do escopo. Os dados dos cards e as informações de mídia são placeholders do Figma. O fluxo de envio permanece exploratório e precisa de aprovação antes do handoff final.

---

# v0.27 — Seção 05 · Deixe o seu depoimento / Desktop

Esta versão **acrescenta somente o Desktop** da próxima seção do site Leitura 60 Anos ao protótipo único. Arquivo base: v0.26 Manifesto Mobile. As seções Hero, Nossa História, Galeria e Manifesto, seus estilos e seus scripts **não foram alterados** (regressão por comparação de conteúdo e QA de navegador). Não há header/footer extras. A navegação flutuante e as listras globais continuam instâncias únicas.

## Fonte de verdade — Figma

- Arquivo `OtFihfNvBMeg5ITRk3ry2t`, frame **Preview `3624:7405`** (1920×856), **Expanded `3626:7685`** (1920×1804,15; a altura na implementação varia com a fonte disponível).
- Componentes aprovados: **`TestimonialCard`** master `3678:2071`, `authorType=publisher|employee|client` × `media=none|portrait|wide`, 9 combinações. As diferenças no HTML são exclusivamente de dados e presença da mídia, não alterações estruturais por variante. Nos frames originais, a media de teste é bloco cinza e os avatares são círculos sólidos, não fotografias reais.
- `TestimonialsContent`: max-width 1304px; título SectionTitle 308×36px Nunito ExtraBold 28px com cinco segmentos de 4px; gap vertical **36px**; viewport de prévia **580px** com clipping; masonry max-width **1100px**, 3 colunas iguais, gap horizontal/vertical **24px**, cartões Hug; fade de **245px** no viewport, **fora do card**.
- Cartões: fundo `#e5e5e5`, padding `24px`, radius `16px`, gap de blocos `16px`; avatar 36×36px sólido `#525252` na referência; nome Nunito ExtraBold 18px, metadados 14px, corpo 16px/130%, data Nunito Medium 16px **sempre no final**. Mídia `#a7a3a3` com raio de 8px e aspect ratios distintos `wide` / `portrait`. Textos demonstrativos mantidos do Figma (sem nomes de pessoas reais). Layout por coluna segue os 13 cards da referência Desktop.
- Botões: “Ver todos os depoimentos” **271×40px** e “Deixe o seu depoimento” **254×40px**, gap 16px. As setas e ícones são **SVGs originais exportados dos nós Figma `3639:144` e `3624:7670`**, presentes localmente em `assets/testimonials-*`.

## Comportamentos e estados

- **Preview (inicial)**: mostra os cards em viewport de 580px e fade gradual no fim do masonry. 
- **Expandido**: clicar em “Ver todos os depoimentos” remove **somente o limite do viewport, o fade e esse botão**, exibindo as mesmas instâncias de cards por inteiro, com altura Hug. O CTA de envio permanece centralizado. Não foi criado botão de recolher, pois ele não aparece no frame Expanded.
- **Fluxo exploratório de envio**: clicar em “Deixe o seu depoimento” abre `<dialog>` com escolha Cliente, Funcionário(a), Empresa, baseado na seção do Figma `3842:3764`. Formulários incluem os campos por perfil, depoimento obrigatório com limite de 200 caracteres, upload opcional (um JPG/PNG até 1,5 MB ou um MP4 até 20 MB), checkbox de autorização do uso da mídia, validação inline, Escape/Fechar/Voltar/Alterar perfil, confirmação visual. **É simulação de front-end**: não há backend, publicação, persistência ou transmissão de arquivos. “Depoimento enviado!” é o estado de demonstração, não confirmação real de recebimento. O URL real do regulamento está pendente no Figma; o texto aparece como referência, sem link inventado.
- O envio é classificado no Figma como **Fluxo exploratório**; não tratá-lo como handoff aprovado sem a revisão de negócio/design. A seção de cards pode ser validada independentemente do fluxo.

## QA executado

- Chromium headless em **1024×768, 1440×900 e 1920×1040**: seção da prévia **856px**; viewport **580px**; masonry de três colunas até 1100px; botões 271×40 e 254×40; ausência de overflow horizontal.
- Testados: expansão para masonry completo, remoção do fade, CTA mantido, abertura do diálogo, campos Client / Employee / Company, validação obrigatória, caminho de confirmação e fechamento por Escape e botão.
- Conferida navegação flutuante global com a **4ª seção ativa**, sem duplicar menu nem as listras fixas. Regressão de medidas em **1023, 768 e 390px**: a Seção 05 continua oculta porque seus breakpoints ainda não foram implementados.
- **QA tipográfico parcial:** neste ambiente o navegador não dispõe da Nunito externa nem da Bogart local licenciada; fallback pode alterar quebras de linha, largura de textos e altura dos cards. Não foram forçadas alturas para compensá-lo. Capturas de QA estão na pasta, sem usar screenshot do Figma como asset do HTML.

## Pendências já existentes do projeto

A fonte Bogart Extrabold permanece dependente de uma instalação local ou licença web. O lockup de Leitura no Manifesto e a fotografia do Hero/História ainda podem depender de URLs temporárias do Figma; são questões herdadas, não modificadas nesta etapa. Fotos locais da Galeria e todos os outros SVGs originais recebidos continuam no ZIP. Tablet e Mobile de Depoimentos ainda serão implementados após aprovação do Desktop.

---

# Histórico de versões anteriores

# v0.26 — Manifesto Mobile (Seção 04)

A partir do protótipo único v0.25, a Seção 04 **Manifesto** foi adicionada ao breakpoint **Mobile (até 614px)**, preservando Desktop, Tablet e as Seções 01–03. A referência é o frame Figma **`3655:7057`** do arquivo `OtFihfNvBMeg5ITRk3ry2t` (390 × 2575px).

## Especificação implementada

- Manifesto com fundo branco e padding vertical **48px**, ContentContainer `width:100%`, padding lateral **32px**, ManifestoContent com `gap:36px` e altura Hug.
- Título **Manifesto Leitura** com Nunito ExtraBold **24px** (medida real do nó de texto do Mobile `3655:7172`), largura de 217px, cap-height de 17px, intervalo vertical de 12px e sublinhado local de cinco cores com 4px. **Nota de especificação:** a annotation textual do título ainda menciona 28px, mas o nó no frame Mobile mede 24px; foi priorizado o valor real desenhado.
- **Sete statements em coluna**, com a frase **sempre acima da copy**, sem zigue-zague no Mobile. Cada statement usa largura Fill, altura Hug, gap interno de **24px** e **zero padding** (as margens laterais já pertencem ao ContentContainer). Blocos com colunas invertidas no DOM nas versões Desktop/Tablet usam `order` no Mobile para restaurar a ordem visual correta. Não foi duplicado o texto nem criado componente novo.
- Frase em **Bogart ExtraBold 28px**, 115% de line-height, letter-spacing -0.532px, azul `Brand/Primary`. Copy em **Nunito SemiBold 16px**, 130% de line-height, letter-spacing -0.304px, `Text/Secondary`, alinhamento central e separação de 16px entre parágrafos. Sem clamp/truncamento e sem alturas fixas.
- **Seis divisores** originais entre statements, cada um com duas linhas SVG, gap de 10px e ponto central SVG de 6px. Os mesmos arquivos locais existentes foram reutilizados, sem rasterização.
- Lockup final **200px de largura**, logo com aproximadamente 32.7px de altura e assinatura com **175px** de largura; gap de 16px. As referências dos dois vetores Figma são as mesmas da versão anterior (ver limitação abaixo).
- Navegação flutuante horizontal **única**, fixa na viewport e com a seção ativa **Manifesto 03**; não foram adicionadas outras instâncias do menu. A faixa global multicolorida fixa permanece única com **6px** de altura. Nenhuma interação extra foi acrescentada, pois o Manifesto não contém controles próprios.

## QA v0.26

Chromium headless: conferidos **320×650, 375×812, 390×844, 390×550, 430×932, 614×830**, além da transição Tablet **615, 768, 900, 1023px** e regressão Desktop **1024, 1440 e 1920px**. Passaram: ausência de overflow horizontal, 7 blocos e 6 divisores, divisor SVG local carregado, título 217×33px em Mobile, copy 16px, frase 28px, ordenação visual de todos os blocos, ausência de sobreposição de textos, logo 200px em Mobile, menu horizontal 180×40px ativo no Manifesto e preservação dos layouts em duas colunas nos demais breakpoints. Os scripts JavaScript existentes não emitiram exceções.

**Limitações para fidelidade visual completa:** no ambiente de teste, a família **Bogart Extrabold licenciada** não está instalada, e a fonte Nunito do Google Fonts não pode ser baixada; portanto, a captura de QA usa fallbacks e as quebras de linha e altura total **não correspondem 1:1** ao Figma. Com os arquivos/licenças corretos a composição é definida por Hug, não por altura fixa. O lockup ao final ainda depende dos **dois links temporários dos SVGs originais do Figma** herdados das versões anteriores: a rede deste ambiente bloqueia a exportação; não foram substituídos por PNG, texto nem outra marca. Para o handoff offline, exportar o logo e a assinatura originais para `assets/` e trocar as duas URLs no `index.html`.

---

# v0.25 — Manifesto Tablet (Figma 3655:6446)

Implementado somente o breakpoint Tablet do **Manifesto**, de 615 a 1023px, partindo da v0.24.

- Frame de referência de **768 × 2268px**; seção branca com padding vertical **48px**, largura Fill com margens internas de **32px** e conteúdo Hug com gap **36px**.
- Os **7 statements alternados** continuam com **duas colunas 50%**, padding **24px** em cada coluna, raio herdado de **32px** e alinhamento central; copy e headings nunca são truncados.
- Titulação editorial: **Bogart Extrabold 28px**, peso 800, line-height 115% e letter-spacing **−0,532px**; parágrafos: **Nunito SemiBold 16px**, line-height 130%, letter-spacing **−0,304px** e gap de 16px entre parágrafos.
- **6 separadores originais** continuam 100% da largura útil de 704px, com duas linhas SVG locais, ponto central de 6px e gap de 10px. Nenhum novo vetor foi desenhado.
- **Lockup original** ao final: 220px de largura, logo escalado para 220px, tagline 180px e gap 16px. As referências SVG ainda são remotas do Figma na v0.24 de origem: precisam ser localizadas/exportadas antes de handoff final.
- **Uma só navegação flutuante global** e uma faixa decorativa global fixa, herdadas do protótipo. Não duplicar instâncias dentro do Manifesto.
- **Mobile Manifesto não implementado** (frame Figma `3655:7057`); manter oculta somente esta seção em larguras <=614px até a etapa Mobile.

## QA realizado

- Chromium headless em **615, 768, 900 e 1023px**: duas colunas de mesma largura, padding de 24px, gap de 36px, headings em 28px, copy em 16px, divisores 100% de largura e lockup 220px; todas as caixas e parágrafos íntegros sem overflow ou truncamento.
- Teste do menu flutuante no Manifesto Tablet: seção **03 / Manifesto** ativa, navegação fixa e centralizada, sem variant dark da Galeria.
- Regressão em **1024 e 1440px**: Manifesto Desktop preserva 32px/18px, padding de 32px por coluna e lockup de 250px. Em **390px**, o Manifesto continua oculto até sua própria etapa Mobile. Seções anteriores (HTML idêntico) e todos os assets locais preservados bit a bit.
- Altura medida de **2401px no QA a 768px**, enquanto o Figma indica **2268px**. Essa diferença decorre das fontes ausentes e não deve ser ajustada com alturas fixas, truncamento ou substituição de tipografia.

## Limitações

- A fonte Bogart original **não está incluída**; o CSS já está preparado para a instalação local licenciada da v0.24. Se ausente, o fallback altera quebras de linha e altura total do manifesto, impedindo afirmar fidelidade tipográfica 1:1 no navegador de QA.
- Também permanecem as URLs temporárias do lockup original, herdadas da v0.24. Não foram substituídas por raster nem texto.

---

# v0.24 — Fonte Bogart Extrabold (Manifesto)

- Configurei `@font-face` para carregar **Bogart Extrabold**, a variante usada nos sete títulos do Manifesto no Figma, a partir de uma instalação local licenciada (`local(...)`). O CSS dos títulos agora usa `Leitura Bogart` antes da família `Bogart`, peso `800`, sem negrito sintetizado (`font-synthesis: none`).
- Não substituí a fonte por Georgia nem alterei peso, corpo, entrelinha, espaçamento, conteúdo ou composição da seção. As seções 01–03 e os breakpoints anteriores estão intactos.
- **Requisito externo:** o ambiente de edição não possui Bogart instalada e o ZIP de assets não contém webfont. Assim, **o visual exato só aparece onde a fonte está instalada**. Para visualização universal, insira no `<head>` um link CSS do seu **Adobe Fonts Web Project** autorizado contendo Bogart Extrabold, ou configure o kit webfont licenciado da Zetafonts. O arquivo da fonte não foi incorporado nem redistribuído ao pacote. Não considero a correspondência visual 1:1 verificada até que esse recurso esteja conectado.

---

# Leitura 60 Anos — Protótipo único v0.22 / Galeria Mobile

**Atualização responsiva aprovada em 6/11/2026:** a fotografia Mobile da Galeria usa **largura Fill Container e altura calculada por `aspect-ratio: 326 / 245`**. A proporção do frame Figma a 390px foi preservada, mas a altura NÃO fica fixada em 245px em outras larguras. Esta decisão mais recente prevalece sobre o `layoutSizingVertical=FIXED` existente no frame `3744:3194`; harmonizar a annotation antes do handoff final.

O HTML usa uma única `index.html` com CSS e JavaScript internos, e todos os SVGs e sete JPEGs locais na pasta `assets/`. Desktop e Tablet aprovados permanecem intactos; o Mobile tem **três coleções empilhadas sem abas**, cada uma com galeria, contador, paginação 100×32px, setas e legenda independentes. Os datasets demonstrativos continuam com **7, 6 e 5 fotos** nos respectivos assuntos. Os arquivos de imagem originais não foram recompactados nem renomeados nesta revisão.

## Comportamento Mobile

- Conteúdo com margem lateral de 32px, título principal Galeria, três assuntos separados por gap de 48px. Cada assunto tem heading de 20px, gap de 16px até o carrossel, controles centralizados 24px abaixo da foto e padding inferior de segurança de 120px na seção.
- Foto: largura `100%` do container (326px a 390px de viewport), altura `auto`, proporção `326 / 245`, `object-fit: cover`, raio de 24px. Dimensões verificadas: **256×192,4px** a 320px; **311×233,7px** a 375px; **326×245px** a 390px; **366×275,1px** a 430px; **550×413,3px** a 614px.
- Contador original GalleryImageCounter no canto superior direito a 12px. Legenda com gradiente original abre/fecha por toque curto quando houver conteúdo; toque fora fecha e swipe troca slide sem abrir legenda. Em Desktop, hover continua funcionando. Arrasto com mouse não seleciona imagem/texto.
- Cada assunto tem contador, setas, swipe e paginação **independentes**. A página não tem overflow horizontal; bolinha azul ocupa o primeiro slot no primeiro slide, o centro nos intermediários e o último no final. O menu horizontal e as listras inferiores permanecem **instâncias globais**, não duplicadas entre assuntos.

## QA e restrição de legenda em 320px

Chromium: QA da Galeria Mobile em **320, 375, 390 (alturas 844 e 550), 430 e 614px**; regressão em **615, 768, 1023, 1024 e 1440px**. Testados sem overflow horizontal; labels, controles e imagens carregados; contadores independentes (1/7, 1/6, 1/5); próxima/anterior; índice final (5/5 com terceiro indicador azul); toque abre/fecha legenda; swipe avança um slide sem abrir legenda. A tela 390px mantém a seção Galeria de 1362px como no Figma; demais alturas variam de acordo com a largura proporcional das fotos.

**Atenção para futuro QA de conteúdo:** em larguras estreitas como 320px, a legenda fictícia longa da amostra **ultrapassa a área visual da foto** com tipografia de 16px e padding original de 36px. Esta entrega mantém o contrato visual `GalleryImage` e NÃO altera estilos nem acrescenta scroll, botões ou truncamento arbitrário. Antes do handoff final, é preciso validar com o designer como a legenda deve se comportar com textos longos nessas larguras — ou estabelecer limite editorial apropriado.

**Assets:** todas as sete fotografias da Galeria são JPEGs locais do `Assets.zip`. Hero e Nossa História ainda referenciam imagens externas temporárias do Figma, fora do escopo desta revisão. Fonte Nunito é carregada por recurso externo.

---

## Histórico das versões anteriores

# Leitura 60 anos — Galeria v0.20 com fotografias reais para teste

A partir do **protótipo v0.19** aprovado, somente os **assets de conteúdo da Galeria e o dataset demonstrativo** foram atualizados. Nada mudou no CSS, na estrutura de componentes, na paginação, nos gestos, no Hero ou em Nossa História. Todas as sete fotografias vêm do `Assets.zip` enviado pelo usuário, preservadas **byte a byte** em `assets/gallery/` (JPEG original; sem recortes nem recompactação).

## Como as imagens foram distribuídas

O ZIP não traz categorias nem legendas editoriais. Para testar a paginação dinâmica com quantidades diferentes e imagens consecutivas visualmente distintas, as abas **Assunto 01/02/03 permanecem placeholders**:

- **Assunto 01 — 7 slides:** Maceió 7423, Maceió 7446, Loja Nova 28, Loja Nova 71, Loja Nova 75, REN 3480, REN 3503.
- **Assunto 02 — 6 slides:** Loja Nova 28, Loja Nova 71, Loja Nova 75, REN 3480, REN 3503, Maceió 7423.
- **Assunto 03 — 5 slides:** REN 3480, REN 3503, Maceió 7423, Maceió 7446, Loja Nova 28.

Esta distribuição **não atribui assuntos reais às fotografias**. Se houver uma ordem e associação editorial específica no Figma, basta substituir a matriz `galleryOrders` dentro do último script de `index.html`. A imagem ocupa o componente `GalleryImage` original (960×450px, raio 36px, crop `object-fit: cover`); seu arquivo original não foi modificado. A legenda demonstrativa e os estados `caption=yes/no` foram mantidos da v0.19; não foram criadas legendas descritivas nem conteúdo oficial.

## Correspondência dos nomes originais

- `maceio-7423.jpg` ← `Assets/LEITURA Maceió IMG_7423 foto Flávia Correia.jpg` (SHA-256 `419722fd5c2c…`)
- `maceio-7446.jpg` ← `Assets/LEITURA Maceió IMG_7446 foto Flávia Correia.jpg` (SHA-256 `2e5afcb9b5cb…`)
- `loja-nova-28.jpg` ← `Assets/loja nova-28.jpg` (SHA-256 `b2dfa9dbcdf6…`)
- `loja-nova-71.jpg` ← `Assets/loja nova-71.jpg` (SHA-256 `38a886616adf…`)
- `loja-nova-75.jpg` ← `Assets/loja nova-75.jpg` (SHA-256 `020032297dc9…`)
- `ren-3480.jpg` ← `Assets/REN_3480.jpg` (SHA-256 `0737161d5ec3…`)
- `ren-3503.jpg` ← `Assets/REN_3503.jpg` (SHA-256 `1a7c41201234…`)

## QA e pendências

**QA executado em Chromium** (1024px, 1440px e 1920px, regressões a 768px e 390px): os sete JPEGs locais carregaram com `naturalWidth` válido; cada slide exibiu uma origem distinta dentro de seu assunto; contadores e paginação passaram de 1/N a N/N nos três assuntos (7/6/5 imagens), com reset ao mudar de aba e sem rolagem horizontal. O arrasto com mouse mudou da segunda para a terceira fotografia sem seleção nativa de texto. As regras de legenda, toque e teclado são as mesmas da v0.19, não modificadas nesta versão. Na Galeria, a dependência antiga de foto externa do Figma **foi eliminada**: todos os sete JPEGs agora são locais. **As fotos do Hero e de Nossa História continuam dependendo do asset Figma temporário**, por não fazerem parte deste ajuste. Nunito ainda depende de carregamento de fonte externa. Na implementação final, os assuntos e legendas devem ser mapeados ao conteúdo editorial definitivo.

---

## Documentação anterior — base v0.19

# Leitura 60 Anos — Protótipo único v0.18

## Revisão v0.18 — Contiguidade das seções e paginação nas extremidades

- **Gap entre seções 02 e 03:** havia os caracteres literais `\n` após `</section>` da Nossa História, fora de qualquer tag ou comentário. O navegador criava um line box de ~18px sobre o fundo branco entre as duas seções. Esse texto espúrio foi removido. Não foram modificados os paddings, as alturas ou o background de nenhuma seção.
- **Paginações extremas:** na **primeira E na última foto** de cada assunto, a bolinha azul de 12px ocupa o primeiro slot (x=26); em fotos intermediárias, ocupa o slot central (x=50). As outras duas bolinhas permanecem cinza de 8px. Mantidas a dimensão 100×32px, as posições 26/50/74, as transições de 240ms, a animação dinâmica intermediária e a janela de três marcadores, sem adicionar novos indicadores.
- **Estados:** setas, swipe, drag, teclado e troca de assunto atualizam simultaneamente índice, contador, estado das setas e paginação. Ao trocar assunto, retorna para a primeira posição azul; respeita `prefers-reduced-motion` e não ultrapassa os limites do dataset.
- **Figma:** trata-se de uma correção de comportamento explicitamente solicitada para a GalleryPagination original. O componente gráfico, os assets e as demais seções não foram modificados. A Galeria segue Desktop apenas nesta etapa.

---

**Etapa atual:** Galeria Desktop (Seção 03), revisão de paginação e gestos. Continuidade do mesmo `index.html` da v0.15. As Seções 01 e 02 preservam os breakpoints Desktop, Tablet e Mobile aprovados. A Galeria tem apenas Desktop nesta entrega; Tablet e Mobile serão implementados após validação.

## Revisão v0.16 — Paginação dinâmica e legenda/drag

Referência comportamental: https://swiperjs.com/demos/040-pagination-dynamic/core . Mantivemos **a aparência 1:1 do GalleryPagination do Figma** (100×32px, fundo #D9D9D9 e 3 dots de 8/12/8px nas posições 26/50/74; azul ativo #0033A0, cinza inativo #999999). A geometria do SVG original foi reutilizada no HTML para possibilitar a animação dos círculos, e o arquivo `assets/gallery-pagination-original.svg` foi preservado integralmente para o handoff. A janela representa **anterior / atual / próximo** e desloca seus indicadores em 24px ao avançar/retroceder, usando transição de 240ms e respeitando `prefers-reduced-motion`; na v0.16 o indicador ativo permanecia no centro inclusive nas extremidades (corrigido na v0.18). O estado real é indexado em `data-index`, o total em `data-total` e o contador acessível mostra imagem atual/total. Não há uma bolinha por slide, e não se navega além dos limites.

O conjunto de slides é **demonstrativo** para o QA: `Assunto 01` tem 7 imagens, `Assunto 02` tem 6, `Assunto 03` tem 5, todas reutilizando **a única fotografia e a legenda de placeholder já previstas no Figma**. Não foram criadas fotos, textos ou categorias oficiais. A mudança de aba sempre reinicia em 1/N, atualiza setas/contador/dots e fecha a legenda.

**Legenda e gestos:** no Desktop, hover ou foco de teclado continuam revelando o overlay do `GalleryImage` com gradiente e texto já aprovados. Ao mover horizontalmente ≥8px com o botão pressionado, o gesto assume prioridade e oculta a legenda; ao deslocar ≥45px, a soltura navega exatamente um slide. O overlay usa `pointer-events:none`, mantendo o drag no próprio container da imagem. Depois de trocar de slide, a legenda permanece fechada até o próximo movimento de mouse ou novo foco. No toque, um toque curto abre/fecha legenda quando o slide tem texto; swipe horizontal navega uma imagem e **nunca** ativa a legenda do mesmo gesto. Um toque fora fecha a legenda. Escape fecha; setas de teclado sobre a imagem também navegam. Rolagem vertical natural é preservada via `touch-action:pan-y`. O DOM não adiciona controles visuais.

**Escopo:** Galeria segue apenas no breakpoint Desktop (`>=1024px`) nesta entrega; a lógica de toque foi testada em emulação touch na largura Desktop como preparação para Tablet/Mobile, **sem acrescentar layout de Galeria nesses breakpoints**. Hero e Nossa História mantidos sem modificações.

### QA v0.16

Chromium testado a 1920×900, 1440×900, 1024×768, mais regressões 1023×800, 768×892 e 390×844. Foram conferidas a altura original de 786px, o pager de 100×32px, ausência de overflow horizontal, 3 dots em repouso / 4 durante a transição, contadores 1/7→7/7, limites das setas, três abas com datasets de 7/6/5 e reset do índice, hover/drag/foco no Desktop, gesto curto sem mudar slides, touch tap alternando legenda e swipe navegando uma imagem sem exibir legenda. Também foram testados toque rápido após swipe e `prefers-reduced-motion`. A fonte e a foto via URLs externas não carregam no navegador de QA; o enquadramento fotográfico real permanece pendente até obter o asset original local.

---

## Fonte de verdade no Figma

Arquivo `OtFihfNvBMeg5ITRk3ry2t`. Galeria Default `3639:151`, Hover com legenda `3639:243`. Componentes aprovados: `GalleryImage` (`3730:2184`), `CarouselButton` (`2001:3531`), `GalleryPagination` (`3731:2186`), `GalleryImageCounter` (`3810:2309`) e `GallerySubjectTabs` (`3804:3413`). O menu flutuante e a faixa de cinco listras são globais: **uma única instância de cada**, sem duplicação em outras seções. O menu assume o rail `Light Blue/500` (`#3BA5F2`) na Galeria.

## Desktop — geometria e comportamentos (base v0.15)

Fundo `Brand/Primary #0033A0`, padding vertical 64px e altura 786px no frame 1920px. Container max-width 1368px com padding lateral 32px. Título Nunito ExtraBold 28px e sublinhado original multicolorido com altura de 4px. Abas “Assunto 01–03” de 144×44px, gap 16px; painel central de foto 960×450px com raio 36px; contador no canto superior direito a 20px das bordas, com altura 32px. Controles: gap vertical 24px; grupo de 212×32px, com setas CarouselButton de 36×32px, GalleryPagination de 100×32px e 20px de espaço entre elementos. Os quatro SVGs das setas (previous/next default/hover) e o SVG da paginação foram exportados da geometria vetorial original do componente Figma e estão em `assets/`, sem dependência de biblioteca de ícones.

O `GalleryImage` exibe gradiente preto 10%→80% e legenda original em Nunito Bold Italic 16px quando existe legenda e a imagem recebe hover ou foco de teclado; não exibe nada disso quando a imagem não possui legenda. A transição dura 220ms (sem animação em prefers-reduced-motion). Ao trocar slide, a legenda fecha; ao trocar aba, o índice é redefinido para o primeiro slide. `GalleryPagination` mantém três bolinhas originais (8/12/8) como janela compacta do estado; não se adicionam bolinhas por quantidade de imagens. O contador mostra o número real de slides, sem zeros à esquerda. O protótipo também responde a arrasto/swipe horizontal sobre a foto, avançando um slide por gesto, sem criar novos controles.

## Conteúdo demonstrativo — base v0.15 (substituído pelos dados de teste v0.16 acima)

“Assunto 01”, “Assunto 02” e “Assunto 03” são **placeholders aprovados no Figma**, não categorias oficiais. Para testar seleção independente, contadores e legendas, cada assunto oferece três slides demonstrativos com a **mesma imagem de referência do Figma** e, quando aplicável, **a mesma legenda de exemplo**. Nenhuma fotografia, legenda ou categoria nova foi inventada. O contador do protótipo mostra `1/3` em vez de `1/20`, porque `20` é um exemplo no Figma e a quantidade do conteúdo real ainda não foi definida.

A Galeria usa o mesmo IMAGE fill do Hero (hash Figma idêntico: `7fc95402c01635bbd14da48a8b028877ef830152`), aqui com link temporário atualizado `https://www.figma.com/api/mcp/asset/ee3c89ff-348d-467b-bc8b-981e4057f20a/880f8.png`. **Limitação:** a fotografia original não está empacotada localmente no ZIP porque o ambiente não acessa o host do Figma; também a fonte Nunito depende de Google Fonts. É preciso exportar os assets originais antes do handoff definitivo offline. Nenhuma fotografia foi substituída por screenshot/arte fictícia, e os assets antigos não foram modificados.

## QA da v0.15

Chromium: testes de geometria e overflow em 1920×900, 1440×900, 1024×768, com seção de 786px, imagem 960×450px, abas 464×44px e controles 212×32px. Em 1023px, 768px e 390px, Galeria permanece oculta até implementação dos breakpoints Tablet/Mobile. Validados: troca de aba e reset, teclado, setas e limites, atualização do contador, gradiente apenas para caption=yes, drag de uma imagem e mudança da variante escura do menu global. Todas as referências SVG locais existem e o JS passou em `node --check`. A imagem externa e Google Fonts não puderam ser inspecionados visualmente na automação local. A validação fotográfica 1:1 permanece pendente até carregar os assets reais.

---

## Histórico de revisões anteriores

# Leitura 60 anos — v0.12 (ajustes Mobile)

- **Hero:** altura automática com `min-height:0`, terminando imediatamente na fotografia, sem vazio criado por `100dvh`.
- **Timeline:** configuração `cardsPerView=1` explícita: uma carta cheia na área visível, largura `100vw - 64px`, outros cards ocultos fora da viewport; arrasto livre sem snap e setas com snap por marco.
- **Escopo:** Desktop, Tablet, HeroSectionNavigation, SVGs, menu flutuante e outras medidas mantidos.
- **Recursos externos:** a fotografia e Nunito continuam dependendo de URLs externas, como na v0.11; não foram substituídos.

---

# Leitura 60 Anos — Protótipo único v0.11

## Escopo

O mesmo `index.html` contém **Seção 01 (Hero) e Seção 02 (Nossa História / Linha do Tempo)** com CSS e JavaScript internos, sem framework. A versão 0.11 acrescenta **apenas o breakpoint Mobile da Seção 02**. Foram mantidos os arquivos SVG originais já existentes na pasta `assets/` e as regras aprovadas de Desktop e Tablet.

**Fonte de verdade — Figma:** arquivo `OtFihfNvBMeg5ITRk3ry2t`, frame de Nossa História Mobile fechado `3799:3413`, aberto `3931:7150`, narrativa `3922:7104`, componente de navegação `FloatingSectionNavigation` (`3614:1700`). Versões anteriores: Hero Desktop `3559:1712`, Tablet `3575:2061`, Mobile `3559:1758`; História Desktop `3788:3413`, Tablet `3798:3413`.

## Mobile — Nossa História (até 614px)

- Fundo `surface/subtle`, padding vertical `48px`, margem lateral `32px` e distância de `32px` entre título, painel narrativo e timeline.
- Título **Nossa história** em Nunito ExtraBold `24px` e faixa decorativa local de cinco cores e altura `4px`.
- Painel narrativo **326 × 560px** na referência de `390px`: largura fluida `(100vw - 64px)`, raio de `32px`, borda de `1px`. O scroll é **interno**, com a scrollbar recuada para não ultrapassar os cantos. Todo o conteúdo editorial que já existe nas outras versões permanece acessível, sem truncamento.
- Conteúdo do painel: padding lateral de `24px` em relação à borda de referência, título Nunito Black `32px`; corpo inicial `16px/125%`, fotografia original com proporção `560/320`, legenda de `16px`, subtítulo final `21px`, com alturas Hug.
- Timeline com eixo azul de `2px`, **um marco visível por vez**, ano/nó/conector alinhados ao centro do viewport, nós em SVG preservados. Card de `326px` (fluido) com padding `20px`, imagem `284×208px` na referência, raio de imagem de `32px`, texto de `16px/135%`, altura por conteúdo.
- **Arrasto livre** de cards, sem `scroll-snap`. **Apenas as setas** alinham automaticamente ao marco anterior/seguinte; o rótulo do ano acompanha o card mais próximo durante o arrasto. As datas adicionais além de 1983 e 1986 continuam **placeholders de teste**, não fatos históricos.
- Menu flutuante **global** (uma única instância no HTML) escondido no Hero, visível a partir da História. Mobile: `180×40px` recolhido, fixo ao centro horizontal `32px` acima da base; `250×191px` expandido. O rail recolhido mantém fundo azul a `50%`, `backdrop-filter: blur(5px)` e sombra `0 0 4px rgb(0 0 0 / 10%)`. Ao expandir: painel branco `250×135px`, gap `16px` e rail `180×40px`, ambos com sombra `0 0 10px rgb(0 0 0 / 35%)` (Figma atualizado). Os cinco traços são os SVGs originais. Em toque, a barra pode ser aberta antes de navegar; teclado/Escape também funcionam.
- A faixa decorativa global inferior é única e fixa à viewport, com `6px` no Mobile, não duplicada dentro da Seção 02.

**Não foi adicionado um seletor novo de décadas:** embora algumas annotations citem um dropdown, o frame Mobile atual mostra somente a timeline e o menu flutuante. Não inventar UI que não esteja desenhada. Quando houver conteúdo real de outras décadas, conectar os dados à navegação conforme as annotations, em vez de criar fatos fictícios.

## Desktop / Tablet preservados

A v0.11 acrescenta regras apenas no bloco `@media (max-width: 614px)` para a Seção 02 e uma camada de marcador mobile que permanece oculta nas outras larguras. A Seção 01 aprovada e a Seção 02 em Desktop/Tablet mantêm seus CSS e estruturas anteriores. A lógica de navegação global passa a considerar Mobile (onde a Seção 02 agora existe), sem duplicar o menu.

## Como testar

Abra `index.html` num navegador. Use **390×844px** como referência Mobile e teste 320px, 375px, 430px e 614px; confira também a transição para Tablet em 615px. Role além do Hero, leia o painel até o fim usando o scroll interno, arraste a timeline e clique nas setas. O menu flutuante deve surgir a partir de Nossa História e abrir no hover/foco ou toque.

**QA executado:** Chromium headless com 320, 375, 390 (incluindo viewport de altura 550), 430, 614, 615, 768, 900, 1023, 1024 e 1440px. Conferidos: ausência de overflow horizontal, painel de 560px, scroll completo, recuo da barra, eixo/card centralizados, snap de `350px` na seta de 390px, arrasto sem snap em posição intermediária, menu 180×40 → 250×191 com sombras de `35%`, e regressão de medidas Desktop/Tablet. Também passou a validação sintática do JavaScript. A comparação de tipografia e fotografias não é completa no navegador de teste, que bloqueia recursos externos.

## Pendência de asset original

A fotografia da loja **ainda está apontada para uma URL temporária antiga do Figma**, herdada do protótipo de origem; o ambiente atual não consegue resolver o host para baixá-la (`curl: Could not resolve host`). Não foi feita substituição por outra fotografia nem por um screenshot. Para handoff final offline, exportar a foto original em arquivo local e trocar as referências no `index.html`. Os SVGs existentes, incluindo logo, nós, setas e riscos, estão preservados localmente no pacote e não foram rasterizados. A fonte Nunito é referenciada via Google Fonts e requer carregamento externo, mas **arquivos de fonte não estão incluídos**.


## v0.13 — Correção da altura da Seção 01 no Tablet

- Em `615px–1023px`, a Seção 01 passa a ter `height: auto; min-height: 0;` em vez de `min-height: 100vh/100dvh - header - listras`. Assim a base do Hero coincide com a base real da fotografia, mesmo em viewports altos.
- Mantidos os gaps, paddings, proporção 768/560 e bordas de 32px originais do Tablet. A seção Nossa História começa imediatamente após a foto, sem espaço em branco gerado pelo Hero.
- A mudança é limitada ao CSS do Hero Tablet; todos os outros componentes e breakpoints foram preservados, incluindo o Mobile corrigido na v0.12.


## v0.14 — Correção da narrativa Mobile e fundo das setas (06/11/2026)

- Removido **apenas** o override de `18px` em `.history__figure + .history__prose` no Mobile. Todos os parágrafos do painel narrativo Mobile usam `16px` (Nunito SemiBold, line-height `125%`, letter-spacing `-0.304px`), conforme Figma `3799:3413` / texto `3922:7111`. A tipografia original de `18px` do Desktop e Tablet **permanece** conforme seus respectivos frames.
- Adicionado o token CSS `--surface-brand-soft: #f5fbfe` correspondente à variável Figma **Surface/Brand Soft** (`VariableID:2086:1347`) e aplicado como `background` em `.history__timeline-arrow`, em **Desktop, Tablet e Mobile**. As caixas de previous/next continuam com `24 × 24px`, sem mudança em padding, raio, posição, SVG nem interações (drag livre; snap apenas nas setas).
- Nenhuma outra seção, breakpoint ou componente foi alterado.


## v0.17 — Evitar seleção de conteúdo durante o arrasto da Galeria

Alteração exclusivamente na interação `.gallery__media` da seção Galeria. O contêiner da imagem recebeu `user-select: none`, `-webkit-user-select: none` e `-webkit-touch-callout: none` para impedir seleção nativa da imagem, legenda e contador. O início do gesto com o **mouse** cancela o comportamento padrão (`pointerdown.preventDefault()`), mas eventos touch não são cancelados, preservando scroll vertical e swipe. O elemento `img` já mantinha `draggable="false"` e `-webkit-user-drag: none`, preservados. Não há mudança de aparência, tamanhos, assets, paginação, hover, foco ou comportamento dos componentes existentes.

**QA:** Chromium 1920×1080, 1440×900 e 1024×820: arrasto de mouse avança slides sem texto selecionado, sem overflow; setas e teclado continuam funcionando. Em sessão touch, toque curto exibe legenda, swipe horizontal avança imagem e fecha legenda. Fotografia externa Figma continua sujeita à limitação registrada anteriormente.


## Revisão v0.19 — Última bolinha da paginação

Corrigida apenas a lógica de posição do indicador ativo do `GalleryPagination`: no primeiro slide a bolinha azul maior fica no indicador da esquerda (`x=26`), nos slides intermediários fica no centro (`x=50`) e **no último slide fica no indicador da direita (`x=74`)**. Os três indicadores continuam no componente original de 100×32px, com raios 6/4/4 conforme o ativo, mantendo transições, arrasto, setas e alternância de assuntos da v0.18. Não foram alterados os frames Desktop/Tablet/Mobile nem o conteúdo de outras seções.
