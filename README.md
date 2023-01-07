# CSCCTFv4

## Whispering Forensics Challenge 
Reading the Challenge Name and Description we identify it is a network analysis challenge, that is related to PacketWhispring; Stealthily Transfer Data & Defeat Attribution Using DNS Queries & Text-Based Steganography, without the need for attacker-controlled Name Servers or domains, opening the given `.pcap` file and filtering it into dns queries:

<img width="958" alt="2023-01-08 00_55_18-Main - VMware Workstation" src="https://user-images.githubusercontent.com/84410099/211171759-7c2921c4-5799-4e12-9fdd-eab045b0ff3e.png">

We notice whispering starts somewhere around here, digging more in the file we find the following cloudflare dns packets:

<img width="961" alt="image" src="https://user-images.githubusercontent.com/84410099/211171790-dce3e534-6b43-4d19-a4b3-6bb45bef5b92.png">

This means the subdomains are being randomly generated. 

To solve this challenge a tool called [PacketWhisper](https://github.com/TryCatchHCF/PacketWhisper) is needed (Thanks to TryCatchHCF).

Step-by-Step Solution: 

Running the given python script:

<img width="959" alt="image" src="https://user-images.githubusercontent.com/84410099/211172110-bf77fa17-b1fa-49b0-9e04-2a8b369ca1dd.png">

The menu shows the options from through 5, we will be using option 2 since all we have is a `.PCAP` file.

<img width="957" alt="image" src="https://user-images.githubusercontent.com/84410099/211171953-0ebbfa3f-00f6-41bf-8a21-ab84d96d7b9d.png">

Choosing option 2, then typing in the file name and choosing the OS type will get us to the next section in which we have to choose the PacketWhisper Cipher --> As mentioned above, it is a Random CloudFront subdomain. 

<img width="958" alt="image" src="https://user-images.githubusercontent.com/84410099/211172057-d4bfc888-3da9-495a-8690-dfe85c1f06d7.png">

Last but not least, we need to save the extracted data to a file ( I chose to call this file flag.txt)

Reading the content of `flag.txt`: 

<img width="958" alt="image" src="https://user-images.githubusercontent.com/84410099/211172096-ef80d2a9-48c6-469a-81ad-3ba19f0a90a1.png">
