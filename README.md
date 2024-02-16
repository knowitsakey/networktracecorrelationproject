Project 2: 
This project sets up a tor-in-a-box lab towards developing netflow correlation capabilities to trace malicious traffic in tor. The project automatically sets up series of virtualbox virtual machines on Ubuntu linux.
For more details, reach out.

A more detailed description of the project follows:


The aim of this project is to understand how traffic correlation trace collection works from a practical perspective. Companies like ciphertrace provide this functionality https://ciphertrace.com/ to try and track cryptocurrency on behalf of governments. Various cryptocurrency corporations are beginning to try and mitigate the trace collection "problem" faced by cryptocurrency users, by releasing tools to allow people to make anonymous payments. However, until tools like this are widespread, traffic correlation trace anaylsis remains viable.

A background on traffic correlation trace collection:

Some sets of defenses against malicious cyber activity rely on netflow correlation patterns. Netflow is a log format for IP traffic, including incoming and outgoing ip addresses, timestamps and packet sizes. A national cybersecurity apparatus operating with the ability to interecept traffic, such as that maintained by the National Security Agency sets up a series of high bandwidth routers at the points where internet traffic exits and enters the country and uses correlations in netflow to try and identify malicious patterns. This process could hopefully be effective in blocking foreign-originating cyberattacks, and it could benefit strongly from automation.
For example, if a person in a foreign country is using a VPN in order to make it appear that their internet traffic is originating from the united states in order to do a cyberattack, the timestamps in the netflow logs for the incoming and outgoing traffic might help identify the original ip address source of this traffic.

The process of tracing malicious user traces becomes harder when addressing traffic routed through Tor. Tor works by making traffic appear uniform, padding the lengths of transmissions, and adding random time delays. With that said, traffic can still be identified and correlated. Especially with a large amount of data and computing power, it is potentially feasible to find some needles in the haystack. For example, if an adversary is able to listen at the point when traffic enters tor, such as that coming from a vpn endpoint and the traffic leaving the tor exit nodes, it possible to get a trace based on a method like an end-to-end confirmation attack. https://security.stackexchange.com/questions/147402/how-do-traffic-correlation-attacks-against-tor-users-work#:~:text=This%20is%20called%20an%20end,in%20order%20to%20deanonymize%20users.


In order to develop an understanding of traffic correlation trace collection, we are going to attempt to create a program to evade trace collection. Our software program will mitigate an adversary able to perform an end to end confirmation attack on the tor network. Then we will design a method to gather traces again.

The project must have the following components:

1. Enable high enough bandwidth for functional web browsing
2. Avoid making requests to servers from tor exit nodes.
3. Take as input a list of a series of tor hidden services configured to run as socks5 proxies

The project was accomplished by doing the following:

1. Modify the darkssh project to create several socks5 proxies to hidden services encrypted via ssh. https://github.com/knowitsakey/darkssh
2. Leverage the chutney framework to create an ansible role to spin up a tor network in a box https://github.com/knowitsakey/naanbread

Key learning points were:

1. Building an understanding of how TCP works on a socket level.
2. Defining an accurate mental model of how netflow correlation traces might be gathered.
3. Developing a thorough understanding of the topology of the tor anonymity network.


Note, based on publishing date, a reader notes that this code was written prior to the release of GPT. Python scripts and ansible roles still had to be written and debugged by hand during this time period.

