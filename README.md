<p align="center">
  <img
    src="http://neonexchange.org/img/NEX-logo.svg"
    width="125px;">
    
</p>
<h3 align="center">Neo ICO Template</h3>
<p align="center">A template for NEP5 Compliant Tokens on the NEO platform</p>
<hr/>

#### original ReadMe.md
https://github.com/neonexchange/neo-ico-template/blob/master/README.md

#### Considerations

Useful links:

https://medium.com/neon-exchange/nex-ico-template-4ca7ba19fc8b
https://github.com/CityOfZion/neo-privatenet-docker
https://www.youtube.com/watch?v=yLPEsst_SVw

#### Creating a private network

1. Create AWS account and deploy an Amazon Linux AMI

2. SSH via putty:: https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/putty.html

3. installing docker on Amazon Linux AMI:: https://docs.aws.amazon.com/AmazonECS/latest/developerguide/docker-basics.html
```sudo yum update -y
sudo yum install -y docker
sudo service docker start
sudo usermod -a -G docker ec2-user
logout
```

4. run NEO nodes:: https://hub.docker.com/r/cityofzion/neo-privatenet/
```docker info #just a check
docker pull cityofzion/neo-privatenet
docker run --rm -d --name neo-privatenet -p 20333-20336:20333-20336/tcp -p 30333-30336:30333-30336/tcp cityofzion/neo-privatenet
```

Additional Ref:
https://docs.aws.amazon.com/cli/latest/userguide/awscli-install-linux.html
https://medium.com/@gubanotorious/installing-and-running-neo-python-on-windows-10-284fb518b213

#### Creating your local Env

ref: https://medium.com/@gubanotorious/installing-and-running-neo-python-on-windows-10-284fb518b213

1. Make sure you have Python 3.6
    1. go to Environment Variables
    2. look for the following in path:
    ```
    C:\<your_python_install_path>\Python36
    C:\<your_python_install_path>\Python36\Scripts
    ```

2. clone neo-python
```
C:\> git clone https://github.com/CityOfZion/neo-python.git c:/<your_folder_path>/neo-python
```

3. make a debug copy
```
C:\> robocopy c:\<your_folder_path>\neo-python c:\<your_folder_path\neo-python-debug /s
```

4. Open Windows PowerShell: https://docs.microsoft.com/en-us/windows/wsl/install-win10
```
Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux
restart
```

5. download Ubuntu: https://www.microsoft.com/en-ca/store/p/ubuntu/9nblggh4msv6?rtc=1

6. install neo-python: https://github.com/CityOfZion/neo-python#getting-started
```apt-get install software-properties-common python-software-properties
add-apt-repository ppa:deadsnakes/ppa
apt-get update
apt-get install python3.6 python3.6-dev python3.6-venv python3-pip libleveldb-dev libssl-dev g++

cd neo-python
apt-get install python3-venv
python3 -m venv venv
source venv/bin/activate    ** this line is important for part 4
pip install -e .
pip install -r requirements.txt
```

7. pull Nathan's smartcontract: https://github.com/nathanmukena/SmartContract
```
cd ../SmartContract
python3
>> from boa.compiler import Compiler
>> Compiler.load_and_save('ico_template.py')
```

This will compile your template to `ico_template.avm`


#### Testnet Deployed Details

For testing purposes, this template is deployed on testnet with the following contract script hash:

`0b6c1f919e95fe61c17a7612aebfaf4fda3a2214`

```json
{
    "code": {
        "parameters": "0710",
        "hash": "0b6c1f919e95fe61c17a7612aebfaf4fda3a2214",
        "returntype": 5,
        "script": ".. omitted .."
    },
    "version": 0,
    "code_version": ".2",
    "name": "NEX Ico Template",
    "author": "localhuman",
    "description": "An ICO Template",
    "properties": {
        "dynamic_invoke": false,
        "storage": true
    },
    "email": "tom@neonexchange.org"
}
```
