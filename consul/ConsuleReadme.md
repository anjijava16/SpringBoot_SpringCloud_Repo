http://localhost:8500/ui/dc1/services

http://localhost:9098/getStudentDetailsForSchool/abcschool

# Consul
Step 1: Download : https://www.consul.io/downloads.html

Step 2: Check the IPConfig get th IPV4 address :
     IPv4 Address. . . . . . . . . . . : 192.168.0.3

Step 3: Go to the consul install path :
      consul agent -server -bootstrap-expect=1 -data-dir=consul-data -ui -bind=192.168.0.3
	  
Step 4: Check consul details in the UI :
      http://localhost:8500/ui/dc1/nodes/DESKTOP-25T44JJ

Step 5: Check the service status using consul web UI 	  
