# Install Alibaba Cloud SDK for Python

This topic describes how to build a Python development environment on an on-premises machine to run demos of Server Load Balancer \(SLB\) SDK for Python. Alibaba Cloud supports Python 2.7. To run demos of SLB SDK for Python, you must install the core library of Alibaba Cloud SDK for Python and SLB SDK for Python. SLB SDK for Python supports Windows, Linux, and Mac. All demos in this topic are running in the Windows operating system.

1.  Install Python.

    1.  Open [download link of Python](https://www.python.org/downloads/).

    2.  Download Python 2.7.

        Select and download the required installation package from the download list. The package name is in the python-XYZ.msi format and XYZ represents the version number.

    3.  Double-click the package to open the Python installation wizard and use the default configurations to complete the installation.

    4.  Set environment variables.

        Add the Python installation path and the directory of the pip program to the Path row. Separate the directories with a semicolon \(;\).

        ```
        C:\Python27;C:\Python27\Scripts
        ```

    5.  At the cmd command-line interface, run the `python` command. If the following output is returned, you have launched the Python interactive environment. This indicates that Python has been installed.

        ```
        
        Python 2.7.15 (v2.7.15:ca079a3ea3, Apr 30 2018, 16:30:26) [MSC v.1500 64 bit (AM
        D64)] on win32
        Type "help", "copyright", "credits" or "license" for more information.
        >>>
        
                                    
        ```

2.  Install the core library of Alibaba Cloud SDK for Python.

    Run the following command to install the core library of Alibaba Cloud SDK for Python:

    ```
    pip install aliyun-python-sdk-core
    ```

    For more information about how to use Python and PIP, see [Python documentation](https://docs.python.org/3/).

3.  To install the SLB SDK, run the following command:

    ```
    pip install aliyun-python-sdk-slb
    ```

4.  Use Cloud Monitor to view the monitoring data of an SLB instance, such as the number of connections, the number of packets, and the amount of data transfer.

    ```
    pip install aliyun-python-sdk-cms
    ```

5.  To execute SDK files in Cloud Shell, run the --user command, install the SDK, and then execute the setup.py file.

    ```
    pip install --user aliyun-python-sdk-cms
    ```

    ```
    python setup.py install --user
    ```


