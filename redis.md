# Delete all the keys of the currently selected DB
    127.0.0.1:6379>FLUSHALL  or flushall
    
# select database

the number of databases is defined in the configuration file with the databases directive (the default value is 16). To switch between the databases, call SELECT.
    127.0.0.1:6379>select <1>
