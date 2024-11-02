# NDAE-Projeto_e_Arquitetura_de_Software-Cria-o_de_diagrama_de_classes_com_scout_s-mula
Avaliação 2 - Criação de diagrama de classes com scout/súmula de competição esportiva

Atividade avaliativa consiste em construir um diagrama de classe com base no modelo de classes fornecido em aula - slide 176 do arquivo https://www.dropbox.com/scl/fi/ze53uqdz4jkofa8uohsh4/Projeto-de-Software-com-UML.pdf?rlkey=5lottt8qk296batfsjdrxkxhz&dl=0
para isso deve-se construir um modelo de classes para registro de eventos de alguma competição esportiva que envolva pelo menos duas equipes participantes. São exemplos de contextos aceitos: partida de voleibol, partida de basquetebol, corrida de automóveis, etc.

Entregar a solução na forma de uma imagem em alta resolução do diagrama produzido e um texto explicativo do contexto modelado.

--------------------------------------------//--------------------------------------------------------------------------------

DESCRIÇÃO DA RESOLUÇÂO

Para descrever um diagrama de classes UML em um cenário esportivo, usarei como exemplo um jogo de basquete. Este diagrama se baseará na imagem apresentada, modificando as classes e relações para espelhar os aspectos particulares deste tipo de competição.

--------------------------------------------//--------------------------------------------------------------------------------

CONTEXTO MODELADO

O modelo detalha o registro de acontecimentos durante um jogo de basquete, no qual duas equipes disputam entre si. O modelo permite o registro de eventos como substituições, pontuações e ausências em cada equipe. O jogo é parte de uma competição, podendo contar com um árbitro principal e assistentes. A ferramenta computacional de suporte para criação do Diagrama de Classe foi o Astah UML Versão 10.0.0 Release 30/10/2024.

--------------------------------------------//--------------------------------------------------------------------------------

DESCRIÇÃO DAS CLASSES

Classe: Torneio
- Atributos: dataInicio (int), dataFim (int), nome (String).
- Descrição: Representa o torneio em que a partida de basquete ocorre, com datas de início e fim e um nome para identificação.
- Relacionamentos:
Relacionamento 0..1 com a classe Jogo, indicando que o torneio pode ter vários jogos, mas um jogo específico pode pertencer a um único torneio.

Classe: Jogo
- Atributos: dataHora (int), publicoPagante (int).
- Descrição: Representa uma partida específica do torneio.
- Relacionamentos:
Relacionamento 1..* com EquipeEmJogo, indicando que cada jogo envolve duas equipes.
Relacionamento 1..* com Arbitro, onde há um árbitro principal e até dois auxiliares.
Relacionamento 0..1 com Estadio, onde o jogo ocorre.
Relacionamento com Escalacao, representando a lista de jogadores titulares e reservas em cada equipe para o jogo.

Classe: Equipe
- Atributos: nome (String).
- Descrição: Representa uma equipe de basquete que participa do jogo.
- Relacionamentos:
- Relacionamento 0..1 com EquipeEmJogo, indicando que uma equipe específica pode participar de vários jogos.

Classe: EquipeEmJogo
- Atributos: qtdCestasMarcadas (int).
- Descrição: Representa uma equipe específica em um jogo, com a contagem de pontos marcados.
- Relacionamentos:
Relacionamento com Gol (ou Pontuação), indicando as cestas feitas pela equipe.

Classe: Jogador
- Atributos: nome (String), apelido (String), posicao (int).
- Descrição: Representa um jogador específico, com posição na quadra.
- Relacionamentos:
Relacionamento com EscalacaoJogador, definindo a função e o tipo de cada jogador (titular ou reserva) em um jogo específico.

Classe: Escalacao
- Descrição: Representa a formação de jogadores em uma equipe durante um jogo.
- Relacionamentos:
Relacionamento com EscalacaoJogador, que define os jogadores e suas funções na partida.

Classe: EscalacaoJogador
- Atributos: funcao (int), tipo (titular/reserva).
- Descrição: Representa o papel de um jogador específico no jogo (ex.: armador, pivô, etc.), e se ele é titular ou reserva.

Classe: Gol (ou Pontuação)
- Atributos: instante (int).
- Descrição: Representa uma cesta marcada em um instante específico.
- Relacionamentos:
Associado a EquipeEmJogo, indicando qual equipe marcou o ponto.

Classe: Substituicao
- Atributos: instante (int).
- Descrição: Registra uma substituição de jogador durante o jogo.
- Relacionamentos:
Conecta Jogador substituído e substituto, indicando uma troca de jogadores em campo.

Classe: Cartao (ou Falta)
- Atributos: instante (int), cor (int).
- Descrição: Representa uma falta registrada para um jogador em um instante específico.
- Relacionamentos:
Relacionamento com Jogador, para identificar o atleta que cometeu a falta.

Classe: Arbitro
- Atributos: nome (String).
- Descrição: Representa um árbitro que participa da partida.
- Relacionamentos:
Um árbitro principal e até dois auxiliares em cada Jogo.

Classe: Estadio
- Atributos: nome (String).
- Descrição: Representa o local onde o jogo ocorre.
- Relacionamentos:
Conexão com Jogo, indicando o local da partida.

Classe: Relacionamentos
- Composições e agregações entre as classes modelam a hierarquia e participação de equipes, jogadores e eventos durante o jogo.
- Associações entre classes como Jogador, Substituicao, e Cartao permitem registrar eventos específicos de substituições e faltas.
