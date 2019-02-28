---

copyright:
  years: 2018, 2019
lastupdated: "2019-02-28"

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

# Overview for developers
{: #developerOverview}

You can access the capabilities of {{site.data.keyword.ibmwatson}} {{site.data.keyword.speechtotextshort}}: Customer Care by using a WebSocket interface and by using synchronous, asynchronous, or batch-processing HTTP Representational State Transfer (REST) interfaces. You can also customize the service's language models to suit your domain and environment. SDKs are available to simplify application development in many programming languages.
{: shortdesc}

## Programming with the service
{: #programming}

[Making a recognition request](/docs/services/speech-to-text-icp/basic-request.html) shows you how to request basic transcription with each of the service's programming interfaces:

-   [The WebSocket interface](/docs/services/speech-to-text-icp/websockets.html) offers an efficient, low-latency, and high-throughput implementation over a full-duplex connection.
-   [The synchronous HTTP interface](/docs/services/speech-to-text-icp/http.html) provides a basic interface to transcribe audio with blocking requests.
-   [The asynchronous HTTP interface](/docs/services/speech-to-text-icp/async.html) provides a non-blocking interface that lets you register a callback URL to receive notifications or to poll the service for job status and results.
-   [The batch-processing HTTP interface](/docs/services/speech-to-text-icp/batch.html) provides a means of transcribing multiple audio files with a single request. In addition to speech recognition, the interface provides [speech analytics](/docs/services/speech-to-text-icp/analytics.html) to learn detailed information about conversations and their individual speakers.

The interfaces provide similar speech recognition capabilities, but you might specify the same parameter as a request header, a query parameter, or a parameter of a JSON object depending on the interface that you use. The batch-processing interface requires a Cloud Object Storage (COS) server for passing audio files to the service and for obtaining results from the service. Batch processing currently supports a limited set of speech recognition parameters.

The WebSocket and synchronous HTTP interfaces accept a maximum of 100 MB of audio data with a single request. The batch-processing interface accepts a maximum of 100 MB of audio for any file of a request. The asynchronous HTTP interface accepts a maximum of 1 GB of audio data with a request.

-   For information about making requests with each of the {{site.data.keyword.speechtotextshort}}: Customer Care interfaces, see [Making requests to the service](/docs/services/speech-to-text-icp/making-requests.html).
-   For examples of basic speech recognition requests with each of the service's interfaces, see [Making a recognition request](/docs/services/speech-to-text-icp/basic-request.html).
-   For descriptions of all available speech recognition parameters, see the [Parameter summary](/docs/services/speech-to-text-icp/summary.html).
-   For descriptions of all methods and their parameters, along with examples, see the [API reference ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://{DomainName}/apidocs/speech-to-text-icp){: new_window}.

## Advantages of the WebSocket interface
{: #advantages}

The WebSocket interface has a number of advantages over the HTTP interface:

-   The WebSocket interface provides a single-socket, full-duplex communication channel. The interface lets the client send requests and audio to the service and receive results over a single connection in an asynchronous fashion.
-   It provides a much simpler and more powerful programming experience. The service sends event-driven responses to the client's messages, eliminating the need for the client to poll the server.
-   It allows you to establish and use a single authenticated connection indefinitely. The HTTP interfaces require you to authenticate each call to the service.
-   It reduces latency. Recognition results arrive faster because the service sends them directly to the client. The HTTP interface requires four distinct requests and connections to achieve the same results.
-   It reduces network utilization. The WebSocket protocol is lightweight. It requires only a single connection to perform live-speech recognition.
-   It enables audio to be streamed directly from browsers (HTML5 WebSocket clients) to the service.

## Customizing the service
{: #customizing}

[The customization interface](/docs/services/speech-to-text-icp/custom.html) lets you create custom models to improve the service's speech recognition capabilities:

-   [Custom language models](/docs/services/speech-to-text-icp/language-create.html) let you define domain-specific words for a base model. Custom language models expand the service's base vocabulary with terminology specific to domains such as medicine and law.
-   [Custom acoustic models](/docs/services/speech-to-text-icp/acoustic-create.html) let you adapt a base model for the acoustic characteristics of your environment and speakers. Custom acoustic models improve the service's ability to recognize speech for specific acoustic characteristics.
-   [Grammars](/docs/services/speech-to-text-icp/grammar.html) let you restrict the phrases that the service can recognize to those defined in the grammar's rules. By limiting the search space for valid strings, the service can deliver results faster and more accurately. Grammars are supported with custom language models.

You can use a custom language model, a custom acoustic model, or both for speech recognition with any of the service's interfaces. (The batch-processing interface does not currently support grammars.)

## CORS support
{: #cors}

The service supports Cross-Origin Resource Sharing (CORS). By using CORS, web pages can request resources directly from a foreign domain. CORS circumvents the same-origin security policy, which otherwise prevents such requests. Because the service supports CORS, a web page can communicate directly with the service without passing the request through the web server that hosts the page.

For instance, a web page that is loaded from a server in {{site.data.keyword.Bluemix_notm}} can call the customization API directly, bypassing the {{site.data.keyword.Bluemix_notm}} server. For more information, see [enable-cors.org ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://enable-cors.org/){: new_window}.

## Using Software Development Kits
{: #sdks}

SDKs are available for the {{site.data.keyword.speechtotextshort}}: Customer Care service to simplify the development of speech applications. {{site.data.keyword.ibmwatson}} SDKs are available for many popular programming languages and platforms.

-   For a complete list of SDKs and links to the SDKs on GitHub, see [Using SDKs](/docs/services/watson/getting-started-sdks.html).
-   For detailed information about all methods of the Node, Java&trade;, Python, Ruby, Swift, and Go SDKs for the {{site.data.keyword.speechtotextshort}}: Customer Care service, see the [API reference ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://{DomainName}/apidocs/speech-to-text-icp){: new_window}.
