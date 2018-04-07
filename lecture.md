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

Creating a Persistent Disk
======
- Standard persistent disk
- SSD Persistent disk

### What you'll do
- Create a new VM instance and attach a persistent disk
- Format and mount a persistent disk

1. Create new instance
```
gcloud compute instances create gcelab --zone us-central1-c
```
2. Create a new persistent disk
```
gcloud compute disks create mydisk --size=200GB \
--zone us-central1-c
```
3. Attaching a disk
```
gcloud compute instances attach-disk gcelab --disk mydisk --zone us-central1-c
```
4. SSH for checking
```
gcloud compute ssh gcelab --zone us-central1-c
```
- find the disk device by listing the disk devices in /dev/disk/by-id/.
```
ls -l /dev/disk/by-id/
```
default name => scsi-0Google_PersistentDisk_persistent-disk-1
- Specify your own name
```
gcloud compute instances attach-disk gcelab --disk mydisk --device-name <YOUR_DEVICE_NAME> --zone us-central1-c
```
5. Formatting and mounting the persistent disk

Once you find the block device, you can partition the disk, format it, and then mount it using the following Linux utilities:
- mkfs: creates a filesystem
- mount: attaches to a filesystem
5.1 Make a mount point:
```
sudo mkdir /mnt/mydisk
```
5.2 Next, format the disk with a single ext4 filesystem using the mkfs tool. This command deletes all data from the specified disk:
```
sudo mkfs.ext4 -F -E lazy_itable_init=0,lazy_journal_init=0,discard /dev/disk/by-id/scsi-0Google_PersistentDisk_persistent-disk-1
```
5.3 Now use the mount tool to mount the disk to the instance with the discard option enabled:
```
sudo mount -o discard,defaults /dev/disk/by-id/scsi-0Google_PersistentDisk_persistent-disk-1 /mnt/mydisk
```
6. Automatically mount the disk on restart

```
sudo vi /etc/fstab
```

```
UUID=e084c728-36b5-4806-bb9f-1dfb6a34b396 / ext4 defaults 1 1
/dev/disk/by-id/scsi-0Google_PersistentDisk_persistent-disk-1 /mnt/mydisk ext4 defaults 1 1
```

Introduction to Docker
======

### What you'll do
- How to build, run, and debug Docker containers
- How to pull Docker images from Docker Hub and Google Container Registry
- How to push Docker images to Google Container Registry