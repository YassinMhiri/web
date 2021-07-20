---
title: AddSimpleModelTimed
description: Добавляет сторонний объект для скачивания.
tags: []
---

<VersionWarn version='SA-MP 0.3.DL R1' />

## Описание

Аналог AddSimpleModel, только с дополнительными крайними двумя параметрами времени.
Добавляет сторонний объект для скачивания. Файл модели будет помещен в папку на компьютер игрока Documents\GTA San Andreas User Files\SAMP\cache под названием IP и Порта сервера в виде CRC.

| Параметр     | Описание                                                                                                                |
| ------------ | ----------------------------------------------------------------------------------------------------------------------- |
| virtualworld | Виртуальный мир, в котором объект доступен. Используйте -1 для всех миров.                                              |
| baseid       | ID существующего объекта ( для замены объекта при ошибке загрузки )                                                     |
| newid        | ID нового объекта в пределах от -1000 до -30000 (29000 слотов) для использования в CreateObject или CreatePlayerObject. |
| dffname      | Название .dff файла колизии модели, расположенного стандартно в папке models (параметр настройки artpath).              |
| txdname      | Название .txd файла текстур модели, расположенного стандартно в папке models (параметр настройки artpath).              |
| timeon       | Время игрового мира (часы), со скольки объект виден.                                                                    |
| timeoff      | Время игрового мира (часы), когда объект пропадает.                                                                     |

## Возвращаемые данные

1: Функция выполнена успешно.

0: Функция не выполнена.

## Примеры

```c
public OnGameModeInit()
{
    AddSimpleModelTimed(-1, 19379, -2000, "wallzzz.dff", "wallzzz.txd", 9, 18); // Объект будет виден с 9:00 до 18:00
    return 1;
}
```

## Примечания

:::tip

`useartwork` должна быть включена ( 1 ) в настройках сервера, чтобы данная функция работала. В случае если установлен виртуальный мир (virtualworld), модель будет скачана когда игрок попадёт в указанный виртуальный мир.

:::

:::warning

В данный момент нет ограничений для вызова данной функции, но учтите, что если вы вызываете функцию НЕ в OnFilterScriptInit/OnGameModeInit, то у игроков, которые находяться на сервере, могут не быть скачаны данные файлы модели.

:::

## Связанные функции

- [OnPlayerFinishedDownloading](../callbacks/OnPlayerFinishedDownloading.md): Вызывается когда игрок закончил скачивание сторонних файлов.
- [AddSimpleModel](AddSimpleModel.md): Добавляет стороннюю модель объекта для скачивания.