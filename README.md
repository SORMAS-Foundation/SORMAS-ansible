# sormas-docker-ansible
Allows you to install the dockerized version of sormas via ansible.

Tested with following OS:<br>
Ubuntu 16 LTS<br>
Ubuntu 18 LTS<br>
<br><br>
## Prequisites
1. Change the remote_user inside the ansible.cfg to the user you want to execute the playbooks (make sure he has root privileges)
2. Tweak the vars inside vars/ folder to your needs.
3. Execute the install-galaxy-roles.sh to install the needed roles from the ansible-galaxy<br>
 <code>./install-galaxy-roles.sh</code>
4. Execute the site.yml<br>
<code>ansible-playbook site.yml</code>

## Important notes!
Depending on your current infrastructure, be sure to set the correct booleans under the "### LetsEncrypt variables ###" section inside vars/vars.yml to match your needs

### Installation with LetsEncrypt
If you want to use LetsEncrypt to secure your SORMAS installation<br>
<code>
use_letsencrypt: true

selfsigned_cert_generation: false

use_existing_certs: false

acme_mail: <your@email> # Make sure you set this to a valid address, otherwise the certificate generation will fail!</code>
### Installation behind a existing reverse proxy
The webserver will create selfsigned certificates to secure the connection between your existing reverse proxy and the webserver itself<br>
This option can also be used, to test the installation on your local workstation / inside a LAN environment<br>
<code>use_letsencrypt: false
selfsigned_cert_generation: true
use_existing_certs: false
</code>
### Installation with existing certificate
If you already have an existing certificate you want to use, place them inside the roles/webserver/files folder<br>
Make sure you name your fullchain-certificate fullchain.pem and your private key privkey.pem<br>
<code>use_letsencrypt: false
selfsigned_cert_generation: false
use_existing_certs: true
</code>

