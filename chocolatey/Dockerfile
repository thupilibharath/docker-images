#
# Dockerfile for chocolatey
#

FROM microsoft/windowsservercore:latest
MAINTAINER frozenbytes

# Setup one or more individual labels
LABEL com.i-m-code.chocolatey.version="0.0.5-alpha" \
	  com.i-m-code.chocolatey.release-date="1-26-2017" \
	  com.i-m-code.chocolatey.license="MIT" \
	  com.i-m-code.chocolatey.repo="chocolatey" \
	  com.i-m-code.chocolatey.baserepo="frozenbytes" 

# Startup Policy MUST BE SET in COMPOSE file

#Setup Environment Variable
RUN mkdir C:\data \
	&& mkdir C:\data\chocolatey 

RUN powershell echo $env:ChocolateyInstall \
	&& powershell [Environment]::SetEnvironmentVariable('ChocolateyInstall', 'C:\data\chocolatey', [System.EnvironmentVariableTarget]::Machine) \
	&& powershell echo $env:ChocolateyInstall

# Setup Package Management with Chocolatey
RUN powershell iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1')) \
	&& powershell -Command Install-PackageProvider -Name chocolatey -Force

# BoxStarter, SublimeText3, Git, ConEmu Console
RUN powershell CINST Boxstarter -y \
	&& powershell CINST Sublimetext3 -y \
	&& powershell CINST git.install -y \
	&& powershell CINST conemu -y 