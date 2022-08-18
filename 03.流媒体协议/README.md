# 流媒体

所谓流媒体是指采用流式传输的方式在 Internet 播放的媒体格式。 流媒体又叫流式媒体，它是指商家用一个视频传送服务器把节目当成数据包发出，传送到网络上。用户通过解压设备对这些数据进行解压后，节目就会像发送前那样显示出来。流媒体以流的方式在网络中传输音频、视频和多媒体文件的形式。流媒体文件格式是支持采用流式传输及播放的媒体格式。流式传输方式是将视频和音频等多媒体文件经过特殊的压缩方式分成一个个压缩包，由服务器向用户计算机连续、实时传送。在采用流式传输方式的系统中，用户不必像非流式播放那样等到整个文件，全部下载完毕后才能看到当中的内容，而是只需要经过几秒钟或几十秒的启动延时即可在用户计算机上利用，相应的播放器对压缩的视频或音频等流式媒体文件进行播放，剩余的部分将继续进行下载，直至播放完毕。

#### RTP

RTP(Real-time Transport Protocol)是用于Internet上针对多媒体数据流的一种传输层协议。RTP协议和RTP控制协议RTCP 一起使用，而且它是建立在UDP协议上的。RTP不像http和ftp可完整的下载整个影视文件，它是以固定的数据率在网络上发送数据，客户端也是按照这种速度观看影视文件，当影视画面播放过后，就不可以再重复播放，除非重新向服务器端要求数据。

#### RTCP

Real-time Transport Control Protocol 或 RTP Control Protocol或简写 RTCP)是实时传输控制协议,是实时传输协议(RTP)的一个姐妹协议，

注:--:RTP 协议和 RTP控制协议(RTCP) 一起使用，而且它是建立在UDP协议上的

#### RTSP

RTSP(Real Time Streaming Protocol)实时流媒体会话协议,SDP(会话描述协议)，RTP(实时传输协议)。是用来控制声音或影像的多媒体串流协议,RTSP 提供了一个可扩展框架，使实时数据，如音频与视频的受控、点播成为可能。媒体数据使用rtp,rtcp协议。一般使用udp 作为传输层。适合IPTV场景。数据源包括现场数据与存储在剪辑中的数据。该协议目的在于控制多个数据发送连接，为选择发送通道，如UDP、多播UDP与TCP提供途径，并为选择基于RTP上发送机制提供方法，传输时所用的网络通讯协定并不在其定义的范围内，服务器端可以自行选择使用TCP或UDP来传送串流内容，比较能容忍网络延迟.


RTSP 与 RTP 最大的区别在于：RTSP 是一种双向实时数据传输协议，它允许客户端向服务器端发送请求，如回放、快进、倒退等操作。当然，RTSP 可基于 RTP 来传送数据，还可以选择 TCP、UDP、组播 UDP 等通道来发送数据，具有很好的扩展性。它时一种类似与http协议的网络应用层协议.

#### WebRTC

web端实现流媒体的协议。google刚推出WebRTC的时候巨头们要么冷眼旁观，要么抵触情绪很大。使用RTP协议传输。

#### RTMP

RTMP(Real Time Messaging Protocol)是Macromedia开发的一套视频直播协议，现在属于 Adobe。和 HLS 一样都可以应用于视频直播，基于TCP不会丢失。区别是 RTMP 基于 flash 无法在 iOS 的浏览器里播放，但是实时性比 HLS 要好。实时消息传送协议是 Adobe Systems 公司为 Flash 播放器和服务器之间音频、视频和数据传输 开发的开放协议。 iOS 代码里面一般常用的是使用 RTMP 推流，可以使用第三方库 librtmp-iOS 进行推流，librtmp 封装了一些核心的 API 供使用者调用，RTMP 协议也要客户端和服务器通过“握手”来建立 RTMP Connection，然后在Connection上传输控制信息。RTMP 协议传输时会对数据格式化，而实际传输的时候为了更好地实现多路复用、分包和信息的公平性，发送端会把Message划分为带有 Message ID的Chunk，每个Chunk可能是一个单独的Message，也可能是Message的一部分，在接受端会根据Chunk中包含的data的长度，message id和message的长度把chunk还原成完整的Message，从而实现信息的收发。

#### HLS

HLS(HTTP Live Streaming)是苹果公司(Apple Inc.)实现的基于HTTP的流媒体传输协议，可实现流媒体的 直播 和 点播 ,主要应用在iOS系
统，为iOS设备(如iPhone、iPad)提供音视频直播和点播方案。HLS 点播，基本上就是常见的分段HTTP点播，不同在于，它的分段非常小。相对于常见的流媒体直播协议，例如RTMP协议、RTSP 协议、MMS 协议等，HLS 直播最大的不同在于，直播客户端获取到的，并不是一个完整的数据流。HLS 协议在服务器端将直播数据流存储为连续的、很短时长的媒体文件(MPEG-TS格式)，而客户端则不断的下载并播放这些小文件，因为服务器端总是会将最新的直播数据生成新的小文件，这样客户端只要不停的按顺序播放从服务器获取到的文件，就实现了直播。由此可见，基本上可以认为，HLS 是以点播的技术方式来实现直播。由于数据通过 HTTP 协议传输，所以完全不用考虑防火墙或者代理的问题，而且分段文件的时长很短，客户端可以很快的选择和切换码率，以适应不同带宽条件下的播放。不过HLS的这种技术特点，决定了它的延迟一般总是会高于普通的流媒体直播协议。iOS和 Android 都天然支持这种协议，配置简单，直接使用 video 标签即可

#### VLS

是一种流服务器，专门用来解决流的各种问题，它也具有一些 VLC 的特征。 videolan 作为服务器可以输出http，rtp，rtsp的流。

#### MediaCodec

MediaCodec是安卓自带的视频编解码接口，由于使用的是硬解码，其效率相对FFMPEG高出来不少。而MediaCodec就很好拓展，我们可以根据流媒体的协议和设备硬件本身来自定义硬件解码，代表播放器就是Google的ExoPlayer。

ExoPlayer的开源地址 ： https://github.com/google/ExoPlayer

基本流程：

- 1.创建和配置MediaCodec对象
- 2.进行以下循环：
- 如果一个输入缓冲区准备好：
- 读取部分数据，复制到缓冲区
- 如果一个输出缓冲区准备好：
- 复制到缓冲区
- 3.销毁MediaCodec对象

接口如下：

```java
// 根据视频编码创建解码器，这里是解码AVC编码的视频
MediaCodec mediaCodec = MediaCodec.createDecoderByType(MediaFormat.MIMETYPE_VIDEO_AVC);

// 创建视频格式信息
MediaFormat mediaFormat = MediaFormat.createVideoFormat(mimeType, width, height);

// 配置
mediaCodec.configure(mediaFormat, surfaceView.getHolder().getSurface(), null, 0);
mediaCodec.start();

// 停止解码，此时可以再次调用configure()方法
mediaCodec.stop();

// 释放内存
mediaCodec.release();

// 以下是循环解码接口
getInputBuffers：获取需要编码数据的输入流队列，返回的是一个ByteBuffer数组 
queueInputBuffer：输入流入队列 
dequeueInputBuffer：从输入流队列中取数据进行编码操作 
getOutputBuffers：获取编解码之后的数据输出流队列，返回的是一个ByteBuffer数组 
dequeueOutputBuffer：从输出队列中取出编码操作之后的数据 
releaseOutputBuffer：处理完成，释放ByteBuffer数据 
```

用MediaCodec来实现的话，代码中主要通过上面的接口实现了媒体的播放过程。

实例可以参考：

https://blog.csdn.net/u014653815/article/details/81084161
