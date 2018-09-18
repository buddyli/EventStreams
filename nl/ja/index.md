---

copyright:
  years: 2015, 2018
lastupdated: "2018-07-13"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Message Hub入門 
{: #messagehub}

{{site.data.keyword.messagehub}} を開始し、メッセージの送受信を開始するには、Java™ サンプルを使用できます。 このサンプルは、プロデューサーがトピックを使用してメッセージをコンシューマーに送信する方法を示します。 同じサンプル・プログラムが、メッセージのコンシュームとメッセージのプロデュースに使用されます。

{{site.data.keyword.messagehub}} がどのように機能するのかについて詳しくは、[{{site.data.keyword.messagehub}} について](/docs/services/MessageHub/messagehub010.html)を参照してください。

Node.js および Python のサンプルを含め、他の {{site.data.keyword.messagehub}} サンプルにアクセスするには、[{{site.data.keyword.messagehub}} サンプル ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://github.com/ibm-messaging/message-hub-samples){:new_window} を参照してください。

<!-- 11/01/18 - Karen - removing diagram as requested by James
![Java sample overview diagram](getting_started_sample.gif "Overview diagram of Java sample showing the flow of messages.")
-->

以下のステップを実行してください。
{: #getting_started_steps}
 
1. {{site.data.keyword.messagehub}} サービス・インスタンスを作成します。

  a. Web ユーザー・インターフェースを使用して {{site.data.keyword.Bluemix_notm}} にログインします。 
  
  b. **「カタログ」** をクリックします。
  
  c. **「アプリケーション・サービス」**セクションで、**{{site.data.keyword.messagehub}}「標準プラン」**をクリックします。 {{site.data.keyword.messagehub}} サービス・インスタンス・ページが開きます。
  
  d. **「接続」**メニューでサービスを未結合のままにし、サービス名と資格情報を入力します。 デフォルト値を使用することができます。
  
  e. **「作成」**をクリックします。

2. 前提条件である以下の製品がまだインストールされていない場合はインストールします。

    * [git ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://git-scm.com/){:new_window}
	* [Gradle ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://gradle.org/){:new_window}
    * Java 8 以上
 
3. コマンド・ラインから次のコマンドを実行して、message-hub-samples git リポジトリーを複製します。

    <pre class="pre">
    git clone https://github.com/ibm-messaging/message-hub-samples.git
    </pre>
	{: codeblock}

4. 次のコマンドを実行して、ディレクトリーを java console sample に変更します。

    <pre class="pre">
    cd message-hub-samples/kafka-java-console-sample
    </pre>
	{: codeblock}

5. 次のビルド・コマンドを実行します。

    <pre class="pre">
    gradle clean && gradle build
    </pre>
	{: codeblock}

6. 次のコマンドを実行して、ご使用のコンソールでコンシューマーを開始します。

    <pre class="pre">java -jar build/libs/kafka-java-console-sample-2.0.jar 
	<var class="keyword varname">kafka_brokers_sasl</var> <var class="keyword varname">kafka_admin_url</var> token<var class="keyword varname">:api_key</var> -consumer</pre>
    {: codeblock}
    
    このサンプルでは、`kafka-java-console-sample-topic` という名前のトピックが使用されます。 このトピックがまだ存在していない場合、このサンプルは {{site.data.keyword.messagehub}} 管理 API を使用して作成します。 このサンプルは、メッセージの送受信には Apache Kafka Java API を使用します。

    *kafka_brokers_sasl*、*kafka_admin_url*、および *api_key* の値を調べるには、{{site.data.keyword.Bluemix_notm}} で {{site.data.keyword.messagehub}} インスタンスに移動し、**「サービス資格情報」**タブに進み、使用したい**資格情報**を選択します。
	
	ユーザー名として <code>token</code> を、パスワードとして <var class="keyword varname">api_key</var> を指定します。<code>token</code> と <var class="keyword varname">api_key</var> はコロンで区切ってください。
    
	**重要:** *kafka_brokers_sasl* は、単一ストリングでなければならず、引用符で囲む必要があります。 以下に例を示します。

    <pre class="pre">
    "host1:port1,host2:port2"
    </pre>
	{: codeblock}

    選択した**資格情報**にリストされているすべての Kafka ホストを使用することをお勧めします。

7. 次のコマンドを実行して、ご使用のコンソールでプロデューサーを開始します。
   
    <pre class="pre">java -jar build/libs/kafka-java-console-sample-2.0.jar 
	<var class="keyword varname">kafka_brokers_sasl</var> <var class="keyword varname">kafka_admin_url</var> token<var class="keyword varname">:api_key</var> -producer</pre>
 {: codeblock}
  
8. これで、プロデューサーによって送信されたメッセージがコンシューマーで表示されるようになります。 次に出力例の一部を示します。

    ```
    [2018-07-02 14:54:50,788] INFO Running in local mode. (com.messagehub.samples.MessageHubConsoleSample)
    [2018-07-02 14:54:50,789] INFO Kafka Endpoints: kafka-0.mh-zarjkgtnzzspbkfrkqgdhmq.us-south.containers.appdomain.cloud:9093,kafka-1.mh-zarjkgtnzzspbkfrkqgdhmq.us-south.containers.appdomain.cloud:9093,kafka-2.mh-zarjkgtnzzspbkfrkqgdhmq.us-south.containers.appdomain.cloud:9093 (com.messagehub.samples.MessageHubConsoleSample)
    [2018-07-02 14:54:50,789] INFO Admin REST Endpoint: https://mh-zarjkgtnzzspbkfrkqgdhmq.us-south.containers.appdomain.cloud (com.messagehub.samples.MessageHubConsoleSample)
    [2018-07-02 14:54:50,789] INFO Creating the topic kafka-java-console-sample-topic (com.messagehub.samples.MessageHubConsoleSample)
    [2018-07-02 14:54:52,680] INFO Admin REST response : (com.messagehub.samples.MessageHubConsoleSample)
    [2018-07-02 14:54:53,351] INFO Admin REST Listing Topics: [{"name":"kafka-java-console-sample-topic","partitions":1,"retentionMs":86400000,"cleanupPolicy":"delete"},{"name":"__consumer_offsets","partitions":50,"retentionMs":86400000,"cleanupPolicy":"compact"}] (com.messagehub.samples.MessageHubConsoleSample)
    [2018-07-02 14:54:55,126] INFO [Partition(topic = kafka-java-console-sample-topic, partition = 0, leader = 0, replicas = [0,2,1], isr = [0,2,1], offlineReplicas = [])] (com.messagehub.samples.ConsumerRunnable)
    [2018-07-02 14:54:55,126] INFO class com.messagehub.samples.ConsumerRunnable is starting. (com.messagehub.samples.ConsumerRunnable)
    [2018-07-02 14:54:56,328] INFO [Partition(topic = kafka-java-console-sample-topic, partition = 0, leader = 0, replicas = [0,2,1], isr = [0,2,1], offlineReplicas = [])] (com.messagehub.samples.ProducerRunnable)
    [2018-07-02 14:54:56,328] INFO MessageHubConsoleSample will run until interrupted. (com.messagehub.samples.MessageHubConsoleSample)
    [2018-07-02 14:54:56,328] INFO class com.messagehub.samples.ProducerRunnable is starting. (com.messagehub.samples.ProducerRunnable)
    [2018-07-02 14:54:57,514] INFO Message produced, offset: 0 (com.messagehub.samples.ProducerRunnable)
    [2018-07-02 14:54:59,652] INFO Message produced, offset: 1 (com.messagehub.samples.ProducerRunnable)
    [2018-07-02 14:55:00,671] INFO No messages consumed (com.messagehub.samples.ConsumerRunnable)
    [2018-07-02 14:55:01,788] INFO Message produced, offset: 2 (com.messagehub.samples.ProducerRunnable)
    [2018-07-02 14:55:01,797] INFO Message consumed: ConsumerRecord(topic = kafka-java-console-sample-topic, partition = 0, offset = 2, CreateTime = 1530539701655, serialized key size = 3, serialized value size = 25, headers = RecordHeaders(headers = [], isReadOnly = false), key = key, value = This is a test message #2) (com.messagehub.samples.ConsumerRunnable)
    [2018-07-02 14:55:03,921] INFO Message consumed: ConsumerRecord(topic = kafka-java-console-sample-topic, partition = 0, offset = 3, CreateTime = 1530539703789, serialized key size = 3, serialized value size = 25, headers = RecordHeaders(headers = [], isReadOnly = false), key = key, value = This is a test message #3) (com.messagehub.samples.ConsumerRunnable)
    [2018-07-02 14:55:03,921] INFO Message produced, offset: 3 (com.messagehub.samples.ProducerRunnable)
    [2018-07-02 14:55:06,053] INFO Message consumed: ConsumerRecord(topic = kafka-java-console-sample-topic, partition = 0, offset = 4, CreateTime = 1530539705922, serialized key size = 3, serialized value size = 25, headers = RecordHeaders(headers = [], isReadOnly = false), key = key, value = This is a test message #4) (com.messagehub.samples.ConsumerRunnable)
    [2018-07-02 14:55:06,054] INFO Message produced, offset: 4 (com.messagehub.samples.ProducerRunnable)
    [2018-07-02 14:55:08,186] INFO Message consumed: ConsumerRecord(topic = kafka-java-console-sample-topic, partition = 0, offset = 5, CreateTime = 1530539708055, serialized key size = 3, serialized value size = 25, headers = RecordHeaders(headers = [], isReadOnly = false), key = key, value = This is a test message #5) (com.messagehub.samples.ConsumerRunnable)
    ```
	{: codeblock}
	
9. このサンプルは、ユーザーが停止するまで無期限に実行されます。 処理を停止するには、<code>Ctrl+C</code> のようなコマンドを実行します。

<!-- 07/06/18 - Karen: removing until a newer version available
To watch a video that walks
you through getting a Java sample to run against {{site.data.keyword.messagehub}}, see [{{site.data.keyword.messagehub}} - Getting started with IBM's Kafka in the cloud ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.youtube.com/watch?v=tt-bLtFzC_4){:new_window}.
-->


