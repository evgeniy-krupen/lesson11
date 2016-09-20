# lesson11

Please provide your PR for lesson 11

Student: [Evgeniy_Krupen](https://upsa.epam.com/workload/employeeView.do?employeeId=4060741400038655484#emplTab=general)

**1. First of all I downloaded Learning VM for Puppet and learned "Resources, Manifest, Class" articles.**
![](https://github.com/evgeniy-krupen/lesson11/blob/master/source/puppet_awesoe.png)

**2. I set up Puppet Standalone**

$ yum install puppet

I created manifest for nginx with content:

package { 'nginx':
        ensure=>'installed'
}

notify { 'Nginx is installed.':
}

service { 'nginx':
        ensure=>'running'
}

notify { 'Nginx is running.':
}

$ puppet parser validate ~/first_manifest.pp

**3. I set up 2 VM by [vagrant](https://github.com/evgeniy-krupen/lesson11/blob/master/Vagrantfile)**

for puppet server - 4096 MB RAM
for puppet client - 512 MB RAM

I installed puppet repo for centos 6.7

$ rpm -Uvh https://yum.puppetlabs.com/puppetlabs-release-pc1-el-6.noarch.rpm

$ yum install puppetserver (for server) puppet (cor client)

**4. Here instruction how to connect client with server**

checked on server : - facter fqdn

**on client:**


1. In /etc/hosts -> 192.168.25.100 chef-server chef-server.minsk.epam.com
2. Puppet agent -t --server chef-server.minsk.epam.com --waitforcert 60 --test
![](https://github.com/evgeniy-krupen/lesson11/blob/master/source/p1.png)

**on server:**

puppet cert --list - I saw request

puppet cert --sign web2.minsk.epam.com - I sign request

puppet cert list -a  - I checked all sertivicate which sign Puppet CA
![](https://github.com/evgeniy-krupen/lesson11/blob/master/source/p2.png)

**5. I set up ntp module on puppet server**

$ puppet module install puppetlabs-ntp

I created manifest on server:

$ vim [/etc/puppetlabs/code/environments/production/manifests/site.pp](https://github.com/evgeniy-krupen/lesson11/blob/master/site.pp)


After that I triggerd on client with [log](https://github.com/evgeniy-krupen/lesson11/blob/master/task11.log):

$ puppet agent --server chef-server.minsk.epam.com -t

I checked on puppet client ntp daemon

![](https://github.com/evgeniy-krupen/lesson11/blob/master/source/p3.png)





