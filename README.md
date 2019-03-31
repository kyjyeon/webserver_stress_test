# webserver_stress_test on aws-EC2 vm
<h2>Description</h2><br>
<h3>Objective</h3><br>
Create virtual user request(numbers / concurrent) input to a web application address and check the overall status of the web server
<h3>Preparation</h3><br>
Wordpress Instance  Heavy web application for defense <br>
Ubuntu Instance with  <b>apache2 utils</b>  installed For Attacker <br>

<h3>Methods</h3><br>
In your 'Attacker' Ubuntu, write 
`
sudo apt-get update
`  to update all versions first using terminal<br>
Write command  `sudo apt-get install apache-utils` <br>
After downloading, write `ab` and you can checkout the description of usage<br>
In your 'Defender' wordpress, write `top` at command to see status
Write command `ab -n <"number of request you want"> -c <"number of concurrent you want"> http://<your ip or dns address/>` <br>
Will see CPU usage rate, new resource usage by ex- php, apache, mysql<br>


<h2>Personal Result</h2><br>

| Request       | Concurreny    | Time_taken  | Failed | 
| ------------- |:-------------:| -----------:|-------:|
| 400           | 1             | 8.082       |   none |
| 400           | 2             | 8.086       |   none |
| 600           | 3             | 11.933      |   none |
| 800           | 10            | 15.549      |   none |
| 800           | 20            | 15.527      |   none |
| 1000          | 10            | 19.212      |   none |
| 1000          | 50            | 19.471      |   none |
| 1000          | 200           | 19.086      |   none |
| 1000          | 1000          | 19.259      |   none |
| 3000          | 1000          | -           |   9    |
<br>
<b>-The higher concurrency the longer 'Time per request'</b><br>
<b>-The last test 3000 request started to slow down from 2400 request.</b><br>
