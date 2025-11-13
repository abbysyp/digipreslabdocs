# Cloud (Google Drive or Dropbox)

_Last updated on November 13, 2025_

## 📁 Prepare Media Directory

_These instructions are adapted for the Windows machine (Yoda) in the Digital Preservation Lab._
   
1. For each transfer, create an empty folder and name it the corresponding barcode. Note that for cloud files, we assign a barcode but toss the sticker afterwards to prevent reuse.

6. Within the top-level barcode folder, create two additional folders called **carved_files** and **transfer_metadata**.
   
   ![Example of carved_files and transfer_metadata folders created in File Explorer.](https://github.com/user-attachments/assets/52b9f6f8-6405-4f2d-935d-b1e58a4ccff2)
  
8. Continue to **Rclone File Transfer**.

## 🔁 Rclone File Transfer

_Rclone is a command-line tool for managing files on cloud storage services like Google Drive and Dropbox. First, you may need to configure your Google or Dropbox drive to access the shared files you would like to download, instructions for each are linked below._

+ _[Google Drive](https://rclone.org/drive/)_
+ _[Dropbox Drive](https://rclone.org/dropbox/)_

_These instructions are adapted for the Windows machine (Yoda) in the Digital Preservation Lab._

1. First, navigate to the folder you would like to download in Google Drive or Dropbox and **copy** the name to your clipboard.

   ![Example of Google Drive folder pulled up with the folder name displayed at the top of the page.](../workflow-images/google_drive_folder.png)

3. In a terminal, locate the **rclone** folder on the Desktop of Yoda and `cd` into it.
4. Once you are in **rclone**, enter:

    ```
    rclone md5sum [drive name]:"[folder name]" > [transfer metadata folder path]\checksums.txt
    ```
    **💡 Command Breakdown**
    + `rclone md5sum` generates an md5 checksum for each file while it is still located on the drive
    + `[drive name]:"[folder name]"` is the name of the folder containing the files
    + `> [transfer metadata folder path]\checksums.txt` writes the output to a file called checksums.txt in our metadata folder

    Here's a more specific example:
    
    ```
    cd C:\Users\lstuch1\Desktop\rclone
    ```
    ```
    rclone md5sum abbysyp:"Wang Mei wu dao zuo pin xuan ji" > C:\Users\lstuch1\Desktop\39015092248429\transfer_metadata\checksums.txt
    ```
   Once the command has run, check that the file is there and that its contents look valid.
6. Enter the command:

    ```
    rclone copy [drive name]:"[folder name]" [carved files folder path]
    ```
    **💡 Command Breakdown**
    + `rclone copy` copies files from one location to another
    + `[drive name]:"[folder name]"` is the name of the folder containing the files we want to copy
    + `[carved files folder path]`is where want the copied files to go

   Here's a more specific example:
    
   ```
    rclone copy abbysyp:"Wang Mei wu dao zuo pin xuan ji" C:\Users\lstuch1\Desktop\39015092248429\carved_files
    ```
   Once the command has run, check that the files have been downloaded into your **carved_files** folder.

7. Continue to [Packaging and Transfer Workflow](https://github.com/abbysyp/digipreslabdocs/blob/main/docs/PACKAGING.md#packaging-and-transferring-files-to-archivematica).

   
