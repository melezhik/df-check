# SYNOPSIS

elementary file system checks using df utility report 

# Dependencies

* df utility should be installed

# Install

    sparrow index update
    sparrow plg install df-check
    sparrow project create system
    sparrow check add system disk
    sparrow check set system disk df-check
    sparrow check ini system disk # skip this step if you want default settings 
        

    # and finally run:

    sparrow check run system disk


# Configuration

suite.ini : 

    [disk]
    # disk used threshold in %
    threshold = 80
    
    
# Output

    vagrant@Debian-jessie-amd64-netboot:~/my/df-check$ strun
    /tmp/.outthentic/6832/home/vagrant/my/df-check/disk-shortage/story.t ..
    ok 1 - perl /home/vagrant/my/df-check/disk-shortage/story.pl succeeded
    ok 2 - stdout saved to /tmp/.outthentic/6832/UJtafDBH5d
    # threshhold: 80
    # verify ... /dev/sda1
    # verify ... udev
    # verify ... tmpfs
    # verify ... tmpfs
    # verify ... tmpfs
    # verify ... tmpfs
    # verify ... none
    # verify ... none
    ok 3 - output match /(\S+)\s+(\S+)\s+(\S+)\s+(\S+)\s+(\S+)/
    ok 4 - enough disk space (76%) on /dev/sda1
    ok 5 - enough disk space (0%) on udev
    ok 6 - enough disk space (1%) on tmpfs
    ok 7 - enough disk space (1%) on tmpfs
    ok 8 - enough disk space (0%) on tmpfs
    ok 9 - enough disk space (0%) on tmpfs
    not ok 10 - enough disk space (90%) on none
    not ok 11 - enough disk space (90%) on none
    
    #   Failed test 'enough disk space (90%) on none'
    #   at /usr/local/share/perl/5.20.2/Outthentic.pm line 123.
    
    #   Failed test 'enough disk space (90%) on none'
    #   at /usr/local/share/perl/5.20.2/Outthentic.pm line 123.
    1..11
    # Looks like you failed 2 tests of 11.
    Dubious, test returned 2 (wstat 512, 0x200)
    Failed 2/11 subtests
    
    Test Summary Report
    -------------------
    /tmp/.outthentic/6832/home/vagrant/my/df-check/disk-shortage/story.t (Wstat: 512 Tests: 11 Failed: 2)
      Failed tests:  10-11
      Non-zero exit status: 2
    Files=1, Tests=11,  0 wallclock secs ( 0.02 usr  0.01 sys +  0.05 cusr  0.00 csys =  0.08 CPU)
    Result: FAIL
    
# Author

[Alexey Melezhik](mailto:melezhik@gmail.com)
