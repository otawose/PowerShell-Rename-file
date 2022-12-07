

while($true) {
    $csvFiles = gci $file -include *.csv -recurse

    if ($csvFiles.Length -eq 0) {
         break
    }

    foreach ($file in gci $file -include *.csv -recurse) {       
        if (Test-Path $chkFile) {
            Write-Host "that file exists!"
            Start-Sleep -s 60
        } else {
            Write-Host "file doesn't exist, renaming..."
            rename-item -path $file -newname ("$new")
            Start-Sleep -s 10
        }
    }
}
