This repository contains java sdk and samples for Merchant API.

Prerequisites:
---------------
*	Java jdk-1.5 or higher
*	Apache Maven 3 or higher
*	Please refer http://maven.apache.org/guides/getting-started/maven-in-five-minutes.html for any help in Maven.

To build sdk and samples:
--------------------------
*	Build core files from https://github.com/paypal/sdk-core-java, as it is a dependency for sdk.
*	Then, run 'mvn install' to build sdk jar and sample war files.

SDK Integration:
----------------
*	Create a new maven application.

*	Add dependency to sdk in your application's pom.xml as below.
		
		<dependency>
			<groupId>com.paypal.sdk</groupId>
			<artifactId>merchantsdk</artifactId>
			<version>2.0.96</version>
		</dependency>
		
To make an API call:
--------------------			
*	Import PayPalAPIInterfaceServiceService.java into your code.
		
*	Copy the configuration file 'sdk_config.properties' in 'merchantsample/src/main/resources' folder to your application 'src/main/resources'. And load it using,  
		  
		new PayPalAPIInterfaceServiceService(this.getClass().getResourceAsStream("/sdk_config.properties"));
	
*	Or load the configuration file from any location using absolute path with the below method calls as required.

          new PayPalAPIInterfaceServiceService(new File(" .../sdk_config.properties"));
                                 Or
		  new PayPalAPIInterfaceServiceService(new InputStream(new File(" .../sdk_config.properties")));
                                 Or
          new PayPalAPIInterfaceServiceService(" .../sdk_config.properties");
  
*	Create a service wrapper object.

*	Create a request object as per your project needs. 

*	Invoke the appropriate method on the service wrapper object.

For example,

          
	  import urn.ebay.api.PayPalAPI.PayPalAPIInterfaceServiceService;
	  import urn.ebay.api.PayPalAPI.TransactionSearchReq;
	  import urn.ebay.api.PayPalAPI.TransactionSearchRequestType;
	  import urn.ebay.api.PayPalAPI.TransactionSearchResponseType;
	  ...
	  
          
          
      TransactionSearchReq txnreq = new TransactionSearchReq();
	  TransactionSearchRequestType requestType = new TransactionSearchRequestType();
	  
	  requestType.setStartDate("2011-10-04T00:00:00.000Z"); 
	  requestType.setEndDate("2011-10-05T23:59:59.000Z"); 
	  requestType.setVersion("95.0");
	  requestType.setTransactionID(request.getParameter("transactionID"));
	  txnreq.setTransactionSearchRequest(requestType);
	  
      PayPalAPIInterfaceServiceService service = new PayPalAPIInterfaceServiceService(this.getClass().getResourceAsStream("/sdk_config.properties"));
	  //username is optional
	  TransactionSearchResponseType txnresponse = service.transactionSearch(txnreq, username);
		  

SDK Logging:
------------
*	For logging - java.util.logging has been used. To change the default configuration, edit the logging.properties file in 'jre/lib' folder under your JDK root.		  

		  
SDK Configuration:
------------------
The SDK uses .properties format configuration file. Sample of this file is at 
 
'merchantsample/src/main/resources/'. You can use the 'sdk_config.properties' configuration file to configure

*	(Multiple) API account credentials.

*	HTTP connection parameters.

*	Service configuration.


For additional information on Merchant API, please refer to https://www.x.com/developers/paypal/documentation-tools/api

Instant Payment Notification(IPN) 
---------------------------------
* Please refer readme  at 'merchantsample/IPN-README.md'


