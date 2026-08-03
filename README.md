# Subtitles Addon (ver. ..) for IX-Ray Platform

## Overview
If you hear speech, you see the text. But there is also a feature: in addition to the usual subtitles on the screen, subtitles are implemented in the world space - they appear above the speaker's head. You can use it in your mods, the addon adds new fields to the sound sections from `configs/misc/script_sound.ltx` and all files included to it.

## Remarks

> [!WARNING]
>
> Supported only on __IX-Ray Platform__!

## Requirements

Installation:

1. Install original Stalker Call of Pripyat 1.6.02
2. Install current version of IX-Ray (minimum ..)
3. Extract addon archive into the game folder
4. Start the game and play

Link to the current __IX-Ray__ [release](https://github.com/ixray-team/ixray-1.6-stcop/releases/latest)

## Contributors
* `Emmis`
* `Drombeys`

## License

Сontents of this repository are licensed under terms of the __CC BY-NC-SA 4.0__ license unless otherwise specified. See [this](./LICENSE.txt) file for details

## Обзор
Слышите речь - видите текст. Но есть и особенность: помимо привычных субтитров на экране, реализованы субтитры в мировом пространстве - появляются над головой говорящего. Вы можете использовать его в своих модах, аддон добавляет новые поля в секции звуков из `configs/misc/script_sound.ltx` и всех подключенных к нему файлов.

## Примечаниe

> [!WARNING]
>
> Поддерживается только на __IX-Ray Platform__!

## Рекомендации

Установка:

1. Установить оригинальный Stalker Call of Pripyat 1.6.02
2. Установить актуальную версию IX-Ray (минимальная ..)
3. Распакуйте архив аддона в папку с игрой
4. Запустите игру и играйте

Ссылка на текущую версию __IX-Ray__ [релиз](https://github.com/ixray-team/ixray-1.6-stcop/releases/latest)

## Документация

### Типы звуков и виды субтитров, которые они поддерживают
| **Тип звука** | **Экранные субтитры** | **World Space субтитры** |
|---------------|:---------------------:|:------------------------:|
| `npc`         |           ✅          |            ✅           |
| `actor`       |           ✅          |            ❌           |
| `3d`          |           ✅          |            ✅           |

### Новые поля в секциях звуков
| **Поле** | **Тип** | **Значение по умолчанию** | **Справка** |
|----------|---------|---------------------------|-------------|
| `subtitles` | `bool` | Значение поля `def_npc_subtitles`, `def_actor_subtitles` или `def_3d_subtitles` (в зависимости от типа звука)<br><br>секции `[subtitles]`<br><br>в файле `configs\subtitles.ltx` | Включить/выключить экранные субтитры для выбранного звука |
| `subtitles_name` | `string` | Имя НПС, актора или объекта (в зависимости от типа звука) | Имя говорящего экранных субтитров |
| `subtitles_text` | `string` | Путь до звука в виде (пример):<br>`$characters_voice_scenario_zaton_zat_a23_about_x8` | Текст экранных субтитров |
| `subtitles_distance` | `number` | Значение поля `max_distance`<br><br>секции `[subtitles]`<br><br>в файле `configs\subtitles.ltx` | Дистанция от камеры до говорящего больше которой экранные субтитры перестанут показываться |
| `subtitles_delay` | `number` | Значение поля `show_delay`<br><br>секции `[subtitles]`<br><br>в файле `configs\subtitles.ltx` | Задержка перед показом в миллисекундах для экранных субтитров |
| `ws_subtitles` | `bool` | Значение поля `def_npc_subtitles` или `def_3d_subtitles`<br>(в зависимости от типа звука)<br><br>секции `[world_space_subtitles]`<br><br>в файле `configs\subtitles.ltx` | Включить/выключить World Space субтитры для выбранного звука |
| `ws_subtitles_text` | `string` | Путь до звука в виде (пример):<br>`$characters_voice_scenario_zaton_zat_a23_about_x8` | Текст World Space субтитров |
| `ws_subtitles_section` | `string` | Значение поля `def_ws_section`<br><br>секции `[world_space_subtitles]`<br><br>в файле `configs\subtitles.ltx` | Секция World Space элемента |
| `ws_subtitles_delay` | `number` | Значение поля `show_delay`<br><br>секции `[world_space_subtitles]`<br><br>в файле `configs\subtitles.ltx` | Задержка перед показом в миллисекундах для World Space субтитров |

### Примеры
#### Пример с типом npc
*За основу взят звук привествия Бороды.*

Включаем экранные субтитры и прописываем имя и текст, что не обязательно, тогда будут значения по умолчанию:
```ini
[zat_a2_stalker_barmen_greeting]
type = npc
path = scenario\zaton\zat_a2_stalker_barmen_greeting_
shuffle = rnd
play_always = true
idle = 0,0,100
subtitles = true
subtitles_name = st_test_name
subtitles_text = st_text_text
```
<details>
<summary>Показать результат</summary>
<img width="974" height="538" alt="image" src="https://github.com/user-attachments/assets/8eb3d942-3b86-4824-ac69-4669924fc628" />
</details>

Вдобавок включим world space субтитры и пропишем свой текст:
```ini
[zat_a2_stalker_barmen_greeting]
type = npc
path = scenario\zaton\zat_a2_stalker_barmen_greeting_
shuffle = rnd
play_always = true
idle = 0,0,100
subtitles = true
subtitles_name = st_test_name
subtitles_text = st_text_text
ws_subtitles = true
ws_subtitles_text = st_test2_text
```
<details>
<summary>Показать результат</summary>
<img width="974" height="576" alt="image" src="https://github.com/user-attachments/assets/baaf4683-fa26-4e83-974a-08b528a347e7" />
</details>

#### Пример с типом actor
*За основу взят звук осмотра одного из вертолетов*

Этот тип звука поддерживает только экранные субтитры, так что их и пропишем:
```ini
[zat_b100_heli_2_maps]
type = actor
npc_prefix = false
path = characters_voice\scenario\zaton\zat_b100_heli_2_maps
shuffle = seq
idle = 0,0,100
subtitles = true
subtitles_text = st_test_text
```
<details>
<summary>Показать результат</summary>
<img width="974" height="520" alt="image" src="https://github.com/user-attachments/assets/a1869a56-d4e0-41f6-a074-e6b681b39d6e" />
</details>

> [!NOTE]
> Обратите внимание, что мы не указали поле `subtitles_name`, в таком случае взялось значение по умолчанию, что для звука с типом actor будет имя актора.

#### Пример с типом 3d
*За основу взят звук “убери оружие” при подходе к Скадовску, который проигрывается из рупора висячего у двери*

Включим сразу оба вида субтитров. Для экранных пропишем свои значения имени и текста, а для world space субтитров только новую секцию world space элемента, так как в секции по умолчанию элемент привязан к кости bip01_head, которой нет у физических объектов:
```ini
[zat_a2_base_megaphone]
type = 3d
path = characters_voice\scenario\zaton\zat_a2_base_megaphone_
shuffle = rnd
idle = 10,15,100
subtitles = true
subtitles_name = zat_a2_stalker_barmen_name
subtitles_text = st_test_text
ws_subtitles = true
ws_subtitles_section = ws_test_element
```

Создадим нашу новую секцию world space элемента `[ws_test_element]`, в которой уберем только привязку к кости, тогда элемент будет прикреплен к позиции объекта. 
Файл `configs/misc/mod_world_space_ui_elements_subtitles.ltx` (реализует [DLTX](https://github.com/ixray-team/ixray-1.6-stcop/wiki/DLTX)):
```ini
[ws_subtitles_element]:ws_default_element
billboard = subtitles_billboard
show = false
show_distance = 15
attach_bone = bip01_head

[ws_test_element]:ws_subtitles_element
attach_bone = nil
```

Не забудем прописать наш world space элемент нужному объекту. Файл `configs/mod_system_subtitles.ltx` (реализует [DLTX](https://github.com/ixray-team/ixray-1.6-stcop/wiki/DLTX)):
```ini
![stalker]
ws_elements = ws_subtitles_element

[zaton_a2_ph_rupor]
ws_elements = ws_test_element
```
> [!NOTE]
> В данном примере мы прописываем world space элемент конкретному объекту. Обратите внимание, что субтитры над головой НПС прописаны в секции `[stalker]`, то есть для всех человеческих НПС разом. Подобное может быть удобно в некоторых случаях. Например, мы бы могли прописать наш новый world space элемент в секцию `[physic_object]`, что добавило бы его для всех физических объектов в игре, без необходимости прописывать каждому отдельно. Но важно использовать поддобное только с пониманием дела.

<details>
<summary>Показать результат</summary>
<img width="974" height="588" alt="image" src="https://github.com/user-attachments/assets/fac6661b-2943-4f80-9242-18323f1cd66c" />
</details>

> [!NOTE]
> Обратите внимание на world space субтитры, так как мы не указали поле `ws_subtitles_text` в секции звука, взялось значение по умолчанию, то есть путь до звука с символом `$` в начале. Без этого символа будут приходить сообщения на КПК, как это было в Чистом Небе и соталось в Зов Припяти, но не использовалось.

### Дополнительные функции
#### функция fake_subtitles
Для экранных субтитров существует функция `fake_subtitles`, которая реализована в неймспейсе xr_effects, что позволит вызывать её из спейс рестрикторов и т.д.

Принимаемые параметры: 
* `имя`
* `текст`
* `время_жизни` (не обязательный параметр)
* `задержка_перед_появлением` (не обязательный параметр)

Пример вызова из спейс рестриктора:
```ini
[sr_idle@1]
on_info = %=fake_subtitles(st_actor_name:st_test_fake_text:50:30)% sr_idle@2

[sr_idle@2]
```
Покажет экранные субтитры на 5 сек. после задрежки в 3 сек.

<details>
<summary>Показать результат</summary>
<img width="974" height="177" alt="image" src="https://github.com/user-attachments/assets/3d013ea8-4f4f-4c0c-80aa-fb8c3761c7e0" />
</details>

## Контрибьюторы
* `Emmis`
* `Drombeys`

## Лицензия

Содержимое этого репозитория лицензировано в соответствии с условиями лицензии __CC BY-NC-SA 4.0__, если не указано иное. Подробности см. в файле [здесь](./LICENSE.txt)
