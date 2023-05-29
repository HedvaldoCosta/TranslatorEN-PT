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

# Pré-processamento de dados
Limpeza e preparação os dados para o treinamento. Etapa em que faremos o tokenizer dos nossos dados textuais.

````python
phrase_list_bit = [remote_dataset["train"]["translation"][c] for c in range(1, 10)]
````
````python
phrase_list_bit
````

![image](https://github.com/HedvaldoCosta/TranslatorEN-PT/assets/67663958/12bebad8-fff0-44b9-8fdd-dc049ef4ef68)

O código acima pega apenas 10 pares de frases do conjunto de dados para diminuir o tempo de pré-processamento.

---
````python
!pip install nltk -q
````

Para fazer a tokenização das frases, estaremos utilizando a biblioteca [NLTK](https://www.nltk.org).

````python
import nltk
from nltk.tokenize import word_tokenize
````
O "word_tokenize" é um tokenizador simples que cria tokens das palavras e pontuações das frases.

---
````python
list_tokens = []
for pair in phrase_list_bit:
    tokens_english = word_tokenize(pair["english"])
    tokens_portuguese = word_tokenize(pair["portuguese"])
    list_tokens.append(tokens_english)
    list_tokens.append(tokens_portuguese)
````
Aplicação do "word_tokenize" nas frases da lista "phrase_list_bit".

---
````python
for token in list_tokens:
    print(token)
````
![image](https://github.com/HedvaldoCosta/TranslatorEN-PT/assets/67663958/34a5270b-fcb3-4a72-a4ed-9f0f5c90a88a)



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

# Data pre-processing
Cleaning and preparing data for training. Step in which we will tokenize our textual data.

````python
phrase_list_bit = [remote_dataset["train"]["translation"][c] for c in range(1, 10)]
````
````python
phrase_list_bit
````

![image](https://github.com/HedvaldoCosta/TranslatorEN-PT/assets/67663958/12bebad8-fff0-44b9-8fdd-dc049ef4ef68)

The code above grabs only 10 sentence pairs from the dataset to decrease preprocessing time.

---
````python
!pip install nltk -q
````

To tokenize the sentences, we will be using the [NLTK](https://www.nltk.org) library.

````python
import nltk
from nltk.tokenize import word_tokenize
````
"word_tokenize" is a simple tokenizer that tokenizes words and sentence punctuations.

---
````python
list_tokens = []
for pair in phrase_list_bit:
    tokens_english = word_tokenize(pair["english"])
    tokens_portuguese = word_tokenize(pair["portuguese"])
    list_tokens.append(tokens_english)
    list_tokens.append(tokens_portuguese)
````
Application of "word_tokenize" in the phrases of the "phrase_list_bit" list.

---
````python
for token in list_tokens:
    print(token)
````
![image](https://github.com/HedvaldoCosta/TranslatorEN-PT/assets/67663958/34a5270b-fcb3-4a72-a4ed-9f0f5c90a88a)