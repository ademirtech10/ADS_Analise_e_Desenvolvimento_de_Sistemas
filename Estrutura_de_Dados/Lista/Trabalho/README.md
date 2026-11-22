# 🎵 Trabalho — Playlist de Músicas

## 📖 Proposta

Desenvolver uma **playlist** usando uma **lista duplamente encadeada**, em que cada música aponta para a **próxima** e para a **anterior**.

```
None ◀─ [Música A] ⇄ [Música B] ⇄ [Música C] ─▶ None
           ▲
         tocando
```

## 📏 Requisitos

1. **Adicionar** música no fim da playlist;
2. **Remover** música pelo nome;
3. **Avançar** para a próxima e **voltar** para a anterior;
4. **Exibir** a playlist marcando a música atual;
5. Mostrar a **quantidade** de músicas.

## 🧱 Relação com Lista

- cada música é um **nó** com `anterior` e `proximo`;
- avançar/voltar é só seguir os **ponteiros**;
- remover do meio é **religar** os vizinhos, sem deslocar elementos.

## 💻 Implementação em Python

```python
class Musica:
    def __init__(self, nome):
        self.nome = nome
        self.anterior = None
        self.proximo = None


class Playlist:
    def __init__(self):
        self.inicio = self.fim = self.atual = None
        self.tamanho = 0

    def adicionar(self, nome):
        nova = Musica(nome)
        if self.inicio is None:
            self.inicio = self.fim = self.atual = nova
        else:
            nova.anterior = self.fim
            self.fim.proximo = nova
            self.fim = nova
        self.tamanho += 1

    def remover(self, nome):
        m = self.inicio
        while m and m.nome != nome:
            m = m.proximo
        if m is None:
            return False
        if m.anterior:
            m.anterior.proximo = m.proximo
        else:
            self.inicio = m.proximo
        if m.proximo:
            m.proximo.anterior = m.anterior
        else:
            self.fim = m.anterior
        if self.atual is m:
            self.atual = m.proximo or m.anterior
        self.tamanho -= 1
        return True

    def proxima(self):
        if self.atual and self.atual.proximo:
            self.atual = self.atual.proximo
        return self.atual.nome if self.atual else None

    def anterior(self):
        if self.atual and self.atual.anterior:
            self.atual = self.atual.anterior
        return self.atual.nome if self.atual else None

    def exibir(self):
        m = self.inicio
        while m:
            marca = "▶" if m is self.atual else " "
            print(f"{marca} {m.nome}")
            m = m.proximo
        print(f"Total: {self.tamanho} músicas")


p = Playlist()
for nome in ["Música A", "Música B", "Música C", "Música D"]:
    p.adicionar(nome)

print(p.proxima())   # Música B
print(p.proxima())   # Música C
print(p.anterior())  # Música B
p.remover("Música C")
p.exibir()
```

### ▶️ Saída final

```
  Música A
▶ Música B
  Música D
Total: 3 músicas
```

## ✅ Checklist de entrega

- [ ] explicar nó, cabeça e ponteiros;
- [ ] usar lista duplamente encadeada;
- [ ] implementar adicionar, remover, avançar e voltar;
- [ ] tratar playlist vazia e remoção da música atual;
- [ ] exibir a playlist marcando a música tocando.
