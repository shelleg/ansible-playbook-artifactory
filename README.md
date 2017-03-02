Artifactory example playbook
============================

This playbook utilizes the original
[ansible-nexus3-oss](https://github.com/savoirfairelinux/ansible-nexus3-oss) by [samherve](https://github.com/samherve) which we will mostdefintelly contribute back once we complete.

What [Dan Hirsch](https://github.com/hackndoes) did in the dev branch fork
is add support for docker hosted, virtual & proxy repos, there is still
some work ... [ configuring docker privilidges, configure apache or and nginx to proxy docker registry and more ]


## QuickStart

```
git clone git@github.com:shelleg/ansible-playbook-nexus3.git
ansible-galaxy install -r requirements.yml
Vagrant up
```

#### Upon completion:

Navigate to http://vagrant_ip:nexus_port in this example `172.16.1.160:8081`
username: admin
password: changeme 

## How to contribute ?:
- Add support for all tyoes of repos ... 
    - pypi
    - npm
    - "raw"


## Customizing this for your needs
- See the recommended playbook @->  [here](https://github.com/savoirfairelinux/ansible-nexus3-oss/blob/master/README.md#example-playbook)
- Comments are awesome feel free to comment on code || open issues etc etc.



## list
registry="172.16.1.110:5000"
repos=`curl http://$registry/v2/_catalog?n=100 | jq '.repositories[]' | tr -d '"'`
for repo in $repos; do 
   curl http://$registry/v2/$repo/tags/list; 
done