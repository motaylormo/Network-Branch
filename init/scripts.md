## 1. Write a script which displays only the login, UID and Path of each entry of the /etc/passwd file.
```
##		$> man 5 passwd
##		/etc/passwd contains one line for each user account, with seven fields delimited by colons (“:”). These fields are:
##			1) login name
##			2) optional encrypted password
##			3) numerical user ID
##			4) numerical group ID
##			5) user name or comment field
##			6) user home directory
##			7) optional user command interpreter

awk -F':' '{print $1 ":" $3 ":" $6}' /etc/passwd
```

## 2. Write a script which delete an ACTIVE user on the VM.
```
if [ $(whoami) != 'root' ]; then
		echo "you need to be in root to run this"
	else
	if [ ! $1 ]; then
			echo "arg needed"
		else
			/usr/sbin/userdel $1
	fi
fi
```

## 3. Three’s a Charm. Write a script of you choice.
```
if [ ! $1 ]
	then
		echo "type 'otter', 'deer', or 'cat'"
else
if [ $1 == 'otter' ]
	then
		echo "\t  .-\"\"\"-.\n\t /      o\\ \n\t|    o   0).-.\n\t|       .-;(_/     .-.\n\t \\     /  /)).---._|  \`\\   ,\n\t  '.  '  /((       \`'-./ _/|\n\t    \\  .'  )        .-.;\`  /\n\t     '.             |  \`\\-'\n\t       '._        -'    /\n\t          \`\`\"\"--\`------\`"
	else
		if [ $1 == 'deer' ]
			then
				echo "\t               .     _, \n\t               |\`\\__/ / \n\t               \\  . .( \n\t                | __T| \n\t               /   | \n\t  _.---======='    | \n\t //               {} \n\t\`|      ,   ,     {} \n\t \\      /___;    ,' \n\t  ) ,-;\`    \`\\  // \n\t | / (        ;|| \n\t ||\`\\\\        ||| \n\t ||  \\\\       ||| \n\t )\\   )\\      )|| \n\t \`\"   \`\"      \`\"\""
			else
				if [ $1 == 'cat' ]
					then
						echo "\t_                ___       _.--. \n\t\\\`.|\\..----...-'\`   \`-._.-'_.-'\` \n\t/  ' \`         ,       __.--' \n\t)/' _/     \\   \`-_,   / \n\t\`-'\" \`\"\\_  ,_.-;_.-\\_ ', \n\t    _.-'_./   {_.'   ; / \n\t   {_.-\`\`-'         {_/"
					else
						echo "type 'otter', 'deer', or 'cat'"
				fi
		fi
fi
fi
```
