1. The --command line interpreter-- in linux is called --shell--, and the language that we use to interact with shell is called
		--bash--

///////////////////////////////////////////// Windows ////////////////////////////////////////////

[Very important]
2. In windows each drive is a filesystem.

3. Using --power shell--:-
			-. ls <address>
			-. Get-Help ls 					
			-. Get-Help ls -Full
			-. ls -Force     						shows the hidden files and permissions
			-. pwd 											print working directory
			-. cd <relative or absolute path>
			-. cd ~				go to home directory C:\Users\Alireza
			-. mkdir <directory name>-
			-. scaping char in powershell is `
			-. history 		// to see the history of your commands
			-. ctrl + r 	// to search for commands
			-. cp <file name > <new address>
			-. wildcard in powershell is *
			-. cp <foldername> <new address> -Recurse -Verbose		// -Verbose is for showing the copy process
			-. mv <filename> <new address or new name>
			-. rm <filename> 	// rm <filename> -Force (to delete system files) 	// rm <foldername> -Recurse-
			-. cat <filename> 		to show the file content
			-. cat <filename> -Head 10		shows 10 first line
			-. cat <filename> -Tail 10	shows 10 last line
			-. more <filename>		to show the file content page by page, enter add one line, space add one page, q for quit
			-. Get-Alias <command name>		powershell uses aliases to resemble the linux commands
			-. Windows GUI search services uses indexing to index files and folders based on their properties and names, you can 
				config indexing options (search in the windows search) to search based on the content of the file.
			-. Select-String <reg expression> <filename>
			-. Select-String cow *.txt
			-. ls 'C:\Program files' -Recurse -Filter *.exe  				-Filter looks for the file name inside directories
			-. echo woof > dog.txt			// in power shell echo is an alias for --Write-Output--
				// every --windows process-- and every --PowerShell command-- can take input and produce output
				// Each process in windows has --three differnet streams--.
					a. --stdin--: we provide input to the process by adding data to stdin
					b. --stdout––: The proccess adds data to the stdout
					c. ––stderr--

			-. --redirect-- stdout of the process to a file instead of the screan:

							echo > dog.txt			// create or overwrite in dog.txt file
							echo >> dog.txt			// append to the file
			-. When you get an error from a command, the error pass to another output stream --stderr--. you can also redirect 
					standard error:

							rm <system file> 2> error.txt

			-. --pipe-- send the output of one command to the input of another commmand:
						cat words.txt | Select-String st
			-. Get-LocalUser			//list all users
			-. Get-LocalGroup			// list all the groups
			-. Get-LocalGroupMember Administrators			// list the members of a group

			// net is the CMD commands
			-. net user <username> <password>			// to change the password of the user.	if you use * instead of password you can enter
																								password seprately
			-. net user <username> /logonpasswordchg:yes			// force user to change his password
			-. net user <username> * /add											// to create new user
			-. net user <username> /del												// to delete a user
			-. Remove-LocalUser	<username>										// to delete a user

4. There are two types of users, --standard users-- and --Administrators users--

5. You can search for --computer management-- for users and groups management in --windows--

6. In windows --files and directory-- permissions are assigned using --ACLs (Access Control Lists)--. Specially we're going to 
		working with DACLs (Discretionary Access Control Lists)

7. ACLs is a list of --Access Control Entries (ACEs)--

8. Windows --files or folders-- can also have --System Access Control Lists (SACLs)--, SACLs are used to tell windows that it should 
		use an event log to make a note of every time someone accesses a file or folder.
	
9. Each file or folder will have --an owner-- and --one or more-- DACLs.

////////////////////////////////////////// Linux //////////////////////////////////////

4. using linux:
				
				-. ls <address>
				-. ls help
				-. man ls 								to see the manual page for ls command
				-. pwd
				-. cd <relative or absolute path>
				-. cd ~ 			go to home directory
				-. mkdir <directory name>
				-. the scape char in bash is \
				-. history		// to see the history
				-. cp <filename> <new address>
				-. cp <foldername> <new address> -r
				-. wildcard is * in bash
				-. mv <filename> <new filename or new address>
				-. rm <filename>  or rm -r <foldername>
				-. cat <filename>
				-. less <filename>		use up and down keys, pagedown and pageup, g moves to the begining of the file, G to the end
															/<word search> for searching, q for quit				
				-. head <filename> 		shows the first 10 lines of the file
				-. tail <filename> 		shows the last 10 lines of the file
				-. grep <regular expression> <filename>
				-. grep cow *.txt

				// every --linux process-- and every --bash command-- can take input and produce output
				// Each process in windows has --three differnet streams--.
					a. --stdin--: we provide input to the process by adding data to stdin
					b. --stdout––: The proccess adds data to the stdout
					c. ––stderr--

			-. --redirect-- stdout of the process to a file instead of the screan:

							echo > dog.txt			// create or overwrite in dog.txt file
							echo >> dog.txt			// append to the file
			-. When you get an error from a command, the error pass to another output stream --stderr--. you can also redirect 
					standard error:

							rm <system file> 2> error.txt
							
			-. --pipe-- send the output of one command to the input of another commmand:
						cat words.txt | grep st
				
			-. passwd <username>			// to change the password of the user

			-. sudo passwd -e <username>		// expires the user password.

			-. sudo useradd <username>		// to add new user

			-. sudo userdel <username>		// to remove the user


. In linux there are --standard users--, --administrators users--, and there is a special user called --root users--.

[ATTENTION]
There is only one super user or root account in linux.

. you can run sudo (superuser do) command for restricted files for example:

		sudo cat /etc/sudoers


		If you don't want to run sudo all the time you can change user to root user:

			sudo su -<username>			// for substitue user if you don't specify the username it will be the root 
	
[Very important]
. If you want to see who has access to the sudo command or the membership of groups, you can see it in /etc/group file

			cat /etc/group

			There are 4 fields that is seprated by colon:

					operator:x:5:root				
					<group name>: <password> (x or * means it is encrypted and saved in a seprated file): <group id> : <group members>

. If you want to see the --users-- in linux (most of them are not human users, they are users that uses processes in linux)

				cat /etc/passwd
			
. User passwords are stored in a file /etc/shadow