# Install static web pages {#task_bh5_dll_vdb .task}

After you create the ECS instances, deploy applications on them. In this tutorial, two static web pages are deployed on the ECS instances using Apache.

1.  Log on to the ECS instance. 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4106/15382928242219_en-US.png)

2.  Run the following command to update the installation package. 

    ```
    sudo apt-get update
    ```

3.  Run the following command to install the Apache server. 

    ```
    sudo apt-get install apache2
    ```

4.  Run the following command to modify the contents of the index.html file. 

    ```
    cd /var/www/html
    
    echo "Hello World ! This is ECS01." > index.html
    ```

    After modifying the content, enter the Elastic IP of the ECS instance in the web browser, you will see the following content.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4106/15382928242224_en-US.png)

5.  Repeat the preceding steps to create a web page on the other ECS instance and change the content to `Hello World ! This is ECS02.`. After modifying the content, enter the EIP of the ECS instance in the web browser, you will see the following content.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4106/15382928242231_en-US.png)


