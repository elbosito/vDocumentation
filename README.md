# vDocumentation
vDocumentation provides a community-created set of PowerCLI scripts that produce documentation of vSphere environments in Excel file format.

Hi! I'm Ariel Sanchez (https://twitter.com/arielsanchezmor) and this is my brainchild. I started a documentation template effort, which can be found here https://sites.google.com/site/arielsanchezmora/home/vmware/free-vmware-documentation-templates . There is a lot of work to do in it, but one very important component that my friend Edgar Sanchez (https://github.com/edmsanchez , https://twitter.com/edmsanchez13 ) has completed is the PowerCLI scripting. This repository stores them, and publishes them to the world so they can start being used and improved by the community!

The main motivation for this project was the sad state of reliable documentation available to many vSphere administrators. It is demoralizing to start a new job, ask for documentation, and find there is none, or what there is turns out to be outdated, or even worse, wrong! And it's also demoralizing to be tasked with creating documentation, realizing that creating it manually would take a long time, and that figuring out all the scripts will take probably longer.

Thus, easy to create documentation "direct from vCenter" that is relevant to what your manager or another VMware administrator wants to see is our goal. The best part is, you only need to run the scripts and they create the needed Excel file for you. This means you can update your documentation at a moment's notice, and even better, use it to identify things in your environment that may not have been easily visible before.

The license on these scripts is a BSD style license - use as you will. Like all the PowerCLI greats have told us before, steal and modify whatever you find useful. We definitely have stolen from all over the internet to create these (and have tried to credit those who we stole from). Special shout-outs to Luc Dekens, William Lam, Alan Renouf, Kyle Ruddy - and many more in the vCommunity.

Our goal is that this project is useful to others and it will be accepted in the official VMware PowerCLI examples. Please, let us know if you found this useful, had trouble running it, or anything that you want to see changed. We are new to GitHub but actively learning - use GitHub or reach out to us on twitter or on the VMware Code Slack (https://code.vmware.com/web/code/join)

To a future where walking into a new place and asking for documentation is greeted with "Yup, we use vDocument" and the interested party replies "Perfect!" :)

# Licensing

Copyright (c) <2017> Ariel Sanchez and Edgar Sanchez

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

# Installation

The scripts run inside a PowerShell window using PowerCLI modules. Powershell is available in all modern windows OS, with PowerShell core available for Mac and Linux. Make sure you have the latest PowerCLI installed (you can check here for a video on how to install https://blogs.vmware.com/PowerCLI/2017/05/powercli-6-5-1-install-walkthrough.html)

From the video, these are the useful commands you should have completed before installing vDocumentation:

_$psversiontable_ [enter]  =  gives you the PowerShell version
_get-module VMware* -ListAvailable_ [enter]  =  Lists all installed PowerCLI modules, if return empty, install PowerCLI

## Installing PowerCLI
  __Find-Module -Name VMware.PowerCLI__  =  checks connectivity to PowerShell Gallery and updates NuGet if needed (yes is default)
  __Install-Module -Name VMware.PowerCLI -Scope CurrentUser__  =  install PowerCLI as long as you answer Y or A

## Execution Policy

 Make sure that your execution policy allows you to run scripts downloaded from the internet. You do this with a command run in a powershell window that has been launched with "Run as Administrator"
 
 __Set-ExecutionPolicy RemoteSigned__

and click Y or A


## Adding the vDocumentation module

vDocumentation are powershell modules as well, but are not yet in the PowerShell Gallery, so we can't use the Install-Module command.  For now, use this manual process:

  1 Download the two files inside the vDocumentation folder.
  2 Browse to the %USERPROFILE%\Documents\WindowsPowerShell\Modules and copy the files inside a folder named vDocumentation
  3 Close all PowerShell windows
  4 Launch PowerShell, you should be able to use the vDocumentation functions now


## One method to copy the needed files from Github to your PC using PowerShell:

Execute these lines in a PowerShell window that is in your home directory (tested with PS 5)

__mkdir Documents\WindowsPowerShell\Modules\vDocument
(new-object Net.WebClient).DownloadString("https://raw.githubusercontent.com/arielsanchezmora/vDocumentation/master/powershell/vDocument/vDocument.psd1") > Documents\WindowsPowerShell\Modules\vDocument\vDocument.psd1
(new-object Net.WebClient).DownloadString("https://raw.githubusercontent.com/arielsanchezmora/vDocumentation/master/powershell/vDocument/vDocument.psm1") > Documents\WindowsPowerShell\Modules\vDocument\vDocument.psm1
exit__
