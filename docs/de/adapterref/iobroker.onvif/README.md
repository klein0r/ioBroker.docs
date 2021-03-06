---
translatedFrom: en
translatedWarning: Wenn Sie dieses Dokument bearbeiten möchten, löschen Sie bitte das Feld "translationsFrom". Andernfalls wird dieses Dokument automatisch erneut übersetzt
editLink: https://github.com/ioBroker/ioBroker.docs/edit/master/docs/de/adapterref/iobroker.onvif/README.md
title: ioBroker.onvif
hash: PjF2jptQFzLAzlK4b4PHvZ93TS8NMOg+4cYhuz9a16A=
---
![Logo](../../../en/adapterref/iobroker.onvif/admin/onvif_logo.png)

![NPM-Version](http://img.shields.io/npm/v/iobroker.onvif.svg)
![Downloads](https://img.shields.io/npm/dm/iobroker.onvif.svg)
![Anzahl der Installationen (spätestens)](http://iobroker.live/badges/onvif-installed.svg)
![Anzahl der Installationen (stabil)](http://iobroker.live/badges/onvif-stable.svg)
![Abhängigkeitsstatus](https://img.shields.io/david/Haba1234/iobroker.onvif.svg)
![Bekannte Sicherheitslücken](https://snyk.io/test/github/Haba1234/ioBroker.onvif/badge.svg)
![NPM](https://nodei.co/npm/iobroker.onvif.png?downloads=true)
![Travis-CI](http://img.shields.io/travis/Haba1234/ioBroker.onvif/master.svg)

# IoBroker.onvif
## RU
### Настройка
1. Открыть Настройки драйвера
2. Нажать кнопку сканирования (сверху справа)
3. Ввести необходимые настройки или оставить по умолчанию: startRange - начальный ip адрес диапазона сканирова

End Range - конечный ip адрес диапазона сканирования, Port-Liste - через запятую порты сервиса onvif (по умолчанию: 80, 75 ию

4. ARTажать SCAN STARTEN

Если все сделано правильно, в основном окне настроек появятся найденые камеры и через несколько секунд должны будут подтянуться снапшоты

### События
Драйвер автоматически подписывается на события к настроенным камерам.
События, которые генерирует камера, появятся в объектах вида:

```
onvif.0.122_116_220_230_2033.message.ruleengine.cellmotiondetector.motion.IsMotion
onvif.0.122_116_220_230_2033.message.ruleengine.tamperdetector.tamper.IsTamper
```

### Запрос снапшота
Для этого используется команда: `sendTo('onvif.0', command, message, callback);`

Пример скрипта для запроса снапшота и отправка в телеграм:

```
const fs = require('fs');

function getSnapshot(caption){
    sendTo('onvif.0', 'saveFileSnapshot', {"id":"192_168_1_4_80", "file":"/opt/cameras/snapshot.jpg"}, (data) => {
        console.log('image принят: ' + data);
        if (data === "OK")
            sendTo('telegram.0', {text: '/opt/cameras/snapshot.jpg', caption: caption});
    });
}
```

* caption * - заголовок для картинки в телеграме.
Вызывать можно как по событию, так и по кнопке / рассписанию.

Вариант загрузки в промежуточный Puffer в место файла:

```
function getSnapshot(){
    sendTo('onvif.0', 'getSnapshot', {"id":"192_168_1_4_80"}, (result) => {
        if (result.err) log(result);
        if (result.img){
			log('image принят: ' + typeof result.img);
            sendTo('telegram.0', {
                user: 'user',
                text: result.img.rawImage,
                type: 'photo',
                caption: 'Camera 1'
			});
		}
    });
}
```

### События Камеры
Чтобы отключить подписку на события от камеры, необходимо выставить состояние `subscribeEvents = false` и перз
При изменении в панели администратора, перезугрузка адаптера выполняется автоматически.

События имеют тип "Объект", например:

```
{
	'Value': false,
	'UtcTime': '2020-04-26T17:35:34.000Z'
}
```

`Value` - значение / состояние, `UtcTime` - время изменения значения / состояния

Т.к. адаптер работает по подписке на события, то время состояния `state.ts` может не совпадать сере

## ENG
### Anpassung
1. Öffnen Sie die Treibereinstellungen
2. Drücken Sie die Scan-Taste (oben rechts).
3. Geben Sie die erforderlichen Einstellungen ein oder belassen Sie die Standardeinstellung:

startRange - die Start-IP-Adresse des Scanbereichs, End Range - die End-IP-Adresse des Scanbereichs, Portliste - durch Kommas getrennte Ports des Onvif-Dienstes (Standard: 80, 7575, 8000, 8080, 8081), Benutzername - Standardadministrator, Passwort - Standardadministrator

4. Drücken Sie START SCAN

Wenn alles korrekt gemacht wurde, werden die gefundenen Kameras in einem primären Einstellungsfenster angezeigt und in einigen Sekunden müssen die Schnappschüsse verschärft werden.

### Veranstaltungen
Der Treiber abonniert automatisch Ereignisse für die konfigurierten Kameras.
Die von der Kamera erzeugten Ereignisse werden in folgenden Objekten angezeigt:

```
onvif.0.122_116_220_230_2033.message.ruleengine.cellmotiondetector.motion.IsMotion
onvif.0.122_116_220_230_2033.message.ruleengine.tamperdetector.tamper.IsTamper
```

### Snapshot-Anfrage
Verwenden Sie dazu den Befehl: `sendTo('onvif.0', command, message, callback);`

Beispiel eines Skripts zur Anforderung des Schnappschusses und zum Senden an Telegramm:

```
const fs = require('fs');

function getSnapshot(caption){
    sendTo('onvif.0', 'saveFileSnapshot', {"id":"192_168_1_4_80", "file":"/opt/cameras/snapshot.jpg"}, (data) => {
        console.log('image received: ' + data);
        if (data === "OK")
            sendTo('telegram.0', {text: '/opt/cameras/snapshot.jpg', caption: caption});
    });
}
```

* caption * - steuert auf das Bild im Telegramm zu Es ist möglich, sowohl bei einem Ereignis als auch gemäß der Schaltfläche / dem Zeitplan zu verursachen.

Die Option zum Laden in einen Zwischenpuffer am Dateispeicherort:

```
function getSnapshot(){
    sendTo('onvif.0', 'getSnapshot', {"id":"192_168_1_4_80"}, (result) => {
        if (result.err) log(result);
        if (result.img){
			log('image received: ' + typeof result.img);
            sendTo('telegram.0', {
                user: 'user',
                text: result.img.rawImage,
                type: 'photo',
                caption: 'Camera 1'
			});
		}
    });
}
```

### Kameraereignisse
Um das Abonnement für Ereignisse von der Kamera zu trennen, müssen Sie den Status `subscribeEvents = false` setzen und den Adapter neu starten.
Beim Ändern im Admin-Bereich wird der Adapter automatisch neu gestartet.

Ereignisse sind vom Typ "Objekt", zum Beispiel:

```
{
	'Value': false,
	'UtcTime': '2020-04-26T17:35:34.000Z'
}
```

`Value` - Wert / Zustand, `UtcTime` - Zustandsänderungszeit

Da der Adapter Ereignisse abonniert, stimmt die Statuszeit von `state.ts` möglicherweise nicht mit der Echtzeit des Ereignisses in der Kamera überein.

## Changelog

### 0.4.3 (2020-05-08)
* (haba1234) Snapshot preview is squeezed
* (haba1234) Preview is buffered and not requested again
* (haba1234) After a minute, re-subscribe to camera events after 4 errors
* (haba1234) Support digest authentification
* (haba1234) node >= 10

### 0.4.2 (2020-05-03)
* (haba1234) Updated admin panel

### 0.4.1 (2020-04-27)
* (haba1234) States as an Object
* (haba1234) Error control 'pullMessages'. Disconnect if there are more than three errors
* (haba1234) Encryption disabled. Compatibility issues

### 0.3.0 (2020-04-24)
* (haba1234) Added support for the Discovery adapter
* (haba1234) Added password encryption

### 0.2.0 (2020-04-21)
* (haba1234) Added camera settings
* (haba1234) Changes in the structure of objects (ATTENTION! After updating, delete cameras and add again)
* (haba1234) Fixed issue [#9](https://github.com/Haba1234/ioBroker.onvif/issues/9)

### 0.1.2 (2020-04-19)
* (haba1234) Fixed uncaught exception: The \"chunk\" argument must be one of type string or Buffer
* (haba1234) Add state 'subscribeEvents'

### 0.1.1 (2020-04-18)
* (haba1234) Port polling bug fixed

### 0.1.0 (2020-04-15)
* (haba1234) bag fix and different little things
* (haba1234) compact mode
* (haba1234) deprecated 'request' is replaced by class 'http'
* (haba1234) 'onvif-snapshot' is replaced by class 'http'
* (haba1234) Added translate
* (haba1234) Refactoring code

### 0.0.2 (2018-11-20)
* (haba1234) add events and snapshot

### 0.0.1 (2018-02-20)
* (Kirov Ilya) intial commit

## License

The MIT License (MIT)

Copyright (c) 2018-2020 Haba1234 <b_roman@inbox.ru>