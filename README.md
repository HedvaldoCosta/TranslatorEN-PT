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

````python
remote_dataset["train"]['translation'][0]['english']
````
![image](https://github.com/HedvaldoCosta/TranslatorEN-PT/assets/67663958/8cc00aec-7295-44e4-ad5b-ffc0caae8484)

````python
remote_dataset["train"]['translation'][0]['portuguese']
````
![image](https://github.com/HedvaldoCosta/TranslatorEN-PT/assets/67663958/e0e73e14-eade-478e-ab85-f180d0b6c725)

Podemos entrar em cada índice e pegar as frases separadamente. Estaremos utilizando esse recurso para fazer o pré-processamento dos dados.

# Data collect
A training dataset containing pairs of English sentences and their corresponding Portuguese translations is required. The larger and more diverse the dataset, the better your model will perform.

For this, we will be using the model VanessaSchenkel/translation-en-pt. Access at: (https://huggingface.co/datasets/VanessaSchenkel/translation-en-pt) which has 260482 sentences in English with their respective translations into Portuguese.

**The entire process will be carried out on a notebook inside kaggle due to its practicality and the possibility of using its GPU**

Code Link: (Not finalized yet)

````python
from datasets import load_dataset

remote_dataset = load_dataset("VanessaSchenkel/translation-en-pt", field="data")

remote_dataset
````
Loading the "VanessaSchenkel/translation-en-pt" dataset into the kaggle notebook and calling the "remote_dataset" variable, we get the following output:

![image](https://github.com/HedvaldoCosta/TranslatorEN-PT/assets/67663958/fcd72931-c1fc-42e9-a410-dd5994430b67)

````python
remote_dataset["train"]["translation"]
````
Entering the dataset and calling the "translation" column we can verify the EN-PT sentence pairs:

![image](https://github.com/HedvaldoCosta/TranslatorEN-PT/assets/67663958/35256b73-ac3c-4da4-9011-3bba499a7ba2)

````python
remote_dataset["train"]['translation'][0]['english']
````
![image](https://github.com/HedvaldoCosta/TranslatorEN-PT/assets/67663958/8cc00aec-7295-44e4-ad5b-ffc0caae8484)

````python
remote_dataset["train"]['translation'][0]['english']
````
![image](https://github.com/HedvaldoCosta/TranslatorEN-PT/assets/67663958/e0e73e14-eade-478e-ab85-f180d0b6c725)

We can go into each index and get the phrases separately. We will be using this feature to pre-process the data.