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















