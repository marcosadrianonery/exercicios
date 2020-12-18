Arquitetura de compiladores e interpretadores
=============================================

## [comp-org]: Compreender as etapas tradicionais de análise do código em um compilador

**Q1)** Descreva a função de cada etapa no processo de compilação de um código

1. Análise léxica
2. Análise sintática
3. Análise semântica
4. Otimização
5. Emissão de código 


## [comp-vs-interp]: Compreender as principais diferenças entre um compilador e um interpretador

**Q1)** Descreva as semelhanças e diferenças entre compiladores e interpretadores, em especial no que ambos diferem (ou se assemelham) com relação às etapas mencionadas na questão anterior.

**Q2)** É um erro comum acreditar que "compilada" vs "interpretada" é um uma característica da linguagem de programação. Estas são características de implementações específicas da linguagem. Ainda que a implementação de Python criada por Guido seja interpretada ou que a versão do C que presente no GCC seja compilada, nada impede se crie versões compiladas de Python ou interpretadas de C. Encontre pelo menos um exemplo de implementação de um compilador para uma linguagem normalmente tida como interpretada ou de um interpretador para uma linguagem normalmente tida como compilada. Forneça uma referência como link, artigo, etc que aponte para o projeto escolhido. 


## [parser-fmt]: Compreender a relevância das técnicas de compiladores no processamento de arquivos.

**Q1)** A gramática no [repositório do Lark](https://github.com/lark-parser/lark/blob/master/examples/json_parser.py) fornece uma implementação razoavelmente fiel da especifiação do formato [JSON](http://json.org). Modifique esta gramática para implementar algumas funcionalidades extra no formato JSON:

1. Aceita comentários no estilo C (`// como este!`)
2. Aceita uma vírgula opcional após os elementos de uma lista ou objeto: `[1, {"n": 42,}, 3,]`. A vírgula não pode aparecer em objetos e listas vazios.
3. As aspas em strings são opcionais para nomes contendo apenas letras ou underscore.
4. Também aceita as constantes `Infinity`, `-Infinity` e `NaN` para representar respectivamente `float("inf")`, `-float("inf")` e `float("nan")`. 
