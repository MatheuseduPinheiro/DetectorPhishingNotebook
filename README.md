# Detecção de URLs de Phishing

Este projeto tem como foco detectar URLs de phishing usando técnicas de aprendizado de máquina. O conjunto de dados contém uma variedade de URLs, rotuladas como phishing ou legítimas, e o objetivo é construir um modelo que possa prever se uma URL é segura ou maliciosa.

## Conjunto de Dados

O conjunto de dados utilizado para este projeto é o [PhiUSIIL Phishing URL Dataset](https://www.phiusiil.org/). Ele contém várias URLs com rótulos correspondentes (`phishing` ou `legítima`). Cada URL é analisada e transformada em características numéricas para fins de classificação.

**Colunas**:
- `URL`: A URL do site.
- `label`: O rótulo correspondente, onde 1 representa um site de phishing e 0 representa um site legítimo.

## Etapas Envolvidas

### 1. Carregamento e Exploração dos Dados
O primeiro passo é carregar o conjunto de dados e explorar seu conteúdo. Estatísticas básicas, como o número de valores ausentes e os tipos de cada recurso, são verificadas. O conjunto de dados é analisado para identificar quaisquer problemas potenciais, como dados ausentes e tipos de dados.

- **Porcentagem de valores ausentes:** Um cálculo é feito para verificar se o conjunto de dados possui valores nulos.
- **Tipos de dados:** Os tipos de dados das colunas são exibidos para garantir que não haja inconsistências.

### 2. Seleção de Recursos
Focamos em usar a URL como nosso recurso principal para previsão.

### 3. Transformação de Dados (TF-IDF)
As URLs são transformadas em características numéricas usando o método **TF-IDF (Frequência de Termo-Frequência Inversa do Documento)**. Este método converte o texto em vetores numéricos, atribuindo pesos de importância aos termos com base em sua frequência no conjunto de documentos.

### 4. Divisão dos Dados
O conjunto de dados é dividido em conjuntos de treinamento e teste usando uma divisão de 80/20 com `train_test_split` do `sklearn`.

### 5. Treinamento do Modelo
Utilizamos um **Classificador de Árvore de Decisão** para treinar o modelo. Este é um algoritmo de aprendizado de máquina supervisionado usado para tarefas de classificação.

### 6. Avaliação do Modelo
Após treinar o modelo, previsões são feitas no conjunto de teste. O modelo é avaliado usando as seguintes métricas:
- **Acurácia:** Mede a correção geral do modelo.
- **Matriz de Confusão:** Visualiza o desempenho do modelo de classificação.
- **Precisão:** Mede quantas das previsões positivas foram realmente corretas.
- **Revocação:** Mede quantos positivos reais foram corretamente previstos.
- **F1-Score:** A média harmônica da precisão e da revocação, fornecendo uma métrica equilibrada.

### 7. Salvamento do Modelo
O modelo treinado e o vetorizador utilizado para transformar as URLs são salvos usando `joblib`. Isso permite que carreguemos e reutilizemos o modelo para previsões futuras.

### 8. Função de Predição de URL
Uma função `predict_phishing(url)` é criada para prever se uma URL fornecida é de phishing ou legítima. A função carrega o modelo treinado e o vetorizador e faz previsões com base na URL fornecida.

## Uso

Para usar este projeto, siga estas etapas:

### 1. Clone o repositório
```bash
git clone https://github.com/seu_usuario/PhishingURLDetection.git
cd PhishingURLDetection
```
## Instalação das Dependências

Para instalar as bibliotecas necessárias, execute os seguintes comandos:

```bash
pip install scikit-learn
pip install pandas
pip install seaborn
pip install matplotlib
pip install joblib
