# Apolloinfo
A vulnerability about apollo-adminservice Unauthorized sensetive info

1.Steps to reproduce (复现步骤)

Access http://host:8090/releases?releaseIds=1 via GET method and carry the releaseIds data。
All configuration information can be obtained by modifying the releaseIds parameter.

This configuration exists for all types of administrator configuration passwords, such as database, ftp, ssh, naocs

![image](https://github.com/user-attachments/assets/719d3861-a3ef-4dd4-a41b-e63235979001)


2.some code(相关代码)

Default ports 8090
https://github.com/apolloconfig/apollo/blob/49bd8ccab93c2484dacabd9d0709bb49efbdfc4b/apollo-portal/src/main/java/com/ctrip/framework/apollo/portal/api/AdminServiceAPI.java#L336

https://github.com/apolloconfig/apollo/blob/49bd8ccab93c2484dacabd9d0709bb49efbdfc4b/apollo-portal/src/main/java/com/ctrip/framework/apollo/portal/spi/configuration/AuthConfiguration.java#L84-L86

![image](https://github.com/user-attachments/assets/25023691-57e6-4eb4-a1de-839152895fd0)

![image](https://github.com/user-attachments/assets/65fd3f9b-9685-4719-bc4a-052f7b8b62f8)


3.Affected Version (受影响的版本)

Apollo 2.2.0 Release

4.fixes Recommendations (修复建议)

For fix this vuln， Here is my advices:
1.Limit unauthorized calls to related interfaces
2.Disable default port 8090 remote calls
