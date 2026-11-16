# Análise da eficácia de LLMs na geração automática de documentação de código

Artigo de Trabalho de Conclusão de Curso em Engenharia de Software (UniCesumar, 2025), com orientação do Prof. Dr. João Paulo Biazotto. Nota final: 9,7.

**[Ler o artigo completo (PDF)](artigo.pdf)**

## Pergunta

Os modelos de linguagem atuais conseguem documentar código com regras de negócio reais de forma útil e correta, a ponto de reduzir a dívida técnica de documentação?

## Método

- **Modelos comparados:** GPT-5 (OpenAI), Claude 4.5 Sonnet (Anthropic), Gemini 2.5 Flash (Google) e Llama 3 70B (Meta, via Groq).
- **Corpus:** 10 arquivos PHP de um marketplace real em produção, escolhidos para cobrir regras de negócio de complexidade variada (comissão, status de pedidos, elegibilidade). Por confidencialidade, nenhum trecho do código é reproduzido.
- **Geração:** um script em Python chamou as APIs dos quatro provedores com o mesmo prompt template, gerando 40 documentações.
- **Avaliação cega:** 7 desenvolvedores com 4 a 12 anos de experiência e domínio da regra de negócio avaliaram as documentações embaralhadas e sem identificação do modelo, em dois critérios: utilidade (capturou a regra de negócio?) e precisão factual (há erro?).
- **Preferência:** em uma etapa separada e não cega, os mesmos desenvolvedores indicaram a ferramenta de IA que mais usam no dia a dia.

## Resultados

| Modelo | Capturou a regra de negócio | Documentações com erro factual |
|---|---|---|
| GPT-5 | 92% | 8% |
| Claude 4.5 Sonnet | 89% | 11% |
| Gemini 2.5 Flash | 78% | 22% |
| Llama 3 70B | 75% | 25% |

- Os modelos de ponta foram claramente superiores em utilidade e precisão. Os modelos otimizados para velocidade erraram de duas a três vezes mais.
- Nenhum modelo ficou livre de alucinações, como parâmetros inexistentes na assinatura real de um método.
- A preferência declarada pelos desenvolvedores favoreceu o ecossistema da OpenAI além do que o desempenho medido justificaria, o que sugere peso da familiaridade na adoção.

## Conclusão

LLMs resolvem bem a **dívida de omissão** (falta de documentação), mas criam uma **dívida de verificação**: o texto gerado precisa ser revisado por quem conhece a regra de negócio. Erros silenciosos podem gerar ainda uma dívida cognitiva no time. O ganho real vem da colaboração entre desenvolvedor e IA, com o desenvolvedor no papel de revisor, e não da automação sem validação.

## Limitações

Quatro modelos, dez arquivos de um único sistema em PHP e um retrato de um momento específico: os modelos mudam com frequência. Os resultados orientam decisões de adoção, mas não são um ranking universal.

## Autor

Nathan Lisandro Toppa · [LinkedIn](https://www.linkedin.com/in/nathan-lisandro-toppa-9496271ba/) · [GitHub](https://github.com/NathanLisandro)
