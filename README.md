<h1>DAST using NMAP and in GitLab</h1>


<h2>Description</h2>
This lab focuses on utilizing NMAP, a powerful network scanning tool, for Dynamic Application Security Testing (DAST) within the GitLab platform. NMAP allows you to perform comprehensive scans of web applications, identify open ports, discover network services, and detect potential vulnerabilities.

During this hands-on lab, participants will gain practical experience in integrating NMAP into the GitLab pipeline to enhance the security of their web applications. 
<br />


<h2>Languages and Utilities Used</h2>

- <b>NMAP</b>
- <b>JSON</b>
- <b>GitLab</b>

<h2>Environments Used </h2>

- <b>Windows 11</b>
- <b>Linux</b> 

<h2>Program walk-through:</h2>

Let’s install nmap to perform Dynamic Analysis: <br/>
```
apt-get update && apt-get install nmap -y
```
<br/>
 
<p align="center">
<img src="https://i.imgur.com/aeQ46Um.png" height="80%" width="80%" alt="Disk Sanitization Step"/>
</p>

<br />
<br />

We have successfully installed Nmap scanner, let’s explore the functionality it provides us: <br/>
```
nmap -help
```
<br/>
 
<p align="center">
<img src="https://i.imgur.com/xeS2uLh.png" height="80%" width="80%" alt="Disk Sanitization Step"/>
</p>

<br />
<br />

Let’s run nmap with the following options: <br/>
```
nmap prod-rcgsg0ei -oX nmap_out.xml
```
<br/>
 
<p align="center">
<img src="https://i.imgur.com/BZUBFiD.png" height="80%" width="80%" alt="Disk Sanitization Step"/>
</p>

<br />
<br />

We can check the scan output using the following command: <br/>
```
cat nmap_out.xml
```
<br/>
 
<p align="center">
<img src="https://i.imgur.com/p6BfzSQ.png" height="80%" width="80%" alt="Disk Sanitization Step"/>
</p>

<br />
<br />

Let’s run the scan in GitLab in the YAML configuration file: <br/>
```
- docker pull hysnsec/nmap
```
```
- docker run --rm -v $(pwd):/tmp hysnsec/nmap hysnsec/nmap <YOUR HOST> -oX /tmp/nmap-output.xml
```
<p align="center">
<img src="https://i.imgur.com/19213TG.png" height="80%" width="80%" alt="Disk Sanitization Step"/>
</p>

Here is the result of this job: <br/>
<p align="center">
<img src="https://i.imgur.com/KrKLZ9I.png" height="80%" width="80%" alt="Disk Sanitization Step"/>
</p>

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
