# Análise de Transição de Fase nos Problemas 3-SAT e 5-SAT

Este repositório contém o código e os resultados de um trabalho prático para a disciplina de Lógica para Computação. O projeto investiga e compara o fenômeno da transição de fase nos problemas 3-SAT e 5-SAT.

## 📜 Sobre o Projeto

O Problema de Satisfatibilidade Booleana (SAT) é central para a ciência da computação. Este projeto foca em uma característica fascinante de problemas NP-completos como o k-SAT: a **transição de fase**.  Trata-se de um ponto crítico na razão entre o número de cláusulas ($$m$$) e o número de variáveis ($$n$$), conhecida como $$\alpha$$, onde a probabilidade de uma fórmula ser satisfatível (SAT) despenca abruptamente de 1 para 0.

O objetivo deste trabalho é:

  * Gerar instâncias aleatórias para os problemas 3-SAT e 5-SAT.
  * Resolver as instâncias utilizando um solver SAT moderno.
  * Analisar a probabilidade de satisfatibilidade e o tempo médio de execução em função da razão $$\alpha$$.
  * Estimar e comparar os pontos críticos ($$\alpha_c$$) para ambos os casos, 3-SAT e 5-SAT. 

## 🛠️ Metodologia

A abordagem foi dividida em módulos para gerar instâncias, executar os experimentos e plotar os resultados. 

1.  **Geração de Instâncias (`gerar_instancia`)**: Uma função foi criada para gerar instâncias k-SAT, garantindo que não haja cláusulas repetidas nem literais contraditórios na mesma cláusula. 
2. **Execução do Experimento (`executar_experimento`)**: Para um conjunto de variáveis `n` e uma faixa de valores `alpha`, 30 instâncias foram geradas e resolvidas. O solver `Glucose4` (da biblioteca `PySAT`) foi utilizado para verificar a satisfatibilidade e medir o tempo de execução. 
3.  **Análise do Ponto Crítico (`pegar_alfa_critico`)**: O ponto crítico ($$\alpha_c$$) foi estimado como o valor de `alpha` onde o tempo médio de execução do solver atinge seu pico máximo, indicando a região de maior dificuldade computacional. 

## 📊 Resultados

Os experimentos revelaram uma clara transição de fase para ambos os problemas, com picos de dificuldade computacional concentrados em torno de um valor crítico $$\alpha_c$$.

### 3-SAT

  * **Valores de `n` testados**: 50, 100, 150, 200. 
  * **Ponto Crítico Estimado ($$\alpha_c$$)**: **4.40** 

O gráfico de probabilidade mostra uma queda acentuada em torno de $$\alpha_c$$, e o gráfico de tempo confirma que as instâncias mais difíceis se concentram nessa região.


### 5-SAT

  * **Valores de `n` testados**: 20, 30, 40, 50. 
  * **Ponto Crítico Estimado ($$\alpha_c$$)**: **21.50** 

O 5-SAT também exibe uma transição de fase, mas seu ponto crítico ocorre em um valor de $$\alpha$$ significativamente mais alto que o do 3-SAT. O tempo de execução no pico também é maior, indicando uma complexidade superior. 



## 🚀 Como Executar

O projeto foi desenvolvido em um notebook do Google Colab. Para reproduzir os resultados, siga os passos abaixo:

### Pré-requisitos

  * Python 3 

### Instalação

Clone o repositório e baixe a matplotlib(caso não tenha)

```bash
pip install python-sat numpy matplotlib
```

### Execução

1.  Abra o notebook `trabalho_logica.ipynb` em um ambiente como Jupyter ou Google Colab.
2.  Execute as células em ordem sequencial.
      * **Atenção**: A célula que executa `executar_experimento()` é computacionalmente intensiva e pode levar cerca de 40 minutos para ser concluída para 30 instâncias. 
3.  Após a execução, os gráficos `3-SAT_probabilidade.png`, `3-SAT_tempo.png`, `5-SAT_probabilidade.png` e `5-SAT_tempo.png` serão salvos no diretório.

## 🛠️ Desenvolvido Com

  * [Python 3](https://www.python.org/)
  * [Google Colab](https://colab.research.google.com/) 
  * [PySAT](https://pysathq.github.io/) (Solver Glucose4) 
  * [NumPy](https://numpy.org/) 
  * [Matplotlib](https://matplotlib.org/) 


