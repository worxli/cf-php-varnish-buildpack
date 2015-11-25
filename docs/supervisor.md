## Supervisor

This buildpack supports supervisor. If you need to have multiple "services" in the background, you can use this to start them and make sure they are running. We use them to start different PHP processes listening on rabbitmq messages.



|      Variable     |   Explanation                                        |
------------------- | -----------------------------------------------------|
| SUPERVISORD      | If supervisor should be used. set to true or false (without quotes)  |


### Configuration

All your config for supervisor works go into .bp-config/supervisor and end with *.ini

### Example

````
[program:varnishworker]
command=nice /home/vcap/app/php/bin/php console acme:varnish:worker -v

# Needs this process num so supervisor can distinguish between the instances
process_name=varnishworker_%(process_num)s

# Number of workers to run
numprocs=1

# Will always restart, no matter if its a normal close or an abnormal one
autorestart=true
````

