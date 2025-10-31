# Tools Setup For Devops

- As we know, Devops is simply set of tools and practices to improve the collaboration between the Development Team and Operations Team which increases the efficiency of Software Development Life Cycle and produces the software very quickly and efficicently. So to master the Devops we actually need to learn the tools which makes the SDLC fast. So here we are installing some common tools and setting some common accounts which are required to learn devops.

  So mainly we are doing these 3 steps 

  1. **Installation of Tools**

  2. **Signup Accounts**

  3. **AWS Setup**

## Installation of Tools

- To learn devops we actually need to install the following tools.

  1. **Oracle Virtual Box**

  2. **JDK**

  3. **Git**

  4. **Maven**

  5. **Vscode**

  6. **Vagrant**

  7. **Sublime Text Editor** (Or any text Editor)

- So inorder to install these software, we actually go to respective software offical websites and download the installers and then we execute those installer files to install the softwares manually. So it requires so much work if you need to install so many other tools

- So, instead of doing this, we can use a single software which can install any other softwares using a single commands and that software is called **Chocolatey** .

- To install Chocolatey in windows just follow these steps.

  1. First Open the Powershell in Administrator Mode.

  2. Next execute the following commnad `Get-ExecutionPolicy`. If it returns **Restricted** then run this command ` Set-ExecutionPolicy AllSigned` which returns **Allsigned**.

  3. Now run this command to install the chocolatey.

     `Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))`

  4. Now run `choco list` command to check whether chocolatey is installed sucessfully or not. (If you need any further assistance just refer this website [Chocolatey](https://chocolatey.org/install))

- After installing Chocolatey, you just need to run the following commands to install the required softwares for learning devops.

  1. **Virtual Box** : `choco install virtualbox --version=7.1.4 -y`

  2. **Git** : `choco install git -y`

  3. **Maven** : `choco install maven -y`

  4. **Corrento7JDK** : `choco install corretto17jdk -y`

  5. **AWSCLI** : `choco install awscli -y`

  6. **VsCode** : `choco install vscode -y`

  7. **Sublime Text Editor** : `choco install sublimetext3 -y`

**Note** : If you want to install or uninstall any softwares then search for the software in this website ([Other Softwares Installation](https://community.chocolatey.org/packages)) which gives `choco` command to install or uninstall any softwares. If you install the softwares with above links you might not get advanced versions, so just go through this website and install the required softwares with advanced websites.


## SignUp Accounts

- Next step is Creating Accounts in all these 3 following Websites.

  1. [Github](https://github.com/)

  2. [DockerHub](https://hub.docker.com/)

  3. [SonarCloud](https://www.sonarsource.com/products/sonarcloud/) -> Create this account with github
