# dns-filter

`dns-filter` is your custom forwarding DNS server that redirects input traffic matching given regular expression to another host.


#### Usage:

    python3 dns_filter.py --verbose --port 10053 --cname xyz.net --ns1 ns1.example.com. --ns2 ns2.example.com. --regexp "^abcd.+?.com$"


#### Options:

    -h, --help            show this help message and exit
    -v, --verbose         log incoming requests to the console
    -p PORT, --port=PORT  DNS server port number
    -t CNAME, --cname=CNAME        destination CNAME
    --ns1=NAMESERVER1        destination NAMESERVER1
    --ns2=NAMESERVER2       destination NAMESERVER2
    -r REGEXP, --regexp=REGEXP
                          regular expression to be checked
    -i INTERFACE, --interface=INTERFACE
                          interface IP to listen on


#### Example:

Install `Twisted` library first:

    $ python3 -m pip install twisted


Run `dns-filter` server locally:

    $ python3 dns_filter.py --verbose --port 10053 --cname xyz.net --ns1 ns1.example.com. --ns2 ns2.example.com. --regexp "^abcd.+?.com$"


Open another console window and run test request via system `dig` tool:

    $ dig -p 10053 @localhost abcd-example.com CNAME +short
    xyz.net


Based on: https://twistedmatrix.com/documents/16.5.0/names/howto/custom-server.html
