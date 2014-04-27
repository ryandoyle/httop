# What is it? #
It's _top_ for Apache, getting its data from mod\_status.

# Requirements #
- ruby => 1.8.7 (no gems)
- curl
- mod\_status available at http://localhost/server-status
- ncurses (for `tput`)
- a wide terminal window (wraps if it's less than 146 characters)

# Hasn't this already been done? #
Yeah, I did find that out afterwards. There's one called [Apachetop](https://github.com/JeremyJones/Apachetop) that scrapes mod\_status and another of the [same name](http://clueful.shagged.org/apachetop/) (link dead) that watches log files. I prefer getting the information using the former method.

# Installing #
### Without a package manager ###
    scp httop my-apache-server:
    ssh my-apache-server
    ./httop

### Using RPM ###
You're going to need `rpmbuild` and `rake` installed to build the RPM
```
rake rpm
scp rpm/RPMS/noarch/httop-*.rpm my-apache-server:
rake clean
ssh my-apache-server
sudo rpm -Uvh httop-*.rpm
```
