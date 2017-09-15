
nomic Diagnostic

#### Primary Procedure
Follow these procedures to export the environment and download the diagnostic file.

1. Subsitute the IP address or FQDN belonging to your Turbnomic VM and navigate your web browser to the following URL.  `http://<YOUR_IP_OR_FQDN>/vmturbo/api?inv.c&MarketManager&saveMarkets&data/repos/turbo.markets.topology`.  Proceed to the next step if your web browser displays `true`.
2. Substitute the IP address or FQDN belonging to your Turbonmic VM and navigate your web browser to the following URL.  `http://<YOUR_IP_OR_FQDN>/update.html`.
3. Enter the credentials for the Turbonomic VM and press and hold the CTRL key (if Windows) or the &#8984; CMD key (if Mac) while you click the `Authenticate` button.
> The default credentials are **Username:** `administrator` and **Password:** `vmturbo`.
4. Select the second from the last option, `Export Environment`, and click the `Download` button.
5. Send a copy of the diagnostic file to your SE.
&nbsp;

-----

#### Manual Procedure
1. Open a console or SSH session to the Turbonomic VM and logon as **Username:** `root` and **Password:** `vmturbo`.
2. Run the following command:
```Shell
curl -s "http://localhost/vmturbo/api?inv.c&MarketManager&saveMarkets&data/repos/turbo.markets.topology"
```
> You may proceed if the command returns `true`.
3. The diagnostic file can be generated manually by running the following command:
```Shell
/srv/tomcat/script/appliance/vmtsupport.sh
```
> Please be patient as this may take a few minutes to complete.  Upon completion the command will return something similar to `123385094bytes written`.
4. Run the following command to obtain the path to the diagnostic file:
```Shell
BKP=$(ll /tmp/*.zip | tail -1 | awk '{print $NF}')
```
5. Run the following command to submit the diagnostic file for analysis:
6. ```Shell
curl -# -F ufile=@$BKP http://upload.vmturbo.com/appliance/cgi-bin/vmtupload.cgi | tee /dev/null
```

