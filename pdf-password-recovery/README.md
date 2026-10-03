# PDF Password Recovery with John the Ripper

## Overview
In this Networkwalks training lab, I recovered the password of a supplied encrypted PDF using John the Ripper on Kali Linux. I verified the recovered password by opening the document and viewing the lab flag.

## Tools Used
- Kali Linux running in VMware
- pdf2john
- John the Ripper
- Firefox PDF viewer

## Scope
This exercise used the password-protected PDF supplied for the training lab.

## Procedure

### 1. Confirm the PDF download
I checked that the practice file was available in my Downloads folder.

    ls -l ~/Downloads/*.pdf

### 2. Extract the PDF hash
I extracted the password verification data into a text file that John could process.

    pdf2john "$HOME/Downloads/My Locked PDF1.pdf" > "$HOME/Downloads/hash1.txt"

I checked the extracted output:

    cat "$HOME/Downloads/hash1.txt"

![Extracted PDF hash](images/01-hash-extraction.png)

### 3. Run John the Ripper
I started the password recovery process:

    john "$HOME/Downloads/hash1.txt"

John loaded the PDF hash and recovered the password during its default wordlist phase.

![John password recovery result](images/02-password-recovery.png)

### 4. Verify the result
I entered the recovered password into the PDF viewer. The document opened successfully and displayed the training flag.

![Opened PDF showing the lab flag](images/03-unlocked-pdf.png)

## Results
- Successfully extracted the PDF hash.
- Recovered the password using John's default wordlist.
- Confirmed the result by opening the encrypted PDF.
- Viewed the flag inside the document.

## What I Learned
- How to prepare an encrypted PDF for password recovery with pdf2john.
- How to run John the Ripper and interpret its output.
- Why successful password recovery should be verified against the original file.
- How a guessable password can weaken the protection offered by encryption.

## Status
Completed using the John the Ripper command-line tool on Kali Linux. The Johnny GUI portion of the assignment has not yet been completed.
