## [ll1-conv]: Criação da tabela de transição para o algoritmo LL(1)

## G1
```
1.  S ⟶ a
2.  S ⟶ ( S )
3.  S ⟶ S *
4.  S ⟶ S S
5.  S ⟶ S | S
```
* Em dado momento é impossivel distinguir-se das regras 3, 4 e 5.
Possuir ambiguidade e os conjuntos "First" não são disjuntos.

## G2
```
1.  S ⟶ + S S
2.  S ⟶ * S S
3.  S ⟶ ~ S
4.  S ⟶ n
```


||+|*|~|n|$|
| :---: | :---: | :---: | :---: | :---: | :--- |
|S|1|2|3|4||

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
Possuir ambiguidade e os conjuntos "First" não são disjuntos.
