---
layout: page
title: "Q228984: Using Certificate Server 2.0 to Generate a Server Certificate"
permalink: /kb/228/Q228984/
---

## Q228984: Using Certificate Server 2.0 to Generate a Server Certificate

{% raw %}

	Article: Q228984
	Product(s): Internet Information Server
	Version(s): 5.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 25-FEB-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Internet Information Services version 5.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Certificate Server 2.0 can be used to generate server certificates (as well as
	other types) for use with Internet Information Services (IIS) 5.0. The
	procedures described in this article assume that you have Certificate Server 2.0
	installed as a Root Certificate authority (this is not a requirement for this to
	work; however, it adds more complexity to the steps you must follow). You must
	also have IIS 5.0 running on this computer (this does not need to be the
	computer that you are enabling SSL/TLS on).
	
	MORE INFORMATION
	================
	
	First, create a certificate request file. This file contains information about
	you, as well as your public key (a public and private key are created when you
	make this request). For this key to be valid, it must be signed by a root
	authority. Certificate Server 2.0 can act as a root authority.
	
	
	When the request file has been generated, submit that request to Certificate
	Server 2.0. Perform the following steps to accomplish this:
	
	1. Open Internet Explorer and browse to the site "http://certificate
	  server/certsrv" (without the quotation marks). The Certificate Server in this
	  URL is the name of the computer that the Certificate Server is running on.
	
	2. You should receive a page with several options on it. Choose the Request a
	  Certificate option, and then click Next.
	
	3. Under Choose Request Type, select Advanced Request, and then click Next.
	
	4. The Web Site Certificate Wizard that generates your key request file uses the
	  standard PKCS #10 (Certificate Request file) format. Choose the Submit a
	  certificate request using a base64 encoded PKCS #10 file or a renewal request
	  using a base64 encoded PKCS #7 file option, and then click Next.
	
	5. On the next screen, you are presented with two forms. The first form is for
	  the text of your certificate request file. can browse to the file or simply
	  copy and paste the file (be sure you do not change the format in any way if
	  you do this). If you browse to the file, be sure that you click the button to
	  read the file. Either way, you should see your certificate request file in
	  the top form. When you have accomplished this, click Next.
	
	6. Your request should have been received. If you receive an error message here,
	  be sure that the file was not tampered with or modified in any way.
	
	Now that you have submitted the request to the Certificate Server, the request
	must be approved. This is a very simple process. Follow these steps:
	
	1. Open the Certificate Authority console (located in Administrative Tools).
	
	2. Expand the name of your Certificate Server in the list (the one that
	  processed the request).
	
	3. Expand the Pending Requests section.
	
	4. You should see the certificate that you uploaded from the browser.
	  Right-click on the certificate, click All Tasks, and then click Resubmit. The
	  certificate should disappear from the list and appear in the Issued
	  Certificates section
	
	You have just approved your own server certificate using Certificate Server 2.0.
	There are still two more main issues to address to complete this task. You still
	need to receive the signed certificate from Certificate Server, and then you
	must install this on the Web server.
	
	To receive the signed certificate, perform the following steps:
	
	1. Open Internet Explorer (this must be the same browser you used in the
	  existing procedures) and browse to the certificate server URL
	  ("http://certificate server machine/certsrv)" (without the quotation marks).
	
	2. Choose the Check on a pending certificate option and click Next.
	
	3. On the next screen, you should see a list of any pending request made with
	  this browser. Choose the request you just approved and click Next.
	
	4. The following screen will give you the opportunity to download the
	  certificate. Be sure you do not open this file; you need to download it to
	  the local computer. The Certificate Wizard will need access to this file.
	
	Now that you have the certificate response file from Certificate Server, you can
	install it using the Certificate Wizard in Internet Information Services 5.0.
	Perform the following steps:
	
	1. Open the Internet Services Manager (or custom snap-in as discussed earlier)
	  and browse to the Web site you generated the request for.
	
	2. Right-click on the Web site and click Properties.
	
	3. Click the Directory Security tab, and then under the Secure Communications
	  section, click Server Certificate.
	
	4. You should now see the Web Site Certificate Wizard. Click Next.
	
	5. Choose the Process the pending request and install the certificate option and
	  click Next.
	
	6. Type in (or browse to) the path of the file you just downloaded from the
	  Certificate Server Web page. When you have done this, click Next.
	
	7. You will receive a summary of the certificate you are installing. Read this
	  information to be sure you are installing the correct certificate. Click
	  Next.
	
	8. You will receive confirmation that the certificate was installed.
	
	The Web server is not configured to use secure communications using the
	certificate you just submitted, approved, and installed.
	
	NOTE: Because you used a Certificate Authority (the Certificate Server) that will
	not be trusted by default on a client's browser, the Certificate Authority
	Certificate needs to be installed on the client's browser (they will generally
	receive an error if it is not).
	
	Additional query words: iis
	
	======================================================================
	Keywords          :  
	Technology        : kbiisSearch kbiis500
	Version           : :5.0
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
