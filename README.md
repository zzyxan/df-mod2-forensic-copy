# df-mod2-forensic-copy

<#  Uploaded to the JMevidence folder are five pieces of "evidence" a couple of PDFs, a PNG, a Word Document and a Text file. 
 I have written powershell commands to copy the contents of the JMevidence folder to the JMevidence Copy folder. 
 ''' PowerShell
 copy-item -Path "c:\Users\zzyxa\OneDrive\Documents\df-mod2-forensic-copy\JMevidence\*" -Destination  "c:\Users\zzyxa\OneDrive\Documents\df-mod2-forensic-copy\JMevidence Copy" -Recurse
 '''
 This folder is the working forensic copy and should be treated as the working directory.
 After this, I wrote a line of code to calculate the hash of the Daikin Mini Split PDF and write it out to a .txt file in the JMevidenceRESULTS Folder as documented in the screenshots. 
 ''' PowerShell
 copy-item -Path "c:\Users\zzyxa\OneDrive\Documents\df-mod2-forensic-copy\JMevidence\*" -Destination  "c:\Users\zzyxa\OneDrive\Documents\df-mod2-forensic-copy\JMevidence Copy" -Recurse
 '''
 I very quickly decided that it would be too much work to write that same line of code, changing the path for each file.
 Based on my code to copy the contents of the JMevidence Folder, I wrote another line to calculate the hash strings for each of the five files and write them to one single .txt file.
 ''' PowerShell
 get-filehash -path "C:\Users\zzyxa\OneDrive\Documents\df-mod2-forensic-copy\JMevidence\*" -algorithm SHA256 | Out-File -path "C:\Users\zzyxa\OneDrive\Documents\df-mod2-forensic-copy\JMevidenceRESULTS\HASH.txt"
 '''
 This process was then repeated for my working forensic copies in the JMevidence Copy folder, and then the two files compared to one another. Unforetunately I wasn't able to figure out how to get Powershell to compare the strings for me, but I was able to write an if statement to compare the two strings and output the phrase "Files Changed" if they didn't match. A quick google search showed that other people have run into the same problem, and were able to write a function to do it for them, but it's way above my working knowledge.
 '''PowerShell
 if("D837E6A6D93452819578AA90258C7107B7FD46FD408277C83E8963F7744EE0F4" -ne "D837E6A6D93452819578AA90258C7107B7FD46FD408277C83E8963F7744EE0F4") {writeforensic-copy\JMevidence Copy" -Recu-output "Files Changed"}
 '''
#>