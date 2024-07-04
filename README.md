# Projeto: Processamento de Sinal de Áudio com Cancelamento de Ruído e Equalização

Este projeto envolve o desenvolvimento de um circuito capaz de processar um sinal de áudio contaminado com ruído, aplicar a equalização desejada e gerar um sinal de saída com ruído reduzido e equalizado. Além disso, o sistema deve fornecer uma potência RMS média de 1 W para as caixas de som.

## Estrutura do Projeto

O projeto é dividido em dois principais circuitos:

1. **circuito_cancela.asc**: Responsável pelo cancelamento do ruído do áudio de entrada.
2. **circuito_filtros.asc**: Responsável pela equalização do sinal de áudio.

## Procedimentos

### Cancelamento de Ruído

1. Execute o circuito `circuito_cancela.asc` por 15 segundos usando a diretiva do LTSpice:
.tran 15

2. Gere o arquivo de áudio sem ruído com a diretiva:
.wave "output_sem_ruido.wav" 16 44.1k V(saida_filtro)

### Equalização

1. Execute o esquemático `circuito_filtros.asc`, que lê o arquivo gerado pelo módulo anterior.
2. Aplique a equalização através de filtros e direcione o sinal para os respectivos alto-falantes conforme a faixa de frequência.
3. Finalmente, concatene as saídas no arquivo de áudio `output_combined_equalizado.wav` com a diretiva:
.wave "output_combined.wav" 16 44.1k V(tweeter) V(mid) V(subwoofer)


## Resultados

- **output_sem_ruido.wav**: Sinal de áudio com ruído cancelado.
- **output_combined_equalizado.wav**: Sinal de áudio final, equalizado e pronto para reprodução nos alto-falantes.

## Diretivas LTSpice Utilizadas

- `.tran 15`: Simulação transiente de 15 segundos.
- `.wave "output_sem_ruido.wav" 16 44.1k V(saida_filtro)`: Gera o arquivo de áudio sem ruído.
- `.wave "output_combined.wav" 16 44.1k V(tweeter) V(mid) V(subwoofer)`: Gera o arquivo de áudio final equalizado.

