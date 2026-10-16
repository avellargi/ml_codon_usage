<img src= "images/imagem (1).png"/>

<h1 align="center">Viés de uso de códons como preditor do grupo taxonômico: uma comparação de algoritmos de aprendizado de máquina</h1>

<p align="center">
  <img src="images/header (3).png" />
</p>

Este repositório contém o código-fonte desenvolvido para a Entrega Final (denominada no sistema de gamificação 'Tiamat') da disciplina "Aprendizado de Máquina" do segundo semestre do Bacharelado em Ciência e Tecnologia da Ilum. O objetivo do trabalho é investigar se é possível identificar o grupo taxonômico de um organismo a partir do seu viés de uso de códons, isto é, da frequência com que cada um dos 64 códons aparece em seu genoma [1]. Para isso, foram comparados cinco algoritmos de aprendizado de máquina (regressão logística, k-vizinhos mais próximos, árvore de decisão, floresta aleatória e [quinto algoritmo]) e um modelo baseline, utilizando o conjunto de dados "Codon Usage", disponível no UCI Machine Learning Repository. Os hiperparâmetros de cada algoritmo foram otimizados com a biblioteca Optuna, e o desempenho dos modelos foi avaliado por validação cruzada e, ao final, em um conjunto de teste separado.

## Conjunto de Dados
O trabalho utiliza o conjunto de dados **Codon Usage**, disponibilizado pelo UCI Machine Learning Repository [2]. A base contém as frequências de uso dos 64 códons em 13.028 organismos de 11 grupos taxonômicos (arqueias, bactérias, bacteriófagos (separados dos demais vírus), plasmídeos, plantas, invertebrados, vertebrados, mamíferos, roedores, primatas e vírus), compiladas a partir do banco de dados CUTG (Codon Usage Tabulated from GenBank).
Após a etapa de limpeza, foram mantidas apenas as entradas de DNA genômico, sem duplicatas, totalizando 9.210 organismos, descritos por 65 atributos (as frequências dos 64 códons e o número total de códons) e classificados em seis grupos taxonômicos: arqueias, bactérias, vírus (incluindo bacteriófagos), plantas, invertebrados e vertebrados (incluindo mamíferos, roedores e primatas). Os plasmídeos foram excluídos por não serem organismos.

## Modelos Analisados
- **Modelo Baseline (DummyClassifier):** utilizado como referência para avaliar se os modelos desenvolvidos apresentam desempenho superior ao obtido por uma estratégia baseada na classe majoritária, isto é, na moda;
-  **Regressão Logística:** modelo linear de classificação que estima a probabilidade de cada classe a partir de uma combinação linear dos atributos, atribuindo ao exemplo a classe de maior probabilidade;
- **k-Nearest Neighbors (k-NN):** algoritmo supervisionado de classificação baseado na proximidade entre exemplos, em que a classe de uma observação é determinada a partir das classes de seus vizinhos mais próximos;
- **Árvore de Decisão (DecisionTree):** algoritmo que divide sucessivamente os dados por meio de regras do tipo "se... então" aplicadas aos atributos, buscando formar grupos cada vez mais homogêneos em relação à classe, o que gera um modelo interpretável;
- **Floresta Aleatória (RandomForest):** modelo de comitê composto por várias árvores de decisão, cada uma treinada com uma amostra diferente dos exemplos e dos atributos, em que a classe final é definida pela votação entre as árvores;
- **Gradient Boosting (HistGradientBoosting):** modelo de comitê que treina árvores de decisão em sequência, em que cada nova árvore busca corrigir os erros cometidos pelas anteriores; a versão baseada em histogramas agrupa os valores dos atributos em faixas, o que torna o treino mais rápido.
  
## Métricas de Desempenho
Os modelos foram analisados por meio das seguintes métricas:
- **F1 macro (métrica principal):** média simples do F1 de cada classe, em que o F1 combina precisão e sensibilidade. Por dar o mesmo peso a todos os grupos taxonômicos, independentemente do número de exemplos, foi utilizada na otimização dos hiperparâmetros e na escolha do melhor modelo, já que as classes são desbalanceadas;
- **Acurácia:** proporção de organismos classificados corretamente, reportada para comparação com o baseline e com outros trabalhos da literatura.

## Tecnologias Utilizadas
- Python (3.13.7): linguagem utilizada para o desenvolvimento do projeto;

- pandas (2.3.3): utilizada para leitura, organização e manipulação de dados;

- NumPy (2.2.6): foi empregada para manipulação de arrays e operações matemáticas;

- Matplotlib (3.10.6): utilizada para a construção de gráficos e visualização dos resultados;

- Seaborn (0.13.2): foi empregada para a visualização estatística dos dados;

- Scikit-Learn (1.7.2): implementação dos modelos, divisão treino-teste e cálculo das métricas de desempenho;

- Optuna (4.5.0): utilizado para a otimização dos hiperparâmetros de cada modelo.


## Acesso ao código
As informações detalhadas do projeto, incluindo a fundamentação teórica, as etapas de pré-processamento dos dados, a construção e treinamento dos modelos de aprendizado de máquina, a avaliação de desempenho e a análise dos resultados obtidos, estão disponíveis no repositório em: [código](https://github.com/avellargi/ml_codon_usage/tree/main/code)

## Autoria
| <img src="https://github.com/avellargi.png" width=115><br><sub>[Giovanna Avellar Machado](https://github.com/avellargi)</sub> |
| :--: |
Giovanna Avellar Machado - Aluna do Segundo Semestre do Bacharelado em Ciência, Tecnologia e Inovação da Ilum - Escola de Ciência 

## Professor Orientador
| <img src="https://github.com/user-attachments/assets/17dfa7bf-5ca9-42df-b63e-917827fc6308" width=115><br><sub>[Prof. Dr. Daniel Roberto Cassar](http://lattes.cnpq.br/1717397276752482)</sub> |
| :--: |
Daniel Roberto Cassar - Docente Pesquisador da Ilum – Escola de Ciência. Doutorado em Ciência e Engenharia de Materiais (UFSCar) e Pós-Doutorado pela UFSCar. Atua na área de Informática de Materiais.

## Referências Bibliográficas
[1] PARVATHY, Sujatha Thankeswaran; UDAYASURIYAN, Varatharajalu; BHADANA, Vijaipal. Codon usage bias. Molecular Biology Reports, v. 49, n. 1, p. 539-565, 2022. DOI: 10.1007/s11033-021-06749-4. Disponível em: https://pmc.ncbi.nlm.nih.gov/articles/PMC8613526/. Acesso em: 21 set. 2026. <br>
[2] HALLEE, L.; KHOMTCHOUK, B. B. Codon usage [Dataset]. UCI Machine Learning Repository, 2020. Disponível em: https://doi.org/10.24432/C5KP6B. Acesso em: 21 set. 2026. <br>

P.S. As referências estão ordenadas em ordem de aparição no documento.

<img src= "images/imagem (2).png"/>
