# Alocação de Memória

## 1. O que é memória?

A memória do computador armazena dados e instruções necessários para a execução dos programas. Durante a execução, um programa pode precisar guardar números, textos, listas, objetos e resultados de operações.

**Alocação de memória** é o processo de reservar espaço na memória para que o programa possa armazenar e utilizar dados.

## 2. Como funciona a alocação?

De forma simplificada, o programa solicita ou utiliza espaço para seus dados, trabalha com essas informações e, quando elas deixam de ser necessárias, a memória pode ser reutilizada.

O modo de alocar e liberar memória depende da linguagem de programação e de seu ambiente de execução.

## 3. Alocação estática e dinâmica

### 3.1 Alocação estática

Em termos gerais, é a alocação cuja reserva e características são definidas antecipadamente, de acordo com as regras da linguagem e do programa. É frequentemente associada a dados de tamanho ou duração definidos previamente.

### 3.2 Alocação dinâmica

Acontece quando a memória é obtida durante a execução do programa, conforme a necessidade. É útil quando a quantidade de dados não é conhecida antecipadamente ou pode variar.

Por exemplo, em Python, uma lista pode crescer quando novos elementos são adicionados:

```python
nomes = []

nomes.append("Ana")
nomes.append("Carlos")
nomes.append("Mariana")

print(nomes)
```

Saída:

```text
['Ana', 'Carlos', 'Mariana']
```

Python gerencia automaticamente a memória necessária para a lista e seus elementos. A lista pode aumentar ou diminuir conforme as operações realizadas.

> **Atenção:** a distinção entre alocação estática e dinâmica depende do contexto. Não significa simplesmente que toda variável comum é estática e toda lista é dinâmica.

## 4. Stack e Heap

Stack (pilha de execução) e Heap são conceitos usados para explicar como a memória é organizada e gerenciada em muitos ambientes de execução.

### 4.1 Stack — pilha de execução

A pilha está relacionada às chamadas de funções e aos contextos necessários durante sua execução.

```python
def calcular():
    resultado = 10 + 5
    return resultado

print(calcular())
```

Ao chamar `calcular()`, o programa precisa manter as informações necessárias para executar a função. Quando ela termina, seu contexto de execução deixa de ser necessário.

### 4.2 Heap

O heap é uma região de memória utilizada para alocar objetos dinamicamente em muitos ambientes de execução.

```python
numeros = [10, 20, 30]
```

A lista é um objeto, e o nome `numeros` permite acessá-la por meio de uma referência. Os detalhes exatos da representação e do gerenciamento dependem da implementação do Python.

> Stack e Heap não são sinônimos de alocação estática e dinâmica. São conceitos relacionados, mas descrevem aspectos diferentes do uso da memória.

## 5. Gerenciamento automático de memória em Python

Python gerencia a memória automaticamente. Na implementação CPython, por exemplo, o gerenciamento inclui contagem de referências e um coletor de lixo que pode identificar determinados ciclos de referências.

Veja o exemplo:

```python
nomes = ["Ana", "Pedro", "João"]

print(nomes)

del nomes
```

A instrução `del nomes` remove o nome `nomes` do ambiente atual. Ela não garante, por si só, que o objeto seja imediatamente apagado da memória física. Se outras referências ainda apontarem para o objeto, ele poderá continuar existindo.

Mesmo quando um objeto pode ser liberado, a memória nem sempre é devolvida imediatamente ao sistema operacional; o gerenciador pode mantê-la disponível para reutilização.

## 6. Problemas relacionados à memória

### Vazamento de memória (memory leak)

Ocorre quando o programa mantém dados na memória mesmo que já não sejam necessários. Em linguagens com gerenciamento automático, isso também pode acontecer quando referências desnecessárias continuam mantendo objetos vivos.

### Falta de memória

Acontece quando o programa não consegue obter memória suficiente para continuar uma operação. Isso pode causar erros ou interromper a execução.

### Recursão excessiva e estouro de pilha

Chamadas recursivas muito profundas podem exceder os limites de recursão ou da pilha, dependendo do ambiente.

Exemplo de recursão sem condição de parada:

```python
def repetir():
    repetir()

repetir()
```

No Python, esse exemplo normalmente resulta em `RecursionError` antes de um estouro físico da pilha.

## 7. Resumo

| Conceito | Significado |
|---|---|
| Alocação de memória | Reserva de espaço para armazenar dados. |
| Alocação estática | Reserva definida antecipadamente, conforme as regras da linguagem. |
| Alocação dinâmica | Reserva realizada durante a execução, conforme a necessidade. |
| Stack | Estrutura relacionada a chamadas de funções e seus contextos de execução. |
| Heap | Área usada para alocar objetos dinamicamente em muitos ambientes. |
| Coletor de lixo | Mecanismo que ajuda a identificar e liberar objetos não mais necessários, inclusive certos ciclos de referências. |
| Memory leak | Memória que permanece ocupada por dados que já não deveriam ser mantidos. |

## 8. Exercícios para praticar

1. Explique com suas palavras o que é alocação de memória.
2. Qual é a diferença geral entre alocação estática e dinâmica?
3. Por que uma lista Python pode crescer quando usamos `append()`?
4. Qual é a diferença entre Stack e Heap?
5. O que a instrução `del nomes` faz no exemplo apresentado?
6. O que é um vazamento de memória?
7. Execute o código abaixo e observe o que é impresso:

```python
valores = [1, 2, 3]
referencia = valores

del valores

print(referencia)
```

**Desafio:** modifique o exemplo para adicionar um novo elemento à lista usando o nome `referencia`. Explique por que ela continua acessível.

## 9. Conclusão

Entender alocação de memória ajuda a compreender como os programas armazenam e utilizam dados. Mesmo que Python cuide de boa parte desse gerenciamento automaticamente, conhecer conceitos como Stack, Heap, referências e coleta de lixo contribui para escrever programas mais eficientes e compreender melhor o funcionamento das linguagens.

---

**Material de estudo:** Fundamentos de Programação  
**Tema:** Alocação de Memória  
**Linguagem utilizada nos exemplos:** Python
