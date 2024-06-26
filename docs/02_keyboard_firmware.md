
Следуйте [инструкции QMK](https://docs.qmk.fm/#/newbs_getting_started) для прошивки платы. Более наглядный процесс показан в [этом видео](https://www.youtube.com/watch?v=it_IcuvnjJM).

После того, как процесс завершен, вам нужно проверить, работают ли все клавиши, вам необходимо замкнуть hotswap разъемы, и проверить, срабатывает ли нажатие. Если некоторые клавиши не регистрируются, это может говорить о том, что диоды под этой клавишей припаяны плохо либо же сам диод не рабочий.

Также возможно вы столкнетесь с проблемой, когда будет работать только одна половинка, даже если они подключены между собой, и если оба контроллера работают. Я долго искал решение, и выходом из ситуации пришел новый метод проверки управляющей стороны, о котором также [говорил в видео](https://www.youtube.com/watch?v=it_IcuvnjJM).

Для оперативности оставляю эти фрагменты и [ссылку на статью](https://medium.com/@keebio/the-case-of-the-wayward-elite-c-73f0fd691f88):
- `qmk json2c old.json -o new.c` - конвертировать json файл из [QMK Configurator](https://config.qmk.fm/) в готовый сишный модуль с раскладкой.
- `#define SPLIT_USB_DETECT` - флаг для обхода "диода Шоттки", это позволяет добавить взаимодействие между половинками клавиатуры, если другие методы оказались не рабочими.
