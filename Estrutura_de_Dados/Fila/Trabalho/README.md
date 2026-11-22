# 🏦 Trabalho — Simulador de Atendimento Bancário

## 📖 Proposta

Desenvolver um programa que simule as **senhas de atendimento** de um banco usando **filas**.

## 📏 Requisitos

1. Gerar senhas **normais** (`N001`, `N002`…) e **preferenciais** (`P001`, `P002`…);
2. Cada tipo de senha fica em uma **fila** própria;
3. A cada **2 preferenciais** chamadas, chamar **1 normal** (se houver);
4. Mostrar a **senha chamada** e quantas pessoas ainda aguardam;
5. Ao final, mostrar o **total atendido** de cada tipo.

## 🧱 Relação com Fila

- emitir senha → `enqueue()` no **fim** da fila;
- chamar senha → `dequeue()` no **início** da fila;
- ver próxima senha → `front()`.

## 💻 Implementação em Python

```python
from collections import deque

class Atendimento:
    def __init__(self):
        self.normal = deque()
        self.preferencial = deque()
        self.cont_n = self.cont_p = 0
        self.seguidas_p = 0
        self.atendidos = {"N": 0, "P": 0}

    def emitir(self, preferencial=False):
        if preferencial:
            self.cont_p += 1
            senha = f"P{self.cont_p:03d}"
            self.preferencial.append(senha)
        else:
            self.cont_n += 1
            senha = f"N{self.cont_n:03d}"
            self.normal.append(senha)
        print(f"Senha emitida: {senha}")

    def chamar(self):
        usar_pref = self.preferencial and (self.seguidas_p < 2 or not self.normal)
        if usar_pref:
            senha = self.preferencial.popleft()
            self.seguidas_p += 1
        elif self.normal:
            senha = self.normal.popleft()
            self.seguidas_p = 0
        else:
            print("Nenhuma senha aguardando.")
            return
        self.atendidos[senha[0]] += 1
        restantes = len(self.normal) + len(self.preferencial)
        print(f"Chamando {senha} | aguardando: {restantes}")


banco = Atendimento()
for _ in range(3):
    banco.emitir()
for _ in range(3):
    banco.emitir(preferencial=True)

for _ in range(7):
    banco.chamar()

print("Atendidos:", banco.atendidos)  # {'N': 3, 'P': 3}
```

### ▶️ Ordem de chamada

```
P001 → P002 → N001 → P003 → N002 → N003
```

## ✅ Checklist de entrega

- [ ] explicar a regra FIFO;
- [ ] usar duas filas (normal e preferencial);
- [ ] aplicar a regra 2 preferenciais : 1 normal;
- [ ] tratar fila vazia;
- [ ] mostrar o relatório final de atendimentos.
