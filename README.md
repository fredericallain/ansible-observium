# Use ansible to setup obervium on Debian 11

## before everyhting, make sure you have installed the required component

    ansible-galaxy collection install community.mysql 
    ansible-galaxy collection install community.general

## Update all varariables in group_vars/all.yml

    ansible_user: <USERNAME>
    ansible_email: <MAIL@DOMAIN.TLD>
    systemd_dir: /etc/systemd/system

    system_timezone: "Europe/Paris"

    mysql_root_pass: ''
    new_mysql_root_pass: '<STRONGPASSWORD>'

    observium_db_user: <DB_USERNAME>
    observium_db_password: '<STRONGPASSWORD>'
    observium_admin_email: <MAIL@DOMAIN.TLD>
    observium_url: <DOMAIN.TLD>
    observium_admin_pass: "<STRONGPASSWORD>"

    snmp_auth_type: <AUTH_TYPE> # noAuthNoPriv | authNoPriv | authPriv
    snmp_location: <LOCATION>
    snmp_pass_algo: <PASS_ALGO> # MD5 | SHA
    snmp_crypto_algo: <CRYPTO_TYPE> # AES | DES
    snmp_username: <USERNAME>
    snmp_password: "<STRONGPASSWORD>"
    snmp_enryption: "<STRONGPASSPHRASE>"

## Auto add device
You can ask ansible to auto add your device by defining the list in /roles/observium.yml

> In "Add device from dictionnary" section

## Then use the command to start the setup
    ansible-playbook observium.yml

## After install is done, connect to the GUI using the url you've setup in all.yml
DOMAIN.TLD

> The login is "admin", the password id the one you set in observium_admin_pass

### Have fun !