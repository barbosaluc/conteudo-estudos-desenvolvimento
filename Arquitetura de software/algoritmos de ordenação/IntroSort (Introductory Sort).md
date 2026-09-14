O IntroSort é um algoritmo de ordenação híbrido, Ele combina o melhor do **Quicksort**, **Heapsort** e **Insertion Sort** para fornecer alta performance no caso médio com uma garantia matemática de pior caso $\mathcal{O}(n \log n)$.

### Por que ele foi criado?
O **Quicksort** é extremamente rápido na prática (tem baixos fatores de constante e excelente localidade de referência em cache). No entanto, sua escolha de pivô pode falhar em arranjos específicos, fazendo a complexidade degradar para [[O(n²) - Complexidade Quadrática]] e correndo risco de causar estouro de pilha (_stack overflow_) por [[recursão profunda]].

O IntroSort resolve isso monitorando a profundidade da recursão: se o Quicksort começar a ir longe demais, o algoritmo muda automaticamente de estratégia.
### Como Funciona o Algoritmo

O IntroSort opera em **três fases**:

1. **Fase 1: Quicksort (O motor principal)**
    
    - Inicia a ordenação usando Quicksort (geralmente com a técnica de "pivô da mediana de três").
    - Define um limite máximo de profundidade de recursão baseado no tamanho do array, tipicamente:$$\text{profundidade\_máxima} = 2 \times \lfloor\log_2(n)\rfloor$$
2. **Fase 2: Heapsort (A rede de segurança)**
    
    - Se a profundidade de recursão atingir o limite estipulado, o IntroSort interrompe o Quicksort para aquela partição e alterna para o **Heapsort**.
    - Isso garante que, mesmo no pior cenário possível de pivôs do Quicksort, o tempo restante da partição será limitado em $\mathcal{O}(k \log k)$.

3. **Fase 3: Insertion Sort (O ajuste fino)**
    
    - Para sub-arrays pequenos (tipicamente $n < 16$ ou $n < 32$), a recursão é interrompida.
    - O **Insertion Sort** é executado nesses blocos pequenos, pois sua simplicidade e ausência de chamadas de função superam o overhead do Quicksort para poucos elementos.
### Complexidade e Propriedades

|**Métrica / Propriedade**|**Desempenho**|
|---|---|
|**Tempo (Melhor Caso)**|$\mathcal{O}(n \log n)$|
|**Tempo (Caso Médio)**|$\mathcal{O}(n \log n)$|
|**Tempo (Pior Caso)**|$\mathcal{O}(n \log n)$ _(graças ao Heapsort)_|
|**Espaço Auxiliar**|$\mathcal{O}(\log n)$ _(devido à pilha do Quicksort)_|
|**Estabilidade**|**Não estável** (altera a ordem relativa de elementos iguais)|
|**Tipo de Ordenação**|Baseado em **comparação** e **In-place**|