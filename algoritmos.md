Algoritmos de analise sintática
===============================

## [ll1-conv]: Criação da tabela de transição para o algoritmo LL(1)

**Q1)** Verifique se as gramáticas abaixo são compatíveis com o LL(1) e monte a tabela de transição para as gramáticas compatíveis. Em caso contrário, aponte o motivo do conflito da gramática com o LL(1). Resolva 1 exemplo de gramática compatível com LL(1) para demonstrar competência.

## G1
```
1.  S ⟶ a
2.  S ⟶ ( S )
3.  S ⟶ S *
4.  S ⟶ S S
5.  S ⟶ S | S
```
* Em dado momento é impossivel distinguir-se das regras 3, 4 e 5.

## G2
```
1.  S ⟶ + S S
2.  S ⟶ * S S
3.  S ⟶ ~ S
4.  S ⟶ n
```


||+|*|~|n|
| :---: | :---: | :---: | :---: | :---: |
|S|1|2|3|4|

* Exemplo

input = + 3 4 

Estado:
[S]
-> Em 'S' o simbolo '+' aponta para a linha 1.
[+ S S]
-> Em 'S' o simbolo '3' aponta para a linha 4.
[+ 4 S]
-> Em 'S' o simbolo '4' aponta para a linha 4.
[+ 4 4]

---> Os passos em que os tokens são dispensados e não são mostrados para uma resolução mais limpa.




## G3
```
1.  S ⟶ S + S
2.  S ⟶ S * S
3.  S ⟶ - S
4.  S ⟶ ( S )
5.  S ⟶ n
```
* Em dado momento é impossivel distinguir-se das regras 1 e 2.


## [rd-prog]: Implementar gramática simples usando descida recursiva

**Q1)** Implemente uma das gramáticas da questão anterior utilizando a técnica de descida recursiva. Você pode utilizar o esqueleto do código da questão abaixo como base para organização do analisador sintático.

**Q2)** Complete o código abaixo que faz a descida recursiva da seguinte gramática:

```python

grammar = """
value : lst | var | pair
lst   : "[" [value ("," value)*] "]"
pair  : "(" value ":" value ")"
var   : /[a-z]+/
"""

import re
lex = re.compile(r"[a-z]+|[[\],():]")


def parse(src):
    """
    Retorna valor a partir da representação como string.
    """
    tokens = [*lex.findall(src), "$"]
    res = value(tokens)
    if tokens != ["$"]:
        raise SyntaxError("espera o fim do arquivo")
    return res


def expect(tk, tokens):
    """
    Remove primeiro elemento da lista de tokens e produz um erro
    de sintaxe se o elemento não for igual a tk.
    """
    tk_ = tokens.pop(0)
    if tk != tk_:
        raise SyntaxError(f"esperava {tk}, obteve {tk_}")


def value(tokens):
    # Implemente a regra que lê uma lista de tokens e retorna um
    # valor da linguagem:
    #
    #   value : lst | var | pair 
    
    if tokens[0] == "[":
        return lst(tokens)
    ...
    raise SyntaxError


def lst(tokens):
    # Processa listas:
    #
    #   lst   : "[" [value ("," value)*] "]" 
    ...


def pair(tokens):
    # Processa pares:
    # 
    #   pair  : "(" value ":" value ")" 
    ...
    

src = "[a,b,(c:d),[ab,cd,ef]]"
assert parse(src) == ["a", "b", ("c", "d"), ["ab", "cd", "ef"]]
```


## [ll1-epsilon]: Tratar caso especial do LL(1) em gramática que possui epsilons

**Q1)** Verifique se as gramáticas abaixo são compatíveis com o LL(1) e monte a tabela de transição para as gramáticas compatíveis. Em caso contrário, aponte o motivo do conflito da gramática com o LL(1). Resolva 1 exemplo de gramática compatível com LL(1) para demonstrar competência.

## G1
```
1.  S ⟶ a S b
2.  S ⟶ ε
```

||a|b|
| :---: | :---: |
|S|1|2|

## G2
```
1.  S ⟶ E S
2.  S ⟶ ε
3.  E ⟶ v
4.  E ⟶ ( L )
5.  L ⟶ E L
6.  L ⟶ ε
```

Possuir ambiguidade e os conjuntos "First" não são disjuntos.


## G3
```
1.  S ⟶ E
2.  S ⟶ ε
3.  E ⟶ v
4.  E ⟶ λ v . E
5.  E ⟶ ( E R )
6.  E ⟶ let v = E in E
7.  R ⟶ E
8.  R ⟶ ε
```

Possuir ambiguidade e os conjuntos "First" não são disjuntos.
