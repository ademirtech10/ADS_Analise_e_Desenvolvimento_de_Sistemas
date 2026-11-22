# 📚 Pilha (Stack)

A **pilha** é uma estrutura de dados que segue a regra **LIFO** (*Last In, First Out*): o **último** elemento a entrar é o **primeiro** a sair.

Pense em uma pilha de pratos: você coloca e retira pratos sempre **pelo topo**.

```
      ┌─────┐  ← topo (último a entrar, primeiro a sair)
      │  30 │
      ├─────┤
      │  20 │
      ├─────┤
      │  10 │
      └─────┘  ← base
```

## ⚙️ Operações

| Operação | Descrição | Complexidade |
|---|---|---|
| `push(x)` | empilha `x` no topo | O(1) |
| `pop()` | desempilha e retorna o topo | O(1) |
| `peek()` | consulta o topo sem remover | O(1) |
| `is_empty()` | verifica se a pilha está vazia | O(1) |
| `size()` | retorna a quantidade de elementos | O(1) |

## 💻 Implementação em Python

```python
class Pilha:
    def __init__(self):
        self.itens = []

    def push(self, item):
        self.itens.append(item)

    def pop(self):
        if self.is_empty():
            raise IndexError("Pilha vazia")
        return self.itens.pop()

    def peek(self):
        if self.is_empty():
            raise IndexError("Pilha vazia")
        return self.itens[-1]

    def is_empty(self):
        return len(self.itens) == 0

    def size(self):
        return len(self.itens)


p = Pilha()
p.push(10)
p.push(20)
p.push(30)
print(p.pop())   # 30
print(p.peek())  # 20
print(p.size())  # 2
```

## 🌍 Onde a pilha é usada

- botão **Desfazer** (Ctrl+Z) de editores;
- botão **Voltar** do navegador;
- **pilha de chamadas** de funções e recursão;
- verificação de **parênteses balanceados**;
- avaliação de **expressões** (notação pós-fixa);
- algoritmo da **Torre de Hanói**.

## 🗂️ Conteúdo da pasta

```
Pilha/
├── README.md        → teoria e implementação
├── Exercicios/      → exercícios resolvidos
└── Trabalho/
    └── Torre_de_Hanoi.md
```

🔗 [Exercícios](Exercicios/) · 🔗 [Trabalho — Torre de Hanói](Trabalho/Torre_de_Hanoi.md)
