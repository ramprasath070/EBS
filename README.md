### WORKING WITH EBS
### NAME: RAM PRASATH S
### REG NO: 212224040266
### Aim:
To create and configure an Amazon Elastic Block Store (EBS) volume, attach and mount it to an Amazon EC2 instance, create a snapshot backup, and restore the snapshot to a new EBS volume.

### Algorithm / Steps:
Create a new Amazon EBS volume with a size of 1 GiB.
Select the same Availability Zone as the EC2 instance.
Attach the EBS volume to the EC2 instance using /dev/sdb.
Connect to the EC2 instance using AWS Systems Manager Session Manager.
Check the available storage using df -h.
Create an ext3 file system on the EBS volume.
Create the /mnt/data-store directory.
Mount the EBS volume to /mnt/data-store.
Configure /etc/fstab for automatic mounting.
Verify that the EBS volume is successfully mounted.
Create file.txt inside the mounted EBS volume.
Verify the contents of the created file.
Create an EBS snapshot named My Snapshot.
Delete file.txt from the original EBS volume.
Create a new EBS volume from the snapshot.
Attach the restored volume to the EC2 instance using /dev/sdc.
Create the /mnt/data-store2 directory.
Mount the restored volume to /mnt/data-store2.
Verify that file.txt has been successfully restored.

### Program:
1. Check Available Storage
```
df -h
```
2. Create an ext3 File System
```
sudo mkfs -t ext3 /dev/sdb
```
3. Create a Mount Directory
```
sudo mkdir /mnt/data-store
```
4. Mount the EBS Volume
```
sudo mount /dev/sdb /mnt/data-store
```
5. Configure Automatic Mounting
```
echo "/dev/sdb   /mnt/data-store ext3 defaults,noatime 1 2" | sudo tee -a /etc/fstab
```
6. View the File System Configuration
```
cat /etc/fstab
```
7. Verify the Mounted Volume
```
df -h
```
8. Create a File in the EBS Volume
```
sudo sh -c "echo some text has been written > /mnt/data-store/file.txt"
```
9. Read the File
```
cat /mnt/data-store/file.txt
```
10. Delete the File
```
sudo rm /mnt/data-store/file.txt
```
11. Verify File Deletion
```
ls /mnt/data-store/
```
12. Create a Mount Directory for the Restored Volume
```
sudo mkdir /mnt/data-store2
```
13. Mount the Restored EBS Volume
```
sudo mount /dev/sdc /mnt/data-store2
```
14. Verify Snapshot Restoration
```
ls /mnt/data-store2/
```
Expected output:

```
file.txt
```
Outputs
### Outputs:

<img width="1917" height="1150" alt="Screenshot 2026-11-20 101510" src="https://github.com/user-attachments/assets/8da8597d-8118-4f53-a3bb-ba87fc449758" />
<img width="1912" height="1147" alt="Screenshot 2026-11-20 101639" src="https://github.com/user-attachments/assets/7dd29020-516d-40bd-b894-be0f38d36c14" />
<img width="960" height="1105" alt="Screenshot 2026-11-20 102221" src="https://github.com/user-attachments/assets/61a92bd3-05f5-4392-b20e-6adca526dd1a" />
<img width="1915" height="1150" alt="Screenshot 2026-11-20 102613" src="https://github.com/user-attachments/assets/cdf47be8-9774-42db-9a8e-17c8f36ea173" />
<img width="1917" height="1097" alt="Screenshot 2026-11-20 102619" src="https://github.com/user-attachments/assets/ab67c77d-bf97-4dbc-9167-825f7d4eafb0" />
<img width="951" height="1095" alt="Screenshot 2026-11-20 102837" src="https://github.com/user-attachments/assets/5344ada7-f618-419a-b44e-2fe777e139b6" />
<img width="950" height="572" alt="Screenshot 2026-11-20 102956" src="https://github.com/user-attachments/assets/84bb46f7-8f35-4999-99a7-ffb8fe9f416c" />
<img width="946" height="1092" alt="Screenshot 2026-11-20 103111" src="https://github.com/user-attachments/assets/cdbecfd0-9276-4c67-bc3e-196f7c51896b" />

### Result:
Thus, an Amazon EBS volume was successfully created and attached to an Amazon EC2 instance. The volume was formatted with an ext3 file system, mounted, and used for storing data. An EBS snapshot was successfully created as a backup, and a new EBS volume was restored from the snapshot. The previously deleted file.txt was successfully recovered, demonstrating the backup and restore functionality of Amazon EBS.
