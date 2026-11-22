# 🔗 Lista Encadeada (Linked List)

A **lista encadeada** é formada por **nós**. Cada nó guarda um **valor** e uma **referência** (ponteiro) para o próximo nó. O último nó aponta para `None`.

Diferente do vetor, os elementos **não precisam estar lado a lado na memória**, e é possível inserir e remover em **qualquer posição** sem deslocar os demais.

```
 cabeça
   │
   ▼
┌────┬───┐    ┌────┬───┐    ┌────┬───┐
│ 10 │ ●─┼───▶│ 20 │ ●─┼───▶│ 30 │ ●─┼───▶ None
└────┴───┘    └────┴───┘    └────┴───┘
 valor próx.
```

## ⚙️ Operações

| Operação | Descrição | Complexidade |
|---|---|---|
| `inserir_inicio(x)` | insere `x` antes da cabeça | O(1) |
| `inserir_fim(x)` | insere `x` após o último nó | O(n) |
| `remover(x)` | remove o primeiro nó com valor `x` | O(n) |
| `buscar(x)` | verifica se `x` está na lista | O(n) |
| `exibir()` | mostra todos os elementos | O(n) |

## 💻 Implementação em Python

```python
class No:
    def __init__(self, valor):
        self.valor = valor
        self.proximo = None


class ListaEncadeada:
    def __init__(self):
        self.cabeca = None
        self.tamanho = 0

    def inserir_inicio(self, valor):
        novo = No(valor)
        novo.proximo = self.cabeca
        self.cabeca = novo
        self.tamanho += 1

    def inserir_fim(self, valor):
        novo = No(valor)
        if self.cabeca is None:
            self.cabeca = novo
        else:
            atual = self.cabeca
            while atual.proximo:
                atual = atual.proximo
            atual.proximo = novo
        self.tamanho += 1

    def remover(self, valor):
        anterior, atual = None, self.cabeca
        while atual:
            if atual.valor == valor:
                if anterior:
                    anterior.proximo = atual.proximo
                else:
                    self.cabeca = atual.proximo
                self.tamanho -= 1
                return True
            anterior, atual = atual, atual.proximo
        return False

    def buscar(self, valor):
        atual = self.cabeca
        while atual:
            if atual.valor == valor:
                return True
            atual = atual.proximo
        return False

    def exibir(self):
        valores, atual = [], self.cabeca
        while atual:
            valores.append(str(atual.valor))
            atual = atual.proximo
        print(" -> ".join(valores) + " -> None")


lista = ListaEncadeada()
lista.inserir_fim(20)
lista.inserir_fim(30)
lista.inserir_inicio(10)
lista.exibir()          # 10 -> 20 -> 30 -> None
lista.remover(20)
lista.exibir()          # 10 -> 30 -> None
print(lista.buscar(30)) # True
```

## 🔄 Variações

| Tipo | Característica |
|---|---|
| Simplesmente encadeada | cada nó aponta só para o próximo |
| Duplamente encadeada | cada nó aponta para o próximo **e** o anterior |
| Circular | o último nó aponta de volta para a cabeça |

## ⚖️ Vetor × Lista encadeada

| | Vetor (`list`) | Lista encadeada |
|---|---|---|
| Acesso por índice | O(1) | O(n) |
| Inserir no início | O(n) | O(1) |
| Memória | contígua | nós espalhados + ponteiros |

## 🗂️ Conteúdo da pasta

```
Lista/
├── README.md        → teoria e implementação
├── Exercicios/      → exercícios resolvidos
└── Trabalho/        → trabalho prático
```

🔗 [Exercícios](Exercicios/) · 🔗 [Trabalho](Trabalho/)
