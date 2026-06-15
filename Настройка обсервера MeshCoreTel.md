## Настройка репитера / обсервера MeshCoreTel

*Пошаговая инструкция по настройке устройства для работы как репитер или обсервер в сети MeshCore **Московского региона** с прошивкой [MeshCoreTel-firmware](https://github.com/VBart/MeshCoreTel-firmware) от [VBart](https://github.com/VBart). Эти настройки подходят не для всех устройств, но являются хорошим вариантом для большинства популярных плат. [Инструкция по прошивке](https://vbart.github.io/MeshCoreTel-firmware/releases/).*

### 1. **Основные настройки ноды:**
- `set name <name>` - произвольное имя узла
- `set prv.key <private_key>` - приватный ключ (для переноса с другой ноды)
- `password <new_password>` - пароль для администрирования
- `set owner.info <text>` - информация о владельце этого узла
- `set lat <degrees>` - широта узла (в формате 00.000000)
- `set lot <degrees>` - долгота узла (в формате 00.000000)
### 2. **Настройки радио:**
- `set radio 868.731018,62.5,7,7`  - частота, BW, SF, CR ([[Настройки BW, SF и CR|подробнее]])
- `set path.hash.mode 1` - размер хеша в 2 байта ([[Настройка размера хэша 2 байта|подробнее]])
- `set tx 20` - уровень мощности передачи в dBm (зависит от платы)
- `set radio.fem.rxgain off` -  выключить LNA (для heltec v4.3)
- `powersaving off` - отключение режима энергосбережения
- `set loop.detect minimal` - включение функции обнаружения петель 
- `set txdelay 1.0` - коэффициент задержки повторной передачи flood-трафика
- `set direct.txdelay 0.3` -коэффициент задержки прямой передачи
- `set multi.acks 1` - включение поддержки Multi-Acks
- `set flood.advert.interval 24` - интервал flood-рекламы (в часах)
- `set advert.interval 120` - интервал zero-hop-рекламы (в минутах)
- `set flood.max 32` - максимальное количество flood-переходов
- `set flood.max.advert 16` - лимит хопов для пакетов-объявлений (advert)
### 3. **Настройки WiFi сети:**
- `set wifi.ssid <your_network_name>` - имя сети (SSID)
- `set wifi.pwd <your_wifi_password>` - пароль сети
- `set wifi.powersaving min` -  задаёт режим энергосбережения WiFi
### 4. **Настройки MQTT-клиента (обсервера):**
- `set mqtt.iata MOW` - установка региона
- `set mqtt.tx on`: включает публикацию переданных пакетов

### 5. **Настройка регионов ([[Регионы - зачем они нужны|зачем это нужно]] и [[Регионы - как это работает|как оно работает]]):
#### "**Классический**" вариант команд:
- `region allowf *` - разрешает пересылку flood-сообщений без scope
- `region put ru`
- `region put mow ru`
- `region put msk mow`
- `region put sao msk`
- `region put svao msk`
- `region put vao msk`
- `region put uvao msk`
- `region put uao msk`
- `region put uzao msk`
- `region put zao msk`
- `region put szao msk`
- `region put mosobl mow`
- `region put north mosobl`
- `region put north-east mosobl`
- `region put east mosobl`
- `region put south-east mosobl`
- `region put south mosobl`
- `region put south-west mosobl`
- `region put west mosobl`
- `region put north-west mosobl`
- `region home <region>` - выбор "домашнего" региона данного узла
- `region` - проверка результата настройки
- `region save` - сохранение изменения

> *Для `msk` и `mosobl` (стр. 5-12 и 14-21) выбрать только необходимые округа / сектора:*
   `ru` - Россия
   `mow` - Москва + Московская область
   `msk` - Москва
   `mosobl` - Московская область

#### "**Новый**" вариант команд (для прошивок MeshCore **1.16+**)

- `region allowf *` - разрешает пересылку flood-сообщений без scope
- `region def ru mow msk msk sao`
- `region def ru mow msk msk svao`
- `region def ru mow msk msk vao`
- `region def ru mow msk msk uvao`
- `region def ru mow msk msk uao`
- `region def ru mow msk msk uzao`
- `region def ru mow msk msk zao`
- `region def ru mow msk msk szao`
- `region def ru mow mosobl north`
- `region def ru mow mosobl north-east`
- `region def ru mow mosobl east`
- `region def ru mow mosobl south-east`
- `region def ru mow mosobl south`
- `region def ru mow mosobl south-west`
- `region def ru mow mosobl west`
- `region def ru mow mosobl north-west`
- `region home <region>` - выбор "домашнего" региона данного узла
- `region` - проверка результата настройки
- `region save` - сохранение изменения

> *Для `msk` и `mosobl` (стр. 2-17) выбрать только необходимые округа / сектора:*
   `ru` - Россия
   `mow` - Москва + Московская область
   `msk` - Москва
   `mosobl` - Московская область

### 6. **Завершение настройки**:

- `reboot` - перезагрузка устройства для применения настроек

  