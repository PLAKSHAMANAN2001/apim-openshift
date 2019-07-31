FROM centos:7
MAINTAINER lakshmanan@wso2.com

# Create group and add user wso2
RUN groupadd admin
RUN useradd -g admin wso2


# Copy the necessary product zip.
COPY files/product/jdk1.8.0_221 /Users/laks/Downloads/wso2demo/dockerimg/wso2/jdk1.8.0_221
COPY files/product/wso2am-2.6.0 /Users/laks/Downloads/wso2demo/dockerimg/wso2/wso2am-2.6.0
COPY files/lib/mysql-connector-java-8.0.12.jar /Users/laks/Downloads/wso2demo/dockerimg/wso2/wso2am-2.6.0/repository/components/lib/mysql-connector-java-8.0.12.jar

# Copy config file/s.
COPY files/apim/axis2.xml /Users/laks/Downloads/wso2demo/dockerimg/wso2/wso2am-2.6.0/repository/conf/axis2/axis2.xml

# Give permission to the user.
RUN chown -R wso2:admin /Users/laks/Downloads/wso2demo/dockerimg/wso2

# Switch to user wso2.
USER wso2

# Set environment variables.
ENV JAVA_HOME=/Users/laks/Downloads/wso2demo/dockerimg/wso2/jdk1.8.0_221

# Set working directory
WORKDIR /Users/laks/Downloads/wso2demo/dockerimg/wso2/wso2am-2.6.0

# Expose ports
EXPOSE 8280 8243 9763 9443 9099 5672 9711 9611 7711 7611 10397

ENTRYPOINT ["bin/wso2server.sh"]
