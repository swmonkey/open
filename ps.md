# Using cd (alias)
cd C:\Users\YourName\Documents

# Using Set-Location
Set-Location C:\Users\YourName\Documents

# Go up one level
cd ..

# Go to home directory
cd ~

# Running Scripts
The .\ tells PowerShell to look in the current directory. You can also use a full path:
powershellC:\path\to\eg.ps1
If you get an "execution policy" error, run this first to allow scripts:
powershellSet-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
