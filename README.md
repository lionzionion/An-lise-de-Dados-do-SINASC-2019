# An-lise-de-Dados-do-SINASC-2019
# Análise de Dados do SINASC 2019

Este notebook realiza uma análise exploratória dos dados do SINASC (Sistema de Informações sobre Nascidos Vivos) para o ano de 2019. Os passos incluem a importação de bibliotecas, download e carregamento dos dados, seguido pela criação de visualizações, como boxplots e histogramas.

---

## Boxplot da Idade da Mãe

Neste exemplo, é criado um boxplot horizontal da idade da mãe.

```python
import pandas as pd
import requests
from io import BytesIO
import matplotlib.pyplot as plt

# URL do arquivo CSV
url_csv = "https://diaad.s3.sa-east-1.amazonaws.com/sinasc/SINASC_2019.csv"

# Baixar o arquivo CSV
response = requests.get(url_csv)
csv_data = BytesIO(response.content)

# Carregar os dados usando o pandas
sinasc_data = pd.read_csv(csv_data)

# Boxplot da idade da mãe
plt.figure(figsize=(10, 6))
plt.boxplot(sinasc_data['IDADEMAE'].dropna(), vert=False)  # Remove valores NaN
plt.title('Boxplot da Idade da Mãe')
plt.xlabel('Idade')
plt.show()

Histograma do Peso do Bebê

Aqui, é gerado um histograma do peso do bebê.

# Código para histograma do peso do bebê
import pandas as pd
import requests
from io import BytesIO
import matplotlib.pyplot as plt

# Histograma do peso do bebê
plt.figure(figsize=(10, 6))
plt.hist(sinasc_data['PESO'].dropna(), bins=30, color='lightcoral', edgecolor='black')
plt.title('Histograma do Peso do Bebê')
plt.xlabel('Peso (g)')
plt.ylabel('Frequência')
plt.grid(axis='y', linestyle='--', alpha=0.7)
plt.show()
