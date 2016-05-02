# SYNOPSIS

elementary file system checks using df utility report 

# Dependencies

* df utility should be installed

# INSTALL

    sparrow plg install df-check

# CONFIGURE

    sparrow project create system
    sparrow check add system disk
    sparrow check set system disk df-check
    sparrow check ini system disk # skip this step if you want default settings 

# RUN        

    $ sparrow check run system disk

    /tmp/.outthentic/31966/home/vagrant/my/df-check/disk-shortage/story.t ..
    # Filesystem      Size  Used Avail Use% Mounted on
    # /dev/sda1       9.2G  7.4G  1.4G  85% /
    # udev             10M     0   10M   0% /dev
    # tmpfs           971M  8.4M  963M   1% /run
    # tmpfs           2.4G  4.0K  2.4G   1% /dev/shm
    # tmpfs           5.0M     0  5.0M   0% /run/lock
    # tmpfs           2.4G     0  2.4G   0% /sys/fs/cgroup
    # none            119G  110G  9.7G  92% /vagrant
    # OK
    # threshhold: 93
    ok 1 - output match /(\S+)\s+(\S+)\s+(\S+)\s+(\S+)\s+(\S+)/
    ok 2 - enough disk space (85%) on /dev/sda1
    ok 3 - enough disk space (0%) on udev
    ok 4 - enough disk space (1%) on tmpfs
    ok 5 - enough disk space (1%) on tmpfs
    ok 6 - enough disk space (0%) on tmpfs
    ok 7 - enough disk space (0%) on tmpfs
    ok 8 - enough disk space (92%) on none
    1..8
    ok
    All tests successful.
    Files=1, Tests=8,  0 wallclock secs ( 0.01 usr  0.01 sys +  0.08 cusr  0.00 csys =  0.10 CPU)
    Result: PASS
    
# Suite.ini

    # disk used threshold in %
    threshold = 80
    
# Author

[Alexey Melezhik](mailto:melezhik@gmail.com)
