# ChatGPT
- Tokenização: https://platform.openai.com/tokenizer
- Embora as respostas geradas pela versão 4 sejam mais precisas e relevantes, elas podem levar mais tempo para serem geradas do que as respostas da versão 3.5.
- [OpenAI GPT 4](https://openai.com/index/gpt-4-research/)
- [Tech Report](https://arxiv.org/abs/2303.08774)
- Precisão (acurácia): https://cdn3.gnarususercontent.com.br/3146-chatgpt/acuracia.png

## Estratégias

1. Testar prompts de conclusão, induzindo o modelo a completar o início do que deseja.
Os prompts de estilo de conclusão aproveitam como os modelos de linguagem tentam escrever o texto que eles acham que provavelmente virá a seguir. Para orientar o modelo, basta iniciar um padrão ou frase que será completada pela saída que ele deseja ver.
"O chatgpt é ...".

2. Testar prompts de demonstração contendo exemplos.
Semelhante aos prompts de estilo de conclusão, as demonstrações podem mostrar ao modelo o que João deseja que ele faça. Essa abordagem às vezes é chamada de aprendizado de poucos disparos (Few-Shot learning), pois o modelo aprende com alguns exemplos fornecidos no prompt.

3. Quebrar a demanda em pequenas tarefas.
4. Solicitar gerar outras respostas caso não esteja satisfatória.
5. Especifique a saída (visando automação por exemplo) colocando o "schema" da resposta.
   ```js
   titulo=""
   ideia=""
   canais=[]
   ```
6. Para automatização, gere 100 testes e avalie se é confiável. Se quiser que gere vários exemplos de uma só vez, pode instruir algo como _Sugestão #k_ no início do schema do trecho de código, para que ele insira um _contador_.

## Orientações Gerais
- """ (tres aspas duplas) ou ``` (tres crases) para separar o código da pergunta.
- _____ (sublinhado) para indicar um formulário (em texto mesmo).
- Clareza e especificidade.
- Forneça contexto.
- Divida uma pergunta complexa em várias perguntas mais simples.
