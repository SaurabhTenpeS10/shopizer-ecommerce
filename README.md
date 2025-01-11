# What is Shopizer
## Shopizer Headless Commerce

Shopizer is enterprise open source e-commerce software for retailers who want flexibility, speed and control of their commerce platform. Shopizer is a software solution that gives organizations the ultimate flexibility to take an experience-first approach to commerce, with simple powerful APIs and built in stores models.

Key technical benefits

Built with Spring framework
Vulnerability checks
Open source and open standards
Cloud Ready: Deploy Shopizer in the public
or private cloud on Amazon Webservices (AWS), Microsoft
Azure or Google Cloud Platform (GCP)
Run on premise servers
Run from Docker containers
Run from any Java servlet containers such as Tomcat
Shopizer is a an application composed of a set of services written in Java that serves functionality needed to build entreprise e-commerce systems.

The software can be used out of the box as a complete ready to use web application including a few web stores templates you can choose from. Shopizer can also be used as a restful backend application for serving a whole set of commerce REST apis on which you can build your own tailored e-commerce front store.

Shopizer e-commerce system provides the following functionality:

Catalog and products management
Shopping cart
Content management
Marketing components
Smart pricing
Ordering
Payment
Shipping
Scope	Features
Software	Supports MySQL
Supports Postgresql
Supports MariaDB
Supports H2
Java - Spring Boot
REST API
Cloud centric
Container based
Open source Apache v2 licence
Catalog management	SKU based product management
One to many prices per item
Simple time based promotion
Complex promotions (Based on JBoss Drools)
Category hierarchy
Product options
Product variants
Custom product properties
B2C
B2B
C2C
Multiple stores
Promotions	Promotions applicable at item level
Promotions applicable at cart level
Customer management	Self serve customer entry point
Social authentication
Customer registration
Rule based engine
Multiple currency
Ordering	Multiple payment modules
Multiple shipping modules
Promotions based on shipping rules
Promotions based vatious property (quantity of items, customer...)
REST API	Administration api
Products api
Customer api
Order api
Cart api
Shipping api
Payment api
User api
Search
Search	Based on Elastic Search and Open Search
Search items
Search autocomplete
Languages	Our language translator converts to multiple language

# Build from the source files. Open a terminal or console

sh
git clone git@github.com:shopizer-ecommerce/shopizer.git
cd shopizer
Build using Maven

sh
mvnw clean install
This command should result in a success message. If you have any errors during this process and require assistance,feel free to use Shopizer forum. See Shopizer forum for asking or searching Shopizer build related questions.

Start Shopizer

sh
cd sm-shop
mvnw spring-boot:run
Once the terminal or console displays that Shopizer is running and listening on service port and ready to be used.

Open a browser and type url localhost:8080

This will open Shopizer headless api. You can view all application interfaces available by opening localhost:8080/swagger-ui.html

Build and run Shopizer Angular administration app
Angular App

Angular app consuming Shopizer administration services endpoints

sh
git clone git@github.com:shopizer-ecommerce/shopizer-admin.git
cd shopizer-admin
Build using npm

sh
npm i
Start app

sh
ng serve -o
Open a browser on localhost:4200

Username: admin@shopizer.com

Password: password

All software requirements for Node and Angular are specified in README.md file int the project root


## Run Shopizer with Docker Compose
Docker

Shopizer can be run from Docker containers. The following instructions will run Shopizer Headless, Shopizer Shop App, Shopizer Admin App and Mysql

sh
git clone git@github.com:shopizer-ecommerce/shopizer-docker-compose.git
cd shopizer docker compose
Now run Docker containers

sh
docker compose up -d
Open a browser on this urls

Application	Url
Headless	localhost:8080
Shop	localhost:3000
Admin	localhost:4200
Admin app credentials

Username: admin@shopizer.com

Password: password

Build and run Shopizer
The purpose of this section is to provide new users with the basics of Shopizer e-commerce framework in order to get started in their projects. It will walk the reader through the steps of installing and configuring Shopizer as well as running demo application locally.

These instructions are for running legacy Shopizer with JSP frontends as well as Shopizer backend version with Angular admin and React shop front.

Build Shopizer
Java Backend


Build Shopizer store React app
React App

This is a showcase React app consuming Shopizer services endpoints

From a terminal or console

sh
git clone git@github.com:shopizer-ecommerce/shopizer-shop-reactjs.git
cd shopizer-shop-reactjs
Build using npm

sh
npm i
This command should result in a success message. If you have any errors during this process and require assistance,feel free to use Shopizer forum. See Shopizer forum for asking or searching Shopizer build related questions.

Start app

sh
npm run dev
Once the terminal or console displays that Shopizer is running and listening on service port and ready to be used.

All software requirements for Node js are specified in README.md file int the project root

# Architecture
## Shopizer Architecture

Shopizer is enterprise open source e-commerce software for retailers who want flexibility, speed and control of their commerce platform. Shopizer is a software solution that gives organisations the ultimate flexibility to take an experience-first approach to commerce, with simple powerful APIs and built in store models.

Key technical benefits
Headless commerce
Services built with Spring framework (Spring boot, Spring Security)
Front end Angular - React - Vuejs
CICD, Vulnerability checks
Open source and open standards
On Prem - Cloud
Run from containers or from individual processes (npm, tomcat)
Extensions are built as spring starter components
Shopizer Architecture

Integrationss
Shopizer supports integration with external payment and shipping modules such as Stripe, Fedex, Braintree, Square USPS and more. A set of module extensions allows using various content management storage such as JBoss Infinispan, AWS S3 and external web servers such as NGINX or Apache server. Elastic and Open Searh provide searching functionality.

A REST api exposes all commerce functionality (B2C, B2B, C2C, Multi-Stores) as well as complete system administration. Spring Security configured out of the box with JWT Bearer token authentication provides application interface authentication and authorization.

## Authentication API Reference
Administration authentication
Administration API (/private) require authentication. Authentication is performed through an endpoint accepting administration username and password. Subsequent calls to all private api require the presence of a Bearer token in the request header.

Method:

POST

Url:

/api/v1/private/login

Body:

js
{
  "username":"admin@shopizer.com",
  "password":"password"
}
Response:

status: OK

code: 200

js
{
    "id": 1,
    "token": "...eyJhbGciOiJIUzUxMiJ9....."
}
Private (admin) api subsequent requests require the token to be sent in the request header

sh
curl --location --request GET 'http://localhost:8080/api/v1/private/product/types' \
--header 'Authorization: Bearer ...eyJhbGciOiJIUzUxMiJ9.....' \
--header 'Content-Type: application/json'
Swagger documentations
All apis are described on Swaggerhub Shopizer repository

Shopize Swagger Documentationhttps://app.swaggerhub.com/apis-docs/shopizer/shopizer-rest-api/3.0.1

## Product API Reference
Product characteristics
Products can be configured with characteristics. Characteristics are defined outside of the product and can used during the configuration of different products.

Product types
Product brands
Product options
Products can have options. Options are used to differenciate products having the same definition. For instance, a product color or a product size are options of the same base product. Options are defined outside of the product and can used during the configuration of different products.

Product options
Product definition
Product definition is product metadata that defines core non variables elements of a product. For instance a t-shirt is a basic product definition. A product definition has no variants attached. It contains basic characteristiques, core attributes and dynamic attributes.

Product definition
Product images
Product
Product definition returns product summary usefull when working on a product management perspective. Product api returns complete object with composition rules and should be used when listing products or getting product details.

Product
Product properties (attributes)
Properties (attributes) adds extension to the product core attributes by allowing the creation of custom properties (attributes).

Product custom properties
Product variations (options)
Variations of product definitions.

Product variations
Product variants
Product variants are product definitions with variations attached to it. A single product definition can have multiple product variants. Each product variant has its own sku.

Product variants
Product variants group
Product classification
Products are classified in Category.

Product category
List products
List products with pagination and filters for a specific Merchant Store and Language.

Product listing
Search products
Full Text search and Auto complete keywords using Search server such as Elastic Search and Open Search

Product search
Swagger documentations
All apis are described on Swaggerhub Shopizer repository

## Shopize Swagger Documentationhttps://app.swaggerhub.com/apis-docs/shopizer/shopizer-rest-api/3.0.1

Product with variants
Products can be configured with characteristics. Characteristics are defined outside of the product and can used during the configuration of different products.

Product with variants

## Database configuration
Shopizer has been tested and supports H2, MySQL (recommended), MariaDB and Postgresql databases. Shopizer comes pre-configured with H2 database. H2 is an embedded database (http://www.h2database.com) configured by default to save data on files.

This pre-configuration should only be used for testing and never be used in a production environment.

Configure Shopizer with H2 database
By default H2 files are saved into your application server runtime directory. To change the location where the files have to be saved, edit sm-shop/src/main/resources/database.properties and edit the line

sh
db.jdbcUrl=jdbc\:h2\:file\:c:/SALESMANAGER;AUTOCOMMIT\=OFF;INIT\=CREATE SCHEMA IF NOT EXISTS SALESMANAGER
Make sure the file path is a valid existing directory. In this case the configuration file will be saved in c:\

Configure Shopizer with MySQL
Log to your MySQL as root and create schema SALESMANAGER

sh
mysql>CREATE DATABASE SALESMANAGER;
mysql>GRANT USAGE, SELECT ON *.* TO <YOUR USERNAME>@localhost IDENTIFIED BY '<YOUR PASSWORD>' with grant option;
mysql>GRANT ALL ON SALESMANAGER.* TO <YOUR USERNAME>@localhost;
mysql>GRANT FILE ON *.* TO <YOUR USERNAME>@localhost;
mysql>FLUSH PRIVILEGES;
Example

sh
mysql>CREATE DATABASE SALESMANAGER;
mysql>GRANT USAGE, SELECT ON *.* TO testuser@localhost IDENTIFIED BY 'password' with grant option;
mysql>GRANT ALL ON SALESMANAGER.* TO testuser@localhost;
mysql>FLUSH PRIVILEGES;
Create user that can connect from everywhere

sh
mysql>CREATE USER 'mysuer'@'%' IDENTIFIED BY 'mypassword';
mysql>GRANT USAGE, SELECT ON MYDB.* TO 'mysuer'@'%' with grant option;
mysql>GRANT ALL ON MYDB.* TO 'mysuer'@'%';
mysql>FLUSH PRIVILEGES;
Edit sm-shop/src/main/resources/database.properties

sh
db.jdbcUrl=jdbc:mysql://localhost:3306/SALESMANAGER?autoReconnect=true&useUnicode=true&characterEncoding=UTF-8
db.user=YOUR USERNAME
db.password=YOUR PASSWORD
db.driverClass=com.mysql.jdbc.Driver
hibernate.dialect=org.hibernate.dialect.MySQL5InnoDBDialect
db.preferredTestQuery=SELECT 1

db.schema=SALESMANAGER
hibernate.hbm2ddl.auto=update
Note: Database and table names are not case sensitive in Windows, and case sensitive in most varieties of Unix-Linux. Consequently MySQL which uses lower case schema and table names will not be able to see the schema and tables which are created upper case in Shopizer. If you get an exception of a table not being found and being displayed in lower case in the error message, you will have to specify this property in My.cnf. To resolve the issue set the lower_case_table_names to 1 in My.cnf configuration file.

Edit My.cnf

sh
lower_case_table_names=1
Configure Shopizer with Postgresql
Create a new postgresql

sh
CREATE DATABASE SHOPIZER;
Create schema

sh
CREATE SCHEMA salesmanager;
Edit sm-shop/src/main/resources/database.properties

sh
#POSTGRES
db.jdbcUrl=jdbc:postgresql://localhost:5432/SHOPIZER
db.user=postgres
db.password=password
db.driverClass=org.postgresql.Driver
hibernate.dialect=org.hibernate.dialect.PostgreSQLDialect
db.preferredTestQuery=SELECT 1

db.schema=SALESMANAGER
hibernate.hbm2ddl.auto=update
Edit shopizer/pom.xml

Un-comment both postgresql dependency

sh
<!--  postgres 
		<dependency>
			<groupId>org.postgresql</groupId>
			<artifactId>postgresql</artifactId>
		</dependency>
		-->

## Emails configuration
Shopizer supports 2 methods for sending emails:

smtp (default)
AWS Simple Email Service (ses)
SMTP Configuration (Default method)
This can be done by configuring SMTP connectivity at the server level from Shopizer administration console. When logging in the console move to Configurations and then to Email settings. SMTP configuration uses underlying Spring SpringHtmlEmailSender for sending HTML based emails.

Protocol: SMTP or SMTPS (this depends on SMTP provider. It usualy is SMTPS) Host: SMTP server host Post: Most of the time either 25 or 465 Username: SMTP server attributed username Password: SMTP server attributed password Requires authentication: Should always be true TLS: Should always be true (Usualy mentioned by SMTP provider)

Shopizer configuration

Make sure shopizer-core.properties in sm-core project is configured fot smtp method before starting the server.

sh
config.emailSender=default
SES (AWS Simple Email SDK)
This method uses AWS SDK implementation to perform SMTP(S) connectivity. AWS SES SDK is already included in Shopizer Maven POM file.


<!-- https://mvnrepository.com/artifact/com.amazonaws/aws-java-sdk-ses -->
    <dependency>
      <groupId>com.amazonaws</groupId>
      <artifactId>aws-java-sdk-ses</artifactId>
    </dependency>

## Shopizer configuration

Make sure shopizer-core.properties in sm-core project is configured fot ses method before starting the server. It requires 2 specific property for connecting to AWS Simple Email Service (ses method and region in which ses is configured in your AWS account)

sh
config.emailSender=ses
config.emailSender.region=US_EAST_1
User model
Business rules
Role	Description
superadmin	Can create, modify any user of any stores
admin	Can create, modify any user from its pertaining store
admin_store	Can create, modify any user from its pertaining store
admin_retail	Can only modify their profile, Deletion is not supported
Global Rules
User even if superuser can’t change roles
Superuser can’t create superuser
Admins can’t delete or modify superuser
Pages rules
User List
When login in as super admin all users are displayed in the list
When login in a any other admin only users from same store are displayed in the list
User cannot delete himself, he has to rely on other admin
Create / modify user page
Cannot assign group to superadmin
Self cannot edit it’s own groups
Self cannot change merchant store
Default selected merchant is current user merchant
Schema
USERMERCHANT_STORESM_GROUPUSER_GROUPPERMISSION_GROUPPERMISSION

Users belong to MERCHANT_STORE. Users are assigned to groups having predefined sets of permissions.

User database tables
