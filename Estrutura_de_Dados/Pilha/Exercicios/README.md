# 📝 Exercícios — Pilha

Exercícios resolvidos usando a classe `Pilha` do [README da Pilha](../README.md).

---

## 1️⃣ Inverter uma palavra

Empilhe cada letra e depois desempilhe tudo.

```python
def inverter(texto):
    pilha = []
    for letra in texto:
        pilha.append(letra)
    resultado = ""
    while pilha:
        resultado += pilha.pop()
    return resultado

print(inverter("ESTRUTURA"))  # ARUTURTSE
```

---

## 2️⃣ Parênteses balanceados

Verifique se `()`, `[]` e `{}` abrem e fecham na ordem correta.

```python
def balanceado(expressao):
    pares = {")": "(", "]": "[", "}": "{"}
    pilha = []
    for c in expressao:
        if c in "([{":
            pilha.append(c)
        elif c in ")]}":
            if not pilha or pilha.pop() != pares[c]:
                return False
    return len(pilha) == 0

print(balanceado("{[(1 + 2) * 3]}"))  # True
print(balanceado("([)]"))             # False
```

---

## 3️⃣ Decimal para binário

Empilhe os restos da divisão por 2 e desempilhe para formar o número.

```python
def decimal_para_binario(n):
    if n == 0:
        return "0"
    pilha = []
    while n > 0:
        pilha.append(n % 2)
        n //= 2
    binario = ""
    while pilha:
        binario += str(pilha.pop())
    return binario

print(decimal_para_binario(13))  # 1101
```

---

## 4️⃣ Palíndromo

Uma palavra é palíndromo quando é igual à sua versão invertida.

```python
def palindromo(texto):
    texto = texto.lower().replace(" ", "")
    return texto == inverter(texto)

print(palindromo("Arara"))  # True
```

---

## 5️⃣ Desafio — Desfazer (Ctrl+Z)

Simule um editor que guarda cada ação em uma pilha e permite desfazer a última.

```python
historico = []

def digitar(texto, acao):
    historico.append(texto)
    return texto + acao

def desfazer(texto):
    return historico.pop() if historico else texto

t = ""
t = digitar(t, "Olá")
t = digitar(t, " mundo")
print(t)            # Olá mundo
t = desfazer(t)
print(t)            # Olá
```
