# k8s-sabnzb

The goal for this is to help me learn Kubernetes in a practical way while also building out some fundamentals of my homelab.  Sabznbd will function as the core of the Usenet stack.

# Goal
To setup a deployment of sabnzb, accessible via http://<cluster>/sabnzb as easily as possible.

# How it works
I'm using the NFS-CSI provider to setup the StorageClass for my kstorage1 node, which has a single SSD connected to it.  This is temporary until I complete my NAS setup.

There are 5 PersistentVolumes setup
/config - holds all the config and *.ini's for sabnzb
/downloads - for complete downloads
/incomplete - for in progress downloads
/scripts - for any post scripting
/watched - watch folder for incoming nzbs

The Deployment pulls the image from linuxserver, and a Service is setup to establish and endpoint for sabnzb.

Finally we have a traefik ingress serving as a reverse proxy, allowing this service to be accessible via http://<node>/sabnzbd/
