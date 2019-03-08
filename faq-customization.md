---

copyright:
  years: 2018, 2019
lastupdated: "2019-03-07"

subcollection: speech-to-text-icp

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:tip: .tip}
{:important: .important}
{:note: .note}
{:deprecated: .deprecated}
{:pre: .pre}
{:codeblock: .codeblock}
{:screen: .screen}
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}

# Customization
{: #faq-customization}

## Language model customization
{: #lmCustomization}

1.  <span style="color:#003F69">Can I add my own specialized vocabulary to the service?</span>

    Yes. The service's base vocabulary contains many words that are used in everyday conversation by a broad, general audience. Its models provide sufficiently accurate recognition for many applications but can lack knowledge of specific terms that are associated with particular domains. Such words are referred to as *out-of-vocabulary (OOV) words*.

    The language model customization interface can improve the accuracy of speech recognition for specialized domains. You can use customization to expand and tailor the vocabulary of a base model to include domain-specific terminology. For more information, see [Creating a custom language model](/docs/services/speech-to-text-icp/language-create.html) and [Using a custom language model](/docs/services/speech-to-text-icp/language-use.html).

1.  <span style="color:#003F69">How much data is needed to build a custom language model?</span>

    It is not possible to provide an exact figure, since many factors contribute to the answer. Adding OOV words in context via a corpus and adding custom words directly can both improve the quality of a custom language model. When you add OOV words from corpora, a corpus that uses the words in the context in which they are used in audio can improve transcription accuracy. But depending on the use case, even adding a few custom words directly to a model can make a positive difference.

1.  <span style="color:#003F69">Can corpora that I add to a custom language model repeat words and sentences?</span>

    Yes. Repeating the OOV words in corpora can improve the quality of the custom language model. How you duplicate the words in corpora depends on how you expect users to say them in the audio that is to be recognized.

    In general, it is better for the corpora to use the OOV words in different contexts and phrases, which improves how the service learns the words. However, if users speak the words in only a couple of contexts, then showing the words in other contexts does not improve the quality of the custom model. Speakers never use the words in those contexts. If speakers are likely to use the same phrase frequently, then repeating that phrase in the corpora can improve the quality of the model.

## Acoustic model customization
{: #amCustomization}

1.  <span style="color:#003F69">Can I adapt the service for the acoustic characteristics of my environment and speakers?</span>

    Yes. The service was developed with a base acoustic model that works well with various audio characteristics. But adapting a base model can improve speech recognition in some cases, such as a unique or noisy environment, atypical speech patterns, or speaker accents.

    The acoustic model customization interface can improve the accuracy of speech recognition for different environments and speakers. For more information, see [Creating a custom acoustic model](/docs/services/speech-to-text-icp/acoustic-create.html) and [Using a custom acoustic model](/docs/services/speech-to-text-icp/acoustic-use.html).

1.  <span style="color:#003F69">How much audio data is needed to build a custom acoustic model?</span>

    You must add at least 10 minutes and no more than 100 hours of audio to a custom acoustic model. The quality of the audio makes a difference when you are determining how much to add. The better the model's audio reflects the characteristics of the audio that is to be recognized, the better the quality of the custom model. If the audio is of good quality, adding more audio can improve transcription accuracy. As a rough guideline, adding five to ten hours of audio can make a positive difference.

1.  <span style="color:#003F69">Do I need to transcribe the audio data that I add to a custom acoustic model?</span>

    Transcribing the audio data is not strictly necessary. But if you have transcriptions of the audio, or even a list of the OOV words that are used in the audio, they can improve the quality of the custom acoustic model. Transcriptions are especially valuable if the audio contains many OOV words.

    To use a transcription or list of words, you first create a custom language model with the textual data. You can then use both the custom language model and the custom acoustic model together:

    -   You can train the custom acoustic model with the custom language model. For more information, see [Training a custom acoustic model with a custom language model](/docs/services/speech-to-text-icp/acoustic-both.html#useBothTrain).
    -   You can use the custom language model with the custom acoustic model in speech recognition requests. For more information, see [Using custom language and custom acoustic models during speech recognition](/docs/services/speech-to-text-icp/acoustic-both.html#useBothRecognize).

   Both of these approaches can improve the accuracy of speech recognition with a custom acoustic model.

1.  <span style="color:#003F69">What kind of improvement in recognition accuracy can I expect from using a custom acoustic model?</span>

    The answer depends on a number of factors, such as how much audio data the custom acoustic model contains and how similar that data is to the audio that is being transcribed. The answer also depends on whether the custom acoustic model is trained with a corresponding custom language model. Using audio data alone is referred to as *unsupervised training*. Using a corresponding custom language model during training is referred to as *lightly supervised training*.

    Using a custom language model to train a custom acoustic model is effective only if

    -   The custom language model was built with direct transcriptions of the audio data.
    -   The custom language model contains words from the same domain as the audio data.

    If the audio contains many OOV words, it is better to use a custom language model during training, even if the custom language model merely adds a list of custom words. In general, a good custom acoustic model can improve the accuracy of transcription by as much as 40 percent.
