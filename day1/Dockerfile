FROM centos:7
RUN yum -y install httpd ; systemctl enable httpd ; echo "NxZei" > /var/www/html/index.html
MAINTAINER Mohammed Nawaz
WORKDIR /var/www/html
COPY ./login.php ./login.php
CMD systemctl start httpd &&
