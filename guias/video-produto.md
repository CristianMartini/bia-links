# Faça um vídeo de produto com a Bia

Do produto ao vídeo vertical: roteiro, imagem, voz, montagem e motions. Você pede em português, acompanha a prévia e aprova o resultado.

O exemplo é uma vela fictícia criada com IA. Para sua loja, comece com a foto verdadeira do produto.

## Antes de começar

Abra a conversa com a Bia ou com o agente instalado no seu computador. É ali que você cola os pedidos deste guia e envia a foto. Uma conversa comum de chat, sem acesso ao computador, pode explicar os passos, mas não executa a montagem local.

Use sua conta para a geração de imagens. O agente confere as instalações locais; o acesso às ferramentas depende das contas e condições de uso de cada serviço. Comece pelo pedido de preparação abaixo.

## 1. Separe o material

Tenha uma foto nítida, nome do produto, características confirmadas e a ação que deseja no final: visitar a loja, conhecer a coleção ou chamar no WhatsApp. Preço e condições só entram se estiverem corretos.

As ferramentas usadas neste exemplo:

- **GPT Image:** imagem de produto, com referência quando houver foto real.
- **edge-tts, voz Francisca em português:** narração.
- **Remotion:** montagem, câmera, textos e motions.
- **FFmpeg e ffprobe:** conferir o arquivo e medir o áudio.
- **Um agente que executa no computador:** organiza os arquivos e opera as ferramentas. Aqui usamos a Bia.

Para repetir a montagem, o computador precisa de Node.js, Python, FFmpeg e um projeto Remotion. Não precisa decorar comandos: peça ao agente para conferir e preparar o ambiente antes de produzir. Login e qualquer contratação ficam com você.

Copie este pedido:

> Quero fazer um vídeo vertical de produto. Confira se tenho Node.js, Python, FFmpeg, edge-tts e um projeto Remotion funcionando. Mostre o que falta e use uma pasta separada para este vídeo. Não contrate nada. Eu faço os logins necessários. Primeiro deixe o ambiente pronto e me diga onde os arquivos serão salvos.

O acesso ao GPT Image depende da conta utilizada. Confira também as [condições de licença do Remotion](https://www.remotion.dev/docs/license) para o seu uso.

## 2. Peça um roteiro curto

Comece com um vídeo de 15 a 25 segundos, três cenas e uma única chamada no final.

> Faça um roteiro de vídeo vertical de 20 segundos para uma vela de lavanda. Público: pessoas que gostam de decorar a casa. Cena 1: mostre a vela acesa em uma mesa bem iluminada. Cena 2: destaque os detalhes visuais do produto. Cena 3: convide a conhecer a coleção. Use frases curtas. Não invente benefícios, preço ou depoimento. Mostre o roteiro antes de produzir.

Troque a vela pelo seu produto. Leia a fala em voz alta: precisa soar como conversa. Se ficar comprida, corte antes de gerar a voz.

## 3. Prepare a imagem

Para um produto real, envie a foto como referência e peça para manter cor, formato, embalagem, rótulo e quantidade. Confira o resultado antes de seguir.

> Use a foto que enviei como referência. Crie uma composição vertical 9:16, com o produto em destaque, iluminação de estúdio e espaço para o título. Preserve o produto e sua embalagem. Não invente texto no rótulo nem acrescente acessórios que pareçam fazer parte da oferta. Me mostre a imagem para aprovação.

Para experimentar com um produto fictício:

> Crie uma imagem de uma vela fictícia de lavanda em copo de vidro âmbar, acesa, com rótulo creme sem palavras ou marca. Mesa de madeira escura, ramos de lavanda e luz lateral quente. Foto realista, vertical 9:16, com espaço acima para o título. Sem pessoas.

Salve a imagem aprovada. Não use uma imagem diferente em cada cena se isso mudar o produto.

## 4. Gere a voz

> Gere a narração aprovada com edge-tts, voz pt-BR-FranciscaNeural, em velocidade normal. Salve o áudio em MP3. Meça a duração real com ffprobe e use esse tempo para montar as cenas e sincronizar as legendas. Não acelere a fala para caber no roteiro.

Para quem quiser testar a voz pelo terminal, com Python e edge-tts instalados:

```sh
python -m edge_tts --voice pt-BR-FranciscaNeural --text "Uma luz suave para o seu cantinho. Conheça nossa coleção." --write-media voz.mp3
```

Ouça antes de montar. Corrija palavras, pausas e pronúncia agora.

## 5. Monte o vídeo e os motions

> No projeto Remotion, monte um vídeo vertical 1080×1920 a 30 quadros por segundo com a imagem e a voz aprovadas. Comece mostrando o produto. Faça uma aproximação suave de câmera, títulos que entram no momento da fala, transições curtas e legendas grandes. Deixe textos importantes longe das bordas e dos controles do Instagram. Use movimentos com antecipação e assentamento suave. Sincronize tudo com a duração real do áudio. Entregue primeiro uma prévia de 6 segundos.

Motions que funcionam juntos neste exemplo:

- Câmera aproxima devagar para destacar o produto.
- Título entra em duas partes, acompanhando a fala.
- Palavras importantes ganham destaque de cor ou escala.
- Corte entre plano geral e detalhe mantém a continuidade.
- Chamada final permanece tempo suficiente para ler.

Movimento de câmera e texto pode ser feito na edição. Para uma pessoa atuar, uma chama se mover ou um objeto mudar fisicamente, é preciso filmagem ou uma etapa de imagem para vídeo. Se usar essa etapa, confira se ela preservou o produto e peça uma prévia antes de integrar.

## 6. Veja a prévia antes de exportar tudo

Abra os seis segundos e confira:

- O produto continua igual à foto?
- A primeira frase chama atenção e dá para ler no celular?
- Voz e legendas estão juntas?
- Os movimentos ajudam a olhar para o produto?
- O texto fica longe dos botões da rede social?

Peça ajustes específicos: “aumente a legenda”, “reduza a aproximação” ou “deixe o título por mais um segundo”. Só depois aprove a exportação completa.

## 7. Exporte e confira o original

> Exporte o vídeo completo em MP4, H.264, 1080×1920, 30 quadros por segundo, com áudio AAC. Abra o arquivo final e confira imagem, voz, legendas e duração. Faça também uma verificação de integridade com FFmpeg. Me entregue o arquivo original, sem passar por compressão de aplicativo de mensagem.

Conferência técnica opcional, no terminal:

```sh
ffprobe -v error -show_entries stream=codec_name,width,height,r_frame_rate,duration -of default=nw=1 video.mp4
ffmpeg -v error -xerror -i video.mp4 -f null -
```

A verificação técnica encontra problemas de arquivo. Você ainda precisa assistir e ouvir o vídeo inteiro.

## Pedido completo para copiar

> Bia, faça um vídeo vertical de 20 segundos para [produto], voltado a [público], com a chamada [ação]. Vou enviar a foto real e as informações corretas. Confira as ferramentas e prepare uma pasta separada. Primeiro mostre o roteiro em três cenas. Depois prepare a imagem preservando meu produto, gere a narração Francisca em velocidade normal e monte no Remotion com câmera suave, tipografia em movimento e legendas sincronizadas. Me mostre uma prévia de 6 segundos antes de exportar. Depois entregue o MP4 original em 1080×1920 e confira imagem, áudio e integridade. Não publique nem contrate nada sem minha autorização.

Quer a Bia fazendo isso no seu computador? Conheça a Bia pelo link do perfil [@bia.agente.ia](https://www.instagram.com/bia.agente.ia/).

Exemplo ilustrativo com produto fictício. Personagem criada com IA.
