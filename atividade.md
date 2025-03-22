<!--
Uma fábrica produz quatro tipos de peças: P1, P2, P3 e P4. Para tanto,
emprega os seguintes equipamentos: Tornos, Fresas e Furadeiras. Cada
peça a ser produzida passa necessariamente pelos três equipamentos e
ocupam os tempos relacionados na tabela abaixo.
As disponibilidades semanais de cada equipamento e o lucro unitário
obtido com a venda de cada peça também estão indicados na mesma
tabela.
Deseja-se saber quais as quantidades ótimas de cada peça devem ser
produzidas, para fornecerem o máximo lucro possível ao empresário.

| Recursos (equipamentos) | Processamento das Peças (horas) P1 | Processamento das Peças (horas) P2 | Processamento das Peças (horas) P3 | Processamento das Peças (horas) P4 | Disponibilidade Semanal (horas) |
|---|---|---|---|---|---|
| Torno | 1,5 | 1 | 2,5 | 1 | 2000 |
| Frezadora | 1 | 5 | 1 | 3 | 8000 |
| Furad. | 1,5 | 3 | 3,7 | 1,2 | 5000 |
| Lucro Unitário (R$) | 5.20 | 7.10 | 9.30 | 4.50 | |



Função Objetivo
Max Z = 5,20X1 +7,10X2 + 9,30X3 + 4,5X4
Sujeito a:
Torno) 1,5 X1 + X2 + 2,5 X3 + X4 ≤ 2000
Fresa) X1 + 5X2 + x3 + 3X4 ≤ 8000
Furad) 1,5 X1 + 3X2 + 3,7X3 + 1,2X4 ≤ 5000


Resolver pelo algoritmo simplex

Importante -> representar o modelo na forma canônica, ou seja, com todas as variáveis não-negativas e com todas as restrições na forma de desigualdade ≤. Para isso, adicione variáveis de folga para cada uma das restrições.

formato de tabela da resolução:
| Base | rhs | x1 | x2 | x3 | x4 |    |    |    |
|---|---|---|---|---|---|---|---|---|
|    |     |    |    |    |    |    |    |    |
|    |     |    |    |    |    |    |    |    |

 -->

## Resolução do modelo pelo Algoritmo Simplex

**1. Modelo Canônico**
Max Z = 5,20X1 + 7,10X2 + 9,30X3 + 4,50X4  
Sujeito a:  
1,5X1 + X2 + 2,5X3 + X4 + X5 = 2000  
X1 + 5X2 + X3 + 3X4 + X6 = 8000  
1,5X1 + 3X2 + 3,7X3 + 1,2X4 + X7 = 5000  
X1, X2, X3, X4, X5, X6, X7 ≥ 0

**2. Tableau Inicial (simplificado)**
| Base | RHS | X1 | X2 | X3 | X4 | X5 | X6 | X7 | Z |
|------|------|-----|-----|-----|-----|-----|-----|-----|-----|
| X5 | 2000 | 1,5 | 1 | 2,5 | 1 | 1 | 0 | 0 | 0 |
| X6 | 8000 | 1 | 5 | 1 | 3 | 0 | 1 | 0 | 0 |
| X7 | 5000 | 1,5 | 3 | 3,7 | 1,2 | 0 | 0 | 1 | 0 |
| Z | 0 |-5,2 |-7,1 |-9,3|-4,5| 0 | 0 | 0 | 1 |

**Próxima Iteração (Iteração 1)**
Variável de entrada: X3 (coeficiente -9,3 em Z)  
Variável de saída: X5 (mínimo de 2000 ÷ 2,5 = 800)

_Normalização da linha pivô (linha de X5):_

- RHS: 2000 ÷ 2,5 = 800
- X1: 1,5 ÷ 2,5 = 0,6
- X2: 1 ÷ 2,5 = 0,4
- X3: 2,5 ÷ 2,5 = 1
- X4: 1 ÷ 2,5 = 0,4
- X5: 1 ÷ 2,5 = 0,4
- X6 e X7 permanecem 0

_Eliminação de X3 nas demais linhas:_

Linha 2 (base X6):

- Nova linha 2 = linha 2 − 1 × (nova linha 1)
- RHS: 8000 − 800 = 7200
- X1: 1 − 0,6 = 0,4
- X2: 5 − 0,4 = 4,6
- X3: 1 − 1 = 0
- X4: 3 − 0,4 = 2,6
- X5: 0 − 0,4 = -0,4
- (X6, X7 inalterados)

Linha 3 (base X7):

- Nova linha 3 = linha 3 − 3,7 × (nova linha 1)
- RHS: 5000 − 3,7×800 = 2040
- X1: 1,5 − 3,7×0,6 = 1,5 − 2,22 = -0,72
- X2: 3 − 3,7×0,4 = 3 − 1,48 = 1,52
- X3: 3,7 − 3,7 = 0
- X4: 1,2 − 3,7×0,4 = 1,2 − 1,48 = -0,28
- X5: 0 − 3,7×0,4 = -1,48
- (X6 permanece 0 e X7 permanece 1)

Linha Z:

- Nova linha Z = linha Z + 9,3 × (nova linha 1)
- RHS: 0 + 9,3×800 = 7440
- X1: -5,2 + 9,3×0,6 = -5,2 + 5,58 = 0,38
- X2: -7,1 + 9,3×0,4 = -7,1 + 3,72 = -3,38
- X3: -9,3 + 9,3×1 = 0
- X4: -4,5 + 9,3×0,4 = -4,5 + 3,72 = -0,78
- X5: 0 + 9,3×0,4 = 3,72
- (X6 e X7 permanecem 0; constante de Z = 1)

_Tableau atualizado após Iteração 1:_

| Base | RHS  | X1    | X2    | X3  | X4    | X5    | X6  | X7  | Z   |
| ---- | ---- | ----- | ----- | --- | ----- | ----- | --- | --- | --- |
| X3   | 800  | 0,6   | 0,4   | 1   | 0,4   | 0,4   | 0   | 0   | 0   |
| X6   | 7200 | 0,4   | 4,6   | 0   | 2,6   | -0,4  | 1   | 0   | 0   |
| X7   | 2040 | -0,72 | 1,52  | 0   | -0,28 | -1,48 | 0   | 1   | 0   |
| Z    | 7440 | 0,38  | -3,38 | 0   | -0,78 | 3,72  | 0   | 0   | 1   |

**Próxima Iteração (Iteração 2)**
Variável de entrada: X2 (coeficiente -3,38 na linha Z)  
Variável de saída: X7 (mínimo de 2040 ÷ 1,52 ≈ 1342,11)

-- Passo 1: Normalizar a linha pivô (Linha 3 – antiga base X7)  
Dividindo a Linha 3 por 1,52:

- RHS: 2040 ÷ 1,52 ≈ 1342,11
- X1: -0,72 ÷ 1,52 ≈ -0,47
- X2: 1,52 ÷ 1,52 = 1
- X3: 0 ÷ 1,52 = 0
- X4: -0,28 ÷ 1,52 ≈ -0,18
- X5: -1,48 ÷ 1,52 ≈ -0,97
- X6: 0
- X7: 1 ÷ 1,52 ≈ 0,66

-- Passo 2: Eliminar X2 das demais linhas

_Linha 1 (base X3), coeficiente de X2 = 0,4:_  
Nova Linha 1 = Linha 1 − 0,4 × (nova Linha 3):

- RHS: 800 − 0,4×1342,11 ≈ 263,16
- X1: 0,6 − 0,4×(-0,47) ≈ 0,79
- X2: 0,4 − 0,4×1 = 0
- X3: 1
- X4: 0,4 − 0,4×(-0,18) ≈ 0,47
- X5: 0,4 − 0,4×(-0,97) ≈ 0,79
- X6: 0
- X7: 0 − 0,4×0,66 ≈ -0,26

_Linha 2 (base X6), coeficiente de X2 = 4,6:_  
Nova Linha 2 = Linha 2 − 4,6 × (nova Linha 3):

- RHS: 7200 − 4,6×1342,11 ≈ 1026,29
- X1: 0,4 − 4,6×(-0,47) ≈ 2,56
- X2: 4,6 − 4,6×1 = 0
- X3: 0
- X4: 2,6 − 4,6×(-0,18) ≈ 3,43
- X5: -0,4 − 4,6×(-0,97) ≈ 4,06
- X6: 1
- X7: 0 − 4,6×0,66 ≈ -3,04

_Linha Z, coeficiente de X2 = -3,38:_  
Nova Linha Z = Linha Z + 3,38 × (nova Linha 3):

- RHS: 7440 + 3,38×1342,11 ≈ 11975,34
- X1: 0,38 + 3,38×(-0,47) ≈ -1,21
- X2: -7,1 + 3,38×1 = -3,72 → ajustado para 0 na eliminação
- X3: 0
- X4: -0,78 + 3,38×(-0,18) ≈ -1,39
- X5: 3,72 + 3,38×(-0,97) ≈ 0,44
- X6: 0
- X7: 0 + 3,38×0,66 ≈ 2,23

-- Resultado: Novo tableau após Iteração 2

| Base | RHS      | X1    | X2  | X3  | X4    | X5    | X6  | X7    | Z   |
| ---- | -------- | ----- | --- | --- | ----- | ----- | --- | ----- | --- |
| X3   | 263,16   | 0,79  | 0   | 1   | 0,47  | 0,79  | 0   | -0,26 | 0   |
| X6   | 1026,29  | 2,56  | 0   | 0   | 3,43  | 4,06  | 1   | -3,04 | 0   |
| X2   | 1342,11  | -0,47 | 1   | 0   | -0,18 | -0,97 | 0   | 0,66  | 0   |
| Z    | 11975,34 | -1,21 | 0   | 0   | -1,39 | 0,44  | 0   | 2,23  | 1   |

**Próxima Iteração (Iteração 3)**
Variável de entrada: X4 (coeficiente -1,39 na linha Z)  
Variável de saída: X6 (mínimo de 1026,29 ÷ 3,43 ≈ 299)

-- Passo 1: Normalizar a linha pivô (Linha 2, base X6) dividindo por 3,43:
Nova Linha 2 (nova base: X4):
• RHS: 1026,29 ÷ 3,43 ≈ 299,00  
• X1: 2,56 ÷ 3,43 ≈ 0,75  
• X2: 0  
• X3: 0  
• X4: 3,43 ÷ 3,43 = 1  
• X5: 4,06 ÷ 3,43 ≈ 1,18  
• X6: 1 ÷ 3,43 ≈ 0,29  
• X7: -3,04 ÷ 3,43 ≈ -0,89

-- Passo 2: Eliminar a coluna X4 das demais linhas usando a nova Linha 2

_Linha 1 (base X3 a partir dos valores da Iteração 2):_  
Valores originais da Linha 1 (Iteração 2):  
 RHS = 263,16; X1 = 0,79; X2 = 0; X3 = 1; X4 = 0,47; X5 = 0,79; X6 = 0; X7 = -0,26  
Coeficiente em X4 = 0,47  
Nova Linha 1 = Linha 1 - 0,47 × (Nova Linha 2):
• RHS: 263,16 - 0,47×299,00 ≈ 263,16 - 140,53 = 122,63  
• X1: 0,79 - 0,47×0,75 ≈ 0,79 - 0,3525 = 0,44  
• X2: 0 - 0,47×0 = 0  
• X3: 1 - 0,47×0 = 1  
• X4: 0,47 - 0,47×1 = 0  
• X5: 0,79 - 0,47×1,18 ≈ 0,79 - 0,5546 = 0,24  
• X6: 0 - 0,47×0,29 ≈ -0,14  
• X7: -0,26 - 0,47×(-0,89) ≈ -0,26 + 0,4183 = 0,16

_Linha 3 (base X2 da Iteração 2):_  
Valores originais da Linha 3:  
 RHS = 1342,11; X1 = -0,47; X2 = 1; X3 = 0; X4 = -0,18; X5 = -0,97; X6 = 0; X7 = 0,66  
Coeficiente em X4 = -0,18  
Nova Linha 3 = Linha 3 - (-0,18)×(Nova Linha 2) = Linha 3 + 0,18×(Nova Linha 2):
• RHS: 1342,11 + 0,18×299,00 ≈ 1342,11 + 53,82 = 1395,93  
• X1: -0,47 + 0,18×0,75 ≈ -0,47 + 0,135 = -0,335  
• X2: 1 + 0,18×0 = 1  
• X3: 0 + 0,18×0 = 0  
• X4: -0,18 + 0,18×1 = 0  
• X5: -0,97 + 0,18×1,18 ≈ -0,97 + 0,2124 = -0,7576 ≈ -0,76  
• X6: 0 + 0,18×0,29 ≈ 0,0522  
• X7: 0,66 + 0,18×(-0,89) ≈ 0,66 - 0,1602 = 0,50

_Linha Z (da Iteração 2):_  
Valores originais da Linha Z:  
 RHS = 11975,34; X1 = -1,21; X2 = 0; X3 = 0; X4 = -1,39; X5 = 0,44; X6 = 0; X7 = 2,23  
Coeficiente em X4 = -1,39  
Nova Linha Z = Linha Z - (-1,39)×(Nova Linha 2) = Linha Z + 1,39×(Nova Linha 2):
• RHS: 11975,34 + 1,39×299,00 ≈ 11975,34 + 415,61 = 12390,95  
• X1: -1,21 + 1,39×0,75 ≈ -1,21 + 1,0425 = -0,17  
• X2: 0 + 1,39×0 = 0  
• X3: 0 + 1,39×0 = 0  
• X4: -1,39 + 1,39×1 = 0  
• X5: 0,44 + 1,39×1,18 ≈ 0,44 + 1,6402 = 2,08  
• X6: 0 + 1,39×0,29 ≈ 0,40  
• X7: 2,23 + 1,39×(-0,89) ≈ 2,23 - 1,2371 = 0,99

-- Resultado: Novo tableau após Iteração 3

| Base | RHS      | X1     | X2  | X3  | X4  | X5    | X6    | X7    | Z   |
| ---- | -------- | ------ | --- | --- | --- | ----- | ----- | ----- | --- |
| X3   | 122,63   | 0,44   | 0   | 1   | 0   | 0,24  | -0,14 | 0,16  | 0   |
| X4   | 299,00   | 0,75   | 0   | 0   | 1   | 1,18  | 0,29  | -0,89 | 0   |
| X2   | 1395,93  | -0,335 | 1   | 0   | 0   | -0,76 | 0,052 | 0,50  | 0   |
| Z    | 12390,95 | -0,17  | 0   | 0   | 0   | 2,08  | 0,40  | 0,99  | 1   |

**Próxima Iteração (Iteração 4)**
Variável de entrada: X1, pois é o único coeficiente negativo em Z (–0,17).  
Variável de saída: X3 (mínimo de 122,63 ÷ 0,44 ≈ 278,70)

-- Passo 1: Normalizar a linha pivô (Linha 1, base X3) dividindo por 0,44:
Nova Linha 1 (nova base: X1):
• RHS: 122,63 ÷ 0,44 ≈ 278,70  
• X1: 0,44 ÷ 0,44 = 1  
• X2: 0 ÷ 0,44 = 0  
• X3: 1 ÷ 0,44 ≈ 2,27  
• X4: 0 ÷ 0,44 = 0  
• X5: 0,24 ÷ 0,44 ≈ 0,55  
• X6: -0,14 ÷ 0,44 ≈ -0,32  
• X7: 0,16 ÷ 0,44 ≈ 0,36

-- Passo 2: Eliminar a coluna X1 das demais linhas usando a nova Linha 1

_Linha 2 (base X4):_  
Coeficiente em X1 = 0,75  
Nova Linha 2 = Linha 2 - 0,75 × (Nova Linha 1):
• RHS: 299,00 - 0,75×278,70 ≈ 89,98  
• X1: 0,75 - 0,75×1 = 0  
• X2: 0 - 0,75×0 = 0  
• X3: 0 - 0,75×2,27 ≈ -1,70  
• X4: 1 - 0,75×0 = 1  
• X5: 1,18 - 0,75×0,55 ≈ 0,77  
• X6: 0,29 - 0,75×(-0,32) ≈ 0,53  
• X7: -0,89 - 0,75×0,36 ≈ -1,16

_Linha 3 (base X2):_  
Coeficiente em X1 = -0,335  
Nova Linha 3 = Linha 3 - (-0,335)×(Nova Linha 1) = Linha 3 + 0,335×(Nova Linha 1):
• RHS: 1395,93 + 0,335×278,70 ≈ 1489,30  
• X1: -0,335 + 0,335×1 = 0  
• X2: 1 + 0,335×0 = 1  
• X3: 0 + 0,335×2,27 ≈ 0,76  
• X4: 0 + 0,335×0 = 0  
• X5: -0,76 + 0,335×0,55 ≈ -0,58  
• X6: 0,052 + 0,335×(-0,32) ≈ -0,05  
• X7: 0,50 + 0,335×0,36 ≈ 0,62

_Linha Z:_  
Coeficiente em X1 = -0,17  
Nova Linha Z = Linha Z - (-0,17)×(Nova Linha 1) = Linha Z + 0,17×(Nova Linha 1):
• RHS: 12390,95 + 0,17×278,70 ≈ 12438,33  
• X1: -0,17 + 0,17×1 = 0  
• X2: 0 + 0,17×0 = 0  
• X3: 0 + 0,17×2,27 ≈ 0,39  
• X4: 0 + 0,17×0 = 0  
• X5: 2,08 + 0,17×0,55 ≈ 2,17  
• X6: 0,40 + 0,17×(-0,32) ≈ 0,35  
• X7: 0,99 + 0,17×0,36 ≈ 1,05

-- Resultado: Novo tableau após Iteração 4
| Base | RHS | X1 | X2 | X3 | X4 | X5 | X6 | X7 | Z |
| ---- | -------- | ---- | -- | ---- | -- | ---- | ----- | ----- | - |
| X1 | 278,70 | 1 | 0 | 2,27 | 0 | 0,55 | -0,32 | 0,36 | 0 |
| X4 | 89,98 | 0 | 0 | -1,70| 1 | 0,77 | 0,53 | -1,16 | 0 |
| X2 | 1489,30 | 0 | 1 | 0,76 | 0 | -0,58| -0,05 | 0,62 | 0 |
| Z | 12438,33 | 0 | 0 | 0,39 | 0 | 2,17 | 0,35 | 1,05 | 1 |
