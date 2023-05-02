Download Link: https://assignmentchef.com/product/solved-cop4600-ex-6-io-device-files
<br>



<h1>Overview</h1>

This exercise should begin to help you understand the Linux File System and how to interact with it. Linux originally used Minix’s file system, but it has gone through four iterations of extended file systems over the course of the kernel’s development, your kernel’s file system is using the ext4 file system (fourth extended file system).

In Unix-based systems (like Linux) and many other operating systems, devices in the system are represented using <strong><em>device files</em></strong> – that is, virtual files present in the virtual filesystem presented by the OS that do not present data records on a storage medium (as traditional files do). Instead, device files act as handles to read from and write to connected devices. These devices are often physical ones – such as solid-state drives, mice, or keyboards – but they can also be virtual devices, which simulate hardware via a software mechanism.







In this exercise, you will create and attach a virtual storage drive via a <strong><em>loopback device</em></strong>, which allows a regular file to masquerade as a device… which will then to represented using a virtual file. (<em>Unix be cray like that.</em>) Loopback devices are commonly used on Unix systems, especially for creating, reading, and writing storage images (such disc images, i.e. “ISOs”). You’ll connect the storage, mount it, write to it, unmount it, and then verify that the data has been written.




<h1>Structure</h1>

The exercise is broken into these main parts:




<ul>

 <li>Create a storage device image file.</li>

 <li>Connect the file to a loopback device, format it, and mount a filesystem on the device.</li>

 <li>Write data to the virtual device by creating files on it after mounting</li>

 <li>Unmount the virtual device and disconnect the loopback device 5) Verify the data has been written to the image file</li>

</ul>

<strong> </strong>

<h2>Creating the Image</h2>

Follow these steps to completed the exercise:




<ol>

 <li>Create a <strong>img</strong> file, filled with zeroes, of size one megabyte (<strong>1MiB</strong>) using <strong>dd</strong>:</li>

</ol>

<strong> </strong>

<strong>$</strong><strong> dd if=&lt;input file&gt; of=&lt;output file&gt; bs=&lt;block size&gt; count=&lt;how many&gt;  </strong>




The <strong>dd</strong> command’s input can come from any source, a regular file or a special (device) file. A special file, <strong>/dev/zero</strong>, will have an <u>infinite number of zeroes</u> available for reading. The output data’s size is defined by the <u>block-size</u> and <u>block-count</u> – you could create a 1KiB file by using a size of 512 and a count of 2, for example.




<ol start="2">

 <li>Create a loopback device connected to the image file via <strong>losetup</strong>, format the image in <strong>ext4 format</strong> using <strong>mkfs</strong>, and then mount the loopback device on <strong>/mnt/ex6</strong> via <strong>mount</strong>. <em>Take a screenshot of the commands you used in this step.</em>

  <ol>

   <li>You will need to use <strong>sudo</strong> for the <strong>losetup</strong></li>

  </ol></li>

</ol>




<ol start="3">

 <li>In this step you will be writing data to the virtual device by creating files on it after mounting.</li>

</ol>

In the mounted directory (<strong>/mnt/ex6</strong>), create <strong>two</strong> text files:

<ol>

 <li>one empty,</li>

 <li>and one containing a message.</li>

</ol>

Display the contents of each file using the <strong>cat</strong> command and <em>take a screenshot</em>.




<ol start="4">

 <li>Unmount the filesystem (<strong>umount</strong>) and disconnect the loopback device (<strong>losetup</strong>).</li>

</ol>




<ol start="5">

 <li>Lastly, you need to verify if the data has been written to the image file.</li>

</ol>

Install the <strong>hexedit</strong> program (<strong>sudo apt-get install hexedit</strong>) and use it to examine the image file – you should be able to find your <strong>filenames</strong> and <strong>text</strong>. <em>Take a screenshot</em>.




Just for fun: try the <strong>strings</strong> command and see what happens!