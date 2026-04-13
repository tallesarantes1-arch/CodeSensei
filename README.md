# CodeSensei
from transformers import pipeline

# Carregar um modelo de linguagem pré-treinado
explain = pipeline("text-generation", model="gpt2")

def explicar_codigo(codigo: str):
    linhas = codigo.strip().split("\n")
    for i, linha in enumerate(linhas, start=1):
        print(f"Linha {i}: {linha}")
        # Gerar explicação automática
        explicacao = explain(f"Explique o que faz este código em Python: {linha}", max_length=50, num_return_sequences=1)
        print("Explicação:", explicacao[0]['generated_text'])
        print("-" * 50)

# Exemplo de uso
codigo_exemplo = """
for i in range(5):
    print(i)
"""

explicar_codigo(codigo_exemplo)

