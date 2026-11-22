# 📝 Exercícios — Lista Encadeada

Exercícios resolvidos usando as classes `No` e `ListaEncadeada` do [README da Lista](../README.md).

---

## 1️⃣ Contar elementos percorrendo a lista

```python
def contar(lista):
    total, atual = 0, lista.cabeca
    while atual:
        total += 1
        atual = atual.proximo
    return total
```

---

## 2️⃣ Somar os valores

```python
def somar(lista):
    soma, atual = 0, lista.cabeca
    while atual:
        soma += atual.valor
        atual = atual.proximo
    return soma
```

---

## 3️⃣ Inverter a lista (mudando os ponteiros)

```python
def inverter(lista):
    anterior, atual = None, lista.cabeca
    while atual:
        proximo = atual.proximo
        atual.proximo = anterior
        anterior = atual
        atual = proximo
    lista.cabeca = anterior

# 10 -> 20 -> 30 -> None  vira  30 -> 20 -> 10 -> None
```

---

## 4️⃣ Inserir em posição específica

```python
def inserir_na_posicao(lista, posicao, valor):
    if posicao == 0:
        lista.inserir_inicio(valor)
        return
    atual = lista.cabeca
    for _ in range(posicao - 1):
        if atual is None:
            raise IndexError("Posição inválida")
        atual = atual.proximo
    if atual is None:
        raise IndexError("Posição inválida")
    novo = No(valor)
    novo.proximo = atual.proximo
    atual.proximo = novo
    lista.tamanho += 1
```

---

## 5️⃣ Remover valores duplicados

```python
def remover_duplicados(lista):
    vistos = set()
    anterior, atual = None, lista.cabeca
    while atual:
        if atual.valor in vistos:
            anterior.proximo = atual.proximo
            lista.tamanho -= 1
        else:
            vistos.add(atual.valor)
            anterior = atual
        atual = atual.proximo

# 1 -> 2 -> 2 -> 3 -> 1 -> None  vira  1 -> 2 -> 3 -> None
```

---

## 6️⃣ Desafio — Encontrar o elemento do meio

Use dois ponteiros: um anda de 1 em 1, o outro de 2 em 2.

```python
def meio(lista):
    lento = rapido = lista.cabeca
    while rapido and rapido.proximo:
        lento = lento.proximo
        rapido = rapido.proximo.proximo
    return lento.valor if lento else None
```
