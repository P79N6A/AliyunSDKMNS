# Aliyun MNS PHP SDK

# 安装

- composer
```
composer require shuguang/aliyun-sdk-mns
```

- composer自动加载

```
require_once "vendor/autoload.php";

```

- 实例化
```
use AliyunMNS\Client;
$client = new Client($endPoint, $accessId, $accessKey);

```


- 发送

    - 主题消息

    ```
    use AliyunMNS\Client;
    use AliyunMNS\Requests\PublishMessageRequest;

    $endPoint = '';
    $accessId = '';
    $accessKey = '';
    $topicName = '';

    $client = new Client($endPoint, $accessId, $accessKey);
    $topic = $client->getTopicRef($topicName);//获取Topic地址
    $messageBody = 'test message';  //消息内容
    $messageTag = 'pay_success';    //消息标签
    $request = new PublishMessageRequest($messageBody,$messageTag);
    $res = $topic->publishMessage($request);
    $res->isSucceed();
    ```

    - 队列消息
    ```
    use AliyunMNS\Client;
    use AliyunMNS\Requests\PublishMessageRequest;

    $endPoint = '';
    $accessId = '';
    $accessKey = '';
    $queueName = '';

    $client = new Client($endPoint, $accessId, $accessKey);
    $topic = $client->getQueueRef($queueName);//获取Topic地址
    $messageBody = 'test message';  //消息内容
    $request = new PublishMessageRequest($messageBody);
    $res = $topic->publishMessage($request);
    $res->isSucceed();

    ```