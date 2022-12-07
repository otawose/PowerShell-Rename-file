# PowerShell-Rename-file
ent## Set the file location where the log files are
$file = "C:\logs"   

$new = "newfilename.csv"
$chkFile = "C:\logs\newfilename.csv"
$fileExists = Test-Path $chkFile

## Loop through all the .csv files in the log folder
foreach ($file in gci $file -include *.csv -recurse){       
    if($fileExists -eq $True){
        Write-Host "that file exists!"
        Start-Sleep -s 60
    } else{
    Write-Host "file doesn't exist, renaming..."
    rename-item -path $file -newname ("$new")}
    Start-Sleep -s 10   
}
