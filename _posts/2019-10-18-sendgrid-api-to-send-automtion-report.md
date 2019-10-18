---
layout: post
title: "QA Automation: Send Automation Report Using Sendgrid Email API"
date: 2019-10-18
---

This article explains the implementation of how to send an Automation execution report using [Sendgrid](https://sendgrid.com/docs/API_Reference/Web_API_v3/Mail/index.html). Implementing sending email option on test completion is good when stakeholders are interested in following up and understanding how stable is the application.   

<span style="color:blue">Pre-requisite</span>:
create account at [Sendgrid](https://app.sendgrid.com)  and generate api token. Sendgrid provides different plans to opt for. For testing, You can opt for free 100 emails/day plan.

<span style="color:blue">Project Background:</span>
Its a page object framework using Selenium Webdriver and TestNG. Tests are triggered with the help of a docker container and Kubernetes. Following dependencies are required to generate extent reports and send it as emails



```
<!-- https://mvnrepository.com/artifact/com.relevantcodes/extentreports -->
<dependency>
    <groupId>com.relevantcodes</groupId>
    <artifactId>extentreports</artifactId>
    <version>2.41.2</version>
</dependency>

<!-- https://mvnrepository.com/artifact/com.sendgrid/sendgrid-java -->
<dependency>
    <groupId>com.sendgrid</groupId>
    <artifactId>sendgrid-java</artifactId>
    <version>4.4.1</version>
</dependency>
```


Below code, the snippet is class which is used to send the report from its location via email. Make sure to update required fields like sender, recipient address and API key



```
public class SendReport {


    @AfterSuite(alwaysRun = true)
    public static void sendMail() throws IOException {
        Response response;

        Email from = new Email("<Sender Email>");
        String subject = "<Email Subject>";

        Email to = new Email("<Receiver Email Address>");
        Content content = new Content("text/plain", "Hello,\n" +
                "This is an Email generated on completion of Automated Tests\n");
        Mail mail = new Mail(from, subject, to, content);
        String reportDirectory = new File(System.getProperty("user.dir")).getAbsolutePath() + "/extent-reports";

        File file = new File(reportDirectory + "ExtentReportResults.html");
        byte[] fileData = null;
        try {
            fileData = IOUtils.toByteArray(new FileInputStream(file));
        } catch (IOException e) {
            e.printStackTrace();
        }


        Attachments attachments3 = new Attachments();
        Base64 x = new Base64();
        String imageDataString = x.encodeAsString(fileData);
        attachments3.setContent(imageDataString);
        attachments3.setFilename("AutomationReport.html");
        attachments3.setDisposition("attachment");
        attachments3.setContentId("Banner");
        mail.addAttachments(attachments3);

        MailSettings mailSettings = new MailSettings();
        Setting sandBoxMode = new Setting();
        sandBoxMode.setEnable(true);
        mailSettings.setSandboxMode(sandBoxMode);

        SendGrid sg = new SendGrid("<Your Sendgrid API Key>");
        Request request = new Request();
        try {
            request.setMethod(Method.POST);
            request.setEndpoint("mail/send");
            request.setBody(mail.build());
            response = sg.api(request);
        } catch (IOException ex) {
            System.out.println(ex);
        }
    }
}
```
