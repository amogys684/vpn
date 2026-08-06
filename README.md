# VPN-набор для INCY

Подписка в открытом (plain text) формате — совместима с приложением **INCY**
(iOS / Android / Windows / Linux / TV), а также с Happ, V2RayTun, Streisand,
Hiddify и другими клиентами на ядре Xray.

Файл: `aaaaaaaaaaa.txt`

## Состав (44 сервера)

| Протокол   | Кол-во |
|------------|--------|
| VLESS Reality / TLS / none (tcp, ws, grpc, xhttp) | 32 |
| Hysteria2 (hy2) | 10 |
| Trojan (ws, xhttp) | 2 |

## Что исправлено для поддержки INCY

Параметры ссылок приведены в соответствие с официальной документацией INCY
([Параметры конфигов](https://incy.gitbook.io/docs/dokumentaciya-dlya-razrabotchikov/parametry-konfigov)):

- `type=raw` → `type=tcp` (INCY принимает: tcp, ws, grpc, xhttp, kcp, quic);
- убраны не поддерживаемые параметры:
  - `mode=gun` (мода для gRPC, INCY её не парсит),
  - `packetEncoding=xudp`, `udp=1`,
  - `insecure=0` (для VLESS/Hysteria2 — это значение по умолчанию),
  - `headerType=none` и пустые параметры (`authority=`, `path=`, `host=`);
- `mode=packet-up` → `mode=packet` (режимы xhttp в INCY: auto, packet, connect);
- у Hysteria2-ссылок убраны `headerType=none&encryption=none`;
- убран лишний слэш перед `?` в первой hy2-ссылке (`:443/?sni=` → `:443?sni=`).

Все серверы, UUID, ключи Reality (`pbk`, `sid`, `spx`), пути и хосты сохранены
без изменений.

## Как подключить в INCY

1. Скопируйте содержимое `aaaaaaaaaaa.txt` целиком.
2. В INCY: «Добавить подписку» → «Импортировать из буфера» (или вставьте ссылку
   на файл/сырой GitHub-URL как URL подписки).
3. Приложение само распознает plain text формат и служебные строки
   `#profile-title`, `#profile-update-interval`, `#support-url`.

## Замечания

- Серверы бесплатные и публичные — работоспособность и скорость не
  гарантируются, часть может быть недоступна.
- Если какой-то сервер не подключается — это обычно проблема самого сервера,
  а не формата ссылки.
