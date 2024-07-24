# File System Forensics with Autopsy and Sleuth Kit

## Introduction

File system forensics involves the detailed examination of file systems to uncover evidence of malicious activity, recover deleted files, and analyze the structure and integrity of the system. Autopsy and Sleuth Kit are powerful tools used in digital forensics for these purposes. This advanced-level lab will guide you through complex forensic tasks using these tools, including advanced file recovery, timeline analysis, and detecting data obfuscation.

## Pre-requisites

- Advanced knowledge of Linux file systems (ext4, XFS, etc.)
- Familiarity with forensic principles and techniques
- Experience with command-line tools
- Basic understanding of scripting (optional)

## Lab Set-up and Tools

- A computer running a Linux distribution (e.g., Ubuntu)
- Autopsy and Sleuth Kit installed
- A disk image with pre-configured forensic challenges (can be created using tools like `dd` or downloaded from a reputable source)
- Sufficient disk space for analysis

### Installing Autopsy and Sleuth Kit

1. Update your package list:
    ```bash
    sudo apt update
    ```
2. Install Autopsy:
    ```bash
    sudo apt install autopsy
    ```
3. Install Sleuth Kit:
    ```bash
    sudo apt install sleuthkit
    ```

## Exercises

### Exercise 1: Advanced Disk Image Acquisition

**Objective**: Acquire a disk image with specific partitions for detailed forensic analysis.

1. Create a disk image of a storage device with multiple partitions:
    ```bash
    sudo dd if=/dev/sda of=/path/to/image.img bs=4M
    ```
2. Verify the integrity of the disk image using `md5sum`:
    ```bash
    md5sum /dev/sda
    md5sum /path/to/image.img
    ```
3. Mount the disk image to examine its partitions:
    ```bash
    sudo mount -o loop,ro /path/to/image.img /mnt/forensics
    ```

**Expected Output**: A verified disk image with accessible partitions for analysis.

### Exercise 2: In-depth File System Analysis

**Objective**: Use Sleuth Kit to conduct a detailed analysis of the file system structure and identify hidden data.

1. List the partitions within the disk image:
    ```bash
    mmls /path/to/image.img
    ```
2. Use `fsstat` to analyze the file system structure of a selected partition:
    ```bash
    fsstat -f ext4 /path/to/image.img
    ```
3. Search for hidden or obfuscated data using `icat` and `fls`:
    ```bash
    fls -r /path/to/image.img
    icat /path/to/image.img <inode_number> > hidden_data
    ```

**Expected Output**: Identification of hidden or obfuscated data within the file system.

### Exercise 3: Timeline Analysis

**Objective**: Create and analyze a timeline of file system activities using Sleuth Kit tools.

1. Generate a timeline of file system events using `mactime`:
    ```bash
    fls -m / /path/to/image.img > bodyfile.txt
    mactime -b bodyfile.txt -d > timeline.txt
    ```
2. Analyze the timeline to identify suspicious activities or anomalies.
3. Use Autopsy to create a visual representation of the timeline for easier analysis.

**Expected Output**: A detailed timeline of file system activities highlighting suspicious events.

### Exercise 4: Recovering Deleted Files

**Objective**: Use Sleuth Kit and Autopsy to recover and analyze deleted files from the disk image.

1. Identify deleted files using `fls`:
    ```bash
    fls -rd /path/to/image.img
    ```
2. Recover a specific deleted file using `icat`:
    ```bash
    icat /path/to/image.img <inode_number> > recovered_file
    ```
3. Use Autopsy to further analyze the recovered files for evidence of tampering or malicious content.

**Expected Output**: Recovered deleted files and detailed analysis of their content.

### Exercise 5: Detecting Data Obfuscation and Manipulation

**Objective**: Identify and analyze techniques used to obfuscate or manipulate data within the file system.

1. Search for unusual patterns or anomalies in file metadata using `istat`:
    ```bash
    istat /path/to/image.img <inode_number>
    ```
2. Use `strings` to search for hidden text within files:
    ```bash
    strings /path/to/image.img | grep -i "suspicious_text"
    ```
3. Analyze the results to detect obfuscation techniques such as steganography or encryption.

**Expected Output**: Identification of data obfuscation techniques and detailed analysis of manipulated data.

## Conclusion

By completing these exercises, you have gained advanced skills in file system forensics using Autopsy and Sleuth Kit. You have learned to acquire and verify disk images, conduct detailed file system analysis, create timelines of system activities, recover deleted files, and detect data obfuscation. These skills are essential for performing comprehensive forensic investigations and uncovering hidden evidence in complex cases.


## About Me

I am a cybersecurity trainer with a passion for teaching and helping others learn essential cybersecurity skills through practical, hands-on projects. Connect with me on social media for more updates and resources:

[![LinkedIn](https://img.icons8.com/fluent/48/000000/linkedin.png)](https://www.linkedin.com/in/rajneeshcyber)
[![YouTube](https://img.icons8.com/fluent/48/000000/youtube-play.png)](https://www.youtube.com/@rajneeshcyber)
[![Twitter](https://img.icons8.com/fluent/48/000000/twitter.png)](https://twitter.com/rajneeshcyber)

Feel free to reach out with any questions or feedback. Happy learning!
