Google Cloud Study Jams 2018
======

Qwiklabs
======
Google Cloud Self-Paced Labs

https://google.qwiklabs.com/

1 credit = 1 USD
69 USD/month

(GCP Essentials & Kubernetes in the GCloud) in 30 days will get extend 30 days more

Today labs
======
- Creating a Virtual Machine
- Provision Services with Cloud Launcher
- Creating a Persistent Disk

Creating a Virtual Machine
======
- using the Google Cloud Platform Console (GSC)
- also learn how to connect an NGINX

### What you'll do
- Create a virtual machine with the Google Cloud Platform Console
- Create a virtual machine with gcloud command line
- Deploy a web server and connect it to a virtual machine

### Let get start
1. Compute Engine > VM Instances.
- external ip always need to allow http 
2. Create or 
```
gcloud compute instances create gcelab2 --zone asia-southeast1-a
gcloud compute ssh gcelab2 --zone asia-southeast1-a
```
See your current zone
```
curl -H "Metadata-Flavor: Google" metadata/computeMetadata/v1/instance/zone
```
3. Install Nginx
```
sudo su -
apt-get update
apt-get install nginx -y
```
4. Check Nginx
```
ps auwx | grep nginx
```
5. Use gcloud command line
```
gcloud compute instances create gcelab2 --zone us-central1-c
gcloud compute ssh gcelab2 --zone us-central1-c
```

Provision Services with Cloud Launcher
======
GCE (cloud launcher)

### What you'll do
- Launch a common web stack with Cloud Launcher
- Verify your deployment

1. Cloud launcher
2. Nginx Certified by Bitnami
3. Launching the Nginx Stack

