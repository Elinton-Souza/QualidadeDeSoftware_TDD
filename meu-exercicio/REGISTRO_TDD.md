# Registro do ciclo de TDD

## Comportamento escolhido

Cobrar taxa fixa de R$ 5 para distancia de ate 3 km.

## Red

**Teste criado:** test_taxa_ate_3km

**Motivo da falha:** a funcao calcular_taxa_entrega ainda nao existia em src/pedido.py (estava apenas comentada como exercicio), entao o teste falhava com `ImportError: cannot import name 'calcular_taxa_entrega' from 'src.pedido'` ao tentar importa-la.

## Green

**Implementacao realizada:** criei a funcao calcular_taxa_entrega retornando o valor fixo 5, suficiente para fazer esse primeiro teste passar (toda a suite ficou verde: 5 passed).

## Refactor

**Melhoria realizada:** so apos os tres cenarios obrigatorios e o desafio opcional estarem verdes, adicionei tipagem (distancia_km: float, total_pedido: float) e um docstring explicando as regras de negocio, sem alterar o comportamento da funcao.

**Resultado final:** os 8 testes da suite (4 de calcular_total + 3 cenarios obrigatorios + 1 do desafio opcional de calcular_taxa_entrega) passam.

---

## Ciclos adicionais registrados (para referencia)

### Ciclo 2 — acima de 3 km

- **Red:** test_taxa_acima_3km falhou com `assert 5 == 7` (a implementacao ainda retornava o valor fixo do ciclo 1).
- **Green:** generalizei a funcao com `if distancia_km <= 3: return 5` e `excedente = distancia_km - 3; return 5 + 2 * excedente`.
- **Resultado:** 6 passed.

### Ciclo 3 — entrega gratuita acima de R$ 100

- **Red:** test_entrega_gratuita_acima_100 falhou com `assert 9 == 0` (a regra de frete gratis ainda nao existia).
- **Green:** adicionei `if total_pedido >= 100: return 0` no inicio da funcao.
- **Resultado:** 7 passed.

### Ciclo 4 — desafio opcional (distancia negativa)

- **Red:** test_distancia_negativa_gera_valueerror falhou com `Failed: DID NOT RAISE ValueError`.
- **Green:** adicionei `if distancia_km < 0: raise ValueError("A distancia nao pode ser negativa.")` no inicio da funcao.
- **Resultado:** 8 passed.
