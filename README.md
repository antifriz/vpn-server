# VPN server

This is a docker-compose project to bring up VPN server with DyDNS by noip.com.

## Running

1. Clone the repo
1. Set the working directory to the root of the repo.
1. Create a new file `override.env` in the root of the repo.
1. Add a line `TZ=Etc/UTC` and change the value to the timezone of the VPN server (see https://en.wikipedia.org/wiki/List_of_tz_database_time_zones)
1. Add a line `SERVERURL=change.me.to.noip.address` and change the value to the given noip.com FQDN (the whole domain name).
1. Add a line `PEERS=comma,separated,names,of,vpn,users` and change the value to the names of VPN users which will connect to this VPN. There will be created a directory for each user under `/opt/wireguard/config` with creds to connect to the VPN.
1. Add lines `NOIP_USER=...` and `NOIP_PASS=...` and change them to the given credentials on the noip.com page for the given FQDN.
1. Optionally add `NOIP_INTERVAL=60` and change the value to the interval in seconds between two attempts to update the server IP.
1. Run `docker compose --build up` to bring up the whole setup
1. Directory `/opt/wireguard/config` will contain credentials required to connect to the VPN.
