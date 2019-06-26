# Downloading Edge Configuration File and Initializing Edge Image

## Creating a Script 

Create a script as follows to download the edge configuration file, _box.env_.

```sh
vi download-box-env.sh
url='http://10.21.18.226:8080/eostoolset/download?type=env&amp;boxid='
dir='default_box'
box=''
file='box.env'
while getopts "b:f:" arg
do
case $arg in
b)
box=$OPTARG
echo 'get box: '$box
;;
f)
file=$OPTARG
echo 'save to: '$file
;;
?)
echo "unkown argument"
exit 1
;;
esac
done
download="'"$url$box"' -O $file"
cmd_wget='wget'
echo 'command: '$cmd_wget $download
$cmd_wget $url$box -O $file 
```

The URL is the Edge Registration Environment address. Replace it with the environment address that you are going to use. See the following table for the list of registration environment addresses.

.. list-table:: EnOS Edge Registration Environment
   :widths: auto

   * - Environment
     - URL
   * - Europe
     - https://eoseu.envisioncn.com/configuration/
   * - The United States
     - https://eosus.envisioncn.com/configuration/
   * - China AWS
     - https://eos.envisioncn.com/configuration/
   * - China Azure
     - https://eosaz.envisioncn.com/configuration/

## Running the Script to Download the Edge Configuration File

```bash
bash download-box-env.sh -b 4afc74ad-401b-41c1-ad8c-dfcfa5b5078b
```

`4afc74ad-401b-41c1-ad8c-dfcfa5b5078b` indicates the SN. Replace it with the SN that you obtained in the previous step.

## Installing the Edge Image and Initializing the Parameters

```
docker run --name eos-edge --restart=always --env INSTANCE_SPEC=dell3000 --env BOX_ID=4afc74ad-401b-41c1-ad8c-dfcfa5b5078b --env  LOCAL_PUBLIC_KEY=MIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQDKR8er9d1vFWrJIkVGEXqChfUYqWug4wK9RgV2A9Lc8P1mGqXBIfJcpevhCsijQmCfpwqx/p36ULCfNy/590d3guybfXfcELYG2MXGnjTgeSBj5bhqAObpW/78YomlnFq29KSCHqBw9TXmm6JvNebUUTUnKUe2GUWRv5XVEMnegwIDAQAB   --env   GLOBAL_PUBLIC_KEY=MIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQCh+x8P5evInljwkALg9Qro20BJ9LOHndtvnI/yPrj5LqKeF7HkR/F1t+EDetF5/LQhOvML4xPSr9QQyuL51aCYJG8w/Ijpqp6pxNtTyEE61vj23KRxAYQ9rz -v /root/dockerdata/box:/home/envuser/box -v /root/dockerdata/data:/data -v /root/dockerdata/config:/data/apps/config/lionconfig/config/   registry.envisioncn.com/eos-all/cloudedge: tag-20180515-001
```

Replace the following parameters with the ones in _box.env_ file:
- INSTANCE_SPEC
- BOX_ID
- LOCAL_PUBLIC_KEY
- GLOBAL_PUBLIC_KEY

Replace the following parameters with the one you obtain from a Envision support or project manager:
- tag-20180515-001

## Verifying the Installation

Run the following commands to verify whether the service can be start normally. "docker service run normally" indicates that the installation is successfu.

```sh
container_id=`docker ps | grep eos-edge | awk '{print $1}'` && number=`docker exec   $container_id ps -ef | grep -E 'gateway|activemq|redis|conf_client|conn_clt|rtc|energy-os/fe' | wc -l`   &&  [ $number -eq 7 ]   && echo "docker service run normally" || echo "please wait"
```

Run the following commands to verify whether the connection between the edge and the cloud is working properly. "Connected to the cloud" indicates that the installation is successfully. Otherwise, contact the Envision Support for troubleshooting.

```sh
test=`netstat -ano | grep   -E '8099|8043' | grep -i est | awk '{print $5}' | wc -l` && [ $test   -eq 0 ] && echo "Not connected to the cloud yet" || echo   "Connected to the cloud"
```

<!--end-->
