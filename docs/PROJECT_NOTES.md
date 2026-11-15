# Pip-Boy 3000 Mk IV — рабочие заметки

Форк [zapwizard/pypboy](https://github.com/zapwizard/pypboy) + архив CAD/печати проекта ZapWizard (Joshua Driggs).

## Источники
- Тред RPF: https://www.therpf.com/forums/threads/functional-pip-boy-3000-mk-iv-from-fallout-4.245034/ (41 стр.)
- CAD "Unfinished Version" (Google Drive, дек. 2017): https://drive.google.com/drive/folders/1NlcHtdtjH62fnaz1pvxRJu8AqO-tezmg
- Фото/рендеры Flickr: https://www.flickr.com/photos/zapwizard/albums/72157657477982742
- Shapeways автора (гололенты и др.): https://www.shapeways.com/designer/zapwizard
- Бесплатная упрощённая модель Yvo de Haas: http://ytec3d.com/pip-boy-3000-mark-iv/
- Pip-Boy 2000 Mk VI (rad-модуль на стрелочном приборе): https://hackaday.io/project/173206-fully-functional-pip-boy-2000-mk-vi

Лицензия CAD: CC BY-NC-SA (см. `cad/zapwizard_unfinished/Cc-by-nc-sa.png`, readme в той же папке).
Некоммерческое использование, указывать автора, производные — под той же лицензией.

## Хронология (по треду)
- 2015: старт. CAD в Solid Edge, рендер Keyshot. Длина корпуса 138 мм, позже +10%.
- 2015–2017: план — плата BeagleBone Black, затем DragonBoard 410c (ради Android и приложения-компаньона).
- янв. 2018: CAD за покупку на Shapeways.
- июнь 2018: CAD выложен публично (это версия в `cad/`).
- 2018 изменения (НЕ в выложенном CAD): радио 1:9 вместо 1:3, плавное открывание гололенты,
  гололента включается магнитом, отдельные накладки кнопок, фиксатор колеса выбора в задней крышке,
  больше мелких PCB вместо проводов, место под Pocket Geiger.
- 2021: SLS-принтер Formlabs Fuse 1. Шарнир = контактное кольцо (6 каналов, pogo-пины).
  Задняя половина: аккумулятор, зарядка, USB ("Power Board r1.0").
- июль 2021: GUI — этот форк pypboy.

## Электроника (версия 2021)
- Raspberry Pi CM4
- Дисплей Pimoroni HyperPixel 4.0 Square 720×720 (DPI, занимает почти весь GPIO)
- RP2040 — кнопки, энкодеры, потенциометры, аналог; связь с GUI по USB HID / serial
- Гейгер: SparkFun Pocket Geiger (PIN-диод), https://www.sparkfun.com/products/14209
- Стрелка RAD: миниатюрный air-core мотор (автомобильный)
- Динамик 13 мм
- Шкалы: акрил с печатью + рассеиватель + LED на PCB

## Механика
- Колесо выбора: рифление = шестерня → энкодер; кнопка под ним (ход 1 мм); фиксатор-плунжер
- Макро-ручка 5 позиций (Stat/Inventory/Data/Map/Radio), шариковый плунжер, потенциометр
- Ручка радио: редуктор, потенциометр
- Защёлка снизу + магниты; шарнир на съёмном штифте McMaster
- Печать рассчитана на SLS (нейлон). FDM — с переменным успехом, много шлифовки.

## Мой план (плата)
- Кандидаты: Mango Pi MQ-Quad (H616, размер Pi Zero) или Orange Pi 5/5 Pro (не влезает на место CM4 без переделки).
- HyperPixel не работает вне Raspberry Pi → нужен 4" 720×720 по HDMI или MIPI-DSI.
- Ввод через RP2040 USB HID — не зависит от платы.
- Android: на MQ-Quad только Android 10 TV (HDMI), на MQ-Pro нет; на Orange Pi 5 есть 12/13. Для pypboy не нужен.

## Известная проблема репозитория на Windows
В `images/perks/` есть папки `Gunslinger` и `gunslinger` — на Windows (регистронезависимая ФС) они сливаются.
Работать лучше в WSL/Linux, либо переименовать одну из папок.
