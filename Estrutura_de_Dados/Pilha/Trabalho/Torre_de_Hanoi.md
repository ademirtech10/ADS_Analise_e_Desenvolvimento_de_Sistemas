# 🗼 Trabalho — Torre de Hanói

## 📖 O problema

A **Torre de Hanói** tem **3 pinos** (A, B e C) e **n discos** de tamanhos diferentes, todos começando empilhados no pino **A**, do maior (embaixo) para o menor (em cima).

**Objetivo:** mover todos os discos para o pino **C**.

### 📏 Regras

1. Só pode mover **um disco por vez**;
2. Só pode mover o disco que está no **topo** de um pino;
3. Um disco **maior nunca** pode ficar sobre um disco **menor**.

```
     A           B           C
     |           |           |
    -|-          |           |
   --|--         |           |
  ---|---        |           |
 ====================================
```

## 🧱 Relação com Pilha

Cada pino funciona exatamente como uma **pilha**:

- só se mexe no **topo** → `peek()`;
- tirar um disco → `pop()`;
- colocar um disco → `push()`.

## 🧠 Ideia da solução (recursiva)

Para mover `n` discos de **A** para **C** usando **B** como auxiliar:

1. mover `n-1` discos de **A** para **B**;
2. mover o maior disco de **A** para **C**;
3. mover `n-1` discos de **B** para **C**.

O número mínimo de movimentos é **2ⁿ − 1**.

| Discos (n) | Movimentos |
|---|---|
| 1 | 1 |
| 2 | 3 |
| 3 | 7 |
| 4 | 15 |
| 5 | 31 |

## 💻 Implementação em Python usando pilhas

```python
class Pilha:
    def __init__(self, nome):
        self.nome = nome
        self.itens = []

    def push(self, disco):
        if self.itens and self.itens[-1] < disco:
            raise ValueError("Disco maior não pode ficar sobre um menor")
        self.itens.append(disco)

    def pop(self):
        return self.itens.pop()


def mover(origem, destino):
    disco = origem.pop()
    destino.push(disco)
    print(f"Mover disco {disco} de {origem.nome} para {destino.nome}")


def hanoi(n, origem, auxiliar, destino):
    if n == 0:
        return 0
    movimentos = hanoi(n - 1, origem, destino, auxiliar)
    mover(origem, destino)
    movimentos += 1
    movimentos += hanoi(n - 1, auxiliar, origem, destino)
    return movimentos


n = 3
A, B, C = Pilha("A"), Pilha("B"), Pilha("C")
for disco in range(n, 0, -1):
    A.push(disco)

total = hanoi(n, A, B, C)
print(f"Total de movimentos: {total}")  # 7
print("Pino C:", C.itens)               # [3, 2, 1]
```

### ▶️ Saída para 3 discos

```
Mover disco 1 de A para C
Mover disco 2 de A para B
Mover disco 1 de C para B
Mover disco 3 de A para C
Mover disco 1 de B para A
Mover disco 2 de B para C
Mover disco 1 de A para C
Total de movimentos: 7
Pino C: [3, 2, 1]
```

## ✅ Checklist de entrega

- [ ] explicar o problema e as regras;
- [ ] mostrar a relação entre pinos e pilhas;
- [ ] implementar com `push` e `pop`;
- [ ] impedir disco maior sobre disco menor;
- [ ] mostrar os movimentos e o total (2ⁿ − 1);
- [ ] testar com 3, 4 e 5 discos.
