# Portfólio SQL: Engenharia Reversa, Normalização e Análise Histórica da Copa do Mundo

## 📺 Vídeo de Demonstração (Pitch de 1 Minuto)
▶️ [Clique aqui para assistir ao vídeo do projeto](https://drive.google.com/drive/folders/1KeYC20xCuiH6TCrP8KVwUEJfO-olL167?usp=drive_link)
> *Nota: O vídeo demonstra a execução em tempo real da consulta analítica sobre a Média de Gols em Finais por Estádio.*

## 📜 Certificados DataCamp
* 🎓 [Certificados de Nivelamento SQL - DataCamp](https://drive.google.com/drive/folders/1tNv_IeBCvQbvBji5y7qNNSS-T7-FAoob?usp=drive_link)

## 🗺️ Modelo Entidade-Relacionamento (ME-R)

### ❌ Antes (Estrutura Bruta/Não-Normalizada)
Os dados originais em formato CSV continham sérios problemas de redundância. Nomes de países, estádios e cidades eram repetidos textualmente em milhares de linhas. Isso causava anomalias de inserção, inconsistência de escrita e desperdício de armazenamento.

###  Depois (Estrutura Otimizada - 3ª Forma Normal)
Após o processo de engenharia reversa, os dados foram isolados em tabelas lógicas interconectadas por chaves primárias (PK) e estrangeiras (FK), eliminando as redundâncias textuais[cite: 2]:
* **TB_SELECAO** (`id_selecao` [PK], `nome_selecao` [UNIQUE])[cite: 2]
* **TB_CIDADE** (`id_cidade` [PK], `nome_cidade`, `pais_sede`)[cite: 2]
* **TB_ESTADIO** (`id_estadio` [PK], `nome_estadio`, `id_cidade` [FK])[cite: 2]
* **TB_PARTIDA** (`id_partida` [PK], `ano`, `data_hora`, `fase`, `id_estadio` [FK], `id_selecao_casa` [FK], `gols_casa`, `gols_visitante`, `id_selecao_visitante` [FK], `publico`)[cite: 2]
* **TB_JOGADOR** (`id_jogador` [PK], `nome_jogador` [UNIQUE])[cite: 2]
* **TB_JOGADOR_PARTIDA** (`id_partida` [FK], `id_jogador` [FK], `id_selecao` [FK], `posicao`, `num_camisa`, `evento`) -> *Chave Primária Composta (`id_partida`, `id_jogador`)*[cite: 2]

## 📊 Dossiê das 15 Consultas Analíticas

| Nº | Enunciado Original da Pergunta (O que a Query faz?) | Justificativa de Inovação Analítica (De forma humanizada) |
| :--- | :--- | :--- |
| **1.0** | Escreva uma consulta que calcule a média de gols em finais por estádio, filtre palcos de decisões e avalia a tendência histórica de gols.[cite: 2] | Em vez de olhar para a Copa inteira (onde goleadas contra times pequenos distorcem os dados), esta query foca apenas no jogo do título, onde a pressão é gigante.[cite: 2] |
| **2.0** | Escreva uma consulta que mostre os jogadores que fizeram gols em jogos perdidos, cruze o evento de gol do jogador com o placar desfavorável da equipe.[cite: 2] | Ela cruza uma informação individual (o gol do atleta) com o resultado coletivo (a derrota do time), achando atuações brilhantes que infelizmente acabaram em derrota.[cite: 2] |
| **3.0** | Escreva uma consulta que busque estádios que acumulam médias altas de público em jogos com goleadas.[cite: 2] | Descobre quais arenas costumam entregar um verdadeiro espetáculo para os adeptos, cruzando estádios cheios com partidas que tiveram 4 gols ou mais.[cite: 2] |
| **4.0** | Analise o desempenho de gols de países quando jogam em casa.[cite: 2] | O banco faz um teste inteligente: ele checa se o nome da seleção que está a jogar é igual ao nome do país que está a sediar aquela Copa.[cite: 2] |
| **5.0** | Escreva uma consulta que identifique os estádios que receberam a maior diversidade de seleções distintas.[cite: 2] | Em vez de só contar o número de jogos, ela usa um filtro para contar países únicos, mostrando quais arenas foram as mais "globais" e cosmopolitas.[cite: 2] |
| **6.0** | Escreva uma query que mostre o ranking de cidades onde o somatório de gols marcados tanto por mandantes quanto visitantes foi superior.[cite: 2] | Mapeia as cidades onde as redes mais balançaram, ajudando a entender se fatores como altitude ou clima influenciaram no ritmo do futebol.[cite: 2] |
| **7.0** | Escreva uma consulta que mostre o total de gols e média de público mapeados por década, faça um Agrupamento cronológico para avaliar a evolução da audiência vs placares.[cite: 2] | O código faz uma conta matemática para juntar os anos de 10 em 10, permitindo-nos ver a evolução do desporto desde a década de 1930 até hoje.[cite: 2] |
| **8.0** | Escreva uma consulta que mostre as seleções com piores desempenhos defensivos fora de casa. Isole os jogos como visitante para encontrar defesas frágeis externas.[cite: 2] | Isola completamente o desempenho defensivo das equipes quando elas jogam fora de casa, sem o apoio direto de sua torcida.[cite: 2] |
| **9.0** | Escreva uma consulta que calcule a média de gols apenas em fases eliminatórias avançadas, ignorando fases de grupo e focando em semifinais e finais.[cite: 2] | Ignora a fase de grupos e calcula se os times jogam mais trancados ou mais abertos quando estão a apenas um ou dois passos da taça.[cite: 2] |
| **10** | Escreva uma consulta que mostre os jogadores com maior densidade de gols/cartões por seleção, filtre strings de eventos para mapear a participação ativa do atleta em campo.[cite: 2] | Ela varre o histórico de eventos textuais para contar quantas vezes o nome de um jogador apareceu envolvido em momentos capitais da partida.[cite: 2] |
| **11** | Consulte as partidas com placar empatado por fase, medindo quais fases historicamente produzem mais prorrogações ou igualdades.[cite: 2] | Mostra em qual etapa do torneio o nível tático fica tão parecido que os jogos tendem a ir para o prolongamento ou para as grandes penalidades.[cite: 2] |
| **12** | Escreva uma consulta que localize arenas construídas que receberam pouquíssimos jogos na história do torneio.[cite: 2] | Usa o filtro de agrupamento para encontrar arenas que custaram caro mas foram pouquíssimo aproveitadas na história da competição.[cite: 2] |
| **13** | Descubra quais seleções aplicam mais pressão de gols quando jogam em seus domínios normais.[cite: 2] | Define um mínimo de 10 jogos disputados para criar um ranking justo e realista das seleções mais avassaladoras dentro dos seus domínios.[cite: 2] |
| **14** | Consulte os picos e vales de presença do público total em estádios por edição anual.[cite: 2] | Compara no mesmo ano o jogo de maior interesse (como a abertura ou final) com aquele jogo menos apelativo, mostrando a disparidade de público.[cite: 2] |
| **15** | Localize atletas resilientes que jogaram muitas partidas pertencendo a ligas menores.[cite: 2] | Esconde de propósito as grandes potências (Brasil, Alemanha, Itália...) para encontrar aqueles guerreiros de seleções menores que fizeram história no torneio.[cite: 2] |
