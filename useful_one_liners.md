-  Add comma to end of every line
   ```sh
	gsed '0~1 s/$/,/g' < transcript.txt > transcript.csv
   ```
-  Merge every two lines
   ```sh
	gsed 'N;s/\n/ /' transcript.csv > workshop_transcript.csv
   ```
-  Compress a file
   ```sh
	tar czf <compressed-file-name>.tar.gz <to-compress-dir>
   ```
   
-  scp to ec2 instance
     ```sh
     	scp -i ~/<path_to_id_rsa_key> chunks.tar.gz ubuntu@ec2-xx-xxx-xxx-xxx.us-west-2.compute.amazonaws.com:~/.
     ```
-  Checking directory sizes
   ```sh
    du -sh directory_name
    ```
-  View memory usage
   ```sh
	- cat /proc/meminfo 
  	- watch -n 1 “cat /proc/meminfo”
	- ps aux | grep [p]y
   ```
-  Abstractify the jupyter notebook logs
  ```sh
    jupyter notebook &> /dev/null &
  ```

-  Display all lines starting from nth line:
  ```sh
	tail -n +<k> file 
  ```

-  Write a list strlist to csv file
  ```sh
	file = open(‘out.csv’, ‘w’)
	file.write(‘\n’.join(strlist))
   ```
  
-  To restore all those deleted files in a folder enter the following command.
  ```sh
	git ls-files -d | xargs git checkout --
  ```
  
-  Remove duplicate lines from file
  ```sh
	awk '!seen[$0]++'
  ```
  
-  Discard unstated changes from git
  ```sh
    - git stash save --keep-index --include-untracked
    - git stash drop
  ```
  
-  One liner to stop / remove all of docker containers:
  ```sh
    - docker stop $(docker ps -a -q)
    - docker rm $(docker ps -a -q)
  ```
  
-  Docker list all images : All the Docker images on a system can be listed by adding -a to the docker images command. Once you're sure you want to delete them all, you can add the -q flag to pass the Image ID to docker rmi
   ```sh
	— docker images -a	
	— docker images -f dangling=true	
	— docker rmi $(docker images -f dangling=true -q)
   ```
   
-  In the process of running docker I had accumulated several images that are not tagged. To remove these I use this command:
  ```sh
	— docker rmi $(docker images -a | grep "^<none>" | awk '{print $3}')
  ```
  
-  Docker ground zero
  ```sh
	— rm -rf /var/lib/docker
  ```
