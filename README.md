# Fragmentos do Amanha

Documentacao de producao de *Fragmentos do Amanha* / *Era Zero*, um metroidvania 2D de acao-plataforma sobre viagem no tempo, desenvolvido na Unity com apoio de IA em documentacao, arte, animacao, pipeline e programacao.

## Visao rapida

Theo, um cientista inicialmente nao-combatente, foge pelo tempo para desfazer o golpe de Voss, seu ex-parceiro, que reescreveu a historia para se tornar um tirano absoluto. Em cada epoca, uma versao da linhagem de Naiara atua como resistencia contra essa tirania.

O jogo usa duas camadas de arte:
- **Artbook e apresentacao:** ilustracoes detalhadas para lore, direcao visual e comunicacao.
- **In-game:** pixel art limpa, legivel, animavel e otimizada para gameplay.

## Estrutura atual

A migracao dos conteudos criativos e documentais foi incorporada na main. As pastas antigas duplicadas foram removidas; os caminhos canonicos sao:

- `Game/` - assets aprovados e projeto Unity (o projeto Unity ainda aguarda transferencia tecnica).
- `Sprites/` - producao visual, PSDs, PNGs, estudos, spritesheets e historico.
- `Artbook/` - concepts, ilustracoes, referencias, branding e publicacoes.
- `Documents/` - GDD, narrativa, personagens, game design e documentacao tecnica.
- `Production/` - prompts, workflows, ferramentas, status e roadmap.

Documentos de governanca:
- [Manual de organizacao](Documents/TechnicalDocumentation/PROJECT_ORGANIZATION_GUIDE.md)
- [Plano de migracao](Documents/TechnicalDocumentation/REPOSITORY_MIGRATION_PLAN.md)
- [Status da migracao](Documents/TechnicalDocumentation/MIGRATION_STATUS_2026-11-15.md)
- [Inventario do repositorio](Documents/TechnicalDocumentation/REPOSITORY_INVENTORY_2026-11-15.md)

## Fluxo de assets

Produzir em `Sprites/`, preservar PSD + PNG e versoes relevantes, aguardar a aprovacao explicita **Aprovado**, publicar somente a exportacao aprovada em `Game/ApprovedAssets/` e integrar a mesma exportacao no projeto Unity. A organizacao de arquivos nao equivale a aprovacao criativa.

## Caminhos importantes

- [Status atual](Production/Status/Current-Status.md)
- [Handoff atual](Production/Status/Handoff-Current-State.md)
- [Roadmap](Production/Roadmap/Roadmap.md)
- [Manual de producao](Production/Workflows/Production-Handbook.md)
- [Pipeline de producao assistida por IA](Production/Workflows/AI-Assisted-Production-Pipeline.md)
- [Visao geral do projeto](Documents/GDD/Project/project-overview.md)
- [Direcao visual](Documents/ArtDirection/VisualDevelopment/visual-development-guide.md)
- [Biblia de pixel art](Documents/ArtDirection/VisualDevelopment/pixel-art-bible.md)
- [DNA dos personagens](Documents/Characters/character-dna.md)
- [Biblia de animacao](Documents/Animation/animation-bible.md)
- [Pipeline Unity](Documents/UnityPipeline/unity-production-pipeline.md)

## Unity

O projeto Unity real continua em `unity/FragmentosDoAmanha/` ate a fase especifica de transferencia para `Game/Unity/FragmentosDoAmanha/`. Nao mova essa pasta manualmente. A transferencia sera isolada, preservando `Assets/`, `Packages/`, `ProjectSettings/`, arquivos `.meta` e GUIDs, e validada no Unity Editor.

## Escopo inicial

O primeiro objetivo de producao e um vertical slice com Era Zero e Egito Antigo, Theo jogavel, movimento, camera, combate basico, um inimigo simples, vida/dano, tilesets iniciais e prefabs modulares.

## Uso de IA

A IA deve atuar como assistente de producao, nao como diretora criativa. A validacao final permanece manual.
