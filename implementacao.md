### Etapas para a implementação de um sistema Fuzzy

1.  Importar pacotes
2.  Declarar as variáveis de Entrada e Saída (Antecedente e Consequente)
3.  Declarar os intervalos das variáveis, suas funções de pertinência
4.  Criação das regras para o sistema



Todo sistema fuzzy possui um Antecedente (uma entrada para o sistema) e um Consequente (a saída do sistema)

Quantos mais variáveis, mais regras serão utilizadas

1. **Importações**

```
import numpy as np
import skfuzzy as fuzz
from skfuzzy import control as ctrl
```



2. **Declaração das variáveis de Antecedente e Consequente**

```
preco = ctrl.Antecedent(np.arange(60000, 100000, 1), 'preço')
consumo = ctrl.Antecedent(np.arange(11, 18, 1), 'consumo')

beneficio = ctrl.Consequent(np.arange(0, 11, 0.5), 'benefício')
```



Agora deve-se criar as faixas dos valores de classificação, os níveis para as variáveis, estas chamadas de funções de pertinência

3. **Definições das funções de pertinência**

```python
preco.automf(number=3, names=['baixo', 'medio', 'alto'])
consumo.automf(number=3, names=['alto', 'medio', 'baixo'])
```

Como o próprio começo de nome da função `automf()` sugere, as funções de pertinência (membership functions) foram feitas no automático

A variável consumo é do tipo decrescente em questão de importância, o número pequeno não é bom, conforme vai aumentando que melhora

quanto maior a quantidade de km que o veiculo faz com um litro de gasolina, mais baixo é o consumo (inversamente proporcional)

> Deve-se sempre checar se a variável está parametrizada corretamente



Para que as funções de pertinência sejam feitas na mão, usa-se por exemplo o `trimf()` (triangular) ou o `trapmf()` (trapezoidal)

```python
beneficio['baixo'] = fuzz.trimf(beneficio.universe, [0, 2.5, 5])
beneficio['medio'] = fuzz.trimf(beneficio.universe, [2.5, 5, 7.5])
beneficio['alto'] = fuzz.trimf(beneficio.universe, [5, 7.5, 10])
```

O `universe` sendo o universo de discurso



4. **Criação das regras para o sistema**

Serve para o gerenciamento de regras para que possa ser retornado um grau de retorno por uma previsão

As regras são mapeadas de acordo com a modelagem do problema
