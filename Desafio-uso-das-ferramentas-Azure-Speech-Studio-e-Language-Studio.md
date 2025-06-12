# Introdução à Análise de Linguagem e Fala com Azure AI

Este guia apresenta, de forma clara, objetiva e didática, como usar o **Language Studio** e o **Speech Studio** no Azure AI para:

1. **Análise de Sentimentos** em texto (Language Studio).  
2. **Reconhecimento e Síntese de Fala** (Speech Studio).

Cada seção inclui explicações complementares e exemplos práticos.

---

## 1. Análise de Sentimentos com o Language Studio

### O que é o Language Studio?

O **Language Studio** faz parte do Azure AI e fornece ferramentas de Processamento de Linguagem Natural (PLN) para:

- **Classificação de texto** (por exemplo, análise de sentimentos).  
- **Extração de entidades**, **resumo de texto**, entre outras funções.

### Como funciona a análise de sentimentos?

1. **Pré-processamento**: 
   
   - **Tokenização**: divide o texto em palavras ou subpalavras.  
   - **Normalização**: transforma tudo em letras minúsculas e remove pontuação.  

2. **Representação**:
   
   - Cada token vira um vetor numérico (embedding) que representa o significado das palavras.

3. **Classificação**:
   
   - Um modelo (geralmente uma rede neural) calcula a probabilidade de cada sentimento: positivo, neutro ou negativo.

### Exemplo prático

Comentário de cliente:

> "O produto chegou rápido, mas a embalagem estava danificada."

- O modelo atribui uma **nota de sentimento** para cada trecho:
  - "chegou rápido" → positivo  
  - "embalagem danificada" → negativo  
- Resultado final: um escore geral, como 0,45 numa escala de -1 a +1.

### Passo a passo para usar o Language Studio

1. Acesse o portal [https://portal.azure.com](https://portal.azure.com) e faça login.  
2. Clique em **Create a resource** → **AI + Machine Learning** → **Language service** → **Create**.  
3. Selecione os recursos desejados (como análise de sentimento) e clique em **Review + create**.  
4. Após o deploy, vá para [https://language.cognitive.azure.com](https://language.cognitive.azure.com).  
5. No **Language Studio**, clique em **Create new** → **Classify text** → **Analyze sentiment and mine opinions**.  
6. Escolha o idioma, cole ou envie seu texto e clique em **Run** para obter a análise.

---

## 2. Compreensão de Linguagem Coloquial com o Speech Studio

### O que é o Speech Studio?

O **Speech Studio** é um conjunto de ferramentas da Azure AI que permite:

- **Conversão de fala em texto** (ASR - Automatic Speech Recognition)  
- **Conversão de texto em fala** (TTS - Text-to-Speech)

### Como a IA entende a linguagem coloquial?

- **Modelos acústicos** transformam sons da fala em fonemas.  
- **Modelos de linguagem** ajudam a prever quais palavras vêm a seguir, facilitando o reconhecimento de gírias, expressões informais e sotaques.

### Fluxo de Reconhecimento de Fala (ASR)

1. **Captura de áudio** (via microfone ou arquivo de áudio)  
2. **Extração de características** (como MFCCs, espectrogramas)  
3. **Decodificação** com redes neurais e modelos de linguagem  
4. **Geração do texto final**

### Fluxo de Síntese de Fala (TTS)

1. **Entrada de texto**  
2. **Análise linguística** (identifica pausas, ênfases e entonações)  
3. **Síntese neural** (o modelo gera a voz com som natural)

### Exemplo prático de TTS com Python

```python
from azure.cognitiveservices.speech import SpeechConfig, SpeechSynthesizer, AudioOutputConfig

speech_key = "<YOUR_KEY>"
service_region = "eastus"

speech_config = SpeechConfig(subscription=speech_key, region=service_region)
audio_config = AudioOutputConfig(filename="saida.wav")
synthesizer = SpeechSynthesizer(speech_config=speech_config, audio_config=audio_config)

texto = "Olá, bem-vindo ao Azure Speech Studio!"
synthesizer.speak_text(texto)
```

### Passo a passo para usar o Speech Studio (ASR)

1. Acesse [Speech Studio](https://speech.microsoft.com/portal)

2. Clique na engrenagem (⚙️) e crie um **New Resource** do tipo **Speech**

3. Clique em **Use resource** após a criação

4. Vá até **Speech to Text** → **Real-time transcription**

5. Escolha o idioma, inicie a gravação de voz ou envie um arquivo

---

## 3. Aplicações práticas

* **Atendimento ao cliente**: análise de sentimentos para identificar críticas recorrentes.
* **Acessibilidade**: TTS pode ajudar pessoas com deficiência visual.
* **Legendas automáticas**: ASR pode gerar transcrições automáticas para vídeos.
* **Assistentes virtuais**: combinação de TTS + ASR = chatbot de voz com linguagem natural.
  
---

## 4. Links Úteis

- [Portal do Azure](https://portal.azure.com/)
- [Azure Language Studio](https://language.cognitive.azure.com/)
- [Azure Speech Studio](https://speech.microsoft.com/portal)
- [Bootcamp DIO – Suzano Python Developer](https://www.dio.me)

---

💡 Este material foi elaborado a partir de anotações de vídeo-aulas disponibilizadas durante **Bootcamp Suzano Python Developer**, oferecido pela plataforma [DIO](https://www.dio.me) e expandido com exemplos e explicações extras para tornar o aprendizado mais acessível e eficiente.


