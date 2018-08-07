## 批量发送工资条  
**功能简介:** 读取excel中工资条数据，并批量发送邮件,功能比较简单，仅用于学习。   
**步骤介绍:** 
- 工资条模板格式

  |姓名|工资项1|工资项2|....|工资项n|邮件地址|
  |---|---|---|----|----|---|
  | | | | | | |
  
  *首列必须为接收人姓名,最后一列必须为对应的接收人邮件地址。*
1. 用户打开网页，上传excel，服务器进行数据检查，然后返回检查结果，如果检查通过则返回将会下发的工资条数量，并要求用户填写邮件主题
2. 用户填写邮件主题，并确定发送
3. 服务器启动一个线程进行批量发送，每次发送工资条的数量可以配置。
4. 服务器启动线程后，用户可以看见发送进度，发送进度以"饼形"显示(使用了两种实现方式，一种是浏览器定时轮询，一种是websocket服务器实时通知)
5. 如果由于邮件较多，用户没有时间等待，关闭了网页，后续想看进度如何，仍可以输入网址查看。  
>  说明:邮件批量发送是以主题分类，如果用户上传了多次exel属于同一主题，则进度会进行合并显示;
        如果发送过程中，有的邮件发送失败，则将在前端页面显示，用户可以选择重发，都发送成功后，用户可以选择删除服务器硬盘保存的excel及数据库发送记录。
 
**开发环境:**  
  - Intellij idea 2017
  - Windows10
  - JDK1.8
  - Mysql5.7.21  
  
**开发技术:**   
  - Springboot1.5.12
  - Mybatis1.3.2
  - Websocket
  - Jquery3.1.1
  - Thymeleaf
  - ECharts3.2.3
  
**部分截图:**    

  成功发送的邮件状态截图:   
  ![邮件状态](https://picabstract-preview-ftn.weiyun.com:8443/ftn_pic_abs_v2/d7d71df71a1866c21e522329aacf20e0f0a8b978a5899eed460ebc66dd9bf0db222be351e285ea368d834fdb144e2276?pictype=scale&from=30111&version=3.3.3.3&uin=542600078&fname=email%20status.png&size=750)
  
  发送失败的邮件状态截图:     
  ![邮件状态](https://picabstract-preview-ftn.weiyun.com/ftn_pic_abs_v3/ce846c2aea63557e2819e6da390e7d68e2165ec064bbc0342aa178302fc944917f7f4cf701520bbfe6d3b93c2c7846b6?pictype=scale&from=30113&version=3.3.3.3&uin=542600078&fname=failed_sending.png&size=750)
  
  
  
  
