# Lecture 0: HTTP #

## When you go to your browser and enter www.google.com, what happens? ##

1. We translate the domain of the site, i.e. google.com, into an *IP address*, which identifies a server or computer on the internet.
	* IP addresses come in a pattern that looks like w.x.y.z. Each of these placeholders can be a whole number from 0 to 255. An example could be 121.0.39.255.
		* This means that each placeholder is an 8-bit number and an IP address as a whole uses 32 bits. This gives us up to 2<sup>32</sup> or roughly 4 billion possible IP addresses.
		* IPv4 utilizes these 32-bit representations of servers or computers. IPv6 will use 128 bits and a transition to this version will eventually happen.
	* In order to find the IP address of a domain, your computer has to do a domain-name lookup using a *DNS (Domain Name System)* server.
		* You personally would probably not have a DNS server to do this for you, but your ISP (Internet Service Provider) or employer (if your on a large work network) for instance, would have a DNS server.
		* If the DNS server you utilize doesn't have a record of the domain you're looking for, then it will ask other DNS servers if they know about the domain and those DNS servers will ask other DNS servers if they don't know. If the DNS servers throughout this hierarchy can't find record of the domain you're looking for, they will look for a root server. These root servers are spread out geographically among the continents and these root servers would know who does know what the IP address you need. They essentially know which DNS server is the authority on certain domains.
	* So your computer has an IP address. Now your computer can send a message to this IP address that will look something like this: ```GET / HTTP/1.0```
		* The first part of this is an HTTP method, which is ```GET``` in this instance. The second part if what resource you're attempting to access. Using just a slash ```/``` means you're accessing the root resource (imaging something like index.html). This could easily be changed to something like ```/about``` and a different resource would get requested. The last part is declaring the HTTP protocol and version, which in this case is ```1.0```.
		* This message is serving as a request for a resource.

```javascript
const triple = function (x) {
	return x * 3;
}

const waffle = triple;

waffle(30); // 90
```

## Quiz Yourself ##

1. Functions are not values. True or false.
> False. Functions are values in the way that numbers or strings are values.

Source: https://www.youtube.com/watch?v=8KuO4r5CHjM
