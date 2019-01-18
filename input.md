---

copyright:
  years: 2015, 2019
lastupdated: "2019-01-01"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:tip: .tip}
{:note: .note}
{:deprecated: .deprecated}
{:important: .important}
{:pre: .pre}
{:codeblock: .codeblock}
{:screen: .screen}
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}

# Input features
{: #input}

{{site.data.keyword.ibmwatson}} {{site.data.keyword.speechtotextshort}}: Customer Care offers the following features to specify how the service is to perform a speech recognition request. All of the input parameters that are described in the following sections are optional. Only the input audio is required.
{: shortdesc}

-   For examples of simple speech recognition requests for each of the service's interfaces, see [Making a recognition request](/docs/services/speech-to-text-icp/basic-request.html).
-   For an alphabetized list of all available speech recognition parameters, including their status (generally available or beta), supported languages, and supported interfaces, see the [Parameter summary](/docs/services/speech-to-text-icp/summary.html).

## Custom models
{: #custom}

Language and acoustic model customization are available at different levels of support (generally available or beta). For more information, see [Language support for customization](/docs/services/speech-to-text-icp/custom.html#languageSupport).
{: note}

All interfaces accept a custom model for use in a recognition request:

-   *Custom language models* expand the service's base vocabulary with terminology from specific domains. Use the `language_customization_id` parameter to include a custom language model with a request. You can also specify an optional `customization_weight` parameter. The parameter indicates the relative weight that is given to words from the custom model as opposed to words from the base vocabulary.

    For more information, see [Using a custom language model](/docs/services/speech-to-text-icp/language-use.html).
-   *Custom acoustic models* adapt the service's base acoustic model for the acoustic characteristics of your environment and speakers. Use the `acoustic_customization_id` parameter to include a custom acoustic model with a request. You can specify both a custom language model and a custom acoustic model with a request.

    For more information, see [Using a custom acoustic model](/docs/services/speech-to-text-icp/acoustic-use.html).

Custom models are based on one of the language models that are described in [Languages and models](/docs/services/speech-to-text-icp/models.html). A custom model can be used only with the base model for which it is created. If your custom model is based on a model other than `en-US_BroadbandModel`, the default, you must also specify the name of the model with the request. To use a custom model, you must issue the request with service credentials that are created for the instance of the service that owns the custom model.

For an introduction to customization, see [The customization interface](/docs/services/speech-to-text-icp/custom.html).

### Custom model examples
{: #customExample}

The following example request includes the `language_customization_id` parameter to use the custom language model with the specified ID. It includes the `customization_weight` parameter to indicate that words from the custom model are to be given a relative weight of `0.5`.

```bash
curl -X POST -u "apikey:{apikey}"
--header "Content-Type: audio/flac"
--data-binary @{path}audio-file.flac
"https://{icp_cluster_host}{:port}/speech-to-text/api/v1/recognize?language_customization_id={customization_id}&customization_weight=0.5"
```
{: pre}

The following example request uses both a custom language model and a custom acoustic model. The former is identified with the `language_customization_id` parameter, the latter with the `acoustic_customization_id` parameter.

```bash
curl -X POST -u "apikey:{apikey}"
--header "Content-Type: audio/flac"
--data-binary @{path}audio-file1.flac
"https://{icp_cluster_host}{:port}/speech-to-text/api/v1/recognize?language_customization_id={customization_id}&acoustic_customization_id={customization_id}"
```
{: pre}

For examples that use custom models with each of the service's interfaces, see

-   [Using a custom language model](/docs/services/speech-to-text-icp/language-use.html)
-   [Using a custom acoustic model](/docs/services/speech-to-text-icp/acoustic-use.html)

## Grammars
{: #grammars}

The grammars feature is beta functionality for all languages. The batch-processing interfaces does not currently support grammars.
{: note}

You can add grammars to a custom language model and use them for speech recognition. Grammars use a formal language specification to define a set of production rules for transcribing strings. The rules specify how to form valid strings from the language's alphabet.

When you use a grammar for speech recognition, the service recognizes only phrases that are recognized by the grammar. By limiting the search space for valid strings, the service can deliver results faster and more accurately.

All interfaces accept the following parameters for a recognition request:

-   The `language_customization_id` parameter identifies the custom language model for which the grammar is defined. You must issue the request with service credentials for the instance of the service that owns the model.
-   The `grammar_name` parameter specifies the grammar that you want to use. You can specify only a single grammar with a request.

For more information, see [Using grammars with custom language models](/docs/services/speech-to-text-icp/grammar.html).

### Grammars example
{: #grammarsExample}

The following example request includes the `language_customization_id` and `grammar_name` parameters to restrict the service's response to strings that are defined in the grammar named `list-abnf`.

```bash
curl -X POST -u "apikey:{apikey}"
--header "Content-Type: audio/flac"
--data-binary @{path}audio-file.flac
"https://{icp_cluster_host}{:port}/speech-to-text/api/v1/recognize?language_customization_id={customization_id}&grammar_name=list-abnf"
```
{: pre}

For examples that use grammars with each of the service's interfaces, see [Using a grammar for speech recognition](/docs/services/speech-to-text-icp/grammar-use.html).

## Base model version
{: #version}

To improve the quality of speech recognition, the service occasionally updates the base language models described in [Languages and models](/docs/services/speech-to-text-icp/models.html). The base models for languages are independent of each other, as are the broadband and narrowband models for a language. Therefore, updates to base models occur independently of each other and have no effect on other models.

When multiple versions of a base model exist, the optional `base_model_version` parameter specifies the version of the model to be used with a recognition request. The parameter is intended primarily for use with custom models that are updated for a new base model, but it can be used without a custom model. The version of a base model that is used for a request depends on whether you pass the `base_model_version` parameter. It also depends on whether you specify a custom model (language, acoustic, or both) with the request.

-   *If you do not specify a custom model with the request*

    -   Omit the `base_model_version` parameter to use the latest version of the base model.
    -   Specify the `base_model_version` parameter to use a specific version of the base model.

-   *If you specify a custom model with the request*

    -   Omit the `base_model_version` parameter to use the latest version of the base model to which the custom model is upgraded. For example, if the custom model is upgraded to the latest version of the base model, the service uses the latest versions of the base and custom models.
    -   Specify the `base_model_version` parameter to use the specified versions of both the base and custom models.

The parameter is intended for use with custom models. Therefore, you can learn about the available versions of a base model only by listing information about a custom model that is based on it.

-   For more information about upgrading custom models, see [Upgrading custom models](/docs/services/speech-to-text-icp/custom-upgrade.html).
-   For more information about using different versions of base and custom models for speech recognition, see [Making recognition requests with upgraded custom models](/docs/services/speech-to-text-icp/custom-upgrade.html#upgradeRecognition).

The batch-processing interfaces does not support the `base_model_version` parameter. Batch processing always uses the latest base model for which a custom model is defined.
{: note}

## Audio transmission
{: #transmission}

*With the WebSocket interface,* audio data is always streamed to the service over the connection. You can pass data through the socket all at once, or you can pass data for the live-use case as it becomes available. The service returns results as they become available.

*With the synchronous and asynchronous HTTP interfaces,* you can transmit audio to the service in either of the following ways:

-   *One-shot delivery* - You omit the `Transfer-Encoding` header and pass all of the audio data to the service at one time as a single delivery.
-   *Streaming* - You set the `Transfer-Encoding` request header to the value `chunked` and stream the data over a persistent connection. The data does not need to exist fully before you stream it to the service. You can stream the data as it becomes available. The service sends results only when it receives the final chunk, which you indicate by sending an empty chunk.

    For more information about streaming chunked audio with the `Transfer-Encoding` header, see
    -   [en.wikipedia.org/wiki/Chunked_transfer_encoding ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://en.wikipedia.org/wiki/Chunked_transfer_encoding){: new_window}
    -   [Transfer Codings ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://tools.ietf.org/html/rfc7230#section-4){: new_window} in *IETF RFC 7320 HTTP/1.1: Message Syntax and Routing*

With the HTTP interfaces, the service always transcribes the entire audio stream before sending any results. The results can include multiple `transcript` elements to indicate phrases that are separated by pauses. Concatenate the `transcript` elements to assemble the complete transcript.

To preserve system resources when you stream audio data, the service enforces timeouts. The service can terminate a request if

-   The request is initiated but the service receives no audio.
-   The service detects an extended period of silence in the audio.

For more information about timeouts and how to work around them, see [Timeouts](#timeouts).

The batch-processing interface does not support streaming audio data.
{: note}

### Audio transmission example
{: #transmissionExample}

The following example request specifies `chunked` for the `Transfer-Encoding` header to use streaming mode. The connection remains open to accept additional chunks of audio.

```bash
curl -X POST -u "apikey:{apikey}"
--header "Content-Type: audio/flac"
--header "Transfer-Encoding: chunked"
--data-binary @{path}audio-file1.flac
"https://{icp_cluster_host}{:port}/speech-to-text/api/v1/recognize"
```
{: pre}

## Timeouts
{: #timeouts}

To preserve resources when you stream audio data, the service enforces timeouts. If a timeout lapses during a streaming session, the service closes the connection. Your application must recover gracefully from possible closed connections.

When you initiate a streaming session with the HTTP `/v1/recognize` or WebSocket `/v1/recognize` method, the service enforces the following timeouts:

-   A *session timeout* (HTTP status code 408) occurs when the client opens a streaming session but

    -   Sends no audio to the service for 30 seconds
    -   Stops sending audio for 30 seconds before it sends the last chunk to the service
    -   Streams audio at a rate that is much slower than real-time

    Ideally, you would initiate a request to establish a session just before you obtain audio for transcription and maintain it by sending audio at a rate that is close to real time. If the client has sent all data, the service can take more than 30 seconds to generate a response for long audio. In this case, the request does not time out.

    You can keep a session active by sending any audio data, including just silence, before the 30-second session timeout occurs. (You must also set the `inactivity_timeout` parameter to `-1`, as described in the next bullet.) You are charged for the duration of any audio data that you send to the service, including the silence that you send to extend a session.

-   An *inactivity timeout* (HTTP status code 400) occurs when the service is receiving audio from the client but it detects silence (no speech) for 30 seconds. The inactivity timeout is useful, for example, for terminating a session when a user simply walks away from a live microphone. The service uses the timeout to ensure that a session remains active.

    You can override this timeout by specifying a different value for the `inactivity_timeout` parameter. Specify a value of `-1` to set the inactivity timeout to infinity.

To improve usability for long audio, the service avoids HTTP REST inactivity timeouts by sending a space character every 20 seconds in the response JSON object until it completes the transcription. Sending the character keeps the connection alive while recognition is ongoing. (The WebSocket interface is not subject to this type of timeout.)

### Inactivity timeout example
{: #timeoutsExample}

The following example request sets the inactivity timeout to 60 seconds. The client sends an initial file to begin the streaming session.

```bash
curl -X POST -u "apikey:{apikey}"
--header "Transfer-Encoding: chunked"
--header "Content-Type: audio/flac"
--data-binary @{path}audio-file1.flac
"https://{icp_cluster_host}{:port}/speech-to-text/api/v1/recognize?inactivity_timeout=60"
```
{: pre}

## Information security
{: #security}

*Information security* includes features to associate a customer ID with data that is passed to the service with a request. You associate a customer ID with the data by passing the `X-Watson-Metadata` header with the request. If necessary, you can then delete the data by using the `DELETE /v1/user_data` method. For more information, see [Information security](/docs/services/speech-to-text-icp/information-security.html).
