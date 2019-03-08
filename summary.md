---

copyright:
  years: 2018, 2019
lastupdated: "2019-03-07"

subcollection: speech-to-text-icp

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

# Parameter summary
{: #summary}

A summary follows of all of the parameters available for speech recognition. For more information about all methods of the {{site.data.keyword.ibmwatson}} {{site.data.keyword.speechtotextshort}}: Customer Care service, see the [API reference ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://{DomainName}/apidocs/speech-to-text-icp){: new_window}.
{: shortdesc}

Consider the following basic requirements when you make a speech recognition request:

-   Method names are case-sensitive.
-   HTTP request headers are case-insensitive.
-   HTTP and WebSocket query parameters are case-sensitive.
-   JSON field names are case-sensitive.
-   All JSON response content is in the UTF-8 character set.

Also consider the following service-specific requirements:

-   You need to specify only the input audio. All other parameters are optional.
-   If you specify an invalid query parameter or JSON field as part of the input, the response includes a `warnings` field that describes the invalid argument. The request succeeds despite any warnings.

## acoustic_customization_id
{: #summary-acoustic-customization-id}

An optional customization ID for a custom acoustic model that is adapted for the acoustic characteristics of your environment and speakers. By default, no custom model is used. For more information, see [Custom models](/docs/services/speech-to-text-icp/input.html#custom-input).

<table>
  <caption>Table 1. The acoustic_customization_id parameter</caption>
  <tr>
    <th>Availability and usage</th>
    <th style="vertical-align:bottom">Description</th>
  </tr>
  <tr>
    <td style="text-align:left; width:30%">
      **Availability**
    </td>
    <td style="text-align:left">
      Beta for all languages
    </td>
  </tr>
  <tr>
    <td style="text-align:left">
      **WebSocket**
    </td>
    <td style="text-align:left">
      Query parameter of <code>/v1/recognize</code> connection request
    </td>
  </tr>
  <tr>
    <td style="text-align:left">
      **Synchronous HTTP**
    </td>
    <td style="text-align:left">
      Query parameter of <code>POST /v1/recognize</code> method
    </td>
  </tr>
  <tr>
    <td style="text-align:left">
      **Asynchronous HTTP**
    </td>
    <td style="text-align:left">
      Query parameter of <code>POST /v1/recognitions</code> method
    </td>
  </tr>
  <tr>
    <td style="text-align:left">
      **Batch-processing HTTP**
    </td>
    <td style="text-align:left">
      Query parameter of <code>POST /v1/batches</code> method
    </td>
  </tr>
</table>

## base_model_version
{: #summary-base-model-version}

An optional version of a base model. The parameter is intended primarily for use with custom models that are updated for a new base model, but it can be used without a custom model. The default value depends on whether the parameter is used with or without a custom model. For more information, see [Base model version](/docs/services/speech-to-text-icp/input.html#version).

<table>
  <caption>Table 2. The base_model_version parameter</caption>
  <tr>
    <th>Availability and usage</th>
    <th style="vertical-align:bottom">Description</th>
  </tr>
  <tr>
    <td style="text-align:left; width:30%">
      **Availability**
    </td>
    <td style="text-align:left">
      Generally available for all languages
    </td>
  </tr>
  <tr>
    <td style="text-align:left">
      **WebSocket**
    </td>
    <td style="text-align:left">
      Query parameter of <code>/v1/recognize</code> connection request
    </td>
  </tr>
  <tr>
    <td style="text-align:left">
      **Synchronous HTTP**
    </td>
    <td style="text-align:left">
      Query parameter of <code>POST /v1/recognize</code> method
    </td>
  </tr>
  <tr>
    <td style="text-align:left">
      **Asynchronous HTTP**
    </td>
    <td style="text-align:left">
      Query parameter of <code>POST /v1/recognitions</code> method
    </td>
  </tr>
  <tr>
    <td style="text-align:left">
      **Batch-processing HTTP**
    </td>
    <td style="text-align:left">
      Not supported
    </td>
  </tr>
</table>

## Content-Type
{: #summary-content-type}

An optional audio format (MIME type) that specifies the format of the audio data that you pass to the service. The service can automatically detect the format of most audio, so the parameter is optional for most formats. It is required for `audio/basic`, `audio/l16`, and `audio/mulaw`. (For the batch-processing interface, the header must be the value `multipart/form-data`.) For more information, see [Audio formats](/docs/services/speech-to-text-icp/audio-formats.html).

<table>
  <caption>Table 3. The Content-Type parameter</caption>
  <tr>
    <th>Availability and usage</th>
    <th style="vertical-align:bottom">Description</th>
  </tr>
  <tr>
    <td style="text-align:left; width:30%">
      **Availability**
    </td>
    <td style="text-align:left">
      Generally available for all languages
    </td>
  </tr>
  <tr>
    <td style="text-align:left">
      **WebSocket**
    </td>
    <td style="text-align:left">
      <code>content-type</code> parameter of JSON <code>start</code>
      message
    </td>
  </tr>
  <tr>
    <td style="text-align:left">
      **Synchronous HTTP**
    </td>
    <td style="text-align:left">
      Request header of <code>POST /v1/recognize</code> method
    </td>
  </tr>
  <tr>
    <td style="text-align:left">
      **Asynchronous HTTP**
    </td>
    <td style="text-align:left">
      Request header of <code>POST /v1/recognitions</code> method
    </td>
  </tr>
  <tr>
    <td style="text-align:left">
      **Batch-processing HTTP**
    </td>
    <td style="text-align:left">
      Request header of <code>POST /v1/batches</code> method that
      specifies the value <code>multipart/form-data</code>
    </td>
  </tr>
</table>

## customization_weight
{: #summary-customization-weight}

An optional double between 0.0 and 1.0 that indicates the relative weight that the service gives to words from a custom language model versus words from the base vocabulary. The default is 0.3 unless a different weight was specified when the custom language model was trained. For more information, see [Custom models](/docs/services/speech-to-text-icp/input.html#custom-input).

<table>
  <caption>Table 4. The customization_weight parameter</caption>
  <tr>
    <th>Availability and usage</th>
    <th style="vertical-align:bottom">Description</th>
  </tr>
  <tr>
    <td style="text-align:left; width:30%">
      **Availability**
    </td>
    <td style="text-align:left">
      Generally available for all languages
    </td>
  </tr>
  <tr>
    <td style="text-align:left">
      **WebSocket**
    </td>
    <td style="text-align:left">
      Parameter of JSON <code>start</code> message
    </td>
  </tr>
  <tr>
    <td style="text-align:left">
      **Synchronous HTTP**
    </td>
    <td style="text-align:left">
      Query parameter of <code>POST /v1/recognize</code> method
    </td>
  </tr>
  <tr>
    <td style="text-align:left">
      **Asynchronous HTTP**
    </td>
    <td style="text-align:left">
      Query parameter of <code>POST /v1/recognitions</code> method
    </td>
  </tr>
  <tr>
    <td style="text-align:left">
      **Batch-processing HTTP**
    </td>
    <td style="text-align:left">
      Query parameter of <code>POST /v1/batches</code> method
    </td>
  </tr>
</table>

## grammar_name
{: #summary-grammar-name}

An optional string that identifies a grammar that is to be used for speech recognition. The service recognizes only strings that are defined by the grammar. You must specify both the name of the grammar and the customization ID of the custom language model for which the grammar is defined. For more information, see [Grammars](/docs/services/speech-to-text-icp/input.html#grammars-input).

<table>
  <caption>Table 5. The grammar_name parameter</caption>
  <tr>
    <th>Availability and usage</th>
    <th style="vertical-align:bottom">Description</th>
  </tr>
  <tr>
    <td style="text-align:left; width:30%">
      **Availability**
    </td>
    <td style="text-align:left">
      Beta for all languages
    </td>
  </tr>
  <tr>
    <td style="text-align:left">
      **WebSocket**
    </td>
    <td style="text-align:left">
      Parameter of JSON <code>start</code> message
    </td>
  </tr>
  <tr>
    <td style="text-align:left">
      **Synchronous HTTP**
    </td>
    <td style="text-align:left">
      Query parameter of <code>POST /v1/recognize</code> method
    </td>
  </tr>
  <tr>
    <td style="text-align:left">
      **Asynchronous HTTP**
    </td>
    <td style="text-align:left">
      Query parameter of <code>POST /v1/recognitions</code> method
    </td>
  </tr>
  <tr>
    <td style="text-align:left">
      **Batch-processing HTTP**
    </td>
    <td style="text-align:left">
      Not supported
    </td>
  </tr>
</table>

## inactivity_timeout
{: #summary-inactivity-timeout}

An optional integer that specifies the number of seconds for the service's inactivity timeout. Inactivity means that the service detects no speech in streaming audio. The default is 30 seconds. Use `-1` to indicate infinity. For more information, see [Inactivity timeout](/docs/services/speech-to-text-icp/input.html#timeouts-inactivity).

<table>
  <caption>Table 6. The inactivity_timeout parameter</caption>
  <tr>
    <th>Availability and usage</th>
    <th style="vertical-align:bottom">Description</th>
  </tr>
  <tr>
    <td style="text-align:left; width:30%">
      **Availability**
    </td>
    <td style="text-align:left">
      Generally available for all languages
    </td>
  </tr>
  <tr>
    <td style="text-align:left">
      **WebSocket**
    </td>
    <td style="text-align:left">
      Parameter of JSON <code>start</code> message
    </td>
  </tr>
  <tr>
    <td style="text-align:left">
      **Synchronous HTTP**
    </td>
    <td style="text-align:left">
      Query parameter of <code>POST /v1/recognize</code> method
    </td>
  </tr>
  <tr>
    <td style="text-align:left">
      **Asynchronous HTTP**
    </td>
    <td style="text-align:left">
      Query parameter of <code>POST /v1/recognitions</code> method
    </td>
  </tr>
  <tr>
    <td style="text-align:left">
      **Batch-processing HTTP**
    </td>
    <td style="text-align:left">
      Not supported
    </td>
  </tr>
</table>

## interim_results
{: #summary-interim-results}

An optional boolean that directs the service to return intermediate hypotheses that are likely to change before the final transcript. By default (`false`), interim results are not returned. For more information, see [Interim results](/docs/services/speech-to-text-icp/output.html#interim).

<table>
  <caption>Table 7. The interim_results parameter</caption>
  <tr>
    <th>Availability and usage</th>
    <th style="vertical-align:bottom">Description</th>
  </tr>
  <tr>
    <td style="text-align:left; width:30%">
      **Availability**
    </td>
    <td style="text-align:left">
      Generally available for all languages
    </td>
  </tr>
  <tr>
    <td style="text-align:left">
      **WebSocket**
    </td>
    <td style="text-align:left">
      Parameter of JSON <code>start</code> message
    </td>
  </tr>
  <tr>
    <td style="text-align:left">
      **Synchronous HTTP**
    </td>
    <td style="text-align:left">
      Not supported
    </td>
  </tr>
  <tr>
    <td style="text-align:left">
      **Asynchronous HTTP**
    </td>
    <td style="text-align:left">
      Not supported
    </td>
  </tr>
  <tr>
    <td style="text-align:left">
      **Batch-processing HTTP**
    </td>
    <td style="text-align:left">
      Not supported
    </td>
  </tr>
</table>

## keywords
{: #summary-keywords}

An optional array of keyword strings that the service spots in the input audio. By default, keyword spotting is not performed. For more information, see [Keyword spotting](/docs/services/speech-to-text-icp/output.html#keyword_spotting).

<table>
  <caption>Table 8. The keywords parameter</caption>
  <tr>
    <th>Availability and usage</th>
    <th style="vertical-align:bottom">Description</th>
  </tr>
  <tr>
    <td style="text-align:left; width:30%">
      **Availability**
    </td>
    <td style="text-align:left">
      Generally available for all languages
    </td>
  </tr>
  <tr>
    <td style="text-align:left">
      **WebSocket**
    </td>
    <td style="text-align:left">
      Parameter of JSON <code>start</code> message
    </td>
  </tr>
  <tr>
    <td style="text-align:left">
      **Synchronous HTTP**
    </td>
    <td style="text-align:left">
      Query parameter of <code>POST /v1/recognize</code> method
    </td>
  </tr>
  <tr>
    <td style="text-align:left">
      **Asynchronous HTTP**
    </td>
    <td style="text-align:left">
      Query parameter of <code>POST /v1/recognitions</code> method
    </td>
  </tr>
  <tr>
    <td style="text-align:left">
      **Batch-processing HTTP**
    </td>
    <td style="text-align:left">
      Not supported
    </td>
  </tr>
</table>

## keywords_threshold
{: #summary-keywords-threshold}

An optional double between 0.0 and 1.0 that indicates the minimum threshold for a positive keyword match. By default, keyword spotting is not performed. For more information, see [Keyword spotting](/docs/services/speech-to-text-icp/output.html#keyword_spotting).

<table>
  <caption>Table 9. The keywords_threshold parameter</caption>
  <tr>
    <th>Availability and usage</th>
    <th style="vertical-align:bottom">Description</th>
  </tr>
  <tr>
    <td style="text-align:left; width:30%">
      **Availability**
    </td>
    <td style="text-align:left">
      Generally available for all languages
    </td>
  </tr>
  <tr>
    <td style="text-align:left">
      **WebSocket**
    </td>
    <td style="text-align:left">
      Parameter of JSON <code>start</code> message
    </td>
  </tr>
  <tr>
    <td style="text-align:left">
      **Synchronous HTTP**
    </td>
    <td style="text-align:left">
      Query parameter of <code>POST /v1/recognize</code> method
    </td>
  </tr>
  <tr>
    <td style="text-align:left">
      **Asynchronous HTTP**
    </td>
    <td style="text-align:left">
      Query parameter of <code>POST /v1/recognitions</code> method
    </td>
  </tr>
  <tr>
    <td style="text-align:left">
      **Batch-processing HTTP**
    </td>
    <td style="text-align:left">
      Not supported
    </td>
  </tr>
</table>

## language_customization_id
{: #summary-language-customization-id}

An optional customization ID for a custom language model that includes terminology from your domain. By default, no custom model is used. For more information, see [Custom models](/docs/services/speech-to-text-icp/input.html#custom-input).

<table>
  <caption>Table 10. The language_customization_id parameter</caption>
  <tr>
    <th>Availability and usage</th>
    <th style="vertical-align:bottom">Description</th>
  </tr>
  <tr>
    <td style="text-align:left; width:30%">
      **Availability**
    </td>
    <td style="text-align:left">
      Generally available for all languages
    </td>
  </tr>
  <tr>
    <td style="text-align:left">
      **WebSocket**
    </td>
    <td style="text-align:left">
      Query parameter of <code>/v1/recognize</code> connection request
    </td>
  </tr>
  <tr>
    <td style="text-align:left">
      **Synchronous HTTP**
    </td>
    <td style="text-align:left">
      Query parameter of <code>POST /v1/recognize</code> method
    </td>
  </tr>
  <tr>
    <td style="text-align:left">
      **Asynchronous HTTP**
    </td>
    <td style="text-align:left">
      Query parameter of <code>POST /v1/recognitions</code> method
    </td>
  </tr>
  <tr>
    <td style="text-align:left">
      **Batch-processing HTTP**
    </td>
    <td style="text-align:left">
      Query parameter of <code>POST /v1/batches</code> method
    </td>
  </tr>
</table>

## max_alternatives
{: #summary-max-alternatives}

An optional integer that specifies the maximum number of alternative hypotheses that the service returns. By default, the service returns a single final hypothesis. For more information, see [Maximum alternatives](/docs/services/speech-to-text-icp/output.html#max_alternatives).

<table>
  <caption>Table 11. The max_alternatives parameter</caption>
  <tr>
    <th>Availability and usage</th>
    <th style="vertical-align:bottom">Description</th>
  </tr>
  <tr>
    <td style="text-align:left; width:30%">
      **Availability**
    </td>
    <td style="text-align:left">
      Generally available for all languages
    </td>
  </tr>
  <tr>
    <td style="text-align:left">
      **WebSocket**
    </td>
    <td style="text-align:left">
      Parameter of JSON <code>start</code> message
    </td>
  </tr>
  <tr>
    <td style="text-align:left">
      **Synchronous HTTP**
    </td>
    <td style="text-align:left">
      Query parameter of <code>POST /v1/recognize</code> method
    </td>
  </tr>
  <tr>
    <td style="text-align:left">
      **Asynchronous HTTP**
    </td>
    <td style="text-align:left">
      Query parameter of <code>POST /v1/recognitions</code> method
    </td>
  </tr>
  <tr>
    <td style="text-align:left">
      **Batch-processing HTTP**
    </td>
    <td style="text-align:left">
      Not supported
    </td>
  </tr>
</table>

## model
{: #summary-model}

An optional model that specifies the language in which the audio is spoken and the rate at which it was sampled: broadband or narrowband. By default, `en-US_BroadbandModel` is used. For more information, see [Languages and models](/docs/services/speech-to-text-icp/models.html).

<table>
  <caption>Table 12. The model parameter</caption>
  <tr>
    <th>Availability and usage</th>
    <th style="vertical-align:bottom">Description</th>
  </tr>
  <tr>
    <td style="text-align:left; width:30%">
      **Availability**
    </td>
    <td style="text-align:left">
      Generally available for all languages
    </td>
  </tr>
  <tr>
    <td style="text-align:left">
      **WebSocket**
    </td>
    <td style="text-align:left">
      Query parameter of <code>/v1/recognize</code> connection request
    </td>
  </tr>
  <tr>
    <td style="text-align:left">
      **Synchronous HTTP**
    </td>
    <td style="text-align:left">
      Query parameter of <code>POST /v1/recognize</code> method
    </td>
  </tr>
  <tr>
    <td style="text-align:left">
      **Asynchronous HTTP**
    </td>
    <td style="text-align:left">
      Query parameter of <code>POST /v1/recognitions</code> method
    </td>
  </tr>
  <tr>
    <td style="text-align:left">
      **Batch-processing HTTP**
    </td>
    <td style="text-align:left">
      Query parameter of <code>POST /v1/batches</code> method
    </td>
  </tr>
</table>

## profanity_filter
{: #summary-profanity-filter}

An optional boolean that indicates whether the service censors profanity from a transcript. By default (`true`), profanity is filtered from the transcript. For more information, see [Profanity filtering](/docs/services/speech-to-text-icp/output.html#profanity_filter).

<table>
  <caption>Table 13. The profanity_filter parameter</caption>
  <tr>
    <th>Availability and usage</th>
    <th style="vertical-align:bottom">Description</th>
  </tr>
  <tr>
    <td style="text-align:left; width:30%">
      **Availability**
    </td>
    <td style="text-align:left">
      Generally available for US English
    </td>
  </tr>
  <tr>
    <td style="text-align:left">
      **WebSocket**
    </td>
    <td style="text-align:left">
      Parameter of JSON <code>start</code> message
    </td>
  </tr>
  <tr>
    <td style="text-align:left">
      **Synchronous HTTP**
    </td>
    <td style="text-align:left">
      Query parameter of <code>POST /v1/recognize</code> method
    </td>
  </tr>
  <tr>
    <td style="text-align:left">
      **Asynchronous HTTP**
    </td>
    <td style="text-align:left">
      Query parameter of <code>POST /v1/recognitions</code> method
    </td>
  </tr>
  <tr>
    <td style="text-align:left">
      **Batch-processing HTTP**
    </td>
    <td style="text-align:left">
      Query parameter of <code>POST /v1/batches</code> method
    </td>
  </tr>
</table>

## redaction
{: #summary-redaction}

An optional boolean that indicates whether the service redacts numeric data with three or more consecutive digits from a transcript. If you set the `redaction` parameter to `true`, the service automatically forces the `smart_formatting` parameter to be `true`. By default (`false`), numeric data is not redacted. For more information, see [Numeric redaction](/docs/services/speech-to-text-icp/output.html#redaction).

<table>
  <caption>Table 14. The redaction parameter</caption>
  <tr>
    <th>Availability and usage</th>
    <th style="vertical-align:bottom">Description</th>
  </tr>
  <tr>
    <td style="text-align:left; width:30%">
      **Availability**
    </td>
    <td style="text-align:left">
      Beta for US English, Japanese, and Korean
    </td>
  </tr>
  <tr>
    <td style="text-align:left">
      **WebSocket**
    </td>
    <td style="text-align:left">
      Parameter of JSON <code>start</code> message
    </td>
  </tr>
  <tr>
    <td style="text-align:left">
      **Synchronous HTTP**
    </td>
    <td style="text-align:left">
      Query parameter of <code>POST /v1/recognize</code> method
    </td>
  </tr>
  <tr>
    <td style="text-align:left">
      **Asynchronous HTTP**
    </td>
    <td style="text-align:left">
      Query parameter of <code>POST /v1/recognitions</code> method
    </td>
  </tr>
  <tr>
    <td style="text-align:left">
      **Batch-processing HTTP**
    </td>
    <td style="text-align:left">
      Query parameter of <code>POST /v1/batches</code> method
    </td>
  </tr>
</table>

## smart_formatting
{: #summary-smart-formatting}

An optional boolean that indicates whether the service converts dates, times, numbers, currency, and similar values into more conventional representations in the final transcript. For US English, the feature also converts certain keyword phrases into punctuation symbols. By default (`false`), smart formatting is not performed. For more information, see [Smart formatting](/docs/services/speech-to-text-icp/output.html#smart_formatting).

<table>
  <caption>Table 15. The smart_formatting parameter</caption>
  <tr>
    <th>Availability and usage</th>
    <th style="vertical-align:bottom">Description</th>
  </tr>
  <tr>
    <td style="text-align:left; width:30%">
      **Availability**
    </td>
    <td style="text-align:left">
      Beta for US English, Japanese, and Spanish
    </td>
  </tr>
  <tr>
    <td style="text-align:left">
      **WebSocket**
    </td>
    <td style="text-align:left">
      Parameter of JSON <code>start</code> message
    </td>
  </tr>
  <tr>
    <td style="text-align:left">
      **Synchronous HTTP**
    </td>
    <td style="text-align:left">
      Query parameter of <code>POST /v1/recognize</code> method
    </td>
  </tr>
  <tr>
    <td style="text-align:left">
      **Asynchronous HTTP**
    </td>
    <td style="text-align:left">
      Query parameter of <code>POST /v1/recognitions</code> method
    </td>
  </tr>
  <tr>
    <td style="text-align:left">
      **Batch-processing HTTP**
    </td>
    <td style="text-align:left">
      Query parameter of <code>POST /v1/batches</code> method
    </td>
  </tr>
</table>

## speaker_labels
{: #summary-speaker-labels}

An optional boolean that indicates whether the service identifies which individuals spoke which words in a multi-participant exchange. If you set the `speaker_labels` parameter to `true`, the service automatically forces the `timestamps` parameter to be `true`. By default (`false`), speaker labels are not returned. For more information, see [Speaker labels](/docs/services/speech-to-text-icp/output.html#speaker_labels).

<table>
  <caption>Table 16. The speaker_labels parameter</caption>
  <tr>
    <th>Availability and usage</th>
    <th style="vertical-align:bottom">Description</th>
  </tr>
  <tr>
    <td style="text-align:left; width:30%">
      **Availability**
    </td>
    <td style="text-align:left">
      Beta for US English, Japanese, and Spanish
    </td>
  </tr>
  <tr>
    <td style="text-align:left">
      **WebSocket**
    </td>
    <td style="text-align:left">
      Parameter of JSON <code>start</code> message
    </td>
  </tr>
  <tr>
    <td style="text-align:left">
      **Synchronous HTTP**
    </td>
    <td style="text-align:left">
      Query parameter of <code>POST /v1/recognize</code> method
    </td>
  </tr>
  <tr>
    <td style="text-align:left">
      **Asynchronous HTTP**
    </td>
    <td style="text-align:left">
      Query parameter of <code>POST /v1/recognitions</code> method
    </td>
  </tr>
  <tr>
    <td style="text-align:left">
      **Batch-processing HTTP**
    </td>
    <td style="text-align:left">
      Query parameter of <code>POST /v1/batches</code> method<br/>
      Always enabled (`true`) for the current release
    </td>
  </tr>
</table>

## speech_analytics
{: #summary-speech-analytics}

An optional boolean that indicates whether the service is to produce speech analytics results for the input audio. The service further analyzes its speech recognition results to produce detailed information about the topics of overall conversation and the tone, sentiment, keywords, and topics of individual speakers. If you set the `speech_analytics` parameter to `true`, the service automatically forces the `speaker_labels` parameter to be `true`. By default (`false`), speech analytics are not returned. For more information, see [Speech analytics](/docs/services/speech-to-text-icp/analytics.html).

<table>
  <caption>Table 17. The speech_analytics parameter</caption>
  <tr>
    <th>Availability and usage</th>
    <th style="vertical-align:bottom">Description</th>
  </tr>
  <tr>
    <td style="text-align:left; width:30%">
      **Availability**
    </td>
    <td style="text-align:left">
      Generally available for US English
    </td>
  </tr>
  <tr>
    <td style="text-align:left">
      **WebSocket**
    </td>
    <td style="text-align:left">
      Not supported
    </td>
  </tr>
  <tr>
    <td style="text-align:left">
      **Synchronous HTTP**
    </td>
    <td style="text-align:left">
      Not supported
    </td>
  </tr>
  <tr>
    <td style="text-align:left">
      **Asynchronous HTTP**
    </td>
    <td style="text-align:left">
      Not supported
    </td>
  </tr>
  <tr>
    <td style="text-align:left">
      **Batch-processing HTTP**
    </td>
    <td style="text-align:left">
      Query parameter of <code>POST /v1/batches</code> method
    </td>
  </tr>
</table>

## timestamps
{: #summary-timestamps}

An optional boolean that indicates whether the service produces timestamps for the words of the transcript. By default (`false`), timestamps are not returned. For more information, see [Word timestamps](/docs/services/speech-to-text-icp/output.html#word_timestamps).

<table>
  <caption>Table 18. The timestamps parameter</caption>
  <tr>
    <th>Availability and usage</th>
    <th style="vertical-align:bottom">Description</th>
  </tr>
  <tr>
    <td style="text-align:left; width:30%">
      **Availability**
    </td>
    <td style="text-align:left">
      Generally available for all languages
    </td>
  </tr>
  <tr>
    <td style="text-align:left">
      **WebSocket**
    </td>
    <td style="text-align:left">
      Parameter of JSON <code>start</code> message
    </td>
  </tr>
  <tr>
    <td style="text-align:left">
      **Synchronous HTTP**
    </td>
    <td style="text-align:left">
      Query parameter of <code>POST /v1/recognize</code> method
    </td>
  </tr>
  <tr>
    <td style="text-align:left">
      **Asynchronous HTTP**
    </td>
    <td style="text-align:left">
      Query parameter of <code>POST /v1/recognitions</code> method
    </td>
  </tr>
  <tr>
    <td style="text-align:left">
      **Batch-processing HTTP**
    </td>
    <td style="text-align:left">
      Query parameter of <code>POST /v1/batches</code> method<br/>
      Always enabled (`true`) for the current release
    </td>
  </tr>
</table>

## Transfer-Encoding
{: #summary-transfer-encoding}

An optional value of `chunked` that causes the audio to be streamed to the service. By default, audio is sent all at once as a one-shot delivery. For more information, see [Audio transmission](/docs/services/speech-to-text-icp/input.html#transmission).

<table>
  <caption>Table 19. The Transfer-Encoding parameter</caption>
  <tr>
    <th>Availability and usage</th>
    <th style="vertical-align:bottom">Description</th>
  </tr>
  <tr>
    <td style="text-align:left; width:30%">
      **Availability**
    </td>
    <td style="text-align:left">
      Generally available for all languages
    </td>
  </tr>
  <tr>
    <td style="text-align:left">
      **WebSocket**
    </td>
    <td style="text-align:left">
      Not applicable; always streamed
    </td>
  </tr>
  <tr>
    <td style="text-align:left">
      **Synchronous HTTP**
    </td>
    <td style="text-align:left">
      Request header of <code>POST /v1/recognize</code> method
    </td>
  </tr>
  <tr>
    <td style="text-align:left">
      **Asynchronous HTTP**
    </td>
    <td style="text-align:left">
      Request header of <code>POST /v1/recognitions</code> method
    </td>
  </tr>
  <tr>
    <td style="text-align:left">
      **Batch-processing HTTP**
    </td>
    <td style="text-align:left">
      Not applicable; never streamed
    </td>
  </tr>
</table>

## watson-token
{: #summary-watson-token}

An optional authentication token that makes authenticated requests to the service without embedding your service credentials in every call. By default, service credentials must be passed with each request.

You cannot use JavaScript to call the WebSocket interface from a browser. The `watson-token` parameter does not accept API keys. For more information about working around this limitation, see the [Known limitations](/docs/services/speech-to-text-icp/release-notes.html#limitations) in the release notes.
{: important}

<table>
  <caption>Table 20. The watson-token parameter</caption>
  <tr>
    <th>Availability and usage</th>
    <th style="vertical-align:bottom">Description</th>
  </tr>
  <tr>
    <td style="text-align:left; width:30%">
      **Availability**
    </td>
    <td style="text-align:left">
      Generally available for all languages
    </td>
  </tr>
  <tr>
    <td style="text-align:left">
      **WebSocket**
    </td>
    <td style="text-align:left">
      Query parameter of <code>/v1/recognize</code> connection request
    </td>
  </tr>
  <tr>
    <td style="text-align:left">
      **Synchronous HTTP**
    </td>
    <td style="text-align:left">
      Not supported
    </td>
  </tr>
  <tr>
    <td style="text-align:left">
      **Asynchronous HTTP**
    </td>
    <td style="text-align:left">
      Not supported
    </td>
  </tr>
  <tr>
    <td style="text-align:left">
      **Batch-processing HTTP**
    </td>
    <td style="text-align:left">
      Not supported
    </td>
  </tr>
</table>

## word_alternatives_threshold
{: #summary-word-alternatives-threshold}

An optional double between 0.0 and 1.0 that specifies the threshold at which the service reports acoustically similar alternatives for words of the input audio. By default, word alternatives are not returned. For more information, see [Word alternatives](/docs/services/speech-to-text-icp/output.html#word_alternatives).

<table>
  <caption>Table 21. The word_alternatives_threshold parameter</caption>
  <tr>
    <th>Availability and usage</th>
    <th style="vertical-align:bottom">Description</th>
  </tr>
  <tr>
    <td style="text-align:left; width:30%">
      **Availability**
    </td>
    <td style="text-align:left">
      Generally available for all languages
    </td>
  </tr>
  <tr>
    <td style="text-align:left">
      **WebSocket**
    </td>
    <td style="text-align:left">
      Parameter of JSON <code>start</code> message
    </td>
  </tr>
  <tr>
    <td style="text-align:left">
      **Synchronous HTTP**
    </td>
    <td style="text-align:left">
      Query parameter of <code>POST /v1/recognize</code> method
    </td>
  </tr>
  <tr>
    <td style="text-align:left">
      **Asynchronous HTTP**
    </td>
    <td style="text-align:left">
      Query parameter of <code>POST /v1/recognitions</code> method
    </td>
  </tr>
  <tr>
    <td style="text-align:left">
      **Batch-processing HTTP**
    </td>
    <td style="text-align:left">
      Not supported
    </td>
  </tr>
</table>

## word_confidence
{: #summary-word-confidence}

An optional boolean that indicates whether the service provides confidence measures for the words of the transcript. By default (`false`), word confidence measures are not returned. For more information, see [Word confidence](/docs/services/speech-to-text-icp/output.html#word_confidence).

<table>
  <caption>Table 22. The word_confidence parameter</caption>
  <tr>
    <th>Availability and usage</th>
    <th style="vertical-align:bottom">Description</th>
  </tr>
  <tr>
    <td style="text-align:left; width:30%">
      **Availability**
    </td>
    <td style="text-align:left">
      Generally available for all languages
    </td>
  </tr>
  <tr>
    <td style="text-align:left">
      **WebSocket**
    </td>
    <td style="text-align:left">
      Parameter of JSON <code>start</code> message
    </td>
  </tr>
  <tr>
    <td style="text-align:left">
      **Synchronous HTTP**
    </td>
    <td style="text-align:left">
      Query parameter of <code>POST /v1/recognize</code> method
    </td>
  </tr>
  <tr>
    <td style="text-align:left">
      **Asynchronous HTTP**
    </td>
    <td style="text-align:left">
      Query parameter of <code>POST /v1/recognitions</code> method
    </td>
  </tr>
  <tr>
    <td style="text-align:left">
      **Batch-processing HTTP**
    </td>
    <td style="text-align:left">
      Query parameter of <code>POST /v1/batches</code> method
    </td>
  </tr>
</table>

## X-Watson-Metadata
{: #summary-x-watson-metadata}

An optional string that associates a customer ID with data that is passed for recognition requests. The parameter accepts the argument `customer_id={id}`. By default, no customer ID is associated with the data. For more information, see [Information security](/docs/services/speech-to-text-icp/information-security.html).

<table>
  <caption>Table 23. The X-Watson-Metadata parameter</caption>
  <tr>
    <th>Availability and usage</th>
    <th style="vertical-align:bottom">Description</th>
  </tr>
  <tr>
    <td style="text-align:left; width:30%">
      **Availability**
    </td>
    <td style="text-align:left">
      Generally available for all languages
    </td>
  </tr>
  <tr>
    <td style="text-align:left">
      **WebSocket**
    </td>
    <td style="text-align:left">
      <code>x-watson-metadata</code> query parameter of
      <code>/v1/recognize</code> connection request (You must URL-encode
      the argument, for example, `customer_id%3dmy_customer_ID`.)
    </td>
  </tr>
  <tr>
    <td style="text-align:left">
      **Synchronous HTTP**
    </td>
    <td style="text-align:left">
      Request header of POST <code>/v1/recognize</code> method
    </td>
  </tr>
  <tr>
    <td style="text-align:left">
      **Asynchronous HTTP**
    </td>
    <td style="text-align:left">
      Request header of <code>POST /v1/register_callback</code> and
      <code>POST /v1/recognitions</code> method
    </td>
  </tr>
  <tr>
    <td style="text-align:left">
      **Batch-processing HTTP**
    </td>
    <td style="text-align:left">
      Request header of POST <code>/v1/batches</code> method
    </td>
  </tr>
</table>
