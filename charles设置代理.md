可以使用Charles来让手机访问电脑上的本地项目。下面是一种常见的设置方法：

1. 确保你的电脑和手机连接在同一个局域网（Wi-Fi）中。

2. 在电脑上运行Charles，并确保它在监听状态。

3. 在电脑上找到Charles的IP地址。你可以在Charles的菜单栏中选择"Help" -> "Local IP Address"来查看。

4. 在手机上连接到相同的局域网，并确保可以访问互联网。

5. 打开手机的网络设置，并找到当前连接的Wi-Fi网络。

6. 在Wi-Fi网络设置中，找到"代理"或"Proxy"选项。

   <img src="https://aronimage.oss-cn-hangzhou.aliyuncs.com/img/2c56bdb594d68a951500e2469141636.jpg" alt="2c56bdb594d68a951500e2469141636" style="zoom: 25%;" />

7. 选择"手动"或"Manual"代理配置，并输入以下信息：

   - 代理主机/服务器：输入你电脑上运行Charles的IP地址。

     **实际上是wifi的这个地址！**

     <img src="https://aronimage.oss-cn-hangzhou.aliyuncs.com/img/image-20230601000615031.png" alt="image-20230601000615031" style="zoom:33%;" />

   - 端口：输入Charles使用的端口，默认为8888。（任意可以）

8. 保存设置并关闭网络设置。

现在，你的手机将通过Charles代理服务器连接到电脑上的本地项目。你可以在Charles中监控和记录手机与项目之间的网络流量，并进行调试和分析。请注意，有些应用程序可能会使用HTTPS进行加密通信。在这种情况下，你需要在手机上安装并信任Charles的SSL证书，以便Charles能够解密和查看HTTPS请求。你可以在Charles的菜单栏中选择"Help" -> "SSL Proxying" -> "Install Charles Root Certificate on a Mobile Device or Remote Browser"来获取详细的安装指南。

> 为什么Charles可以实现这个效果呢？

Charles通过作为一个代理服务器来实现手机访问电脑的本地项目。下面是其工作原理的简要说明：

1. **设置代理**：**在手机上将代理设置为电脑上运行Charles的IP地址和端口。这样，所有手机的网络流量将通过Charles进行中转**。（让手机的网络去访问到电脑）
2. 拦截和转发流量：当手机发送请求时，流量会被路由到Charles代理服务器。Charles会拦截这些请求并将它们转发到目标服务器。
3. 监视和记录流量：Charles在拦截请求和响应时会记录下详细的信息，包括头部、正文和元数据。这使得开发人员能够查看请求和响应的内容，以便调试和分析。
4. SSL解密（可选）：对于使用HTTPS进行加密通信的应用程序，Charles可以生成和安装自己的SSL证书，并将其信任。这使得Charles能够解密和查看加密的HTTPS流量。

通过上述过程，Charles允许开发人员在电脑和手机之间创建一个中间层，以便监控和调试手机与电脑上的本地项目之间的网络通信。这对于开发和测试应用程序特别有用，可以帮助开发人员捕获和分析网络请求、识别问题和进行性能优化。