# 🚶 Fila (Queue)

A **fila** é uma estrutura de dados que segue a regra **FIFO** (*First In, First Out*): o **primeiro** elemento a entrar é o **primeiro** a sair.

Pense na fila de um banco: quem chega entra **no fim** e o atendimento acontece **no início**.

```
 saída ←  ┌────┬────┬────┬────┐  ← entrada
          │ 10 │ 20 │ 30 │ 40 │
          └────┴────┴────┴────┘
          início            fim
```

## ⚙️ Operações

| Operação | Descrição | Complexidade |
|---|---|---|
| `enqueue(x)` | insere `x` no fim da fila | O(1) |
| `dequeue()` | remove e retorna o início | O(1) |
| `front()` | consulta o início sem remover | O(1) |
| `is_empty()` | verifica se a fila está vazia | O(1) |
| `size()` | retorna a quantidade de elementos | O(1) |

## 💻 Implementação em Python

Usamos `collections.deque`, que remove do início em O(1) (uma `list` com `pop(0)` seria O(n)).

```python
from collections import deque

class Fila:
    def __init__(self):
        self.itens = deque()

    def enqueue(self, item):
        self.itens.append(item)

    def dequeue(self):
        if self.is_empty():
            raise IndexError("Fila vazia")
        return self.itens.popleft()

    def front(self):
        if self.is_empty():
            raise IndexError("Fila vazia")
        return self.itens[0]

    def is_empty(self):
        return len(self.itens) == 0

    def size(self):
        return len(self.itens)


f = Fila()
f.enqueue("Ana")
f.enqueue("Bruno")
f.enqueue("Carla")
print(f.dequeue())  # Ana
print(f.front())    # Bruno
print(f.size())     # 2
```

## 🔄 Variações

| Tipo | Característica |
|---|---|
| Fila circular | o fim "dá a volta" e reaproveita as posições do vetor |
| Fila de prioridade | sai primeiro quem tem maior prioridade |
| Deque | permite inserir e remover nas duas pontas |

## 🌍 Onde a fila é usada

- fila de **impressão**;
- atendimento em **bancos** e **senhas**;
- **escalonamento de processos** no sistema operacional;
- **mensagens** entre sistemas;
- busca em largura (**BFS**) em grafos.

## 🗂️ Conteúdo da pasta

```
Fila/
├── README.md        → teoria e implementação
├── Exercicios/      → exercícios resolvidos
└── Trabalho/        → trabalho prático
```

🔗 [Exercícios](Exercicios/) · 🔗 [Trabalho](Trabalho/)
