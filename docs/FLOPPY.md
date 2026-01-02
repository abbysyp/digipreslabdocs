# Floppy Disk

_Last updated on January 2, 2026_

## 📁 Prepare Media Directory

_These instructions are adapted for the Windows machine (Yoda) in the Digital Preservation Lab._
   
1. For each physical disk, create an empty folder and name it the corresponding barcode.

6. Within the top-level barcode folder, create two additional folders called **carved_files** and **transfer_metadata**. If you are working with an Apple 3.5" or 5.25" floppy, create an additional folder called **image**.

   <img src="../workflow-images/prepared_directory.jpeg" alt="Example of carved_files and transfer_metadata folders created in File Explorer." width="500">
  
8. Continue to **Getting Carved Files**.

## 💾 Getting Carved Files

_These instructions are adapted for the Windows machine (Yoda) in the Digital Preservation Lab._

### KryoFlux

1. Connect KryoFlux via USB without connecting to external power supply.
2. Open the folder **kryoflux_3.00_windows** on Desktop and find the **dtc** folder.
3. In the terminal, enter:
   
    ```
    cd [path to dtc folder]
    ```
  
4. Next, enter:

   ```
    dtc -c2
    ```

   This should return with the message `CM: maxtrack=0`.

5. Plug KryoFlux into external power supply, or turn powerstrip on.
   
6. Again, enter:

   ```
    dtc -c2
    ```

   Now, it should return with the message `CM: maxtrack=83`.

7. In File Explorer, open the application **kryoflux-ui.jar** located in the **dtc** folder.
8. Navigate to **File → Settings → Output Tab** and change the output file path to the corresponding disk image folder.
9. Insert floppy disk into the reader.
10. On the toolbar, locate the Drive tab and make sure **Drive 0** is selected.
11. Under the Control bar, enter the barcode as the image name, then select the type of disk you want to read. In most cases, it’s **Apple DOS 400K/800K sector image**.
12. Press **Start** and wait for the image to be made.

    There are two grids that will fill up with color indicators, each grid represents a side of the disk (sometimes your disk may be only one-sided, so one grid will be empty), and each square in the grid represents a sector of the disk.

    **🔑 Color Key**
      + Green = track decoded, no errors found
      + Grey = noise (or unknown encoding scheme)
      + Red = track decoded, error(s) found, reading will be retried
      + Yellow = notifications and warnings, e.g. additional header data
      + Glowing = track is being dumped
   
13. Remove the media and disconnect the hardware first from the power strip, then the computer.
14. Your disk image and log file can now be found in your **image** folder.
15. Continue to **Logical Transfer of Files**.

### FC5025

1. Configure external setup for FC5025.
   
3. On the desktop, open **Disk Image and Browse**.
4. Select **Disk Type**, typically **MS-DOS 360k**.
5. Drag the image folder path into **Image Output Directory** box.
6. Enter the barcode in the **Output Image Filename** box.
7. Select **Capture Disk Image File**.
8. Select **Done** and check that the image is there. It may say **Bummer!** instead of **Done**. Click on the prompt and check the image folder anyways...sometimes it still works.
9. If it continues to fail, try using [KryoFlux](https://github.com/abbysyp/digipreslabdocs/edit/main/docs/FLOPPY.md#kryoflux) with the 5.25” drive.
10. Continue to **Logical Transfer of Files**.

### Floppy Reader

1. Connect disk reader via USB to the computer.
   
3. Insert disk into reader.
4. Continue to **Logical Transfer of Files**.

## 🔁 Logical Transfer of Files

1. From the desktop open **AccessData FTK Imager**.
2. Select **File → Add Evidence Item**.
3. Next, choose one of two options:
   
     + _If you already extracted a disk image using KryoFlux or FTK_, select **Image File** then **barcode → image → image file (.E01)** as the Source Path
       
     + _If you are extracting files from a 3.5” floppy via USB reader_, select **Logical Drive > A:\\** then click **Finish**
       
4. Under **Evidence Tree**, click on **+** to expand the directories until you see **[root]** or **[HTE]** and click on it.
5. In the **File List** panel, select everything using **Ctrl+click**.
6. Once all the files are highlighted, **right-click** and select **Export Files**.
7. Select **barcode → carved_files** as the destination folder then click **OK**.
8. **Right-click** the highlighted files again in FTK and select **Export File Hash List**.
9. This time, select **barcode → transfer_metadata** as the destination folder. Enter filename as **checksums** then click **OK**.

    Note: Essentially, we are asking FTK to generate a csv of MD5 and SHA1 checksums for each of the carved files as early as possible. We will use this later to double-check that the files haven’t changed

10. Double check that both the carved files and checksums.csv are there:
   
     + _If it was a clean transfer_, you may now delete the image and image folder
       
     + _Otherwise_, please talk to your supervisor so that a decision can be made about whether or not to retain the disk image

15. Continue to [Packaging and Transfer Workflow](https://github.com/abbysyp/digipreslabdocs/blob/main/docs/PACKAGING.md#packaging-and-transferring-files-to-archivematica).
   


   
