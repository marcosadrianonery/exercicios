Arquitetura de compiladores e interpretadores
=============================================

## [comp-org]: Compreender as etapas tradicionais de análise do código em um compilador

**Q1)** Descreva a função de cada etapa no processo de compilação de um código

1. Análise léxica


* É o processo de analisar entradas de linhas de caracteres, analisar se os mesmo estão adequados e produzir uma sequência de símbolos chamado "símbolos léxicos", ou somente "símbolos"(tokens), estes podem ser manipulados mais facilmente por um parser.


2. Análise sintática

* A análise sintática (parsing) é o processo onde o compilador, é a segunda fase da compilação onde se analisa uma sequência que foi dada entrada para verificar sua estrutura gramatical segundo uma determinada gramática formal. Aprova ou não as entradas. 


3. Análise semântica

* A análise semântica é o processo onde o compilador verifica os erros semânticos nas entradas e são coletadas as informações necessárias para a próxima fase da compilação.

4. Otimização

* É a ultima etapa na geração de código pelo compilador. Apos os processos anteriores diversas situações contendo sequências de código ineficiente podem ocorrer. O objeto da etapa de otimização de código é aplicar um conjunto de heurísticas para detectar tais seqüências e substituí-las por outras que removam as situações de ineficiência.

5. Emissão de código 

* A tradução do código de alto nível para o código do processador está associada à traduzir para a linguagem-alvo a representação da árvore gramatical obtida para as diversas expressões do programa. Embora tal atividade possa ser realizada para a árvore completa após a conclusão da análise sintática, em geral ela é efetivada através das ações semânticas associadas à aplicação das regras de reconhecimento do analisador sintático.

## [comp-vs-interp]: Compreender as principais diferenças entre um compilador e um interpretador

**Q1)** Descreva as semelhanças e diferenças entre compiladores e interpretadores, em especial no que ambos diferem (ou se assemelham) com relação às etapas mencionadas na questão anterior.

* Compilador é um programa onde seu objetivo principal é o de traduzir todas as suas linhas de código para outra linguagem.
* Interpretador é um programa, mas, ao contrário do compilador, ele não converte o código todo para linguagem de máquina de uma vez. Ele executa diretamente cada instrução, passo a passo.

* Ambos são programas.
* Ambos convertem um codigo de uma linguagem para outra.
* Enquanto o compilador traduz todas as linhas do codigo de uma unica vez, o interpretador converte cada instrução por vez.
* Os compiladores costumam ter uma maior velocidade de execução, o maior trabalho é no começo onde todo o código é convertido de uma vez. Não precisar fazer a conversão toda vez que o sistema é executado dá uma eficiência muito maior do que um interpretador. O interpretador faz uma nova conversão a cada execução.
- Enquanto o codigo convertido pelo compilador apenas executa, o interpretador executa e converte.

**Q2)** É um erro comum acreditar que "compilada" vs "interpretada" é um uma característica da linguagem de programação. Estas são características de implementações específicas da linguagem. Ainda que a implementação de Python criada por Guido seja interpretada ou que a versão do C que presente no GCC seja compilada, nada impede se crie versões compiladas de Python ou interpretadas de C. Encontre pelo menos um exemplo de implementação de um compilador para uma linguagem normalmente tida como interpretada ou de um interpretador para uma linguagem normalmente tida como compilada. Forneça uma referência como link, artigo, etc que aponte para o projeto escolhido. 


* Linguagem python normalmente interpretada, um compilador pode ser encontrado no endereço: http://py2exe.org/ o desenvolvimento está hospedado em: https://github.com/py2exe/py2exe

* Linguagem 'C' normalmente compilada, um interpretador pode ser encontrado no endereço(mais informações): https://www.softintegration.com/ o download pode ser feito em: https://download.cnet.com/Ch-Professional-64-bit/3000-2247_4-75833264.html



## [parser-fmt]: Compreender a relevância das técnicas de compiladores no processamento de arquivos.

**Q1)** A gramática no [repositório do Lark](https://github.com/lark-parser/lark/blob/master/examples/json_parser.py) fornece uma implementação razoavelmente fiel da especifiação do formato [JSON](http://json.org). Modifique esta gramática para implementar algumas funcionalidades extra no formato JSON:

1. Aceita comentários no estilo C (`// como este!`)
2. Aceita uma vírgula opcional após os elementos de uma lista ou objeto: `[1, {"n": 42,}, 3,]`. A vírgula não pode aparecer em objetos e listas vazios.
3. As aspas em strings são opcionais para nomes contendo apenas letras ou underscore.
4. Também aceita as constantes `Infinity`, `-Infinity` e `NaN` para representar respectivamente `float("inf")`, `-float("inf")` e `float("nan")`. 
