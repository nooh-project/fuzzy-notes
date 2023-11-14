Todo sistema fuzzy possui um Antecedente (uma entrada para o sistema) e um Consequente (a saída do sistema)

Quantos mais variáveis, mais regras serão utilizadas

```
import numpy as np
import skfuzzy as fuzz
from skfuzzy import control as ctrl
```

^ Importações

```
preco = ctrl.Antecedent(np.arange(60000, 100000, 1), 'preço')
consumo = ctrl.Antecedent(np.arange(11, 18, 1), 'consumo')

beneficio = ctrl.Consequent(np.arange(0, 11, 0.5), 'benefício')
```

^ Declaração das variáveis de Antecedente e Consequente



Agora deve-se criar as faixar dos valores de classificação, os níveis para as variáveis



Checar se a variável está parametrizada corretamente
