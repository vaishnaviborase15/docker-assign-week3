# Task: Create a Custom Docker Bridge Network

```
docker run -dit --name container1 --network caps_custom_bridge alpine sh


docker run -dit --name container2 --network caps_custom_bridge alpine sh


Microsoft Windows [Version 10.0.22000.2538]
(c) Microsoft Corporation. All rights reserved.

C:\Users\admin>docker network ls
NETWORK ID     NAME            DRIVER    SCOPE
83ba01984c5f   bridge          bridge    local
77147a213607   host            host      local
1d6b9e1adba8   mongo-network   bridge    local
ed5d5c6345f0   none            null      local

C:\Users\admin>docker network create --driver bridge caps_custom_bridge
9fe91e348619ad0807acfed7835d53cac5089000de3f3e4d22ccd5de3d27609a

C:\Users\admin>docker network inspect caps_custom_bridge
[
    {
        "Name": "caps_custom_bridge",
        "Id": "9fe91e348619ad0807acfed7835d53cac5089000de3f3e4d22ccd5de3d27609a",
        "Created": "2025-06-26T11:02:41.884942273Z",
        "Scope": "local",
        "Driver": "bridge",
        "EnableIPv6": false,
        "IPAM": {
            "Driver": "default",
            "Options": {},
            "Config": [
                {
                    "Subnet": "172.19.0.0/16",
                    "Gateway": "172.19.0.1"
                }
            ]
        },
        "Internal": false,
        "Attachable": false,
        "Ingress": false,
        "ConfigFrom": {
            "Network": ""
        },
        "ConfigOnly": false,
        "Containers": {},
        "Options": {},
        "Labels": {}
    }
]

C:\Users\admin>docker run -dit --name container1 --network caps_custom_bridge alpine sh
Unable to find image 'alpine:latest' locally
latest: Pulling from library/alpine
fe07684b16b8: Pull complete
Digest: sha256:8a1f59ffb675680d47db6337b49d22281a139e9d709335b492be023728e11715
Status: Downloaded newer image for alpine:latest
8a1269d387489c83324c6c5aea83ae99615d20e5adaaa58771c30aa5e28920ca

C:\Users\admin>docker run -dit --name container2 --network caps_custom_bridge alpine sh
a9168186806fcb82d4b8786095036aeef47218b42583feacd0d735c4b7a60d09

C:\Users\admin>docker exec -it container1 sh
/ # ping container2
PING container2 (172.19.0.3): 56 data bytes
64 bytes from 172.19.0.3: seq=0 ttl=64 time=2.458 ms
64 bytes from 172.19.0.3: seq=1 ttl=64 time=0.097 ms
64 bytes from 172.19.0.3: seq=2 ttl=64 time=0.155 ms
64 bytes from 172.19.0.3: seq=3 ttl=64 time=0.109 ms
64 bytes from 172.19.0.3: seq=4 ttl=64 time=0.076 ms
64 bytes from 172.19.0.3: seq=5 ttl=64 time=0.123 ms
64 bytes from 172.19.0.3: seq=6 ttl=64 time=0.088 ms
64 bytes from 172.19.0.3: seq=7 ttl=64 time=0.129 ms
64 bytes from 172.19.0.3: seq=8 ttl=64 time=0.092 ms
64 bytes from 172.19.0.3: seq=9 ttl=64 time=0.204 ms
64 bytes from 172.19.0.3: seq=10 ttl=64 time=0.253 ms
64 bytes from 172.19.0.3: seq=11 ttl=64 time=0.066 ms
64 bytes from 172.19.0.3: seq=12 ttl=64 time=0.131 ms
64 bytes from 172.19.0.3: seq=13 ttl=64 time=0.117 ms
64 bytes from 172.19.0.3: seq=14 ttl=64 time=0.118 ms
64 bytes from 172.19.0.3: seq=15 ttl=64 time=0.108 ms
64 bytes from 172.19.0.3: seq=16 ttl=64 time=0.066 ms
64 bytes from 172.19.0.3: seq=17 ttl=64 time=0.091 ms
64 bytes from 172.19.0.3: seq=18 ttl=64 time=0.160 ms
64 bytes from 172.19.0.3: seq=19 ttl=64 time=0.164 ms
64 bytes from 172.19.0.3: seq=20 ttl=64 time=0.161 ms
64 bytes from 172.19.0.3: seq=21 ttl=64 time=0.071 ms
64 bytes from 172.19.0.3: seq=22 ttl=64 time=0.068 ms
64 bytes from 172.19.0.3: seq=23 ttl=64 time=0.089 ms
64 bytes from 172.19.0.3: seq=24 ttl=64 time=0.171 ms
64 bytes from 172.19.0.3: seq=25 ttl=64 time=0.172 ms
64 bytes from 172.19.0.3: seq=26 ttl=64 time=0.261 ms
64 bytes from 172.19.0.3: seq=27 ttl=64 time=0.168 ms
64 bytes from 172.19.0.3: seq=28 ttl=64 time=0.174 ms
64 bytes from 172.19.0.3: seq=29 ttl=64 time=0.241 ms
64 bytes from 172.19.0.3: seq=30 ttl=64 time=0.169 ms
64 bytes from 172.19.0.3: seq=31 ttl=64 time=0.153 ms
64 bytes from 172.19.0.3: seq=32 ttl=64 time=0.170 ms
64 bytes from 172.19.0.3: seq=33 ttl=64 time=0.168 ms
64 bytes from 172.19.0.3: seq=34 ttl=64 time=0.110 ms
64 bytes from 172.19.0.3: seq=35 ttl=64 time=0.121 ms
64 bytes from 172.19.0.3: seq=36 ttl=64 time=0.177 ms
64 bytes from 172.19.0.3: seq=37 ttl=64 time=0.189 ms
64 bytes from 172.19.0.3: seq=38 ttl=64 time=0.070 ms
64 bytes from 172.19.0.3: seq=39 ttl=64 time=0.120 ms
64 bytes from 172.19.0.3: seq=40 ttl=64 time=0.203 ms
64 bytes from 172.19.0.3: seq=41 ttl=64 time=0.157 ms
64 bytes from 172.19.0.3: seq=42 ttl=64 time=0.224 ms
64 bytes from 172.19.0.3: seq=43 ttl=64 time=0.209 ms
64 bytes from 172.19.0.3: seq=44 ttl=64 time=0.163 ms
64 bytes from 172.19.0.3: seq=45 ttl=64 time=0.167 ms
64 bytes from 172.19.0.3: seq=46 ttl=64 time=0.116 ms
64 bytes from 172.19.0.3: seq=47 ttl=64 time=0.306 ms
64 bytes from 172.19.0.3: seq=48 ttl=64 time=0.192 ms
64 bytes from 172.19.0.3: seq=49 ttl=64 time=0.166 ms
64 bytes from 172.19.0.3: seq=50 ttl=64 time=0.164 ms
64 bytes from 172.19.0.3: seq=51 ttl=64 time=0.166 ms
64 bytes from 172.19.0.3: seq=52 ttl=64 time=0.332 ms
64 bytes from 172.19.0.3: seq=53 ttl=64 time=0.169 ms
64 bytes from 172.19.0.3: seq=54 ttl=64 time=0.171 ms
64 bytes from 172.19.0.3: seq=55 ttl=64 time=0.170 ms
64 bytes from 172.19.0.3: seq=56 ttl=64 time=0.170 ms
64 bytes from 172.19.0.3: seq=57 ttl=64 time=0.186 ms
64 bytes from 172.19.0.3: seq=58 ttl=64 time=0.239 ms
64 bytes from 172.19.0.3: seq=59 ttl=64 time=0.184 ms
64 bytes from 172.19.0.3: seq=60 ttl=64 time=0.233 ms
64 bytes from 172.19.0.3: seq=61 ttl=64 time=0.490 ms
64 bytes from 172.19.0.3: seq=62 ttl=64 time=0.173 ms
64 bytes from 172.19.0.3: seq=63 ttl=64 time=0.172 ms
64 bytes from 172.19.0.3: seq=64 ttl=64 time=0.174 ms
64 bytes from 172.19.0.3: seq=65 ttl=64 time=0.302 ms
64 bytes from 172.19.0.3: seq=66 ttl=64 time=0.195 ms
64 bytes from 172.19.0.3: seq=67 ttl=64 time=0.069 ms
64 bytes from 172.19.0.3: seq=68 ttl=64 time=0.165 ms
64 bytes from 172.19.0.3: seq=69 ttl=64 time=0.183 ms
64 bytes from 172.19.0.3: seq=70 ttl=64 time=0.168 ms
64 bytes from 172.19.0.3: seq=71 ttl=64 time=0.187 ms
64 bytes from 172.19.0.3: seq=72 ttl=64 time=0.179 ms
64 bytes from 172.19.0.3: seq=73 ttl=64 time=0.166 ms
64 bytes from 172.19.0.3: seq=74 ttl=64 time=0.168 ms
64 bytes from 172.19.0.3: seq=75 ttl=64 time=0.119 ms
64 bytes from 172.19.0.3: seq=76 ttl=64 time=0.167 ms
64 bytes from 172.19.0.3: seq=77 ttl=64 time=0.199 ms
64 bytes from 172.19.0.3: seq=78 ttl=64 time=0.187 ms
64 bytes from 172.19.0.3: seq=79 ttl=64 time=0.167 ms
64 bytes from 172.19.0.3: seq=80 ttl=64 time=0.344 ms
64 bytes from 172.19.0.3: seq=81 ttl=64 time=0.166 ms
64 bytes from 172.19.0.3: seq=82 ttl=64 time=0.166 ms
64 bytes from 172.19.0.3: seq=83 ttl=64 time=0.125 ms
64 bytes from 172.19.0.3: seq=84 ttl=64 time=0.221 ms
64 bytes from 172.19.0.3: seq=85 ttl=64 time=0.169 ms
64 bytes from 172.19.0.3: seq=86 ttl=64 time=0.168 ms
64 bytes from 172.19.0.3: seq=87 ttl=64 time=0.234 ms
64 bytes from 172.19.0.3: seq=88 ttl=64 time=0.178 ms
64 bytes from 172.19.0.3: seq=89 ttl=64 time=0.169 ms
64 bytes from 172.19.0.3: seq=90 ttl=64 time=0.197 ms
64 bytes from 172.19.0.3: seq=91 ttl=64 time=0.188 ms
64 bytes from 172.19.0.3: seq=92 ttl=64 time=0.205 ms
64 bytes from 172.19.0.3: seq=93 ttl=64 time=0.195 ms
64 bytes from 172.19.0.3: seq=94 ttl=64 time=0.081 ms
64 bytes from 172.19.0.3: seq=95 ttl=64 time=0.067 ms
64 bytes from 172.19.0.3: seq=96 ttl=64 time=0.170 ms
64 bytes from 172.19.0.3: seq=97 ttl=64 time=0.182 ms
64 bytes from 172.19.0.3: seq=98 ttl=64 time=0.271 ms
64 bytes from 172.19.0.3: seq=99 ttl=64 time=0.220 ms
64 bytes from 172.19.0.3: seq=100 ttl=64 time=0.152 ms
64 bytes from 172.19.0.3: seq=101 ttl=64 time=0.102 ms
64 bytes from 172.19.0.3: seq=102 ttl=64 time=0.130 ms
64 bytes from 172.19.0.3: seq=103 ttl=64 time=0.168 ms
64 bytes from 172.19.0.3: seq=104 ttl=64 time=0.098 ms
64 bytes from 172.19.0.3: seq=105 ttl=64 time=0.097 ms
64 bytes from 172.19.0.3: seq=106 ttl=64 time=0.066 ms
64 bytes from 172.19.0.3: seq=107 ttl=64 time=0.061 ms
64 bytes from 172.19.0.3: seq=108 ttl=64 time=0.115 ms
64 bytes from 172.19.0.3: seq=109 ttl=64 time=0.122 ms
64 bytes from 172.19.0.3: seq=110 ttl=64 time=0.166 ms
64 bytes from 172.19.0.3: seq=111 ttl=64 time=0.097 ms
64 bytes from 172.19.0.3: seq=112 ttl=64 time=0.165 ms
64 bytes from 172.19.0.3: seq=113 ttl=64 time=0.168 ms
64 bytes from 172.19.0.3: seq=114 ttl=64 time=0.166 ms
64 bytes from 172.19.0.3: seq=115 ttl=64 time=0.192 ms
64 bytes from 172.19.0.3: seq=116 ttl=64 time=0.169 ms
64 bytes from 172.19.0.3: seq=117 ttl=64 time=0.181 ms
64 bytes from 172.19.0.3: seq=118 ttl=64 time=0.080 ms
64 bytes from 172.19.0.3: seq=119 ttl=64 time=0.168 ms
64 bytes from 172.19.0.3: seq=120 ttl=64 time=0.186 ms
64 bytes from 172.19.0.3: seq=121 ttl=64 time=0.182 ms
64 bytes from 172.19.0.3: seq=122 ttl=64 time=0.187 ms
64 bytes from 172.19.0.3: seq=123 ttl=64 time=0.270 ms
64 bytes from 172.19.0.3: seq=124 ttl=64 time=0.167 ms
64 bytes from 172.19.0.3: seq=125 ttl=64 time=0.181 ms
64 bytes from 172.19.0.3: seq=126 ttl=64 time=0.187 ms
64 bytes from 172.19.0.3: seq=127 ttl=64 time=0.190 ms
64 bytes from 172.19.0.3: seq=128 ttl=64 time=0.434 ms
64 bytes from 172.19.0.3: seq=129 ttl=64 time=0.168 ms
64 bytes from 172.19.0.3: seq=130 ttl=64 time=0.168 ms
64 bytes from 172.19.0.3: seq=131 ttl=64 time=0.571 ms
64 bytes from 172.19.0.3: seq=132 ttl=64 time=0.167 ms
64 bytes from 172.19.0.3: seq=133 ttl=64 time=0.167 ms
64 bytes from 172.19.0.3: seq=134 ttl=64 time=0.069 ms
64 bytes from 172.19.0.3: seq=135 ttl=64 time=0.167 ms
64 bytes from 172.19.0.3: seq=136 ttl=64 time=0.166 ms
64 bytes from 172.19.0.3: seq=137 ttl=64 time=0.167 ms
64 bytes from 172.19.0.3: seq=138 ttl=64 time=0.167 ms
64 bytes from 172.19.0.3: seq=139 ttl=64 time=0.220 ms
64 bytes from 172.19.0.3: seq=140 ttl=64 time=0.166 ms
64 bytes from 172.19.0.3: seq=141 ttl=64 time=0.174 ms
64 bytes from 172.19.0.3: seq=142 ttl=64 time=0.199 ms
64 bytes from 172.19.0.3: seq=143 ttl=64 time=0.120 ms
64 bytes from 172.19.0.3: seq=144 ttl=64 time=0.167 ms
64 bytes from 172.19.0.3: seq=145 ttl=64 time=0.172 ms
64 bytes from 172.19.0.3: seq=146 ttl=64 time=0.101 ms
64 bytes from 172.19.0.3: seq=147 ttl=64 time=0.172 ms
64 bytes from 172.19.0.3: seq=148 ttl=64 time=0.153 ms
64 bytes from 172.19.0.3: seq=149 ttl=64 time=0.169 ms
64 bytes from 172.19.0.3: seq=150 ttl=64 time=0.168 ms
64 bytes from 172.19.0.3: seq=151 ttl=64 time=0.167 ms
64 bytes from 172.19.0.3: seq=152 ttl=64 time=0.150 ms
64 bytes from 172.19.0.3: seq=153 ttl=64 time=0.244 ms
64 bytes from 172.19.0.3: seq=154 ttl=64 time=0.169 ms
64 bytes from 172.19.0.3: seq=155 ttl=64 time=0.154 ms
64 bytes from 172.19.0.3: seq=156 ttl=64 time=0.103 ms
64 bytes from 172.19.0.3: seq=157 ttl=64 time=0.076 ms
64 bytes from 172.19.0.3: seq=158 ttl=64 time=0.121 ms
64 bytes from 172.19.0.3: seq=159 ttl=64 time=0.178 ms
64 bytes from 172.19.0.3: seq=160 ttl=64 time=0.163 ms
64 bytes from 172.19.0.3: seq=161 ttl=64 time=0.066 ms
64 bytes from 172.19.0.3: seq=162 ttl=64 time=0.067 ms
64 bytes from 172.19.0.3: seq=163 ttl=64 time=0.163 ms
64 bytes from 172.19.0.3: seq=164 ttl=64 time=0.168 ms
64 bytes from 172.19.0.3: seq=165 ttl=64 time=0.171 ms
64 bytes from 172.19.0.3: seq=166 ttl=64 time=0.204 ms
64 bytes from 172.19.0.3: seq=167 ttl=64 time=0.169 ms
64 bytes from 172.19.0.3: seq=168 ttl=64 time=0.167 ms
64 bytes from 172.19.0.3: seq=169 ttl=64 time=0.315 ms
64 bytes from 172.19.0.3: seq=170 ttl=64 time=0.182 ms
64 bytes from 172.19.0.3: seq=171 ttl=64 time=0.464 ms
64 bytes from 172.19.0.3: seq=172 ttl=64 time=0.168 ms
64 bytes from 172.19.0.3: seq=173 ttl=64 time=0.203 ms
64 bytes from 172.19.0.3: seq=174 ttl=64 time=0.234 ms
64 bytes from 172.19.0.3: seq=175 ttl=64 time=0.091 ms
64 bytes from 172.19.0.3: seq=176 ttl=64 time=0.097 ms
64 bytes from 172.19.0.3: seq=177 ttl=64 time=0.161 ms
64 bytes from 172.19.0.3: seq=178 ttl=64 time=0.084 ms
64 bytes from 172.19.0.3: seq=179 ttl=64 time=0.165 ms
64 bytes from 172.19.0.3: seq=180 ttl=64 time=0.115 ms
64 bytes from 172.19.0.3: seq=181 ttl=64 time=0.167 ms
64 bytes from 172.19.0.3: seq=182 ttl=64 time=0.081 ms
64 bytes from 172.19.0.3: seq=183 ttl=64 time=0.182 ms
64 bytes from 172.19.0.3: seq=184 ttl=64 time=0.189 ms
64 bytes from 172.19.0.3: seq=185 ttl=64 time=0.167 ms
64 bytes from 172.19.0.3: seq=186 ttl=64 time=0.167 ms
64 bytes from 172.19.0.3: seq=187 ttl=64 time=0.172 ms
64 bytes from 172.19.0.3: seq=188 ttl=64 time=0.172 ms
64 bytes from 172.19.0.3: seq=189 ttl=64 time=0.082 ms
64 bytes from 172.19.0.3: seq=190 ttl=64 time=0.172 ms
64 bytes from 172.19.0.3: seq=191 ttl=64 time=0.222 ms
64 bytes from 172.19.0.3: seq=192 ttl=64 time=0.082 ms
64 bytes from 172.19.0.3: seq=193 ttl=64 time=0.103 ms
64 bytes from 172.19.0.3: seq=194 ttl=64 time=0.064 ms
64 bytes from 172.19.0.3: seq=195 ttl=64 time=0.188 ms
64 bytes from 172.19.0.3: seq=196 ttl=64 time=0.191 ms
^C
--- container2 ping statistics ---
197 packets transmitted, 197 packets received, 0% packet loss
round-trip min/avg/max = 0.061/0.178/2.458 ms
/ #
/ # exit

What's next:
    Try Docker Debug for seamless, persistent debugging tools in any container or image → docker debug container1
    Learn more at https://docs.docker.com/go/debug-cli/

C:\Users\admin>
