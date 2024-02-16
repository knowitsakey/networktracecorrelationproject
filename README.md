
This project sets up a tor-in-a-box lab towards developing traffic correlation trace capabilities on the tor network. The project automatically sets up a mini version of the tor network in a series of virtualbox virtual machines on Ubuntu linux.
For more details, reach out.

A more detailed description of the project follows:

Project 2:

The aim of this project is to understand how traffic correlation trace collection works from a practical, hands on perspective.

A background on traffic correlation trace collection:

Some sets of defenses against malicious cyber activity rely on trace analysis by traffic correlation. Companies like ciphertrace set up middleboxes in the internet backbone in order to try and trace obfuscated cryptocurrency payments. Government agencies also collect their own traces in the same ways. On an unobfuscated network like TCP/IP, trace correlation can be aided by log formats such as netflow, which collects timestamps, ip addresses, and packet sizes. On an obfuscated network, like tor, traces may still be collected, especially when an adversary maintains the capability to listen at the entry and exit nodes.
https://arxiv.org/pdf/2009.13018.pdf

In order to develop an understanding of end to end traffic correlation trace collection, we are going to attempt to create a program to use tor to connect to the clearweb while evading trace collection. First we will create a self-contained version of the tor network, and enable trace collection on our entry and exit nodes in the box. Then we will design a program Our software program will mitigate an adversary who has a position listening at entry and exit nodes. Then we will design a method to gather traces on the obfuscated traffic.

The project must have the following components:

1. Enable high enough bandwidth for functional web browsing
2. Avoid making requests to servers from tor exit nodes.
3. Take as input a list of a series of tor hidden services configured to run as socks5 proxies

The project was accomplished by doing the following:

1. Modify the darkssh project to create several socks5 proxies to hidden services encrypted via ssh. https://github.com/knowitsakey/darkssh
2. Leverage the chutney framework to create an ansible role to spin up a tor network in a box for testing https://github.com/knowitsakey/naanbread
3. Create a rotating tor proxy that proxies client request through a hidden service in our network in a box https://github.com/knowitsakey/rotoxy

Key learning points were:

1. Building an understanding of how TCP works on a socket level.
2. Defining an accurate mental model of how netflow correlation traces might be gathered.
3. Solidify understanding of the client-server networking paradigm.
4. Developing a thorough understanding of the topology of the tor anonymity network.

Note, based on publishing date, a reader notes that this code was written prior to the release of GPT. Python scripts and ansible roles still had to be written and debugged by hand during this time period.

