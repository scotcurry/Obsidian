	Pull the Datadog agent container
	sudo docker pull datadog/agent

Command to execute datadog agent
docker run -d --cgroupns host --pid host --name dd-agent -v /var/run/docker.sock:/var/run/docker.sock:ro -v /proc/:/host/proc/:ro -v /sys/fs/cgroup/:/host/sys/fs/cgroup:ro -e DD_API_KEY=<DATADOG_API_KEY> gcr.io/datadoghq/agent:7

	-d = detached -means don't leave the process log on the screen, just print the container ID and go to the background.
	--cgroupns = Cgroup namespace -It seems that this is need to make sure the container doesn't run in a private namespace.  Need to understand this better.
	--pid = PID namespace to use -Need to figure out why you wouldn't use the PID of the host.
	-v = Volume - I think of volumes that get created to hold the data from containers.  In this way you can delete the container, but anything that the container wrote to the volumes will be preserved for the next version of the container.  

Once this runs, the ddagent will show up in the console.  Need to figure out where to set the name as this there are probably going to be a number of agents.