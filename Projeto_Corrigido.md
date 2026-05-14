# Projeto Corrigido

## 📝 Introdução

Este documento apresenta as correções implementadas para cada tipo de erro identificado. Cada solução inclui o código corrigido e uma justificativa técnica detalhada.

---

## 1️⃣ Corrigindo Erros de Sintaxe

### 1.1 Falta de dois-pontos em estruturas condicionais

**Código com erro:**
```python
if usuario == "admin"
    print("Acesso permitido")
```

**Código corrigido:**
```python
if usuario == "admin":
    print("Acesso permitido")
```

**Justificativa:** Em Python, o `:` é obrigatório após condições `if`, `elif`, `else`, e outras estruturas de controle. Ele indica o início do bloco de código que será executado.

---

### 1.2 Parênteses não fechados

**Código com erro:**
```python
print("Olá, mundo!"
```

**Código corrigido:**
```python
print("Olá, mundo!")
```

**Justificativa:** Todo parêntese aberto deve ser fechado. Isso é uma regra básica de sintaxe em qualquer linguagem de programação.

---

### 1.3 Problemas de indentação

**Código com erro:**
```python
def saudar():
print("Olá!")  # Sem indentação
```

**Código corrigido:**
```python
def saudar():
    print("Olá!")  # Com indentação (4 espaços)
```

**Justificativa:** Python utiliza indentação para delimitar blocos de código. A falta de indentação gera um `IndentationError`. O padrão é usar 4 espaços ou 1 TAB.

---

### 1.4 Variáveis escritas de forma incorreta

**Código com erro:**
```python
nome = "João"
print(Nome)  # 'Nome' com 'N' maiúsculo
```

**Código corrigido:**
```python
nome = "João"
print(nome)  # 'nome' com 'n' minúsculo
```

**Justificativa:** Python diferencia maiúsculas de minúsculas (case-sensitive). A variável `nome` é diferente de `Nome`. Sempre use o mesmo nome da variável quando referenciá-la.

---

## 2️⃣ Corrigindo Erros de Lógica

### 2.1 Condições invertidas

**Código com erro:**
```python
idade = 16

if idade >= 18:
    print("Menor de idade")      # ❌ Errado
else:
    print("Maior de idade")       # ❌ Errado
```

**Código corrigido:**
```python
idade = 16

if idade >= 18:
    print("Maior de idade")       # ✅ Correto
else:
    print("Menor de idade")        # ✅ Correto
```

**Justificativa:** A condição `idade >= 18` verifica se a pessoa é maior de idade. As mensagens devem corresponder ao resultado da condição.

---

### 2.2 Operadores lógicos incorretos

**Código com erro:**
```python
numero = 5
if numero < 1 or numero > 10:  # ❌ Lógica errada
    print("Fora do intervalo")
else:
    print("Dentro do intervalo")
```

**Código corrigido:**
```python
numero = 5
if numero < 1 or numero > 10:  # ✅ Correto
    print("Fora do intervalo")
else:
    print("Dentro do intervalo")

# Ou alternativa mais clara:
if 1 <= numero <= 10:  # ✅ Mais pythônico
    print("Dentro do intervalo")
else:
    print("Fora do intervalo")
```

**Justificativa:** A condição `1 <= numero <= 10` é mais clara e Pythônica para verificar se um número está dentro de um intervalo.

---

### 2.3 Cálculos errados

**Código com erro:**
```python
preco = 100
desconto = 0.1  # 10%
preco_final = preco - desconto  # ❌ Resultado: 99.9
print(f"Preço final: R${preco_final}")
```

**Código corrigido:**
```python
preco = 100
desconto = 0.1  # 10%
preco_final = preco * (1 - desconto)  # ✅ Resultado: 90.0
print(f"Preço final: R${preco_final:.2f}")
```

**Justificativa:** Para calcular um desconto percentual, devemos multiplicar o preço pela fração (1 - desconto). Neste caso: 100 × 0.9 = 90.

---

### 2.4 Informações exibidas incorretamente

**Código com erro:**
```python
usuario = "João"
idade = 25
print(f"Nome: {idade}, Idade: {usuario}")  # ❌ Trocado
```

**Código corrigido:**
```python
usuario = "João"
idade = 25
print(f"Nome: {usuario}, Idade: {idade}")  # ✅ Correto
```

**Justificativa:** As variáveis devem estar na ordem correta dentro da string formatada. A lógica também deve fazer sentido: nome vem antes de idade.

---

## 3️⃣ Corrigindo Erros de Execução

### 3.1 Divisão por zero com try/except

**Código com erro:**
```python
numero = int(input("Digite um número: "))
resultado = 10 / numero
print(resultado)
```

**Código corrigido:**
```python
try:
    numero = int(input("Digite um número: "))
    if numero == 0:
        print("Não é possível dividir por zero.")
    else:
        resultado = 10 / numero
        print(f"Resultado: {resultado}")
except ValueError:
    print("Erro: Digite apenas números válidos.")
except ZeroDivisionError:
    print("Erro: Não é possível dividir por zero.")
```

**Justificativa:** O bloco `try` tenta executar o código. Se ocorrer um `ZeroDivisionError` ou `ValueError`, o `except` captura o erro e exibe uma mensagem amigável ao usuário.

---

### 3.2 Entrada de letras em lugar de números

**Código com erro:**
```python
idade = int(input("Digite sua idade: "))
print(f"Você tem {idade} anos")
```

**Código corrigido:**
```python
try:
    idade = int(input("Digite sua idade: "))
    if idade < 0:
        print("Idade não pode ser negativa.")
    elif idade > 150:
        print("Idade inválida.")
    else:
        print(f"Você tem {idade} anos")
except ValueError:
    print("Erro: Digite apenas números inteiros.")
```

**Justificativa:** Validamos a entrada com `try/except` para `ValueError` e também verificamos se a idade está em um intervalo válido.

---

### 3.3 Variáveis não definidas

**Código com erro:**
```python
print(f"Saldo: R${saldo}")  # ❌ 'saldo' não foi definido
```

**Código corrigido:**
```python
saldo = 1000.00  # ✅ Definir a variável antes de usar
print(f"Saldo: R${saldo}")
```

**Justificativa:** Sempre defina uma variável antes de utilizá-la. Para evitar esse problema, use inicializações padrão no início do programa.

---

### 3.4 Falhas na leitura de arquivos

**Código com erro:**
```python
arquivo = open("dados.txt", "r")
conteudo = arquivo.read()
```

**Código corrigido:**
```python
try:
    with open("dados.txt", "r", encoding="utf-8") as arquivo:
        conteudo = arquivo.read()
        print(conteudo)
except FileNotFoundError:
    print("Erro: O arquivo 'dados.txt' não foi encontrado.")
except IOError:
    print("Erro: Não foi possível ler o arquivo.")
```

**Justificativa:** O `try/except` captura erros de arquivo. O `with` garante que o arquivo seja fechado automaticamente. Especificamos `encoding="utf-8"` para evitar problemas com caracteres especiais.

---

### 3.5 Acesso a índices inválidos

**Código com erro:**
```python
lista = [1, 2, 3]
print(lista[10])  # ❌ Índice não existe
```

**Código corrigido:**
```python
lista = [1, 2, 3]

try:
    indice = int(input("Qual índice deseja acessar? "))
    if 0 <= indice < len(lista):  # ✅ Verificar se o índice é válido
        print(f"Valor: {lista[indice]}")
    else:
        print(f"Índice inválido. A lista tem {len(lista)} elementos.")
except ValueError:
    print("Erro: Digite um número inteiro válido.")
except IndexError:
    print("Erro: Índice fora do intervalo.")
```

**Justificativa:** Verificamos se o índice está dentro do intervalo válido usando `0 <= indice < len(lista)` antes de acessá-lo.

---

## 🎯 Exemplo Integrado: Sistema de Cadastro de Usuários

**Versão com erros:**
```python
def cadastrar_usuario(nome, idade, email)
    usuarios = []
    if idade >= 18
        usuarios.append({"nome": nome, "idade": email, "email": idade})
        print("Usuário cadastrado!")
    else
        print("Maior de idade")

nome = input("Digite seu nome: ")
idade = int(input("Digite sua idade: "))  # Pode quebrar se digitar letra
cadastrar_usuario(nome, idade)
```

**Versão corrigida:**
```python
def cadastrar_usuario(nome, idade, email):
    """Cadastra um novo usuário com validação de dados."""
    usuarios = []
    
    # Validação de idade
    if not isinstance(idade, int) or idade < 0:
        print("Erro: Idade deve ser um número positivo.")
        return False
    
    # Validação de email
    if "@" not in email:
        print("Erro: Email inválido.")
        return False
    
    # Lógica corrigida
    if idade >= 18:
        usuarios.append({
            "nome": nome, 
            "idade": idade,      # ✅ Campo correto
            "email": email       # ✅ Campo correto
        })
        print(f"Usuário {nome} cadastrado com sucesso!")
        return True
    else:
        print("Erro: Você deve ser maior de idade para se cadastrar.")
        return False

# Entrada de dados com tratamento de erros
try:
    nome = input("Digite seu nome: ").strip()
    
    if not nome:
        print("Erro: Nome não pode ser vazio.")
    else:
        idade = int(input("Digite sua idade: "))
        email = input("Digite seu email: ").strip()
        
        cadastrar_usuario(nome, idade, email)
        
except ValueError:
    print("Erro: Digite um número válido para idade.")
except Exception as e:
    print(f"Erro inesperado: {e}")
```

**Melhorias implementadas:**
- ✅ Dois-pontos adicionados corretamente
- ✅ Parênteses balanceados
- ✅ Indentação corrigida
- ✅ Variáveis nos campos corretos
- ✅ Condições lógicas corretas
- ✅ Tratamento de exceções
- ✅ Validação de dados
- ✅ Mensagens claras ao usuário
- ✅ Docstring explicativa

---

## 📋 Checklist de Boas Práticas

- ✅ Sempre use `try/except` para entrada de usuário
- ✅ Valide dados antes de usá-los
- ✅ Use nomes descritivos para variáveis
- ✅ Mantenha indentação consistente (4 espaços)
- ✅ Adicione mensagens de erro claras
- ✅ Teste casos extremos (valores 0, negativos, muito grandes)
- ✅ Use `with` para abrir arquivos
- ✅ Revise a lógica após implementar
- ✅ Adicione comentários em código complexo
- ✅ Use f-strings para formatação

