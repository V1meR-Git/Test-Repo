```bash
cat <<EOF > /etc/zapret-firewall.nft
#!/bin/sh
nft insert rule inet fw4 mangle_postrouting meta mark 0x99 counter queue flags bypass to 200
EOF

chmod +x /etc/zapret-firewall.nft

uci set firewall.zapret_include=include
uci set firewall.zapret_include.type='script'
uci set firewall.zapret_include.path='/etc/zapret-firewall.nft'
uci commit firewall
```

В настройках Zapret выставить
Указанный порт должен отличаться от часто используемых, например 12345

```bash
FILTER_MARK = 0x99
NFQWS_PORTS_TCP = ваш порт
NFQWS_PORTS_UDP = ваш порт
```
Блок для интеграции Zapret от Remmitor для OpenWRT в Podkop от ITDog

```bash
{
	"type": "direct",
	"tag": "zapret-out",
	"routing_mark": 153
}
```
