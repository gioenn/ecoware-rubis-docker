FROM rabbitmq

MAINTAINER Giovanni Quattrocchi <giovanni.quattrocchi@polimi.it>

RUN apt-get update
RUN apt-get -y install python
RUN apt-get -y install nano
ADD http://hg.rabbitmq.com/rabbitmq-management/raw-file/rabbitmq_v3_4_1/bin/rabbitmqadmin /usr/bin/rabbitmqadmin

RUN chmod u+x /usr/bin/rabbitmqadmin


