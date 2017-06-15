# TestHuanXim
![环信大致介绍](https://github.com/MarsKang1/TestHuanXim/blob/master/ImageFolder/in1.jpg)
通过上面的图片我们可以了解到无论是pc端还是手机端最终我们都要首先将我们发送的信息提交给环信的处理器也就是说主要的业务处理首先是交给环信处理的。
当然我们也可以将我们的消息发送给我们的后台前提是我们的后台实现了restAPI

![环信Api消息处理](https://github.com/MarsKang1/TestHuanXim/blob/master/ImageFolder/in2.jpg)
在这幅图中我们可以看到当环信发送完消息后消息会在环信服务器中存储数据当数据处理完成后如果用户在线状态则接受消息处理消息内容。如果用户不在线则
通过将消息添加到消息队列中直到用户收到消息后才删除推送内容

环信的创建账号过程按照开发文档即可在这里就不在介绍了
在配置过程中可以将环信的jar包之类的添加到工程中我个人是在gradle中配置的配置如下  
1.添加gradle配置
compile 'com.hyphenate:hyphenate-sdk:3.3.0'
突然发现一点添加完引用后apk的大小变成了将近18M
然后试了一下添加jar包支持发现也是18M果然没什么卵用
2.添加权限
  <!-- Required -->
    <uses-permission android:name="android.permission.VIBRATE" />
    <uses-permission android:name="android.permission.INTERNET" />
    <uses-permission android:name="android.permission.RECORD_AUDIO" />
    <uses-permission android:name="android.permission.CAMERA" />
    <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
    <uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
    <uses-permission android:name="android.permission.MOUNT_UNMOUNT_FILESYSTEMS"/>
    <uses-permission android:name="android.permission.ACCESS_FINE_LOCATION" />
    <uses-permission android:name="android.permission.GET_TASKS" />
    <uses-permission android:name="android.permission.ACCESS_WIFI_STATE" />
    <uses-permission android:name="android.permission.CHANGE_WIFI_STATE" />
    <uses-permission android:name="android.permission.WAKE_LOCK" />
    <uses-permission android:name="android.permission.MODIFY_AUDIO_SETTINGS" />
    <uses-permission android:name="android.permission.READ_PHONE_STATE" />
    <uses-permission android:name="android.permission.RECEIVE_BOOT_COMPLETED" />
3.添加环信的相关配置
<!-- 设置环信应用的AppKey -->
        <meta-data android:name="EASEMOB_APPKEY"  android:value="marskang#useintroduce" />
        <!-- 声明SDK所需的service SDK核心功能-->
        <service android:name="com.hyphenate.chat.EMChatService" android:exported="true"/>
        <service android:name="com.hyphenate.chat.EMJobService" android:permission="android.permission.BIND_JOB_SERVICE" android:exported="true" />
        <!-- 声明SDK所需的receiver -->
        <receiver android:name="com.hyphenate.chat.EMMonitorReceiver">
            <intent-filter>
                <action android:name="android.intent.action.PACKAGE_REMOVED"/>
                <data android:scheme="package"/>
            </intent-filter>
            <!-- 可选filter -->
            <intent-filter>
                <action android:name="android.intent.action.BOOT_COMPLETED"/>
                <action android:name="android.intent.action.USER_PRESENT" />
            </intent-filter>
        </receiver>












