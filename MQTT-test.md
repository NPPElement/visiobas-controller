# MQTT test
Установит mosquitto и mosquitto-clients

`
sudo apt --assume-yes install mosquitto mosquitto-clients
`

Подписатся на топики

`
mosquitto_sub -L mqtt://user:user@visiodesk.net:1883/#
`

Открыть второй терминал и опубликоват топик {device_id} {object_type} {object_id} {present_value} {status_flags}

Пример для статтуса вкл первый автомат

`
mosquitto_pub -L mqtt://user:user@visiodesk.net:1883/Site/1300 -m '1300 3 3200 1 0'
`

Пример для статтуса выкл первый автомат

`
mosquitto_pub -L mqtt://user:user@visiodesk.net:1883/Site/1300 -m '1300 3 3200 0 0'
`

Пример для управления он отличается началом Set вместо Site и будет принят только контроллером

`
mosquitto_pub -L mqtt://user:user@visiodesk.net:1883/Set/200 -m '{"jsonrpc":"2.0","method":"value","params":{"device_id":200,"object_identifier":3901,"object_type":4,"priority":11,"value":1}}'
`
