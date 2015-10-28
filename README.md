# dubboResearch
20151028
--------------------------------
一、建立dubbo项目
  0.依赖jar包
  必需依赖
JDK1.5+
  缺省依赖
通过mvn dependency:tree > dep.log命令分析，Dubbo缺省依赖以下三方库：
[INFO] +- com.alibaba:dubbo:jar:2.1.2:compile
[INFO] |  +- log4j:log4j:jar:1.2.16:compile 
[INFO] |  +- org.javassist:javassist:jar:3.15.0-GA:compile
[INFO] |  +- org.springframework:spring:jar:2.5.6.SEC03:compile
[INFO] |  +- commons-logging:commons-logging:jar:1.1.1:compile
[INFO] |  \- org.jboss.netty:netty:jar:3.2.5.Final:compile


  1.provider 服务生产者
      1,1 provider.xml
        <?xml version="1.0" encoding="UTF-8" ?> 
        - <beans xmlns="http://www.springframework.org/schema/beans" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:dubbo="http://code.alibabatech.com/schema/dubbo" xsi:schemaLocation="http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans.xsd http://code.alibabatech.com/schema/dubbo http://code.alibabatech.com/schema/dubbo/dubbo.xsd">
        - <!--  具体的实现bean 
          --> 
          <bean id="demoService" class="com.unj.dubbotest.provider.impl.DemoServiceImpl" /> 
        - <!--  提供方应用信息，用于计算依赖关系 
          --> 
          <dubbo:application name="xixi_provider" /> 
        - <!--  使用multicast广播注册中心暴露服务地址 <dubbo:registry address="multicast://224.5.6.7:1234" 
        		/> 
          --> 
        - <!--  使用zookeeper注册中心暴露服务地址 
          --> 
          <dubbo:registry address="zookeeper://192.168.1.166:2181" /> 
        - <!--  用dubbo协议在20880端口暴露服务 
          --> 
          <dubbo:protocol name="dubbo" port="20880" /> 
        - <!--  声明需要暴露的服务接口 
          --> 
          <dubbo:service interface="com.unj.dubbotest.provider.DemoService" ref="demoService" /> 
          </beans>
       1,2 
  2.costormer 服务消费者
  3.zookeep注册中心
