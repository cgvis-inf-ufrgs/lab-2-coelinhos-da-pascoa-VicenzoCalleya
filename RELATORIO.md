# Relatório - Coelinhos da Páscoa

> [!CAUTION]
> - Lembre-se que você <ins>**não pode utilizar ferramentas de IA para
>   escrever este relatório**</ins>

## Dados do aluno

- **Cartão UFRGS**: <mark>`589370`</mark>
- **Nome**: <mark>`Vicenzo Lamberti Calleya`</mark>

## Passos que eu segui para resolver o problema especificado (em formato de *"prompt"*)

> [!IMPORTANT]
> - Coloque aqui todas as informações necessárias para que alguém
>   (pessoa ou ferramenta de IA) possa reproduzir os seus passos para
>   solucionar o problema
> - Escreva em formato imperativo, como se fosse um *prompt* com as
>   instruções a serem seguidas na solução do problema
> - Seja objetivo e conciso: quanto *menos palavras* você utilizar,
>   melhor
> - Seja técnico e use terminologia adequada: assuma que quem irá ler
>   os seus passos possui conhecimento de Ciência da Computação e
>   Computação Gráfica
> - Caso você queira incluir informações "longas" (como algum *prompt*
>   grande usado com alguma ferramenta de IA), crie arquivos à parte e
>   adicione links no texto (por exemplo, crie o arquivo `PROMPTS.md`
>   e adicione um link markdown `[os prompts detalhados estão
>   aqui](PROMPTS.md)`)
> - Novamente, lembre-se que você *não pode utilizar ferramentas
>   de IA para escrever este relatório*

1) Dentro do loop while (!glfwWindowShouldClose(window)), substitua tanto a contrução do modelo do coelho e da esfera por um loop for, que se repete 16 vezes (por conta dos 16 coelhos)

2) Dentro desse loop for (a partir daqui, todos os passos serão dentro desse loop), comece definindo a váriavel t (tempo) para (float)glfwGetTime(); e uma que defina a velocidade da roda (ou seja, a velocidade que os coelhos vão rodar) para 0,4f

3) Para definir o trajeto dos coelhos (a roda em que eles giram) é necessário informar o ângulo, o raio da roda, e a função seno (como eles sobem e descem). Defina como (2.0f * 3.14159265359f * i / 16.0f) - t * wheel_speed;, 2,5f; e 1.0f * sin(angle * 4.0f); respectivamente

4) Defina a matriz do coelho como = Translação (por onde ele vai) * Rotação (para ele encarar por onde ele está indo) * Escala (Tamanho). Essa matriz, matematicamente falando, deverá ser definida assim: Matrix_Translate(radius * cos(angle), y_pos, radius * sin(angle)) * Matrix_Rotate_Y(-angle - 1.57f) * Matrix_Scale(0.35f, 0.35f, 0.35f);

5) A cada 4 coelhos, um rotaciona no eixo Z. Para isso, use a função iterativa if (i % 4 == 0), e dentro dela adicione float mortal_angle = (angle * 4.0f) + 1.57f; e model_bunny = model_bunny * Matrix_Rotate_Z(-mortal_angle);

6) Desenhe os coelhos (por meio das funções glUniformMatrix4fv, glUniform1i e DrawVirtualObject)

7) Para cada coelho, há 2 ovos girando ao redor dele. Para isso adicione um loop for adicional (que se repete 2 vezes), e dentro desse loop defina tanto a matriz do modelo (que é dependente do modelo do coelho) quanto desenhe os ovos, por meio da matriz = model_bunny * Matrix_Rotate_X(egg_angle) * Matrix_Translate(0.0f, 0.8f, 0.0f) * Matrix_Scale(0.2f, 0.25f, 0.2f);

8) Por fim, para deixar o chão coerente, fora do loop dos 16 coelhos, substitua a parte de translação da matriz do modelo do chão de Matrix_Translate(0.0f,-1.0f,0.0f) para Matrix_Translate(0.0f,-1.3f,0.0f)

## Principais dificuldades encontradas durante o desenvolvimento (formato livre)

Incrivelmente, a maior dificuldade que eu encontrei nesse trabalho não foi a edição do código, mas sim em fazê-lo compilar inicialmente. Após algumas horas de tentativas finalmente resultarem num sucesso em compilar e rodar o main.c original, editar o programa para fazer com que ele fique parecido com o video de referência foi bem mais tranquilo. Embora a maior parte dela foi tranquila, há uma das caracteristicas que eu não consegui reproduzir na minha versão do código: No video original, os ovos que rodeam os coelhos sempre tem o "topo" deles em direção para cima, enquanto na minha versão o "topo" dos ovos sempre ficavam direcionados onde o coelho estava. Acredito que esse problema se deve principalmente por conta de que o modelo dos ovos era muito dependente do modelo dos coelhos, mas não consegui editar ele de um jeito em que o problema da direção deles sumisse. Por conta disso, o trabalho está tecnicamente incompleto.

## Você acha que conseguiu resolver o problema de forma adequada?

Acredito que sim, já que sem ser o erro da direção dos ovos mencionada anteriormente, a minha versão conseguiu atingir uma forma muito semelhante ao video original, com as diferenças sendo apenas algumas discrepâncias de escala bem pequenas, como provavelmente a diferença mínima da velocidade do giro, ou do tamanho dos coelhos/roda. De qualquer forma, penso que os resultados foram ainda sim satisfatórios, já que tentei replicar o resultado esperado conforme minhas melhores habilidades.

## Se você quiser compartilhar mais alguma coisa, coloque aqui:

<mark>`<preencher>`</mark>

## Se você possui alguma sugestão para o professor sobre esta atividade, coloque aqui:

<mark>`<preencher>`</mark>
