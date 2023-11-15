# Attack Range Config

## attack_range.yml
`attack_range.yml` is the configuration file for Attack Range. Attack Range reads first the default configuration file located in `configs/attack_range_default.yml` and then the attack_range.yml (or the config which you specify with the -c parameter). The parameters in `attack_range.yml` override the parameters in `configs/attack_range_default.yml`.

## attack_range_default.yml
The `attack_range_default.yml` defines all default values for the Attack Range. The following file contains some comments to describe the different parameters:
````yml
general:
  attack_range_password: "Pl3ase-k1Ll-me:p"
# Attack Range Master Password for all accounts in Attack Range.

  cloud_provider: "aws"
# Cloud Provider: aws/azure/local

  key_name: "attack-range-key-pair"
# The key name is the name of the AWS key pair and at the same time an unique identifier for Attack Ranges.

  attack_range_name: "ar"
# Attack range Name let you build multiple Attack Ranges by changing this parameter.

  ip_whitelist: "0.0.0.0/0"
# Blocks from which Attack Range machines can be reached.
# This allow comma-separated blocks
# ip_whitelist = 0.0.0.0/0,35.153.82.195/32

  version: "3.0.0"
# The current released version of Attack Range.

  use_prebuilt_images_with_packer: "0"
# Enable/Disable usage of packer to create pre-built images by setting this to 1 or 0.

  crowdstrike_falcon: "0"
# Enable/Disable Crowdstrike Falcon by setting this to 1 or 0.

  crowdstrike_agent_name: "WindowsSensor.exe"
  crowdstrike_customer_ID: ""
  crowdstrike_logs_region: ""
  crowdstrike_logs_access_key_id: ""
  crowdstrike_logs_secret_access_key: ""
  crowdstrike_logs_sqs_url: ""
# All these fields are needed to automatically deploy a Crowdstrike Agent and ingest Crowdstrike Falcon logs into the Splunk Server.
# See the chapter Crowdstrike Falcon in the docs page Attack Range Features.

  carbon_black_cloud: "0"
# Enable/Disable VMWare Carbon Black Cloud by setting this to 1 or 0.

  carbon_black_cloud_agent_name: "installer_vista_win7_win8-64-3.8.0.627.msi"
  carbon_black_cloud_company_code: ""
  carbon_black_cloud_s3_bucket: ""
# All these fields are needed to automatically deploy a Carbon Black Agent and ingest Carbon Black logs into the Splunk Server.
# See the chapter Carbon Black in the docs page Attack Range Features.

aws:
  region: "us-west-2"
# Region used in AWS. This should be the same as the region configured in AWS CLI.

  private_key_path: "~/.ssh/id_rsa"
# Path to your private key. This needs to match the public key uploaded to AWS.

  cloudtrail: "0"
# Enable/Disable collection of Cloudtrail logs by setting this to 1 or 0.

  cloudtrail_sqs_queue: "https://sqs.us-west-2.amazonaws.com/111111111111/cloudtrail-cloud-attack-range"
# Cloudtrail SQS queue. See the chapter AWS Cloudtrail in the docs page Attack Range Cloud.

  use_elastic_ips: "1"
# Enable/disable usage of Elastic IPs by setting this to 1 or 0.

azure:
  location: "West Europe"
# Region used in Azure.

  subscription_id: "xxx"
# Azure subscription ID.

  private_key_path: "~/.ssh/id_rsa"
# Path to your private key.

  public_key_path: "~/.ssh/id_rsa.pub"
# Path to your public key.

  azure_logging: "0"
# Enable/Disable Azure logs and onboard them into the Splunk Server by setting this to 1 or 0.

  client_id: "xxx"
  client_secret: "xxx"
  tenant_id: "xxx"
  event_hub_name: "xxx"
  event_hub_host_name: "xxx"
# All these fields are needed to configure the Azure logs. See the chapter Azure Logs in the docs page Attack Range Cloud.

local:
  provider: "Virtual Box"
# Attack Range Local used Virtualbox and Vagrant to build the Attack Range.

splunk_server:
  splunk_image: "splunk-v3-0-0"
# Name of the image of the Splunk Server. Packer is used to build this image.

  install_es: "0"
# Enable/Disable Enterprise Security by setting this to 1 or 0.

  splunk_es_app: "splunk-enterprise-security_701.spl"
# File name of the Enterprise Security spl file. Needs to be located in the apps folder.

  s3_bucket_url: "https://attack-range-appbinaries.s3-us-west-2.amazonaws.com"
# S3 bucket containing the Splunk Apps which will be installed in Attack Range.

  splunk_url: "https://download.splunk.com/products/splunk/releases/9.0.2/linux/splunk-9.0.2-17e00c557dc1-Linux-x86_64.tgz"
# Url to download Splunk Enterprise.

  splunk_uf_url: "https://download.splunk.com/products/universalforwarder/releases/9.0.2/linux/splunkforwarder-9.0.2-17e00c557dc1-linux-2.6-amd64.deb"
# Url to download Splunk Universal Forwarder Linux.

  splunk_uf_win_url: "https://download.splunk.com/products/universalforwarder/releases/9.0.2/windows/splunkforwarder-9.0.2-17e00c557dc1-x64-release.msi"
# Url to download Splunk Universal Forwarder Windows.

  byo_splunk: "0"
# Enable/Disable Bring your own Splunk by setting this to 1 or 0.

  byo_splunk_ip: ""
# Specify Splunk IP address when you enable BYO Splunk.

  ingest_bots3_data: "0"
# Ingest BOTS data to Attack Range.

  install_dltk: "0"
# Install Deep Learning Toolkit.

phantom_server:
  phantom_server: "0"
# Enable/Disable Phantom Server by setting this to 1 or 0.

  phantom_image: "phantom-v3-0-0"
# name of the image of the Phantom Server. Packer is used to build this images.

  phantom_community_username: user
# Specify the username needed to login to my.phantom.us to download Phantom.
# This must be changed to a real username.
# You can register at https://www.splunk.com/en_us/download/soar-free-trial.html.

  phantom_community_password: password
# Specify the password used to login to my.phantom.us to download Phantom.
# This must be changed to a real password.
# You can register at https://www.splunk.com/en_us/download/soar-free-trial.html.

  phantom_repo_url: https://repo.phantom.us/phantom/5.2/base/7/x86_64/phantom_repo-5.2.1.78411-1.x86_64.rpm
# Specify the Phantom install RPM.

  phantom_version: "5.2.1.78411-1"
# Fields the Phantom Version.

  phantom_byo: "0"
# Enable/Disable Bring your own Phantom by setting this to 1 or 0.

  phantom_byo_ip: ""
# Specify Phantom IP address when you enabled byo Phantom.

  phantom_byo_api_token: ""
# Phantom Api Token.

windows_servers_default:
  hostname: ar-win
# Define the hostname for the Windows Server.

  windows_image: windows-2016-v3-0-0
# name of the image of the Windows Server. Packer is used to build this images.

  create_domain: "0"
# Create Domain will turn this Windows Server into a Domain Controller. Enable by setting this to 1.

  join_domain: "0"
# Join a domain by setting this to 1 or 0.

  win_sysmon_config: "SwiftOnSecurity.xml"
# Specify a Sysmon config located under configs/ .

  install_red_team_tools: "0"
# Install different read team tools by setting this to 1 or 0.

  bad_blood: "0"
# Install Bad Blood by setting this to 1 or 0.
# More information in chapter Bad Blood under Attack Range Features.

linux_servers_default:
  hostname: ar-linux
# Define the hostname for the Linux Server.

  linux_image: linux-v3-0-0
# Name of the image of the Linux Server. Packer is used to build this image.

  sysmon_config: "SysMonLinux-CatchAll.xml"
# Specify a Sysmon config located under configs/ .

kali_server:
  kali_server: "0"
# Enable Kali Server by setting this to 1.

nginx_server:
  nginx_server: "0"
# Enable Nginx Server by setting this to 1.

  hostname: "nginx"
# Specify the image used for Nginx Server.

  nginx_image: nginx-web-proxy-v3-0-0
# name of the image of the Web proxy. Packer is used to build this images.

  proxy_server_ip: "10.0.1.12"
# Specify what ip to proxy.

  proxy_server_port: "8000"
# Specify what port to proxy.

zeek_server:
  zeek_server: "0"
# Enable Zeek Server by setting this to 1.

  zeek_image: "zeek-v3-0-0"
# Specify the image used for Zeek Server.

simulation:
  atomic_red_team_repo: redcanaryco
# Specify the repository owner for Atomic Red Team.

  atomic_red_team_branch: master
# Specify the branch for Atomic Red Team.

  prelude: "0"
# Install Prelude by setting this to 1. 

  prelude_operator_url: "https://download.prelude.org/latest?arch=x64&platform=linux&variant=zip&edition=headless"
# Specify where to download Prelude Operator from.

  prelude_account_email: "test@test.com"
# Email account login into a Prelude Operator UI.
# Required for connecting to redirector, can be found on the GUI under connect -> deploy manual redirector -> accountEmail.
````
