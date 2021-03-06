---
title: Local File Inclusion
localeTitle: Включение локального файла
---
## Включение локального файла

Уязвимость в приложении, вызванная программистом, требующая ввода файла, предоставленного пользователем, и не дезинфекция ввода перед доступом к запрашиваемому файлу. Это приводит к включению файла, где он не должен быть.

### Примеры локальных попыток включения файлов

Веб-сайт позволяет просматривать PDF-файлы как `download.php?file=myfile.php` , из-за отсутствия надлежащей проверки злоумышленник может запросить / etc / passwd и получить конфиденциальную информацию о конфигурации с веб-сервера.

### Защита вашего сайта от локальных атак на включение файлов в PHP

```PHP
<?php 
 if(basename($_GET['file]) !== $_GET['file']) { 
  die('INVALID FILE REQUESTED'); 
 } 
```

#### Дополнительная информация:

*   [OWASP Wiki - Тестирование для включения локального файла](https://www.owasp.org/index.php/Testing_for_Local_File_Inclusion)