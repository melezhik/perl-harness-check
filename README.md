# SYNOPSIS

Run tests against Perl test harness report

# Perl versions supported

* 5.20.1

Let me know if you want to support another Perl version.

# OS supported

* minoca

Let me know if you want support another OS.


# INSTALL


    $ sparrow plg install perl-harness-check


# USAGE

    $ cd /your/perl/source/distribution && make test 1>perl-test-report.txt &2>1 # run perl test harness
    $ cat perl-test-report.txt | sparrow plg run perl-harness-check # verify test report 


# Configuration

## os

Sets OS name for target server. Obligatory. Default value is `minoca`. 

## perl

Sets perl version. Obligatory. Default value is `5_20_1`


# Workflow

At the begining you've got some tests are passed and some are failed. It's ok. 
Succeeded perl tests are listed in  *default pass list* at [plugin default configuration 
file](https://github.com/melezhik/perl-harness-check/blob/master/suite.ini).



Aftewards you fix some OS level bugs and belive that a related perl test issues should be gone, you can run:

  
    $ cd /your/perl/source/distribution && make test 1>perl-test-report.txt &2>1

    $ cat perl-test-report.txt | sparrow plg run perl-harness-check --param should_pass=ext/POSIX/t/time.t 

    $ cat perl-test-report.txt | sparrow plg run perl-harness-check --param should_pass=io/fs.t 


Ok if you really see that bugs are gone create pull request to add succeeded test to default pass list.

# Author

[Alexey Melezhik](mailto:melezhik@gmail.com)


