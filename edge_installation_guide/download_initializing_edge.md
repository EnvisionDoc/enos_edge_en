# Downloading edge configuration file and initializing edge image

## Creating a script to download the edge configuration file

*Table: EnOS Edge Registration Environment:Create a script for downloading the edge configuration file box.env*

<table>
  <tr>
    <td>Commands </td>
    <td>Remarks </td>
  </tr>
  <tr>
    <td>vi download-box-env.sh<br>
      url='http://10.21.18.226:8080/eostoolset/download?type=env&amp;boxid=' <br>
      dir='default_box'<br>
      box=''<br>
      file='box.env'<br>
      while getopts &quot;b:f:&quot; arg<br>
      do<br>
      case $arg in<br>
      b)<br>
      box=$OPTARG<br>
      echo 'get box: '$box<br>
      ;;<br>
      f)<br>
      file=$OPTARG<br>
      echo 'save to: '$file<br>
      ;;<br>
      ?)<br>
      echo &quot;unkonw argument&quot;<br>
      exit 1<br>
      ;;<br>
      esac<br>
      done<br>
      download=&quot;'&quot;$url$box&quot;' -O $file&quot;<br>
      cmd_wget='wget'<br>
      echo 'command: '$cmd_wget $download<br>
      $cmd_wget $url$box -O $file</td>
    <td>Where, the URL is the Edge   Registration Environment address, and need to be replaced by the environment   address that you are going to use.. See the following table for the list of   registration environments.</td>
  </tr>
</table>

*Table: EnOS Edge Registration Environment*

<table>
  <tr>
    <td>Environment</td>
    <td>URL</td>
  </tr>
  <tr>
    <td>Europe</td>
    <td><a href="https://eoseu.envisioncn.com/configuration/">https://eoseu.envisioncn.com/configuration/</a></td>
  </tr>
  <tr>
    <td>US</td>
    <td><a href="https://eosus.envisioncn.com/configuration/">https://eosus.envisioncn.com/configuration/</a></td>
  </tr>
  <tr>
    <td>China AWS</td>
    <td><a href="https://eos.envisioncn.com/configuration/">https://eos.envisioncn.com/configuration/</a></td>
  </tr>
  <tr>
    <td>China Azure</td>
    <td><a href="https://eosaz.envisioncn.com/configuration/">https://eosaz.envisioncn.com/configuration/</a></td>
  </tr>
</table>

## Running Script to download the Edge Configuration File

*Table: Run the script to download the edge file "box.env"*

<table>
  <tr>
    <td>Commands </td>
    <td>Remarks </td>
  </tr>
  <tr>
    <td>bash download-box-env.sh   -b 4afc74ad-401b-41c1-ad8c-dfcfa5b5078b</td>
    <td>Where   &ldquo;4afc74ad-401b-41c1-ad8c-dfcfa5b5078b&rdquo; is the SN, replace it with the SN that   you obtained in the previous step.</td>
  </tr>
</table>

After the download is completed, open the box.env file and get the parameters that used in the next step.

## Installing the edge image and initialize the parameters

*Table: Install the edge image and initialize the parameters*

<table>
  <tr>
    <td>Commands </td>
    <td>Remarks </td>
  </tr>
  <tr>
    <td>docker run --name eos-edge --restart=always --env INSTANCE_SPEC=dell3000 --env BOX_ID=4afc74ad-401b-41c1-ad8c-dfcfa5b5078b --env  LOCAL_PUBLIC_KEY=MIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQDKR8er9d1vFWrJIkVGEXqChfUYqWug4wK9RgV2A9Lc8P1mGqXBIfJcpevhCsijQmCfpwqx/p36ULCfNy/590d3guybfXfcELYG2MXGnjTgeSBj5bhqAObpW/78YomlnFq29KSCHqBw9TXmm6JvNebUUTUnKUe2GUWRv5XVEMnegwIDAQAB   --env   GLOBAL_PUBLIC_KEY=MIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQCh+x8P5evInljwkALg9Qro20BJ9LOHndtvnI/yPrj5LqKeF7HkR/F1t+EDetF5/LQhOvML4xPSr9QQyuL51aCYJG8w/Ijpqp6pxNtTyEE61vj23KRxAYQ9rz -v /root/dockerdata/box:/home/envuser/box -v /root/dockerdata/data:/data -v /root/dockerdata/config:/data/apps/config/lionconfig/config/   registry.envisioncn.com/eos-all/cloudedge: tag-20180515-001 </td>
    <td>What&rsquo;s marked in blue are parameters that need to be replaced by the parameters obtained from the box.env. What&rsquo;s marked in green is the Edge version tag that can be obtained from your Envision project manager or support representative. </td>
  </tr>
</table>

## Verifying the installation

Run the following commands to verify whether the service can be start normally. "docker service run normally" indicates that the installation is successful and you can proceed to the next step.

*Table: Step 1. Check Docker service availability*

<table>
  <tr>
    <td>Commands </td>
    <td>Remarks </td>
  </tr>
  <tr>
    <td>container_id=`docker ps |   grep eos-edge | awk '{print $1}'` &amp;&amp; number=`docker exec   $container_id ps -ef | grep -E 'gateway|activemq|redis|conf_client|conn_clt|rtc|energy-os/fe' | wc -l`   &amp;&amp;  [ $number -eq 7 ]   &amp;&amp; echo &quot;docker service run normally&quot; || echo &quot;please   wait&quot; </td>
    <td>Change to UTF-8 format if you encounter the Chinese display problem. </td>
  </tr>
</table>

Run the following commands to verify whether the connection between the edge and the cloud is ok:

- "Connected to the cloud" indicates that the installation is successfully.

- Otherwise, please contact the Envision Support.

*Table: Step 2. Test connection to the cloud*

<table>
  <tr>
    <td>Command </td>
    <td>Remark </td>
  </tr>
  <tr>
    <td>test=`netstat -ano | grep   -E '8099|8043' | grep -i est | awk '{print $5}' | wc -l` &amp;&amp; [ $test   -eq 0 ] &amp;&amp; echo &quot;Not connected to the cloud yet&quot; || echo   &quot; Connected to the cloud &quot; </td>
    <td></td>
  </tr>
</table>
