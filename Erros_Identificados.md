# Erros Identificados

##  Introdução

Durante a análise do projeto, foram identificados três categorias principais de erros que afetavam o funcionamento do sistema. Este documento registra cada tipo de erro encontrado, sua causa e impacto.

---

## 1️ Erros de Sintaxe

Os erros de sintaxe foram os mais fáceis de identificar, porque **impedem a execução do código**. Em alguns momentos aconteceram erros relacionados à escrita incorreta dos comandos em Python.

### 1.1 Falta de dois-pontos (`:`) em estruturas condicionais

**Código com erro:**
```python
if usuario == "admin"
    print("Acesso permitido")
```

**Impacto:** O Python não consegue executar o código e gera um erro de sintaxe na linha.

**Justificativa:** Em Python, o `:` é obrigatório após a condição `if` para indicar o início do bloco de código.

---

### 1.2 Parênteses não fechados

**Código com erro:**
```python
print("Olá, mundo!"
```

**Impacto:** SyntaxError - parênteses desbalanceados impedem a execução.

**Justificativa:** Toda função `print()` ou qualquer função que abra parênteses precisa fechá-los.

---

### 1.3 Problemas de indentação

**Código com erro:**
```python
def saudar():
print("Olá!")  # Indentação faltando
```

**Impacto:** IndentationError - Python exige indentação consistente.

**Justificativa:** Python utiliza indentação para delimitar blocos de código (if, for, while, funções, etc.).

---

### 1.4 Variáveis escritas de forma incorreta

**Código com erro:**
```python
nome = "João"
print(Nome)  # Variável com 'N' maiúsculo
```

**Impacto:** NameError - a variável `Nome` não está definida.

**Justificativa:** Python diferencia maiúsculas de minúsculas (case-sensitive). `nome` e `Nome` são variáveis diferentes.

---

## 2️ Erros de Lógica

Os erros de lógica são mais difíceis de perceber porque **o código executa normalmente, mas apresenta resultados errados**. Esses erros podem causar consequências graves, pois o sistema funcionará sem avisar sobre o problema.

### 2.1 Condições invertidas

**Código com erro:**
```python
idade = 16

if idade >= 18:
    print("Menor de idade")  # Mensagem errada!
else:
    print("Maior de idade")   # Mensagem errada!
```

**Impacto:** Uma pessoa com 25 anos receberá a mensagem "Menor de idade", o que é logicamente incorreto.

**Problema:** As mensagens estão invertidas em relação à condição.

---

### 2.2 Operadores lógicos incorretos

**Código com erro:**
```python
# Verificar se o número está entre 1 e 10
numero = 5
if numero < 1 or numero > 10:  # Deveria ser 'and'
    print("Fora do intervalo")
else:
    print("Dentro do intervalo")
```

**Impacto:** O número 5 será considerado "Fora do intervalo" quando deveria ser "Dentro do intervalo".

**Problema:** Uso incorreto de `or` quando deveria ser `and`.

---

### 2.3 Cálculos errados

**Código com erro:**
```python
preco = 100
desconto = 0.1  # 10%
preco_final = preco - desconto  # Deveria ser multiplicação
print(f"Preço final: R${preco_final}")  # Resultado: R$99.9 (ERRADO!)
```

**Impacto:** O desconto aplicado seria R$0.10 em vez de R$10.00.

**Problema:** Subtração simples em vez de cálculo percentual.

---

### 2.4 Informações exibidas incorretamente

**Código com erro:**
```python
usuario = "João"
idade = 25
print(f"Nome: {idade}, Idade: {usuario}")  # Variáveis trocadas!
```

**Impacto:** Exibe "Nome: 25, Idade: João" em vez de "Nome: João, Idade: 25".

**Problema:** Variáveis foram colocadas em ordem errada no f-string.

---

## 3️ Erros de Execução

Os erros de execução acontecem durante a execução do programa, geralmente quando o usuário insere dados inesperados ou inválidos.

### 3.1 Divisão por zero

**Código com erro:**
```python
numero = int(input("Digite um número: "))
resultado = 10 / numero
print(resultado)
```

**Impacto:** Se o usuário digitar 0, o programa quebra com ZeroDivisionError.

**Cenário problemático:** 
- Entrada: `0`
- Erro: `ZeroDivisionError: division by zero`

---

### 3.2 Entrada de letras no lugar de números

**Código com erro:**
```python
idade = int(input("Digite sua idade: "))
print(f"Você tem {idade} anos")
```

**Impacto:** Se o usuário digitar "abc", o programa quebra com ValueError.

**Cenário problemático:**
- Entrada: `abc`
- Erro: `ValueError: invalid literal for int() with base 10: 'abc'`

---

### 3.3 Variáveis não definidas

**Código com erro:**
```python
print(f"Saldo: R${saldo}")  # Variável 'saldo' não foi definida
```

**Impacto:** O programa quebra com NameError.

**Erro:**
```
NameError: name 'saldo' is not defined
```

---

### 3.4 Falhas na leitura de arquivos

**Código com erro:**
```python
arquivo = open("dados.txt", "r")
conteudo = arquivo.read()
```

**Impacto:** Se o arquivo não existir, o programa quebra com FileNotFoundError.

**Cenário problemático:**
- Erro: `FileNotFoundError: [Errno 2] No such file or directory: 'dados.txt'`

---

### 3.5 Acesso a índices inválidos

**Código com erro:**
```python
lista = [1, 2, 3]
print(lista[10])  # Índice 10 não existe
```

**Impacto:** O programa quebra com IndexError.

**Erro:**
```
IndexError: list index out of range
```

---

##  Resumo dos Erros

| Tipo | Fácil Identificar? | Impacto | Solução |
|------|-------------------|--------|----------|
| **Sintaxe** |  Sim | Impede execução | Corrigir escrita |
| **Lógica** |  Não | Resultados errados | Revisar algoritmo |
| **Execução** |  Não (até testar) | Travamento | Usar try/except |

---

**Conclusão:** Identificar esses erros é fundamental para criar softwares confiáveis e preparados para diferentes cenários.
