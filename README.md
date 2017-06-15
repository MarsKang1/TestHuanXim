# TestHuanXim
![环信大致介绍](https://github.com/MarsKang1/TestHuanXim/blob/master/ImageFolder/in1.jpg)
通过上面的图片我们可以了解到无论是pc端还是手机端最终我们都要首先将我们发送的信息提交给环信的处理器也就是说主要的业务处理首先是交给环信处理的。
当然我们也可以将我们的消息发送给我们的后台前提是我们的后台实现了restAPI

![环信Api消息处理](https://github.com/MarsKang1/TestHuanXim/blob/master/ImageFolder/in2.jpg)
在这幅图中我们可以看到当环信发送完消息后消息会在环信服务器中存储数据当数据处理完成后如果用户在线状态则接受消息处理消息内容。如果用户不在线则
通过将消息添加到消息队列中直到用户收到消息后才删除推送内容














