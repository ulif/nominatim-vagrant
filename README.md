# nominatim-vagrant

Vagrant boxes running OSM nominatim


## Installing Nominatim

Clone this repository:

    $ git clone https://github.com/ulif/nominatim-vagrant

Then change into the created repository:

    $ cd nominatim-vagrant/

The local `Vagrantfile` first configures a vagrant box based on Ubuntu 16.04,
installs databases, apache, etc. and then runs the local `installmaps.yml`
ansible playbook.installs map data from different countries.

Fire up vagrant:

    $ vagrant up ubuntu

This will take a remarkable amount of time, but in the end should give you a
running `virtualbox` where you can log into:

    $ vagrant ssh ubuntu

The database will exist but be _empty_ after this step.


## Installing maps

The desired set of countries, the available memory and other important values
can be set at top of `installmaps.yml`. Edit this file:

    $ nano installmaps.yml

Then, run the playbook. In a vagrant machine this can be done manually like
this:

    $ ansible-playbook --private-key=.vagrant/machines/ubuntu/virtualbox/private_key -u vagrant -i .vagrant/provisioners/ansible/inventory/vagrant_ansible_inventory installmaps.yml

This step will run for a very, very, very long time, depending on the country
you picked above. Larger datasets like europe or the world will take several
days even on strong machines with lots of RAM.

The nominatim service will be routed from vagrant port 80 to port 8089 of the
host. Edit `Vagrantfile` if you prefer a different port or similar.

Before proceeding, these steps must have been finished successfully.


## Using Nominatim

After install, the nominatim service is available at port 8089 of your host
machine. You can browse to

  ` http://localhost:8089/nominatim/search.php

to play with your new nominatim server.

Of course you can also talk via commandline:

    $ curl curl 'http://localhost:8089/nominatim/search.php?format=json&q=17,%20boulevard%20de%20suisse'
    [{"place_id":"100822","licence":"Data © OpenStreetMap contributors, ODbL 1.0. http:\/\/www.openstreetmap.org\/copyright",
    "osm_type":"way","osm_id":"94399519","boundingbox":["43.7379492","43.7383593","7.4217809","7.4224633"],
    "lat":"43.7381542","lon":"7.42217981938168","display_name":"Rose de France, 17, Boulevard de Suisse, Monte-Carlo, Monaco, 98000, Monaco",
    "class":"building","type":"yes","importance":0.301}]

Oh, and you need the map data of the country you query, of course.

