# Especificacoes Tecnicas — Fragmentos do Amanha

**Documento:** referencia tecnica consolidada para continuidade do projeto  
**Atualizado em:** 2026-11-10  
**Repositorio:** https://github.com/Gravit-Studios/fragmentos-do-amanha  
**Projeto Unity:** `unity/FragmentosDoAmanha`

> Este documento consolida as decisoes de design e o estado tecnico registrado no repositorio. Para o estado operacional mais recente, prevalecem `AGENTS.md`, `production/handoff-current-state.md` e `production/roadmap.md`. Quando houver divergencia entre este resumo e esses arquivos, atualizar este documento a partir das fontes versionadas.

---

## 1. Visao geral

- **Nome de trabalho:** Fragmentos do Amanha / Era Zero.
- **Genero:** metroidvania 2D de acao e plataforma.
- **Engine:** Unity 6.
- **Estilo in-game:** pixel art autentico, baixa resolucao efetiva, pixels nitidos, dithering e paletas limitadas.
- **Arte de apresentacao:** ilustracao/concept art detalhada, separada dos assets finais do jogo.
- **Modelo de producao:** desenvolvimento independente com pipeline assistido por IA e validacao criativa/manual.
- **Prioridade de escopo vigente:** concluir e polir a demo Era Zero + Egito antes de expandir para outras epocas. Nao iniciar Grecia ou outras epocas sem decisao explicita do usuario.

### Pitch

Um cientista viaja pelo tempo para desfazer as alteracoes historicas feitas por seu ex-parceiro, Voss, que reescreveu a historia para governar diferentes epocas. Em cada periodo, uma integrante da linhagem de Naiara resiste a tirania.

## 2. Pilares de design

1. Viagem no tempo como estrutura de mundo: cada epoca possui identidade visual, arquitetura, inimigos, armas, paleta e presenca ambiental de Voss.
2. Exploracao metroidvania: areas interconectadas, retornos e caminhos liberados por habilidades.
3. Combate responsivo: leitura clara de ataques, telegraph e feedback consistente.
4. Narrativa ambiental: propaganda, arquitetura, estatuas, objetos e simbolos comunicam a influencia de Voss.
5. Escopo sustentavel: assets modulares, documentacao versionada e IA como apoio, sem substituir aprovacao manual.

## 3. Narrativa e personagens

### Theo — protagonista

Cientista inicialmente nao combatente, forcado a fugir e investigar as alteracoes temporais. Elementos recorrentes: oculos de protecao na testa, dispositivo temporal em cobre/laranja e visual funcional assimetrico. A Anomalia temporal adapta roupas, ferramentas e armas ao periodo visitado.

### Voss — antagonista

Ex-parceiro de Theo e tirano atraves das epocas. Sua presenca deve existir fisicamente em momentos-chave e ambientalmente por meio de estatuas, retratos, propaganda, arquitetura e simbolos. Linguagem visual: verticalidade, simetria, imponencia, preto/dourado e tecnologia crescente conforme a epoca.

### Naiara — linhagem de resistencia

Cada epoca possui uma integrante diferente da linhagem. As personagens resistem a Voss e compartilham uma marca/objeto herdado (Ivory Mark) na mesma posicao. Naiara nao e personagem jogavel; aparece em momentos narrativos-chave e atua por conta propria.

## 4. Estrutura de epocas

O conceito geral possui Era Zero introdutoria e sete epocas jogaveis:

1. Era Zero — laboratorio futurista.
2. Egito Antigo.
3. Grecia Antiga.
4. Medieval.
5. Piratas.
6. Segunda Guerra Mundial.
7. Inicio da Internet.
8. Futuro proximo / era tecnologica final.

Cada epoca deve possuir identidade arquitetonica e cromatica propria, armas e inimigos locais, uma versao de Naiara, presenca ambiental de Voss e um fragmento relacionado a maquina do tempo.

**Escopo implementado/prioritario:** somente Era Zero + Egito. As demais epocas permanecem fora da producao ativa ate a demo estar completa e polida.

## 5. Modelo de jogo

- Exploracao nao linear dentro de cada epoca, com estrutura lock-and-key.
- Progressao entre epocas mais linear, condicionada aos fragmentos da maquina do tempo.
- Evolucao dupla: habilidades que liberam caminhos e customizacao opcional.
- Equipamentos e figurino mudam de acordo com a epoca por efeito da Anomalia.
- Theo e predominantemente silencioso; a narrativa e transmitida pelo ambiente, animacao, trilha e aparicoes pontuais de Naiara.
- A introducao no laboratorio deve ser jogavel, ensinando controles durante a sequencia de fuga.
- Cada epoca futura deve introduzir ao menos uma mecanica propria, alem da mudanca visual.

## 6. Stack e configuracao Unity

### Versao e pacotes registrados

- **Unity:** `6000.5.3f1`.
- **Renderizacao:** Universal Render Pipeline 2D, pacote URP `17.5.0`.
- **Input:** Input System `1.19.0`.
- **Camera:** Cinemachine `3.1.7`, namespace `Unity.Cinemachine`.
- **Pixel art camera:** 2D Pixel Perfect `6.0.0`, namespace `UnityEngine.U2D.PixelPerfectCamera`.
- **Unity MCP:** pacote comunitario `com.coplaydev.unity-mcp` registrado no projeto; bridge local descrita no handoff. Requer Unity Editor aberto e servidor iniciado na maquina local.

A versao efetiva deve ser conferida em `ProjectSettings/ProjectVersion.txt` antes de alterar a configuracao. Se mudar, registrar em `production/current-status.md`.

### Localizacao do projeto

Abrir no Unity Hub a pasta:

```text
unity/FragmentosDoAmanha
```

Nao abrir a raiz do repositorio como projeto Unity.

## 7. Cenas Unity

Cenas registradas como ativas:

- `Assets/Scenes/Prototype_Theo_Controller.unity` — sandbox para testes do controlador.
- `Assets/Scenes/VS_EraZero_Lab.unity` — sala introdutoria oficial da Era Zero.
- `Assets/Scenes/VS_Egypt_Blockout.unity` — area inicial do Egito.

A fatia oficial conecta Era Zero ao Egito por portal temporal apos a conclusao do objetivo. A build standalone interna foi registrada como testada de ponta a ponta em Windows.

## 8. Controles e gameplay implementado

Controles documentados:

| Acao | Entrada |
|---|---|
| Mover para esquerda | `A` / seta esquerda |
| Mover para direita | `D` / seta direita |
| Pular | `Space` / `W` / seta para cima |
| Ataque basico | `J` / clique esquerdo |
| Dash | `Shift` |

Sistemas implementados na fatia inicial:

- Movimento horizontal, pulo, gravidade e deteccao de chao.
- Tolerancia de pulo em bordas (coyote time) e protecoes contra travamento em quinas.
- Plataformas atravessaveis por baixo e colisao pelo topo.
- Dash com invulnerabilidade curta e cooldown.
- Vida, dano, invulnerabilidade e respawn; queda aplica dano antes do respawn.
- Ataque basico com hitbox e animacao.
- Inimigo com patrulha, telegraph, ataque, cooldown, dano e estado de morte.
- Fragmento temporal coletavel e inventario/contador.
- HUD temporario de vida, fragmento e objetivo.
- Objetivo de sala e portal temporal Era Zero -> Egito.

O kit de Theo para a demo esta limitado a ataque basico e dash, sem antecipar habilidades de epocas futuras.

## 9. Scripts e responsabilidades

Caminho base: `unity/FragmentosDoAmanha/Assets/Scripts/`.

| Script | Responsabilidade registrada |
|---|---|
| `Player/TheoController.cs` | Movimento, pulo, dash, flip do sprite e parametros de Animator (`Speed`, `Grounded`, `VerticalSpeed`). |
| `Player/PlayerHealth.cs` | Vida, dano, invulnerabilidade e respawn. |
| `Player/FragmentInventory.cs` | Inventario/contagem de fragmentos. |
| `Combat/PlayerAttack.cs` | Ataque basico e acionamento da animacao; usa `HashSet<IDamageable>` para evitar dano duplicado por multiplos colliders do mesmo alvo. |
| `Combat/IDamageable.cs` | Contrato de alvos que recebem dano. |
| `Enemies/PrototypeEnemy.cs` | IA simples, patrulha, telegraph, ataque, cooldown e morte. |
| `Systems/TemporalFragment.cs` | Coleta de fragmento temporal. |
| `Systems/PrototypeObjectiveState.cs` | Estado do objetivo da sala. |
| `Camera/CameraFollow2D.cs` | Implementacao anterior de camera de acompanhamento; verificar uso nas cenas atuais. |
| `UI/PrototypeHealthHud.cs` | HUD de vida. |
| `UI/PrototypeFragmentHud.cs` | HUD de fragmentos. |
| `UI/PrototypeObjectiveHud.cs` | HUD do objetivo. |

Ferramentas de editor em `Assets/Editor/` incluem `TheoSpriteSetup.cs`, `TheoAnimationSetup.cs`, `TilesetImportSetup.cs` e `CameraUpgradeSetup.cs`. Os menus de editor devem ser usados para importar/configurar sprites, construir Animator Controllers, fatiar tilesets e atualizar cameras nas cenas.

## 10. Camera e resolucao

- Cinemachine substitui o acompanhamento temporario de camera.
- Pixel Perfect Camera esta integrada.
- Referencia de resolucao usada na build: `960x540`.
- `assetsPPU` foi ajustado para `54` na configuracao de referencia da build para preservar o enquadramento com `orthographicSize 5`.
- Os assets historicos foram produzidos com densidades diferentes (tiles Era Zero ~627 PPU, Egito ~512 PPU, Theo ~795 PPU); portanto, nao assumir que todos compartilham PPU uniforme.
- O handoff registra como pendencia conferir/configurar `CinemachineConfiner2D` manualmente por cena, pois os bounds nao foram migrados automaticamente.

Validar enquadramento, pixel snapping e limites em cada cena apos qualquer alteracao de camera ou escala de assets.

## 11. Direcao de arte e especificacoes de pixel art

### Regras gerais

- Pixel art autentico, com baixa resolucao efetiva; nao usar ilustracao suavizada com filtro de pixelizacao.
- Pixels quadrados e bordas duras; sem anti-aliasing ou blending suave.
- Sombreamento por dithering, nao por gradientes suaves.
- Paleta limitada, contavel e coerente por personagem/ambiente.
- Iluminacao atmosferica com uma fonte de luz principal como ancora visual.
- Identidade cromatica tecnologica em cobre/laranja, reservada a elementos temporais.
- Cada epoca deve ter paleta e arquitetura proprias.

### Escala e tiles

- Tile base de referencia: `32x32`.
- Personagem jogavel de referencia: aproximadamente `64x96` (2x3 tiles).
- Props pequenos nao devem competir com a silhueta do personagem.
- Tilesets em grade, tiles adjacentes, fundo transparente e bordas tileaveis.
- Categorias: ground, platform, walls, borders e props.
- Separar tiles funcionais de props ornamentais sempre que possivel.
- Elementos decorativos podem ter versoes limpas e detalhadas.

### Prompting de arte

Os prompts-base reutilizaveis definidos no projeto sao:

- **Tileset Sheet:** folha organizada em grade de tiles 32x32, adjacentes, tileaveis e com fundo transparente.
- **Single Tile:** um unico tile 32x32, isolado, ocupando a area, sem cena ou variacoes extras.
- **Character Sprite / Run Cycle:** personagem com escala, silhueta, orientacao e linha de chao consistentes.

Os prompts completos e regras de validacao ficam em `docs/03_VisualDevelopment/sprite-prompt-guide.md`, `docs/03_VisualDevelopment/pixel-art-bible.md` e nas bibliotecas em `docs/03_VisualDevelopment/prompts/`. Ao solicitar os atalhos `Tileset Sheet prompt base` ou `Single Tile prompt base`, aplicar as especificacoes reutilizaveis correspondentes e acrescentar somente os detalhes do asset solicitado.

### Theo — padrao de sprite v04

- Um arquivo por frame/pose.
- Canvas fixo `1024x1024`.
- Transparencia alpha real; nunca xadrez desenhado no arquivo.
- Linha dos pes em `y=987` para poses no solo (Idle, Run, Attack).
- Poses no ar mantem a altura real do movimento; nao alinhar artificialmente o pe em y=987.
- Nome: `theo-sprite-<pose>-NN.png`.
- Visual v04 desenhado manualmente no Photoshop, usando o template `docs/03_VisualDevelopment/theo-sprite-canvas-template-1024.png`.

Estado de animacoes descrito no handoff:
- Idle: 6 frames, integrado e validado.
- Run: 8 frames integrados; o handoff registra problema de alternancia de perna (poses lideram com a mesma perna). Nao considerar o ciclo visualmente finalizado ate validar a alternancia correta em Play Mode.
- Jump: 6 frames, clip nao-looping integrado; cobre o arco completo e foi confirmado pelo usuario em Play Mode.
- Attack: 3 frames, clip nao-looping integrado e acionado pelo `PlayerAttack.cs`.
- Crouch: 4 frames recebidos, sem mecanica de agachar e sem integracao de gameplay.
- Land, Fall e HitDeath: pendentes; HitDeath exige arte especifica fora da ficha atual.

**Nota de consistencia:** `unity/FragmentosDoAmanha/Assets/Art/Characters/Theo/README.md` e o handoff podem divergir sobre o status de Run e testes. O handoff registra o defeito de alternancia como bloqueador visual; confirmar os arquivos e o comportamento real no Editor antes de alterar o status para concluido.

## 12. Assets, pastas e versionamento

### Regra de destino

Assets necessarios para o jogo funcionar devem ficar diretamente dentro do projeto Unity:

- `unity/FragmentosDoAmanha/Assets/Art/Characters/`
- `unity/FragmentosDoAmanha/Assets/Art/Tilesets/`
- demais categorias sob `unity/FragmentosDoAmanha/Assets/Art/`

Materiais que nao entram no jogo (concept art, ilustracoes, branding, PDFs, reference sheets e crops) ficam em `artbook/`.

Documentacao viva e tecnica fica em `docs/`; planejamento e estado de producao ficam em `production/`; documentos historicos/de design vindos do ChatGPT ficam em `ChatGPT/`.

### Regras Git/Unity

- Preservar todos os arquivos `.meta` da Unity.
- Nao versionar `Library/`, `Temp/`, `Logs/`, `UserSettings/`, crash logs ou caches locais.
- Nao criar manualmente arquivos de cena/prefab serializados quando a Unity/editor deve produzi-los.
- Scripts C# podem ser editados fora da Unity.
- Preferir menus/scripts de editor para criar ou modificar cenas, prefabs, Animator Controllers e importacoes.
- Conferir `git diff` em arquivos `.unity` apos testes que alterem estado em Play Mode, evitando salvar posicao/estado transitorio do Rigidbody.
- Assets binarios pesados devem seguir a configuracao Git LFS do repositorio; confirmar Git LFS ativo na maquina de producao antes de novos lotes grandes.

## 13. Pipeline de producao e validacao

1. Consultar `AGENTS.md`, `production/handoff-current-state.md` e `production/roadmap.md`.
2. Definir se o asset e material de jogo ou referencia de artbook.
3. Criar/editar o asset conforme os guias e prompts oficiais.
4. Salvar assets de jogo diretamente em `unity/FragmentosDoAmanha/Assets/Art/`.
5. Importar/configurar pela Unity e atualizar scripts de editor quando necessario.
6. Testar no Play Mode e, para a demo, validar build standalone.
7. Atualizar indice de assets, status, handoff e roadmap conforme o impacto.
8. Fazer commit e enviar para GitHub.

A IA e ferramenta de apoio; a aprovacao visual e tecnica final e manual.

## 14. Estado da demo e pendencias conhecidas

### Concluido conforme o roadmap/handoff versionados

- Fatia Era Zero + Egito jogavel de ponta a ponta.
- Controle, pulo, dash e ataque basico.
- Inimigo com telegraph, dano e morte.
- Vida, respawn, fragmento, HUD e objetivo.
- Portal temporal Era Zero -> Egito.
- Cinemachine e Pixel Perfect Camera.
- Tilesets iniciais das duas areas importados e testados no Tilemap.
- Build interna standalone Windows testada.

### Pendencias prioritarias registradas

1. Corrigir e validar alternancia de pernas no ciclo de corrida do Theo.
2. Reimportar/reconstruir/aplicar Animator nas cenas apos a correcao do ciclo.
3. Produzir/integrar as poses pendentes de Land, Fall e HitDeath.
4. Produzir props e arte final de Voss na Era Zero e no Egito.
5. Produzir/integrar FX de tecnologia temporal.
6. Revisar limites de camera por cena (`CinemachineConfiner2D`) e consistencia de PPU.
7. Revisar sensacao de controle, pipeline de arte e custo de animacao antes de decidir o escopo da proxima epoca.

Nao marcar itens como concluidos sem evidencia no repositorio e validacao correspondente. Play Mode e build devem ser testados em uma maquina com Unity Editor; ambientes web/nuvem sem acesso ao Editor devem registrar essas validacoes como pendentes.

## 15. Documentos de referencia

- `AGENTS.md` — regras de trabalho e organizacao.
- `production/handoff-current-state.md` — estado operacional detalhado e handoff.
- `production/roadmap.md` — escopo, fases e checklist.
- `production/production-handbook.md` — fluxo de producao.
- `production/ai-assisted-production-pipeline.md` — pipeline assistido por IA.
- `docs/00_Project/project-overview.md` — visao geral e pilares.
- `docs/08_UnityPipeline/prototype-theo-controller.md` — cena/controlador e sistemas do prototipo.
- `docs/03_VisualDevelopment/pixel-art-bible.md` — padrao visual pixel art.
- `docs/03_VisualDevelopment/sprite-prompt-guide.md` — prompts e escalas.
- `unity/FragmentosDoAmanha/Assets/Art/Characters/Theo/README.md` — organizacao dos frames de Theo.
- `ChatGPT/GDD.md` e subpastas de `ChatGPT/` — GDD e documentos historicos de design/narrativa.

---

## Regra de manutencao

Atualizar este documento sempre que houver mudanca relevante em engine/pacotes, arquitetura de scripts, controles, cenas, pipeline de arte, formatos de assets ou escopo. O estado de tarefas deve continuar sendo mantido nos arquivos de `production/`; nao duplicar checklists operacionais aqui.
