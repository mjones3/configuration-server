FROM openjdk:8-jdk-alpine
RUN  apk update && apk upgrade && apk add netcat-openbsd && apk add curl
RUN apk add --no-cache nss
RUN mkdir -p /usr/local/configserver
RUN cd /tmp/ && \
    curl -k -LO "http://cdn-files.evildayz.com/mirror/java/jce/jce_policy-8.zip" -H 'Cookie: oraclelicense=accept-securebackup-cookie' && \
    #curl -k -LO "http://download.oracle.com/otn-pub/java/jce/8/jce_policy-8.zip" -H 'Cookie: oraclelicense=accept-securebackup-cookie' && \
    #wget --no-check-certificate -c --header "Cookie: oraclelicense=accept-securebackup-cookie" http://download.oracle.com/otn-pub/java/jce/8/jce_policy-8.zip
    #wget \
    #--no-cookies \
    #--no-check-certificate \
    #--header "Cookie: gpw_e24=http%3A%2F%2Fwww.oracle.com%2F; oraclelicense=accept-securebackup-cookie" \
    #-O jce_policy-8.zip \
    #http://download.oracle.com/otn-pub/java/jce/8/jce_policy-8.zip
    
    unzip jce_policy-8.zip && \
    rm jce_policy-8.zip && \
    yes |cp -v /tmp/UnlimitedJCEPolicyJDK8/*.jar /usr/lib/jvm/java-1.8-openjdk/jre/lib/security/
ADD @project.build.finalName@.jar /usr/local/configserver/
ADD run.sh run.sh
RUN chmod +x run.sh
CMD ./run.sh
