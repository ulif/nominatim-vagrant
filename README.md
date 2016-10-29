# nominatim-vagrant

Vagrant boxes running OSM nominatim


## Install

Clone this repository:

    $ git clone https://github.com/ulif/nominatim-vagrant

Then change into the created repository and clone `Nominatim` inside it:

    $ cd nominatim-vagrant/
    $ git clone --recursive https://github.com/twain47/Nominatim.git

Fire up vagrant:

    $ vagrant up ubuntu

This should give you a running `virtualbox` where you can log in:

    $ vagrant ssh ubuntu

Before proceeding, these steps must have been finished successfully.