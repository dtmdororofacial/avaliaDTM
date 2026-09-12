# AvaliaDTM

Algoritmo diagnóstico do Eixo I do DC/TMD para uso clínico, em português brasileiro.

Ferramenta de apoio ao raciocínio diagnóstico do cirurgião-dentista durante a consulta. Conduz um fluxo guiado de cinco blocos (história de dor, história articular, exame físico, exames de imagem e resultado) e devolve as hipóteses diagnósticas por lado, com o resumo pronto para copiar no prontuário.

## Como usar

Abra o `index.html` no navegador, pelo celular, tablet ou computador. Não precisa de instalação nem de internet depois que a página carrega.

## Privacidade

Nenhum dado é salvo. Não há banco de dados, servidor, cookie ou armazenamento local: todas as respostas existem apenas na memória do navegador durante a sessão e desaparecem ao recarregar ou fechar a página. Em conformidade com a LGPD.

## O que a ferramenta faz

- Aplica os critérios do Eixo I do DC/TMD para mialgia e subtipos, artralgia, cefaleia atribuída à DTM, deslocamento de disco com redução (com e sem travamento intermitente), deslocamento de disco sem redução (com e sem limitação de abertura), doença articular degenerativa e subluxação.
- Ramifica o exame conforme a história: itens que não se aplicam ao caso não são exibidos.
- Distingue o que foi descartado por achado negativo do que ainda não foi avaliado, e aponta qual item falta para fechar cada diagnóstico em aberto.
- Indica quais hipóteses dependem de imagem para confirmação e qual exame as confirmaria.
- Mostra, em cada hipótese, os critérios cumpridos e os pressupostos não confirmados.

## Limitações

Esta é uma versão operacional simplificada do exame do DC/TMD: contém apenas os itens que alimentam o algoritmo diagnóstico. Pressupõe examinador treinado no protocolo completo, incluindo palpação calibrada e o conceito de dor familiar. A ferramenta apoia o raciocínio clínico e não substitui o julgamento do examinador.

## Créditos

Baseado em: Schiffman E et al. Diagnostic Criteria for Temporomandibular Disorders (DC/TMD) for Clinical and Research Applications. J Oral Facial Pain Headache. 2014;28(1):6 a 27.

Instrumentos em português brasileiro: tradução de Pereira Jr. FJ e Gonçalves DAG (2020), International Network for Orofacial Pain and Related Disorders Methodology (INfORM). Os instrumentos do DC/TMD são de reprodução livre com atribuição.

Implementação digital independente, sem endosso oficial do INfORM.

Desenvolvimento: Profa. Dra. Juliana Stuginski Barbosa, @dtmdororofacial

## Testes

A pasta `testes` contém a bateria automática que verifica o algoritmo (69 testes, incluindo os casos de validação da especificação). Para rodar, no Terminal, dentro da pasta do projeto:

```bash
bash testes/rodar-testes.sh
```

Detalhes em `testes/LEIA-ME.md`.
