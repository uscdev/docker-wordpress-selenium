# docker-wordpress-selenium
Framework to run Wordpress inside Docker and test it using docker-selenium 

## Steps to run

1) Run Docker swarm on your localhost using - "docker swarm init"
2) Build the test container using the command - "docker-compose build"
3) Run the containers using - "docker-compose up -d"

    a) 4 containers have been setup in the docker-compose file : Wordpress, Mysql, Selenium and Test.
    
    b) The Test container would likely fail to start since it does not wait for the Selenium and Wordpress container to come up entirely.
    
    c) The port exposed for Wordpress container is 80 on the host as well. This is since, if the port is something else (eg. xxxx) then whenever selenium tries to communicate with the wordpress on 80 (inside the docker network), wordpress redirects all requests to the exposed port xxxx.
    
4) Check if the Wordpress site is up, by going to http://localhost on your host computer. The wordpress site is exposed on port 80 of the host, so prior to starting this all processes running on 80 on your host computer should be stopped.

5) If the wordpress site is up, go through the setup procedure of wordpress and bring the basic site up.
6) Once the site is up, run "docker-compose run test" to run the test container. This container comes up and tests the docker wordpress installation using Selenium. It should print the Title of your website.

## To make changes to test

1) Bring the running containers down using "docker-compose down"
2) Make changes to the selenium test file.
3) Follow steps 2-6 from above.

