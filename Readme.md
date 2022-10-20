# HW13
This project realize scheme https://drive.google.com/file/d/15lfS8uYrx487FXjFjh8qjFGpqkhD0mVm/view. Where upper host is `gateway`. 

### Install
````
vagrant up --provision
````

### Settings
You can change variables in file `ansible_vars.yml`

### Check
````
vagrant ssh gateway
wget -O - mysite.com
````
Domain name `mysite.com` corresponds variable `site_domain` in `ansible_vars.yml`

### Uninstall
````
vagrant destoy
````
