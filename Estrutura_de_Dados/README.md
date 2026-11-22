# 🧱 Estrutura de Dados

Disciplina que estuda **como organizar e armazenar dados na memória** para que possam ser usados de forma eficiente.

## 🗂️ Conteúdos

| Estrutura | Regra | Ideia principal | Link |
|---|---|---|---|
| 📚 Pilha | LIFO | o último a entrar é o primeiro a sair | [Acessar](Pilha/) |
| 🚶 Fila | FIFO | o primeiro a entrar é o primeiro a sair | [Acessar](Fila/) |
| 🔗 Lista | — | elementos encadeados, inserção e remoção em qualquer posição | [Acessar](Lista/) |

## 🧭 Organização

```
Estrutura_de_Dados/
│
├── Pilha/
│   ├── README.md
│   ├── Exercicios/
│   └── Trabalho/
│       └── Torre_de_Hanoi.md
│
├── Fila/
│   ├── README.md
│   ├── Exercicios/
│   └── Trabalho/
│
└── Lista/
    ├── README.md
    ├── Exercicios/
    └── Trabalho/
```

## 👨‍🏫 Sequência de estudo

```
NÍVEL 1 → Pilha   (LIFO: push, pop, peek)
   ↓
NÍVEL 2 → Fila    (FIFO: enqueue, dequeue)
   ↓
NÍVEL 3 → Lista   (nós, ponteiros, inserção e remoção)
```

## ⏱️ Complexidade das operações principais

| Operação | Pilha | Fila | Lista encadeada |
|---|---|---|---|
| Inserir | O(1) no topo | O(1) no fim | O(1) no início / O(n) no meio |
| Remover | O(1) no topo | O(1) no início | O(1) no início / O(n) no meio |
| Buscar | O(n) | O(n) | O(n) |

## 🛠️ Tecnologia

Os exemplos são escritos em **Python 3**.
