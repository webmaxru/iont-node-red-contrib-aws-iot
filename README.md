node-red-contrib-aws-iot-custom-auth
====================

A Node-Red node to read and write to the Amazon Web Services AWS IoT using the Custom Authorizer.

Install
-------

Run the following command in the root directory of your Node-RED install

    npm install node-red-contrib-aws-iot-custom-auth

Usage with custom authorizer
-----

Use "Custom Authorizer" type for your device and specify:
* Custom Authorizer Name (optional)
* Token Key  
* Token Value  
* Custom Authorizer Signature

You don't have to provide certificated in this case.

See more at https://docs.aws.amazon.com/iot/latest/developerguide/custom-auth.html


Usage with certificates
-----
					
+ Install your AWS certificates into your local folder where node-red can reach your directory
	
	Example: 
```
	/root/.agent/certs/-
					|--YourThingName.private.key
					|--YourThingName.cert.pem
					|--root-CA.crt
```
	YourThingName is the AWS Thing name what is the value you keyin when creating your thing/device.
	
+ Setup the **node-red-contrib-aws-iot-custom-auth** node with *AWS Certs* path pointed to /root/.agent/certs/
	
	Example: 
```
	awsCerts = /root/.agent/certs/
```

+ The final configuration will be used in the **node-red-contrib-aws-iot-custom-auth** code look likes:

```
	keyPath : '/root/.agent/certs/YourThingName.private.key',
	certPath : '/root/.agent/certs/YourThingName.cert.pem',
	caPath : '/root/.agent/certs/root-CA.crt',
	clientId : YourThingName,
	host : <YourAWSIoTCustomEndpoint>
```

See more at https://github.com/aws/aws-iot-device-sdk-js/blob/master/README.md#certificate-configuration 

This node is based on <a href="https://github.com/darrenchiu/iont-node-red-contrib-aws-iot" target="_new">iont-node-red-contrib-aws-iot</a> by <a href="https://github.com/darrenchiu">Darren Chiu</a>.

