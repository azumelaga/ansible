# ansible
Ansible ikasten
Lehen adibidea: Hemen beste makina batean NGINX web zerbitzria instalatuko dugu.Horretarako destinuan python instalatuta egon beharko da. Frogatu dezakegu hau ere automatizatzen.

SSH bidez konetatuko gara. Horretarako klabeak sortuko ditugu:

ssh-keygen

Gero gure klabe publikoa bezeroan kopiatuko dugu:

ssh-copy-id -i /root/.ssh/id_rsa aitor@10.0.2.15

eta jarraian konektatu gaitezkeen edo ez probatuko dugu:
ssh aitor@10.0.2.15

Konexioak ondo daudenez ansible-ekin hasiko gara gure lehen playbook-a egiten

1.Direktorio bat sortuko dugu eta bertan hosts fitxategia sortuko dugu.
Bertan hau idatziko dugu.

[webserver]
10.0.2.15      //hau instalatu nahi dugun makinaren ip-a da
 gorde eta 

jarraian webserver.yml sortuko dugu. Kontuz espazio eta indentazioarekin. Nik bi espazio txuri erabiltzen ditut bakoitzarentzako.

---
- hosts: webserver
  remote_user: aitor
  tasks:
    - name: Install last version of NGINX
      apt: name=nginx state=latest
      become: yes
    - name: Start/Enable
      service:
       name: nginx
       state: started
       enabled: yes
      become: yes

Behin hau eginda.
