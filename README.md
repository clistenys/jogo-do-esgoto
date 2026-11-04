# Jogo do Esgoto

Projeto pessoal de estudo e portfólio desenvolvido em Unity. Este README é o **Game Design Document (GDD) vivo** do jogo: reúne a visão, o material produzido, o estado da implementação e as decisões que ainda precisam ser tomadas.

**Fase atual:** preparação do personagem e de suas animações, usando um projeto de tutorial como base de estudo. Ainda não há uma versão final do jogo.

## Visão do jogo

| Elemento | Definição atual |
| --- | --- |
| Nome de trabalho | Jogo do Esgoto |
| Personagem | João, identificado nos arquivos de arte como `joao` |
| Apresentação visual | 2D em pixel art |
| Engine | Unity 6 — `6000.3.25f1` |
| Objetivo do projeto | Aprender desenvolvimento de jogos e construir um portfólio |
| Gênero e ritmo | A definir; o repositório contém uma base de estudo Roguelike 2D |
| Plataformas de lançamento | A definir |
| Público-alvo | A definir |

O nome sugere uma ambientação em esgotos, mas a história, o papel de João nesse mundo e o objetivo da aventura ainda precisam ser definidos. A presença de recursos do tutorial não significa que suas regras serão adotadas no jogo final.

## Experiência e regras

As decisões abaixo devem orientar a implementação conforme o projeto evoluir.

| Área | Decisão pendente |
| --- | --- |
| Objetivo do jogador | O que João precisa conquistar em uma partida ou fase? |
| Ciclo principal | Quais ações o jogador repete e que recompensa recebe? |
| Movimento | Livre ou em grade? Em tempo real ou por turnos? |
| Combate | Como atacar, acertar um alvo e calcular dano? |
| Dash | Será uma habilidade própria ou apenas a representação do deslocamento? |
| Sobrevivência | Como funcionam vida, dano, recuperação e morte? |
| Vitória e derrota | O que encerra uma fase ou partida? O que acontece ao reiniciar? |
| Progressão | Fases, habilidades, itens e melhorias: quais farão parte do escopo? |
| Controles | Dispositivos, comandos e possibilidade de remapeamento |

**Proposta para o primeiro protótipo, ainda sujeita à decisão do autor:** uma área pequena onde seja possível controlar João, testar um ataque contra um alvo, receber dano e reiniciar após a morte. Essa proposta delimita um teste de gameplay; não representa funcionalidades concluídas.

## João e suas animações

Os GIFs abaixo são prévias da arte, não gravações de gameplay. Eles estão em [`Assets/Documentation`](Assets/Documentation). Ter uma animação disponível não significa que a mecânica correspondente já esteja implementada.

| Repouso — Idle | Ataque — Attack | Deslocamento — Dash |
| :---: | :---: | :---: |
| ![João em repouso](Assets/Documentation/joao-idle.gif) | ![João atacando](Assets/Documentation/joao-attack.gif) | ![João em deslocamento](Assets/Documentation/joao-dash.gif) |

| Dano — Hurt | Morte — Death |
| :---: | :---: |
| ![João recebendo dano](Assets/Documentation/joao-hurt.gif) | ![Animação de morte de João](Assets/Documentation/joao-death.gif) |

### Integração no Unity

| Arte | Clip existente | Situação |
| --- | --- | --- |
| `joao-idle.png` | `PlayerIdle.anim` | Estado inicial do controller |
| `joao-attack.png` | `PlayerAttack.anim` | Clip e estado criados |
| `joao-dash.png` | `PlayerMove.anim` | Arte de dash utilizada no clip de movimento |
| `joao-hurt.png` | `PlayerHurt.anim` | Clip e estado criados |
| `joao-death.png` | `PlayerDeath.anim` | Clip e estado criados |

O `PlayerAnimationController` contém esses cinco estados, mas ainda não possui parâmetros nem transições. A integração entre comandos, regras e animações está pendente. A diferença entre o nome da arte `dash` e o clip `PlayerMove` deve ser resolvida conceitualmente antes de definir a habilidade.

## Mundo, fases e apresentação

| Área | Estado do design |
| --- | --- |
| Narrativa | História, motivação do protagonista e tom a definir |
| Cenários | Layouts, obstáculos, interação e identidade visual a definir |
| Inimigos | Tipos, comportamentos e relação com o combate a definir |
| Itens | Funções, disponibilidade e efeitos a definir |
| Interface | Informações essenciais, menus e feedback a definir |
| Áudio | Trilha, efeitos e identidade sonora a definir |

O repositório inclui recursos de tutorial. A seleção de quais serão usados, substituídos ou mantidos apenas para estudo ainda faz parte do trabalho de design.

## Estado atual do desenvolvimento

- [x] Sprites de repouso, ataque, dash, dano e morte importados.
- [x] GIFs de apresentação disponíveis na documentação.
- [x] Cinco clips e um Animator Controller criados.
- [x] Objeto `Player` com SpriteRenderer e Animator adicionado à cena `TutorialMain`.
- [ ] Definir o ciclo principal, o objetivo e as condições de vitória e derrota.
- [ ] Integrar o personagem ao controle de gameplay.
- [ ] Configurar e validar parâmetros e transições das animações.
- [ ] Testar as regras do primeiro protótipo no Unity.
- [ ] Definir o escopo de fases, inimigos, interface e áudio.
- [ ] Preparar uma versão jogável para apresentação no portfólio.

Esta lista registra o que pode ser identificado nos arquivos. Não substitui testes de execução no Editor.

## Organização do repositório

```text
Assets/
├── _Project/
│   ├── Animations/       # Clips e controller do personagem
│   └── Sprites/          # Sprites utilizados pelo personagem
├── Documentation/       # GIFs exibidos neste GDD
├── Roguelike2D/          # Material e código da base de estudo
└── Settings/             # Configurações de renderização
Packages/                 # Dependências e versões resolvidas
ProjectSettings/          # Configurações do projeto Unity
README.md                 # GDD vivo
```

Os arquivos de produção de arte mantidos fora deste repositório não são necessários para exibir os GIFs deste README.

## Abrindo o projeto

1. Clone o repositório com Git LFS instalado para obter os arquivos binários versionados por LFS.
2. No Unity Hub, adicione a pasta que contém `Assets`, `Packages` e `ProjectSettings`.
3. Abra com a versão **6000.3.25f1** e aguarde a importação dos assets e a resolução dos pacotes.
4. Para inspecionar o personagem adicionado, abra `Assets/Roguelike2D/TutorialVersion/Scenes/TutorialMain.unity`.

As cenas atualmente listadas nas configurações de build pertencem à `ExtendedVersion` do tutorial. Elas não representam uma build final do Jogo do Esgoto nem incluem automaticamente as alterações da cena `TutorialMain`.

## Autoria, estudo e manutenção

O desenvolvimento do game e suas decisões de implementação ficam com o autor do projeto. A assistência de IA é usada para mentoria, análise, sugestões e tarefas de documentação e versionamento autorizadas pelo autor. A arte também conta com assistência de ferramentas de IA; os recursos do tutorial devem ser distinguidos do trabalho desenvolvido para o jogo ao apresentar o portfólio.

As mensagens de commit são escritas **em inglês**, seguindo os [padrões de commits](https://github.com/iuricode/padroes-de-commits). Cada commit deve reunir uma mudança coerente, incluindo os arquivos `.meta` correspondentes aos assets. Pastas geradas, como `Library` e `Temp`, ficam fora do versionamento.

Atualize este GDD quando uma decisão de design for tomada ou uma etapa for validada. Mantenha propostas identificadas como propostas e marque como concluído apenas o que tiver sido efetivamente realizado.
