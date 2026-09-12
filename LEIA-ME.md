# Testes do AvaliaDTM

Bateria automática que confere se o algoritmo diagnóstico continua correto depois de qualquer alteração no `index.html`.

## Como rodar

No Terminal, dentro da pasta do projeto:

```bash
bash testes/rodar-testes.sh
```

Não precisa instalar nada: usa só o `python3` e o `osascript` que já vêm no macOS, e funciona offline. O resultado aparece linha a linha, com `PASSA` ou `FALHA`, e a última linha diz se tudo passou.

## O que é verificado

**`casos-diagnosticos.js`** (41 testes), o motor de decisão:

- Os 10 casos de teste da especificação do projeto (seção 9), que cobrem mialgia e subtipos, artralgia, cefaleia atribuída à DTM, DDCR, DDCR com travamento intermitente, DDSR, DAD e subluxação.
- Os pressupostos que antes ficavam silenciosos: DDSR sem a medida de abertura, item 3.14 não respondido na cefaleia e item 3.19 na subluxação.
- O motor de pendências: se um item não respondido mantém o diagnóstico em aberto, se um achado negativo o descarta de verdade, e se a sugestão de imagem aponta o exame certo.

**`casos-interface.js`** (28 testes), a camada de tela:

- Os cinco blocos renderizam sem erro.
- A ramificação esconde o que precisa ser escondido (por exemplo, o ramo de cefaleia fechado não exibe seus itens).
- O Bloco 5 monta as seções de pendências, refinamentos e imagem, com os atalhos de navegação.
- Nenhum travessão e nenhum emoji na interface gerada.

## Como isso roda sem navegador

O script recorta do `index.html` apenas as funções de lógica e as executa no JavaScriptCore do próprio macOS (via `osascript -l JavaScript`). Para os testes de interface, um DOM mínimo é simulado, de modo que as funções de renderização rodam de verdade e o HTML gerado é inspecionado.

## Ao alterar o algoritmo

Se você mudar um critério de propósito (por exemplo, um ponto de corte), o teste correspondente vai falhar. Isso é esperado: ajuste o valor esperado no arquivo de testes junto com a mudança, para que a bateria continue protegendo o resto.
