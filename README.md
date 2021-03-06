# CSC323-Powershell

#Ch.3

Get-Help -Name Get-Service -ShowWindow 

Get-Help Get-EventLog -Full

Get-Help Get-EventLog -Example

Get-Help -Full

Get-Help *process*

Get-Help *printer*

Get-Help *help*

Get-Help Get-*

Get-EventLog

Get-EventLog Application

Get-EventLog Application -Newest 10

Get-Help about_*

Get-Help about_Aliases

Get-Help Stop-Service -ShowWindow

Show-Command -Name Get-EventLog


#Ch.4 

Get-PSSnapin -Registered


Get-Module -ListAvailable

Get-Module -Name ServerManager | Measure-Object

Get-Module -Name ActiveDirectory | Measure-Object

Get-Module -ListAvailable | Import-Module ; Get-Command -CommandType Cmdlet | Measure-Object

Get-Module -ListAvailable | Import-Module ; Get-Command -CommandType Cmdlet | Measure-Object -ShowWindow

Get-Get-Module -ListAvailable | Import-Module ; Get-Command -CommandType Cmdlet | Measure-Object

Get-Verb | Sort-Object Verb

 Get-Command service

 gcm *service*

 get-service

get-service *registry*

Get-Help Get-Command

Get-Command -Noun AD*

gcm -Noun SP*

Get-Command -Verb Get* -Noun PS*

Get-Help *service*

Get-Command -Name Get-Process

Get-Help -Name Get-Process

Get-Command *process*

cd alias: dir | Where-Object {$_.Definition -eq "Get-Process"}

Get-Process

Get-Process | Select-Object ProcessName, VM -First 30 | Sort-Object VM -Descending

Get-Process | Select-Object ProcessName, VM -First 20 | Sort-Object VM 

notepad

Get-Process -Name *notepad*

Get-Process -Name *notepad* | Get-Member | more

ping -a -n 2 executrain.com

netstat /?

netstat -a

netstat -e

netstat -e -s

netstat -f

netstat -n

netstat -o

netstat -p proto

netstat -p proto -s

netstat -q

netstat -r

netstat -s

netstat -t

netstat -x

netstat -y

netstat interval

ipconfig

ipconfig /displaydns

net use * \\server\share

net use *

$env:path

Invoke-Item

Invoke-Item -Path "C:\pdfs\mypdfdocument.pdf"

iexplore

& "C:\Program Files\Internet Explorer\iexplore.exe"

& "C:\Program Files\Internet Explorer\iexplore.exe" www.bing.com

& "C:\Program Files\Internet Explorer\iexplore.exe" www.google.com

$ie = & "C:\Program Files\Internet Explorer\iexplore.exe"
$extoff = "-extoff"
$url = "www.google.com"
& $ie $extoff $url

icacls .\docs /grant Chad(CI)(OI)M

icacls .\docs --% /grant Chad(CI)(OI)M

Get-Help about_parsing -ShowWindow

icacls X:\VMS /grant Dom\HVAdmin:`(CI`)`(OI`)F

icacls X:\VMS --% /grant Dom\HVAdmin:(CI)(OI)F

X:\VMS /grant Dom\HVAdmin:(CI)(OI)F


#Ch.5 (Linux Commands)

ps

grep

awk


#Ch.6 

Dir | more

Get-Process | Sort-Object -Property CPU -Descending

Get-Process

Get-Process | Get-Member

Get-Help Get-Process -Online

Get-Service -Name *spool*

Get-EventLog -LogName Application

Get-EventLog Application

Get-ChildItem C:\Windows -Recurse

Get-Help about_*


#Ch.7

Out-Default

Get-Process | Out-Default

Get-Process | Out-Host

Get-Process

Get-Process | Sort-Object -Property Name

Get-Process | Sort-Object -Descending 

Get-Process | Get-Member -MemberType Properties 


#Code Snippets

foreach ($item in $collection)
{
    
}


do
{
    
}
until ($x -gt 0)


#More Powershell Commands

Get-PSProvider

cd alias:

Get-PSDrive

$path = "HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion\Run\"

New-PSDrive -Name HKCuRun -PSProvider Registry -Root $path


#Class on March 20, 2017

 $Room = "Hawkins053C"

  $Machine = "01"

  $Target = "$Room-Machine"
  $Target


  Get-Service

  $Service = Get-Service

$Service | Select *

$User = "bvill003"
$UserFolder = "C:\Users\$user\Documents"

$Files = Get-ChildItem -Path $UserFolder -Recurse -File


#Arrays: April 3, 2017

$arr = 4,6,8,10,12

$arr

$Services = Get-Service

$Services


$Computers = "hawk053B-TS", "Hawk053B-01","Hawk053B-00"
$On = @()
$Off = @()


foreach($Computer in $Computers){
    if(Test-Connection -ComputerName $Computer -Count 1 -Quiet)
        $On = $On + $Computer
    }else{
        $Off = $Off + $Computer
}

$Off



$Computers = Get-ADComputer -Filter 'Name -like"053D*"' | select -ExpandProperty Name
$On = @()
$Off = @()


foreach($Computer in $Computers){
    if(Test-Connection -ComputerName $Computer -Count 1 -Quiet){
        $On = $On + $Computer
    }else{
        $Off = $Off + $Computer
    }
}

$Off


#Class on April 10,2017

Get-Printer -ComputerName print-acad | Select -First 2

Get-Printer -ComputerName print-acad

Get-Printer -ComputerName print-acad | Select -Last 10

Get-Printer -ComputerName print-acad | select -First 1 *

Get-Printer -ComputerName print-acad | select *


$Printers = Get-Printer -ComputerName print-acad
$Printers.Count


#Hash Tables
$Computer = @{Name="DC01";OS="Server 2012 R2"}
$Computer


$Computer = [ordered]@{Name="DC01";OS="Server 2012 R2"}
$Computer

$Computer.OS


$Computer.item("OS")


$Computer.Name = "DC02"



$Computer.add("StartupRam","2048MB")


$Computer.Remove("StartupRam")
$Computer


$Computer = @{}
$Computer.Add("Name",$env:computername)
$Computer.add("Networking",(Get-NetIPAddress -InterfaceAlias "Ethernet0"))

$Computer
$Computer.Name
$Computer.Networking
$Computer.Networking.IPAddress






#ISE Objects

dir "C:\User Desktops"

$users = dir "C:\User Desktops"

$users | select * -First 1

$users = dir "C:\User Desktops" | select name

$users | select * -First 1 | Get-Member

$users = dir "C:\User Desktops" | select -ExpandProperty name

foreach($User in $users){
$FilePath = "C:\User Desktops\$User\Desktop\RDP.link"
if(Test-Path -Path $FilePath){"File is there"}else{"file is not there"}
"The current user being Processed is $User."
}


#Modules

$env:PSModulePath

$env:PSModulePath.Split(",")

Get-Module -ListAvailable

Get-Module

(Get-Module -ListAvailable).count

Get-Command -Module SQLPS

Get-Command Get-SmbShare


#Arrays & Hashtables

$newhires = newhires.csv
Import-Csv -Path .\newhires.csv | 
Select-Object -Property * , `
@{name='samAccountName';expression={$_.netname}}, `
@{name='GivenName';expression={$_.firstname}}, `
@{name='Name';expression={$_.lastname}}, `
# @{name='EmailAddress';expression={$_.emailaddress}} |




#April 24, 2017
#Serialization / Deserialization

Get-Service | Export-Clixml -Path MyServices.xml
$XML = Import-Clixml -Path .\MyServices.xml
$XML

$XML | select -First 2 *



notepad .\MyServices.xml



































































