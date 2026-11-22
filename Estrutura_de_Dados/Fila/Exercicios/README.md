# 📝 Exercícios — Fila

Exercícios resolvidos usando `collections.deque` como fila.

---

## 1️⃣ Atendimento por ordem de chegada

```python
from collections import deque

fila = deque(["Ana", "Bruno", "Carla"])
while fila:
    cliente = fila.popleft()
    print(f"Atendendo {cliente}")
```

---

## 2️⃣ Fila de impressão

Cada documento tem um número de páginas. Imprima na ordem de chegada e mostre o total.

```python
from collections import deque

impressao = deque([("relatorio.pdf", 5), ("foto.png", 1), ("contrato.docx", 3)])
total = 0
while impressao:
    nome, paginas = impressao.popleft()
    total += paginas
    print(f"Imprimindo {nome} ({paginas} pág.)")
print(f"Total impresso: {total} páginas")  # 9
```

---

## 3️⃣ Inverter uma fila usando uma pilha

```python
from collections import deque

def inverter_fila(fila):
    pilha = []
    while fila:
        pilha.append(fila.popleft())
    while pilha:
        fila.append(pilha.pop())
    return fila

print(inverter_fila(deque([1, 2, 3, 4])))  # deque([4, 3, 2, 1])
```

---

## 4️⃣ Batata quente (problema de Josefo)

Os jogadores passam a batata `k` vezes; quem está com ela sai. O último vence.

```python
from collections import deque

def batata_quente(nomes, k):
    fila = deque(nomes)
    while len(fila) > 1:
        for _ in range(k):
            fila.append(fila.popleft())
        print(f"{fila.popleft()} saiu")
    return fila[0]

print("Vencedor:", batata_quente(["Ana", "Bruno", "Carla", "Davi", "Eva"], 3))
```

---

## 5️⃣ Desafio — Fila com prioridade

Clientes preferenciais são atendidos antes, mas mantendo a ordem de chegada entre eles.

```python
from collections import deque

preferencial = deque()
normal = deque()

def chegar(nome, prioridade=False):
    (preferencial if prioridade else normal).append(nome)

def atender():
    if preferencial:
        return preferencial.popleft()
    if normal:
        return normal.popleft()
    return None

chegar("Ana")
chegar("Seu José", prioridade=True)
chegar("Bruno")
print(atender())  # Seu José
print(atender())  # Ana
print(atender())  # Bruno
```
