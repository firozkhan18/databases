
```java
package com.spring.batch.api.config;

import java.text.SimpleDateFormat;
import java.util.HashMap;
import java.util.Map;

import org.springframework.batch.core.Job;
import org.springframework.batch.core.Step;
import org.springframework.batch.core.configuration.annotation.JobBuilderFactory;
import org.springframework.batch.core.configuration.annotation.StepBuilderFactory;
import org.springframework.batch.item.ItemProcessor;
import org.springframework.batch.item.data.MongoItemReader;
import org.springframework.batch.item.xml.StaxEventItemWriter;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;
import org.springframework.core.io.FileSystemResource;
import org.springframework.data.domain.Sort;
import org.springframework.data.domain.Sort.Direction;
import org.springframework.data.mongodb.core.MongoTemplate;
import org.springframework.oxm.xstream.XStreamMarshaller;

import com.spring.batch.api.data.Person;
import com.spring.batch.api.util.MailUtil;

@Configuration

public class ApplicationConfig {

	@Autowired
	private JobBuilderFactory jobBuilderFactory;
	@Autowired
	private StepBuilderFactory stepBuilderFactory;
	@Autowired
	private MongoTemplate template;

	@Autowired
	private MailUtil util;

	@SuppressWarnings("serial")
	@Bean
	public MongoItemReader<Person> reader() {
		MongoItemReader<Person> reader = new MongoItemReader<Person>();
		reader.setTemplate(template);
		reader.setQuery("{}");
		reader.setTargetType(Person.class);
		reader.setSort(new HashMap<String, Sort.Direction>() {
			{
				put("_custId", Direction.DESC);
			}
		});
		return reader;
	}

	@Bean
	public StaxEventItemWriter<Person> writter() {
		StaxEventItemWriter<Person> writter = new StaxEventItemWriter<Person>();
		writter.setRootTagName("Persons");
		writter.setResource(new FileSystemResource("xml/bank.xml"));
		writter.setMarshaller(marshaller());
		return writter;
	}

	private XStreamMarshaller marshaller() {
		XStreamMarshaller marshaller = new XStreamMarshaller();
		Map<String, Class> map = new HashMap<>();
		map.put("Person", Person.class);
		marshaller.setAliases(map);
		return marshaller;
	}

	@Bean
	public Step step1() {
		return stepBuilderFactory.get("step1").<Person, Person>chunk(10).reader(reader()).processor(process())
				.writer(writter()).build();
	}

	@Bean
	public Job runJob() {
		return jobBuilderFactory.get("report generation").flow(step1()).end().build();
	}

	public ItemProcessor<Person, Person> process() {

		ItemProcessor<Person, Person> process = new ItemProcessor<Person, Person>() {

			@Override
			public Person process(Person person) throws Exception {
				if (person.getStatus().equalsIgnoreCase("Pending")) {
					String msg = util.sendEmail(person.getEmail(), buildMessage(person));
					System.out.println(msg);
					return person;
				}
				return null;
			}

			private String buildMessage(Person person) {
				String mailBody = "Dear " + person.getName() + "," + "\n" + "statement of your credit card ending with "
						+ person.hashCode() + "**" + " has been generated" + "\n" + "dues amount :"
						+ person.getOutstandingAmount() + "\n" + "last payment date : "
						+ new SimpleDateFormat("yyyy/MM/dd HH:mm:ss a").format(person.getLastDueDate()) + "\n" + "\n"
						+ "If you already paid please ignore this email" + "\n" + "Thanks for using our credit card ";
				return mailBody;
			}

		};
		return process;

	}

}
```
```java
package com.spring.batch.api.data;

import java.util.Date;

import org.springframework.data.annotation.Id;
import org.springframework.data.mongodb.core.mapping.Document;

import lombok.Getter;
import lombok.Setter;

@Getter
@Setter
@Document(collection = "Bank Users")
public class Person {
	@Id
	private int custId;
	private String name;
	private String email;
	private String contactNo;
	private Date dob;
	private String status;
	private double outstandingAmount;
	private Date lastDueDate;
}
```
```java
package com.spring.batch.api.util;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.mail.SimpleMailMessage;
import org.springframework.mail.javamail.JavaMailSender;
import org.springframework.stereotype.Component;

@Component
public class MailUtil {

	@Autowired
	private JavaMailSender sender;

	public String sendEmail(String to, String TextBody) {
		String msg = "";
		SimpleMailMessage message = new SimpleMailMessage();
		try {
			message.setTo(to);
			message.setText(TextBody);
			message.setSubject("Payment Dues Alert");
			message.setFrom("javatechie4u@gmail.com");
			sender.send(message);
			msg = "mail triggered successfully to : " + to;
		} catch (Exception e) {
			msg = e.getMessage();
		}
		return msg;
	}

}
```
```java
package com.spring.batch.api;

import org.springframework.batch.core.configuration.annotation.EnableBatchProcessing;
import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
import org.springframework.boot.autoconfigure.jdbc.DataSourceAutoConfiguration;

@SpringBootApplication(exclude = DataSourceAutoConfiguration.class)
@EnableBatchProcessing
public class SpringBatchMongoApplication {

	public static void main(String[] args) {
		SpringApplication.run(SpringBatchMongoApplication.class, args);
	}
}
```

application.properties
```
#DB
spring.data.mongodb.database=Person
spring.data.mongodb.host=localhost
spring.data.mongodb.port=27017

#Mail Properties
spring.mail.protocol=smtp
spring.mail.host=smtp.gmail.com
spring.mail.port=587
spring.mail.username=Enter ur email
spring.mail.password=Enter ur pwd
spring.mail.properties.mail.smtp.auth = true
spring.mail.properties.mail.smtp.starttls.enable = true
```

```pom
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
	<modelVersion>4.0.0</modelVersion>

	<groupId>com.example</groupId>
	<artifactId>spring-batch-mongo</artifactId>
	<version>0.0.1-SNAPSHOT</version>
	<packaging>jar</packaging>

	<name>spring-batch-mongo</name>
	<description>Spring batch using mongoDB and email notification</description>

	<parent>
		<groupId>org.springframework.boot</groupId>
		<artifactId>spring-boot-starter-parent</artifactId>
		<version>1.5.12.RELEASE</version>
		<relativePath /> <!-- lookup parent from repository -->
	</parent>

	<properties>
		<project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
		<project.reporting.outputEncoding>UTF-8</project.reporting.outputEncoding>
		<java.version>1.8</java.version>
	</properties>
	<dependencies>
		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-web</artifactId>
		</dependency>
		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-batch</artifactId>
		</dependency>
		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-data-mongodb</artifactId>
		</dependency>

		<dependency>
			<groupId>org.projectlombok</groupId>
			<artifactId>lombok</artifactId>
			<optional>true</optional>
		</dependency>
		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-test</artifactId>
			<scope>test</scope>
		</dependency>
		<dependency>
			<groupId>org.springframework.batch</groupId>
			<artifactId>spring-batch-test</artifactId>
			<scope>test</scope>
		</dependency>
		<dependency>
			<groupId>org.springframework</groupId>
			<artifactId>spring-oxm</artifactId>
		</dependency>
		<dependency>
			<groupId>com.thoughtworks.xstream</groupId>
			<artifactId>xstream</artifactId>
			<version>1.4.9</version>
		</dependency>
		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-mail</artifactId>
		</dependency>
	</dependencies>
	<build>
		<plugins>
			<plugin>
				<groupId>org.springframework.boot</groupId>
				<artifactId>spring-boot-maven-plugin</artifactId>
			</plugin>
		</plugins>
	</build>


</project>
```
