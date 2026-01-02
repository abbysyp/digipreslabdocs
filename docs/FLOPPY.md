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

_For 3.5” Apple and 5.25” floppies, we must extract an image from the disk using specialized equipment in the lab. For standard 3.5” floppies, we’re able to grab the carved files right off of the disk using FTK. This workflow covers all methods, so first identify the type of floppy disk you’re working with then follow the instructions accordingly._

### 🍎 3.5" Apple Floppy

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

   
