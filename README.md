# Coleta de dados
É necessário um conjunto de dados de treinamento que contenha pares de frases em inglês e suas traduções correspondentes em português. Quanto maior e mais diversificado for o conjunto de dados, melhor será o desempenho do seu modelo.

Para isso, estaremos utilizando o modelo VanessaSchenkel/translation-en-pt. Acesso em: (https://huggingface.co/datasets/VanessaSchenkel/translation-en-pt) que possui 260482 frases em inglês com suas respectivas traduções para o português.

**Todo o processo será realizado em um notebook dentro do kaggle por conta de sua praticidade e a possibilidade de estarmos utilizando sua GPU**

Link do Código: (Ainda não finalizado)

````python
from datasets import load_dataset

remote_dataset = load_dataset("VanessaSchenkel/translation-en-pt", field="data")

remote_dataset
````
Carregando o dataset "VanessaSchenkel/translation-en-pt" dentro do notebook kaggle e fazendo a chamada da variável "remote_dataset" temos a seguinte saída:

![image](https://github.com/HedvaldoCosta/TranslatorEN-PT/assets/67663958/fcd72931-c1fc-42e9-a410-dd5994430b67)

````python
remote_dataset["train"]["translation"]
````
Entrando no conjunto de dados e chamando a coluna "translation" podemos verificar os pares de frases EN-PT:

![image](https://github.com/HedvaldoCosta/TranslatorEN-PT/assets/67663958/35256b73-ac3c-4da4-9011-3bba499a7ba2)



# Data collect
A training dataset containing pairs of English sentences and their corresponding Portuguese translations is required. The larger and more diverse the dataset, the better your model will perform.
