# ChatGPT
- Tokenização: https://platform.openai.com/tokenizer
- Embora as respostas geradas pela versão 4 sejam mais precisas e relevantes, elas podem levar mais tempo para serem geradas do que as respostas da versão 3.5.
- [OpenAI GPT 4](https://openai.com/index/gpt-4-research/)
- [Tech Report](https://arxiv.org/abs/2303.08774)
- Precisão (acurácia): https://cdn3.gnarususercontent.com.br/3146-chatgpt/acuracia.png
- Quando iniciamos um diálogo, a primeira mensagem não é a minha interação, por debaixo dos panos já há instruções do sistema operando. Podemos mudar as mensagens de sistema via API ou no [Playground](https://platform.openai.com/playground/chat), ambos pagos.

## Estratégias

- Testar prompts de conclusão, induzindo o modelo a completar o início do que deseja.
  Os prompts de estilo de conclusão aproveitam como os modelos de linguagem tentam escrever o texto que eles acham que provavelmente virá a seguir. Para orientar o modelo, basta iniciar um padrão ou frase que será completada pela saída que ele deseja ver.  
  *Exemplo:* `"O chatgpt é ..."`.

- Testar prompts de demonstração contendo exemplos.  
  Semelhante aos prompts de estilo de conclusão, as demonstrações podem mostrar ao modelo o que João deseja que ele faça. Essa abordagem às vezes é chamada de *aprendizado de poucos disparos* (*Few-Shot learning*), pois o modelo aprende com alguns exemplos fornecidos no prompt.

- Quebrar a demanda em pequenas tarefas.

- Solicitar gerar outras respostas caso não esteja satisfatória.

- Especificar a saída (visando automação, por exemplo) colocando o *schema* da resposta.
  ```js
  titulo=""
  ideia=""
  canais=[]
   ```
- Para automatização, gere 100 testes e avalie se é confiável. Se quiser que gere vários exemplos de uma só vez, pode instruir algo como _Sugestão #k_ no início do schema do trecho de código, para que ele insira um _contador_.
- Consulte "várias ideias" e pegue o melhor entre elas. Ou instrua o chat para dar notas entre os pontos positivos e negativos de cada ideia e, quem sabe (outra fala), gerar uma nova ideia a partir dos pontos fortes obtidos.

## Trabalhando com textos
Usar o chatGPT para automatizar coisas.
- Dicas gerais para textos:
  - Dividir as tarefas em etapas pode ajudar a simplificar o processo de execução e tornar a resposta mais eficiente.
  - Delimitadores ajudam o ChatGPT a entender a estrutura do texto original e a produzir resultados mais precisos e relevantes.
  - É interessante especificar qual deve ser o tamanho máximo do resumo.
- Texto e traduções, especifique "variáveis" para melhorar a compreensão do chat (no exemplo foi XXXXX).
   ```
   Resuma o texto: """
   cole o texto na lingua que quiser
   """
   Idioma: XXXXX
   Resumo em XXXXX: _____
   ```
- Especificar o formato de saída. Exemplo: _Capture os pontos negativos do comentário e me devolva no formato `pontos_negativos=[]`.
- Sentimentos "qual o sentimento da pessoa sobre o produto no seu comentário? Opções [positivo, misto, neutro, negativo]".
- Em textos longos, quebre em diálogos diferentes, por causa da limitação de memória dos tokens do chatGPT. Se programaticamente, use bibliotecas que calculam os tokens.
  - O limite é 4mil tokens, faça o resumo de 2mil tokens, armazene a resposta, gere outro diálogo com mais 2mil tokens, junte as respostas, faça um novo chat agora sim com o resumo dos resumos, desde que não ultrapasse o limite.
  - https://github.com/langchain-ai/langchain já faz de forma programática
- Exemplos de aplicação:
  - Mudar o tom do texto (deixe o texto mais carismático, etc)
  - Adapte para a plataforma de comunicação TAL.
  - Converter formatos (csv, python, etc).
  - verificação ortográfica e gramatical.
  - respostas automáticas a e-mails.
    ```
    Você é um assistente de IA de atendimento ao cliente. Sua tarefa é enviar uma resposta por e-mail a um(a) cliente. Dado o e-mail do(a) cliente delimitado por """", gere uma resposta para agradecer ao cliente por sua avaliação. Se o sentimento for positivo ou neutro, agradeça por sua revisão. Se o sentimento for negativo, peça desculpas e sugira que eles entrem em contato com o atendimento ao cliente. Certifique-se de usar detalhes específicos da resenha. Escreva em um tom conciso e profissional. Assine o e-mail como Atendimento ao cliente.
    Resenha """..."""
    Sentimento da Resenha: 
    ```

## Orientações Gerais
- """ (tres aspas duplas) ou ``` (tres crases) para separar o código da pergunta.
- _____ (sublinhado) para indicar um formulário (em texto mesmo).
- Clareza e especificidade.
- Forneça contexto.
- Divida uma pergunta complexa em várias perguntas mais simples.
- chatGPT tem limites de memória então quando o diálogo fica grande, ele vai esquecendo as interações anteriores.

