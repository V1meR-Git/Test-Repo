# Настройка интеграции

Команды терминала для межсетевого экрана

```bash
cat <<EOF > /etc/zapret-firewall.nft
#!/bin/sh
nft insert rule inet fw4 mangle_postrouting meta mark 0x99 counter queue flags bypass to 200
EOF
```

```bash
chmod +x /etc/zapret-firewall.nft
```

```bash
uci set firewall.zapret_include=include
uci set firewall.zapret_include.type='script'
uci set firewall.zapret_include.path='/etc/zapret-firewall.nft'
uci commit firewall
```

В настройках Zapret выставить

```bash
FILTER_MARK = 0x99
NFQWS_PORTS_TCP = ваш порт
NFQWS_PORTS_UDP = ваш порт
```
Указанный порт должен отличаться от часто используемых, например 12345

# Блок для интеграции в Podkop от ITDog

```bash
{
	"type": "direct",
	"tag": "zapret-out",
	"routing_mark": 153
}
```
