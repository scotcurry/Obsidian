This seems to be the pattern:

- Remote repositories have names:
	- us-central1-docker.pkg.dev for the GCP registry
	- docker.io for Docker Hub

At this point I manually create the registry using the web UI tools for the two locations.  Once they are built, it becomes important to get the exact path of the registry in its respective location.

When building the image build it with the destination repository in mind:
- <Path to Remote Registry(docker.io)>/<path within remote registry(scotcurry4/datadogcurryware)>:tag

You can then use **docker push** to transfer the file to the remote registry.