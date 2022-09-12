# How to init OpenVPN

with `docker-compose.yml`, do the next commands :

```bash
docker compose run openvpn ovpn_genconfig -u udp://<DNS or IP ADDRESS>
docker compose run openvpn ovpn_initpki
docker compose up -d
docker exec -it openvpn easyrsa build-client-full CLIENTNAME nopass
docker exec -it openvpn ovpn_getclient CLIENTNAME > CLIENTNAME.ovpn
```
