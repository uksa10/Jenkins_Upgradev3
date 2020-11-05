FROM tomcat:8.0
ADD java-tomcat-sample/target/**/*.war /usr/local/tomcat/webapps/
EXPOSE 8088
CMD ["catalina.sh", "run"]
