### Avamar Collection Procedure

Use the following commands to run the proactive check script and collect the output.

1. Connect to Avamar via SSH and login as `admin`.
2. Load admin SSH key by typing the following.
    ```Shell
    ssh-agent bash
    ssh-add ~admin/.ssh/admin_key
    ```
3. When prompted for passphrase, enter `P3t3rPan!`.
    > This is the same for almost all Avamar grids.
4. Then, run the following commands;
    ```Shell
    mccli server show-prop
    cd /home/admin
    ./proactive_check.pl
    ```
    > When you run the last command, you may be prompted to download the latest proactive check script.  Simply run the following command, `curl -O <enter the ftp site you are provided>`.
5. Upon completion of the script, you should find `hc_results.txt` or `hc_results.out` located at `/home/admin/proactive_check/`.  This is the file you need to share with your sales engineer.
