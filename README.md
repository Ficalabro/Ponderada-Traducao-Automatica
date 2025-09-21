# 📘 Tradução Automática – Estudo de Caso (D2L, Seção 9.5)

Este repositório contém a implementação da seção **9.5 – Estudo de Caso de Tradução Automática** do livro [*Dive into Deep Learning*](https://pt.d2l.ai/chapter_recurrent-modern/machine-translation-and-dataset.html).  

O notebook [`Pond_tradução_automática.ipynb`](./Pond_tradução_automática.ipynb) realiza:

- **Download e pré-processamento** do conjunto de dados do Projeto Tatoeba (inglês–francês).  
- **Tokenização** e construção dos vocabulários.  
- Implementação e **treinamento de um modelo Seq2Seq com atenção**.  
- **Tradução de frases de exemplo** após o treinamento.  
- **Experimentos variando `num_examples`** para analisar o impacto nos vocabulários.  

---

## ❓ Questões da seção 9.5.7

### 1. Como a variação do argumento `num_examples` em `load_data_nmt` afeta os tamanhos do vocabulário de origem e destino?

Ao variar `num_examples` (500, 1000, 2000, 6000), observou-se que os tamanhos dos vocabulários aumentaram progressivamente.  
Isso acontece porque, com mais exemplos, aparecem mais palavras únicas nas sentenças, ampliando tanto o vocabulário do idioma de origem (inglês) quanto o do idioma de destino (francês).  

📌 **Conclusão:** mais exemplos = vocabulário mais rico e extenso.

---

### 2. Em idiomas como chinês e japonês, onde não há separadores explícitos de palavras, a tokenização em nível de palavra ainda é uma boa ideia?

Não. Em chinês e japonês não existem espaços delimitando palavras, o que torna a tokenização em nível de palavra ambígua e pouco confiável.  

Nesses casos, técnicas mais adequadas são:
- **Tokenização em nível de caractere**, onde cada ideograma é tratado como um token.  
- **Tokenização em nível de subpalavra** (como BPE ou SentencePiece), que equilibra a cobertura do vocabulário e a generalização.  

📚 **Referências**:  
- Seção 9.5 do *Dive into Deep Learning*.  
- Sennrich et al. (2016), *Neural Machine Translation of Rare Words with Subword Units*.  

📌 **Conclusão:** tokenizar por palavra não é uma boa estratégia nesses idiomas. Subpalavra ou caractere são abordagens preferíveis.
