# Installation script of CodeDeploy agent.
This Script will be used on Linux RHEL OS.

```
#!/bin/bash
sudo yum update
sudo yum install ruby
sudo yum install wget
CODEDEPLOY_BIN="/opt/codedeploy-agent/bin/codedeploy-agent"
$CODEDEPLOY_BIN stop
yum erase codedeploy-agent -y
cd /home/ec2-user
wget https://aws-codedeploy-<Region-ID>.s3.<Region-ID>.amazonaws.com/latest/install
chmod +x ./install
sudo ./install auto
```

# to install CodeDeploy agent in Windows environment, you can follow below steps.

- Open Windows powershell and enter below command and type 'Y' if it prompt any.
  Set-ExecutionPolicy RemoteSigned
- Import-Module AWSPowerShell
- New-Item -Path "c:\temp" -ItemType "directory" -Force
- Configure AWS crentials with **Set-AWSCredential** and **Initialize-AWSDefaultConfiguration** command.
- powershell.exe -Command Read-S3Object -BucketName aws-codedeploy-<Region-ID> -Key latest/codedeploy-agent.msi -File c:\temp\codedeploy-agent.msi
- c:\temp\codedeploy-agent.msi /quiet /l c:\temp\host-agent-install-log.txt
- powershell.exe -Command Get-Service -Name codedeployagent


