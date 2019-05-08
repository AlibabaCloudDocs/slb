# 安装阿里云Python SDK {#task_ntm_dcw_tgb .task}

介绍如何在本地搭建可以运行负载均衡Python SDK示例的Python开发环境，阿里云Python SDK支持Python 2.7，要运行负载均衡的Python SDK示例，您需要安装阿里云Python SDK的核心库和SLB Python SDK。Python SDK支持Windows、Linux和Mac操作系统，所有负载均衡Python SDK示例均在Windows系统下运行。

1.  安装Python。 
    1.  登录[Python下载地址](https://www.python.org/downloads/)。
    2.  下载2.7版本的Python。 

        在下载列表中选择平台安装包，包格式为：python-XYZ.msi 文件 ， XYZ 为你要安装的版本号。

    3.  下载后，双击下载包，进入Python安装向导，使用默认设置即可。
    4.  设置环境变量。 在Path行添加python安装路径和pip命令运行程序所在的目录，目录之间以;分隔。

        ```
        C:\Python27;C:\Python27\Scripts
        ```

    5.  在cmd命令行，执行`python`命令，显示类似如下，进入Python交互式环境，表示Python安装成功。 

        ```
        
        Python 2.7.15 (v2.7.15:ca079a3ea3, Apr 30 2018, 16:30:26) [MSC v.1500 64 bit (AM
        D64)] on win32
        Type "help", "copyright", "credits" or "license" for more information.
        >>>
        
        							
        ```

2.  安装阿里云SDK核心库。 执行如下命令，安装阿里云SDK核心库：

    ```
    pip install aliyun-python-sdk-core
    ```

    关于Python及PIP的使用说明，请参考[Python文档](https://docs.python.org/3/)。

3.  执行如下命令，安装SLB SDK。 

    ```
    pip install aliyun-python-sdk-slb
    ```

4.  需要结合阿里云云监控服务，查看负载均衡的云监控数据，如连接数、数据包数和流量等，执行如下命令，安装云监控SDK。 

    ```
    pip install aliyun-python-sdk-cms
    ```

5.  如果需要使用CloudShell运行SDK文档，执行如下命令，使用--user安装SDK并运行setup.py文件。 

    ```
    pip install --user aliyun-python-sdk-cms
    ```

    ```
    python setup.py install --user
    ```


