# ftb-endeavour - v1.7.0
Feed The Beast Endeavour modpack
made by Feed The Beast at https://feed-the-beast.com

Modpack for Minecraft 1.16 with Log4j CVE-2021-44228 vulnerability mitigation.
All-purpose modpack expanding on our hugely successful FTB Revelations.</br>
Endeavour includes mods that revolve around tech, magic, exploration and general building.

<img src="https://apps.modpacks.ch/modpacks/art/78/1024_1024.png" width="256" height="256">

NOTE: In compliance with Mojang "End User License Agreement", you will need to agree to the EULA in order to run your own Minecraft server. By using this container you acknowledge the EULA! If you do not agree, then you are not permitted to use this container!
https://account.mojang.com/documents/minecraft_eula

The worldname must be the default "world". 
Settings will reset when upgrading.
Access the console to op and whitelist.

Running ftb-endeavour data container:
<code>docker run --name [name of your data container] jonasbonno/ftb-endeavour:1.7.0-logj4 echo 'Data-only container'</code>

Running ftb-endeavour server:
<code>docker run --tty=true --interactive=true --detach=true --name [name of your container] --volumes-from [name of your data container] --publish=[port on your host]:25565 jonasbonno/ftb-endeavour:1.7.0-log4j</code>

When upgrading sometime items have been remove and therefor you have to confirm removal.</br>
To do so run <code>docker attach [name of your container]</code> and type <code>/fml confirm</code> when prompted to confirm or cancel.</br>
Exit with CTRL+P CTRL+Q. </br>

To access the console:
</br><code>docker attach [name of container]</code>
</br>Run your commands
</br>To exit: CTRL+P CTRL+Q

Tips:
</br>Check for OS updates: <code>docker exec -u 0 -it [name of your container] /usr/bin/apt update</code>
</br>Install OS updates: <code>docker exec -u 0 -it [name of your container] /usr/bin/apt full-upgrade -y</code>
</br>Download file: <code>docker cp [name of your container]:/minecraft/options.txt .</code>
</br>Upload file: <code>docker cp options.txt [name of your container]:/minecraft/options.txt</code>
</br>Say Hi!: <code>echo "say Hi!" | socat EXEC:"docker attach [name of your container]",pty STDIN</code>
</br>Say CPU and RAM usage: <code>echo "say $(docker stats [name of your container] --no-stream --format "table CPU: {{.CPUPerc}} RAM: {{.MemPerc}}" | sed -n -e 2p)" | socat EXEC:"docker attach [name of your container]",pty STDIN</code>

The first time the server starts it creates the server.properties file with default settings and spawns "world". 
Not recommended to change these settings by hand.
