# Fawn — Notes

## Lessons Learned

- FTP commonly uses TCP/21.
- Nmap is useful for identifying exposed services.
- Anonymous FTP should be checked during FTP enumeration.
- `ls` and `dir` reveal accessible files.
- `get` downloads a file from an FTP server.

## Workflow

1. Spawn the HTB machine.
2. Obtain the target IP.
3. Enumerate with Nmap.
4. Identify FTP on port 21.
5. Test anonymous login.
6. Enumerate the directory.
7. Download `flag.txt`.
8. Verify the file locally.
9. Submit the flag on HTB.
10. Document the attack chain.
