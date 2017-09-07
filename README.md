# WinHttpSample
Http访问有两种方式，GET和POST，就编程来说GET方式相对简单点，它不用向服务器提交数据，在这个例程中我使用POST方式，提交数据value1与value2，并从服务器得到他们的和（value1 + value2）。

为实现Http访问，微软提供了二套API：WinINet, WinHTTP。WinHTTP比WinINet更加安全和健壮，可以这么认为WinHTTP是WinINet的升级版本。这两套API包含了很多相似的函数与宏定义，呵呵，详细对比请查阅msdn中的文章“Porting WinINet Applications to WinHTTP”，在线MSDN连接：http://msdn2.microsoft.com/en-us/library/aa384068.aspx。在这个例程中，通过一个宏的设置来决定是使用WinHttp还是WinINet。代码如下:

#define USE_WINHTTP      //Comment this line to user wininet.

下面来说说实现Http访问的流程（两套API都一样的流程）：

1， 首先我们打开一个Session获得一个HINTERNET session句柄；

2， 然后我们使用这个session句柄与服务器连接得到一个HINTERNET connect句柄；

3， 然后我们使用这个connect句柄来打开Http 请求得到一个HINTERNET request句柄；

4， 这时我们就可以使用这个request句柄来发送数据与读取从服务器返回的数据；

5， 最后依次关闭request，connect，session句柄。

