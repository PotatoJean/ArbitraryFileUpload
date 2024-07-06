<h1>Arbitrary File Upload</h1>

<h2>Description</h2>

This is a simple project to demonstrate what an arbitrary file upload looks like in a client-side regulated only entry field</br>
</br>
Goal of Project: to simulate an upload of hidden webshell through the change of extension 
<br />


<h2>Languages and Utilities Used</h2>

- <b>Burpsuite</b> 

<h2>Environments Used </h2>

- <b>Windows 10</b> (21H2)
- <b>Vulnerability Testing Environment</b> 
  
 
<h2>Task 1 :  Bypass client side file upload validation</h2>

<p align="center">
Hiding file within another file <br/>
  <p>

-This method is a simulation of hiding a php code within a jpg file. <br/>
-To do that we are using the command “copy car.jpg /b + secret.txt/a 222.jpg”<br/>
 </p> <br/>
 <br/>

 <p align="center">
<img src="https://imgur.com/YES6smu.png" height="80%" width="80%" alt="Change mod of shell script"/>
<br />
<br />

 <p>
-This command basically copies the original car.jpg file and combines it together with the secret.txt file to form 222.jpg file as shown below.<br/>
 </p> <br/>
 <br/>
 <p align="center">
<img src="https://imgur.com/kPwhaNg.png" height="80%" width="80%" alt="Change mod of shell script"/>
<br />
<br />
-Upon viewing the 222.jpg file with a notepad, we can see the code we have prepared in the secret.txt file following behind the car.jpg image.<br/>
 </p> <br/>
 <br/>
 <p align="center">
<img src="https://imgur.com/b0hPxoY.png" height="80%" width="80%" alt="Change mod of shell script"/>
<br />
<br />
<p align="center">
Testing file upload on website <br/>
  <p>
 <p>
-The testing portal does not allow the upload of files other than the common image format on the client side as shown in the snippet below. <br/>
 </p> <br/>
 <br/>
 <p align="center">
<img src="https://imgur.com/F4yv8wa.png" height="80%" width="80%" alt="Change mod of shell script"/>
   <p align="center">
“Pictures uploaded can only be in jpg, jpeg and png format!” <br/>
<br />
<br />



<p align="center">
Intercepting traffic with BurpSuite <br/>
  <p>
 <p>
-In order to make the code we have inserted inside the 222.jpg work, we have to make the file extension php instead of jpg but php is not allowed on the testing portal. So we intercept the post request packet and change the extension there.. <br/>
 </p> <br/>
 <br/>
 <p align="center">
<img src="https://imgur.com/aQef8qc.png" height="80%" width="80%" alt="Change mod of shell script"/>
<br />
<br />

   <p>
-We forward the request and get the results below, indicating a successful upload of the 222.php file.
 <br/>

 </p> <br/>
 <br/>
 <p align="center">
<img src="https://imgur.com/Eg7slMT.png" height="80%" width="80%" alt="Change mod of shell script"/>
    <p align="center">
“File uploaded successfully, file path stored at uploads/222.php” <br/>
<br />
<br />

       
-To test if our upload is received successfully, we can test it out using the path shown below.
 <br/>

 </p> <br/>
 <br/>
 <p align="center">
<img src="https://imgur.com/UxIrugW.png" height="80%" width="80%" alt="Change mod of shell script"/>

<br />
<br />
<br />
     <p>
-This is the results with the output from our code highlighted on the bottom right corner.
 <br/>

 </p> <br/>
 <br/>
 <p align="center">
<img src="https://imgur.com/r9hq7nP.png" height="80%" width="80%" alt="Change mod of shell script"/>

<br />
<br />

<h2>Task 2 : Bypass MIME type file upload validation</h2>


   <p align="center">
Content Type Modification <br/>
  <p>

-We can change the content type to bypass the restriction on the testing portal.  <br/>
-Initially, if we attempt to upload a txt file, it will show the content type as text/plain. <br/>
-To bypass the rules, we can change the content type in the intercepted packet. <br/>
 </p> <br/>
 <br/>

 <p align="center">
<img src="https://imgur.com/Tn2Mlwy.png" height="80%" width="80%" alt="Change mod of shell script"/>
<br />
<br />

 <p>
-Changing the content type allows us to bypass the original rule when we forward the traffic.<br/>
-Upon successful upload, we can test it out by pasting the path in the url (if the file path is given as a vulnerability).<br/>
 </p> <br/>
 <br/>
 <p align="center">
<img src="https://imgur.com/9bq8Ahg.png" height="80%" width="80%" alt="Change mod of shell script"/>
<br />
<br />
-The results is the content of the file can be viewed<br/>
 </p> <br/>
 <br/>
 <p align="center">
<img src="https://imgur.com/9KG08NY.png" height="80%" width="80%" alt="Change mod of shell script"/>
<br />
<br />

 <p align="center">
Conclusion <br/>
  <p>
<p>Of course I did not actually upload a webshell, this is a simulation of what can be done on an environment with this type of vulnerability. I used secret.txt with content of "This is a car!" as an example in this case. Hope you learn something new because I definitely did!</br></p>

<p>That's all for this project, thanks for reading this far. If you are interested in Google Docs version of this write-up, check out the link below </br></p>
[Google Docs] : https://docs.google.com/document/d/1CvibBQCU3cBF7KzkbOGpVCmSFDAi9yCeKhcz0mTFtl8/edit?usp=sharing



<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
