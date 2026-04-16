Блок для интеграции Zapret от Remmitor для OpenWRT в Podkop от ITDog

```bash
{
	"type": "direct",
	"tag": "zapret-out",
	"routing_mark": 153
}
```

В настройках Zapret выставить

```bash
FILTER_MARK = 0x99
NFQWS_PORTS_TCP = ваш порт
NFQWS_PORTS_UDP = ваш порт
```

Указанный порт должен отличаться от часто используемых, например 12345
