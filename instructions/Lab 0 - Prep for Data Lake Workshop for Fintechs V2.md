Data Lake workshop for Fintechs -- Instructions
===============================================

Lab Preparation
---------------

1.  You should have set up AWS CLI by now. After you have setup the CLI,
    follow the instructions below,

    a.  Simply copy the export commands from the Event Engine dashboard
        screen. In case you are using Linux/MacOS, and you should simply paste
        the commands you copied to your command prompt so the environment 
        variables take effect.
![](./Credential_Sharing_V1.png)
![](./Using_Credentials.png)
    b.  In case of Windows, copy the commands from the Windows tab in
        the Event Engine dashboard screen, and paste it to the command
        prompt.

    c.  Do the same for the Powershell prompt if you are using
        Powershell

        For this workshop, we will assume that we are using Linux/Mac
        based clients except when we are using the AWS Management
        Console.

2.  Proceed to the EC2 console, choose the instance we just created,
    click the connect button, click on the session manager tab, click
    **connect**. A terminal session will start in your browser window.
    **Again, setup the AWS CLI environment, just the way you set it up
    in step 1 above**.

3.  Run the following command in the Session Manager session you started
    in step 3. (*you will get the bucket name and the DB endpoint from
    the cloudformation stack output*):

        cd && sudo yum update -y && sudo yum install -y git && git clone \
        https://github.com/OmarKhayyam/data-lake-ws.git && cd \
        data-lake-ws/datagen && ./instance_setup.sh && pip3 install -r \
        ./requirements.txt && ./generatedata.py -s \
        <bucket_name> -e <aurora_db_endpoint>

4.  Open the file badworkflows.py in vi editor and change the line
    number 46 to `for userid in lines\[:4000\]:` and then run the
    following command to start the data generation:

        ./badworkflows.py -e <aurora_db_endpoint>

    This should create the initial data you need. Leave the running and
    proceed to the next step.

5. Reserved
